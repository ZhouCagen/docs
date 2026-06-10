# 08 绑定 Socket

## 一、本节目标

上一节已经创建了服务器端用于监听的 Socket：

```cpp
SOCKET listenSocket = socket(result->ai_family, result->ai_socktype, result->ai_protocol);
```

但是，此时这个 Socket 还没有和具体的 IP 地址、端口号绑定。

服务器要想让客户端连接，就必须先绑定一个地址和端口。

本节主要学习：

```cpp
bind
```

`bind` 的作用是：

```text
把服务器 Socket 绑定到本机的某个 IP 地址和端口号上。
```

可以简单理解为：

```text
服务器占用了一个端口。
客户端以后就可以通过这个端口找到服务器。
```

---

## 二、为什么服务器需要绑定端口

客户端连接服务器时，需要知道两个信息：

```text
服务器 IP 地址
服务器端口号
```

例如：

```text
127.0.0.1:27015
```

其中：

| 内容          | 含义        |
| ----------- | --------- |
| `127.0.0.1` | 服务器 IP 地址 |
| `27015`     | 服务器端口号    |

如果服务器没有绑定端口，客户端就不知道应该连接到哪里。

所以服务器端必须执行：

```text
创建 Socket
↓
绑定 Socket
↓
监听 Socket
```

---

## 三、`sockaddr` 结构的作用

在绑定 Socket 时，需要地址信息。

地址信息通常保存在 `sockaddr` 结构中。

不过在官方示例里，我们不需要自己手动填写 `sockaddr`，因为前面已经使用了：

```cpp
getaddrinfo(NULL, DEFAULT_PORT, &hints, &result);
```

`getaddrinfo` 返回的 `result` 中已经包含了可以用于绑定的地址信息。

后面调用 `bind` 时，直接使用：

```cpp
result->ai_addr
result->ai_addrlen
```

即可。

---

## 四、`bind` 函数的基本写法

服务器端绑定 Socket 的代码如下：

```cpp
int resultCode = bind(listenSocket, result->ai_addr, static_cast<int>(result->ai_addrlen));
```

参数含义如下：

| 参数                   | 含义           |
| -------------------- | ------------ |
| `listenSocket`       | 服务器监听 Socket |
| `result->ai_addr`    | 要绑定的地址信息     |
| `result->ai_addrlen` | 地址信息长度       |

这句话的作用是：

```text
把 listenSocket 绑定到 result 中保存的本机地址和端口上。
```

---

## 五、判断绑定是否成功

`bind` 调用后，需要判断是否成功：

```cpp
if (resultCode == SOCKET_ERROR)
{
    cout << "bind failed: " << WSAGetLastError() << endl;
    freeaddrinfo(result);
    closesocket(listenSocket);
    WSACleanup();
    return 1;
}
```

如果 `bind` 返回：

```cpp
SOCKET_ERROR
```

说明绑定失败。

绑定失败时，需要释放资源：

```cpp
freeaddrinfo(result);
closesocket(listenSocket);
WSACleanup();
```

---

## 六、绑定失败的常见原因

### 1. 端口已经被占用

例如服务器使用端口：

```text
27015
```

如果另一个程序已经占用了这个端口，`bind` 就可能失败。

解决方法：

```text
换一个端口号，或者关闭占用端口的程序。
```

---

### 2. 上一次程序没有正常退出

如果服务器程序异常关闭，端口可能短时间内还没有完全释放。

解决方法：

```text
等待一会儿再重新运行，或者换一个端口号。
```

---

### 3. 权限问题

某些特殊端口可能需要管理员权限。

实验中建议使用：

```text
8888
27015
9000
10086
```

这类普通端口。

---

## 七、释放 `getaddrinfo` 返回的地址信息

绑定成功后，`getaddrinfo` 返回的地址信息已经用完了。

此时应该调用：

```cpp
freeaddrinfo(result);
```

完整结构如下：

```cpp
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
```

注意：

```text
freeaddrinfo 释放的是地址信息。
closesocket 关闭的是 Socket。
WSACleanup 释放的是 Winsock 库资源。
```

它们不是同一个东西。

---

## 八、本节完整代码片段

下面代码接在“创建服务器 ListenSocket”之后。

```cpp
int resultCode = bind(listenSocket, result->ai_addr, static_cast<int>(result->ai_addrlen));

if (resultCode == SOCKET_ERROR)
{
    cout << "bind failed: " << WSAGetLastError() << endl;
    freeaddrinfo(result);
    closesocket(listenSocket);
    WSACleanup();
    return 1;
}

freeaddrinfo(result);

cout << "Bind successfully." << endl;
```

---

## 九、放进服务器程序中的位置

服务器程序目前的结构如下：

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

    cout << "Bind successfully." << endl;

    // 5. 下一步：监听 Socket

    closesocket(listenSocket);
    WSACleanup();

    return 0;
}
```

---

## 十、本节小结

本节学习了服务器端如何绑定 Socket。

需要记住：

1. 服务器端需要绑定 IP 地址和端口号。
2. `bind` 用于把 Socket 绑定到指定地址和端口。
3. 客户端连接服务器时，需要使用服务器 IP 和端口。
4. `result->ai_addr` 保存地址信息。
5. `result->ai_addrlen` 保存地址信息长度。
6. `bind` 返回 `SOCKET_ERROR` 表示绑定失败。
7. 绑定成功后，可以调用 `freeaddrinfo(result)` 释放地址信息。

最重要的代码是：

```cpp
int resultCode = bind(listenSocket, result->ai_addr, static_cast<int>(result->ai_addrlen));

if (resultCode == SOCKET_ERROR)
{
    cout << "bind failed: " << WSAGetLastError() << endl;
    freeaddrinfo(result);
    closesocket(listenSocket);
    WSACleanup();
    return 1;
}

freeaddrinfo(result);
```

下一步需要学习的是：侦听 Socket。

