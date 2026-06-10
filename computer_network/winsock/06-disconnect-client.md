# 06 断开客户端连接

## 一、本节目标

客户端完成发送和接收数据之后，需要正确断开连接并释放资源。

本节主要学习三个函数：

```cpp
shutdown
closesocket
WSACleanup
```

它们的作用分别是：

| 函数            | 作用                   |
| ------------- | -------------------- |
| `shutdown`    | 关闭 Socket 的发送方向或接收方向 |
| `closesocket` | 关闭 Socket            |
| `WSACleanup`  | 释放 Winsock 资源        |

---

## 二、客户端断开连接的流程

客户端断开连接的基本流程如下：

```text
发送数据完成
↓
调用 shutdown 关闭发送方向
↓
继续接收服务器返回的数据
↓
接收完成后调用 closesocket
↓
调用 WSACleanup
↓
程序结束
```

---

## 三、为什么要调用 `shutdown`

当客户端不再发送数据时，可以调用：

```cpp
shutdown(connectSocket, SD_SEND);
```

这表示：

```text
客户端不再向服务器发送数据
```

但是客户端仍然可以继续接收服务器发送回来的数据。

可以理解为：

```text
我说完了，但我还能听你说。
```

---

## 四、`shutdown` 的基本写法

```cpp
int result = shutdown(connectSocket, SD_SEND);

if (result == SOCKET_ERROR)
{
    cout << "shutdown failed: " << WSAGetLastError() << endl;
    closesocket(connectSocket);
    WSACleanup();
    return 1;
}
```

参数含义：

| 参数              | 含义                |
| --------------- | ----------------- |
| `connectSocket` | 已经连接成功的客户端 Socket |
| `SD_SEND`       | 关闭发送方向            |

如果 `shutdown` 返回：

```cpp
SOCKET_ERROR
```

说明关闭发送方向失败。

这时应该关闭 Socket，并释放 Winsock 资源。

---

## 五、为什么还要调用 `closesocket`

`shutdown` 只是关闭某个方向的数据传输。

真正关闭 Socket，需要调用：

```cpp
closesocket(connectSocket);
```

也就是说：

```text
shutdown：告诉对方我不再发送了
closesocket：真正关闭这个 Socket
```

客户端完成全部通信后，应该调用：

```cpp
closesocket(connectSocket);
```

---

## 六、为什么最后要调用 `WSACleanup`

程序开始时调用了：

```cpp
WSAStartup
```

程序结束前应该调用：

```cpp
WSACleanup
```

这表示释放 Winsock 相关资源。

基本结构是：

```cpp
WSAStartup(MAKEWORD(2, 2), &wsaData);

// socket 通信过程

WSACleanup();
```

---

## 七、客户端清理资源的标准代码

客户端完成数据接收后，可以这样写：

```cpp
closesocket(connectSocket);
WSACleanup();

return 0;
```

如果之前已经调用过 `shutdown`，完整结构一般是：

```cpp
int result = shutdown(connectSocket, SD_SEND);

if (result == SOCKET_ERROR)
{
    cout << "shutdown failed: " << WSAGetLastError() << endl;
    closesocket(connectSocket);
    WSACleanup();
    return 1;
}

// 继续 recv 接收服务器数据

closesocket(connectSocket);
WSACleanup();

return 0;
```

---

## 八、完整客户端大致流程

目前客户端的完整流程可以整理成：

```text
WSAStartup
↓
getaddrinfo
↓
socket
↓
connect
↓
send
↓
shutdown
↓
recv
↓
closesocket
↓
WSACleanup
```

对应含义如下：

| 步骤            | 作用            |
| ------------- | ------------- |
| `WSAStartup`  | 初始化 Winsock   |
| `getaddrinfo` | 获取服务器地址信息     |
| `socket`      | 创建客户端 Socket  |
| `connect`     | 连接服务器         |
| `send`        | 发送数据          |
| `shutdown`    | 关闭发送方向        |
| `recv`        | 接收服务器数据       |
| `closesocket` | 关闭 Socket     |
| `WSACleanup`  | 释放 Winsock 资源 |

---

## 九、常见错误

### 1. 忘记关闭 Socket

错误写法：

```cpp
WSACleanup();
return 0;
```

更完整的写法：

```cpp
closesocket(connectSocket);
WSACleanup();
return 0;
```

---

### 2. 初始化失败后还继续运行

错误写法：

```cpp
if (result != 0)
{
    cout << "WSAStartup failed" << endl;
}

socket(...);
```

正确写法：

```cpp
if (result != 0)
{
    cout << "WSAStartup failed" << endl;
    return 1;
}
```

初始化失败后，不应该继续调用 Socket 相关函数。

---

### 3. Socket 创建失败后不释放资源

如果 `socket` 创建失败，应该释放 `getaddrinfo` 返回的地址信息，并调用 `WSACleanup`：

```cpp
if (connectSocket == INVALID_SOCKET)
{
    cout << "socket failed: " << WSAGetLastError() << endl;
    freeaddrinfo(result);
    WSACleanup();
    return 1;
}
```

---

## 十、本节小结

本节学习了客户端如何断开连接。

需要记住：

1. `shutdown(connectSocket, SD_SEND)` 表示关闭发送方向。
2. 调用 `shutdown` 后，客户端仍然可以继续接收服务器数据。
3. `closesocket` 用来真正关闭 Socket。
4. `WSACleanup` 用来释放 Winsock 资源。
5. 程序开始有 `WSAStartup`，程序结束就应该有 `WSACleanup`。
6. Socket 不再使用时，应该调用 `closesocket`。

最重要的代码是：

```cpp
shutdown(connectSocket, SD_SEND);
closesocket(connectSocket);
WSACleanup();
```

下一步开始学习服务器端：为服务器创建 Socket。

