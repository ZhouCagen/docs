# 异步 TCP 通信实验学习路线

## 0. 实验最终目标

本实验要完成一个 **异步 TCP C/S 通信程序**。

目标不是普通的：

```text
accept 一个客户端
recv 一个客户端
send 一个客户端
再处理下一个客户端
```

而是要做到：

```text
服务器可以同时管理多个客户端
哪个客户端有数据，服务器就处理哪个客户端
服务器不会因为某个客户端没发消息而卡住
客户端也可以一边发消息，一边接收服务器回复
```

最终效果：

```text
client1 可以发消息
client2 可以发消息
client3 可以发消息

服务器可以同时处理它们
不会必须等 client1 结束后才能处理 client2
```

---

## 1. 先明确几个概念

### 1.1 同步阻塞 TCP 是什么

普通 TCP 服务端一般是：

```text
socket()
bind()
listen()
accept()
recv()
send()
close()
```

如果代码是这样：

```cpp
int clientSocket = accept(serverSocket, nullptr, nullptr);
handleClient(clientSocket);
```

那么问题是：

```text
handleClient 不结束
服务器就回不到 accept
服务器就不能继续处理新的客户端
```

这就是 **阻塞式顺序处理**。

---

### 1.2 多线程 TCP 是什么

多线程版本一般是：

```text
主线程负责 accept
每 accept 一个客户端，就创建一个线程处理它
```

结构：

```text
主线程：
    accept client1
    创建线程1处理 client1

    accept client2
    创建线程2处理 client2

    accept client3
    创建线程3处理 client3
```

这种可以同时处理多个客户端，但它不是严格意义上的异步事件驱动。

它的特点是：

```text
每个客户端一个线程
每个线程里的 recv 还是阻塞的
```

优点：

```text
简单
容易理解
实验够用
```

缺点：

```text
客户端很多时线程数量会爆炸
线程切换开销大
不好扩展
```

---

### 1.3 异步 TCP 是什么

异步 TCP 的核心不是每个客户端一个线程，而是：

```text
一个线程同时管理很多 socket
哪个 socket 有事件，就处理哪个 socket
```

Linux 下常用：

```text
non-blocking socket + epoll
```

也就是：

```text
所有 socket 都设置成非阻塞
epoll 负责监听这些 socket
哪个 socket 可读，epoll 就通知服务器
哪个 socket 可写，epoll 也可以通知服务器
```

核心思想：

```text
程序不傻等某一个客户端
程序只处理已经准备好的 socket
```

---

## 2. 必须掌握的基础知识

## 2.1 文件描述符 fd

在 Linux 下，socket 本质上也是一个文件描述符。

```cpp
int serverSocket = socket(AF_INET, SOCK_STREAM, 0);
```

这里的 `serverSocket` 是一个整数。

它代表：

```text
操作系统里创建出来的一个 socket 资源
```

后续所有操作都是围绕这个 fd 进行：

```cpp
bind(serverSocket, ...);
listen(serverSocket, ...);
accept(serverSocket, ...);
recv(clientSocket, ...);
send(clientSocket, ...);
close(clientSocket);
```

所以要先记住：

```text
socket 返回的是 fd
fd 是操作系统资源编号
```

---

## 2.2 TCP 服务端基本流程

TCP 服务端基础流程：

```text
socket      创建服务器 socket
setsockopt  设置地址复用
bind        绑定本机 IP + 本机端口
listen      开始监听
accept      接收客户端连接
recv        接收客户端数据
send        给客户端发送数据
close       关闭 socket
```

每一步的作用：

```text
socket:
    创建通信对象

setsockopt:
    让端口可以快速复用，避免程序刚退出后端口暂时不能用

bind:
    把服务器 socket 绑定到本机的 IP 和端口

listen:
    把 socket 变成监听 socket

accept:
    从监听队列里取出一个已经连接的客户端

recv:
    从客户端 socket 读取数据

send:
    往客户端 socket 发送数据

close:
    释放 socket
```

---

## 2.3 bind 的意义

服务端 `bind` 绑定的是：

```text
本机 IP + 本机端口
```

比如：

```cpp
serverAddr.sin_addr.s_addr = INADDR_ANY;
serverAddr.sin_port = htons(2006);
```

意思是：

```text
本机所有网卡的 2006 端口都归这个 serverSocket 管
```

如果客户端连接：

```text
127.0.0.1:2006
```

或者局域网其他机器连接：

