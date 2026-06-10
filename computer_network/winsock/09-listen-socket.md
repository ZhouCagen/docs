# 09 侦听 Socket

## 一、本节目标

前面服务器端已经完成了：

```text
初始化 Winsock
↓
创建 ListenSocket
↓
绑定 IP 地址和端口号
```

绑定完成后，服务器还不能直接接收客户端连接。

下一步需要让服务器进入监听状态。

本节主要学习：

```cpp
listen
```

`listen` 的作用是：

```text
让服务器 Socket 开始监听客户端的连接请求。
```

可以简单理解为：

```text
服务器已经站在指定端口上，开始等待客户端来连接。
```

---

## 二、为什么需要 `listen`

服务器绑定端口后，只是说明：

```text
服务器占用了这个端口。
```

但是客户端连接请求来了以后，服务器还需要一个机制来等待这些连接请求。

这个机制就是：

```cpp
listen
```

服务器端 TCP 通信流程是：

```text
socket
↓
bind
↓
listen
↓
accept
```

其中：

| 函数       | 作用        |
| -------- | --------- |
| `socket` | 创建 Socket |
| `bind`   | 绑定 IP 和端口 |
| `listen` | 开始监听客户端连接 |
| `accept` | 接受客户端连接   |

---

## 三、`listen` 函数的基本写法

官方示例中的写法如下：

```cpp
if (listen(listenSocket, SOMAXCONN) == SOCKET_ERROR)
{
    cout << "listen failed: " << WSAGetLastError() << endl;
    closesocket(listenSocket);
    WSACleanup();
    return 1;
}
```

这里最核心的是：

```cpp
listen(listenSocket, SOMAXCONN);
```

参数含义如下：

| 参数             | 含义                  |
| -------------- | ------------------- |
| `listenSocket` | 已经创建并绑定好的服务器 Socket |
| `SOMAXCONN`    | 挂起连接队列的最大合理长度       |

---

## 四、什么是 `SOMAXCONN`

`SOMAXCONN` 是一个特殊常量。

可以简单理解为：

```text
让系统使用一个合理的最大等待连接队列长度。
```

当多个客户端同时连接服务器时，连接请求会先进入一个等待队列。

`listen` 的第二个参数就是设置这个队列的长度。

在实验中，直接写：

```cpp
SOMAXCONN
```

即可。

---

## 五、判断监听是否成功

`listen` 调用后，也需要判断是否成功。

如果失败，它会返回：

```cpp
SOCKET_ERROR
```

所以一般写成：

```cpp
if (listen(listenSocket, SOMAXCONN) == SOCKET_ERROR)
{
    cout << "listen failed: " << WSAGetLastError() << endl;
    closesocket(listenSocket);
    WSACleanup();
    return 1;
}
```

如果监听失败，后面就不能继续调用 `accept`。

---

## 六、本节完整代码片段

下面代码应该接在 `bind` 成功之后。

```cpp
if (listen(listenSocket, SOMAXCONN) == SOCKET_ERROR)
{
    cout << "listen failed: " << WSAGetLastError() << endl;
    closesocket(listenSocket);
    WSACleanup();
    return 1;
}

cout << "Server is listening..." << endl;
```

这段代码运行成功后，说明服务器已经开始等待客户端连接。

---

## 七、放进服务器程序中的位置

服务器程序目前结构如下：

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

    // 3. 创建 ListenSocket
    SOCKET listenSocket = INVALID_SOCKET;

    listenSocket = socket(result->ai_family, result->ai_socktype, result->ai_protocol);

    if (listenSocket == INVALID_SOCKET)
    {
        cout << "socket failed: " << WSAGetLastError() << endl;
        freeaddrinfo(result);
        WSACleanup();
        return 1;
    }

    // 4. 绑定 Socket
    resultCode = bind(listenSocket, result->ai_addr, static_cast<int>(result->ai_addrlen));

    if (resultCode == SOCKET_ERROR)
    {
        cout << "bind failed: " << WSAGetLastError() << endl;
        freeaddrinfo(result);
        closesocket(listenSocket);
        WSACleanup();
        return 1;
    }

    freeaddrinfo(result);

    // 5. 监听 Socket
    if (listen(listenSocket, SOMAXCONN) == SOCKET_ERROR)
    {
        cout << "listen failed: " << WSAGetLastError() << endl;
        closesocket(listenSocket);
        WSACleanup();
        return 1;
    }

    cout << "Server is listening..." << endl;

    // 6. 下一步：接受客户端连接

    closesocket(listenSocket);
    WSACleanup();

    return 0;
}
```

---

## 八、运行到这里会发生什么

如果程序运行成功，会显示：

```text
Server is listening...
```

此时服务器已经在指定端口等待客户端连接。

但是当前程序还没有写：

```cpp
accept
```

所以它还不能真正接收客户端连接。

下一步需要调用 `accept`。

---

## 九、`bind` 和 `listen` 的区别

| 函数       | 作用                |
| -------- | ----------------- |
| `bind`   | 绑定 IP 和端口         |
| `listen` | 在这个 IP 和端口上等待连接请求 |

可以这样理解：

```text
bind：占座
listen：开始等人来
accept：真正接待一个人
```

---

## 十、本节小结

本节学习了服务器端如何监听 Socket。

需要记住：

1. `listen` 用于让服务器进入监听状态。
2. 调用 `listen` 前，必须先完成 `bind`。
3. `listen` 的第一个参数是服务器监听 Socket。
4. `listen` 的第二个参数是等待连接队列长度。
5. 实验中可以直接使用 `SOMAXCONN`。
6. 如果 `listen` 返回 `SOCKET_ERROR`，说明监听失败。
7. 监听成功后，下一步才能调用 `accept`。

最重要的代码是：

```cpp
if (listen(listenSocket, SOMAXCONN) == SOCKET_ERROR)
{
    cout << "listen failed: " << WSAGetLastError() << endl;
    closesocket(listenSocket);
    WSACleanup();
    return 1;
}
```

下一步需要学习的是：接受客户端连接。

