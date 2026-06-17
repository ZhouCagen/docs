# WebSocket v1 学习文档

## 0. 你现在处于哪一步

你已经写完了异步 TCP 服务器：

```text
AsyncTcpServer
    socket
    bind
    listen
    epoll
    accept
    recv
    send
    close
```

也就是说，你现在已经有了最底层的传输能力。

但是浏览器不能直接用你原来的 TCP 文本协议：

```text
hello\n
```

浏览器的 WebSocket 是建立在 TCP 上的应用层协议。

所以你现在要做的是：

```text
在 AsyncTcpServer 上面，加一层 WebSocket 协议解析
```

整体结构是：

```text
浏览器
  |
  | WebSocket 协议
  |
C++ AsyncTcpServer
  |
  | TCP
  |
Linux Socket / epoll
```

---

# 1. WebSocket 到底是啥

WebSocket 是一种应用层协议。

它解决的问题是：

```text
浏览器和服务器之间建立一条长期连接
双方可以随时互相发消息
```

普通 HTTP 是：

```text
客户端请求一次
服务器回复一次
结束
```

WebSocket 是：

```text
客户端连接服务器
服务器同意升级协议
连接保持不断
客户端可以发消息
服务器也可以主动发消息
```

所以聊天室、游戏、在线协作这种东西，经常用 WebSocket。

---

# 2. WebSocket 和 TCP 的关系

WebSocket 不是替代 TCP。

WebSocket 是跑在 TCP 上面的。

```text
TCP:
    只负责字节流传输

WebSocket:
    规定这些字节怎么解释
```

也就是说，TCP 只看见：

```text
一堆二进制字节
```

WebSocket 规定：

```text
第一次发 HTTP Upgrade 请求
后面每条消息都要包装成 frame
```

---

# 3. 你原来的 TCP 协议为什么不能用了

你原来的代码是按换行符分包：

```cpp
std::size_t newlinePos = inputBuffer.find('\n');
```

这种协议意思是：

```text
收到 \n 就认为一条消息结束
```

例如：

```text
hello\n
```

但是浏览器 WebSocket 发过来的不是这种格式。

浏览器第一次连接时发的是 HTTP 请求：

```http
GET / HTTP/1.1
Host: 127.0.0.1:2006
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Key: xxxxx
Sec-WebSocket-Version: 13
```

握手成功以后，浏览器发的也不是裸文本，而是 WebSocket frame。

所以你不能继续用：

```cpp
inputBuffer.find('\n')
```

而是要改成：

```text
如果还没握手：
    按 HTTP 请求头解析

如果已经握手：
    按 WebSocket frame 解析
```

---

# 4. WebSocket v1 要实现什么

你现在第一版只需要实现最小功能。

目标：

```text
1. 浏览器可以 new WebSocket("ws://127.0.0.1:2006")
2. 服务器能完成握手
3. 浏览器能 ws.send("hello")
4. 服务器能收到真正的 hello
5. 服务器能回复 "server received: hello"
6. 浏览器能在 onmessage 里面收到回复
```

暂时不写：

```text
广播
私聊
用户列表
登录
数据库
消息历史
Vue 页面
心跳
分片 frame
二进制 frame
```

---

# 5. WebSocket v1 文件分工

你的项目现在应该这样分：

```text
backend/include/AsyncTcpServer.hpp
backend/src/AsyncTcpServer.cpp

backend/include/WebSocket.hpp
backend/src/WebSocket.cpp
```

职责划分：

```text
AsyncTcpServer:
    管 socket
    管 epoll
    管 accept
    管 read/write
    管 client buffer

WebSocket:
    管 WebSocket 协议
    管握手
    管 frame 编码
    管 frame 解码
```

不要让 WebSocket 里面直接操作 socket。

WebSocket 只处理字符串和二进制数据。

---

# 6. 第一个重点：WebSocket 握手

## 6.1 浏览器第一次发什么

浏览器连接时会发一个 HTTP Upgrade 请求。

大概长这样：

```http
GET / HTTP/1.1
Host: 127.0.0.1:2006
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Key: abcdefg==
Sec-WebSocket-Version: 13
```

重点字段是：

```http
Sec-WebSocket-Key
```

服务器要拿这个 key 算出：

```http
Sec-WebSocket-Accept
```

然后回复：

```http
HTTP/1.1 101 Switching Protocols
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Accept: 算出来的值
```

只要这个回复正确，浏览器就认为 WebSocket 连接建立成功。

---

## 6.2 握手怎么算 Sec-WebSocket-Accept

公式是固定的：

```text
Sec-WebSocket-Accept =
    Base64(
        SHA1(
            Sec-WebSocket-Key + "258EAFA5-E914-47DA-95CA-C5AB0DC85B11"
        )
    )
```

