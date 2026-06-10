# 04 连接到 Socket

## 一、本节目标

上一节已经创建了客户端 Socket：

```cpp
SOCKET connectSocket = socket(ptr->ai_family, ptr->ai_socktype, ptr->ai_protocol);
```

但是此时客户端还没有真正连接到服务器。

本节要学习的是：

```cpp
connect
```

`connect` 的作用是让客户端主动连接服务器。

可以简单理解为：

```text
客户端拿着自己的 Socket，去连接指定 IP 和端口上的服务器
```

---

## 二、客户端连接服务器的流程

客户端连接服务器的基本流程如下：

```text
已经初始化 Winsock
↓
已经创建客户端 Socket
↓
调用 connect 连接服务器
↓
判断连接是否成功
↓
释放 getaddrinfo 返回的地址信息
↓
连接成功后继续发送和接收数据
```

---

## 三、`connect` 函数的作用

`connect` 用于客户端主动连接服务器。

基本写法：

```cpp
resultCode = connect(connectSocket, ptr->ai_addr, static_cast<int>(ptr->ai_addrlen));
```

它需要三个参数：

| 参数                | 含义               |
| ----------------- | ---------------- |
| `connectSocket`   | 客户端已经创建好的 Socket |
| `ptr->ai_addr`    | 服务器地址信息          |
| `ptr->ai_addrlen` | 服务器地址结构的长度       |

其中，服务器地址信息来自上一节的 `getaddrinfo`。

---

## 四、连接服务器的代码

连接服务器的基本代码如下：

```cpp
resultCode = connect(connectSocket, ptr->ai_addr, static_cast<int>(ptr->ai_addrlen));

if (resultCode == SOCKET_ERROR)
{
    closesocket(connectSocket);
    connectSocket = INVALID_SOCKET;
}
```

如果 `connect` 返回 `SOCKET_ERROR`，说明连接失败。

连接失败时需要关闭当前 Socket：

```cpp
closesocket(connectSocket);
```

然后把它重新设置成：

```cpp
INVALID_SOCKET
```

表示当前没有有效连接。

---

## 五、释放地址信息

`getaddrinfo` 返回的地址信息使用完后，需要释放：

```cpp
freeaddrinfo(result);
```

注意：

```text
freeaddrinfo 释放的是 getaddrinfo 申请的地址信息
closesocket 关闭的是 Socket
WSACleanup 释放的是 Winsock 库资源
```

它们负责的资源不同，不要混淆。

---

## 六、判断最终是否连接成功

连接之后，需要判断 `connectSocket` 是否还是有效 Socket：

```cpp
if (connectSocket == INVALID_SOCKET)
{
    cout << "Unable to connect to server!" << endl;
    WSACleanup();
    return 1;
}
```

如果它是 `INVALID_SOCKET`，说明客户端没有成功连接服务器。

常见原因包括：

1. 服务器程序没有启动。
2. 服务器端口号写错。
3. 服务器 IP 地址写错。
4. 防火墙阻止了连接。
5. 客户端和服务器不在同一个网络环境下。

---

## 七、本节完整代码片段

下面代码应该接在“创建客户端 Socket”后面。

```cpp
resultCode = connect(connectSocket, ptr->ai_addr, static_cast<int>(ptr->ai_addrlen));

if (resultCode == SOCKET_ERROR)
{
    closesocket(connectSocket);
    connectSocket = INVALID_SOCKET;
}

freeaddrinfo(result);

if (connectSocket == INVALID_SOCKET)
{
    cout << "Unable to connect to server!" << endl;
    WSACleanup();
    return 1;
}

cout << "Connected to server successfully." << endl;
```

---

## 八、放进完整客户端程序中的位置

客户端程序目前的大致结构如下：

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
    addrinfo *ptr = nullptr;
    addrinfo hints{};

    ZeroMemory(&hints, sizeof(hints));

    hints.ai_family = AF_INET;
    hints.ai_socktype = SOCK_STREAM;
    hints.ai_protocol = IPPROTO_TCP;

    resultCode = getaddrinfo("127.0.0.1", "27015", &hints, &result);

    if (resultCode != 0)
    {
        cout << "getaddrinfo failed: " << resultCode << endl;
        WSACleanup();
        return 1;
    }

    // 3. 创建 Socket
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

    // 4. 连接服务器
    resultCode = connect(connectSocket, ptr->ai_addr, static_cast<int>(ptr->ai_addrlen));

    if (resultCode == SOCKET_ERROR)
    {
        closesocket(connectSocket);
        connectSocket = INVALID_SOCKET;
    }

    freeaddrinfo(result);

    if (connectSocket == INVALID_SOCKET)
    {
        cout << "Unable to connect to server!" << endl;
        WSACleanup();
        return 1;
    }

    cout << "Connected to server successfully." << endl;

    // 5. 发送和接收数据
    // 下一节学习

    // 6. 关闭 Socket
    closesocket(connectSocket);
    WSACleanup();

    return 0;
}
```

---

## 九、现在程序为什么可能连接失败

如果现在直接运行客户端，大概率会输出：

```text
Unable to connect to server!
```

这是正常的。

原因是：

```text
客户端要连接 127.0.0.1:27015
但是当前还没有服务器程序在 27015 端口监听
```

所以客户端连接服务器必须满足：

```text
服务器已经启动
服务器正在监听对应端口
客户端 IP 写对
客户端端口写对
```

也就是说，后面还需要写服务器端程序。

---

## 十、`127.0.0.1` 是什么

`127.0.0.1` 表示本机地址，也叫 localhost。

如果客户端和服务器在同一台电脑上运行，可以写：

```cpp
getaddrinfo("127.0.0.1", "27015", &hints, &result);
```

如果客户端和服务器在不同电脑上运行，需要把 `127.0.0.1` 改成服务器电脑的 IP 地址，例如：

```cpp
getaddrinfo("192.168.1.10", "27015", &hints, &result);
```

---

## 十一、本节小结

本节学习了客户端如何连接服务器。

需要记住：

1. `connect` 用于客户端主动连接服务器。
2. `connectSocket` 是客户端已经创建好的 Socket。
3. `ptr->ai_addr` 保存服务器 IP 和端口信息。
4. `ptr->ai_addrlen` 是服务器地址结构的长度。
5. 如果 `connect` 返回 `SOCKET_ERROR`，说明连接失败。
6. 连接失败时需要 `closesocket`。
7. `getaddrinfo` 返回的地址信息使用完后，需要 `freeaddrinfo`。
8. 没有服务器监听时，客户端连接会失败。

最重要的代码是：

```cpp
resultCode = connect(connectSocket, ptr->ai_addr, static_cast<int>(ptr->ai_addrlen));

if (resultCode == SOCKET_ERROR)
{
    closesocket(connectSocket);
    connectSocket = INVALID_SOCKET;
}

freeaddrinfo(result);

if (connectSocket == INVALID_SOCKET)
{
    cout << "Unable to connect to server!" << endl;
    WSACleanup();
    return 1;
}
```

下一步需要学习的是：客户端如何发送和接收数据。

