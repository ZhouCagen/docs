# ClientManager 服务器业务管理层

## 1. 这一层到底是干什么的？

现在已经写完的 `AsyncTcpServer` 只负责底层网络：

```text
accept 客户端连接
recv 收数据
send 发数据
epoll 监听事件
维护 inputBuffer / outputBuffer
```

但是它不知道：

```text
谁上线了
谁叫张三
谁给谁发消息
怎么广播
怎么私聊
客户端退出后怎么通知别人
消息格式对不对
```

这些都不应该写死在 `AsyncTcpServer` 里面。

所以要加一层：

```text
ClientManager
```

它负责服务器业务逻辑。

整体结构应该变成：

```text
客户端
  ↓
AsyncTcpServer
  ↓
ClientManager
  ↓
决定发给谁
  ↓
AsyncTcpServer::queueSend()
```

也就是说：

```text
AsyncTcpServer 负责收发
ClientManager 负责判断怎么处理消息
```

---

## 2. ClientManager 这一层要写什么？

### 2.1 管理在线客户端

每个客户端连接上来之后，都要记录下来。

需要保存的信息大概是：

```cpp
struct ClientInfo
{
    int socket;
    std::string name;
    bool loggedIn;
};
```

然后用 `unordered_map` 管理：

```cpp
std::unordered_map<int, ClientInfo> clients_;
```

意思是：

```text
socket -> 这个客户端的信息
```

例如：

```text
5  -> 张三
8  -> 李四
11 -> 王五
```

---

### 2.2 客户端上线

当 `AsyncTcpServer` accept 到一个新客户端之后，要通知 `ClientManager`：

```cpp
clientManager.onClientConnected(clientSocket);
```

ClientManager 要做：

```text
1. 把这个 socket 加入 clients_
2. 给这个客户端发欢迎消息
3. 提示它输入用户名
```

例如：

```text
Welcome! Please login with: LOGIN your_name
```

---

### 2.3 客户端下线

当客户端断开连接后，也要通知 `ClientManager`：

```cpp
clientManager.onClientDisconnected(clientSocket);
```

ClientManager 要做：

```text
1. 从 clients_ 里面找到这个人
2. 如果他已经登录，就广播 xxx 下线了
3. 从 clients_ 里面删除这个 socket
```

注意：

```text
close socket 是 AsyncTcpServer 的事情
从在线用户列表删除 是 ClientManager 的事情
```

---

### 2.4 处理客户端发来的消息

现在 `AsyncTcpServer` 收到一行完整消息后，应该交给 ClientManager：

```cpp
clientManager.onMessage(clientSocket, message);
```

ClientManager 根据消息内容决定怎么办。

例如：

```text
LOGIN zhou
ALL hello everyone
TO lisi hello
LIST
QUIT
```

---

## 3. 建议先做的消息协议

先不要一上来搞 JSON，也不要一上来搞数据库。

先用简单文本协议。

### 3.1 登录

客户端发送：

```text
LOGIN zhou
```

服务器处理：

```text
把这个 socket 对应的名字设置成 zhou
通知所有人 zhou 上线了
```

---

### 3.2 群发消息

客户端发送：

```text
ALL hello everyone
```

服务器转发给所有其他客户端：

```text
[zhou]: hello everyone
```

注意可以选择：

```text
发给所有人，包括自己
```

或者：

```text
只发给其他人
```

实验里推荐先发给所有人，包括自己，方便看效果。

---

### 3.3 私聊消息

客户端发送：

```text
TO lisi hello
```

服务器只发给名字叫 `lisi` 的客户端：

```text
[private] zhou -> you: hello
```

如果找不到这个用户，服务器回复发送方：

```text
user not found: lisi
```

---

### 3.4 查看在线用户

客户端发送：

```text
LIST
```

服务器回复：

```text
online users:
- zhou
- lisi
- wangwu
```

---

### 3.5 退出

客户端发送：

```text
QUIT
```

服务器可以主动断开这个客户端。

不过一开始也可以不写 `QUIT`，客户端直接关闭窗口也行。

---

## 4. ClientManager 需要有哪些函数？

建议先这样设计：