这个 GUID 是固定的：

```text
258EAFA5-E914-47DA-95CA-C5AB0DC85B11
```

所以你需要学这几个东西：

```text
1. 从 HTTP 请求头里面取 Sec-WebSocket-Key
2. 字符串拼接 magic GUID
3. SHA1 哈希
4. Base64 编码
5. 拼出 HTTP 101 响应
```

---

## 6.3 你要写的握手函数

在 `WebSocket.hpp` 里需要：

```cpp
static bool hasCompleteHandshakeRequest(const std::string& buffer);
static std::string buildHandshakeResponse(const std::string& request);
```

### hasCompleteHandshakeRequest

HTTP 请求头结束标志是：

```text
\r\n\r\n
```

所以判断方式是：

```cpp
return buffer.find("\r\n\r\n") != std::string::npos;
```

意思是：

```text
如果 buffer 里面已经出现了空行
说明 HTTP 请求头收完整了
```

---

### buildHandshakeResponse

这个函数负责：

```text
1. 找到 Sec-WebSocket-Key
2. 计算 Sec-WebSocket-Accept
3. 拼出 HTTP 101 响应
```

伪代码：

```text
key = getHeaderValue(request, "Sec-WebSocket-Key")

accept = base64(sha1(key + magicGuid))

response =
    "HTTP/1.1 101 Switching Protocols\r\n"
    "Upgrade: websocket\r\n"
    "Connection: Upgrade\r\n"
    "Sec-WebSocket-Accept: " + accept + "\r\n"
    "\r\n"
```

---

# 7. 第二个重点：WebSocket frame

握手之后，浏览器发消息不是直接发文本。

比如浏览器写：

```js
ws.send("hello");
```

TCP 里面真正收到的不是：

```text
hello
```

而是一段 WebSocket frame。

WebSocket frame 格式大概是：

```text
第 1 字节:
    FIN + opcode

第 2 字节:
    MASK + payload length

可能还有:
    扩展长度

然后:
    4 字节 mask key

最后:
    被 mask 加密过的 payload
```

---

# 8. 第一个字节：FIN 和 opcode

第一个字节结构：

```text
1000 0001
```

拆开看：

```text
最高位 1:
    FIN = 1
    表示这是完整的一条消息

低 4 位 0001:
    opcode = 1
    表示 text frame
```

常见 opcode：

```text
0x1    text frame
0x2    binary frame
0x8    close frame
0x9    ping frame
0xA    pong frame
```

v1 你只处理：

```text
0x1    文本消息
0x8    关闭连接
```

---

# 9. 第二个字节：MASK 和 payload length

第二个字节结构：

```text
1000 0101
```

最高位是 MASK：

```text
1 表示 payload 被 mask 过
0 表示 payload 没有 mask
```

浏览器发给服务器的 frame 必须 mask。

服务器发给浏览器的 frame 不用 mask。

所以：

```text
浏览器 -> 服务器:
    masked = true

服务器 -> 浏览器:
    masked = false
```

第二个字节低 7 位是 payload 长度。

长度规则：

```text
0 ~ 125:
    低 7 位就是长度

126:
    后面再读 2 字节，表示真正长度

127:
    后面再读 8 字节，表示真正长度
```

v1 最少支持：

```text
0 ~ 125
126 + 2字节长度
```

---

# 10. mask 解码是什么

浏览器发给服务器的 payload 是被 mask 过的。

解码公式：

```cpp
decoded[i] = encoded[i] ^ maskKey[i % 4];
```

意思是：

```text
payload 每个字节都和 maskKey 的某一个字节做异或
```

maskKey 有 4 字节。

例如：

```text
第 0 个 payload 字节 ^ maskKey[0]
第 1 个 payload 字节 ^ maskKey[1]
第 2 个 payload 字节 ^ maskKey[2]
第 3 个 payload 字节 ^ maskKey[3]
第 4 个 payload 字节 ^ maskKey[0]
```

循环使用。

---

# 11. WebSocket 解码函数要做什么

你需要写：

```cpp
static std::vector<std::string> decodeTextFrames(std::string& buffer, bool& shouldClose);
```

它要做：

```text
1. 检查 buffer 里有没有至少 2 字节
2. 解析 firstByte
3. 解析 secondByte
4. 判断 FIN
5. 判断 opcode
6. 判断 masked
7. 解析 payloadLength
8. 读取 maskKey
9. 判断完整 payload 有没有收全
10. 解码 payload
11. 从 buffer 里删掉已经处理完的 frame
12. 如果是 text frame，返回 message
13. 如果是 close frame，shouldClose = true
```

