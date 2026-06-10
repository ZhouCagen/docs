# 05 客户端发送和接收数据

## 一、本节目标

前面已经完成了客户端的三个步骤：

```text
初始化 Winsock
↓
创建客户端 Socket
↓
连接服务器
```

当客户端成功连接服务器之后，就可以开始发送和接收数据。

本节主要学习两个函数：

```cpp
send
recv
```

其中：

| 函数     | 作用            |
| ------ | ------------- |
| `send` | 客户端向服务器发送数据   |
| `recv` | 客户端接收服务器返回的数据 |

---

## 二、客户端发送和接收数据的流程

客户端连接服务器成功后，数据通信流程如下：

```text
准备要发送的数据
↓
调用 send 发送数据
↓
判断 send 是否成功
↓
调用 shutdown 关闭发送方向
↓
循环调用 recv 接收服务器数据
↓
服务器关闭连接后，recv 返回 0
↓
结束接收
```

注意：

```text
send 和 recv 是 TCP 通信中常用的发送、接收函数。
UDP 通信通常使用 sendto 和 recvfrom。
```

---

## 三、准备发送缓冲区和接收缓冲区

官方示例中先定义了缓冲区大小：

```cpp
#define DEFAULT_BUFLEN 512
```

然后定义发送内容和接收数组：

```cpp
int recvbuflen = DEFAULT_BUFLEN;

const char *sendbuf = "this is a test";
char recvbuf[DEFAULT_BUFLEN];
```

含义如下：

| 变量               | 含义             |
| ---------------- | -------------- |
| `DEFAULT_BUFLEN` | 缓冲区大小          |
| `sendbuf`        | 要发送给服务器的数据     |
| `recvbuf`        | 用来接收服务器返回数据的数组 |
| `recvbuflen`     | 接收缓冲区长度        |

---

## 四、使用 `send` 发送数据

客户端使用 `send` 向服务器发送数据。

基本写法：

```cpp
int result = send(connectSocket, sendbuf, static_cast<int>(strlen(sendbuf)), 0);
```

参数含义：

| 参数                | 含义                |
| ----------------- | ----------------- |
| `connectSocket`   | 已经连接成功的客户端 Socket |
| `sendbuf`         | 要发送的数据            |
| `strlen(sendbuf)` | 要发送的数据长度          |
| `0`               | 标志位，通常写 0         |

如果发送成功，`send` 返回实际发送的字节数。

如果发送失败，返回：

```cpp
SOCKET_ERROR
```

所以需要判断：

```cpp
if (result == SOCKET_ERROR)
{
    cout << "send failed: " << WSAGetLastError() << endl;
    closesocket(connectSocket);
    WSACleanup();
    return 1;
}
```

---

## 五、发送数据完整代码

```cpp
#define DEFAULT_BUFLEN 512

const char *sendbuf = "this is a test";

int result = send(connectSocket, sendbuf, static_cast<int>(strlen(sendbuf)), 0);

if (result == SOCKET_ERROR)
{
    cout << "send failed: " << WSAGetLastError() << endl;
    closesocket(connectSocket);
    WSACleanup();
    return 1;
}

cout << "Bytes sent: " << result << endl;
```

这段代码的作用是：

```text
把字符串 "this is a test" 发送给服务器
```

---

## 六、使用 `shutdown` 关闭发送方向

官方示例中，在客户端发送完数据后，会调用：

```cpp
shutdown(connectSocket, SD_SEND);
```

完整写法：

```cpp
result = shutdown(connectSocket, SD_SEND);

if (result == SOCKET_ERROR)
{
    cout << "shutdown failed: " << WSAGetLastError() << endl;
    closesocket(connectSocket);
    WSACleanup();
    return 1;
}
```

这里的 `SD_SEND` 表示：

```text
关闭发送方向
```

也就是说，客户端告诉服务器：

```text
我这边已经没有数据要继续发送了
```

但是注意：

```text
关闭发送方向后，客户端仍然可以继续接收服务器返回的数据。
```

---

## 七、使用 `recv` 接收数据

客户端使用 `recv` 接收服务器返回的数据。

基本写法：

```cpp
result = recv(connectSocket, recvbuf, recvbuflen, 0);
```

参数含义：