```cpp
#pragma once

#include <functional>
#include <string>
#include <unordered_map>

class ClientManager
{
public:
    using SendFunction = std::function<void(int, const std::string&)>;

    explicit ClientManager(SendFunction sendFunction);

    void onClientConnected(int clientSocket);
    void onClientDisconnected(int clientSocket);
    void onMessage(int clientSocket, const std::string& message);

private:
    struct ClientInfo
    {
        int socket;
        std::string name;
        bool loggedIn{false};
    };

    std::unordered_map<int, ClientInfo> clients_;
    SendFunction sendFunction_;

    void handleLogin(int clientSocket, const std::string& name);
    void handleBroadcast(int clientSocket, const std::string& content);
    void handlePrivateMessage(int clientSocket, const std::string& targetName, const std::string& content);
    void handleListUsers(int clientSocket);

    void sendToClient(int clientSocket, const std::string& message);
    void broadcast(const std::string& message);
    void broadcastExcept(int exceptSocket, const std::string& message);

    ClientInfo* findClientBySocket(int clientSocket);
    ClientInfo* findClientByName(const std::string& name);
};
```

这里最重要的是：

```cpp
using SendFunction = std::function<void(int, const std::string&)>;
```

它的意思是：

```text
ClientManager 不直接 send
ClientManager 只调用一个发送函数
真正怎么发，交给 AsyncTcpServer
```

这样可以降低耦合。

---

## 5. 为什么不要让 ClientManager 直接调用 send？

因为 `send()` 是底层网络函数。

你的 `AsyncTcpServer` 已经有：

```text
outputBuffers_
handleWrite()
epoll EPOLLOUT
非阻塞发送
```

如果 ClientManager 自己直接 `send()`，那就绕过了你前面写好的异步发送机制。

正确做法是：

```text
ClientManager 想发消息
        ↓
调用 sendFunction_
        ↓
实际走 AsyncTcpServer::queueSend()
        ↓
进入 outputBuffer
        ↓
epoll 可写时真正 send
```

所以业务层不能破坏底层异步结构。

---

## 6. AsyncTcpServer 和 ClientManager 怎么连起来？

大概思路是：

```cpp
ClientManager clientManager(
    [this](int clientSocket, const std::string& message)
    {
        queueSend(clientSocket, message);
    }
);
```

然后在这些地方调用：

### 新客户端连接时

```cpp
clientManager.onClientConnected(clientSocket);
```

### 收到完整消息时

```cpp
clientManager.onMessage(clientSocket, message);
```

### 客户端断开时

```cpp
clientManager.onClientDisconnected(clientSocket);
```

---

## 7. 这一层需要学什么？

### 7.1 `std::unordered_map`

必须学。

因为你要维护：

```text
socket -> 客户端信息
```

常用操作：

```cpp
clients_[clientSocket] = clientInfo;
clients_.find(clientSocket);
clients_.erase(clientSocket);
clients_.empty();
clients_.size();
```

---

### 7.2 `struct`

必须学。

因为客户端信息不能只存一个名字。

你需要把多个信息绑在一起：

```cpp
struct ClientInfo
{
    int socket;
    std::string name;
    bool loggedIn;
};
```

---

### 7.3 `std::function`

需要学一点。

因为 ClientManager 需要调用外面的发送函数：

```cpp
std::function<void(int, const std::string&)> sendFunction_;
```

它的意思是：

```text
保存一个函数
以后 ClientManager 想发送消息，就调用这个函数
```

---

### 7.4 lambda 表达式

需要学一点。

因为你要把 `queueSend()` 包装成一个函数传给 ClientManager。

例如：

```cpp
[this](int clientSocket, const std::string& message)
{
    queueSend(clientSocket, message);
}
```

这段意思是：

```text
保存当前对象 this
以后调用这个 lambda 的时候
就执行 queueSend(clientSocket, message)
```

---

### 7.5 字符串解析

需要学。

因为客户端发过来的消息是一整行：

```text
TO lisi hello
```

你要拆成：

```text
命令：TO
目标：lisi
内容：hello
```

可以先用简单方法：

```cpp
message.rfind("LOGIN ", 0) == 0
message.rfind("ALL ", 0) == 0
message.rfind("TO ", 0) == 0
```

暂时不用写复杂解析器。

---

### 7.6 遍历 map

需要学。

广播消息时要遍历所有在线客户端：

```cpp
for (const auto& pair : clients_)
{
    int socket = pair.first;
    const ClientInfo& client = pair.second;

    sendToClient(socket, message);
}
```

这里：

```text
pair.first  是 socket
pair.second 是 ClientInfo
```

