# UDP 通信

## 一、UDP 是什么

UDP，全称是 **User Datagram Protocol**，中文叫**用户数据报协议**。

UDP 的特点是：

* 不需要建立连接。
* 发送方可以直接把数据发给指定 IP 和端口。
* 接收方只要绑定了对应端口，就可以收到数据。
* UDP 不保证数据一定到达。
* UDP 不保证数据顺序。
* UDP 程序结构比 TCP 简单。

可以简单理解为：

```text
UDP 像寄信：
你写好地址，直接寄出去。
对方有没有收到，协议本身不保证。
```

和 TCP 相比：

```text
TCP：先连接，再通信。
UDP：不连接，直接发。
```

---

## 二、UDP 服务端和客户端的区别

UDP 虽然不需要建立连接，但仍然有服务端和客户端的区别。

### 1. UDP 服务端

UDP 服务端要做的事情是：

```text
创建 socket
↓
绑定端口
↓
等待客户端发送数据
↓
接收数据
↓
回复客户端
```

服务端必须绑定端口，因为客户端要知道数据发到哪里。

例如服务端绑定：

```text
端口：8888
```

那么客户端就可以把数据发到：

```text
127.0.0.1:8888
```

---

### 2. UDP 客户端

UDP 客户端要做的事情是：

```text
创建 socket
↓
指定服务器 IP 和端口
↓
发送数据
↓
接收服务器回复
↓
关闭 socket
```

UDP 客户端一般不需要手动绑定端口。

系统会自动给客户端分配一个临时端口。

---

## 三、Linux Socket 和 Winsock 的区别

本实验在 Arch Linux 上完成，所以使用的是 **Linux / POSIX Socket**，不是 Windows Winsock。

主要区别如下：

| 功能        | Windows Winsock   | Linux / POSIX Socket |
| ----------- | ----------------- | -------------------- |
| 初始化网络库| `WSAStartup`        | 不需要               |
| 清理网络库  | `WSACleanup`        | 不需要               |
| 关闭 socket | `closesocket`       | `close`                |
| 错误输出    | `WSAGetLastError`   | `perror`               |
| UDP 发送    | `sendto`            | `sendto`               |
| UDP 接收    | `recvfrom`          | `recvfrom`             |

在 Linux 下，不需要写：

```cpp
WSAStartup();
WSACleanup();
```

直接创建 socket 即可。

---

## 四、UDP 程序需要的头文件

UDP 服务端和客户端都会用到这些头文件：

```cpp
#include <arpa/inet.h>
#include <netinet/in.h>
#include <sys/socket.h>
#include <unistd.h>

#include <cstring>
#include <iostream>
#include <string>
```

作用如下：

| 头文件       | 作用                                         |
| ------------ | -------------------------------------------- |
| `sys/socket.h` | 提供 `socket`、`bind`、`sendto`、`recvfrom`          |
| `netinet/in.h` | 提供 `sockaddr_in`、`htons`、`INADDR_ANY`          |
| `arpa/inet.h`  | 提供 `inet_pton`、`inet_ntop` 等 IP 地址转换函数 |
| `unistd.h`     | 提供 `close`                                   |
| `cstring`      | 提供字符串和内存处理函数                     |
| `iostream`     | 提供 `cin`、`cout`                               |
| `string`       | 提供 `std::string`                             |

---

## 五、UDP 服务端核心函数

UDP 服务端主要使用这些函数：

| 函数     | 作用                 |
| -------- | -------------------- |
| `socket`   | 创建 socket          |
| `bind`     | 绑定 IP 和端口       |
| `recvfrom` | 接收客户端发送的数据 |
| `sendto`   | 向客户端发送回复     |
| `close`    | 关闭 socket          |

服务端核心流程：

```text
socket
↓
bind
↓
recvfrom
↓
sendto
↓
close
```

---

## 六、UDP 客户端核心函数

UDP 客户端主要使用这些函数：

| 函数      | 作用                       |
| --------- | -------------------------- |
| `socket`    | 创建 socket                |
| `inet_pton` | 把字符串 IP 转换为网络地址 |
| `sendto`    | 向服务器发送数据           |
| `recvfrom`  | 接收服务器回复             |
| `close`     | 关闭 socket                |

客户端核心流程：

```text
socket
↓
inet_pton
↓
sendto
↓
recvfrom
↓
close
```

---

# 七、UDP 服务端代码讲解

服务端文件：

```text
src/udpServer.cpp
```

