# TCP 通信

## 一、TCP 是什么

TCP，全称是 **Transmission Control Protocol**，中文叫**传输控制协议**。

TCP 的特点是：

* 通信前需要先建立连接。
* 数据传输可靠。
* 能保证数据按顺序到达。
* 如果数据丢失，TCP 会进行重传。
* TCP 是面向字节流的协议。
* 程序结构比 UDP 稍复杂。

可以简单理解为：

```text
TCP 像打电话：
先拨号建立连接，连接成功后双方才能持续通信。
```

和 UDP 相比：

```text
UDP：不建立连接，直接发送数据。
TCP：先建立连接，再进行数据收发。
```

---

## 二、TCP 服务端和客户端的区别

TCP 通信中，服务端和客户端的流程比 UDP 更明显。

### 1. TCP 服务端

TCP 服务端要做的事情是：

```text
创建 socket
↓
绑定端口
↓
监听连接
↓
等待客户端连接
↓
接收客户端数据
↓
回复客户端
↓
关闭连接
```

TCP 服务端必须先绑定端口，并进入监听状态。客户端连接服务端后，服务端通过 `accept` 接受连接，然后才能和客户端通信。

TCP 服务端中通常会出现两个 socket：

```text
serverSocket：监听 socket，只负责等待客户端连接
clientSocket：通信 socket，负责和客户端 recv/send
```

这是 TCP 和 UDP 很大的区别。

---

### 2. TCP 客户端

TCP 客户端要做的事情是：

```text
创建 socket
↓
指定服务器 IP 和端口
↓
连接服务器
↓
发送数据
↓
接收服务器回复
↓
关闭 socket
```

TCP 客户端需要使用 `connect` 主动连接服务器。

连接成功后，客户端和服务端之间就建立了一条 TCP 连接，之后发送和接收数据时不需要每次都指定对方地址。

---

## 三、Linux Socket 和 Winsock 的区别

本实验在 Arch Linux 上完成，所以使用的是 **Linux / POSIX Socket**，不是 Windows Winsock。

主要区别如下：

| 功能        | Windows Winsock   | Linux / POSIX Socket         |
| --------- | ----------------- | ---------------------------- |
| 初始化网络库    | `WSAStartup`      | 不需要                          |
| 清理网络库     | `WSACleanup`      | 不需要                          |
| 关闭 socket | `closesocket`     | `close`                      |
| 错误输出      | `WSAGetLastError` | `strerror(errno)` / `perror` |
| TCP 发送    | `send`            | `send`                       |
| TCP 接收    | `recv`            | `recv`                       |

在 Linux 下，不需要写：

```cpp
WSAStartup();
WSACleanup();
```

直接创建 socket 即可。

---

## 四、TCP 程序需要的头文件

TCP 服务端和客户端都会用到这些头文件：

```cpp
#include <arpa/inet.h>
#include <netinet/in.h>
#include <sys/socket.h>
#include <unistd.h>

#include <cerrno>
#include <cstddef>
#include <cstdint>
#include <cstdlib>
#include <cstring>
#include <spdlog/spdlog.h>
#include <string>
```

客户端还需要输入输出，所以还需要：

```cpp
#include <iostream>
```

作用如下：

| 头文件               | 作用                                                           |
| ----------------- | ------------------------------------------------------------ |
| `sys/socket.h`    | 提供 `socket`、`bind`、`listen`、`accept`、`connect`、`send`、`recv` |
| `netinet/in.h`    | 提供 `sockaddr_in`、`htons`、`INADDR_ANY`                        |
| `arpa/inet.h`     | 提供 `inet_pton`、`inet_ntop` 等 IP 地址转换函数                       |
| `unistd.h`        | 提供 `close`                                                   |
| `cerrno`          | 提供 `errno`                                                   |
| `cstring`         | 提供 `strerror`                                                |
| `cstdint`         | 提供 `uint16_t`                                                |
| `cstddef`         | 提供 `size_t`                                                  |
| `iostream`        | 提供 `cin`、`cout`                                              |
| `string`          | 提供 `std::string`                                             |
| `spdlog/spdlog.h` | 提供日志输出功能                                                     |

---

## 五、TCP 服务端核心函数

TCP 服务端主要使用这些函数：

