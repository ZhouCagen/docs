# 01 服务器和客户端基本概念

## 一、服务器和客户端是什么

在 Socket 网络程序中，通常会把通信双方分成两类：

* **服务器**：等待别人连接，负责接收请求并返回数据。
* **客户端**：主动连接服务器，负责发送请求并接收服务器返回的数据。

可以简单理解为：

```text
客户端：主动找服务器说话
服务器：一直等客户端来连接
```

例如在一个聊天程序中：

```text
客户端 A 发送消息
↓
服务器接收消息
↓
服务器转发给客户端 B
```

服务器通常不会主动退出，而是一直处于运行和监听状态。

---

## 二、服务器端的一般流程

服务器端的主要任务是：

1. 初始化 Winsock。
2. 创建 Socket。
3. 绑定 IP 地址和端口号。
4. 监听客户端连接。
5. 接受客户端连接。
6. 接收客户端发送的数据。
7. 向客户端发送数据。
8. 关闭连接并释放资源。

服务器端流程可以表示为：

```text
开始
↓
初始化 Winsock
↓
创建 Socket
↓
绑定 IP 地址和端口号
↓
监听客户端连接
↓
接受客户端连接
↓
接收和发送数据
↓
关闭连接
↓
释放 Winsock 资源
↓
结束
```

在 TCP 服务器中，常见函数使用顺序是：

```text
WSAStartup
↓
socket
↓
bind
↓
listen
↓
accept
↓
recv / send
↓
closesocket
↓
WSACleanup
```

---

## 三、客户端的一般流程

客户端的主要任务是：

1. 初始化 Winsock。
2. 创建 Socket。
3. 指定服务器的 IP 地址和端口号。
4. 连接服务器。
5. 向服务器发送数据。
6. 接收服务器返回的数据。
7. 关闭连接并释放资源。

客户端流程可以表示为：

```text
开始
↓
初始化 Winsock
↓
创建 Socket
↓
设置服务器 IP 地址和端口号
↓
连接服务器
↓
发送和接收数据
↓
关闭连接
↓
释放 Winsock 资源
↓
结束
```

在 TCP 客户端中，常见函数使用顺序是：

```text
WSAStartup
↓
socket
↓
connect
↓
send / recv
↓
closesocket
↓
WSACleanup
```

---

## 四、服务器和客户端的区别

| 对比项           | 服务器                 | 客户端             |
| -----------------| ---------------------- | ------------------ |
| 行为             | 被动等待连接           | 主动发起连接       |
| 是否需要绑定端口 | 通常需要               | 通常不需要手动绑定 |
| 是否需要监听     | 需要                   | 不需要             |
| 是否需要接受连接 | 需要                   | 不需要             |
| 典型函数         | `bind` 、`listen`、`accept`  | `connect`            |
| 作用             | 提供服务               | 请求服务           |

服务器需要固定端口，是因为客户端必须知道要连接到哪里。

例如：

```text
服务器 IP：127.0.0.1
服务器端口：8888
```

客户端连接时，就需要指定：

```text
127.0.0.1:8888
```

---

## 五、UDP 和 TCP 的区别

Socket 编程中常见的通信方式有两种：UDP 和 TCP。

### 1. UDP

UDP 是无连接通信。

客户端不需要先连接服务器，可以直接发送数据。

UDP 常用函数：

```text
sendto
recvfrom
```

UDP 通信流程：

```text
服务器：socket → bind → recvfrom → sendto
客户端：socket → sendto → recvfrom
```

特点：

* 不需要建立连接。
* 程序结构比较简单。
* 发送速度较快。
* 不保证数据一定到达。
* 不保证数据顺序。

---

### 2. TCP

TCP 是面向连接通信。

通信之前必须先建立连接。

TCP 常用函数：

```text
listen
accept
connect
send
recv
```

TCP 通信流程：

```text
服务器：socket → bind → listen → accept → recv/send
客户端：socket → connect → send/recv
```

特点：

* 通信前需要建立连接。
* 数据传输可靠。
* 能保证数据顺序。
* 适合聊天、文件传输、网页访问等场景。
* 程序结构比 UDP 稍微复杂。

---

## 六、创建基本 Winsock 应用程序

编写 Winsock 程序时，一般需要以下步骤：

1. 创建一个新的 C++ 项目。
2. 添加 C++ 源文件。
3. 包含 Winsock 相关头文件。
4. 链接 Winsock 库文件 `Ws2_32.lib`。
5. 在程序中初始化 Winsock。
6. 编写 Socket 通信代码。
7. 程序结束前释放资源。

---

## 七、基本头文件

Winsock 程序常用头文件如下：

```cpp
#include <winsock2.h>
#include <ws2tcpip.h>
#include <iostream>

#pragma comment(lib, "Ws2_32.lib")
```

其中：

| 头文件或库 | 作用                                       |
| -----------| ------------------------------------------ |
| `winsock2.h` | 包含大多数 Winsock 函数、结构和定义        |
| `ws2tcpip.h` | 包含 TCP/IP 相关函数，例如 IP 地址转换函数 |
| `iostream`   | 用于 C++ 输入输出，例如 `cin`、`cout`          |
| `Ws2_32.lib` | Winsock 程序需要链接的库文件               |

---

## 八、为什么要链接 `Ws2_32.lib`

Winsock 的函数并不直接包含在普通 C++ 标准库中。

如果使用了下面这些函数：

```text
WSAStartup
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
WSACleanup
```

就需要链接 `Ws2_32.lib`。

可以在代码中写：

```cpp
#pragma comment(lib, "Ws2_32.lib")
```

这句话的作用是告诉 Visual Studio 链接器：

```text
这个程序需要使用 Ws2_32.lib 这个库。
```

---

## 九、关于 `Windows.h` 和 `Winsock2.h`

在 Winsock 程序中，通常不需要手动包含 `Windows.h`。

如果确实需要包含 `Windows.h`，应该先定义：

```cpp
#define WIN32_LEAN_AND_MEAN
```

原因是：

`Windows.h` 可能会包含旧版本的 `winsock.h`，而我们现在使用的是 `winsock2.h`。如果两个头文件同时出现，可能会产生命名冲突和重复定义错误。

推荐写法：

```cpp
#define WIN32_LEAN_AND_MEAN

#include <winsock2.h>
#include <ws2tcpip.h>
#include <iostream>

#pragma comment(lib, "Ws2_32.lib")
```

如果必须包含 `Windows.h`，可以这样写：

```cpp
#ifndef WIN32_LEAN_AND_MEAN
#define WIN32_LEAN_AND_MEAN
#endif

#include <windows.h>
#include <winsock2.h>
#include <ws2tcpip.h>
#include <iostream>

#pragma comment(lib, "Ws2_32.lib")
```

---

## 十、最小 Winsock 程序模板

后续编写 UDP 服务端、UDP 客户端、TCP 服务端和 TCP 客户端时，都可以从这个模板开始：

```cpp
#define WIN32_LEAN_AND_MEAN

#include <winsock2.h>
#include <ws2tcpip.h>
#include <iostream>

#pragma comment(lib, "Ws2_32.lib")

using namespace std;

int main()
{
    return 0;
}
```

这个模板目前还没有真正进行网络通信，只是准备好了使用 Winsock 所需的基本头文件和链接库。

下一步需要学习的是：如何初始化 Winsock。


















程序

.h 的注意事项

