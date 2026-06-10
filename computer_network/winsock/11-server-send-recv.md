# 11 服务器接收和发送数据

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
↓
接受客户端连接，得到 ClientSocket
```

接受客户端连接之后，服务器就可以和客户端进行数据通信。

本节主要学习：

```cpp
recv
send
```

其中：

| 函数     | 作用            |
| ------ | ------------- |
| `recv` | 服务器接收客户端发送的数据 |
| `send` | 服务器向客户端发送数据   |

注意：

服务器真正和客户端通信时，使用的是：

```cpp
clientSocket
```

而不是：

```cpp
listenSocket
```

---

## 二、服务器接收和发送数据的流程

服务器端接收和发送数据的流程如下：

```text
等待客户端发送数据
↓
调用 recv 接收数据
↓
判断 recv 返回值
↓
如果收到数据，就处理数据
↓
调用 send 把数据发送回客户端
↓
继续 recv
↓
客户端关闭连接后，recv 返回 0
↓
服务器结束通信
```

在官方基础示例中，服务器收到客户端发来的数据后，会直接把原数据发送回去。

这种方式叫：

```text
回显 Echo
```

也就是：

```text
客户端发什么，服务器就回什么。
```

---

## 三、准备接收缓冲区

服务器需要准备一个字符数组，用来保存客户端发送的数据：

```cpp
#define DEFAULT_BUFLEN 512

char recvBuffer[DEFAULT_BUFLEN];
int recvBufferLen = DEFAULT_BUFLEN;
```

含义如下：

| 变量               | 含义        |
| ---------------- | --------- |
| `DEFAULT_BUFLEN` | 缓冲区大小     |
| `recvBuffer`     | 用来接收客户端数据 |
| `recvBufferLen`  | 接收缓冲区长度   |

---

## 四、使用 `recv` 接收数据

服务器接收客户端数据的基本写法：

```cpp
int result = recv(clientSocket, recvBuffer, recvBufferLen, 0);
```

参数含义如下：

| 参数              | 含义                |
| --------------- | ----------------- |
| `clientSocket`  | 已经连接成功的客户端 Socket |
| `recvBuffer`    | 接收数据的缓冲区          |
| `recvBufferLen` | 缓冲区大小             |
| `0`             | 标志位，通常写 0         |

`recv` 的返回值有三种情况：

| 返回值   | 含义               |
| ----- | ---------------- |
| `> 0` | 成功接收到数据，返回收到的字节数 |
| `0`   | 客户端关闭连接          |
| `< 0` | 接收失败             |

---

## 五、判断 `recv` 结果

基本判断逻辑如下：

```cpp
if (result > 0)
{
    cout << "Bytes received: " << result << endl;
}
else if (result == 0)
{
    cout << "Connection closing..." << endl;
}
else
{
    cout << "recv failed: " << WSAGetLastError() << endl;
}
```

解释如下：

```text
result > 0：确实收到了数据
result == 0：客户端正常关闭连接
result < 0：接收过程中发生错误
```

---

## 六、把收到的数据打印出来

如果要把客户端发来的字符串显示出来，需要手动添加字符串结束符：

```cpp
recvBuffer[result] = '\0';
cout << "Client says: " << recvBuffer << endl;
```

为了避免数组越界，接收时建议给 `'\0'` 留一个位置：

```cpp
result = recv(clientSocket, recvBuffer, DEFAULT_BUFLEN - 1, 0);
```

完整写法：

```cpp
result = recv(clientSocket, recvBuffer, DEFAULT_BUFLEN - 1, 0);

