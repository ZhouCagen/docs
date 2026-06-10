# 07 为服务器创建 Socket

## 一、本节目标

前面学习的是客户端程序。

从本节开始，学习服务器端程序。

服务器端和客户端最大的区别是：

```text
客户端主动连接服务器
服务器等待客户端连接
```

所以服务器端需要创建一个专门用于监听客户端连接的 Socket。

这个 Socket 通常叫：

```cpp
ListenSocket
```

可以理解为：

```text
服务器用 ListenSocket 在指定端口上等待客户端连接
```

---

## 二、服务器创建 Socket 的流程

服务器创建 Socket 的基本流程如下：

```text
初始化 Winsock
↓
设置 addrinfo 参数
↓
调用 getaddrinfo 获取本地地址信息
↓
创建 ListenSocket
↓
判断 Socket 是否创建成功
↓
下一步绑定 Socket
```

---

## 三、服务器端需要用到的主要内容

| 名称               | 作用                   |
| ---------------- | -------------------- |
| `addrinfo`       | 保存地址信息和 Socket 参数    |
| `hints`          | 设置服务器想要的地址类型、协议等     |
| `getaddrinfo`    | 获取服务器本地地址信息          |
| `AI_PASSIVE`     | 表示这个地址用于服务器绑定        |
| `SOCKET`         | Winsock 中的 Socket 类型 |
| `ListenSocket`   | 服务器用于监听客户端连接的 Socket |
| `socket`         | 创建 Socket            |
| `INVALID_SOCKET` | 表示 Socket 创建失败       |

---

## 四、定义服务器端口号

官方示例中使用：

```cpp
#define DEFAULT_PORT "27015"
```

它表示服务器监听的端口号是：

```text
27015
```

在实验中也可以改成：

```cpp
#define DEFAULT_PORT "8888"
```

只要客户端连接时也使用同一个端口即可。

---

## 五、声明 `addrinfo`

服务器端同样需要 `addrinfo`：

```cpp
addrinfo *result = nullptr;
addrinfo hints{};
```

其中：

| 变量       | 含义                         |
| -------- | -------------------------- |
| `result` | 保存 `getaddrinfo` 返回的地址信息   |
| `hints`  | 设置服务器端需要的地址类型、Socket 类型和协议 |

---

## 六、设置 `hints`

服务器端设置 `hints` 的代码如下：

```cpp
ZeroMemory(&hints, sizeof(hints));

hints.ai_family = AF_INET;
hints.ai_socktype = SOCK_STREAM;
hints.ai_protocol = IPPROTO_TCP;
hints.ai_flags = AI_PASSIVE;
```

含义如下：

| 字段                          | 含义           |
| --------------------------- | ------------ |
| `ai_family = AF_INET`       | 使用 IPv4      |
| `ai_socktype = SOCK_STREAM` | 使用 TCP 流式套接字 |
| `ai_protocol = IPPROTO_TCP` | 使用 TCP 协议    |
| `ai_flags = AI_PASSIVE`     | 表示该地址用于服务器绑定 |

其中，`AI_PASSIVE` 是服务器端很重要的标志。

它表示：

```text
这个 Socket 准备用来绑定到本机地址，并等待客户端连接
```

---

## 七、调用 `getaddrinfo`

服务器端调用 `getaddrinfo` 时，官方示例中第一个参数写 `NULL`：

```cpp
int resultCode = getaddrinfo(NULL, DEFAULT_PORT, &hints, &result);
```

这里和客户端不同。

客户端通常会写服务器 IP，例如：

```cpp
getaddrinfo("127.0.0.1", DEFAULT_PORT, &hints, &result);
```

服务器端写 `NULL` 的意思是：

```text
使用本机地址
```

结合 `AI_PASSIVE`，它表示服务器准备在本机指定端口上接收连接。

完整代码：

```cpp
int resultCode = getaddrinfo(NULL, DEFAULT_PORT, &hints, &result);

if (resultCode != 0)
{
    cout << "getaddrinfo failed: " << resultCode << endl;
    WSACleanup();
    return 1;
}
```

---

## 八、创建 `ListenSocket`

服务器需要一个 Socket 用来监听客户端连接。

先声明：

```cpp
SOCKET listenSocket = INVALID_SOCKET;
```