```text
192.168.x.x:2006
```

只要服务器绑定的是 `INADDR_ANY:2006`，就可以接收。

---

## 2.4 listen 的意义

`listen` 的作用是：

```text
告诉操作系统：这个 socket 现在开始接收 TCP 连接请求
```

调用 listen 之后，服务器 socket 才正式成为监听 socket。

```cpp
listen(serverSocket, SOMAXCONN);
```

---

## 2.5 accept 的意义

`accept` 的作用是：

```text
从已经完成连接的客户端队列里取出一个客户端
```

注意：

```text
serverSocket 是监听 socket
clientSocket 是通信 socket
```

服务器真正和客户端通信，用的是 `accept` 返回的 `clientSocket`。

---

## 3. 非阻塞 socket

## 3.1 阻塞是什么意思

阻塞就是：

```text
如果现在没有数据，函数就一直等
```

例如：

```cpp
recv(clientSocket, buffer, sizeof(buffer), 0);
```

如果客户端没发数据，普通阻塞 socket 会卡在这里。

---

## 3.2 非阻塞是什么意思

非阻塞就是：

```text
如果现在没有数据，函数不会傻等，而是立刻返回错误
```

比如：

```text
recv 没有数据可读
返回 -1
errno 是 EAGAIN 或 EWOULDBLOCK
```

这不是真正的错误，而是表示：

```text
现在没数据，你等会儿再来读
```

---

## 3.3 设置 socket 为非阻塞

需要头文件：

```cpp
#include <fcntl.h>
```

函数：

```cpp
bool setNonBlocking(int fd)
{
    int flags = fcntl(fd, F_GETFL, 0);
    if (flags == -1)
        return false;

    return fcntl(fd, F_SETFL, flags | O_NONBLOCK) != -1;
}
```

要设置非阻塞的 socket：

```text
serverSocket 要设置非阻塞
每个 accept 出来的 clientSocket 也要设置非阻塞
```

---

## 3.4 非阻塞下必须处理的 errno

必须认识：

```text
EAGAIN
EWOULDBLOCK
EINTR
```

### EAGAIN / EWOULDBLOCK

表示：

```text
现在暂时不能读或者不能写
不是致命错误
稍后再试
```

常见场景：

```text
非阻塞 recv 时，没有数据可读
非阻塞 send 时，发送缓冲区满了
```

### EINTR

表示：

```text
系统调用被信号中断
通常可以继续重试
```

例如：

```cpp
int eventCount = epoll_wait(epollFd, events, maxEvents, -1);

if (eventCount == -1)
{
    if (errno == EINTR)
        continue;
}
```

---

## 4. epoll 必须掌握的内容

## 4.1 epoll 是什么

`epoll` 是 Linux 下的 I/O 多路复用机制。

它的作用是：

```text
帮程序同时监听多个 fd
哪个 fd 有事件，就通知程序
```

普通阻塞写法是：

```text
程序自己一个一个 socket 去等
```

epoll 写法是：

```text
把所有 socket 交给 epoll
epoll 告诉你哪些 socket 已经准备好了
```

---

## 4.2 epoll 的三个核心函数

### epoll_create1

创建 epoll 实例。

```cpp
int epollFd = epoll_create1(0);
```

可以理解为：

```text
创建一个事件管理器
```

---

### epoll_ctl

把 fd 加入 epoll，或者从 epoll 删除 fd。

```cpp
epoll_ctl(epollFd, EPOLL_CTL_ADD, fd, &event);
epoll_ctl(epollFd, EPOLL_CTL_MOD, fd, &event);
epoll_ctl(epollFd, EPOLL_CTL_DEL, fd, nullptr);
```

三个操作：

```text
EPOLL_CTL_ADD:
    添加一个 fd

EPOLL_CTL_MOD:
    修改一个 fd 关注的事件

EPOLL_CTL_DEL:
    删除一个 fd
```

---

### epoll_wait

等待事件发生。

```cpp
int eventCount = epoll_wait(epollFd, events, maxEvents, -1);
```

意思是：

```text
等待 epoll 里某些 fd 出现事件
```

最后一个参数：

```text
-1:
    一直等

0:
    不等待，马上返回

正数:
    最多等待多少毫秒
```

---

## 4.3 常见 epoll 事件

### EPOLLIN

表示：

```text
这个 fd 可以读了
```

对于 serverSocket：

```text
有新客户端连接来了，可以 accept
```

