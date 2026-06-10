# Linux Socket API 速查表

## 一、本项目使用的技术栈

本项目运行在 Arch Linux 上，因此使用的是 **Linux / POSIX Socket API**，不是 Windows Winsock。

主要区别：

| 内容        | Linux / POSIX Socket        | Windows Winsock   |
| --------- | --------------------------- | ----------------- |
| 初始化网络库    | 不需要                         | `WSAStartup`      |
| 清理网络库     | 不需要                         | `WSACleanup`      |
| 关闭 socket | `close`                     | `closesocket`     |
| 错误原因      | `errno` / `strerror(errno)` | `WSAGetLastError` |
| UDP 发送    | `sendto`                    | `sendto`          |
| UDP 接收    | `recvfrom`                  | `recvfrom`        |
| TCP 发送    | `send`                      | `send`            |
| TCP 接收    | `recv`                      | `recv`            |

---

## 二、常用头文件

UDP、TCP 都会用到这些头文件：

```cpp
#include <arpa/inet.h>
#include <netinet/in.h>
#include <sys/socket.h>
#include <unistd.h>

#include <cerrno>
#include <cstdlib>
#include <cstring>
#include <string>
#include <vector>
#include <thread>
#include <mutex>

#include <spdlog/spdlog.h>
```

作用如下：

| 头文件               | 作用                                                                            |
| ----------------- | ----------------------------------------------------------------------------- |
| `sys/socket.h`    | `socket`、`bind`、`listen`、`accept`、`connect`、`send`、`recv`、`sendto`、`recvfrom` |
| `netinet/in.h`    | `sockaddr_in`、`htons`、`ntohs`、`INADDR_ANY`                                    |
| `arpa/inet.h`     | `inet_pton`、`inet_ntop`                                                       |
| `unistd.h`        | `close`                                                                       |
| `cerrno`          | `errno`                                                                       |
| `cstring`         | `strerror`、`strlen`、`memset`                                                  |
| `cstdlib`         | `EXIT_SUCCESS`、`EXIT_FAILURE`                                                 |
| `string`          | `std::string`                                                                 |
| `vector`          | 保存多个客户端 socket                                                                |
| `thread`          | 多线程                                                                           |
| `mutex`           | 互斥锁，保护共享数据                                                                    |
| `spdlog/spdlog.h` | 日志输出                                                                          |

---

# 三、基础类型

## 1. `int`

Linux 下 socket 本质上是一个文件描述符，类型是 `int`。

例如：

```cpp
int serverSocket = socket(AF_INET, SOCK_DGRAM, 0);
```

如果成功，返回一个非负整数，例如：

```text
3
4
5
```

如果失败，返回：

```text
-1
```

---

## 2. `ssize_t`

`ssize_t` 是有符号整数类型，经常用于表示发送或接收的字节数。

例如：

```cpp
ssize_t recvLen = recvfrom(...);
```

返回值含义：

| 返回值   | 含义              |
| ----- | --------------- |
| `> 0` | 成功发送或接收的字节数     |
| `0`   | TCP 中通常表示对方关闭连接 |
| `-1`  | 出错              |

---

## 3. `socklen_t`

`socklen_t` 用来表示 socket 地址结构的长度。

例如：

```cpp
socklen_t clientAddrLen = sizeof(clientAddr);
```

常用于：

```cpp
recvfrom
accept
getsockname
```

---

# 四、常用宏和常量

## 1. `AF_INET`

表示使用 IPv4。

```cpp
AF_INET
```

常见用法：

```cpp
socket(AF_INET, SOCK_DGRAM, 0);
```

---

## 2. `SOCK_DGRAM`

表示 UDP。

```cpp
SOCK_DGRAM
```

UDP 创建 socket：

```cpp
socket(AF_INET, SOCK_DGRAM, 0);
```

---

## 3. `SOCK_STREAM`

表示 TCP。

```cpp
SOCK_STREAM
```

TCP 创建 socket：

```cpp
socket(AF_INET, SOCK_STREAM, 0);
```

---

## 4. `INADDR_ANY`