| 参数              | 含义                |
| --------------- | ----------------- |
| `connectSocket` | 已经连接成功的客户端 Socket |
| `recvbuf`       | 接收数据的缓冲区          |
| `recvbuflen`    | 缓冲区大小             |
| `0`             | 标志位，通常写 0         |

`recv` 的返回值有三种情况：

| 返回值   | 含义               |
| ----- | ---------------- |
| `> 0` | 成功接收到数据，返回接收的字节数 |
| `0`   | 对方关闭了连接          |
| `< 0` | 接收失败             |

---

## 八、循环接收服务器数据

官方示例中使用 `do while` 循环接收数据：

```cpp
char recvbuf[DEFAULT_BUFLEN];
int recvbuflen = DEFAULT_BUFLEN;

do
{
    result = recv(connectSocket, recvbuf, recvbuflen, 0);

    if (result > 0)
    {
        cout << "Bytes received: " << result << endl;
    }
    else if (result == 0)
    {
        cout << "Connection closed" << endl;
    }
    else
    {
        cout << "recv failed: " << WSAGetLastError() << endl;
    }

} while (result > 0);
```

这段代码的意思是：

```text
只要还能收到数据，就继续接收。
如果服务器关闭连接，recv 返回 0，循环结束。
如果接收失败，输出错误信息。
```

---

## 九、把接收到的数据打印出来

如果想看见服务器返回的具体内容，需要给字符数组补上字符串结束符：

```cpp
if (result > 0)
{
    recvbuf[result] = '\0';
    cout << "Server reply: " << recvbuf << endl;
}
```

但是要注意，数组大小需要多留一个位置给 `'\0'`。

所以接收时可以写成：

```cpp
result = recv(connectSocket, recvbuf, recvbuflen - 1, 0);
```

完整写法：

```cpp
char recvbuf[DEFAULT_BUFLEN];

do
{
    result = recv(connectSocket, recvbuf, DEFAULT_BUFLEN - 1, 0);

    if (result > 0)
    {
        recvbuf[result] = '\0';
        cout << "Server reply: " << recvbuf << endl;
    }
    else if (result == 0)
    {
        cout << "Connection closed" << endl;
    }
    else
    {
        cout << "recv failed: " << WSAGetLastError() << endl;
    }

} while (result > 0);
```

---

## 十、本节完整代码片段

下面这段代码应该放在客户端连接服务器成功之后。

```cpp
#define DEFAULT_BUFLEN 512

const char *sendbuf = "this is a test";
char recvbuf[DEFAULT_BUFLEN];

int result = send(connectSocket, sendbuf, static_cast<int>(strlen(sendbuf)), 0);

if (result == SOCKET_ERROR)
{
    cout << "send failed: " << WSAGetLastError() << endl;
    closesocket(connectSocket);
    WSACleanup();
    return 1;
}

cout << "Bytes sent: " << result << endl;

result = shutdown(connectSocket, SD_SEND);

if (result == SOCKET_ERROR)
{
    cout << "shutdown failed: " << WSAGetLastError() << endl;
    closesocket(connectSocket);
    WSACleanup();
    return 1;
}

do
{
    result = recv(connectSocket, recvbuf, DEFAULT_BUFLEN - 1, 0);

    if (result > 0)
    {
        recvbuf[result] = '\0';
        cout << "Server reply: " << recvbuf << endl;
    }
    else if (result == 0)
    {
        cout << "Connection closed" << endl;
    }
    else
    {
        cout << "recv failed: " << WSAGetLastError() << endl;
    }

} while (result > 0);
```

---

## 十一、本节小结

本节学习了客户端如何发送和接收数据。

需要记住：

1. TCP 客户端使用 `send` 发送数据。
2. TCP 客户端使用 `recv` 接收数据。
3. `send` 返回实际发送的字节数。
4. `recv` 返回实际接收的字节数。
5. `recv` 返回 0 表示对方关闭连接。
6. `shutdown(connectSocket, SD_SEND)` 表示关闭发送方向。
7. 关闭发送方向后，客户端仍然可以接收数据。

最重要的代码是：

```cpp
send(connectSocket, sendbuf, static_cast<int>(strlen(sendbuf)), 0);
recv(connectSocket, recvbuf, DEFAULT_BUFLEN - 1, 0);
```

下一步需要学习的是：客户端如何断开连接并释放资源。