## 1. 创建 UDP socket

```cpp
int serverSocket = socket(AF_INET, SOCK_DGRAM, 0);
```

参数含义：

| 参数       | 含义                  |
| ---------- | ----------------------|
| `AF_INET`    | 使用 IPv4             |
| `SOCK_DGRAM` | 使用 UDP              |
| `0`          | 让系统自动选择对应协议|

如果创建失败，返回 `-1`。

所以需要判断：

```cpp
if (serverSocket == -1)
{
    perror("socket failed");
    return 1;
}
```

---

## 2. 准备服务器地址

```cpp
sockaddr_in serverAddr{};

serverAddr.sin_family = AF_INET;
serverAddr.sin_addr.s_addr = INADDR_ANY;
serverAddr.sin_port = htons(port);
```

解释：

| 字段            | 含义                  |
| --------------- | --------------------- |
| `sin_family`      | 地址族，这里使用 IPv4 |
| `sin_addr.s_addr` | 绑定哪个 IP           |
| `sin_port`        | 绑定哪个端口          |

其中：

```cpp
INADDR_ANY
```

表示绑定本机所有 IP 地址。

```cpp
htons(port)
```

表示把端口号转换为网络字节序。

端口号放进 `sockaddr_in` 前，必须使用 `htons`。

---

## 3. 绑定端口

```cpp
int bindResult = bind(
    serverSocket,
    reinterpret_cast<sockaddr*>(&serverAddr),
    sizeof(serverAddr)
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

实验中建议使用普通端口，例如：

```text
8888
9000
10086
```

---

## 4. 接收客户端消息

```cpp
ssize_t recvLen = recvfrom(
    serverSocket,
    buffer,
    bufferSize - 1,
    0,
    reinterpret_cast<sockaddr*>(&clientAddr),
    &clientAddrLen
);
```

`recvfrom` 的作用是：

```text
从 UDP socket 接收数据，并记录发送方的地址。
```

参数含义：

| 参数               | 含义         |
| ---------------- | ---------- |
| `serverSocket`   | 服务端 socket |
| `buffer`         | 接收数据的缓冲区   |
| `bufferSize - 1` | 最多接收多少字节   |
| `0`              | 标志位，通常写 0  |
| `clientAddr`     | 保存客户端地址    |
| `clientAddrLen`  | 客户端地址结构长度  |

接收到数据后，需要手动补字符串结束符：

```cpp
buffer[recvLen] = '\0';
```

否则用 `cout` 输出时可能出现乱码或多余内容。

---

## 5. 获取客户端 IP 和端口

```cpp
char clientIp[INET_ADDRSTRLEN];

inet_ntop(
    AF_INET,
    &clientAddr.sin_addr,
    clientIp,
    sizeof(clientIp)
);
```

`inet_ntop` 的作用是：

```text
把网络地址转换成人能看懂的字符串 IP。
```

例如把地址转换成：

```text
127.0.0.1
```

客户端端口可以这样输出：

```cpp
ntohs(clientAddr.sin_port)
```

`ntohs` 和 `htons` 相反，用来把网络字节序转换回主机字节序。

---

## 6. 回复客户端

```cpp
string reply = "Server received: ";
reply += buffer;

sendto(
    serverSocket,
    reply.c_str(),
    reply.size(),
    0,
    reinterpret_cast<sockaddr*>(&clientAddr),
    clientAddrLen
);
```

`sendto` 的作用是：

```text
向指定 IP 和端口发送 UDP 数据。
```

因为 UDP 没有连接，所以发送时必须指定目标地址。

这里的目标地址就是刚才 `recvfrom` 得到的 `clientAddr`。

---

# 八、UDP 服务端完整代码

```cpp
#include <arpa/inet.h>
#include <netinet/in.h>
#include <sys/socket.h>
#include <unistd.h>

#include <cstring>
#include <iostream>
#include <string>

using namespace std;