表示绑定本机所有 IP 地址。

服务端常用：

```cpp
serverAddr.sin_addr.s_addr = INADDR_ANY;
```

意思是：

```text
不指定某一个 IP，本机所有网卡收到这个端口的数据都可以交给该程序处理。
```

---

## 5. `EXIT_SUCCESS`

表示程序正常结束。

```cpp
return EXIT_SUCCESS;
```

通常等价于：

```cpp
return 0;
```

---

## 6. `EXIT_FAILURE`

表示程序异常结束。

```cpp
return EXIT_FAILURE;
```

通常比直接写 `return 1;` 更语义化。

---

# 五、核心结构体

## 1. `sockaddr`

`sockaddr` 是通用 socket 地址结构。

很多 socket 函数参数需要：

```cpp
sockaddr*
```

例如：

```cpp
bind(int sockfd, const sockaddr* addr, socklen_t addrlen);
```

但是我们写 IPv4 程序时，通常不直接填写 `sockaddr`。

---

## 2. `sockaddr_in`

`sockaddr_in` 是 IPv4 专用地址结构。

UDP / TCP IPv4 程序中最常见。

```cpp
sockaddr_in serverAddr{};
```

常用成员：

| 成员                | 含义                   |
| ----------------- | -------------------- |
| `sin_family`      | 地址族，IPv4 写 `AF_INET` |
| `sin_addr.s_addr` | IP 地址                |
| `sin_port`        | 端口号                  |

服务端常见写法：

```cpp
sockaddr_in serverAddr{};

serverAddr.sin_family = AF_INET;
serverAddr.sin_addr.s_addr = INADDR_ANY;
serverAddr.sin_port = htons(8888);
```

客户端常见写法：

```cpp
sockaddr_in serverAddr{};

serverAddr.sin_family = AF_INET;
serverAddr.sin_port = htons(8888);
inet_pton(AF_INET, "127.0.0.1", &serverAddr.sin_addr);
```

---

## 3. 为什么要把 `sockaddr_in*` 转成 `sockaddr*`

很多 socket 函数参数要求的是：

```cpp
sockaddr*
```

但是我们实际写的是：

```cpp
sockaddr_in
```

所以需要强转：

```cpp
reinterpret_cast<sockaddr*>(&serverAddr)
```

例如：

```cpp
bind(
    serverSocket,
    reinterpret_cast<sockaddr*>(&serverAddr),
    sizeof(serverAddr)
);
```

原因是：

```text
sockaddr 是通用地址结构。
sockaddr_in 是 IPv4 地址结构。
socket API 为了兼容 IPv4、IPv6 等多种地址类型，所以统一接收 sockaddr*。
```

---

# 六、字节序函数

## 1. `htons`

函数名含义：

```text
host to network short
```

作用：

```text
把主机字节序转换成网络字节序。
```

端口号放进 `sockaddr_in` 前必须使用 `htons`。

```cpp
serverAddr.sin_port = htons(8888);
```

不要直接写：

```cpp
serverAddr.sin_port = 8888;
```

---

## 2. `ntohs`

函数名含义：

```text
network to host short
```

作用：

```text
把网络字节序转换回主机字节序。
```

常用于打印客户端端口：

```cpp
spdlog::info("client port: {}", ntohs(clientAddr.sin_port));
```

---

# 七、IP 地址转换函数

## 1. `inet_pton`

函数名含义：

```text
presentation to network
```

作用：

```text
把字符串 IP 转换成网络地址。
```

常用于客户端设置服务器 IP。

函数形式：

```cpp
int inet_pton(int af, const char* src, void* dst);
```

常见用法：

```cpp
int ipResult = inet_pton(AF_INET, "127.0.0.1", &serverAddr.sin_addr);

if (ipResult <= 0)
{
    spdlog::error("inet_pton failed: {}", strerror(errno));
    close(clientSocket);
    return EXIT_FAILURE;
}
```

参数：

