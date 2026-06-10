# 03 为客户端创建 Socket

## 一、本节目标

上一节已经完成了 Winsock 初始化。

在调用完：

```cpp
WSAStartup(MAKEWORD(2, 2), &wsaData);
```

之后，客户端程序还不能直接发送数据。

下一步需要创建一个 Socket。

Socket 可以理解为：

```text
网络通信的入口
```

客户端后续连接服务器、发送数据、接收数据，都需要通过这个 Socket 完成。

---

## 二、客户端创建 Socket 的基本流程

客户端创建 Socket 的流程如下：

```text
声明 addrinfo 结构
↓
设置连接参数
↓
调用 getaddrinfo 获取服务器地址信息
↓
声明 SOCKET 对象
↓
调用 socket 创建套接字
↓
判断是否创建成功
```

---

## 三、需要用到的主要内容

本节主要会用到这些内容：

| 名称                | 作用                       |
| ----------------- | ------------------------ |
| `addrinfo`        | 保存地址信息和 socket 创建参数      |
| `getaddrinfo`     | 根据服务器地址和端口号获取可用地址信息      |
| `SOCKET`          | Winsock 中表示套接字的类型        |
| `socket`          | 创建一个新的套接字                |
| `INVALID_SOCKET`  | 表示 socket 创建失败           |
| `WSAGetLastError` | 获取 Winsock 错误码           |
| `freeaddrinfo`    | 释放 `getaddrinfo` 申请的地址信息 |

---

## 四、声明 `addrinfo`

官方示例中会先声明几个 `addrinfo` 变量：

```cpp
struct addrinfo *result = NULL;
struct addrinfo *ptr = NULL;
struct addrinfo hints;
```

也可以写成 C++ 风格：

```cpp
addrinfo *result = nullptr;
addrinfo *ptr = nullptr;
addrinfo hints{};
```

其中：

| 变量       | 含义                       |
| -------- | ------------------------ |
| `result` | 保存 `getaddrinfo` 返回的地址链表 |
| `ptr`    | 指向当前要使用的地址信息             |
| `hints`  | 告诉系统我们想要什么类型的地址和 socket  |

---

## 五、设置 `hints`

`hints` 用来告诉 `getaddrinfo`：

```text
我要使用什么地址类型
我要使用 TCP 还是 UDP
我要创建什么类型的 Socket
```

官方示例中大致写法如下：

```cpp
ZeroMemory(&hints, sizeof(hints));

hints.ai_family = AF_UNSPEC;
hints.ai_socktype = SOCK_STREAM;
hints.ai_protocol = IPPROTO_TCP;
```

含义如下：

| 字段            | 含义                                 |
| ------------- | ---------------------------------- |
| `ai_family`   | 地址族，`AF_UNSPEC` 表示 IPv4 或 IPv6 都可以 |
| `ai_socktype` | Socket 类型，`SOCK_STREAM` 表示 TCP     |
| `ai_protocol` | 协议，`IPPROTO_TCP` 表示 TCP 协议         |

如果实验中只想使用 IPv4，也可以写成：

```cpp
hints.ai_family = AF_INET;
```

目前为了简单，实验代码可以优先使用 IPv4。

---

## 六、设置服务器端口号

官方示例中使用了：

```cpp
#define DEFAULT_PORT "27015"
```

这里的端口号是字符串形式。

例如：

```cpp
#define DEFAULT_PORT "27015"
```

表示客户端准备连接服务器的 `27015` 端口。

在我们自己的实验中，也可以改成：

```cpp
#define DEFAULT_PORT "8888"
```

只要客户端和服务器使用同一个端口即可。

---

## 七、调用 `getaddrinfo`

`getaddrinfo` 用来根据服务器地址和端口号获取地址信息。

示例：

```cpp
int resultCode = getaddrinfo("127.0.0.1", DEFAULT_PORT, &hints, &result);

if (resultCode != 0)
{
    cout << "getaddrinfo failed: " << resultCode << endl;
    WSACleanup();
    return 1;
}
```

这里：

| 参数             | 含义                   |
| -------------- | -------------------- |
| `"127.0.0.1"`  | 服务器 IP 地址            |
| `DEFAULT_PORT` | 服务器端口号               |
| `&hints`       | 需要的地址类型、Socket 类型和协议 |
| `&result`      | 保存查询到的地址信息           |

`127.0.0.1` 表示本机地址。

也就是说：

```text
客户端和服务器运行在同一台电脑上时，可以使用 127.0.0.1
```