---

# 12. WebSocket 编码函数要做什么

服务器回复浏览器时，也要打包成 WebSocket frame。

你需要写：

```cpp
static std::string encodeTextFrame(const std::string& message);
```

服务器发文本 frame：

```text
第 1 字节:
    0x81
    FIN = 1
    opcode = 1

第 2 字节:
    payload length
    不设置 mask

后面:
    message 原文
```

所以最简单的 frame 是：

```text
0x81 + length + message
```

如果消息长度小于 126：

```cpp
frame.push_back(0x81);
frame.push_back(message.size());
frame += message;
```

如果长度大于等于 126，就要写扩展长度。

---

# 13. AsyncTcpServer 要怎么改

你现在 `AsyncTcpServer` 里有：

```text
inputBuffers_
outputBuffers_
```

还需要加一个：

```cpp
std::unordered_map<int, ClientState> clientStates_;
```

每个客户端都有一个状态。

```cpp
enum class ClientState
{
    WebSocketHandshake,
    WebSocketConnected
};
```

状态含义：

```text
WebSocketHandshake:
    客户端刚连接，还没完成 HTTP Upgrade

WebSocketConnected:
    握手成功，后面可以收发 WebSocket frame
```

---

# 14. handleAccept 要改什么

客户端刚连接进来时，状态应该是：

```cpp
clientStates_[clientSocket] = ClientState::WebSocketHandshake;
```

完整逻辑：

```text
accept 成功
setNonBlocking
inputBuffers_[clientSocket] = ""
outputBuffers_[clientSocket] = ""
clientStates_[clientSocket] = WebSocketHandshake
addToEpoll
```

---

# 15. closeClient 要改什么

关闭客户端时，除了删 input/output buffer，还要删状态。

```cpp
inputBuffers_.erase(clientSocket);
outputBuffers_.erase(clientSocket);
clientStates_.erase(clientSocket);
```

---

# 16. processInputBuffer 要改什么

原来：

```text
按 \n 分包
```

现在：

```text
按客户端状态分发
```

新逻辑：

```cpp
void AsyncTcpServer::processInputBuffer(int clientSocket)
{
    auto stateIterator = clientStates_.find(clientSocket);
    if (stateIterator == clientStates_.end())
        return;

    if (stateIterator->second == ClientState::WebSocketHandshake)
    {
        processWebSocketHandshake(clientSocket);
        return;
    }

    if (stateIterator->second == ClientState::WebSocketConnected)
    {
        processWebSocketFrames(clientSocket);
        return;
    }
}
```

意思是：

```text
没握手:
    去处理 HTTP Upgrade

握手完:
    去处理 WebSocket frame
```

---

# 17. processWebSocketHandshake 要做什么

新增函数：

```cpp
void processWebSocketHandshake(int clientSocket);
```

它负责：

```text
1. 找到 inputBuffer
2. 判断 HTTP 请求头有没有收完整
3. 取出完整请求头
4. 从 inputBuffer 里删掉请求头
5. 构造握手响应
6. queueSend 给客户端
7. 状态改成 WebSocketConnected
8. 如果 inputBuffer 里还有剩余数据，继续处理 frame
```

伪代码：

```cpp
void AsyncTcpServer::processWebSocketHandshake(int clientSocket)
{
    std::string& inputBuffer = inputBuffers_[clientSocket];

    if (!WebSocket::hasCompleteHandshakeRequest(inputBuffer))
        return;

    std::size_t headerEnd = inputBuffer.find("\r\n\r\n");
    std::string request = inputBuffer.substr(0, headerEnd + 4);

    inputBuffer.erase(0, headerEnd + 4);

    std::string response = WebSocket::buildHandshakeResponse(request);
    queueSend(clientSocket, response);

    clientStates_[clientSocket] = ClientState::WebSocketConnected;

    if (!inputBuffer.empty())
        processWebSocketFrames(clientSocket);
}
```

---

# 18. processWebSocketFrames 要做什么

新增函数：

```cpp
void processWebSocketFrames(int clientSocket);
```

它负责：

```text
1. 找到 inputBuffer
2. 调 decodeTextFrames
3. 拿到真正的文本消息
4. 调 onTcpMessage
5. 如果收到 close frame，就 closeClient
```

伪代码：

```cpp
void AsyncTcpServer::processWebSocketFrames(int clientSocket)
{
    std::string& inputBuffer = inputBuffers_[clientSocket];

    bool shouldClose = false;
    std::vector<std::string> messages =
        WebSocket::decodeTextFrames(inputBuffer, shouldClose);

    for (const std::string& message : messages)
    {
        onTcpMessage(clientSocket, message);
    }

    if (shouldClose)
    {
        closeClient(clientSocket);
    }
}
```

