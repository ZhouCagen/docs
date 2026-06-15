# WebSocket 学习清单

## 一、先明确 WebSocket 是什么

WebSocket 不是新的 Linux socket 函数。

底层仍然是 TCP，服务端还是使用：

```cpp
socket()
bind()
listen()
accept()
recv()
send()
close()
```

WebSocket 是建立在 TCP 之上的一层协议。
它解决的是：浏览器前端如何和服务器进行长连接、双向通信。

普通 TCP 程序中，客户端和服务端都是自己写的，所以可以直接发送字符串：

```text
client -> server: hello
server -> client: hello
```

但是浏览器不能直接连接普通 TCP socket。浏览器提供的是 WebSocket API：

```js
const ws = new WebSocket("ws://127.0.0.1:2006")
```

所以 C++ 服务端如果要和浏览器通信，就必须理解 WebSocket 协议。

---

## 二、普通 TCP 和 WebSocket 的区别

### 1. 普通 TCP

普通 TCP 通信流程：

```text
客户端 socket()
客户端 connect()

服务端 socket()
服务端 bind()
服务端 listen()
服务端 accept()

双方 send() / recv()
```

数据内容由程序员自己决定。

例如：

```text
hello
```

服务端收到的也基本就是：

```text
hello
```

---

### 2. WebSocket

WebSocket 通信流程：

```text
浏览器 WebSocket()
        |
        v
C++ socket 服务端 accept()
        |
        v
HTTP Upgrade 握手
        |
        v
WebSocket 数据帧通信
```

WebSocket 多了两个核心步骤：

```text
1. HTTP Upgrade 握手
2. WebSocket Frame 数据帧解析
```

所以服务端不能简单地把 `recv()` 到的数据直接当成聊天内容。

---

## 三、必须学会的 4 个核心点

## 1. HTTP Upgrade 握手

浏览器连接 WebSocket 时，第一次发来的不是聊天消息，而是 HTTP 请求：

```http
GET / HTTP/1.1
Host: 127.0.0.1:2006
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Key: xxxxx
Sec-WebSocket-Version: 13
```

服务端要识别这些字段：

```text
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Key
Sec-WebSocket-Version
```

其中最重要的是：

```text
Sec-WebSocket-Key
```

服务端需要用它计算响应值。

---

## 2. Sec-WebSocket-Accept 计算

浏览器发来：

```http
Sec-WebSocket-Key: xxxxx
```

服务端要把这个 key 和固定字符串拼接：

```text
258EAFA5-E914-47DA-95CA-C5AB0DC85B11
```

然后执行：

```text
SHA1
Base64
```

最终得到：

```http
Sec-WebSocket-Accept: xxxxx
```

服务端返回：

```http
HTTP/1.1 101 Switching Protocols
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Accept: xxxxx
```

返回成功后，浏览器 WebSocket 才会进入 connected 状态。

---

## 3. WebSocket Frame 数据帧

握手完成后，浏览器发消息时，不会直接发送裸字符串。

比如前端写：

```js
ws.send("hello")
```

网络里真正发送的是 WebSocket frame。

基本结构：

```text
FIN + opcode + mask + payload length + masking key + payload data
```

需要重点理解：

```text
FIN：这一帧是不是完整消息的最后一帧
opcode：这一帧是什么类型
mask：浏览器发给服务端的数据必须带 mask
payload length：真实数据长度
masking key：用于还原数据
payload data：真正的数据内容
```

常见 opcode：

```text
0x1：文本帧
0x2：二进制帧
0x8：关闭连接
0x9：ping
0xA：pong
```

本实验主要处理：

```text
0x1 文本帧
0x8 关闭帧
```

---

## 4. Mask 解码

浏览器发给服务端的数据 payload 是被 mask 过的。

服务端需要用 masking key 还原：

```text
真实数据[i] = payload[i] ^ masking_key[i % 4]
```

还原之后，才能得到真正的聊天内容：

```text
hello
```

注意：

```text
浏览器 -> 服务端：必须 mask
服务端 -> 浏览器：不需要 mask
```

---

# 四、C++ 服务端需要写哪些模块

## 1. SocketUtils

负责通用 socket 工具函数。

需要写：

```cpp
bool sendAll(int socketFd, const char* data, size_t length);
bool recvExact(int socketFd, char* data, size_t length);
```

原因：

TCP 是字节流协议，`send()` 和 `recv()` 不保证一次就发送或接收完整数据。

所以必须封装：

```text
sendAll：保证把所有数据都发完
recvExact：保证读够指定字节数
```