对于 clientSocket：

```text
客户端发数据来了，可以 recv
```

---

### EPOLLOUT

表示：

```text
这个 fd 可以写了
```

也就是：

```text
现在可以 send 数据
```

注意：

```text
不要一开始就一直监听 EPOLLOUT
否则它会一直触发，导致 CPU 空转
```

正确做法：

```text
只有 outputBuffer 里有数据没发完时，才监听 EPOLLOUT
发完后取消 EPOLLOUT
```

---

### EPOLLERR

表示：

```text
socket 出错
```

遇到一般关闭客户端。

---

### EPOLLHUP

表示：

```text
对端挂断
```

遇到一般关闭客户端。

---

## 4.4 LT 和 ET

epoll 有两种模式：

```text
LT: Level Triggered，水平触发
ET: Edge Triggered，边缘触发
```

### LT 模式

默认模式。

特点：

```text
只要 fd 还有数据没读完，epoll_wait 还会继续通知你
```

优点：

```text
简单
不容易写错
适合第一版异步服务器
```

---

### ET 模式

边缘触发。

特点：

```text
只有状态变化的时候通知一次
```

比如：

```text
从没有数据变成有数据时通知一次
```

要求：

```text
必须一次 recv 循环读到 EAGAIN
否则可能剩下的数据再也收不到通知
```

第一版实验建议：

```text
先用 LT，不用 ET
```

---

## 5. 异步服务器整体结构

## 5.1 初始化流程

服务器启动流程：

```text
createSocket()
setReuseAddress()
bindAddress()
listenSocket()
setNonBlocking(serverSocket)
createEpoll()
add serverSocket to epoll
eventLoop()
```

对应代码结构：

```cpp
void TcpServer::run()
{
    createSocket();
    setReuseAddress();
    bindAddress();
    listenSocket();

    if (!setNonBlocking(serverSocket_))
    {
        spdlog::error("set server socket non-blocking failed");
        return;
    }

    eventLoop();
}
```

---

## 5.2 事件循环

事件循环是异步服务器的核心。

伪代码：

```text
while true:
    eventCount = epoll_wait()

    for each event:
        if event.fd == serverSocket:
            acceptClients()
        else:
            handleClientEvent()
```

也就是：

```text
serverSocket 有事件：
    说明有新客户端连接

clientSocket 有事件：
    说明客户端有数据、可写、断开、出错
```

---

## 5.3 acceptClients

`acceptClients` 的作用：

```text
把当前所有已经连接完成的客户端全部 accept 出来
```

为什么要循环 accept？

因为：

```text
同一时刻可能来了多个客户端
非阻塞 accept 要一直 accept 到 EAGAIN
```

伪代码：

```text
while true:
    clientSocket = accept(serverSocket)

    if clientSocket == -1:
        if errno == EAGAIN:
            break
        else:
            error
            break

    setNonBlocking(clientSocket)
    add clientSocket to epoll
    create Client object
```

---

## 5.4 handleClientEvent

`handleClientEvent` 的作用：

```text
处理某个客户端 socket 上发生的事件
```

通常要处理：

```text
EPOLLIN:
    客户端发来了数据，需要 recv

EPOLLOUT:
    当前可以继续发送数据，需要 flush outputBuffer

EPOLLERR / EPOLLHUP:
    客户端异常或断开，需要 close
```

---

## 6. 客户端状态管理

真正的异步服务器不能只保存 fd。

还要保存每个客户端的状态。

可以设计：

```cpp
struct Client
{
    std::string inputBuffer;
    std::string outputBuffer;
};
```

服务器类里保存：

```cpp
std::unordered_map<int, Client> clients_;
```

含义：

```text
key:
    clientSocket

value:
    这个客户端对应的输入缓冲区和输出缓冲区
```

---

## 6.1 inputBuffer

`inputBuffer` 用来保存客户端发来的数据。

为什么需要它？

因为 TCP 是字节流。

一次 `recv` 不一定刚好收到一条完整消息。

可能出现：

```text
客户端发送: hello\n
服务器 recv 一次只收到: he
服务器下一次 recv 收到: llo\n
```

也可能出现：

```text
客户端发送两条:
hello\n
world\n

服务器一次 recv 收到:
hello\nworld\n
```

所以不能认为：

```text
一次 recv 等于一条完整消息
```

---

## 6.2 outputBuffer

`outputBuffer` 用来保存还没发送完的数据。