int main()
{
    const int port = 8888;
    const int bufferSize = 1024;

    int serverSocket = socket(AF_INET, SOCK_DGRAM, 0);

    if (serverSocket == -1)
    {
        perror("socket failed");
        return 1;
    }

    sockaddr_in serverAddr{};

    serverAddr.sin_family = AF_INET;
    serverAddr.sin_addr.s_addr = INADDR_ANY;
    serverAddr.sin_port = htons(port);

    int bindResult = bind(
        serverSocket,
        reinterpret_cast<sockaddr*>(&serverAddr),
        sizeof(serverAddr)
    );

    if (bindResult == -1)
    {
        perror("bind failed");
        close(serverSocket);
        return 1;
    }

    cout << "UDP server started, listening on port " << port << endl;

    char buffer[bufferSize];

    while (true)
    {
        sockaddr_in clientAddr{};
        socklen_t clientAddrLen = sizeof(clientAddr);

        ssize_t recvLen = recvfrom(
            serverSocket,
            buffer,
            bufferSize - 1,
            0,
            reinterpret_cast<sockaddr*>(&clientAddr),
            &clientAddrLen
        );

        if (recvLen == -1)
        {
            perror("recvfrom failed");
            continue;
        }

        buffer[recvLen] = '\0';

        char clientIp[INET_ADDRSTRLEN];

        inet_ntop(
            AF_INET,
            &clientAddr.sin_addr,
            clientIp,
            sizeof(clientIp)
        );

        cout << "Client [" << clientIp << ":" << ntohs(clientAddr.sin_port)
             << "] says: " << buffer << endl;

        string reply = "Server received: ";
        reply += buffer;

        ssize_t sendLen = sendto(
            serverSocket,
            reply.c_str(),
            reply.size(),
            0,
            reinterpret_cast<sockaddr*>(&clientAddr),
            clientAddrLen
        );

        if (sendLen == -1)
        {
            perror("sendto failed");
        }
    }

    close(serverSocket);

    return 0;
}
```

---

# 九、UDP 客户端代码讲解

客户端文件：

```text
src/udpClient.cpp
```

## 1. 指定服务器地址

```cpp
const char* serverIp = "127.0.0.1";
const int serverPort = 8888;
```

`127.0.0.1` 表示本机地址。

如果服务端和客户端在同一台电脑上运行，就使用：

```text
127.0.0.1
```

如果服务端和客户端在不同电脑上运行，需要把它改成服务端电脑的局域网 IP 地址。

例如：

```text
192.168.1.10
```

---

## 2. 创建客户端 socket

```cpp
int clientSocket = socket(AF_INET, SOCK_DGRAM, 0);
```

这和服务端一样，表示创建一个 IPv4 UDP socket。

客户端一般不需要手动 `bind`，系统会自动分配临时端口。

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

如果转换失败，返回值小于等于 0。

---

## 4. 发送消息给服务器

```cpp
ssize_t sendLen = sendto(
    clientSocket,
    message.c_str(),
    message.size(),
    0,
    reinterpret_cast<sockaddr*>(&serverAddr),
    sizeof(serverAddr)
);
```

这里的 `serverAddr` 表示目标服务器地址。

也就是说：

```text
客户端把 message 发送到 serverIp:serverPort。
```

---

## 5. 接收服务器回复

```cpp
ssize_t recvLen = recvfrom(
    clientSocket,
    buffer,
    bufferSize - 1,
    0,
    reinterpret_cast<sockaddr*>(&fromAddr),
    &fromAddrLen
);
```

客户端也使用 `recvfrom` 接收数据。

虽然我们知道回复来自服务器，但 UDP 本身没有连接，所以接收函数仍然会带上发送方地址。

接收后也要补字符串结束符：

```cpp
buffer[recvLen] = '\0';
```

---

# 十、UDP 客户端完整代码

```cpp
#include <arpa/inet.h>
#include <netinet/in.h>
#include <sys/socket.h>
#include <unistd.h>

#include <cstring>
#include <iostream>
#include <string>

using namespace std;