| 参数                     | 含义           |
| ---------------------- | ------------ |
| `AF_INET`              | IPv4         |
| `"127.0.0.1"`          | 字符串 IP       |
| `&serverAddr.sin_addr` | 转换后的网络地址存放位置 |

返回值：

| 返回值  | 含义      |
| ---- | ------- |
| `1`  | 成功      |
| `0`  | IP 格式错误 |
| `-1` | 系统错误    |

---

## 2. `inet_ntop`

函数名含义：

```text
network to presentation
```

作用：

```text
把网络地址转换成字符串 IP。
```

常用于服务端打印客户端 IP。

函数形式：

```cpp
const char* inet_ntop(int af, const void* src, char* dst, socklen_t size);
```

常见用法：

```cpp
char clientIp[INET_ADDRSTRLEN];

inet_ntop(
    AF_INET,
    &clientAddr.sin_addr,
    clientIp,
    sizeof(clientIp)
);

spdlog::info("client ip: {}", clientIp);
```

参数：

| 参数                     | 含义          |
| ---------------------- | ----------- |
| `AF_INET`              | IPv4        |
| `&clientAddr.sin_addr` | 网络地址        |
| `clientIp`             | 转换后的字符串保存位置 |
| `sizeof(clientIp)`     | 缓冲区大小       |

---

## 3. `INET_ADDRSTRLEN`

IPv4 字符串地址缓冲区大小。

常见写法：

```cpp
char clientIp[INET_ADDRSTRLEN];
```

它足够保存：

```text
255.255.255.255
```

---

# 八、错误处理

## 1. `errno`

`errno` 是系统调用失败时保存错误编号的变量。

例如：

```cpp
int bindResult = bind(...);

if (bindResult == -1)
{
    spdlog::error("bind failed: {}", strerror(errno));
}
```

当 `bind` 失败时，系统会设置 `errno`。

---

## 2. `strerror`

`strerror` 用来把 `errno` 转成人能看懂的错误信息。

需要头文件：

```cpp
#include <cstring>
```

用法：

```cpp
strerror(errno)
```

例如：

```cpp
spdlog::error("socket failed: {}", strerror(errno));
```

输出示例：

```text
[error] socket failed: Address family not supported by protocol
```

---

## 3. 系统调用失败判断规律

Linux socket 函数常见失败返回值：

| 函数         | 成功         | 失败   |
| ---------- | ---------- | ---- |
| `socket`   | 非负 fd      | `-1` |
| `bind`     | `0`        | `-1` |
| `listen`   | `0`        | `-1` |
| `accept`   | 非负 fd      | `-1` |
| `connect`  | `0`        | `-1` |
| `send`     | 发送的字节数     | `-1` |
| `recv`     | 接收的字节数，或 0 | `-1` |
| `sendto`   | 发送的字节数     | `-1` |
| `recvfrom` | 接收的字节数     | `-1` |
| `close`    | `0`        | `-1` |

---

# 九、spdlog 日志函数

## 1. 常用等级

```cpp
spdlog::debug("debug message");
spdlog::info("normal message");
spdlog::warn("warning message");
spdlog::error("error message");
spdlog::critical("critical message");
```

含义：

| 函数         | 用途     |
| ---------- | ------ |
| `debug`    | 调试细节   |
| `info`     | 正常运行信息 |
| `warn`     | 警告     |
| `error`    | 错误     |
| `critical` | 严重错误   |

---

## 2. 带变量输出

spdlog 使用 `{}` 占位。

```cpp
int port = 8888;

spdlog::info("server started, port {}", port);
```

多个变量：

```cpp
spdlog::info("client [{}:{}] connected", clientIp, clientPort);
```

---

## 3. 打印系统错误

推荐写法：

```cpp
spdlog::error("bind failed: {}", strerror(errno));
```

完整例子：

```cpp
int bindResult = bind(
    serverSocket,
    reinterpret_cast<sockaddr*>(&serverAddr),
    sizeof(serverAddr)
);

if (bindResult == -1)
{
    spdlog::error("bind failed: {}", strerror(errno));
    close(serverSocket);
    return EXIT_FAILURE;
}
```

---

# 十、UDP 相关函数