为什么需要它？

因为 `send` 不一定一次把所有数据都发出去。

例如：

```cpp
ssize_t n = send(clientSocket, data, dataSize, MSG_NOSIGNAL);
```

可能：

```text
dataSize 是 1000
send 实际只发送了 300
剩下 700 必须下次继续发
```

如果 socket 是非阻塞，还可能：

```text
send 返回 -1
errno 是 EAGAIN
```

意思是：

```text
现在暂时不能继续发送
等 EPOLLOUT 再发
```

---

## 7. 消息边界问题

TCP 是字节流，没有天然消息边界。

所以必须自己设计协议。

第一版建议使用：

```text
一行一条消息
用 '\n' 作为消息结束标志
```

例如客户端发送：

```text
hello server\n
```

服务器收到后，从 inputBuffer 中查找 `\n`。

只要找到一行完整消息，就取出来处理。

---

## 7.1 行协议处理流程

伪代码：

```text
recv 数据追加到 inputBuffer

while inputBuffer 里能找到 '\n':
    取出一行 message
    删除 inputBuffer 中已经处理的部分
    生成 reply
    追加到 outputBuffer
```

---

## 7.2 后续可以升级为长度头协议

更标准的协议是：

```text
4 字节长度头 + 正文内容
```

例如：

```text
[消息长度][消息内容]
```

优点：

```text
可以发送任意二进制数据
不依赖换行符
```

但是第一版实验建议先用行协议。

---

## 8. 异步发送机制

## 8.1 为什么不能直接 send 完就算了

阻塞版可以简单写：

```cpp
send(clientSocket, reply.c_str(), reply.size(), MSG_NOSIGNAL);
```

但异步非阻塞服务器不应该这么简单。

因为：

```text
send 可能只发送一部分
send 可能返回 EAGAIN
```

所以要这样设计：

```text
业务处理只负责把回复放进 outputBuffer
真正发送由 EPOLLOUT 事件触发
```

---

## 8.2 什么时候监听 EPOLLOUT

当 `outputBuffer` 为空时：

```text
只监听 EPOLLIN
```

当 `outputBuffer` 有数据时：

```text
监听 EPOLLIN | EPOLLOUT
```

当 `outputBuffer` 发送完后：

```text
取消 EPOLLOUT
继续只监听 EPOLLIN
```

---

## 8.3 修改 epoll 监听事件

需要用：

```cpp
epoll_ctl(epollFd, EPOLL_CTL_MOD, clientSocket, &event);
```

比如：

```cpp
void enableWriteEvent(int epollFd, int clientSocket)
{
    epoll_event event{};
    event.events = EPOLLIN | EPOLLOUT;
    event.data.fd = clientSocket;

    epoll_ctl(epollFd, EPOLL_CTL_MOD, clientSocket, &event);
}
```

取消写事件：

```cpp
void disableWriteEvent(int epollFd, int clientSocket)
{
    epoll_event event{};
    event.events = EPOLLIN;
    event.data.fd = clientSocket;

    epoll_ctl(epollFd, EPOLL_CTL_MOD, clientSocket, &event);
}
```

---

## 9. 服务器类需要的成员

第一版异步服务器可以这样设计。

### TcpServer.hpp

```cpp
#pragma once

#include <cstdint>
#include <string>
#include <unordered_map>

class TcpServer
{
public:
    explicit TcpServer(std::uint16_t port);
    ~TcpServer();

    TcpServer(const TcpServer&) = delete;
    TcpServer& operator=(const TcpServer&) = delete;

    void run();

private:
    struct Client
    {
        std::string inputBuffer;
        std::string outputBuffer;
    };

private:
    bool createSocket();
    bool setReuseAddress();
    bool bindAddress();
    bool listenSocket();
    bool setNonBlocking(int fd);

    void eventLoop();
    void acceptClients(int epollFd);
    void handleClientEvent(int epollFd, int clientSocket, std::uint32_t events);

    void readFromClient(int epollFd, int clientSocket);
    void writeToClient(int epollFd, int clientSocket);

    void processInput(int epollFd, int clientSocket);
    void appendReply(int epollFd, int clientSocket, const std::string& message);

    void enableWriteEvent(int epollFd, int clientSocket);
    void disableWriteEvent(int epollFd, int clientSocket);

    void closeClient(int epollFd, int clientSocket);

private:
    std::uint16_t port_;
    int serverSocket_;
    std::unordered_map<int, Client> clients_;
};
```