---

# 19. onTcpMessage 要改什么

原来普通 TCP 回复：

```cpp
std::string response = "server received: " + message + "\n";
queueSend(clientSocket, response);
```

WebSocket 不能直接发裸文本。

要改成：

```cpp
std::string response = "server received: " + message;
queueSend(clientSocket, WebSocket::encodeTextFrame(response));
```

原因：

```text
浏览器只认识 WebSocket frame
不认识你直接 send 的裸字符串
```

---

# 20. queueSend 不用大改

你的 `queueSend` 本质是：

```text
把要发送的数据塞进 outputBuffer
然后让 epoll 监听 EPOLLOUT
```

WebSocket 层只要保证传进去的是：

```text
已经编码好的 WebSocket frame
```

就行。

所以：

```cpp
queueSend(clientSocket, WebSocket::encodeTextFrame(response));
```

---

# 21. CMake 要学什么

WebSocket 握手需要 SHA1。

你可以自己写 SHA1，但是没必要。

直接用 OpenSSL。

Arch 安装：

```fish
sudo pacman -S openssl
```

CMake 里：

```cmake
find_package(OpenSSL REQUIRED)
```

然后链接：

```cmake
target_link_libraries(chat_server
    PRIVATE
        OpenSSL::Crypto
        spdlog::spdlog
)
```

`chat_server` 换成你自己的 target 名。

---

# 22. 你现在要写的函数清单

## WebSocket.hpp

```cpp
#pragma once

#include <cstddef>
#include <cstdint>
#include <string>
#include <vector>

class WebSocket
{
public:
    static bool hasCompleteHandshakeRequest(const std::string& buffer);

    static std::string buildHandshakeResponse(const std::string& request);

    static std::vector<std::string> decodeTextFrames(std::string& buffer, bool& shouldClose);

    static std::string encodeTextFrame(const std::string& message);

private:
    static std::string getHeaderValue(const std::string& request, const std::string& headerName);

    static std::string sha1Base64(const std::string& input);

    static std::string base64Encode(const unsigned char* data, std::size_t length);
};
```

---

## WebSocket.cpp

需要实现：

```text
hasCompleteHandshakeRequest
buildHandshakeResponse
decodeTextFrames
encodeTextFrame
getHeaderValue
sha1Base64
base64Encode
```

---

## AsyncTcpServer.hpp

需要新增：

```cpp
enum class ClientState
{
    WebSocketHandshake,
    WebSocketConnected
};
```

```cpp
void processWebSocketHandshake(int clientSocket);
void processWebSocketFrames(int clientSocket);
```

```cpp
std::unordered_map<int, ClientState> clientStates_;
```

---

## AsyncTcpServer.cpp

需要修改：

```text
handleAccept
closeClient
processInputBuffer
onTcpMessage
```

需要新增：

```text
processWebSocketHandshake
processWebSocketFrames
```

---

# 23. 浏览器测试代码

服务器启动后，打开浏览器控制台：

```js
const ws = new WebSocket("ws://127.0.0.1:2006");

ws.onopen = () => {
  console.log("connected");
  ws.send("hello websocket");
};

ws.onmessage = (event) => {
  console.log("server:", event.data);
};

ws.onclose = () => {
  console.log("closed");
};

ws.onerror = (error) => {
  console.log("error:", error);
};
```

如果成功，浏览器输出：

```text
connected
server: server received: hello websocket
```

服务器日志应该有：

```text
websocket handshake success
received from socket ... : hello websocket
```

---

# 24. 你现在的学习顺序

按照这个顺序学，不要跳。

```text
第一步：
    看懂 HTTP Upgrade 握手

第二步：
    看懂 Sec-WebSocket-Accept 怎么算

第三步：
    看懂 WebSocket frame 的前 2 个字节

第四步：
    看懂 payload length

第五步：
    看懂 mask 解码

第六步：
    写 WebSocket.hpp

第七步：
    写 WebSocket.cpp 的握手部分

第八步：
    接进 AsyncTcpServer，先让浏览器 onopen 成功

第九步：
    写 decodeTextFrames

第十步：
    写 encodeTextFrame

第十一步：
    浏览器 send hello，服务器 echo 回来
```

---

# 25. 最终你要达到的效果

当前阶段成功标准：

```text
浏览器可以连接
浏览器可以发送文本
服务器可以解析文本
服务器可以回复文本
浏览器可以收到回复
```

这个阶段完成后，你才开始写：

```text
ClientManager
广播给其他客户端
聊天室前端页面
```

不要一开始就写广播。

因为如果 WebSocket 单客户端 echo 都没跑通，广播只会更乱。