| 函数       | 作用              |
| -------- | --------------- |
| `socket` | 创建 socket       |
| `bind`   | 绑定 IP 和端口       |
| `listen` | 让 socket 进入监听状态 |
| `accept` | 接受客户端连接         |
| `recv`   | 接收客户端发送的数据      |
| `send`   | 向客户端发送回复        |
| `close`  | 关闭 socket       |

服务端核心流程：

```text
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
close
```

其中：

```text
bind：绑定服务端端口
listen：开始监听客户端连接
accept：真正接受一个客户端连接
```

---

## 六、TCP 客户端核心函数

TCP 客户端主要使用这些函数：

| 函数          | 作用              |
| ----------- | --------------- |
| `socket`    | 创建 socket       |
| `inet_pton` | 把字符串 IP 转换为网络地址 |
| `connect`   | 连接服务器           |
| `send`      | 向服务器发送数据        |
| `recv`      | 接收服务器回复         |
| `close`     | 关闭 socket       |

客户端核心流程：

```text
socket
↓
inet_pton
↓
connect
↓
send
↓
recv
↓
close
```

---

# 七、TCP 服务端代码讲解

服务端文件：

```text
src/tcp/tcpServer.cpp
```

## 1. 创建 TCP socket

```cpp
int serverSocket = socket(AF_INET, SOCK_STREAM, 0);
```

参数含义：

| 参数            | 含义          |
| ------------- | ----------- |
| `AF_INET`     | 使用 IPv4     |
| `SOCK_STREAM` | 使用 TCP      |
| `0`           | 让系统自动选择对应协议 |

UDP 创建 socket 时使用的是：

```cpp
SOCK_DGRAM
```

TCP 创建 socket 时使用的是：

```cpp
SOCK_STREAM
```

如果创建失败，返回 `-1`。

---

## 2. 设置端口复用

```cpp
int opt = 1;

setsockopt(
    serverSocket,
    SOL_SOCKET,
    SO_REUSEADDR,
    &opt,
    sizeof(opt)
);
```

`SO_REUSEADDR` 的作用是允许服务端程序退出后较快重新绑定同一个端口。

如果不设置，有时候程序刚退出又马上重新运行，可能会出现端口占用问题。

---

## 3. 准备服务器地址

```cpp
sockaddr_in serverAddr{};

serverAddr.sin_family = AF_INET;
serverAddr.sin_addr.s_addr = INADDR_ANY;
serverAddr.sin_port = htons(port);
```

解释：

| 字段                | 含义            |
| ----------------- | ------------- |
| `sin_family`      | 地址族，这里使用 IPv4 |
| `sin_addr.s_addr` | 绑定哪个 IP       |
| `sin_port`        | 绑定哪个端口        |

其中：

```cpp
INADDR_ANY
```

表示绑定本机所有 IP 地址。

```cpp
htons(port)
```

表示把端口号转换为网络字节序。

---

## 4. 绑定端口

```cpp
int bindResult = bind(
    serverSocket,
    reinterpret_cast<sockaddr*>(&serverAddr),
    static_cast<socklen_t>(sizeof(serverAddr))
);
```

`bind` 的作用是：

```text
把 serverSocket 绑定到指定 IP 和端口。
```

如果绑定失败，返回 `-1`。

常见失败原因：

* 端口已经被其他程序占用。
* 上一次服务端程序没有正常退出。
* 当前用户没有权限绑定某些特殊端口。

实验中使用端口：

```text
2006
```

---

## 5. 监听客户端连接

```cpp
int listenResult = listen(serverSocket, SOMAXCONN);
```

`listen` 的作用是：

```text
让服务端 socket 进入监听状态，开始等待客户端连接。
```

`SOMAXCONN` 表示使用系统允许的最大连接等待队列长度。

TCP 服务端必须先 `listen`，然后才能 `accept` 客户端连接。

---

## 6. 接受客户端连接

```cpp
int clientSocket = accept(
    serverSocket,
    reinterpret_cast<sockaddr*>(&clientAddr),
    &clientAddrLen
);
```

`accept` 的作用是：

```text
从监听队列中取出一个客户端连接，并返回一个新的 socket。
```

这个新的 socket 就是：

```text
clientSocket
```

之后和客户端通信时，不再使用 `serverSocket`，而是使用 `clientSocket`。

也就是说：

```text
serverSocket：负责监听
clientSocket：负责通信
```

这是 TCP 服务端最重要的地方。

---

## 7. 获取客户端 IP 和端口

