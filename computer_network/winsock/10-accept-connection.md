# 10 接受客户端连接

## 一、本节目标

前面服务器端已经完成：

```text
初始化 Winsock
↓
创建 ListenSocket
↓
绑定 Socket
↓
监听 Socket
```

此时服务器已经可以等待客户端连接。

本节主要学习：

```cpp
accept
```

`accept` 的作用是：

```text
接受一个客户端连接，并返回一个新的 Socket。
```

这个新的 Socket 通常叫：

```cpp
clientSocket
```

服务器之后和客户端真正收发数据，用的是 `clientSocket`，不是 `listenSocket`。

---

## 二、`listenSocket` 和 `clientSocket` 的区别

这是服务器端非常重要的概念。

| Socket         | 作用            |
| -------------- | ------------- |
| `listenSocket` | 负责监听客户端连接     |
| `clientSocket` | 负责和已经连接的客户端通信 |

可以简单理解为：

```text
listenSocket：门口接客的
clientSocket：真正和客人聊天的
```

服务器先用 `listenSocket` 等待连接。

当客户端连接过来时，服务器调用：

```cpp
accept
```

然后得到：

```cpp
clientSocket
```

后续：

```cpp
recv
send
```

都用 `clientSocket`。

---

## 三、声明 `clientSocket`

在接受客户端连接之前，需要先声明一个 `SOCKET` 对象：

```cpp
SOCKET clientSocket = INVALID_SOCKET;
```

这里初始化为 `INVALID_SOCKET`，表示当前还没有接受到有效客户端。

---

## 四、调用 `accept`

接受客户端连接的代码如下：

```cpp
clientSocket = accept(listenSocket, NULL, NULL);
```

参数含义：

| 参数             | 含义              |
| -------------- | --------------- |
| `listenSocket` | 正在监听的服务器 Socket |
| `NULL`         | 不关心客户端地址信息      |
| `NULL`         | 不关心客户端地址长度      |

如果暂时不需要获取客户端 IP 地址，可以直接写：

```cpp
accept(listenSocket, NULL, NULL);
```

如果以后想显示客户端 IP，再传入客户端地址结构。

---

## 五、判断是否接受成功

`accept` 失败时会返回：

```cpp
INVALID_SOCKET
```

所以需要判断：

```cpp
if (clientSocket == INVALID_SOCKET)
{
    cout << "accept failed: " << WSAGetLastError() << endl;
    closesocket(listenSocket);
    WSACleanup();
    return 1;
}
```

如果接受失败，就关闭 `listenSocket`，释放 Winsock 资源，然后结束程序。

---

## 六、`accept` 会阻塞

`accept` 有一个很重要的特点：

```text
如果当前没有客户端连接，accept 会等待。
```

也就是说，程序执行到这里：

```cpp
clientSocket = accept(listenSocket, NULL, NULL);
```

如果没有客户端连接进来，程序就会停在这一行。

这不是卡死，而是在等待客户端连接。

当客户端连接成功后，`accept` 才会返回一个 `clientSocket`。

---

## 七、接受连接后的处理

官方基础示例只接受一个客户端连接。

接受成功后，就可以继续进行：

```text
recv
send
```

也就是服务器从客户端接收数据，再把数据发送回客户端。

在这个基础示例中，接受到一个客户端连接后，就可以关闭 `listenSocket`：

```cpp
closesocket(listenSocket);
```

原因是：

```text
基础示例只处理一个客户端。
已经接受到一个客户端后，不再继续监听其他客户端。
```

但是在聊天室实验中，不能这么早关闭 `listenSocket`。

聊天室服务器应该一直保留 `listenSocket`，并不断接受新的客户端连接。

---

## 八、本节完整代码片段

下面代码应该放在 `listen` 成功之后。

```cpp
SOCKET clientSocket = INVALID_SOCKET;

clientSocket = accept(listenSocket, NULL, NULL);

if (clientSocket == INVALID_SOCKET)
{
    cout << "accept failed: " << WSAGetLastError() << endl;
    closesocket(listenSocket);
    WSACleanup();
    return 1;
}

cout << "Client connected." << endl;

// 官方基础示例只接受一个客户端，因此这里可以关闭 listenSocket
closesocket(listenSocket);
```

---

## 九、放进服务器程序中的位置

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

    // 6. 接受客户端连接
    SOCKET clientSocket = INVALID_SOCKET;

    clientSocket = accept(listenSocket, NULL, NULL);

    if (clientSocket == INVALID_SOCKET)
    {
        cout << "accept failed: " << WSAGetLastError() << endl;
        closesocket(listenSocket);
        WSACleanup();
        return 1;
    }

    cout << "Client connected." << endl;

    // 基础示例只接受一个客户端，因此可以关闭监听 Socket
    closesocket(listenSocket);

    // 7. 下一步：接收和发送数据

    closesocket(clientSocket);
    WSACleanup();

    return 0;
}
```

---

## 十、单客户端服务器和多客户端服务器的区别

官方基础示例是单客户端服务器：

```text
listen
↓
accept 一个客户端
↓
关闭 listenSocket
↓
和这个客户端通信
↓
结束
```

聊天室实验需要多客户端服务器：

```text
listen
↓
while 循环
↓
accept 一个客户端
↓
创建线程处理该客户端
↓
继续 accept 下一个客户端
```

所以后面写聊天室时，服务器不能在第一次 `accept` 后就直接关闭 `listenSocket`。

---

## 十一、本节小结

本节学习了服务器端如何接受客户端连接。

需要记住：

1. `accept` 用于接受客户端连接。
2. `accept` 的参数是正在监听的 `listenSocket`。
3. `accept` 成功后返回一个新的 `clientSocket`。
4. 后续和客户端通信使用 `clientSocket`。
5. `listenSocket` 只负责监听新连接。
6. `accept` 在没有客户端连接时会等待。
7. 官方基础示例只接受一个客户端，所以接受成功后可以关闭 `listenSocket`。
8. 多客户端聊天室不能这么早关闭 `listenSocket`。

最重要的代码是：

```cpp
SOCKET clientSocket = INVALID_SOCKET;

clientSocket = accept(listenSocket, NULL, NULL);

if (clientSocket == INVALID_SOCKET)
{
    cout << "accept failed: " << WSAGetLastError() << endl;
    closesocket(listenSocket);
    WSACleanup();
    return 1;
}
```

下一步需要学习的是：服务器如何接收和发送数据。