## 1. `socket`

作用：

```text
创建 socket。
```

UDP 创建方式：

```cpp
int serverSocket = socket(AF_INET, SOCK_DGRAM, 0);
```

参数：

| 参数           | 含义     |
| ------------ | ------ |
| `AF_INET`    | IPv4   |
| `SOCK_DGRAM` | UDP    |
| `0`          | 自动选择协议 |

返回值：

| 返回值  | 含义              |
| ---- | --------------- |
| 非负整数 | 成功，返回 socket fd |
| `-1` | 失败              |

错误处理：

```cpp
if (serverSocket == -1)
{
    spdlog::error("socket failed: {}", strerror(errno));
    return EXIT_FAILURE;
}
```

---

## 2. `bind`

作用：

```text
把 socket 绑定到本机 IP 和端口。
```

服务端必须绑定端口。

函数形式：

```cpp
int bind(int sockfd, const sockaddr* addr, socklen_t addrlen);
```

常见用法：

```cpp
int bindResult = bind(
    serverSocket,
    reinterpret_cast<sockaddr*>(&serverAddr),
    sizeof(serverAddr)
);
```

参数：

| 参数                   | 含义          |
| -------------------- | ----------- |
| `serverSocket`       | 要绑定的 socket |
| `serverAddr`         | IP 和端口      |
| `sizeof(serverAddr)` | 地址结构大小      |

返回值：

| 返回值  | 含义 |
| ---- | -- |
| `0`  | 成功 |
| `-1` | 失败 |

---

## 3. `recvfrom`

作用：

```text
接收 UDP 数据，并获取发送方地址。
```

函数形式：

```cpp
ssize_t recvfrom(
    int sockfd,
    void* buf,
    size_t len,
    int flags,
    sockaddr* srcAddr,
    socklen_t* addrlen
);
```

服务端常见用法：

```cpp
char buffer[1024];

sockaddr_in clientAddr{};
socklen_t clientAddrLen = sizeof(clientAddr);

ssize_t recvLen = recvfrom(
    serverSocket,
    buffer,
    sizeof(buffer) - 1,
    0,
    reinterpret_cast<sockaddr*>(&clientAddr),
    &clientAddrLen
);
```

参数：

| 参数                   | 含义                      |
| -------------------- | ----------------------- |
| `serverSocket`       | 接收数据的 socket            |
| `buffer`             | 接收缓冲区                   |
| `sizeof(buffer) - 1` | 最多接收的字节数，预留一个位置给 `'\0'` |
| `0`                  | 标志位，通常写 0               |
| `clientAddr`         | 保存发送方地址                 |
| `clientAddrLen`      | 地址结构长度                  |

返回值：

| 返回值   | 含义        |
| ----- | --------- |
| `> 0` | 接收到的字节数   |
| `0`   | 收到 0 字节数据 |
| `-1`  | 失败        |

接收到字符串后：

```cpp
buffer[recvLen] = '\0';
```

---

## 4. `sendto`

作用：

```text
向指定地址发送 UDP 数据。
```

函数形式：

```cpp
ssize_t sendto(
    int sockfd,
    const void* buf,
    size_t len,
    int flags,
    const sockaddr* destAddr,
    socklen_t addrlen
);
```

常见用法：

```cpp
std::string reply = "Server received: ";
reply += buffer;

ssize_t sendLen = sendto(
    serverSocket,
    reply.c_str(),
    reply.size(),
    0,
    reinterpret_cast<sockaddr*>(&clientAddr),
    clientAddrLen
);
```

参数：

| 参数              | 含义           |
| --------------- | ------------ |
| `serverSocket`  | 发送数据的 socket |
| `reply.c_str()` | 要发送的数据       |
| `reply.size()`  | 发送的数据长度      |
| `0`             | 标志位，通常写 0    |
| `clientAddr`    | 目标地址         |
| `clientAddrLen` | 目标地址结构长度     |

返回值：

| 返回值    | 含义       |
| ------ | -------- |
| `>= 0` | 实际发送的字节数 |
| `-1`   | 失败       |