---

## 10. 客户端需要怎么写

服务器异步之后，客户端也最好不要写成：

```text
输入一次
send 一次
recv 一次
再输入下一次
```

因为这样客户端还是顺序的。

第一版客户端建议使用两个线程：

```text
发送线程：
    getline 读取键盘
    send 到服务器

接收线程：
    recv 服务器消息
    打印到屏幕
```

这样可以做到：

```text
用户随时输入消息
服务器回复也能随时显示
```

---

## 10.1 客户端两个线程结构

伪代码：

```text
main:
    socket
    connect

    创建 recvThread
    主线程负责 getline + send

recvThread:
    while running:
        recv server message
        print
```

---

## 10.2 客户端后续也可以升级成 poll

更完整的异步客户端可以使用：

```text
poll 同时监听 stdin 和 socket
```

但是第一版没必要。

因为客户端用两个线程已经可以满足：

```text
同时发
同时收
```

---

## 11. 实验开发顺序

不要一上来就写完整异步，否则容易乱。

按照这个顺序写。

---

## 第 1 步：写普通 TCP 服务端

目标：

```text
能 socket
能 bind
能 listen
能 accept
能 recv
能 send
```

这一版允许阻塞。

验证：

```text
一个客户端能连接服务器
客户端发 hello
服务器回复 server received: hello
```

---

## 第 2 步：改成多客户端 epoll accept

目标：

```text
serverSocket 加入 epoll
epoll_wait 监听 serverSocket
有新连接时 acceptClients
```

这一阶段先不急着处理复杂发送。

验证：

```text
多个客户端可以同时连接
服务器日志能显示多个 client fd
```

---

## 第 3 步：把 clientSocket 加入 epoll

目标：

```text
accept 出来的 clientSocket 设置为非阻塞
clientSocket 加入 epoll
监听 EPOLLIN
```

验证：

```text
client1 发消息，服务器能收到
client2 发消息，服务器也能收到
client1 不发，不影响 client2
```

---

## 第 4 步：加入 inputBuffer

目标：

```text
recv 到的数据追加到 inputBuffer
按 '\n' 切分完整消息
```

验证：

```text
客户端连续发送多行消息
服务器能按行处理
```

---

## 第 5 步：加入 outputBuffer

目标：

```text
处理消息后，不直接假设 send 一定成功
而是把回复追加到 outputBuffer
然后开启 EPOLLOUT
```

验证：

```text
客户端发消息
服务器回复
多个客户端互不影响
```

---

## 第 6 步：完善 EPOLLOUT

目标：

```text
EPOLLOUT 触发时，继续发送 outputBuffer
发完后关闭 EPOLLOUT
```

验证：

```text
大量发送数据时，服务器不会丢回复
```

---

## 第 7 步：完善关闭逻辑

目标：

```text
客户端断开时：
    epoll 删除 clientSocket
    close clientSocket
    clients_ 删除对应状态
```

验证：

```text
客户端退出后服务器不崩
其他客户端继续正常通信
```

---

## 第 8 步：客户端改成收发分离

目标：

```text
主线程发消息
子线程收消息
```

验证：

```text
客户端不用发一次等一次
可以连续发
服务器回复随时显示
```

---

## 12. 必须注意的坑

## 12.1 TCP 一次 recv 不等于一条消息

错误想法：

```text
一次 recv 就是一条完整消息
```

正确想法：

```text
TCP 是字节流
必须自己处理消息边界
```

第一版用：

```text
\n 作为消息结束符
```

---

## 12.2 send 不一定一次发完

错误想法：

```text
send 成功就表示所有数据都发完了
```

正确想法：

```text
send 返回多少，才是真的发送了多少
剩下的要继续保存
```

---

## 12.3 非阻塞里的 EAGAIN 不是错误

遇到：

```text
errno == EAGAIN
errno == EWOULDBLOCK
```

不要直接当成 fatal error。

应该理解为：

```text
现在没准备好，稍后再处理
```

---

## 12.4 不要一直监听 EPOLLOUT

如果一直监听 EPOLLOUT，可能导致：

```text
epoll_wait 一直返回
CPU 占用很高
```

正确做法：

```text
有数据要发才监听 EPOLLOUT
发完就取消 EPOLLOUT
```

---

## 12.5 close 之前要从 epoll 删除

关闭客户端时要做：