```cpp
char clientIp[INET_ADDRSTRLEN];

inet_ntop(
    AF_INET,
    &clientAddr.sin_addr,
    clientIp,
    INET_ADDRSTRLEN
);
```

`inet_ntop` 的作用是：

```text
把网络地址转换成人能看懂的字符串 IP。
```

客户端端口可以这样获取：

```cpp
uint16_t clientPort = ntohs(clientAddr.sin_port);
```

`ntohs` 用来把网络字节序转换回主机字节序。

---

## 8. 接收客户端消息

```cpp
ssize_t recvLen = recv(
    clientSocket,
    buffer,
    bufferSize - 1,
    0
);
```

`recv` 的作用是：

```text
从已经建立的 TCP 连接中接收数据。
```

TCP 的 `recv` 不需要填写客户端地址，因为连接已经通过 `accept` 建立好了。

返回值含义：

| 返回值   | 含义              |
| ----- | --------------- |
| `> 0` | 成功收到数据，返回收到的字节数 |
| `0`   | 对方关闭了连接         |
| `-1`  | 接收失败            |

接收到数据后，需要手动补字符串结束符：

```cpp
buffer[recvLen] = '\0';
```

---

## 9. 回复客户端

```cpp
string reply = "server received: ";
reply += buffer;

ssize_t sendLen = send(
    clientSocket,
    reply.c_str(),
    reply.size(),
    0
);
```

`send` 的作用是：

```text
通过已经建立好的 TCP 连接发送数据。
```

TCP 已经建立连接，所以 `send` 不需要指定目标 IP 和端口。

这也是 TCP 和 UDP 的重要区别：

```text
UDP：sendto，需要指定目标地址
TCP：send，不需要指定目标地址
```

---

# 八、TCP 服务端完整代码

```cpp
#include <arpa/inet.h>
#include <netinet/in.h>
#include <sys/socket.h>
#include <unistd.h>

#include <cerrno>
#include <cstddef>
#include <cstdint>
#include <cstdlib>
#include <cstring>
#include <spdlog/spdlog.h>
#include <string>

using namespace std;

int main()
{
    constexpr uint16_t port = 2006;
    constexpr size_t bufferSize = 1024;

    int serverSocket = socket(AF_INET, SOCK_STREAM, 0);
    if (serverSocket == -1)
    {
        spdlog::error("socket failed: {}", strerror(errno));
        return EXIT_FAILURE;
    }

    spdlog::info("TCP server socket created successfully");

    int opt = 1;
    int setSockOptResult = setsockopt(
        serverSocket,
        SOL_SOCKET,
        SO_REUSEADDR,
        &opt,
        static_cast<socklen_t>(sizeof(opt))
    );

    if (setSockOptResult == -1)
    {
        spdlog::error("setsockopt failed: {}", strerror(errno));
        close(serverSocket);
        return EXIT_FAILURE;
    }

    sockaddr_in serverAddr{};
    serverAddr.sin_family = AF_INET;
    serverAddr.sin_addr.s_addr = INADDR_ANY;
    serverAddr.sin_port = htons(port);

    int bindResult = bind(
        serverSocket,
        reinterpret_cast<sockaddr*>(&serverAddr),
        static_cast<socklen_t>(sizeof(serverAddr))
    );

    if (bindResult == -1)
    {
        spdlog::error("bind failed: {}", strerror(errno));
        close(serverSocket);
        return EXIT_FAILURE;
    }

    spdlog::info("TCP server bound successfully on port {}", port);

    int listenResult = listen(serverSocket, SOMAXCONN);
    if (listenResult == -1)
    {
        spdlog::error("listen failed: {}", strerror(errno));
        close(serverSocket);
        return EXIT_FAILURE;
    }

    spdlog::info("TCP server is listening...");

    sockaddr_in clientAddr{};
    socklen_t clientAddrLen = static_cast<socklen_t>(sizeof(clientAddr));

    int clientSocket = accept(
        serverSocket,
        reinterpret_cast<sockaddr*>(&clientAddr),
        &clientAddrLen
    );

    if (clientSocket == -1)
    {
        spdlog::error("accept failed: {}", strerror(errno));
        close(serverSocket);
        return EXIT_FAILURE;
    }

    char clientIp[INET_ADDRSTRLEN];

    const char* clientIpResult = inet_ntop(
        AF_INET,
        &clientAddr.sin_addr,
        clientIp,
        INET_ADDRSTRLEN
    );

    if (clientIpResult == nullptr)
    {
        spdlog::error("inet_ntop failed: {}", strerror(errno));
        close(clientSocket);
        close(serverSocket);
        return EXIT_FAILURE;
    }

    uint16_t clientPort = ntohs(clientAddr.sin_port);

    spdlog::info("client connected: {}:{}", clientIp, clientPort);

    char buffer[bufferSize];

    while (true)
    {
        ssize_t recvLen = recv(clientSocket, buffer, bufferSize - 1, 0);

        if (recvLen == -1)
        {
            spdlog::error("recv failed: {}", strerror(errno));
            continue;
        }

        if (recvLen == 0)
        {
            spdlog::info("client disconnected");
            break;
        }

        buffer[recvLen] = '\0';

        spdlog::info("client[{}:{}] says: {}", clientIp, clientPort, buffer);

        string reply = "server received: ";
        reply += buffer;

        ssize_t sendLen = send(clientSocket, reply.c_str(), reply.size(), 0);

        if (sendLen == -1)
        {
            spdlog::error("send failed: {}", strerror(errno));
            continue;
        }

        spdlog::info("reply sent, bytes: {}", sendLen);

        if (string(buffer) == "exit")
        {
            spdlog::info("server received exit, shutting down");
            break;
        }
    }

    close(clientSocket);
    close(serverSocket);

    return EXIT_SUCCESS;
}
```