---

## 2. WebSocket

负责 WebSocket 协议处理。

需要写：

```cpp
bool performWebSocketHandshake(int clientSocket);
bool receiveTextFrame(int clientSocket, std::string& message);
bool sendTextFrame(int clientSocket, const std::string& message);
```

这三个函数分别对应：

```text
performWebSocketHandshake：完成 HTTP Upgrade 握手
receiveTextFrame：接收并解析浏览器发来的文本帧
sendTextFrame：把字符串封装成 WebSocket 文本帧发给浏览器
```

---

## 3. ClientManager

负责管理多个客户端。

需要保存：

```cpp
std::vector<int> clients;
std::mutex clientsMutex;
```

需要实现：

```cpp
void addClient(int clientSocket);
void removeClient(int clientSocket);
void broadcastMessage(const std::string& message);
```

作用：

```text
客户端连接后加入列表
客户端断开后移除列表
收到某个客户端消息后广播给其他客户端
```

---

## 4. server.cpp

负责主流程。

服务端流程：

```text
1. 创建 TCP socket
2. bind 端口
3. listen 监听
4. accept 客户端连接
5. 每个客户端创建一个线程
6. 在线程中完成 WebSocket 握手
7. 握手成功后加入客户端列表
8. 循环接收 WebSocket 文本帧
9. 收到消息后广播给其他客户端
10. 客户端断开后移除
```

---

# 五、前端需要学什么

前端不需要一开始学复杂 Vue。

先学浏览器原生 WebSocket API：

```js
const ws = new WebSocket("ws://127.0.0.1:2006")

ws.onopen = () => {
  console.log("连接成功")
}

ws.onmessage = (event) => {
  console.log("收到消息:", event.data)
}

ws.onclose = () => {
  console.log("连接关闭")
}

ws.onerror = () => {
  console.log("连接错误")
}

ws.send("hello")
```

等 C++ 服务端能跑通之后，再把这些逻辑放进 Vue 页面里。

---

# 六、推荐实现顺序

## 第 1 步：普通 TCP 服务端

目标：

```text
服务端能 socket / bind / listen / accept
curl 能连接 127.0.0.1:2006
服务端能打印 HTTP 请求
```

完成标志：

```text
服务端能打印 GET / HTTP/1.1
```

---

## 第 2 步：收到浏览器 WebSocket 握手请求

目标：

```text
浏览器控制台执行 new WebSocket("ws://127.0.0.1:2006")
服务端能打印 Upgrade: websocket
服务端能打印 Sec-WebSocket-Key
```

完成标志：

```text
服务端能提取 Sec-WebSocket-Key
```

---

## 第 3 步：完成 WebSocket 握手

目标：

```text
服务端计算 Sec-WebSocket-Accept
服务端返回 101 Switching Protocols
浏览器进入 connected 状态
```

完成标志：

```text
浏览器 ws.onopen 被触发
```

---

## 第 4 步：解析浏览器发来的文本帧

目标：

```text
前端 ws.send("hello")
服务端解析 WebSocket frame
服务端输出 hello
```

完成标志：

```text
服务端能打印真实消息，而不是乱码
```

---

## 第 5 步：服务端发送文本帧给浏览器

目标：

```text
服务端把字符串封装成 WebSocket text frame
浏览器 onmessage 能收到内容
```

完成标志：

```text
浏览器控制台能打印服务端发来的消息
```

---

## 第 6 步：多客户端广播

目标：

```text
浏览器 A 发送消息
服务端转发给浏览器 B
浏览器 B 显示消息
```

完成标志：

```text
至少两个客户端能互相通信
```

---

## 第 7 步：Vue 页面

目标：

```text
输入服务器 IP
输入端口
输入昵称
点击连接
输入消息
显示聊天记录
显示连接状态
```

完成标志：

```text
有完整前端界面
可以截图写实验报告
```

---

# 七、这个实验最终应该体现什么

最终项目要体现：

```text
1. 使用 C++ Linux socket 编程
2. 服务端处于监听状态
3. 客户端通过 IP 和端口连接服务器
4. 支持至少两个客户端通信
5. 使用 WebSocket 协议连接浏览器前端
6. 前端使用 Vue 实现聊天界面
7. 服务端支持多线程处理多个客户端
8. 服务端支持消息广播
```

一句话总结：

```text
本实验不是简单使用现成 WebSocket 库，而是基于 Linux TCP socket 手动实现 WebSocket 握手、数据帧解析和多客户端消息广播。
```

