# 13 TCP 客户端和服务器阶段总结

## 一、本节目标

到这里，微软官方 Winsock TCP 入门流程已经基本学完。

本节用来整理：

1. TCP 客户端完整流程。
2. TCP 服务器完整流程。
3. 客户端和服务器运行顺序。
4. 目前实验需要掌握到什么程度。
5. 现阶段暂时不需要学习哪些内容。

---

## 二、TCP 客户端完整流程

TCP 客户端的完整流程是：

```text
WSAStartup
↓
getaddrinfo
↓
socket
↓
connect
↓
send
↓
shutdown
↓
recv
↓
closesocket
↓
WSACleanup
```

对应含义如下：

| 步骤            | 作用            |
| ------------- | ------------- |
| `WSAStartup`  | 初始化 Winsock   |
| `getaddrinfo` | 获取服务器地址信息     |
| `socket`      | 创建客户端 Socket  |
| `connect`     | 连接服务器         |
| `send`        | 向服务器发送数据      |
| `shutdown`    | 关闭发送方向        |
| `recv`        | 接收服务器返回的数据    |
| `closesocket` | 关闭客户端 Socket  |
| `WSACleanup`  | 释放 Winsock 资源 |

客户端的核心代码顺序可以记成：

```cpp
WSAStartup(...);

getaddrinfo(...);

connectSocket = socket(...);

connect(connectSocket, ...);

send(connectSocket, ...);

shutdown(connectSocket, SD_SEND);

recv(connectSocket, ...);

closesocket(connectSocket);

WSACleanup();
```

---

## 三、TCP 服务器完整流程

TCP 服务器的完整流程是：

```text
WSAStartup
↓
getaddrinfo
↓
socket
↓
bind
↓
listen
↓
accept
↓
recv
↓
send
↓
shutdown
↓
closesocket
↓
WSACleanup
```

对应含义如下：

| 步骤            | 作用             |
| ------------- | -------------- |
| `WSAStartup`  | 初始化 Winsock    |
| `getaddrinfo` | 获取本机地址信息       |
| `socket`      | 创建服务器监听 Socket |
| `bind`        | 绑定 IP 地址和端口号   |
| `listen`      | 监听客户端连接        |
| `accept`      | 接受客户端连接        |
| `recv`        | 接收客户端数据        |
| `send`        | 向客户端发送数据       |
| `shutdown`    | 关闭发送方向         |
| `closesocket` | 关闭 Socket      |
| `WSACleanup`  | 释放 Winsock 资源  |

服务器核心代码顺序可以记成：

```cpp
WSAStartup(...);

getaddrinfo(NULL, DEFAULT_PORT, ...);

listenSocket = socket(...);

bind(listenSocket, ...);

listen(listenSocket, SOMAXCONN);

clientSocket = accept(listenSocket, NULL, NULL);

recv(clientSocket, ...);

send(clientSocket, ...);

shutdown(clientSocket, SD_SEND);

closesocket(clientSocket);

WSACleanup();
```

---

## 四、客户端和服务器的运行顺序

TCP 程序运行时，必须先启动服务器，再启动客户端。

正确顺序：

```text
1. 启动服务器
2. 服务器 bind 端口
3. 服务器 listen 等待连接
4. 启动客户端
5. 客户端 connect 服务器
6. 服务器 accept 客户端
7. 双方 send / recv
```

如果先启动客户端，可能会出现：

```text
Unable to connect to server
```

原因是：

```text
客户端想连接服务器时，服务器还没有开始监听端口。
```

---

## 五、本机测试用什么 IP

如果客户端和服务器都在同一台电脑上运行，可以使用：

```text
127.0.0.1
```

或者：

```text
localhost
```

例如客户端连接本机服务器：

```cpp
getaddrinfo("127.0.0.1", DEFAULT_PORT, &hints, &result);
```

如果客户端和服务器在两台不同电脑上运行，就要把客户端里的服务器地址改成服务器那台电脑的局域网 IP。

