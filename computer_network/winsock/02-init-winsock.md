# 02 初始化 Winsock

## 一、为什么要初始化 Winsock

在 Windows 中使用 Socket 编程时，不能一上来就直接调用 `socket`、`bind`、`connect` 等函数。

在调用任何 Winsock 函数之前，程序必须先调用：

```cpp
WSAStartup
```

它的作用是初始化 Windows Socket 库。

可以简单理解为：

```text
告诉 Windows：我要开始使用网络编程功能了。
```

如果没有调用 `WSAStartup`，后面的 Socket 相关函数可能无法正常工作。

---

## 二、初始化 Winsock 的基本代码

初始化 Winsock 的代码如下：

```cpp
WSADATA wsaData;

int result = WSAStartup(MAKEWORD(2, 2), &wsaData);

if (result != 0)
{
    cout << "WSAStartup failed: " << result << endl;
    return 1;
}
```

完整最小示例：

```cpp
#define WIN32_LEAN_AND_MEAN

#include <winsock2.h>
#include <ws2tcpip.h>
#include <iostream>

#pragma comment(lib, "Ws2_32.lib")

using namespace std;

int main()
{
    WSADATA wsaData;

    int result = WSAStartup(MAKEWORD(2, 2), &wsaData);

    if (result != 0)
    {
        cout << "WSAStartup failed: " << result << endl;
        return 1;
    }

    cout << "Winsock initialized successfully." << endl;

    WSACleanup();

    return 0;
}
```

运行结果示例：

```text
Winsock initialized successfully.
```

---

## 三、`WSADATA` 是什么

代码中有这样一行：

```cpp
WSADATA wsaData;
```

`WSADATA` 是一个结构体，用来保存 Winsock 初始化之后的一些信息。

例如：

* 当前系统支持的 Winsock 版本。
* Winsock 的描述信息。
* 相关配置信息。

在一般实验代码中，我们只需要创建这个对象，然后把它传给 `WSAStartup` 即可。

通常写成：

```cpp
WSADATA wsaData;
```

---

## 四、`WSAStartup` 是什么

`WSAStartup` 用于初始化 Winsock。

函数调用形式如下：

```cpp
WSAStartup(MAKEWORD(2, 2), &wsaData);
```

它有两个重要参数：

| 参数               | 含义                  |
| ---------------- | ------------------- |
| `MAKEWORD(2, 2)` | 请求使用 Winsock 2.2 版本 |
| `&wsaData`       | 用来接收 Winsock 初始化信息  |

如果初始化成功，`WSAStartup` 返回 `0`。

如果初始化失败，返回非 0 值。

所以一般需要这样判断：

```cpp
int result = WSAStartup(MAKEWORD(2, 2), &wsaData);

if (result != 0)
{
    cout << "WSAStartup failed: " << result << endl;
    return 1;
}
```

---

## 五、`MAKEWORD(2, 2)` 是什么意思

`MAKEWORD(2, 2)` 表示请求使用 Winsock 2.2 版本。

可以简单记成固定写法：

```cpp
MAKEWORD(2, 2)
```

在当前实验中，不需要深入研究这个宏的底层实现。

只要记住：

```text
写 Winsock 程序时，初始化通常使用 MAKEWORD(2, 2)。
```

---

## 六、为什么要写 `&wsaData`

`wsaData` 是一个变量。

`&wsaData` 表示取这个变量的地址。

`WSAStartup` 需要通过这个地址，把初始化结果写入 `wsaData` 中。

所以这里不能写成：

```cpp
WSAStartup(MAKEWORD(2, 2), wsaData);
```

应该写成：

```cpp
WSAStartup(MAKEWORD(2, 2), &wsaData);
```

---

## 七、程序结束时为什么要调用 `WSACleanup`

既然程序开始时调用了：

```cpp
WSAStartup
```

那么程序结束前就应该调用：

```cpp
WSACleanup
```

它的作用是释放 Winsock 相关资源。

可以简单理解为：

```text
告诉 Windows：我已经不用网络库了，可以清理资源了。
```

基本结构如下：

```cpp
WSAStartup(MAKEWORD(2, 2), &wsaData);

// 中间进行 socket 通信

WSACleanup();
```

---

## 八、初始化失败怎么办

如果 `WSAStartup` 返回值不是 0，说明初始化失败。

常见写法：

```cpp
if (result != 0)
{
    cout << "WSAStartup failed: " << result << endl;
    return 1;
}
```

这里的 `return 1` 表示程序异常结束。

如果初始化都失败了，就不应该继续调用后面的 `socket`、`bind`、`connect` 等函数。

---

## 九、初始化 Winsock 的标准模板

后续所有 Winsock 程序都可以先写这一段：

```cpp
#define WIN32_LEAN_AND_MEAN

#include <winsock2.h>
#include <ws2tcpip.h>
#include <iostream>

#pragma comment(lib, "Ws2_32.lib")

using namespace std;

int main()
{
    WSADATA wsaData;

    int result = WSAStartup(MAKEWORD(2, 2), &wsaData);

    if (result != 0)
    {
        cout << "WSAStartup failed: " << result << endl;
        return 1;
    }

    cout << "Winsock initialized successfully." << endl;

    WSACleanup();

    return 0;
}
```

---

## 十、本节小结

本节主要学习了 Winsock 初始化。

需要记住：

1. 使用 Winsock 前必须先调用 `WSAStartup`。
2. `WSADATA` 用来保存 Winsock 初始化信息。
3. `MAKEWORD(2, 2)` 表示请求使用 Winsock 2.2。
4. `WSAStartup` 返回 0 表示成功。
5. 程序结束前应该调用 `WSACleanup`。
6. 初始化失败后，不应该继续执行后续网络操作。

最重要的代码是：

```cpp
WSADATA wsaData;

int result = WSAStartup(MAKEWORD(2, 2), &wsaData);

if (result != 0)
{
    cout << "WSAStartup failed: " << result << endl;
    return 1;
}
```

下一步需要学习的是：如何创建 Socket。