```text
epoll_ctl DEL
close
erase client state
```

顺序可以写成：

```cpp
epoll_ctl(epollFd, EPOLL_CTL_DEL, clientSocket, nullptr);
close(clientSocket);
clients_.erase(clientSocket);
```

---

## 12.6 日志要清楚

建议日志包含：

```text
server socket created
server bind success
server listen success
epoll created
client connected
message received
reply queued
message sent
client disconnected
recv error
send error
```

这样调试非常舒服。

---

## 13. 需要学习的系统调用清单

### socket 相关

```text
socket
setsockopt
bind
listen
accept
recv
send
close
```

### 地址相关

```text
htons
ntohs
inet_ntop
inet_pton
sockaddr_in
sockaddr
INADDR_ANY
```

### 非阻塞相关

```text
fcntl
F_GETFL
F_SETFL
O_NONBLOCK
```

### epoll 相关

```text
epoll_create1
epoll_ctl
epoll_wait
epoll_event
EPOLLIN
EPOLLOUT
EPOLLERR
EPOLLHUP
EPOLL_CTL_ADD
EPOLL_CTL_MOD
EPOLL_CTL_DEL
```

### 错误处理相关

```text
errno
strerror
EAGAIN
EWOULDBLOCK
EINTR
```

---

## 14. 需要学习的 C++ 内容

### 基础类型

```text
std::uint16_t
std::size_t
ssize_t
socklen_t
```

### 字符串

```text
std::string
c_str()
size()
append()
erase()
find()
substr()
```

### 容器

```text
std::unordered_map
```

用途：

```text
根据 clientSocket 找到对应 Client 状态
```

### RAII

析构函数里关闭资源：

```cpp
TcpServer::~TcpServer()
{
    if (serverSocket_ != -1)
        close(serverSocket_);
}
```

### 禁止拷贝

服务器对象管理 socket，不应该随便复制。

```cpp
TcpServer(const TcpServer&) = delete;
TcpServer& operator=(const TcpServer&) = delete;
```

---

## 15. 项目结构建议

```text
AsyncTcpDemo/
├── CMakeLists.txt
├── include/
│   ├── TcpServer.hpp
│   └── TcpClient.hpp
├── src/
│   ├── TcpServer.cpp
│   ├── TcpClient.cpp
│   ├── server_main.cpp
│   └── client_main.cpp
└── README.md
```

---

## 16. CMake 目标

至少两个可执行文件：

```text
async_tcp_server
async_tcp_client
```

CMake 结构：

```text
add_executable(async_tcp_server ...)
add_executable(async_tcp_client ...)
```

需要链接：

```text
spdlog
pthread
```

---

## 17. 第一版最终验收标准

服务器启动后：

```text
[info] TCP async server started on port 2006
```

客户端 1 连接：

```text
[info] client connected: fd = 5
```

客户端 2 连接：

```text
[info] client connected: fd = 6
```

客户端 1 发送：

```text
hello from client1
```

服务器显示：

```text
[info] client 5 says: hello from client1
```

客户端 2 发送：

```text
hello from client2
```

服务器显示：

```text
[info] client 6 says: hello from client2
```

并且：

```text
client1 不发消息时，不影响 client2
client2 不发消息时，不影响 client1
任意客户端退出，服务器不崩
```

---

## 18. 推荐学习顺序总结

最终按这个顺序学：

```text
1. TCP 服务端基础流程
2. fd 是什么
3. 阻塞和非阻塞
4. fcntl 设置 O_NONBLOCK
5. errno / EAGAIN / EWOULDBLOCK / EINTR
6. epoll_create1
7. epoll_ctl
8. epoll_wait
9. EPOLLIN
10. acceptClients 循环 accept
11. clientSocket 加入 epoll
12. recv 循环读数据
13. TCP 字节流和消息边界
14. inputBuffer
15. outputBuffer
16. EPOLLOUT
17. send 部分发送处理
18. 客户端收发分离
19. 多客户端测试
20. 整理实验报告
```

---

## 19. 最终一句话理解

异步 TCP 服务器的本质是：

```text
不要让程序卡在某一个客户端身上
把所有 socket 都交给 epoll
谁准备好了就处理谁
没准备好的就先不管
```

普通阻塞版是：

```text
我等你一个人说话
```

多线程版是：

```text
我给每个人安排一个服务员
```

epoll 异步版是：

```text
一个服务员看着所有人
谁举手就服务谁
```