---

# 十一、TCP 相关函数

## 1. TCP 创建 socket

TCP 使用：

```cpp
int listenSocket = socket(AF_INET, SOCK_STREAM, 0);
```

和 UDP 的区别是：

```cpp
SOCK_STREAM
```

表示 TCP。

---

## 2. `listen`

作用：

```text
让服务端 socket 进入监听状态。
```

函数形式：

```cpp
int listen(int sockfd, int backlog);
```

常见用法：

```cpp
int listenResult = listen(listenSocket, SOMAXCONN);
```

参数：

| 参数             | 含义                 |
| -------------- | ------------------ |
| `listenSocket` | 已经绑定端口的 TCP socket |
| `SOMAXCONN`    | 等待连接队列长度           |

返回值：

| 返回值  | 含义 |
| ---- | -- |
| `0`  | 成功 |
| `-1` | 失败 |

---

## 3. `accept`

作用：

```text
接受客户端 TCP 连接。
```

函数形式：

```cpp
int accept(int sockfd, sockaddr* addr, socklen_t* addrlen);
```

常见用法：

```cpp
sockaddr_in clientAddr{};
socklen_t clientAddrLen = sizeof(clientAddr);

int clientSocket = accept(
    listenSocket,
    reinterpret_cast<sockaddr*>(&clientAddr),
    &clientAddrLen
);
```

返回值：

| 返回值   | 含义                     |
| ----- | ---------------------- |
| 非负 fd | 成功，返回用于和客户端通信的新 socket |
| `-1`  | 失败                     |

注意：

```text
listenSocket 负责等待连接。
clientSocket 负责和某一个客户端通信。
```

---

## 4. `connect`

作用：

```text
客户端主动连接服务器。
```

函数形式：

```cpp
int connect(int sockfd, const sockaddr* addr, socklen_t addrlen);
```

常见用法：

```cpp
int connectResult = connect(
    clientSocket,
    reinterpret_cast<sockaddr*>(&serverAddr),
    sizeof(serverAddr)
);
```

返回值：

| 返回值  | 含义 |
| ---- | -- |
| `0`  | 成功 |
| `-1` | 失败 |

---

## 5. `send`

作用：

```text
TCP 发送数据。
```

函数形式：

```cpp
ssize_t send(int sockfd, const void* buf, size_t len, int flags);
```

常见用法：

```cpp
std::string message = "hello";

ssize_t sendLen = send(
    clientSocket,
    message.c_str(),
    message.size(),
    0
);
```

返回值：

| 返回值   | 含义       |
| ----- | -------- |
| `> 0` | 实际发送的字节数 |
| `0`   | 发送 0 字节  |
| `-1`  | 失败       |

---

## 6. `recv`

作用：

```text
TCP 接收数据。
```

函数形式：

```cpp
ssize_t recv(int sockfd, void* buf, size_t len, int flags);
```

常见用法：

```cpp
char buffer[1024];

ssize_t recvLen = recv(
    clientSocket,
    buffer,
    sizeof(buffer) - 1,
    0
);
```

返回值：

| 返回值   | 含义      |
| ----- | ------- |
| `> 0` | 接收到的字节数 |
| `0`   | 对方关闭连接  |
| `-1`  | 失败      |

接收字符串后：

```cpp
buffer[recvLen] = '\0';
```

---

# 十二、关闭 socket

## 1. `close`

作用：

```text
关闭 socket。
```

函数形式：

```cpp
int close(int fd);
```

常见用法：

```cpp
close(serverSocket);
```

返回值：

| 返回值  | 含义 |
| ---- | -- |
| `0`  | 成功 |
| `-1` | 失败 |

一般实验中关闭失败不重点处理。

---

## 2. `shutdown`

TCP 中可以使用 `shutdown` 半关闭连接。

函数形式：

```cpp
int shutdown(int sockfd, int how);
```

常见用法：

```cpp
shutdown(clientSocket, SHUT_WR);
```

常用参数：