---

# 九、TCP 客户端代码讲解

客户端文件：

```text
src/tcp/tcpClient.cpp
```

## 1. 指定服务器地址

```cpp
constexpr const char* serverIp = "127.0.0.1";
constexpr uint16_t serverPort = 2006;
```

`127.0.0.1` 表示本机地址。

如果服务端和客户端在同一台电脑上运行，就使用：

```text
127.0.0.1
```

如果服务端和客户端在不同电脑上运行，需要把它改成服务端电脑的局域网 IP 地址。

---

## 2. 创建客户端 socket

```cpp
int clientSocket = socket(AF_INET, SOCK_STREAM, 0);
```

这表示创建一个 IPv4 TCP socket。

和 UDP 不同，TCP 使用：

```cpp
SOCK_STREAM
```

---

## 3. 准备服务器地址结构

```cpp
sockaddr_in serverAddr{};

serverAddr.sin_family = AF_INET;
serverAddr.sin_port = htons(serverPort);
```

然后把字符串 IP 转成网络地址：

```cpp
int ipResult = inet_pton(AF_INET, serverIp, &serverAddr.sin_addr);
```

`inet_pton` 的作用是：

```text
把 "127.0.0.1" 这种字符串 IP 转换成 socket 能使用的二进制网络地址。
```

如果转换失败，需要结束程序。

---

## 4. 连接服务器

```cpp
int connectResult = connect(
    clientSocket,
    reinterpret_cast<sockaddr*>(&serverAddr),
    static_cast<socklen_t>(sizeof(serverAddr))
);
```

`connect` 的作用是：

```text
客户端主动连接服务器。
```

连接成功后，客户端和服务端之间建立 TCP 连接。

后续通信时，就可以直接使用：

```cpp
send();
recv();
```

不需要像 UDP 一样每次指定目标地址。

---

## 5. 发送消息给服务器

```cpp
ssize_t sendLen = send(
    clientSocket,
    message.c_str(),
    message.size(),
    0
);
```

`send` 的作用是：

```text
通过已经建立的 TCP 连接发送数据。
```

这里不需要写服务器地址，因为 `connect` 时已经连接到指定服务器。

---

## 6. 接收服务器回复

```cpp
ssize_t recvLen = recv(
    clientSocket,
    buffer,
    bufferSize - 1,
    0
);
```

`recv` 的作用是：

```text
从已经建立的 TCP 连接中接收数据。
```

返回值为 `0` 时，表示服务器关闭了连接。

接收后也要补字符串结束符：

```cpp
buffer[recvLen] = '\0';
```

---

# 十、TCP 客户端完整代码