int main()
{
    const char* serverIp = "127.0.0.1";
    const int serverPort = 8888;
    const int bufferSize = 1024;

    int clientSocket = socket(AF_INET, SOCK_DGRAM, 0);

    if (clientSocket == -1)
    {
        perror("socket failed");
        return 1;
    }

    sockaddr_in serverAddr{};

    serverAddr.sin_family = AF_INET;
    serverAddr.sin_port = htons(serverPort);

    int ipResult = inet_pton(AF_INET, serverIp, &serverAddr.sin_addr);

    if (ipResult <= 0)
    {
        perror("inet_pton failed");
        close(clientSocket);
        return 1;
    }

    cout << "UDP client started." << endl;
    cout << "Input message, type exit to quit." << endl;

    string message;
    char buffer[bufferSize];

    while (true)
    {
        cout << "> ";
        getline(cin, message);

        if (message.empty())
        {
            continue;
        }

        ssize_t sendLen = sendto(
            clientSocket,
            message.c_str(),
            message.size(),
            0,
            reinterpret_cast<sockaddr*>(&serverAddr),
            sizeof(serverAddr)
        );

        if (sendLen == -1)
        {
            perror("sendto failed");
            continue;
        }

        if (message == "exit")
        {
            break;
        }

        sockaddr_in fromAddr{};
        socklen_t fromAddrLen = sizeof(fromAddr);

        ssize_t recvLen = recvfrom(
            clientSocket,
            buffer,
            bufferSize - 1,
            0,
            reinterpret_cast<sockaddr*>(&fromAddr),
            &fromAddrLen
        );

        if (recvLen == -1)
        {
            perror("recvfrom failed");
            continue;
        }

        buffer[recvLen] = '\0';

        cout << "Reply from server: " << buffer << endl;
    }

    close(clientSocket);

    return 0;
}
```

---

# 十一、CMake 配置

项目中的 `CMakeLists.txt` 可以先写成：

```cmake
cmake_minimum_required(VERSION 3.20)

project(SocketLab LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

add_executable(udpServer src/udpServer.cpp)
add_executable(udpClient src/udpClient.cpp)
```

当前 UDP 程序不需要额外链接库。

---

# 十二、编译和运行

## 1. 编译

在项目根目录执行：

```text
cmake --build build
```

如果没有生成过 `build` 目录，先执行：

```text
cmake -S . -B build -G Ninja
cmake --build build
```

---

## 2. 运行服务端

打开第一个终端：

```text
cd ~/Code/cpp/lab/socket
./build/udpServer
```

输出示例：

```text
UDP server started, listening on port 8888
```

---

## 3. 运行客户端

打开第二个终端：

```text
cd ~/Code/cpp/lab/socket
./build/udpClient
```

输入示例：

```text
hello
test udp
exit
```

客户端输出示例：

```text
UDP client started.
Input message, type exit to quit.
> hello
Reply from server: Server received: hello
> test udp
Reply from server: Server received: test udp
> exit
```

服务端输出示例：

```text
UDP server started, listening on port 8888
Client [127.0.0.1:39218] says: hello
Client [127.0.0.1:39218] says: test udp
Client [127.0.0.1:39218] says: exit
```

---

# 十三、常见问题

## 1. `bind failed: Address already in use`

原因：

```text
8888 端口已经被占用。
```

解决方法：

1. 关闭之前运行的服务端。
2. 或者更换端口号。
3. 或者查看端口占用：

```text
ss -lunp | grep 8888
```

---

## 2. 客户端收不到回复

可能原因：

1. 服务端没有启动。
2. 客户端端口写错。
3. 客户端 IP 写错。
4. 防火墙阻止通信。
5. 服务端没有执行 `sendto`。

本机测试时，客户端 IP 应该写：

```text
127.0.0.1
```

---

## 3. 输出乱码或多余字符

原因：

```text
recvfrom 接收到的是字节数据，不一定自动带字符串结束符。
```

解决方法：

```cpp
buffer[recvLen] = '\0';
```

并且接收时给 `'\0'` 留一个位置：

```cpp
recvfrom(socketFd, buffer, bufferSize - 1, ...);
```

---

## 4. 服务端退出不了

当前服务端写的是：

```cpp
while (true)
```

所以它会一直运行。

退出服务端可以在终端按：

```text
Ctrl + C
```

后面如果想让服务端收到 `exit` 后退出，也可以在服务端判断：

```cpp
if (string(buffer) == "exit")
{
    break;
}
```

---

# 十四、本节小结

本节完成了 UDP 服务端和客户端通信。

需要掌握：

1. UDP 不需要建立连接。
2. UDP 服务端需要 `bind` 端口。
3. UDP 客户端一般不需要手动 `bind`。
4. `socket(AF_INET, SOCK_DGRAM, 0)` 创建 UDP socket。
5. `sendto` 用于发送 UDP 数据。
6. `recvfrom` 用于接收 UDP 数据。
7. `sockaddr_in` 用于保存 IP 和端口。
8. `htons` 用于转换端口字节序。
9. `inet_pton` 用于把字符串 IP 转换为网络地址。
10. `inet_ntop` 用于把网络地址转换为字符串 IP。
11. Linux 下关闭 socket 使用 `close`。

UDP 最核心的两句话是：

```text
服务端：socket → bind → recvfrom → sendto
客户端：socket → sendto → recvfrom
```

下一步学习 TCP 通信。