| 参数          | 含义     |
| ----------- | ------ |
| `SHUT_RD`   | 关闭读方向  |
| `SHUT_WR`   | 关闭写方向  |
| `SHUT_RDWR` | 关闭读写方向 |

实验中可以先不重点使用 `shutdown`，直接 `close` 也能完成基本通信。

---

# 十三、多线程聊天室相关内容

## 1. `std::thread`

用于创建线程。

```cpp
std::thread clientThread(handleClient, clientSocket);
clientThread.detach();
```

含义：

```text
创建一个线程去执行 handleClient(clientSocket)。
```

---

## 2. `std::mutex`

用于保护共享数据。

例如服务器保存多个客户端：

```cpp
std::vector<int> clientSockets;
std::mutex clientsMutex;
```

多个线程同时访问 `clientSockets` 时，需要加锁。

---

## 3. `std::lock_guard`

自动加锁和解锁。

```cpp
{
    std::lock_guard<std::mutex> lock(clientsMutex);
    clientSockets.push_back(clientSocket);
}
```

作用：

```text
进入作用域时自动加锁。
离开作用域时自动解锁。
```

---

## 4. `std::vector<int>`

用于保存所有客户端 socket。

```cpp
std::vector<int> clientSockets;
```

添加客户端：

```cpp
clientSockets.push_back(clientSocket);
```

转发消息：

```cpp
for (int socketFd : clientSockets)
{
    if (socketFd != senderSocket)
    {
        send(socketFd, message.c_str(), message.size(), 0);
    }
}
```

---

# 十四、UDP 服务端最小流程

```cpp
int serverSocket = socket(AF_INET, SOCK_DGRAM, 0);

sockaddr_in serverAddr{};
serverAddr.sin_family = AF_INET;
serverAddr.sin_addr.s_addr = INADDR_ANY;
serverAddr.sin_port = htons(8888);

bind(
    serverSocket,
    reinterpret_cast<sockaddr*>(&serverAddr),
    sizeof(serverAddr)
);

char buffer[1024];

sockaddr_in clientAddr{};
socklen_t clientAddrLen = sizeof(clientAddr);

ssize_t recvLen = recvfrom(
    serverSocket,
    buffer,
    sizeof(buffer) - 1,
    0,
    reinterpret_cast<sockaddr*>(&clientAddr),
    &clientAddrLen
);

buffer[recvLen] = '\0';

sendto(
    serverSocket,
    buffer,
    recvLen,
    0,
    reinterpret_cast<sockaddr*>(&clientAddr),
    clientAddrLen
);

close(serverSocket);
```

---

# 十五、UDP 客户端最小流程

```cpp
int clientSocket = socket(AF_INET, SOCK_DGRAM, 0);

sockaddr_in serverAddr{};
serverAddr.sin_family = AF_INET;
serverAddr.sin_port = htons(8888);

inet_pton(AF_INET, "127.0.0.1", &serverAddr.sin_addr);

std::string message = "hello";

sendto(
    clientSocket,
    message.c_str(),
    message.size(),
    0,
    reinterpret_cast<sockaddr*>(&serverAddr),
    sizeof(serverAddr)
);

char buffer[1024];

sockaddr_in fromAddr{};
socklen_t fromAddrLen = sizeof(fromAddr);

ssize_t recvLen = recvfrom(
    clientSocket,
    buffer,
    sizeof(buffer) - 1,
    0,
    reinterpret_cast<sockaddr*>(&fromAddr),
    &fromAddrLen
);

buffer[recvLen] = '\0';

close(clientSocket);
```

---

# 十六、TCP 服务端最小流程

```cpp
int listenSocket = socket(AF_INET, SOCK_STREAM, 0);

sockaddr_in serverAddr{};
serverAddr.sin_family = AF_INET;
serverAddr.sin_addr.s_addr = INADDR_ANY;
serverAddr.sin_port = htons(8888);

bind(
    listenSocket,
    reinterpret_cast<sockaddr*>(&serverAddr),
    sizeof(serverAddr)
);

listen(listenSocket, SOMAXCONN);

sockaddr_in clientAddr{};
socklen_t clientAddrLen = sizeof(clientAddr);

int clientSocket = accept(
    listenSocket,
    reinterpret_cast<sockaddr*>(&clientAddr),
    &clientAddrLen
);

char buffer[1024];

ssize_t recvLen = recv(
    clientSocket,
    buffer,
    sizeof(buffer) - 1,
    0
);

buffer[recvLen] = '\0';

send(
    clientSocket,
    buffer,
    recvLen,
    0
);

close(clientSocket);
close(listenSocket);
```