```cpp
#include <arpa/inet.h>
#include <netinet/in.h>
#include <sys/socket.h>
#include <unistd.h>

#include <cerrno>
#include <cstddef>
#include <cstdint>
#include <cstdlib>
#include <cstring>
#include <iostream>
#include <spdlog/spdlog.h>
#include <string>

using namespace std;

int main()
{
    constexpr const char* serverIp = "127.0.0.1";
    constexpr uint16_t serverPort = 2006;
    constexpr size_t bufferSize = 1024;

    int clientSocket = socket(AF_INET, SOCK_STREAM, 0);
    if (clientSocket == -1)
    {
        spdlog::error("socket failed: {}", strerror(errno));
        return EXIT_FAILURE;
    }

    spdlog::info("TCP client socket created successfully");

    sockaddr_in serverAddr{};
    serverAddr.sin_family = AF_INET;
    serverAddr.sin_port = htons(serverPort);

    int ipResult = inet_pton(AF_INET, serverIp, &serverAddr.sin_addr);
    if (ipResult == 0)
    {
        spdlog::error("invalid server ip: {}", serverIp);
        close(clientSocket);
        return EXIT_FAILURE;
    }

    if (ipResult == -1)
    {
        spdlog::error("inet_pton failed: {}", strerror(errno));
        close(clientSocket);
        return EXIT_FAILURE;
    }

    int connectResult = connect(
        clientSocket,
        reinterpret_cast<sockaddr*>(&serverAddr),
        static_cast<socklen_t>(sizeof(serverAddr))
    );

    if (connectResult == -1)
    {
        spdlog::error("connect failed: {}", strerror(errno));
        close(clientSocket);
        return EXIT_FAILURE;
    }

    spdlog::info("connected to TCP server {}:{}", serverIp, serverPort);

    char buffer[bufferSize];

    while (true)
    {
        cout << "Please enter the content you want to send: " << flush;

        string message;
        if (!getline(cin, message))
        {
            spdlog::info("input closed, client exiting");
            break;
        }

        if (message.empty())
        {
            continue;
        }

        ssize_t sendLen = send(clientSocket, message.c_str(), message.size(), 0);

        if (sendLen == -1)
        {
            spdlog::error("send failed: {}", strerror(errno));
            continue;
        }

        spdlog::info("message sent, bytes: {}", sendLen);

        ssize_t recvLen = recv(clientSocket, buffer, bufferSize - 1, 0);

        if (recvLen == 0)
        {
            spdlog::info("server disconnected");
            break;
        }

        if (recvLen == -1)
        {
            spdlog::error("recv failed: {}", strerror(errno));
            continue;
        }

        buffer[recvLen] = '\0';

        spdlog::info("server replies: {}", buffer);

        if (message == "exit")
        {
            spdlog::info("client exiting");
            break;
        }
    }

    close(clientSocket);

    return EXIT_SUCCESS;
}
```

---

# 十一、CMake 配置

如果项目目录已经按照 UDP 和 TCP 分类，可以使用下面这种结构：

```text
socket/
├── CMakeLists.txt
├── build/
└── src/
    ├── udp/
    │   ├── udpServer.cpp
    │   └── udpClient.cpp
    └── tcp/
        ├── tcpServer.cpp
        └── tcpClient.cpp
```

`CMakeLists.txt` 可以写成：

```cmake
cmake_minimum_required(VERSION 3.20)

project(SocketLab LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

find_package(spdlog REQUIRED)

add_executable(udpServer
    src/udp/udpServer.cpp
)

target_link_libraries(udpServer PRIVATE
    spdlog::spdlog
)

add_executable(udpClient
    src/udp/udpClient.cpp
)

target_link_libraries(udpClient PRIVATE
    spdlog::spdlog
)

add_executable(tcpServer
    src/tcp/tcpServer.cpp
)

target_link_libraries(tcpServer PRIVATE
    spdlog::spdlog
)

add_executable(tcpClient
    src/tcp/tcpClient.cpp
)

target_link_libraries(tcpClient PRIVATE
    spdlog::spdlog
)
```

---

# 十二、编译和运行

## 1. 编译

在项目根目录执行：

```text
cmake --build build
```

如果没有生成过 `build` 目录，先执行：

```text
cmake -S . -B build
cmake --build build
```

---

## 2. 运行服务端

打开第一个终端：

```text
cd ~/Code/cpp/lab/socket
./build/tcpServer
```

输出示例：

```text
TCP server socket created successfully
TCP server bound successfully on port 2006
TCP server is listening...
```

这说明 TCP 服务端已经启动，并正在等待客户端连接。

---

## 3. 运行客户端

打开第二个终端：