if (result > 0)
{
    recvBuffer[result] = '\0';
    cout << "Client says: " << recvBuffer << endl;
}
```

---

## 七、使用 `send` 回复客户端

服务器收到客户端数据后，可以使用 `send` 把数据发回去：

```cpp
int sendResult = send(clientSocket, recvBuffer, result, 0);
```

参数含义如下：

| 参数             | 含义                |
| -------------- | ----------------- |
| `clientSocket` | 已经连接成功的客户端 Socket |
| `recvBuffer`   | 要发送的数据            |
| `result`       | 要发送的数据长度          |
| `0`            | 标志位，通常写 0         |

这里的 `result` 是刚才 `recv` 返回的字节数。

也就是说：

```text
刚才收到多少字节，就发回多少字节。
```

---

## 八、判断 `send` 是否成功

`send` 失败时会返回：

```cpp
SOCKET_ERROR
```

所以要判断：

```cpp
if (sendResult == SOCKET_ERROR)
{
    cout << "send failed: " << WSAGetLastError() << endl;
    closesocket(clientSocket);
    WSACleanup();
    return 1;
}
```

如果发送失败，说明当前通信已经出现问题，应该关闭客户端 Socket 并释放 Winsock 资源。

---

## 九、服务器循环接收和回显

官方基础示例使用循环不断接收客户端数据。

整理成 C++ 写法如下：

```cpp
#define DEFAULT_BUFLEN 512

char recvBuffer[DEFAULT_BUFLEN];
int result;
int sendResult;

do
{
    result = recv(clientSocket, recvBuffer, DEFAULT_BUFLEN - 1, 0);

    if (result > 0)
    {
        recvBuffer[result] = '\0';

        cout << "Bytes received: " << result << endl;
        cout << "Client says: " << recvBuffer << endl;

        sendResult = send(clientSocket, recvBuffer, result, 0);

        if (sendResult == SOCKET_ERROR)
        {
            cout << "send failed: " << WSAGetLastError() << endl;
            closesocket(clientSocket);
            WSACleanup();
            return 1;
        }

        cout << "Bytes sent: " << sendResult << endl;
    }
    else if (result == 0)
    {
        cout << "Connection closing..." << endl;
    }
    else
    {
        cout << "recv failed: " << WSAGetLastError() << endl;
        closesocket(clientSocket);
        WSACleanup();
        return 1;
    }

} while (result > 0);
```

---

## 十、为什么要使用循环

TCP 是持续连接。

客户端可能不只发送一次数据。

所以服务器通常需要循环调用：

```cpp
recv
```

只要客户端还在发送数据，服务器就继续接收。

当客户端关闭连接时：

```cpp
recv 返回 0
```

循环结束。

---

## 十一、回显服务器是什么意思

本节代码实现的是一个最基础的回显服务器。

流程是：

```text
客户端发送：hello
服务器接收：hello
服务器回复：hello
客户端收到：hello
```

这种程序虽然简单，但非常适合用来验证 TCP 通信是否成功。

如果回显服务器能正常运行，就说明：

```text
客户端能连接服务器
客户端能发送数据
服务器能接收数据
服务器能返回数据
客户端能接收返回数据
```

---

## 十二、放进服务器程序中的位置

服务器完整流程目前是：

```text
WSAStartup
↓
getaddrinfo
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
shutdown
↓
closesocket
↓
WSACleanup
```

本节代码应该放在：

```cpp
cout << "Client connected." << endl;
```

之后，也就是 `accept` 成功之后。

示意结构：

```cpp
// accept 成功
cout << "Client connected." << endl;

// 基础示例只处理一个客户端，所以可以关闭 listenSocket
closesocket(listenSocket);

// 接收和发送数据
do
{
    result = recv(clientSocket, recvBuffer, DEFAULT_BUFLEN - 1, 0);

    // 判断 result
    // 如果收到数据，就 send 回去

} while (result > 0);
```

---

## 十三、本节小结

本节学习了服务器如何接收和发送数据。

需要记住：

1. 服务器和客户端真正通信使用的是 `clientSocket`。
2. `listenSocket` 只负责监听连接。
3. `recv` 用于接收客户端数据。
4. `send` 用于向客户端发送数据。
5. `recv` 返回正数表示收到数据。
6. `recv` 返回 0 表示客户端关闭连接。
7. `recv` 返回负数表示接收失败。
8. 回显服务器就是客户端发什么，服务器回什么。
9. 循环 `recv` 可以持续接收客户端数据。

最重要的代码是：

```cpp
result = recv(clientSocket, recvBuffer, DEFAULT_BUFLEN - 1, 0);

if (result > 0)
{
    sendResult = send(clientSocket, recvBuffer, result, 0);
}
```

下一步需要学习的是：服务器如何断开连接。