例如：

```cpp
getaddrinfo("192.168.1.10", DEFAULT_PORT, &hints, &result);
```

---

## 六、端口号要保持一致

服务器监听的端口号和客户端连接的端口号必须一致。

例如服务器写：

```cpp
#define DEFAULT_PORT "27015"
```

客户端也应该连接：

```cpp
#define DEFAULT_PORT "27015"
```

如果服务器监听 `27015`，客户端却连接 `8888`，就会连接失败。

---

## 七、单客户端 TCP 程序能完成什么实验内容

学完这些内容后，已经可以完成实验中的：

```text
3.3 TCP通信
```

可以实现：

```text
客户端连接服务器
客户端发送消息
服务器接收消息
服务器返回消息
客户端接收回复
```

也就是最基本的 TCP 客户端和服务器通信。

---

## 八、和 UDP 的区别

TCP 和 UDP 的最大区别是：

```text
TCP 需要连接
UDP 不需要连接
```

TCP 服务器需要：

```text
bind
listen
accept
```

TCP 客户端需要：

```text
connect
```

UDP 没有：

```text
listen
accept
connect
```

UDP 主要使用：

```text
sendto
recvfrom
```

TCP 主要使用：

```text
send
recv
```

---

## 九、和聊天室实验的关系

现在学到的是：

```text
单客户端 TCP 回显服务器
```

聊天室实验需要在这个基础上继续升级。

聊天室服务器需要：

```text
1. 服务器一直 listen
2. accept 多个客户端
3. 每个客户端开一个线程处理
4. 服务器保存所有客户端 socket
5. 收到某个客户端消息后，转发给其他客户端
```

聊天室客户端需要：

```text
1. 主线程负责输入并发送消息
2. 子线程负责接收服务器转发的消息
```

也就是说，聊天室不是新的网络知识，而是在 TCP 基础上加了：

```text
多线程
客户端列表
消息转发
```

---

## 十、现在必须会的内容

现在必须掌握：

```text
WSAStartup
WSACleanup
socket
bind
listen
accept
connect
send
recv
sendto
recvfrom
closesocket
shutdown
getaddrinfo
freeaddrinfo
```

其中 TCP 最核心的是：

```text
服务器：bind → listen → accept → recv/send
客户端：connect → send/recv
```

UDP 最核心的是：

```text
服务器：bind → recvfrom/sendto
客户端：sendto/recvfrom
```

---

## 十一、现在暂时不需要学的内容

下面这些内容现在暂时不需要学：

```text
select
WSAPoll
IOCP
AcceptEx
WSAAccept
非阻塞 Socket
异步 Socket
粘包拆包
心跳包
线程池
高并发服务器
Boost.Asio
Qt 网络模块
```

原因是：

```text
你的当前实验只要求 UDP、TCP、多线程聊天室。
不需要写高并发网络框架。
```

---

## 十二、下一阶段应该做什么

接下来不要继续看太多理论。

应该开始写代码，顺序如下：

```text
1. udpServer.cpp
2. udpClient.cpp
3. tcpServer.cpp
4. tcpClient.cpp
5. chatServer.cpp
6. chatClient.cpp
```

每完成一个程序，就运行一次并截图。

截图可以直接放到实验报告里。

---

## 十三、最终学习路线

推荐学习顺序：

```text
01 服务器和客户端基本概念
02 初始化 Winsock
03 为客户端创建 Socket
04 客户端连接服务器
05 客户端发送和接收数据
06 断开客户端连接
07 为服务器创建 Socket
08 绑定 Socket
09 侦听 Socket
10 接受客户端连接
11 服务器接收和发送数据
12 断开服务器连接
13 TCP 阶段总结
14 UDP 通信代码
15 TCP 单客户端完整代码
16 多线程聊天室
```

到第 13 节为止，微软官方 TCP 基础入门路线已经够用。

后面第 14、15、16 节是为了完成实验，而不是继续照着官方文档抄概念。