如果客户端和服务器运行在两台不同的电脑上，就需要把 `"127.0.0.1"` 改成服务器那台电脑的局域网 IP 地址。

---

## 八、声明客户端 Socket

创建 Socket 前，先声明一个 `SOCKET` 变量：

```cpp
SOCKET connectSocket = INVALID_SOCKET;
```

这里先把它初始化为 `INVALID_SOCKET`，表示当前还没有创建成功。

---

## 九、调用 `socket` 创建套接字

`getaddrinfo` 返回的结果保存在 `result` 中。

先让 `ptr` 指向 `result`：

```cpp
ptr = result;
```

然后调用 `socket`：

```cpp
connectSocket = socket(ptr->ai_family, ptr->ai_socktype, ptr->ai_protocol);
```

这三个参数来自前面设置好的地址信息：

| 参数                 | 含义                     |
| ------------------ | ---------------------- |
| `ptr->ai_family`   | 地址族，例如 IPv4 或 IPv6     |
| `ptr->ai_socktype` | Socket 类型，例如 TCP 流式套接字 |
| `ptr->ai_protocol` | 协议，例如 TCP              |

如果按照 TCP 写法，最终等价于：

```cpp
socket(AF_INET, SOCK_STREAM, IPPROTO_TCP);
```

或者：

```cpp
socket(AF_UNSPEC, SOCK_STREAM, IPPROTO_TCP);
```

---

## 十、检查 Socket 是否创建成功

调用 `socket` 后，需要判断是否创建成功：

```cpp
if (connectSocket == INVALID_SOCKET)
{
    cout << "socket failed: " << WSAGetLastError() << endl;
    freeaddrinfo(result);
    WSACleanup();
    return 1;
}
```

如果 `socket` 创建失败，会返回：

```cpp
INVALID_SOCKET
```

这时不能继续执行连接服务器的操作。

`WSAGetLastError()` 可以获取具体的错误码。

---

## 十一、本节完整代码片段

下面代码建立在已经完成 Winsock 初始化的基础上。

```cpp
#define DEFAULT_PORT "27015"

addrinfo *result = nullptr;
addrinfo *ptr = nullptr;
addrinfo hints{};

ZeroMemory(&hints, sizeof(hints));

hints.ai_family = AF_INET;
hints.ai_socktype = SOCK_STREAM;
hints.ai_protocol = IPPROTO_TCP;

int resultCode = getaddrinfo("127.0.0.1", DEFAULT_PORT, &hints, &result);

if (resultCode != 0)
{
    cout << "getaddrinfo failed: " << resultCode << endl;
    WSACleanup();
    return 1;
}

SOCKET connectSocket = INVALID_SOCKET;

ptr = result;

connectSocket = socket(ptr->ai_family, ptr->ai_socktype, ptr->ai_protocol);

if (connectSocket == INVALID_SOCKET)
{
    cout << "socket failed: " << WSAGetLastError() << endl;
    freeaddrinfo(result);
    WSACleanup();
    return 1;
}
```

---

## 十二、放进完整程序中的位置

客户端程序目前的大致结构是：

```cpp
int main()
{
    // 1. 初始化 Winsock
    WSADATA wsaData;

    int resultCode = WSAStartup(MAKEWORD(2, 2), &wsaData);

    if (resultCode != 0)
    {
        cout << "WSAStartup failed: " << resultCode << endl;
        return 1;
    }

    // 2. 创建客户端 Socket
    // 本节代码放在这里

    // 3. 连接服务器
    // 下一节学习

    // 4. 发送和接收数据
    // 后面学习

    // 5. 关闭连接
    // 后面学习

    WSACleanup();

    return 0;
}
```

---

## 十三、本节小结

本节学习了客户端如何创建 Socket。

需要记住：

1. `addrinfo` 用来保存地址信息。
2. `hints` 用来设置需要的地址类型、Socket 类型和协议。
3. `getaddrinfo` 用来获取服务器地址信息。
4. `SOCKET` 是 Winsock 中表示套接字的类型。
5. `socket` 用来创建套接字。
6. 如果 `socket` 返回 `INVALID_SOCKET`，说明创建失败。
7. `freeaddrinfo` 用来释放 `getaddrinfo` 返回的地址信息。

最重要的代码是：

```cpp
connectSocket = socket(ptr->ai_family, ptr->ai_socktype, ptr->ai_protocol);

if (connectSocket == INVALID_SOCKET)
{
    cout << "socket failed: " << WSAGetLastError() << endl;
    freeaddrinfo(result);
    WSACleanup();
    return 1;
}
```

下一步需要学习的是：客户端如何连接到服务器。

