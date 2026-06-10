# 12 断开服务器连接

## 一、本节目标

服务器完成数据接收和发送后，需要正确断开连接并释放资源。

本节主要学习三个函数：

```cpp
shutdown
closesocket
WSACleanup
```

它们的作用分别是：

| 函数            | 作用                |
| ------------- | ----------------- |
| `shutdown`    | 关闭 Socket 的某个通信方向 |
| `closesocket` | 关闭 Socket         |
| `WSACleanup`  | 释放 Winsock 资源     |

---

## 二、服务器断开连接的流程

服务器端断开连接的基本流程如下：

```text
服务器完成 recv / send
↓
调用 shutdown 关闭发送方向
↓
调用 closesocket 关闭客户端 Socket
↓
调用 WSACleanup 释放 Winsock 资源
↓
程序结束
```

---

## 三、为什么服务器也要调用 `shutdown`

当服务器不再向客户端发送数据时，可以调用：

```cpp
shutdown(clientSocket, SD_SEND);
```

这里的 `SD_SEND` 表示：

```text
关闭发送方向
```

可以理解为：

```text
服务器告诉客户端：我这边已经没有数据要继续发送了。
```

注意：

```text
shutdown 不等于 closesocket。
shutdown 只是关闭发送或接收方向。
closesocket 才是真正关闭 Socket。
```

---

## 四、`shutdown` 的基本写法

服务器端关闭发送方向：

```cpp
int result = shutdown(clientSocket, SD_SEND);

if (result == SOCKET_ERROR)
{
    cout << "shutdown failed: " << WSAGetLastError() << endl;
    closesocket(clientSocket);
    WSACleanup();
    return 1;
}
```

含义如下：

| 代码                                | 含义               |
| --------------------------------- | ---------------- |
| `shutdown(clientSocket, SD_SEND)` | 关闭服务器向客户端发送数据的方向 |
| `SOCKET_ERROR`                    | 表示关闭失败           |
| `closesocket(clientSocket)`       | 关闭客户端 Socket     |
| `WSACleanup()`                    | 释放 Winsock 资源    |

---

## 五、为什么还要调用 `closesocket`

`shutdown` 只是关闭发送方向。

真正释放 Socket，需要调用：

```cpp
closesocket(clientSocket);
```

可以简单理解为：

```text
shutdown：通知对方我不发了
closesocket：把这个通信通道关掉
```

所以服务器结束通信时，至少应该有：

```cpp
shutdown(clientSocket, SD_SEND);
closesocket(clientSocket);
```

---

## 六、为什么最后要调用 `WSACleanup`

程序一开始调用了：

```cpp
WSAStartup
```

程序结束时应该调用：

```cpp
WSACleanup
```

它的作用是：

```text
释放 Windows Socket 库相关资源
```

完整结构是：

```cpp
WSAStartup(MAKEWORD(2, 2), &wsaData);

// Socket 通信代码

WSACleanup();
```

---

## 七、服务器断开连接标准代码

服务器完成 `recv / send` 循环后，可以写：

```cpp
int result = shutdown(clientSocket, SD_SEND);

if (result == SOCKET_ERROR)
{
    cout << "shutdown failed: " << WSAGetLastError() << endl;
    closesocket(clientSocket);
    WSACleanup();
    return 1;
}

closesocket(clientSocket);
WSACleanup();

return 0;
```

---

## 八、什么时候关闭 `listenSocket`

在官方基础示例中，服务器只接受一个客户端连接。

所以在：

```cpp
clientSocket = accept(listenSocket, NULL, NULL);
```

成功之后，可以关闭：

```cpp
closesocket(listenSocket);
```

因为基础示例后面不再接受新的客户端。

流程是：

```text
accept 一个客户端
↓
关闭 listenSocket
↓
使用 clientSocket 和这个客户端通信
↓
通信结束后关闭 clientSocket
```

但是在聊天室实验中，不能这么写。

聊天室服务器需要一直接受新客户端，所以 `listenSocket` 需要一直保留。

聊天室服务器的流程应该是：

```text
listenSocket 一直监听
↓
accept 一个客户端
↓
创建线程处理该客户端
↓
继续 accept 下一个客户端
```

---

## 九、`listenSocket` 和 `clientSocket` 的关闭时机

| Socket         | 关闭时机          |
| -------------- | ------------- |
| `listenSocket` | 服务器不再接受新连接时关闭 |
| `clientSocket` | 某个客户端通信结束时关闭  |

在单客户端示例中：

```text
accept 成功后，就可以关闭 listenSocket
```

在多客户端聊天室中：

```text
服务器退出时才关闭 listenSocket
每个客户端断开时关闭对应 clientSocket
```

---

## 十、服务器完整基础流程

到这里，官方基础 TCP 服务器流程已经完整：

```text
WSAStartup
↓
getaddrinfo
↓
socket
↓
bind
↓
freeaddrinfo
↓
listen
↓
accept
↓
closesocket(listenSocket)
↓
recv / send
↓
shutdown(clientSocket, SD_SEND)
↓
closesocket(clientSocket)
↓
WSACleanup
```

对应含义如下：

| 步骤            | 作用            |
| ------------- | ------------- |
| `WSAStartup`  | 初始化 Winsock   |
| `getaddrinfo` | 获取服务器地址信息     |
| `socket`      | 创建监听 Socket   |
| `bind`        | 绑定 IP 和端口     |
| `listen`      | 开始监听客户端连接     |
| `accept`      | 接受客户端连接       |
| `recv`        | 接收客户端数据       |
| `send`        | 向客户端发送数据      |
| `shutdown`    | 关闭发送方向        |
| `closesocket` | 关闭 Socket     |
| `WSACleanup`  | 释放 Winsock 资源 |

---

## 十一、常见错误

### 1. 只调用 `shutdown`，忘记 `closesocket`

错误写法：

```cpp
shutdown(clientSocket, SD_SEND);
WSACleanup();
```

更完整的写法：

```cpp
shutdown(clientSocket, SD_SEND);
closesocket(clientSocket);
WSACleanup();
```

---

### 2. 关闭错 Socket

错误写法：

```cpp
closesocket(listenSocket);
```

如果这时真正正在通信的是客户端连接，那么应该关闭：

```cpp
closesocket(clientSocket);
```

---

### 3. 聊天室服务器过早关闭 `listenSocket`

单客户端服务器可以：

```cpp
closesocket(listenSocket);
```

但是聊天室服务器不能在第一次 `accept` 后就关闭 `listenSocket`。

否则后面的客户端就无法连接服务器。

---

## 十二、本节小结

本节学习了服务器如何断开连接。

需要记住：

1. `shutdown(clientSocket, SD_SEND)` 表示服务器不再发送数据。
2. `shutdown` 不是真正关闭 Socket。
3. `closesocket` 才是真正关闭 Socket。
4. `WSACleanup` 用于释放 Winsock 资源。
5. 单客户端示例可以在 `accept` 后关闭 `listenSocket`。
6. 多客户端聊天室不能过早关闭 `listenSocket`。
7. `listenSocket` 负责监听连接。
8. `clientSocket` 负责和客户端通信。

最重要的代码是：

```cpp
shutdown(clientSocket, SD_SEND);
closesocket(clientSocket);
WSACleanup();
```

下一步需要整理完整 TCP 客户端和服务器流程。