```text
cd ~/Code/cpp/lab/socket
./build/tcpClient
```

客户端连接成功后，服务端会显示客户端连接信息。

客户端输入示例：

```text
hello
test tcp
exit
```

客户端输出示例：

```text
TCP client socket created successfully
connected to TCP server 127.0.0.1:2006
Please enter the content you want to send: hello
message sent, bytes: 5
server replies: server received: hello
Please enter the content you want to send: test tcp
message sent, bytes: 8
server replies: server received: test tcp
Please enter the content you want to send: exit
message sent, bytes: 4
server replies: server received: exit
client exiting
```

服务端输出示例：

```text
TCP server socket created successfully
TCP server bound successfully on port 2006
TCP server is listening...
client connected: 127.0.0.1:39120
client[127.0.0.1:39120] says: hello
reply sent, bytes: 22
client[127.0.0.1:39120] says: test tcp
reply sent, bytes: 25
client[127.0.0.1:39120] says: exit
reply sent, bytes: 21
server received exit, shutting down
```

---

# 十三、常见问题

## 1. `bind failed: Address already in use`

原因：

```text
2006 端口已经被占用。
```

解决方法：

1. 关闭之前运行的服务端。
2. 或者更换端口号。
3. 查看端口占用：

```text
ss -ltnp | grep 2006
```

UDP 查看端口使用：

```text
ss -lunp | grep 2006
```

TCP 查看端口使用：

```text
ss -ltnp | grep 2006
```

---

## 2. 客户端 `connect failed`

可能原因：

1. 服务端没有启动。
2. 服务端端口写错。
3. 服务端 IP 地址写错。
4. 服务端没有执行 `listen`。
5. 防火墙阻止连接。

本机测试时，客户端 IP 应该写：

```text
127.0.0.1
```

---

## 3. `accept` 一直卡住

这是正常现象。

因为 `accept` 的作用是等待客户端连接。

如果没有客户端连接，服务端就会停在：

```cpp
accept(...)
```

直到客户端执行：

```cpp
connect(...)
```

---

## 4. `recv` 返回 0

`recv` 返回 0 表示：

```text
对方已经关闭连接。
```

服务端收到 `recvLen == 0`，说明客户端断开了。

客户端收到 `recvLen == 0`，说明服务端断开了。

---

## 5. 输出乱码或多余字符

原因：

```text
recv 接收到的是字节数据，不一定自动带字符串结束符。
```

解决方法：

```cpp
buffer[recvLen] = '\0';
```

并且接收时给 `'\0'` 留一个位置：

```cpp
recv(socketFd, buffer, bufferSize - 1, 0);
```

---

## 6. TCP 的粘包问题

TCP 是面向字节流的协议，不保留消息边界。

也就是说，客户端连续发送两次数据，服务端不一定正好分两次收到。服务端可能一次收到两条消息，也可能一条消息分多次收到。

本实验发送的数据较短，并且采用一发一收的方式，所以可以正常观察 TCP 通信流程。

真正项目中需要自己设计应用层协议，例如：

```text
固定长度消息
消息头 + 消息体
使用换行符作为一条消息的结束标志
```

---

# 十四、本节小结

本节完成了 TCP 服务端和客户端通信。

需要掌握：

1. TCP 是面向连接的可靠传输协议。
2. TCP 通信前需要先建立连接。
3. TCP 服务端需要 `bind` 端口。
4. TCP 服务端需要使用 `listen` 监听连接。
5. TCP 服务端需要使用 `accept` 接受客户端连接。
6. TCP 客户端需要使用 `connect` 连接服务器。
7. TCP 连接建立后，双方使用 `send` 和 `recv` 进行数据通信。
8. TCP 服务端中 `serverSocket` 负责监听，`clientSocket` 负责通信。
9. `recv` 返回 0 表示对方关闭连接。
10. TCP 是字节流协议，不保留消息边界。
11. Linux 下关闭 socket 使用 `close`。

TCP 最核心的两句话是：

```text
服务端：socket → bind → listen → accept → recv → send
客户端：socket → connect → send → recv
```

UDP 和 TCP 的核心区别是：

```text
UDP：不建立连接，使用 sendto / recvfrom，每次发送都需要目标地址。
TCP：先建立连接，使用 send / recv，连接建立后不需要每次指定目标地址。
```

下一步可以在本实验基础上继续实现多客户端 TCP 服务端。