---

### 7.7 什么时候需要锁

你现在的 `AsyncTcpServer` 如果是单线程 epoll，那么暂时不需要 mutex。

因为所有客户端事件都在同一个线程里处理。

但是如果以后变成：

```text
多线程
WebSocket 库自己开线程
线程池处理消息
```

那 `clients_` 就可能被多个线程同时访问，到时候需要：

```cpp
std::mutex
std::lock_guard
```

现在先不用加锁，避免复杂化。

---

## 8. 这一层暂时不需要学什么？

现在先不要碰这些：

```text
数据库
注册登录系统
密码加密
JWT
复杂 JSON 协议
Redis
消息持久化
群组系统
文件传输
```

这些都是后面的东西。

当前目标只有一个：

```text
至少两个客户端可以互相通信
```

所以先把在线用户管理和消息转发写出来。

---

## 9. 推荐文件结构

可以这样放：

```text
src/
├── AsyncTcpServer.cpp
├── ClientManager.cpp
└── main.cpp

include/
├── AsyncTcpServer.hpp
└── ClientManager.hpp
```

如果你的项目现在没有 `include/`，也可以先简单一点：

```text
src/
├── AsyncTcpServer.hpp
├── AsyncTcpServer.cpp
├── ClientManager.hpp
├── ClientManager.cpp
└── main.cpp
```

---

## 10. 推荐开发顺序

### 第一步：写 ClientManager.hpp

先只声明类，不写实现。

包括：

```text
ClientInfo
clients_
sendFunction_
onClientConnected
onClientDisconnected
onMessage
broadcast
sendToClient
```

---

### 第二步：写构造函数

让 ClientManager 保存发送函数：

```cpp
ClientManager::ClientManager(SendFunction sendFunction)
    : sendFunction_(std::move(sendFunction))
{
}
```

这里需要学：

```cpp
std::move
```

不过这个地方先知道：

```text
把传进来的函数移动到成员变量里
避免多余拷贝
```

---

### 第三步：写上线逻辑

实现：

```cpp
void onClientConnected(int clientSocket);
```

功能：

```text
加入 clients_
给客户端发送欢迎消息
```

---

### 第四步：写下线逻辑

实现：

```cpp
void onClientDisconnected(int clientSocket);
```

功能：

```text
找到这个客户端
如果已经登录，广播他下线
从 clients_ 删除
```

---

### 第五步：写登录逻辑

客户端发：

```text
LOGIN zhou
```

服务器做：

```text
设置 name
设置 loggedIn = true
广播 zhou joined chat
```

---

### 第六步：写群发逻辑

客户端发：

```text
ALL hello
```

服务器广播：

```text
[zhou]: hello
```

---

### 第七步：写私聊逻辑

客户端发：

```text
TO lisi hello
```

服务器找到 `lisi`，只发给他。

---

### 第八步：写在线列表

客户端发：

```text
LIST
```

服务器回复当前在线用户。

---

### 第九步：接入 AsyncTcpServer

把原来 `onTcpMessage()` 里面直接回显的逻辑删掉，改成：

```cpp
clientManager.onMessage(clientSocket, message);
```

---

## 11. 这一层写完后，实验完成度会提升多少？

如果不算前端，只算后端：

```text
AsyncTcpServer 已完成：50%～60%
ClientManager 写完后：70%～80%
```

因为后端就具备了：

```text
多客户端连接
在线用户管理
群发
私聊
下线通知
```

这已经很接近实验要求了。

---

## 12. 最终目标

ClientManager 写完后，你的后端逻辑应该是：

```text
客户端 A 连接服务器
客户端 B 连接服务器

A 发送：
LOGIN zhou

B 发送：
LOGIN lisi

A 发送：
ALL hello

服务器转发给所有客户端：
[zhou]: hello

A 发送：
TO lisi nihao

服务器只发给 lisi：
[private] zhou: nihao
```

这样就满足：

```text
至少 2 个客户端之间可以相互通信
```

---

## 13. 当前阶段最重要的一句话

不要把业务逻辑继续塞进 `AsyncTcpServer`。

正确分层是：

```text
AsyncTcpServer：只管网络收发
ClientManager：只管用户和消息转发
Vue/WebSocket：以后再接界面
```

现在下一步就是写：

```text
ClientManager.hpp
ClientManager.cpp
```