然后调用 `socket` 创建：

```cpp
listenSocket = socket(result->ai_family, result->ai_socktype, result->ai_protocol);
```

参数来自 `getaddrinfo` 返回的 `result`：

| 参数                    | 含义        |
| --------------------- | --------- |
| `result->ai_family`   | 地址族       |
| `result->ai_socktype` | Socket 类型 |
| `result->ai_protocol` | 协议        |

因为前面设置的是 TCP，所以这里创建出来的是 TCP Socket。

---

## 九、检查 `ListenSocket` 是否创建成功

创建之后必须检查：

```cpp
if (listenSocket == INVALID_SOCKET)
{
    cout << "socket failed: " << WSAGetLastError() << endl;
    freeaddrinfo(result);
    WSACleanup();
    return 1;
}
```

如果返回 `INVALID_SOCKET`，说明 Socket 创建失败。

失败时要释放资源：

```cpp
freeaddrinfo(result);
WSACleanup();
```

---

## 十、本节完整代码片段

下面代码建立在已经初始化 Winsock 的基础上。

```cpp
#define DEFAULT_PORT "27015"

addrinfo *result = nullptr;
addrinfo hints{};

ZeroMemory(&hints, sizeof(hints));

hints.ai_family = AF_INET;
hints.ai_socktype = SOCK_STREAM;
hints.ai_protocol = IPPROTO_TCP;
hints.ai_flags = AI_PASSIVE;

int resultCode = getaddrinfo(NULL, DEFAULT_PORT, &hints, &result);

if (resultCode != 0)
{
    cout << "getaddrinfo failed: " << resultCode << endl;
    WSACleanup();
    return 1;
}

SOCKET listenSocket = INVALID_SOCKET;

listenSocket = socket(result->ai_family, result->ai_socktype, result->ai_protocol);

if (listenSocket == INVALID_SOCKET)
{
    cout << "socket failed: " << WSAGetLastError() << endl;
    freeaddrinfo(result);
    WSACleanup();
    return 1;
}
```

---

## 十一、服务器端目前的程序结构

目前服务器程序大概是：

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

    // 2. 设置服务器地址信息
    addrinfo *result = nullptr;
    addrinfo hints{};

    ZeroMemory(&hints, sizeof(hints));

    hints.ai_family = AF_INET;
    hints.ai_socktype = SOCK_STREAM;
    hints.ai_protocol = IPPROTO_TCP;
    hints.ai_flags = AI_PASSIVE;

    resultCode = getaddrinfo(NULL, "27015", &hints, &result);

    if (resultCode != 0)
    {
        cout << "getaddrinfo failed: " << resultCode << endl;
        WSACleanup();
        return 1;
    }

    // 3. 创建服务器监听 Socket
    SOCKET listenSocket = INVALID_SOCKET;

    listenSocket = socket(result->ai_family, result->ai_socktype, result->ai_protocol);

    if (listenSocket == INVALID_SOCKET)
    {
        cout << "socket failed: " << WSAGetLastError() << endl;
        freeaddrinfo(result);
        WSACleanup();
        return 1;
    }

    // 4. 下一步：绑定 Socket

    freeaddrinfo(result);
    closesocket(listenSocket);
    WSACleanup();

    return 0;
}
```

---

## 十二、本节小结

本节学习了服务器端如何创建 Socket。

需要记住：

1. 服务器端也需要先初始化 Winsock。
2. 服务器端创建的是用于监听的 Socket，通常叫 `ListenSocket`。
3. `AI_PASSIVE` 表示这个地址准备用于服务器绑定。
4. 服务器端 `getaddrinfo` 的第一个参数通常可以写 `NULL`。
5. `socket` 用于创建服务器监听 Socket。
6. 如果 `socket` 返回 `INVALID_SOCKET`，说明创建失败。
7. 创建失败时，要释放 `getaddrinfo` 返回的地址信息，并调用 `WSACleanup`。

最重要的代码是：

```cpp
hints.ai_flags = AI_PASSIVE;

getaddrinfo(NULL, DEFAULT_PORT, &hints, &result);

listenSocket = socket(result->ai_family, result->ai_socktype, result->ai_protocol);
```

下一步需要学习的是：绑定 Socket。