---

# 十七、TCP 客户端最小流程

```cpp
int clientSocket = socket(AF_INET, SOCK_STREAM, 0);

sockaddr_in serverAddr{};
serverAddr.sin_family = AF_INET;
serverAddr.sin_port = htons(8888);

inet_pton(AF_INET, "127.0.0.1", &serverAddr.sin_addr);

connect(
    clientSocket,
    reinterpret_cast<sockaddr*>(&serverAddr),
    sizeof(serverAddr)
);

std::string message = "hello";

send(
    clientSocket,
    message.c_str(),
    message.size(),
    0
);

char buffer[1024];

ssize_t recvLen = recv(
    clientSocket,
    buffer,
    sizeof(buffer) - 1,
    0
);

buffer[recvLen] = '\0';

close(clientSocket);
```

---

# 十八、必须记住的核心区别

## UDP

```text
服务端：socket → bind → recvfrom → sendto → close
客户端：socket → sendto → recvfrom → close
```

特点：

```text
不需要 listen
不需要 accept
不需要 connect
```

---

## TCP

```text
服务端：socket → bind → listen → accept → recv/send → close
客户端：socket → connect → send/recv → close
```

特点：

```text
通信前必须建立连接。
服务端用 accept 得到 clientSocket。
后续收发数据用 clientSocket，不是 listenSocket。
```

---

# 十九、写代码时的错误处理模板

## 1. 创建 socket

```cpp
int socketFd = socket(AF_INET, SOCK_DGRAM, 0);

if (socketFd == -1)
{
    spdlog::error("socket failed: {}", strerror(errno));
    return EXIT_FAILURE;
}
```

---

## 2. bind

```cpp
if (bind(socketFd, reinterpret_cast<sockaddr*>(&addr), sizeof(addr)) == -1)
{
    spdlog::error("bind failed: {}", strerror(errno));
    close(socketFd);
    return EXIT_FAILURE;
}
```

---

## 3. recvfrom

```cpp
ssize_t recvLen = recvfrom(...);

if (recvLen == -1)
{
    spdlog::error("recvfrom failed: {}", strerror(errno));
}
```

---

## 4. sendto

```cpp
ssize_t sendLen = sendto(...);

if (sendLen == -1)
{
    spdlog::error("sendto failed: {}", strerror(errno));
}
```

---

## 5. recv

```cpp
ssize_t recvLen = recv(...);

if (recvLen == -1)
{
    spdlog::error("recv failed: {}", strerror(errno));
}
else if (recvLen == 0)
{
    spdlog::info("connection closed");
}
```

---

## 6. send

```cpp
ssize_t sendLen = send(...);

if (sendLen == -1)
{
    spdlog::error("send failed: {}", strerror(errno));
}
```

---

# 二十、本节小结

写本实验最重要的 API 有：

```text
socket
bind
listen
accept
connect
send
recv
sendto
recvfrom
close
htons
ntohs
inet_pton
inet_ntop
strerror
```

最重要的结构体是：

```text
sockaddr
sockaddr_in
```

最重要的成员是：

```text
sin_family
sin_addr.s_addr
sin_port
```

最重要的错误处理方式是：

```cpp
if (result == -1)
{
    spdlog::error("xxx failed: {}", strerror(errno));
    return EXIT_FAILURE;
}
```

最重要的两条流程是：

```text
UDP 服务端：socket → bind → recvfrom → sendto
UDP 客户端：socket → sendto → recvfrom
```

```text
TCP 服务端：socket → bind → listen → accept → recv/send
TCP 客户端：socket → connect → send/recv
```

