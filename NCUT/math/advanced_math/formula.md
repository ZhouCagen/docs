# 高等数学公式笔记

## <span style="color: #3498db;">第一部分：函数、极限、连续</span>

### 复合函数的奇偶性

$f(g(x))$ 的定义域须关于原点对称。**内偶则偶，内奇则外。**

| 内函数 $g$ | 外函数 $f$ | 复合函数 |
| ---------- | ---------- | -------- |
| 偶         | 任意       | 偶       |
| 奇         | 奇         | 奇       |
| 奇         | 偶         | 偶       |

外函数非奇非偶时，“内奇则外”不能直接判断。零函数既奇又偶。

### 反三角函数的定义域与值域

| 函数                     | 定义域      | 值域             |
| ------------------------ | ----------- | ---------------- |
| $\arcsin x$              | $[-1,1]$    | $[-\pi/2,\pi/2]$ |
| $\arccos x$              | $[-1,1]$    | $[0,\pi]$        |
| $\arctan x$              | $\mathbb R$ | $(-\pi/2,\pi/2)$ |
| $\operatorname{arccot}x$ | $\mathbb R$ | $(0,\pi)$        |

按上述主值约定：

$$
\arcsin x+\arccos x=\frac\pi2\quad(|x|\le1),\qquad
\arctan x+\operatorname{arccot}x=\frac\pi2
$$

$$
\arcsin(-x)=-\arcsin x,\qquad\arctan(-x)=-\arctan x
$$

$$
\arccos(-x)=\pi-\arccos x,\qquad
\operatorname{arccot}(-x)=\pi-\operatorname{arccot}x
$$

### 数列极限

$$
\lim_{n\to\infty}x_n=a
\iff\forall\varepsilon>0,\ \exists N\in\mathbb N^+,\ \forall n>N:
\quad|x_n-a|<\varepsilon.
$$

存在这样的有限常数 $a$，称数列收敛；否则称发散。$n\to\infty$ 指 $n\to+\infty$。

**收敛数列的任意子列均收敛，且极限与原数列相同：**

$$
x_n\to a\quad\Rightarrow\quad x_{n_k}\to a
\qquad(n_1<n_2<\cdots).
$$

### 函数极限的 24 种定义

**6 种自变量趋近方式 × 4 种函数值趋近方式。** $A\in\mathbb R$，$x$ 限于定义域且能按相应方式趋近。

| 自变量趋近    | 输入条件                      |
| ------------- | ----------------------------- |
| $x\to x_0$    | $0<\lvert x-x_0\rvert<\delta$ |
| $x\to x_0^+$  | $0<x-x_0<\delta$              |
| $x\to x_0^-$  | $0<x_0-x<\delta$              |
| $x\to\infty$  | $\lvert x\rvert>X$            |
| $x\to+\infty$ | $x>X$                         |
| $x\to-\infty$ | $x<-X$                        |

| 函数值趋近       | 任意给定        | 输出条件                          |
| ---------------- | --------------- | --------------------------------- |
| $f(x)\to A$      | $\varepsilon>0$ | $\lvert f(x)-A\rvert<\varepsilon$ |
| $f(x)\to\infty$  | $M>0$           | $\lvert f(x)\rvert>M$             |
| $f(x)\to+\infty$ | $M>0$           | $f(x)>M$                          |
| $f(x)\to-\infty$ | $M>0$           | $f(x)<-M$                         |

任意给定 $\varepsilon>0$ 或 $M>0$，存在 $\delta>0$ 或 $X>0$，使**所有满足输入条件的 $x$ 都满足输出条件** 。$\delta,X$ 不能依赖具体的 $x$。

本笔记中 $\infty$ 表示绝对值无限增大；“极限存在”默认指有限极限。$x\to x_0$ 时不要求 $f(x_0)$ 有定义。

### 极限存在的等价表述

$$
\lim_{x\to x_0}f(x)=A
\iff\lim_{x\to x_0^-}f(x)=\lim_{x\to x_0^+}f(x)=A
$$

$$
\lim_{x\to\infty}f(x)=A
\iff\lim_{x\to-\infty}f(x)=\lim_{x\to+\infty}f(x)=A
$$

$$
f(x)\to A\iff f(x)=A+\alpha(x),\quad\alpha(x)\to0
$$

### 极限的局部保号性

设 $\lim_{x\to x_0}f(x)=A\in\mathbb R$，下述“附近”指充分小的去心邻域。

- $A>0$（$A<0$）$\Rightarrow$ 附近 $f(x)>0$（$f(x)<0$）。
- $A\ne0$ $\Rightarrow$ 附近 $f(x)$ 与 $A$ 同号，且 $|f(x)|>|A|/2$。
- 附近 $f(x)\ge0$（$f(x)\le0$）$\Rightarrow A\ge0$（$A\le0$）。即使函数严格正、负，极限仍可能为 $0$。
- $A=0$ 时，无法判断附近函数的符号。

同样适用于单侧及无穷远趋近。

#### 牢记：脱帽严格不等号，戴帽非严格不等号

这里“帽子”指极限符号 $\lim$。**脱帽：由极限的符号判断函数在附近的符号；戴帽：由函数在附近的符号判断极限的符号。** 以下均假设有限极限存在。

**脱帽（极限 → 函数）：极限严格大于或小于 $0$，函数在充分小的去心邻域内也严格同号。**

$$
\boxed{\lim_{x\to x_0}f(x)>0\ \Rightarrow\ f(x)>0\text{（在充分小的去心邻域内）}}
$$

$$
\boxed{\lim_{x\to x_0}f(x)<0\ \Rightarrow\ f(x)<0\text{（在充分小的去心邻域内）}}
$$

具体地，若 $A>0$，则存在 $\delta>0$，使定义域内满足 $0<|x-x_0|<\delta$ 的 $x$ 均有 $f(x)>0$；$A<0$ 时同理。**这是局部结论，不保证整个定义域内同号，也不要求 $f(x_0)$ 有定义。**

**戴帽（函数 → 极限）：函数在某去心邻域内非负或非正，极限也非负或非正。**

$$
\boxed{f(x)\ge0\text{（在某去心邻域内）}\ \Rightarrow\ \lim_{x\to x_0}f(x)\ge0}
$$

$$
\boxed{f(x)\le0\text{（在某去心邻域内）}\ \Rightarrow\ \lim_{x\to x_0}f(x)\le0}
$$

**戴帽后不能保证严格不等号：即使附近 $f(x)>0$，也只能推出极限 $A\ge0$。** 例如 $x\to0$ 时，去心邻域内 $x^2>0$，但 $\lim_{x\to0}x^2=0$。反之，极限 $A=0$ 时不能脱帽判定正负，例如 $x^2$、$-x^2$、$x$ 都趋于 $0$，附近的符号却不同。

**证明脱帽时，$\varepsilon$ 要选得足够小。** 若 $A>0$，取 $\varepsilon=A/2$，由极限定义，在充分小的去心邻域内有

$$
|f(x)-A|<\frac A2
\quad\Rightarrow\quad
\frac A2<f(x)<\frac{3A}{2}
\quad\Rightarrow\quad f(x)>0.
$$

若取 $\varepsilon=2A$，只能得到 $-A<f(x)<3A$，这个范围包含负数，不能据此证明 $f(x)>0$。$A<0$ 时可取 $\varepsilon=|A|/2$，同理证明 $f(x)<0$。

**另一种常见的“脱帽法”（把极限写成等式）：**

$$
\boxed{\lim_{x\to x_0}f(x)=A
\iff f(x)=A+\alpha(x),\qquad\alpha(x)\to0}.
$$

这里 $\alpha(x)=f(x)-A$ 是无穷小，不能直接把 $f(x)$ 写成 $A$。这与上面的保号口诀用途不同：前者把极限关系转成等式，后者用来判断局部符号。

### 有界性常用结论

- **有限极限存在 $\Rightarrow$ 在相应趋近区域内局部有界** ，反之不成立，如 $\sin(1/x)$ 在 $x\to0$ 时。
- 闭区间上的连续函数有界，并取得最大值、最小值。
- $(a,b)$ 上连续，且两端单侧极限均有限 $\Rightarrow$ 在 $(a,b)$ 上有界。
- $f,g$ 有界 $\Rightarrow f\pm g,fg$ 有界；若另有 $|g|\ge m>0$，则 $f/g$ 有界。

局部有界不等于全域有界；上、下界不唯一，最大、最小值唯一。

### 无穷小的比较

设在自变量的同一变化过程中，$\alpha(x)\to0$、$\beta(x)\to0$，且比较分母 $\beta(x)\ne0$。**比较无穷小的阶，就是通过比值的极限比较它们趋于 $0$ 的速度。**

#### 高阶、低阶、同阶与等价无穷小

| 比值极限                                       | $\alpha$ 相对于 $\beta$ |
| ---------------------------------------------- | ----------------------- |
| $\alpha/\beta\to0$                             | 高阶，$\alpha=o(\beta)$ |
| $\lvert\alpha/\beta\rvert\to+\infty$           | 低阶                    |
| $\alpha/\beta\to c$，$0<\lvert c\rvert<\infty$ | 同阶                    |
| $\alpha/\beta\to1$                             | 等价，$\alpha\sim\beta$ |

这里 $c$ 是有限非零常数；低阶条件中的绝对值趋于 $+\infty$，对应教材中的 $\alpha/\beta\to\infty$（无符号无穷大）。

- **高阶：** $\alpha$ 比 $\beta$ 趋于 $0$ 更快。例如 $x\to0$ 时，$x^2=o(x)$。
- **低阶：** $\alpha$ 比 $\beta$ 趋于 $0$ 更慢。例如 $x\to0$ 时，$x$ 是 $x^2$ 的低阶无穷小。
- **同阶：** 两者趋于 $0$ 的速度相当，比值趋于有限非零常数。例如 $2x$ 与 $x$ 同阶，但不等价。
- **等价：** 比值趋于 $1$，记作 $\alpha\sim\beta$。例如 $x\to0$ 时，$\sin x\sim x$。

**等价必同阶，同阶未必等价；并非任意两个无穷小都能按上表比阶。**

#### 等价不等于相等

当 $x\to0$ 时，

$$
\lim_{x\to0}\frac{\sin x}{x}=1,
\qquad\text{所以 }\sin x\sim x,
$$

但这不表示 $\sin x=x$。它们的差仍有非零的高阶信息：

$$
\boxed{\lim_{x\to0}\frac{x-\sin x}{x^3}=\frac16}.
$$

**这里不能把分子中的 $\sin x$ 直接替换成 $x$，否则会错误地算成 $0$。** 因为 $\sin x=x-x^3/6+o(x^3)$，相减后保留下来的正是三阶项。

一般地，

$$
\alpha\sim\beta\iff\alpha-\beta=o(\beta).
$$

等价只说明两者之差相对于 $\beta$ 可忽略，不说明这个差恒为零，也不说明它相对于更高阶的无穷小仍可忽略。

#### k 阶无穷小

若存在 $k>0$ 和有限非零常数 $c$，使

$$
\boxed{\lim\frac{\alpha(x)}{[\beta(x)]^k}=c,\qquad0<|c|<\infty},
$$

则称 **$\alpha(x)$ 是 $\beta(x)$ 的 $k$ 阶无穷小** ，也即 $\alpha\sim c\beta^k$。

例如 $x\to0$ 时，$1-\cos x\sim x^2/2$，所以 $1-\cos x$ 是 $x$ 的二阶无穷小；$x-\sin x\sim x^3/6$，所以 $x-\sin x$ 是 $x$ 的三阶无穷小。

相对于 $\beta$，$k>1$ 时为高阶，$k=1$ 时为同阶，$0<k<1$ 时为低阶。$k$ 非整数时须保证 $\beta^k$ 在所讨论的趋近过程中有定义。

### 常用等价无穷小

$x\to0$，角度用弧度制：

$$
\sin x\sim\tan x\sim\arcsin x\sim\arctan x\sim x
$$

$$
\ln(1+x)\sim x,\qquad e^x-1\sim x,\qquad1-\cos x\sim\frac{x^2}{2}
$$

$$
x-\ln(1+x)\sim\frac{x^2}{2}
$$

$$
(1+x)^{1/x}-e\sim-\frac e2x
$$

$$
a^x-1\sim x\ln a\quad(a>0,\ a\ne1)
$$

$$
(1+x)^\alpha-1\sim\alpha x\quad(\alpha\ne0\text{ 为常数})
$$

$$
\sqrt{1+x}-1\sim\frac{x}{2},\qquad\frac1{1+x}-1\sim-x
$$

$$
\ln\left(x+\sqrt{x^2+1}\right)\sim x
$$

最后一个函数定义于 $\mathbb R$，为奇函数。各式可将 $x$ 换为趋于 $0$ 的 $u(x)$，须保证表达式有定义、比较分母非零。

**乘除可按条件作等价替换，加减不能任意逐项替换。**

### 小 $o$ 的运算规则

$x\to0$，$m,n$ 为正整数，$k\ne0$ 为常数：

$$
r(x)=o(x^n)\iff\frac{r(x)}{x^n}\to0
$$

$$
o(x^m)\pm o(x^n)=o\bigl(x^{\min\{m,n\}}\bigr)
$$

$$
o(x^m)\,o(x^n)=o(x^{m+n}),\qquad x^m o(x^n)=o(x^{m+n})
$$

$$
o(kx^m)=o(x^m),\qquad k\,o(x^m)=o(x^m)
$$

**加减取低阶，乘法阶数相加，非零常数不改阶。** 加减结果不能任意提高阶数。

不同的 $o(x^m)$ 可代表不同函数，不能直接约掉；$o(x^m)-o(x^m)$ 不一定为 $0$。

### 五个函数的大小关系与三阶差值

$x>0$ 且充分接近 $0$ 时：

$$
\arctan x<\sin x<x<\arcsin x<\tan x
$$

$x<0$ 且充分接近 $0$ 时不等号反向；$x=0$ 时均为 $0$。

$x\to0$ 时：

$$
\sin x-\arctan x\sim x-\sin x\sim\arcsin x-x
\sim\tan x-\arcsin x\sim\frac{x^3}{6}
$$

### 常见无穷大的增长速度比较

固定常数 $\alpha,\beta>0$、$a>1$；$f\ll g$ 表示 $f/g\to0$。

$$
(\ln x)^\alpha\ll x^\beta\ll a^x\qquad(x\to+\infty)
$$

$$
(\ln n)^\alpha\ll n^\beta\ll a^n\ll n!\ll n^n\qquad(n\to\infty)
$$

**对数 → 正幂 → 指数 → 阶乘 → 自身幂，增长越来越快。**

### 常见极限

$$
\lim_{x\to0}\frac{\sin x}{x}=1
$$

$$
\lim_{x\to\infty}\left(1+\frac1x\right)^x=e
$$

第一式用弧度制；第二式在 $x\to+\infty$、$x\to-\infty$ 时均成立。

$$
\lim_{n\to\infty}\sqrt[n]{n}=1
$$

$$
\lim_{n\to\infty}\sqrt[n]{a}=1\qquad(a>0\text{ 为固定常数})
$$

$m$ 为固定正整数，$a_1,\ldots,a_m$ 为固定非负数：

$$
\lim_{n\to\infty}\sqrt[n]{a_1^n+a_2^n+\cdots+a_m^n}
=\max\{a_1,a_2,\ldots,a_m\}.
$$

### 连续性的性质

内点 $x_0$ 处：

$$
f\text{ 在 }x_0\text{ 处连续}
\iff\lim_{x\to x_0^-}f(x)=\lim_{x\to x_0^+}f(x)=f(x_0).
$$

- **四则运算：** $f,g$ 在 $x_0$ 处连续，则 $f\pm g,fg$ 也连续；若 $g(x_0)\ne0$，则 $f/g$ 也连续。
- **复合函数：** $\varphi$ 在 $x_0$ 处连续，$f$ 在 $u_0=\varphi(x_0)$ 处连续，则 $f(\varphi(x))$ 在 $x_0$ 处连续。
- **反函数：** $f$ 在区间 $I$ 上严格单调且连续，则反函数在 $f(I)$ 上连续，且单调性与 $f$ 相同。
- **局部保号：** $f$ 在 $x_0$ 处连续且 $f(x_0)>0$（$<0$），则存在 $\delta>0$，使 $|x-x_0|<\delta$ 时 $f(x)>0$（$<0$）。

#### 绝对值与连续、可导的关系

**基本关系：在 $x_0$ 处可导 $\Rightarrow$ 在 $x_0$ 处连续 $\Rightarrow$ 在 $x_0$ 处有定义，反向均不一定成立。**

**$f(x)$ 在 $x_0$ 处连续，可推出 $|f(x)|$ 在 $x_0$ 处连续；反过来一般不成立。可导性则两个方向一般都不能推。**

反例：

$$
f(x)=\begin{cases}
-1,&x<0,\\
1,&x\ge0.
\end{cases}
$$

$|f(x)|\equiv1$ 在 $x=0$ 处连续，但 $f(x)$ 在该点不连续。

**换成可导性，两个方向一般都不成立：**

- **$f(x)$ 可导，不一定能推出 $|f(x)|$ 可导。** 例如 $f(x)=x$ 在 $0$ 处可导，但 $|x|$ 在 $0$ 处不可导。
- **$|f(x)|$ 可导，也不一定能推出 $f(x)$ 可导。** 上述反例中 $|f(x)|\equiv1$ 处处可导，但 $f(x)$ 在 $0$ 处不连续，因此不可导。

### 间断点分类

| 类别   | 类型       | 条件                                             |
| ------ | ---------- | ------------------------------------------------ |
| 第一类 | 可去间断点 | 左右极限相等且有限，但函数值不等于该极限或未定义 |
| 第一类 | 跳跃间断点 | 左右极限均有限，但不相等                         |
| 第二类 | 无穷间断点 | 至少一侧函数值趋于无穷大                         |
| 第二类 | 振荡间断点 | 因振荡导致至少一侧极限不存在                     |

**第一类：左右极限均存在且有限；第二类：至少一侧不存在有限极限。**

可去间断点可通过补定义或修改 $f(x_0)=\lim_{x\to x_0}f(x)$ 消除。例如：

$$
f(x)=\begin{cases}
\dfrac{\sin x}{x},&x\ne0,\\
1,&x=0
\end{cases}
\quad\text{在 }x=0\text{ 处连续。}
$$

## <span style="color: #3498db;">第二部分：一元函数微分学及其应用</span>

### 函数在一点可导的充要条件

#### 单侧导数

**左导数** ：增量 $\Delta x\to0^-$，从 $x_0$ 左侧趋近。

$$
f'_-(x_0)=\lim_{\Delta x\to0^-}\frac{f(x_0+\Delta x)-f(x_0)}{\Delta x}
$$

**右导数** ：增量 $\Delta x\to0^+$，从 $x_0$ 右侧趋近。

$$
f'_+(x_0)=\lim_{\Delta x\to0^+}\frac{f(x_0+\Delta x)-f(x_0)}{\Delta x}
$$

$f'_-(x_0)$、$f'_+(x_0)$ 分别称为 $f(x)$ 在 $x_0$ 处的左导数、右导数，统称为**单侧导数** 。导数存在要求上述极限为有限值。

#### 可导的充要条件

$$
\boxed{f'(x_0)\text{ 存在}\iff f'_-(x_0)\text{ 与 }f'_+(x_0)\text{ 均存在且相等}}
$$

此时：

$$
f'(x_0)=f'_-(x_0)=f'_+(x_0)
$$

**实际意义：左右两侧的瞬时变化率均存在且相等。**

**几何意义：曲线在该点有斜率有限的切线，可以是斜切线，也可以是水平切线。** 竖直切线的斜率不是有限值，不能据此认为函数在该点可导。

#### 可导与连续的关系

**可导一定连续，连续不一定可导。** 连续是可导的必要条件，可导是连续的充分条件；不连续则一定不可导。

例如，$f(x)=|x|$ 在 $x=0$ 处连续，但左导数 $f'_-(0)=-1$、右导数 $f'_+(0)=1$，左右导数不相等，因此在该点不可导。

#### 可微、增量与微分

设 $\Delta y=f(x_0+\Delta x)-f(x_0)$。若存在与 $\Delta x$ 无关的常数 $A$，使得当 $\Delta x\to0$ 时：

$$
\Delta y=A\Delta x+o(\Delta x),
$$

则称 $f$ 在 $x_0$ 处可微。**一元函数在一点可微与可导等价，且 $A=f'(x_0)$。** 因而：

$$
\boxed{\Delta y=f'(x_0)\Delta x+o(\Delta x)}
$$

令 $dx=\Delta x$，微分为：

$$
\boxed{dy=f'(x_0)dx=f'(x_0)\Delta x}
$$

**增量 $\Delta y$ 是实际变化量，微分 $dy$ 是增量的线性部分。** 两者满足 $\Delta y=dy+o(\Delta x)$，一般不能直接写成 $\Delta y=f'(x_0)\Delta x$；当 $\Delta x$ 很小时，可用 $\Delta y\approx dy$ 作线性近似。

### 基本求导公式

#### 幂函数、指数函数与对数函数

$$
(x^\alpha)'=\alpha x^{\alpha-1}\qquad(\alpha\text{ 为常数})
$$

$$
(a^x)'=a^x\ln a,\qquad(e^x)'=e^x\qquad(a>0,\ a\ne1)
$$

$$
(\log_a x)'=\frac1{x\ln a}\qquad(x>0,\ a>0,\ a\ne1)
$$

幂函数求导公式在函数有定义且可导的范围内使用，尤其要单独检查 $x=0$。

**指数函数的高阶导数：每求一次导数，就多乘一个 $\ln a$。**

$$
(a^x)^{(n)}=a^x(\ln a)^n,\qquad(e^x)^{(n)}=e^x
$$

#### 对数绝对值与复合函数

$$
\boxed{(\ln|x|)'=\frac1x}\qquad(x\ne0)
$$

当 $x>0$ 时，$\ln|x|=\ln x$；当 $x<0$ 时，$\ln|x|=\ln(-x)$，由复合函数求导：

$$
[\ln(-x)]'=\frac1{-x}\cdot(-1)=\frac1x.
$$

更一般地，若 $u(x)$ 可导且 $u(x)\ne0$，则：

$$
\boxed{[\ln|u(x)|]'=\frac{u'(x)}{u(x)}}
$$

**求导后分母保留 $u(x)$ 本身，不带绝对值；同时别漏掉内函数的导数 $u'(x)$。**

#### 三角函数与反三角函数

| 函数                     | 导数                     | 条件               |
| ------------------------ | ------------------------ | ------------------ |
| $\sin x$                 | $\cos x$                 | $x\in\mathbb R$    |
| $\cos x$                 | $-\sin x$                | $x\in\mathbb R$    |
| $\tan x$                 | $\sec^2x$                | $\cos x\ne0$       |
| $\cot x$                 | $-\csc^2x$               | $\sin x\ne0$       |
| $\sec x$                 | $\sec x\tan x$           | $\cos x\ne0$       |
| $\csc x$                 | $-\csc x\cot x$          | $\sin x\ne0$       |
| $\arcsin x$              | $\dfrac1{\sqrt{1-x^2}}$  | $\lvert x\rvert<1$ |
| $\arccos x$              | $-\dfrac1{\sqrt{1-x^2}}$ | $\lvert x\rvert<1$ |
| $\arctan x$              | $\dfrac1{1+x^2}$         | $x\in\mathbb R$    |
| $\operatorname{arccot}x$ | $-\dfrac1{1+x^2}$        | $x\in\mathbb R$    |

#### 两个常用对数复合函数

$$
\left[\ln\left(x+\sqrt{x^2+1}\right)\right]'=\frac1{\sqrt{x^2+1}}\qquad(x\in\mathbb R)
$$

$$
\left[\ln\left(x+\sqrt{x^2-1}\right)\right]'=\frac1{\sqrt{x^2-1}}\qquad(x>1)
$$

### 莱布尼茨公式（高阶导数）

设 $u=u(x)$、$v=v(x)$ 均为 $n$ 阶可导，则：

$$
\boxed{(u\pm v)^{(n)}=u^{(n)}\pm v^{(n)}}
$$

**乘积的 $n$ 阶导数：**

$$
\boxed{(uv)^{(n)}=\sum_{k=0}^n\binom nk u^{(n-k)}v^{(k)}}
$$

展开为：

$$
\begin{aligned}
(uv)^{(n)}={}&u^{(n)}v+\binom n1u^{(n-1)}v'
+\binom n2u^{(n-2)}v''+\cdots\\
&+\binom nku^{(n-k)}v^{(k)}+\cdots
+\binom n{n-1}u'v^{(n-1)}+uv^{(n)}.
\end{aligned}
$$

其中 $\binom nk=C_n^k=\dfrac{n!}{k!(n-k)!}$，$u^{(0)}=u$、$v^{(0)}=v$。

**记忆：共 $n+1$ 项，系数与二项式展开相同；$u$ 的求导阶数逐项递减，$v$ 的逐项递增，每项的求导阶数之和均为 $n$。**

例如：

$$
(uv)''=u''v+2u'v'+uv'',
$$

$$
(uv)'''=u'''v+3u''v'+3u'v''+uv'''.
$$

### 反函数求导公式与 arcsin x 的求导

#### 反函数的一阶、二阶导数

设 $y=f(x)$ 单调且可导，$f'(x)\ne0$，反函数为 $x=\varphi(y)$。一阶导数满足：

$$
\boxed{\frac{dx}{dy}=\frac1{\dfrac{dy}{dx}}}
\qquad\text{即}\qquad
\boxed{\varphi'(y)=\frac1{f'(x)}}.
$$

若 $f$ 二阶可导，则反函数的二阶导数为：

$$
\boxed{\frac{d^2x}{dy^2}=-\frac{\dfrac{d^2y}{dx^2}}{\left(\dfrac{dy}{dx}\right)^3}}
\qquad\text{即}\qquad
\boxed{\varphi''(y)=-\frac{f''(x)}{[f'(x)]^3}}.
$$

其中 $x=\varphi(y)$，两边导数在对应点取值。交换 $x,y$，也可写成：

$$
\frac{dy}{dx}=\frac1{\dfrac{dx}{dy}},\qquad
\frac{d^2y}{dx^2}=-\frac{\dfrac{d^2x}{dy^2}}{\left(\dfrac{dx}{dy}\right)^3}.
$$

**记忆：一阶导数互为倒数；二阶导数为“负的另一方二阶导数，除以另一方一阶导数的三次方”。**

#### 例：y = arcsin x 的求导过程

设 $y=\arcsin x$，$-1<x<1$，则

$$
x=\sin y,\qquad -\frac\pi2<y<\frac\pi2.
$$

由反函数求导公式，

$$
\begin{aligned}
(\arcsin x)'
&=\frac1{(\sin y)'}
=\frac1{\cos y}\\
&=\frac1{\sqrt{1-\sin^2y}}
=\boxed{\frac1{\sqrt{1-x^2}}},\qquad -1<x<1.
\end{aligned}
$$

**这里 $(\sin y)'$ 表示对 $y$ 求导。** 因 $y\in(-\pi/2,\pi/2)$，有 $\cos y>0$，所以 $\sqrt{1-\sin^2y}=\sqrt{\cos^2y}=|\cos y|=\cos y$。

### 罗尔定理与推广

#### 罗尔定理

设 $a<b$，且 $f$ 同时满足：

1. 在 $[a,b]$ 上连续；
2. 在 $(a,b)$ 内可导；
3. $f(a)=f(b)$。

则至少存在一点 $\xi\in(a,b)$，使

$$
\boxed{f'(\xi)=0}.
$$

**牢记：闭区间连续、开区间可导、两端函数值相等。三个条件须同时满足，结论中的 $\xi$ 在区间内部，且不一定唯一。** 几何意义：至少有一条水平切线。常用于证明导数存在零点，也可通过构造辅助函数来证明等式。

#### 推广的罗尔定理

设 $f$ 在 $(a,b)$ 内可导，且两端极限相同：

$$
\lim_{x\to a^+}f(x)=\lim_{x\to b^-}f(x)=A.
$$

则至少存在 $\xi\in(a,b)$，使 $f'(\xi)=0$。这里 $(a,b)$ 可以是有限区间，也可以是无穷区间；无穷端点处取相应的无穷远极限。$A$ 可以是有限实数，也可以是 $+\infty$ 或 $-\infty$，但两端必须趋于**同一个** 值（无穷大时也须同号）。

**牢记：端点函数值相等，可推广为两端极限相等。** 有限端点处不要求原函数有定义；若两端极限一个为 $+\infty$、另一个为 $-\infty$，则不能使用这个结论。

#### 罗尔定理推论：函数与导数的实根个数

以下均在同一个区间 $I$ 内讨论，**实根按不同的取值计数，不计重数** 。假设 $f$ 在 $I$ 上连续、在区间内部 $n$ 阶可导；若 $I$ 包含端点，要求相应的单侧连续。$n\ge1$ 为整数。

**① 原函数有 $m$ 个不同实根，一阶导数至少有 $m-1$ 个不同实根。** 对 $m\ge2$，

$$
\boxed{f(x)=0\text{ 有 }m\text{ 个不同实根}
\ \Rightarrow\ f'(x)=0\text{ 至少有 }m-1\text{ 个不同实根}}.
$$

证明思路：把原函数的根排列为 $x_1<x_2<\cdots<x_m$。在每个 $[x_i,x_{i+1}]$ 上应用一次罗尔定理，就有

$$
\xi_i\in(x_i,x_{i+1}),\qquad f'(\xi_i)=0,
\qquad i=1,\ldots,m-1.
$$

这些开区间互不相交，所以所得 $m-1$ 个根互不相同。

**② 反复使用罗尔定理：每求一次导数，保证的根数减少一个。** 当 $m>n$ 时，

$$
\boxed{f(x)=0\text{ 有 }m\text{ 个不同实根}
\ \Rightarrow\ f^{(n)}(x)=0\text{ 至少有 }m-n\text{ 个不同实根}}.
$$

**③ 反向估计：$n$ 阶导数处处非零，原函数至多有 $n$ 个不同实根。**

$$
\boxed{f^{(n)}(x)\ne0\text{（区间内部处处成立）}
\ \Rightarrow\ f(x)=0\text{ 至多有 }n\text{ 个不同实根}}.
$$

反证：若原函数至少有 $n+1$ 个不同实根，反复使用罗尔定理，就会推出 $f^{(n)}$ 至少有一个零点，与条件矛盾。注意，“处处非零”比“不恒等于零”强，不能混淆。

**④ 更一般地：导数根数的上界，加上求导阶数，就是原函数根数的上界。** 对整数 $k\ge0$，

$$
\boxed{f^{(n)}(x)=0\text{ 在区间内部至多有 }k\text{ 个不同实根}
\ \Rightarrow\ f(x)=0\text{ 在 }I\text{ 内至多有 }k+n\text{ 个不同实根}}.
$$

否则，若 $f$ 至少有 $k+n+1$ 个不同实根，则 $f^{(n)}$ 至少有 $k+1$ 个不同实根，矛盾。

**牢记：正向“至少”，反向“至多”；要证明恰有几个根，通常先用零点定理证明“至少”，再用导数和罗尔定理证明“至多”。**

#### 实系数奇次多项式至少有一个实根

设

$$
P(x)=a_{2r+1}x^{2r+1}+\cdots+a_1x+a_0,
\qquad a_{2r+1}\ne0,\quad r\ge0,
$$

系数均为实数，则

$$
\boxed{P(x)=0\text{ 至少有一个实根}}.
$$

因为奇次最高次项使 $P(x)$ 在 $x\to+\infty$ 与 $x\to-\infty$ 时趋于异号无穷大，可选取充分大的 $R>0$，使 $P(-R)P(R)<0$。多项式连续，由零点定理，$(-R,R)$ 内至少有一个实根。

**这条结论来自零点定理，只保证至少一个实根，不保证唯一。**

### 拉格朗日中值定理

设 $f$ 在 $[a,b]$ 上连续，在 $(a,b)$ 内可导，其中 $a<b$，则至少存在 $\xi\in(a,b)$，使

$$
\boxed{f(b)-f(a)=f'(\xi)(b-a)},
$$

即

$$
\boxed{f'(\xi)=\frac{f(b)-f(a)}{b-a}}.
$$

**几何意义：某点的切线平行于两端点的连线；某点的瞬时变化率等于整个区间的平均变化率。** 当 $f(a)=f(b)$ 时，就得到罗尔定理。

常用结论：

- 若区间内处处 $f'(x)=0$，则 $f$ 在该区间上为常数。
- 若 $m\le f'(x)\le M$，则 $m(b-a)\le f(b)-f(a)\le M(b-a)$。
- 若 $|f'(x)|\le M$，则 $|f(b)-f(a)|\le M|b-a|$。

**注意：一个点的导数为零不能推出函数为常数；必须在整个区间内处处为零。**

### 柯西中值定理

设 $f,g$ 同时满足：

1. 在 $[a,b]$ 上连续；
2. 在 $(a,b)$ 内可导；
3. 对任意 $x\in(a,b)$，都有 $g'(x)\ne0$。

则至少存在 $\xi\in(a,b)$，使

$$
\boxed{\frac{f(b)-f(a)}{g(b)-g(a)}=\frac{f'(\xi)}{g'(\xi)}}.
$$

由罗尔定理可知，$g'(x)\ne0$ 保证 $g(b)\ne g(a)$，所以分母不为零。

**牢记：分子、分母的导数必须取在同一个 $\xi$ 处。** 分别对 $f,g$ 使用拉格朗日中值定理，通常只能得到两个不同的中间点，不能直接合并成上述比值。

取 $g(x)=x$，即得到拉格朗日中值定理。对参数曲线 $X=g(t)$、$Y=f(t)$，$f'(\xi)/g'(\xi)$ 表示相应点的切线斜率，左侧表示两端点连线的斜率。

构造辅助函数时，可取

$$
H(x)=[g(b)-g(a)]f(x)-[f(b)-f(a)]g(x),
$$

由 $H(a)=H(b)$ 应用罗尔定理，即得到结论。

### 泰勒公式与两种余项

**思想：用多项式近似表示函数。** $n$ 阶泰勒多项式为

$$
T_n(x)=\sum_{k=0}^n\frac{f^{(k)}(x_0)}{k!}(x-x_0)^k,
\qquad f^{(0)}=f.
$$

#### 带拉格朗日余项的泰勒公式

设 $f$ 在 $x_0$ 的某邻域内有 $n+1$ 阶导数，则对该邻域内的 $x\ne x_0$，存在严格介于 $x_0$ 与 $x$ 之间的 $\xi$，使

$$
\boxed{f(x)=\sum_{k=0}^n\frac{f^{(k)}(x_0)}{k!}(x-x_0)^k
+\frac{f^{(n+1)}(\xi)}{(n+1)!}(x-x_0)^{n+1}}.
$$

其中

$$
R_n(x)=\frac{f^{(n+1)}(\xi)}{(n+1)!}(x-x_0)^{n+1}
$$

称为**拉格朗日余项** ；$\xi$ 一般随 $x$ 改变。它给出截断后的误差，常用于区间上的不等式证明和近似计算的误差估计。

若 $x_0$ 与 $x$ 之间有 $|f^{(n+1)}(t)|\le M$，则

$$
\boxed{|R_n(x)|\le\frac{M}{(n+1)!}|x-x_0|^{n+1}}.
$$

#### 带佩亚诺余项的泰勒公式

$f$ 在 $x_0$ 处 $n$ 阶可导，则 $x\to x_0$ 时：

$$
f(x)=\sum_{k=0}^{n}\frac{f^{(k)}(x_0)}{k!}(x-x_0)^k
+o\bigl((x-x_0)^n\bigr)
$$

取 $x_0=0$，即麦克劳林公式：

$$
f(x)=f(0)+f'(0)x+\frac{f''(0)}{2!}x^2+\cdots+\frac{f^{(n)}(0)}{n!}x^n+o(x^n)
$$

不要求 $n$ 阶导数连续或存在 $n+1$ 阶导数。

**这是 $x\to x_0$ 时的局部渐近公式，常用于求极限、比较无穷小阶数和判定极值。** $o((x-x_0)^n)$ 表示余项与 $(x-x_0)^n$ 的比值趋于 $0$，一般不能据此给出固定区间上的具体误差上界。

#### 麦克劳林公式的两种余项

**取展开点 $x_0=0$，泰勒公式就称为麦克劳林公式。** 在相应可导条件下，拉格朗日余项形式为

$$
f(x)=f(0)+f'(0)x+\frac{f''(0)}{2!}x^2+\cdots+\frac{f^{(n)}(0)}{n!}x^n
+\frac{f^{(n+1)}(\xi)}{(n+1)!}x^{n+1},
$$

其中 $\xi$ 严格介于 $0$ 与 $x$ 之间；佩亚诺余项形式为

$$
f(x)=\sum_{k=0}^n\frac{f^{(k)}(0)}{k!}x^k+o(x^n),\qquad x\to0.
$$

**牢记：拉格朗日余项涉及 $n+1$ 阶导数，可估计误差；佩亚诺余项为 $o(x^n)$，用于局部阶数比较。** 常用函数的七个有限展开式见前文“截断为有限阶泰勒公式”。

### 截断为有限阶泰勒公式

当 $x\to0$ 时，展开到指定幂次后，加上相应的佩亚诺余项。下面 $n$ 为固定正整数，$\alpha$ 为固定实常数。

**常用七式（有限展开，含通项）：**

$$
e^x=1+x+\frac{x^2}{2!}+\cdots+\frac{x^n}{n!}+o(x^n).
$$

$$
\sin x=x-\frac{x^3}{3!}+\cdots+(-1)^n\frac{x^{2n+1}}{(2n+1)!}+o(x^{2n+1}).
$$

$$
\cos x=1-\frac{x^2}{2!}+\frac{x^4}{4!}+\cdots+(-1)^n\frac{x^{2n}}{(2n)!}+o(x^{2n}).
$$

$$
\frac1{1-x}=1+x+x^2+\cdots+x^n+o(x^n).
$$

$$
\frac1{1+x}=1-x+x^2+\cdots+(-1)^nx^n+o(x^n).
$$

$$
\ln(1+x)=x-\frac{x^2}{2}+\frac{x^3}{3}+\cdots+(-1)^{n-1}\frac{x^n}{n}+o(x^n).
$$

$$
(1+x)^\alpha=1+\alpha x+\frac{\alpha(\alpha-1)}{2!}x^2+\cdots
+\frac{\alpha(\alpha-1)\cdots(\alpha-n+1)}{n!}x^n+o(x^n).
$$

**优先记住常数项及前几个非零项，再按抵消情况展开到所需阶数。** $1/(1+x)$ 可由 $1/(1-x)$ 中的 $x$ 换成 $-x$ 得到；二者也都是二项式展开在 $\alpha=-1$ 时的特例。

反三角函数的有限展开为：

$$
\arcsin x=\sum_{k=0}^n\frac{(2k)!}{4^k(k!)^2(2k+1)}x^{2k+1}+o(x^{2n+1}).
$$

$$
\arctan x=\sum_{k=0}^n(-1)^k\frac{x^{2k+1}}{2k+1}+o(x^{2n+1}).
$$

**相减须展开到抵消后首个非零项；截断或换元时，余项阶数也要相应调整。无穷级数等式须满足收敛区间条件，有限阶泰勒公式描述的是 $x\to0$ 时的局部性质。**

### 驻点、导数符号、极值点与单调性的关系

#### 一、某一点的导数与单调性

1. $f'(x_0)=0$：只能说明 $x_0$ 是驻点，不能说明是极值点，也不能判断邻域内的单调性。
2. $f'(x_0)>0$：只能说明在充分小的邻域内，$x_0$ 左侧函数值小于 $f(x_0)$，右侧函数值大于 $f(x_0)$，**不能推出整个邻域单调递增** 。
3. $f'(x_0)<0$：与上述相反，同样**不能推出整个邻域单调递减** 。

**原因：** 一点导数的符号不代表邻域内导数的符号，导数可能在任意小的邻域内不断变号，导致函数振荡。

#### 二、极值点与单调性的关系

1. 极大值点：只要求存在某个邻域，使 $f(x)\le f(x_0)$。
2. 极小值点：只要求存在某个邻域，使 $f(x)\ge f(x_0)$。
3. **即使是极值点，也不能推出左右邻域分别单调。** 函数在极值点两侧仍然可能无限振荡。
4. 若函数在内点可导且取得极值，则该点导数必为 $0$（费马定理）；**反过来不成立** 。

#### 三、什么时候才能判断单调性？

- 某区间内处处 $f'(x)>0$ $\Rightarrow$ 该区间严格单调递增。
- 某区间内处处 $f'(x)<0$ $\Rightarrow$ 该区间严格单调递减。
- 若 $f'$ 在 $x_0$ 连续，且 $f'(x_0)>0$（或小于 $0$），则可以推出某个邻域内严格单调递增（或递减）。

### 一元函数极值的必要条件

设 $x_0$ 是定义域内点。若 $f$ 在 $x_0$ 处可导且取得极值，则 $f'(x_0)=0$；若还二阶可导，则

$$
\begin{aligned}
x_0\text{ 为极大值点}&\Rightarrow f'(x_0)=0,\quad f''(x_0)\le0,\\
x_0\text{ 为极小值点}&\Rightarrow f'(x_0)=0,\quad f''(x_0)\ge0.
\end{aligned}
$$

**必要条件中的二阶导数允许等于零，不能写成严格不等号。** 如 $f(x)=-x^4$ 在 $0$ 处取极大值，但 $f''(0)=0$。这些必要条件不能反推极值：$f(x)=x^3$ 在 $0$ 处一、二阶导数均为零，却没有极值。

### 极值的二阶导数判别法

设 $x_0$ 为定义域内点，$f$ 在 $x_0$ 的某邻域内可导，且 $f''(x_0)$ 存在。若 $f'(x_0)=0$、$f''(x_0)\ne0$，则：

- **$f''(x_0)<0$：$f$ 在 $x_0$ 处取得极大值 $f(x_0)$。**
- **$f''(x_0)>0$：$f$ 在 $x_0$ 处取得极小值 $f(x_0)$。**

**记忆：一阶为零，二阶看正负；负为极大，正为极小。**

若 $f''(x_0)=0$，此判别法失效，不能据此判断是否有极值；可改用一阶导数在该点两侧的符号变化判断。

### 极值的高阶导数判别法（第三充分条件）

设 $x_0$ 为定义域内点，$f$ 在 $x_0$ 处 $n$ 阶可导，且

$$
f'(x_0)=f''(x_0)=\cdots=f^{(n-1)}(x_0)=0,\qquad
f^{(n)}(x_0)\ne0,\qquad n\ge2.
$$

即从一阶开始，**连续求导，直到首次出现非零导数** 。此时：

| 首次非零导数的阶数与符号     | 结论                  |
| ---------------------------- | --------------------- |
| $n$ 为偶数，$f^{(n)}(x_0)<0$ | 在 $x_0$ 处取得极大值 |
| $n$ 为偶数，$f^{(n)}(x_0)>0$ | 在 $x_0$ 处取得极小值 |
| $n$ 为奇数                   | $x_0$ 不是极值点      |

**记忆：首次非零阶，偶数看正负（负极大、正极小），奇数无极值。** 二阶导数判别法就是 $n=2$ 的情形。

由泰勒公式，

$$
f(x)-f(x_0)=\frac{f^{(n)}(x_0)}{n!}(x-x_0)^n+o\bigl((x-x_0)^n\bigr).
$$

偶数次幂在两侧同号，奇数次幂在两侧异号，因此得到上述结论。若始终未找到非零导数，不能用此法直接下结论。

### 曲线的凹凸性

设 $f(x)$ 在区间 $I$ 上连续，对 $I$ 上任意两个不同的点 $x_1,x_2$：

#### 凹（凹弧）

若恒有

$$
\boxed{f\left(\frac{x_1+x_2}{2}\right)<\frac{f(x_1)+f(x_2)}2},
$$

则称 $y=f(x)$ 在 $I$ 上的图形是**凹的（凹弧）** 。几何意义：**图形上任意弧段位于对应弦的下方** ，形状如 $\cup$，例如 $y=x^2$。

#### 凸（凸弧）

若恒有

$$
\boxed{f\left(\frac{x_1+x_2}{2}\right)>\frac{f(x_1)+f(x_2)}2},
$$

则称 $y=f(x)$ 在 $I$ 上的图形是**凸的（凸弧）** 。几何意义：**图形上任意弧段位于对应弦的上方** ，形状如 $\cap$，例如 $y=-x^2$。

#### 区分不等式中的两个量

- $f\left(\dfrac{x_1+x_2}{2}\right)$：**横坐标中点处的函数值** ，对应的点在曲线上。
- $\dfrac{f(x_1)+f(x_2)}2$：**两端函数值的平均值** ，对应的是弦的中点纵坐标。

**记忆：凹在弦下，凸在弦上。**

#### 拐点的三阶导数判别法

设 $x_0$ 为定义域内点，$f$ 在 $x_0$ 的某邻域内二阶可导，且 $f'''(x_0)$ 存在。若

$$
\boxed{f''(x_0)=0,\qquad f'''(x_0)\ne0},
$$

则曲线在 $x_0$ 两侧的凹凸性发生改变，**$(x_0,f(x_0))$ 是拐点** 。

**记忆：二阶为零、三阶非零，可判定拐点。** 这是充分条件；若三阶导数也为零，仍可能有拐点，需进一步判断两侧凹凸性。例如 $y=x^5$ 在原点有拐点，但 $f'''(0)=0$。

#### 拐点的高阶导数判别法（第三充分条件）

设 $x_0$ 为定义域内点，$f$ 在 $x_0$ 处 $n$ 阶可导，且

$$
f''(x_0)=f'''(x_0)=\cdots=f^{(n-1)}(x_0)=0,\qquad
f^{(n)}(x_0)\ne0,\qquad n\ge3.
$$

**从二阶导数开始，找到首次非零导数：若其阶数 $n$ 为奇数，则 $(x_0,f(x_0))$ 是拐点。** 不要求 $f'(x_0)=0$。

若首次非零导数的阶数 $n$ 为偶数，则二阶导数在该点两侧同号，凹凸性不改变，该点不是拐点。

**与极值判别区分：极值从一阶开始找首次非零导数，偶数阶有极值；拐点从二阶开始找，奇数阶有拐点。** 若始终未找到非零导数，不能用此法直接判断。

### 斜渐近线

#### 当 x 趋于正无穷

若

$$
\lim_{x\to+\infty}\frac{f(x)}x=a_1\ne0,\qquad
\lim_{x\to+\infty}[f(x)-a_1x]=b_1,
$$

其中 $a_1,b_1$ 均为有限常数，则 **$y=a_1x+b_1$ 是曲线 $y=f(x)$ 在正无穷方向的斜渐近线** 。

#### 当 x 趋于负无穷

若

$$
\lim_{x\to-\infty}\frac{f(x)}x=a_2\ne0,\qquad
\lim_{x\to-\infty}[f(x)-a_2x]=b_2,
$$

其中 $a_2,b_2$ 均为有限常数，则 **$y=a_2x+b_2$ 是曲线 $y=f(x)$ 在负无穷方向的斜渐近线** 。

#### 两个方向为同一条斜渐近线

若

$$
\lim_{x\to+\infty}\frac{f(x)}x
=\lim_{x\to-\infty}\frac{f(x)}x=a\ne0,
$$

且

$$
\lim_{x\to+\infty}[f(x)-ax]
=\lim_{x\to-\infty}[f(x)-ax]=b,
$$

其中 $a,b$ 均为有限常数，则 **$y=ax+b$ 是曲线在正、负无穷两个方向上的共同斜渐近线** 。

**步骤：先求 $a=\lim f(x)/x$，再求 $b=\lim[f(x)-ax]$。正、负无穷必须分别考察，可能得到不同的斜渐近线。** 若 $a=0$ 且 $b$ 有限，则 $y=b$ 是水平渐近线。

### 曲率与曲率半径（数学一、数学二）

设 $y=y(x)$ 二阶可导，则曲线在点 $(x,y(x))$ 处的**曲率** 为：

$$
\boxed{k=\frac{|y''|}{[1+(y')^2]^{3/2}}}
$$

当 $y''\ne0$ 时，**曲率半径** 为：

$$
\boxed{R=\frac1k=\frac{[1+(y')^2]^{3/2}}{|y''|}}
$$

**曲率表示曲线的弯曲程度：曲率越大，曲率半径越小。**

## <span style="color: #3498db;">第三部分：一元函数积分学及其应用</span>

### 原函数的存在性

若在区间 $I$ 上有 $F'(x)=f(x)$，则称 $F(x)$ 是 $f(x)$ 在该区间上的一个**原函数** 。

- **连续一定有原函数** ：若 $f$ 在区间 $I$ 上连续，则 $f$ 在该区间上存在原函数。
- **有第一类间断点或无穷间断点，一定没有原函数** ：若 $f$ 在某点有第一类间断点（可去间断点或跳跃间断点）或无穷间断点，则在包含该间断点的区间内，$f$ 必定没有原函数。这里指在整个区间上（包括该点）满足 $F'=f$；避开该点后的子区间需另行判断。
- **有振荡间断点也可能有原函数** ：连续是存在原函数的充分条件，但不是必要条件；不能由函数不连续就断定它没有原函数。

例如，令

$$
F(x)=
\begin{cases}
x^2\sin\dfrac1x, & x\ne0,\\
0, & x=0.
\end{cases}
$$

当 $x\ne0$ 时直接求导；在 $x=0$ 处，由导数定义有

$$
F'(0)=\lim_{h\to0}\frac{h^2\sin(1/h)}h
=\lim_{h\to0}h\sin\frac1h=0.
$$

因此

$$
f(x)=F'(x)=
\begin{cases}
2x\sin\dfrac1x-\cos\dfrac1x, & x\ne0,\\
0, & x=0.
\end{cases}
$$

$f$ 在 $x=0$ 处有振荡间断点，但仍有原函数 $F$。**注意：是“可能有”，不是所有具有振荡间断点的函数都有原函数。**

### 常用不定积分公式

以下 $C$ 为任意常数，公式在被积函数有定义的各个区间内使用；含参数 $a$ 的公式统一取 $a>0$。

#### 三角函数的积分

$$
\int\tan x\,\mathrm dx=-\ln|\cos x|+C,\qquad
\int\cot x\,\mathrm dx=\ln|\sin x|+C.
$$

$$
\boxed{\int\frac{\mathrm dx}{\cos x}
=\int\sec x\,\mathrm dx=\ln|\sec x+\tan x|+C}.
$$

$$
\boxed{\int\frac{\mathrm dx}{\sin x}
=\int\csc x\,\mathrm dx=\ln|\csc x-\cot x|+C}.
$$

$$
\int\sec^2x\,\mathrm dx=\tan x+C,\qquad
\int\csc^2x\,\mathrm dx=-\cot x+C.
$$

$$
\int\sec x\tan x\,\mathrm dx=\sec x+C,\qquad
\int\csc x\cot x\,\mathrm dx=-\csc x+C.
$$

**记忆：** $\tan x=\sin x/\cos x$，令 $u=\cos x$ 即得 $-\ln|\cos x|$；余切同理。正割、余割分别为 $\sec x=1/\cos x$、$\csc x=1/\sin x$。

#### 反正切型与反正弦型

$$
\int\frac1{1+x^2}\,\mathrm dx=\arctan x+C,\qquad
\boxed{\int\frac1{a^2+x^2}\,\mathrm dx=\frac1a\arctan\frac xa+C}.
$$

$$
\int\frac1{\sqrt{1-x^2}}\,\mathrm dx=\arcsin x+C
\qquad(|x|<1),
$$

$$
\boxed{\int\frac1{\sqrt{a^2-x^2}}\,\mathrm dx=\arcsin\frac xa+C}
\qquad(|x|<a).
$$

**换元提示：** 含 $a$ 时令 $u=x/a$。注意反正切型的结果有系数 $1/a$，反正弦型没有。

#### 根式分母的对数型

$$
\boxed{\int\frac1{\sqrt{x^2+a^2}}\,\mathrm dx
=\ln\left(x+\sqrt{x^2+a^2}\right)+C}.
$$

这里 $a>0$，故 $x+\sqrt{x^2+a^2}>0$，不必加绝对值；常见情形为 $a=1$。

$$
\boxed{\int\frac1{\sqrt{x^2-a^2}}\,\mathrm dx
=\ln\left|x+\sqrt{x^2-a^2}\right|+C}
\qquad(|x|>a).
$$

#### 平方差分母

$$
\boxed{\int\frac1{x^2-a^2}\,\mathrm dx
=\frac1{2a}\ln\left|\frac{x-a}{x+a}\right|+C}
\qquad(x\ne\pm a).
$$

$$
\boxed{\int\frac1{a^2-x^2}\,\mathrm dx
=\frac1{2a}\ln\left|\frac{x+a}{x-a}\right|+C}
\qquad(x\ne\pm a).
$$

**记忆：** 分母变号，结果也变号；对数前的负号可通过分式取倒数吸收。

#### 半圆根式

$$
\boxed{\int\sqrt{a^2-x^2}\,\mathrm dx
=\frac{a^2}{2}\arcsin\frac xa+\frac x2\sqrt{a^2-x^2}+C}
\qquad(|x|<a).
$$

#### 三角函数平方：先降幂或用恒等式

$$
\int\sin^2x\,\mathrm dx=\frac x2-\frac{\sin2x}{4}+C,
\qquad \sin^2x=\frac{1-\cos2x}{2}.
$$

$$
\int\cos^2x\,\mathrm dx=\frac x2+\frac{\sin2x}{4}+C,
\qquad \cos^2x=\frac{1+\cos2x}{2}.
$$

$$
\int\tan^2x\,\mathrm dx=\tan x-x+C,
\qquad \tan^2x=\sec^2x-1.
$$

$$
\int\cot^2x\,\mathrm dx=-\cot x-x+C,
\qquad \cot^2x=\csc^2x-1.
$$

#### 指数函数与正弦、余弦乘积的积分

本组公式中 $a,b\in\mathbb R$，且 $a^2+b^2>0$（不要求 $a>0$）。

$$
\boxed{\int e^{ax}\sin bx\,\mathrm dx
=\frac{e^{ax}(a\sin bx-b\cos bx)}{a^2+b^2}+C}.
$$

$$
\boxed{\int e^{ax}\cos bx\,\mathrm dx
=\frac{e^{ax}(a\cos bx+b\sin bx)}{a^2+b^2}+C}.
$$

**行列式记法：** 对 $g(x)=\sin bx$ 或 $g(x)=\cos bx$，均可写为

$$
\int e^{ax}g(x)\,\mathrm dx
=\frac1{a^2+b^2}
\begin{vmatrix}
(e^{ax})'&g'(x)\\
e^{ax}&g(x)
\end{vmatrix}+C
=\frac{(e^{ax})'g(x)-e^{ax}g'(x)}{a^2+b^2}+C.
$$

**记忆：分母为 $a^2+b^2$；分子为“指数求导乘三角，减去指数乘三角求导”。** 这两式也可通过连续两次分部积分得到。

### 有理函数积分：部分分式分解

对有理函数 $P(x)/Q(x)$，**先化为真分式** ：若 $\deg P\ge\deg Q$，先做多项式除法，将其写为“多项式 + 真分式”。再把分母在实数范围内分解为一次因式和不可约二次因式，按下列规则设待定系数。

#### ① 一次单因式

分母中的一次单因式 $ax+b$ 对应一项

$$
\frac{A}{ax+b}.
$$

#### ② k 重一次因式

分母中的 $(ax+b)^k$ 对应 $k$ 项：

$$
\frac{A_1}{ax+b}+\frac{A_2}{(ax+b)^2}
+\cdots+\frac{A_k}{(ax+b)^k}.
$$

#### ③ 不可约二次单因式

分母中的二次单因式 $px^2+qx+r$（$p\ne0$，$q^2-4pr<0$）对应一项

$$
\frac{Ax+B}{px^2+qx+r}.
$$

#### ④ k 重不可约二次因式

分母中的 $(px^2+qx+r)^k$（$q^2-4pr<0$）对应 $k$ 项：

$$
\frac{A_1x+B_1}{px^2+qx+r}
+\frac{A_2x+B_2}{(px^2+qx+r)^2}
+\cdots+\frac{A_kx+B_k}{(px^2+qx+r)^k}.
$$

上述一次因式要求 $a\ne0$，$k$ 为正整数，各分子中的系数分别待定。

#### 例：两类重因式同时出现

若 $P/Q$ 为真分式，且

$$
Q(x)=(ax+b)^2(px^2+qx+r)^2,\qquad q^2-4pr<0,
$$

则设

$$
\boxed{\frac{P(x)}{Q(x)}
=\frac{A_1}{ax+b}+\frac{A_2}{(ax+b)^2}
+\frac{A_3x+B}{px^2+qx+r}
+\frac{A_4x+C}{(px^2+qx+r)^2}}.
$$

两边同乘 $Q(x)$，通过代入特殊值或比较同次幂系数，求出待定系数后逐项积分。

**记忆：一次因式配常数分子，二次因式配一次分子；重因式从一次幂到最高次幂逐项写全，不能只写最高次幂。**

### 定积分存在的充分条件

设 $a<b$，$f$ 在闭区间 $[a,b]$ 上有定义。满足以下条件中的**任意一条** ，即可保证定积分 $\displaystyle\int_a^b f(x)\,\mathrm dx$ 存在（黎曼可积）：

1. **闭区间上连续** ：$f$ 在 $[a,b]$ 上连续。
2. **闭区间上单调** ：$f$ 在 $[a,b]$ 上单调，不要求连续。
3. **有界且只有有限个间断点** ：$f$ 在 $[a,b]$ 上有界，且间断点只有有限个。

**以上均为充分条件，不是必要条件。** 定积分存在不要求函数处处连续；第三条中的“有界”不能省略。

**必要条件：定积分存在必有界。** 若 $f$ 在 $[a,b]$ 上黎曼可积，则 $f$ 在该闭区间上必有界；反过来，仅有界不能保证可积。因此，**有界是黎曼可积的必要不充分条件** 。这里讨论普通定积分，不包括反常积分。

### 定积分的极限表达式（等分区间，取右端点）

设 $a<b$，$f$ 在 $[a,b]$ 上黎曼可积（例如在该闭区间上连续），则

$$
\boxed{
\int_a^b f(x)\,\mathrm dx
=\lim_{n\to\infty}\frac{b-a}{n}
\sum_{i=1}^{n}f\left(a+\frac{i(b-a)}{n}\right)
}
$$

将 $[a,b]$ 等分为 $n$ 个小区间，每个小区间的宽度为 $\Delta x=\dfrac{b-a}{n}$，第 $i$ 个小区间的右端点为 $x_i=a+\dfrac{i(b-a)}{n}$。因此，上式就是 $\lim_{n\to\infty}\sum_{i=1}^{n}f(x_i)\Delta x$。

#### 特殊情形：积分区间为 $[0,1]$

取 $a=0$、$b=1$，若 $f(x)$ 在 $[0,1]$ 上黎曼可积，则

$$
\boxed{
\int_0^1 f(x)\,\mathrm dx
=\lim_{n\to\infty}\frac1n\sum_{i=1}^{n}f\left(\frac in\right)
}
$$

此时小区间宽度为 $\Delta x=\dfrac1n$，右端点为 $x_i=\dfrac in$。求和式极限中出现“$\dfrac1n\sum_{i=1}^{n}f\left(\dfrac in\right)$”时，可识别为上述定积分。

### 定积分的保号性、保序性与绝对值不等式

以下均设 $a<b$，$f(x)$、$g(x)$ 在 $[a,b]$ 上黎曼可积；函数之间的不等式要求对所有 $x\in[a,b]$ 成立。

#### 保号性

$$
\boxed{
f(x)\ge0
\quad\Longrightarrow\quad
\int_a^b f(x)\,\mathrm dx\ge0
}
$$

#### 保序性

$$
\boxed{
f(x)\le g(x)
\quad\Longrightarrow\quad
\int_a^b f(x)\,\mathrm dx
\le\int_a^b g(x)\,\mathrm dx
}
$$

#### 绝对值不等式

$$
\boxed{
\left|\int_a^b f(x)\,\mathrm dx\right|
\le\int_a^b |f(x)|\,\mathrm dx
}
$$

**积分的绝对值不大于绝对值的积分。** $f(x)$ 黎曼可积时，$|f(x)|$ 也黎曼可积。

### 周期函数在一个周期内的积分

设 $f$ 是以 $T>0$ 为周期的连续函数，则对任意实数 $a$，

$$
\boxed{\int_a^{a+T}f(x)\,\mathrm dx=\int_0^T f(x)\,\mathrm dx}.
$$

**在长度为一个周期的区间上的定积分，与区间的起点位置无关。**

### 区间再现公式

设 $f$ 在 $[a,b]$ 上连续，令 $t=a+b-x$，则

$$
\boxed{\int_a^b f(x)\,\mathrm dx=\int_a^b f(a+b-x)\,\mathrm dx}.
$$

**记忆：用“上下限之和减去 $x$”替换 $x$，积分区间和积分值不变。**

### 正弦、余弦幂次的定积分（华里士公式）

#### 区间 $[0,\pi/2]$

对正整数 $n$，记

$$
I_n=\int_0^{\pi/2}\sin^n x\,\mathrm dx
=\int_0^{\pi/2}\cos^n x\,\mathrm dx.
$$

则

$$
\boxed{I_n=
\begin{cases}
\dfrac{n-1}{n}\cdot\dfrac{n-3}{n-2}\cdots\dfrac23\cdot1,
&n>1\text{ 为奇数},\\[6pt]
\dfrac{n-1}{n}\cdot\dfrac{n-3}{n-2}\cdots\dfrac12\cdot\dfrac\pi2,
&n\text{ 为正偶数}.
\end{cases}}
$$

初值和递推关系为

$$
\boxed{I_0=\frac\pi2,\qquad I_1=1,\qquad
I_n=\frac{n-1}{n}I_{n-2}\quad(n\ge2)}.
$$

**记忆：分子比分母小 $1$，每次同时减 $2$；奇数次幂最后乘 $1$，偶数次幂最后乘 $\pi/2$。**

#### 区间 $[0,\pi]$

由 $\sin(\pi-x)=\sin x$，有

$$
\boxed{\int_0^\pi\sin^n x\,\mathrm dx=2I_n
=\begin{cases}
2\cdot\dfrac{n-1}{n}\cdot\dfrac{n-3}{n-2}\cdots\dfrac23\cdot1,
&n>1\text{ 为奇数},\\[6pt]
2\cdot\dfrac{n-1}{n}\cdot\dfrac{n-3}{n-2}\cdots\dfrac12\cdot\dfrac\pi2,
&n\text{ 为正偶数}.
\end{cases}}
$$

其中 $n=1$ 时，$\displaystyle\int_0^\pi\sin x\,\mathrm dx=2$。

由 $\cos(\pi-x)=-\cos x$，有

$$
\boxed{\int_0^\pi\cos^n x\,\mathrm dx
=\begin{cases}
0,&n\text{ 为正奇数},\\[4pt]
2I_n=2\cdot\dfrac{n-1}{n}\cdot\dfrac{n-3}{n-2}\cdots\dfrac12\cdot\dfrac\pi2,
&n\text{ 为正偶数}.
\end{cases}}
$$

#### 区间 $[0,2\pi]$

$$
\boxed{\int_0^{2\pi}\cos^n x\,\mathrm dx
=\int_0^{2\pi}\sin^n x\,\mathrm dx
=\begin{cases}
0,&n\text{ 为正奇数},\\[4pt]
4I_n=4\cdot\dfrac{n-1}{n}\cdot\dfrac{n-3}{n-2}\cdots\dfrac12\cdot\dfrac\pi2,
&n\text{ 为正偶数}.
\end{cases}}
$$

**区间换算要点：** $[0,\pi]$ 上正弦幂积分总是半区间的 $2$ 倍，余弦奇数次幂积分为 $0$；$[0,2\pi]$ 上两者的奇数次幂积分都为 $0$，偶数次幂积分都是 $I_n$ 的 $4$ 倍。

### 定积分的估值定理

设 $a<b$，$f(x)$ 在 $[a,b]$ 上黎曼可积，且对所有 $x\in[a,b]$ 有

$$
m\le f(x)\le M,
$$

其中 $m,M$ 为常数，则

$$
\boxed{
m(b-a)\le\int_a^b f(x)\,\mathrm dx\le M(b-a)
}
$$

$m,M$ 可以是任意满足条件的下界、上界，不一定是最小值、最大值。该结论可由定积分的保序性得到。

### 积分中值定理

设 $a<b$，$f(x)$ 在闭区间 $[a,b]$ 上**连续** ，则至少存在一点 $\xi\in(a,b)$，使得

$$
\boxed{
\int_a^b f(x)\,\mathrm dx=f(\xi)(b-a)
}
$$

等价地，

$$
f(\xi)=\frac{1}{b-a}\int_a^b f(x)\,\mathrm dx.
$$

即函数在区间内部至少有一点的函数值等于它在该区间上的**平均值** 。$\xi$ 不一定唯一；仅有可积条件，不能保证存在这样的 $\xi$。

#### 推广：带权积分中值定理（例 11.1）

设 $a<b$，$f(x),g(x)$ 在 $[a,b]$ 上连续，且 **$g(x)$ 在 $[a,b]$ 上不变号** ，即恒有 $g(x)\ge0$ 或恒有 $g(x)\le0$，允许在某些点取 $0$，则存在 $\xi\in(a,b)$，使

$$
\boxed{\int_a^b f(x)g(x)\,\mathrm dx
=f(\xi)\int_a^b g(x)\,\mathrm dx}.
$$

**记忆：权函数 $g$ 不变号，就能把连续函数 $f$ 以某个中间值 $f(\xi)$ 提出积分号；留下的 $g$ 仍要积分。** 应用时需明确哪一部分作为不变号的权函数，不能让它在区间内正负交替。

若 $g$ 不恒为 $0$，可写为

$$
f(\xi)=\frac{\displaystyle\int_a^b f(x)g(x)\,\mathrm dx}
{\displaystyle\int_a^b g(x)\,\mathrm dx},
$$

即某个内点的函数值等于 $f$ 在该权重下的平均值。若 $g\equiv0$，原等式对任意 $\xi\in(a,b)$ 都成立，但不能写上述比值。

**证明思路：** 若 $g\not\equiv0$，令 $w(x)=|g(x)|$，则 $A=\int_a^b w(x)\,\mathrm dx>0$。记

$$
c=\frac1A\int_a^b f(x)w(x)\,\mathrm dx,
\qquad\int_a^b[f(x)-c]w(x)\,\mathrm dx=0.
$$

若区间内部没有点满足 $f(x)=c$，由连续性与介值定理，$f(x)-c$ 在 $(a,b)$ 内必严格同号。又 $w\ge0$ 且连续、不恒为 $0$，上式积分必严格为正或严格为负，矛盾。故存在 $\xi\in(a,b)$ 使 $f(\xi)=c$；再由 $g$ 不变号，即得结论。

**特别地，取 $g(x)\equiv1$，就得到普通积分中值定理：**

$$
\boxed{\int_a^b f(x)\,\mathrm dx=f(\xi)(b-a),\qquad\xi\in(a,b)}.
$$

积分中值定理及上述满足条件的带权形式，考试中可以直接引用；题目要求证明定理时，再写明证明过程。

### 变上限积分求导（微积分基本定理）

#### 可积则变上限积分连续

若 $f(x)$ 在 $[a,b]$ 上黎曼可积，令

$$
F(x)=\int_a^x f(t)\,\mathrm dt,
$$

则 **$F(x)$ 在 $[a,b]$ 上连续** ，但不一定处处可导。

因为可积必有界，可取 $M\ge0$ 使 $|f(t)|\le M$，于是对任意 $x,y\in[a,b]$，

$$
|F(x)-F(y)|
=\left|\int_y^x f(t)\,\mathrm dt\right|
\le M|x-y|,
$$

从而得到 $F(x)$ 的连续性。**被积函数可积，就能保证变上限积分连续，不要求被积函数连续。**

#### 连续则变上限积分可导

**记忆：被积函数连续，变上限积分函数可导，求导后等于被积函数。** 此时变上限积分函数就是被积函数的一个原函数。

设 $f(x)$ 在区间 $I$ 上连续，固定 $a\in I$，令

$$
F(x)=\int_a^x f(t)\,\mathrm dt,
$$

则 $F(x)$ 在区间 $I$ 的内部可导，且

$$
\boxed{
F'(x)=\frac{\mathrm d}{\mathrm dx}\left[\int_a^x f(t)\,\mathrm dt\right]=f(x)
}
$$

其中 $t$ 是积分变量，$x$ 是积分上限，$a$ 是固定下限。**连续函数的变上限积分是它的一个原函数。** 若区间包含端点，则在端点处理解为相应的单侧导数。

#### 上下限都是函数时的求导公式

设 $f$ 在 $[a,b]$ 上连续，$\varphi_1(x)$、$\varphi_2(x)$ 在公共定义区间内可导，且它们的值都在 $[a,b]$ 内。令

$$
F(x)=\int_{\varphi_1(x)}^{\varphi_2(x)}f(t)\,\mathrm dt,
$$

则在该定义区间内部有

$$
\boxed{
F'(x)
=\frac{\mathrm d}{\mathrm dx}
\left[\int_{\varphi_1(x)}^{\varphi_2(x)}f(t)\,\mathrm dt\right]
=f\bigl(\varphi_2(x)\bigr)\varphi_2'(x)
-f\bigl(\varphi_1(x)\bigr)\varphi_1'(x)
}.
$$

**记忆：上限代入乘上限的导数，减去下限代入乘下限的导数。**

**推导：** 将积分拆成两个固定下限的积分：

$$
F(x)=\int_a^{\varphi_2(x)}f(t)\,\mathrm dt
-\int_a^{\varphi_1(x)}f(t)\,\mathrm dt,
$$

再分别使用微积分基本定理和链式法则即可。

特别地，$c$ 为固定常数时，

$$
\frac{\mathrm d}{\mathrm dx}\int_c^{\varphi(x)}f(t)\,\mathrm dt
=f\bigl(\varphi(x)\bigr)\varphi'(x),
\qquad
\frac{\mathrm d}{\mathrm dx}\int_{\varphi(x)}^c f(t)\,\mathrm dt
=-f\bigl(\varphi(x)\bigr)\varphi'(x).
$$

**注意：这里被积函数只依赖积分变量 $t$；若被积函数还显含 $x$，不能直接只用上述两项求导。**

### 区间内部有瑕点的反常积分

设 $c\in(a,b)$ 是 $f(x)$ 在 $[a,b]$ 上唯一的瑕点（在 $c$ 附近无界），且 $f$ 在避开 $c$ 的闭子区间上可积。必须在瑕点处分开：

$$
\boxed{\int_a^b f(x)\,\mathrm dx
=\int_a^c f(x)\,\mathrm dx+\int_c^b f(x)\,\mathrm dx}.
$$

其中，两侧的反常积分分别定义为

$$
\int_a^c f(x)\,\mathrm dx
=\lim_{t\to c^-}\int_a^t f(x)\,\mathrm dx,
\qquad
\int_c^b f(x)\,\mathrm dx
=\lim_{s\to c^+}\int_s^b f(x)\,\mathrm dx.
$$

**只有两侧极限都存在且有限时，原反常积分才收敛，其值为两者之和；只要有一侧发散，原反常积分就发散。**

两侧极限须独立求取，不能用对称趋近时的正负抵消代替。例如 $\displaystyle\int_{-1}^1\frac1x\,\mathrm dx$ 发散，虽然对称截断的两段积分之和恒为 $0$。

### 由无穷远处的函数极限初步判断积分敛散性

设 $f$ 在 $[1,+\infty)$ 的任意有限闭子区间上可积，则

| $\displaystyle\lim_{x\to+\infty}f(x)$ | $\displaystyle\int_1^{+\infty}f(x)\,\mathrm dx$ |
| ------------------------------------- | ----------------------------------------------- |
| 无穷（$\pm\infty$）                   | 一定发散                                        |
| 非零常数                              | 一定发散                                        |
| $0$                                   | 可能收敛，也可能发散，需进一步判断              |

例如 $1/x^2$ 与 $1/x$ 在无穷远处都趋于 $0$，但在 $[1,+\infty)$ 上的积分分别收敛、发散。

**注意：若已知函数极限存在，积分收敛则该极限必为 $0$；一般情况下，不能由积分收敛直接推出 $f(x)\to0$，因为函数极限可能不存在。**

### 两类常用的 p 型积分

设 $p\in\mathbb R$。

#### 从 0 到 1：考察零点附近

$$
\boxed{\int_0^1\frac1{x^p}\,\mathrm dx
\begin{cases}
\text{收敛，值为 }\dfrac1{1-p},&p<1,\\
\text{发散},&p\ge1.
\end{cases}}
$$

当 $p>0$ 时，$x=0$ 是瑕点；当 $p\le0$ 时，被积函数可在 $0$ 处连续补定义，积分也收敛。

#### 从 1 到正无穷：考察无穷远处

$$
\boxed{\int_1^{+\infty}\frac1{x^p}\,\mathrm dx
\begin{cases}
\text{收敛，值为 }\dfrac1{p-1},&p>1,\\
\text{发散},&p\le1.
\end{cases}}
$$

**记忆：零点附近 $p<1$ 收敛，无穷远处 $p>1$ 收敛；临界值 $p=1$ 两者都发散。** 这两类积分常用作比较判别法的参照。

### 反常积分小常识：对数、幂函数与指数函数的增长比较

**以下均对任意 $a>0$ 成立。**

- 当 $x\to0^+$ 时，$|\ln x|$ 的增长速度小于 $1/x^a$：

  $$
  \boxed{|\ln x|=o\!\left(\frac1{x^a}\right)\quad(x\to0^+)}
  \quad\Longleftrightarrow\quad
  \lim_{x\to0^+}x^a|\ln x|=0.
  $$

- 当 $x\to+\infty$ 时，$\ln x$ 的增长速度小于 $x^a$：

  $$
  \boxed{\ln x=o(x^a)\quad(x\to+\infty)}
  \quad\Longleftrightarrow\quad
  \lim_{x\to+\infty}\frac{\ln x}{x^a}=0.
  $$

- 当 $x\to+\infty$ 时，对任意 $a>0$、$p>0$，幂函数 $x^p$ 的增长速度小于指数函数 $e^{ax}$：

  $$
  \boxed{x^p=o(e^{ax})\quad(x\to+\infty)}
  \quad\Longleftrightarrow\quad
  \lim_{x\to+\infty}\frac{x^p}{e^{ax}}=0.
  $$

**记忆：当 $x\to+\infty$ 且 $a,p>0$ 时，对数增长慢于正幂，正幂增长慢于正指数：**

$$
\boxed{\ln x=o(x^p),\qquad x^p=o(e^{ax})}.
$$

这里指数比较要求 $a>0$；当 $x\to0^+$ 时，$e^{ax}\to1$，不能套用无穷远处的增长顺序。

**应用：** 在瑕点 $0$ 附近或无穷远处，可用任意小的正幂控制对数项；在无穷远处，还可用指数衰减控制幂函数因子，再结合比较判别法判断敛散性。上述结论描述的是极限趋势，不是对所有 $x$ 都成立的大小关系。

#### 例：指数衰减压过幂函数增长

设 $a>0$、$p>0$，判断 $\displaystyle\int_1^{+\infty}x^pe^{-ax}\,\mathrm dx$ 的敛散性。取比较函数 $g(x)=1/x^2$，则

$$
\lim_{x\to+\infty}\frac{x^pe^{-ax}}{1/x^2}
=\lim_{x\to+\infty}\frac{x^{p+2}}{e^{ax}}=0.
$$

因为 $\int_1^{+\infty}x^{-2}\,\mathrm dx$ 收敛，由极限比较判别法，**原积分收敛** 。注意：仅知道被积函数趋于 $0$ 还不能判断积分收敛，必须进一步比较。

#### 例：无穷远处用 $x^a$ 控制 $\ln x$

判断 $\displaystyle\int_1^{+\infty}\frac{\ln x}{x^{3/2}}\,\mathrm dx$ 的敛散性。

由 $\ln x=o(x^a)$，选择比较函数

$$
g(x)=\frac{x^a}{x^{3/2}}=\frac1{x^{3/2-a}}.
$$

要使 $\int_1^{+\infty}g(x)\,\mathrm dx$ 收敛，需要

$$
\frac32-a>1,\qquad a>0
\quad\Longrightarrow\quad\boxed{0<a<\frac12}.
$$

例如取 $a=\frac14$，则 $g(x)=1/x^{5/4}$，且

$$
\lim_{x\to+\infty}
\frac{\ln x/x^{3/2}}{1/x^{5/4}}
=\lim_{x\to+\infty}\frac{\ln x}{x^{1/4}}=0.
$$

因为 $\int_1^{+\infty}x^{-5/4}\,\mathrm dx$ 收敛，由极限比较判别法，**原积分收敛** 。

#### 例：零点附近用 $1/x^a$ 控制 $|\ln x|$

判断 $\displaystyle\int_0^1\frac{|\ln x|}{\sqrt x}\,\mathrm dx$ 的敛散性。

由 $|\ln x|=o(1/x^a)$（$x\to0^+$），选择比较函数

$$
g(x)=\frac{1/x^a}{\sqrt x}=\frac1{x^{1/2+a}}.
$$

要使 $\int_0^1g(x)\,\mathrm dx$ 收敛，需要

$$
\frac12+a<1,\qquad a>0
\quad\Longrightarrow\quad\boxed{0<a<\frac12}.
$$

例如取 $a=\frac14$，则 $g(x)=1/x^{3/4}$，且

$$
\lim_{x\to0^+}
\frac{|\ln x|/\sqrt x}{1/x^{3/4}}
=\lim_{x\to0^+}x^{1/4}|\ln x|=0.
$$

因为 $\int_0^1x^{-3/4}\,\mathrm dx$ 收敛，由极限比较判别法，**原积分收敛** 。

**选指数的关键：先用正幂控制对数，再让比较函数的幂指数满足收敛条件——无穷远处大于 $1$，零点附近小于 $1$。这两个例子都可取 $a=1/4$。**

#### 常用积分：对数绝对值

$$
\boxed{\int_0^1|\ln x|\,\mathrm dx=1}.
$$

因为 $0<x\le1$ 时 $|\ln x|=-\ln x$，且 $\lim_{x\to0^+}x\ln x=0$，所以

$$
\begin{aligned}
\int_0^1|\ln x|\,\mathrm dx
&=\lim_{\varepsilon\to0^+}\int_\varepsilon^1-\ln x\,\mathrm dx\\
&=\lim_{\varepsilon\to0^+}\left[-x\ln x+x\right]_\varepsilon^1\\
&=\lim_{\varepsilon\to0^+}(1+\varepsilon\ln\varepsilon-\varepsilon)=1.
\end{aligned}
$$

#### 常见结论：零点附近的对数除以幂函数

设 $p\in\mathbb R$，则

$$
\boxed{\int_0^1\frac{\ln x}{x^p}\,\mathrm dx
\begin{cases}
\text{绝对收敛，值为 }-\dfrac1{(1-p)^2},&p<1,\\
\text{发散到 }-\infty,&p\ge1.
\end{cases}}
$$

因为 $0<x<1$ 时 $\ln x<0$，换成 $|\ln x|$ 后，敛散范围相同，但收敛时积分值为 $1/(1-p)^2$，发散时趋于 $+\infty$。

**判断方法：** 当 $p<1$ 时，取 $0<a<1-p$，由 $|\ln x|=o(1/x^a)$，有

$$
\frac{|\ln x|}{x^p}
=o\!\left(\frac1{x^{p+a}}\right)\qquad(x\to0^+).
$$

由于 $p+a<1$，比较积分收敛，所以原积分绝对收敛。当 $p\ge1$ 时，在 $0<x\le e^{-1}$ 上有 $|\ln x|\ge1$，故

$$
\frac{|\ln x|}{x^p}\ge\frac1{x^p},
$$

由 $p$ 型积分的发散性可知，原积分发散到 $-\infty$。

**其中 $p<0$ 也收敛，已包含在 $p<1$ 的范围内。**

#### 常见结论：无穷远处的对数除以幂函数

设 $p\in\mathbb R$，则

$$
\boxed{\int_1^{+\infty}\frac{\ln x}{x^p}\,\mathrm dx
\begin{cases}
\text{收敛，值为 }\dfrac1{(p-1)^2},&p>1,\\
\text{发散到 }+\infty,&p\le1.
\end{cases}}
$$

**判断方法：** 当 $p>1$ 时，取 $0<a<p-1$，由 $\ln x=o(x^a)$，有

$$
\frac{\ln x}{x^p}=o\!\left(\frac1{x^{p-a}}\right)
\qquad(x\to+\infty).
$$

由于 $p-a>1$，比较积分收敛，所以原积分收敛。当 $p\le1$ 时，在 $x\ge e$ 上有 $\ln x\ge1$，故

$$
\frac{\ln x}{x^p}\ge\frac1{x^p},
$$

由 $p$ 型积分的发散性可知，原积分发散到 $+\infty$。

**对照记忆：对于 $\ln x/x^p$，从 $0$ 到 $1$ 是 $p<1$ 收敛，从 $1$ 到正无穷是 $p>1$ 收敛；$p=1$ 时两者都发散。**

### 反常积分的比较判别法

#### 无穷区间上的比较判别法

设 $f(x),g(x)$ 在 $[a,+\infty)$ 上连续，且 $0\le f(x)\le g(x)$，则

$$
\boxed{\int_a^{+\infty}g(x)\,\mathrm dx\text{ 收敛}
\ \Longrightarrow\ \int_a^{+\infty}f(x)\,\mathrm dx\text{ 收敛}},
$$

$$
\boxed{\int_a^{+\infty}f(x)\,\mathrm dx\text{ 发散}
\ \Longrightarrow\ \int_a^{+\infty}g(x)\,\mathrm dx\text{ 发散}}.
$$

#### 无界函数的比较判别法（瑕积分）

设 $f(x),g(x)$ 在 $(a,b]$ 上连续，瑕点同为 $x=a$，且 $0\le f(x)\le g(x)$（$a<x\le b$），则

$$
\boxed{\int_a^b g(x)\,\mathrm dx\text{ 收敛}
\ \Longrightarrow\ \int_a^b f(x)\,\mathrm dx\text{ 收敛}},
$$

$$
\boxed{\int_a^b f(x)\,\mathrm dx\text{ 发散}
\ \Longrightarrow\ \int_a^b g(x)\,\mathrm dx\text{ 发散}}.
$$

**记忆：大者收敛，则小者收敛；小者发散，则大者发散。反向不能直接推出。** 比较不等式只需在充分大的 $x$ 处或瑕点附近成立，其余部分可积即可。

### 反常积分比较判别法的极限形式

#### 无穷区间的情形

设 $f(x),g(x)$ 在 $[a,+\infty)$ 上连续，$f(x)\ge0$、$g(x)>0$，且

$$
\lim_{x\to+\infty}\frac{f(x)}{g(x)}=\lambda
\qquad(0\le\lambda\le+\infty).
$$

记 $I_f=\displaystyle\int_a^{+\infty}f(x)\,\mathrm dx$，$I_g=\displaystyle\int_a^{+\infty}g(x)\,\mathrm dx$，则

| 比值极限            | 判别结论                          |
| ------------------- | --------------------------------- |
| $0<\lambda<+\infty$ | $I_f$ 与 $I_g$ 同敛散             |
| $\lambda=0$         | $I_g$ 收敛 $\Rightarrow I_f$ 收敛 |
| $\lambda=+\infty$   | $I_g$ 发散 $\Rightarrow I_f$ 发散 |

#### 瑕积分的情形

设 $f(x),g(x)$ 在 $(a,b]$ 上连续，瑕点同为 $x=a$，$f(x)\ge0$、$g(x)>0$，且

$$
\lim_{x\to a^+}\frac{f(x)}{g(x)}=\lambda
\qquad(0\le\lambda\le+\infty).
$$

记 $I_f=\displaystyle\int_a^b f(x)\,\mathrm dx$，$I_g=\displaystyle\int_a^b g(x)\,\mathrm dx$，则同样有

| 比值极限            | 判别结论                          |
| ------------------- | --------------------------------- |
| $0<\lambda<+\infty$ | $I_f$ 与 $I_g$ 同敛散             |
| $\lambda=0$         | $I_g$ 收敛 $\Rightarrow I_f$ 收敛 |
| $\lambda=+\infty$   | $I_g$ 发散 $\Rightarrow I_f$ 发散 |

若瑕点为右端点 $b$，改取 $x\to b^-$；若瑕点在区间内部，先在瑕点处分开，再分别判别。

**要点：比值趋于有限正数时才能直接判断同敛散；比值趋于 $0$ 或 $+\infty$ 时，只能按表中的方向推断（或使用其逆否命题）。这些判别法用于非负函数，不能直接套用于任意变号函数。**

### 反常积分的绝对收敛与条件收敛

设 $f$ 在 $[1,+\infty)$ 的任意有限闭子区间上可积。

- **绝对收敛：** $\displaystyle\int_1^{+\infty}|f(x)|\,\mathrm dx$ 收敛。
- **条件收敛：** $\displaystyle\int_1^{+\infty}f(x)\,\mathrm dx$ 收敛，但 $\displaystyle\int_1^{+\infty}|f(x)|\,\mathrm dx$ 发散。

**绝对收敛一定推出原积分收敛；原积分收敛不一定绝对收敛。**

### 狄利克雷判别法（反常积分）

设 $f$ 在 $[a,+\infty)$ 的任意有限闭子区间上可积，且变上限积分有界，即存在常数 $M>0$，使

$$
\left|\int_a^t f(x)\,\mathrm dx\right|\le M\qquad(t\ge a).
$$

若 $g(x)$ 在 $[a,+\infty)$ 上单调，且 $\lim_{x\to+\infty}g(x)=0$，则

$$
\boxed{\int_a^{+\infty}f(x)g(x)\,\mathrm dx\text{ 收敛}}.
$$

**直观记忆：振荡抵消 + 单调衰减到零 $\Longrightarrow$ 积分收敛。** 其中“振荡抵消”的准确条件是 $\int_a^t f(x)\,\mathrm dx$ 有界，仅有 $f(x)$ 自身有界或正负交替还不够。该判别法保证收敛，不直接判断是否绝对收敛。

#### 常见结论：正弦、余弦除以幂函数

$$
\int_1^{+\infty}\frac{\sin x}{x^p}\,\mathrm dx,
\qquad
\int_1^{+\infty}\frac{\cos x}{x^p}\,\mathrm dx.
$$

两者的敛散性相同：

| $p$ 的范围 | 敛散性   |
| ---------- | -------- |
| $p>1$      | 绝对收敛 |
| $0<p\le1$  | 条件收敛 |
| $p\le0$    | 发散     |

**① $p>0$ 时收敛。** 因为

$$
\int_1^t\sin x\,\mathrm dx=\cos1-\cos t,\qquad
\int_1^t\cos x\,\mathrm dx=\sin t-\sin1
$$

都有界，且 $x^{-p}$ 单调递减至 $0$，由狄利克雷判别法，两积分均收敛。

**② $p>1$ 时绝对收敛。** 由

$$
\frac{|\sin x|}{x^p}\le\frac1{x^p},\qquad
\frac{|\cos x|}{x^p}\le\frac1{x^p},
$$

与 $p$ 型积分比较即可。

**③ $0<p\le1$ 时不绝对收敛。** 以正弦为例，在每段 $[n\pi+\pi/6,n\pi+5\pi/6]$ 上都有 $|\sin x|\ge1/2$，故对 $n\ge1$，

$$
\int_{n\pi+\pi/6}^{n\pi+5\pi/6}\frac{|\sin x|}{x^p}\,\mathrm dx
\ge\frac{\pi}{3[(n+1)\pi]^p}.
$$

这些互不重叠区间上的积分之和，由发散的 $\sum_{n=1}^{\infty}(n+1)^{-p}$ 控制下界，所以绝对值积分发散。余弦可在每个周期内选取 $|\cos x|\ge1/2$ 的区间，同理可证。因此两者均为条件收敛。

**④ $p\le0$ 时发散。** 以正弦为例，在 $[2n\pi+\pi/6,2n\pi+5\pi/6]$ 上有 $\sin x\ge1/2$，且 $x^{-p}\ge1$，所以

$$
\int_{2n\pi+\pi/6}^{2n\pi+5\pi/6}\frac{\sin x}{x^p}\,\mathrm dx\ge\frac\pi3.
$$

区间两端都趋于无穷，但这些尾部积分不趋于 $0$，不满足积分收敛的柯西准则，故发散。余弦在 $[2n\pi-\pi/3,2n\pi+\pi/3]$ 上同理。

### 定积分的几何应用：平面图形的面积

#### 直角坐标：上减下

设 $f(x)$、$g(x)$ 在 $[a,b]$ 上连续，且 $f(x)\ge g(x)$，则由两条曲线 $y=f(x)$、$y=g(x)$ 及直线 $x=a$、$x=b$ 围成的图形面积为

$$
\boxed{S=\int_a^b[f(x)-g(x)]\,\mathrm dx}.
$$

**记忆：上方曲线减下方曲线。** 面积微元为 $\mathrm dS=[f(x)-g(x)]\,\mathrm dx$；上下限 $a,b$ 是区域在 $x$ 轴上的投影端点。

若两条曲线在区间内交换上下位置，应在交点处分段，或写为

$$
S=\int_a^b|f(x)-g(x)|\,\mathrm dx.
$$

#### 极坐标：外半径平方减内半径平方

设在 $\theta\in[\alpha,\beta]$ 上，区域沿每条射线从内边界 $r=r_2(\theta)$ 延伸至外边界 $r=r_1(\theta)$，其中 $r_1,r_2$ 连续且 $0\le r_2(\theta)\le r_1(\theta)$，并且该角度区间恰好将区域扫过一次，则面积为

$$
\boxed{S=\frac12\int_\alpha^\beta\left[r_1^2(\theta)-r_2^2(\theta)\right]\,\mathrm d\theta}.
$$

**记忆：二分之一乘“外平方减内平方”。** 面积微元是两个小扇形的面积之差；$\alpha,\beta$ 是极角的起止值，角度用弧度表示。

当内边界为极点，即 $r_2(\theta)=0$ 时，化为

$$
S=\frac12\int_\alpha^\beta r^2(\theta)\,\mathrm d\theta.
$$

若内外边界发生交换，应分段积分；确定极角范围时要结合图形，避免重复计算同一区域。注意 $r_1^2-r_2^2\ne(r_1-r_2)^2$，不能先作半径差再平方。

### 旋转体体积：柱壳法（重点记忆）

设 $y=y(x)$ 在 $[a,b]$ 上连续，且 $0\le a<b$。曲线 $y=y(x)$ 与直线 $x=a$、$x=b$ 及 $x$ 轴围成的区域，绕 **$y$ 轴** 旋转一周，所得旋转体的体积为

$$
\boxed{V_y=2\pi\int_a^b x|y(x)|\,\mathrm dx}.
$$

**记忆：柱壳体积微元 = 周长 × 高 × 厚度。** 取一条竖直小条，绕 $y$ 轴旋转后形成薄柱壳，其半径为 $x$、高度为 $|y(x)|$、厚度为 $\mathrm dx$，因此

$$
\mathrm dV=2\pi x|y(x)|\,\mathrm dx.
$$

若 $y(x)\ge0$，可直接写为 $V_y=2\pi\int_a^b xy(x)\,\mathrm dx$。更一般地，若区域位于 $y=f(x)$ 与 $y=g(x)$ 之间，且 $f(x)\ge g(x)$、$0\le a<b$，则

$$
\boxed{V_y=2\pi\int_a^b x[f(x)-g(x)]\,\mathrm dx}.
$$

#### 何时比圆环法更方便

**已知 $y=y(x)$、绕 $y$ 轴旋转时，优先考虑柱壳法。** 它直接对 $x$ 积分，通常不必反解 $x=x(y)$；当反函数难求，或圆环法需要按 $y$ 分段时，柱壳法往往更简便。

| 方法   | 小条与旋转轴的关系 | 体积微元                                                             |
| ------ | ------------------ | -------------------------------------------------------------------- |
| 柱壳法 | 平行于旋转轴       | $\mathrm dV=2\pi\times\text{半径}\times\text{高度}\times\text{厚度}$ |
| 圆环法 | 垂直于旋转轴       | $\mathrm dV=\pi(\text{外半径}^2-\text{内半径}^2)\times\text{厚度}$   |

**柱壳法不一定在所有题目中都更简单，应选边界表达和分段更方便的方法。** 上式中的 $0\le a<b$ 保证 $x$ 就是柱壳半径；若区域跨越 $y$ 轴，旋转后可能重叠，不能简单把 $x$ 换成 $|x|$ 后对整个区间积分，否则可能重复计算体积。

### 绕任意定直线旋转的体积（重点公式）

设平面曲线 $L:y=f(x)$，$a\le x\le b$，$f$ 连续可导；旋转轴为

$$
L_0:Ax+By+C=0,\qquad A^2+B^2>0.
$$

**适用条件：任意一条垂直于 $L_0$ 的直线，与曲线 $L$ 至多有一个交点。** 即曲线沿旋转轴方向的投影不能折返。

以曲线到旋转轴的垂直线段旋转形成圆盘，各圆盘组成的旋转体体积为

$$
\boxed{
V=\frac{\pi}{(A^2+B^2)^{3/2}}
\int_a^b[Ax+Bf(x)+C]^2\,|Af'(x)-B|\,\mathrm dx
}.
$$

这里计算的是曲线、旋转轴及两端点到旋转轴的垂线段所界定区域旋转得到的**实体体积** ，不是曲线旋转形成的曲面面积。

#### 记忆与理解：圆盘面积乘轴向厚度

曲线上一点 $(x,f(x))$ 到旋转轴的距离为圆盘半径：

$$
r(x)=\frac{|Ax+Bf(x)+C|}{\sqrt{A^2+B^2}}.
$$

取旋转轴方向的单位向量 $\dfrac{(-B,A)}{\sqrt{A^2+B^2}}$，相应的轴向坐标及厚度为

$$
t(x)=\frac{-Bx+Af(x)}{\sqrt{A^2+B^2}},\qquad
|\mathrm dt|=\frac{|Af'(x)-B|}{\sqrt{A^2+B^2}}\,\mathrm dx.
$$

将二者代入 $\mathrm dV=\pi r^2|\mathrm dt|$，即得上述公式。**记住分母是 $(A^2+B^2)^{3/2}$，导数因子是 $|Af'(x)-B|$。**

#### 特例与使用提醒

- 绕 $x$ 轴：取 $A=0,B=1,C=0$，得到 $V=\pi\int_a^b f^2(x)\,\mathrm dx$。
- 绕水平直线 $y=k$：取 $A=0,B=1,C=-k$，得到 $V=\pi\int_a^b[f(x)-k]^2\,\mathrm dx$。
- 若某条垂直于旋转轴的直线与曲线有两个或更多交点，不能直接套用此式；应先分析截面，用圆环法等方法处理，避免重复计算。

### 平面曲边梯形的形心坐标

设 $f(x)$ 在 $[a,b]$ 上连续且非负，平面区域为

$$
D=\{(x,y)\mid a\le x\le b,\ 0\le y\le f(x)\},
$$

其面积 $S=\int_a^b f(x)\,\mathrm dx>0$。形心是区域的几何中心；若薄片面密度均匀，形心与质心重合。

#### 公式与二重积分化简过程

以 $\mathrm d\sigma$ 表示面积微元，形心横坐标为

$$
\begin{aligned}
\bar x
&=\frac{\iint_D x\,\mathrm d\sigma}{\iint_D\mathrm d\sigma}\\
&=\frac{\displaystyle\int_a^b\left[\int_0^{f(x)}x\,\mathrm dy\right]\mathrm dx}
{\displaystyle\int_a^b\left[\int_0^{f(x)}1\,\mathrm dy\right]\mathrm dx}\\
&=\frac{\displaystyle\int_a^b[xy]_0^{f(x)}\,\mathrm dx}
{\displaystyle\int_a^b[y]_0^{f(x)}\,\mathrm dx}\\
&=\boxed{\frac{\displaystyle\int_a^b xf(x)\,\mathrm dx}
{\displaystyle\int_a^b f(x)\,\mathrm dx}}.
\end{aligned}
$$

形心纵坐标为

$$
\begin{aligned}
\bar y
&=\frac{\iint_D y\,\mathrm d\sigma}{\iint_D\mathrm d\sigma}\\
&=\frac{\displaystyle\int_a^b\left[\int_0^{f(x)}y\,\mathrm dy\right]\mathrm dx}
{\displaystyle\int_a^b\left[\int_0^{f(x)}1\,\mathrm dy\right]\mathrm dx}\\
&=\frac{\displaystyle\int_a^b\left[\frac{y^2}{2}\right]_0^{f(x)}\,\mathrm dx}
{\displaystyle\int_a^b f(x)\,\mathrm dx}\\
&=\boxed{\frac{\displaystyle\frac12\int_a^b f^2(x)\,\mathrm dx}
{\displaystyle\int_a^b f(x)\,\mathrm dx}}.
\end{aligned}
$$

**计算顺序：先对 $y$ 积分，此时把 $x$ 看作常数；再对 $x$ 积分。** 分母都是区域面积，$\bar y$ 分子中的 $\frac12$ 来自 $\int y\,\mathrm dy=\frac12y^2$。

也可取竖直小条理解：小条面积为 $\mathrm dS=f(x)\,\mathrm dx$，其形心坐标为 $(x,f(x)/2)$，再按面积加权平均，即得到上述两式。

### 平面曲线的弧长

以下曲线设为光滑或分段光滑，分段光滑时将各段弧长相加。参数或极角区间应将所求曲线描绘一次；若重复描绘，积分会累计重复经过的长度。

#### 弧长微元：从勾股关系出发

对曲线上的微小位移，弧长微元满足

$$
\boxed{\mathrm ds=\sqrt{(\mathrm dx)^2+(\mathrm dy)^2}}.
$$

这里表示微元关系；一段有限曲线的弧长通常不等于两端点间的直线距离。

#### 直角坐标方程 $y=y(x)$

设 $a\le x\le b$，由 $\mathrm dy=y'(x)\,\mathrm dx$，有

$$
\begin{aligned}
\mathrm ds
&=\sqrt{(\mathrm dx)^2+[y'(x)\,\mathrm dx]^2}\\
&=\sqrt{1+[y'(x)]^2}\,|\mathrm dx|.
\end{aligned}
$$

按 $x$ 从 $a$ 到 $b$ 递增积分，得到

$$
\boxed{s=\int_a^b\sqrt{1+[y'(x)]^2}\,\mathrm dx}.
$$

#### 参数方程 $x=x(t),\ y=y(t)$

设 $\alpha\le t\le\beta$，由

$$
\mathrm dx=x'(t)\,\mathrm dt,\qquad
\mathrm dy=y'(t)\,\mathrm dt,
$$

代入弧长微元得

$$
\begin{aligned}
\mathrm ds
&=\sqrt{[x'(t)\,\mathrm dt]^2+[y'(t)\,\mathrm dt]^2}\\
&=\sqrt{[x'(t)]^2+[y'(t)]^2}\,|\mathrm dt|.
\end{aligned}
$$

按参数递增积分，得到

$$
\boxed{s=\int_\alpha^\beta\sqrt{[x'(t)]^2+[y'(t)]^2}\,\mathrm dt}.
$$

#### 极坐标方程 $r=r(\theta)$

设 $\alpha\le\theta\le\beta$，先转成以 $\theta$ 为参数的方程：

$$
x=r(\theta)\cos\theta,\qquad y=r(\theta)\sin\theta.
$$

分别求导：

$$
\frac{\mathrm dx}{\mathrm d\theta}=r'(\theta)\cos\theta-r(\theta)\sin\theta,
\qquad
\frac{\mathrm dy}{\mathrm d\theta}=r'(\theta)\sin\theta+r(\theta)\cos\theta.
$$

平方相加时交叉项抵消，利用 $\sin^2\theta+\cos^2\theta=1$，得到

$$
\begin{aligned}
\left(\frac{\mathrm dx}{\mathrm d\theta}\right)^2
+\left(\frac{\mathrm dy}{\mathrm d\theta}\right)^2
&=(r'\cos\theta-r\sin\theta)^2+(r'\sin\theta+r\cos\theta)^2\\
&=(r')^2(\cos^2\theta+\sin^2\theta)+r^2(\sin^2\theta+\cos^2\theta)\\
&=(r')^2+r^2.
\end{aligned}
$$

因此

$$
\mathrm ds=\sqrt{r^2(\theta)+[r'(\theta)]^2}\,|\mathrm d\theta|,
\qquad
\boxed{s=\int_\alpha^\beta\sqrt{r^2(\theta)+[r'(\theta)]^2}\,\mathrm d\theta}.
$$

**记忆：直角坐标是 $\sqrt{1+(y')^2}$，参数方程是 $\sqrt{(x')^2+(y')^2}$，极坐标是 $\sqrt{r^2+(r')^2}$。** 各导数必须对当前积分变量求导；极坐标弧长公式没有面积公式中的 $\frac12$。

### 旋转曲面的面积（侧面积）

设平面曲线光滑或分段光滑，绕 $x$ 轴旋转一周。以下按所求曲面不重复覆盖的情形计算；分段光滑时，各段面积相加。这里只计算曲线旋转形成的**侧面积** ，不额外加入端面圆盘的面积。

#### 核心微元公式

曲线上一点到 $x$ 轴的距离为 $|y|$，因此

$$
\boxed{\mathrm dS=2\pi|y|\,\mathrm ds},
\qquad
\boxed{S=\int_L2\pi|y|\,\mathrm ds}.
$$

**记忆：在弧长微元 $\mathrm ds$ 上，乘“旋转一周的圆周长”$2\pi|y|$。** 半径取到旋转轴的距离，所以需要绝对值；$\mathrm ds$ 是曲线弧长微元，不能直接换成 $\mathrm dx$。

#### ① 直角坐标：$y=f(x)$，$a\le x\le b$

由 $\mathrm ds=\sqrt{1+[f'(x)]^2}\,\mathrm dx$，得

$$
\boxed{S=2\pi\int_a^b|f(x)|\sqrt{1+[f'(x)]^2}\,\mathrm dx}.
$$

相对于直角坐标弧长公式，被积函数多乘了 $2\pi|f(x)|$。

#### ② 参数方程：$x=x(t),\ y=y(t)$，$\alpha\le t\le\beta$

参数区间应将所求曲线描绘一次。由参数方程的弧长微元，得

$$
\boxed{S=2\pi\int_\alpha^\beta|y(t)|
\sqrt{[x'(t)]^2+[y'(t)]^2}\,\mathrm dt}.
$$

图片中 $x'(t)\ne0$ 是采用 $x$ 作中间变量的充分条件；直接使用上述弧长微元时，只需满足相应的光滑、正则和不重复覆盖条件。

#### ③ 极坐标：$r=r(\theta)$，$\alpha\le\theta\le\beta$

因 $y=r(\theta)\sin\theta$，到 $x$ 轴的距离为 $|r(\theta)\sin\theta|$，所以

$$
\boxed{S=2\pi\int_\alpha^\beta|r(\theta)\sin\theta|
\sqrt{r^2(\theta)+[r'(\theta)]^2}\,\mathrm d\theta}.
$$

**极坐标中，绕 $x$ 轴旋转的半径是 $|r\sin\theta|$，不是单独的 $|r|$。** $\sqrt{r^2+(r')^2}$ 来自弧长公式，不能漏掉 $r'$。

三种形式都来自同一关系：**侧面积 = 沿曲线累加“圆周长 × 弧长微元”** 。如果改为绕 $y$ 轴旋转，半径改为 $|x|$，即 $\mathrm dS=2\pi|x|\,\mathrm ds$。

## <span style="color: #3498db;">第四部分：多元函数微分学</span>

### 二重极限的判断：直线、幂曲线与极坐标

以下讨论 $(x,y)\to(0,0)$；趋于其他点时，可先平移坐标。所选路径须在函数定义域内趋近目标点。

**思路：先取 $y=kx$，再按次数取 $y=kx^p$；若未发现不同结果，再用夹逼或极坐标证明。**

1. **先沿直线试探：** 令 $y=kx$，其中 $k$ 为固定常数，并补查竖直路径 $x=0$。若沿不同路径得到不同极限，或沿某条路径极限不存在，则二重极限不存在。这里“与 $k$ 有关”指**求出的极限值** 随 $k$ 改变，代入后的表达式含 $k$ 本身不能说明问题。
2. **再沿幂曲线试探：** 若直线路径的极限均相同，再根据分子、分母中关键项的次数，选取 $y=kx^p$（$p>0$），使关键项同阶。例如要使 $x^m$ 与 $y^n$ 同阶，可取 $p=m/n$。若 $p$ 非整数，须选使幂有实数意义的趋近范围，如 $x\to0^+$。
3. **最后证明存在：** 若所检查的路径结果始终相同，只能得到候选极限 $L$，仍须证明任意趋近方式下均趋于 $L$。常用夹逼法，或令 $x=r\cos\theta,\ y=r\sin\theta$，找到与 $\theta$ 无关的上界：

$$
\left|f(r\cos\theta,r\sin\theta)-L\right|
\le\varphi(r),\qquad\varphi(r)\to0\quad(r\to0^+).
$$

这里估计须对定义域内所有允许的 $\theta$ 同时成立；**只固定 $\theta$ 再令 $r\to0$，仍然只是沿射线检查。**

#### 例：所有直线路径极限相同，二重极限仍可能不存在

设

$$
f(x,y)=\frac{x^2y}{x^4+y^2},\qquad(x,y)\ne(0,0).
$$

沿任意直线 $y=kx$，

$$
f(x,kx)=\frac{kx}{x^2+k^2}\longrightarrow0;
$$

沿 $x=0$ 也恒为 $0$。但分母中 $x^4$ 与 $y^2$ 在 $y=kx^2$ 时同阶，此时

$$
f(x,kx^2)=\frac{k}{1+k^2}.
$$

取 $k=0$ 与 $k=1$，分别得到 $0$ 与 $1/2$，故二重极限不存在。

**记忆：两条路径结果不同即可否定；所有已检查路径结果相同，仍须证明。**

### 全增量、可微与全微分

设 $z=f(x,y)$ 在点 $(x_0,y_0)$ 的某邻域内有定义，记

$$
\Delta z=f(x_0+\Delta x,y_0+\Delta y)-f(x_0,y_0),
\qquad \rho=\sqrt{(\Delta x)^2+(\Delta y)^2}.
$$

若存在只与点 $(x_0,y_0)$ 有关、与 $\Delta x,\Delta y$ 无关的常数 $A,B$，使

$$
\boxed{\Delta z=A\Delta x+B\Delta y+o(\rho)
\qquad(\rho\to0)},
$$

则称 $f$ 在该点**可微** 。其中 $o(\rho)/\rho\to0$，线性部分称为**全微分** ：

$$
\mathrm dz=A\Delta x+B\Delta y=A\,\mathrm dx+B\,\mathrm dy,
\qquad \mathrm dx=\Delta x,\quad \mathrm dy=\Delta y.
$$

**可微时，两个偏导数必存在，且 $A=f_x(x_0,y_0)$、$B=f_y(x_0,y_0)$。** 因此

$$
\boxed{\mathrm dz=f_x(x_0,y_0)\,\mathrm dx+f_y(x_0,y_0)\,\mathrm dy}.
$$

全微分是全增量的线性主要部分，两者之差是 $\rho$ 的高阶无穷小。例如 $z=xy$ 时，

$$
\Delta z=y\Delta x+x\Delta y+\Delta x\Delta y,
\qquad \mathrm dz=y\,\mathrm dx+x\,\mathrm dy.
$$

因为 $|\Delta x\Delta y|\le\rho^2/2$，所以 $\Delta x\Delta y=o(\rho)$。

### 可微的必要条件、充分条件与判别步骤

**必要条件：** 在一点可微 $\Rightarrow$ 在该点连续，且两个偏导数均存在。**仅有偏导数存在，不能保证可微。**

**充分条件：** 若 $f_x,f_y$ 在 $(x_0,y_0)$ 的某邻域内存在，且都在 $(x_0,y_0)$ 连续，则 $f$ 在该点可微。这里“偏导数在该点连续”指

$$
\lim_{(x,y)\to(x_0,y_0)}f_x(x,y)=f_x(x_0,y_0),
\qquad
\lim_{(x,y)\to(x_0,y_0)}f_y(x,y)=f_y(x_0,y_0).
$$

偏导数连续是可微的充分条件，**不是必要条件** ；偏导数在该点不连续时，还须另行判断可微性。

按定义判断可微的步骤：

1. 写出全增量 $\Delta z=f(x_0+\Delta x,y_0+\Delta y)-f(x_0,y_0)$。
2. 求出 $A=f_x(x_0,y_0)$、$B=f_y(x_0,y_0)$，写出线性部分 $A\Delta x+B\Delta y$；若某个偏导数不存在，则不可微。
3. 计算二重极限

$$
\boxed{\lim_{(\Delta x,\Delta y)\to(0,0)}
\frac{\Delta z-f_x(x_0,y_0)\Delta x-f_y(x_0,y_0)\Delta y}
{\sqrt{(\Delta x)^2+(\Delta y)^2}}}.
$$

极限为 $0$ 时可微；极限非零或不存在时不可微。

**判断偏导数在一点是否连续：** 先按定义求出该点的偏导数，再求邻近点的偏导函数，最后比较偏导函数的二重极限与该点的偏导数值。分段函数在分界点的偏导数尤其要按定义计算。

### 一元函数与多元函数的性质关系

以下均讨论同一点的性质；“偏导数存在、连续”指两个偏导数都满足相应条件。

| 关系           | 一元函数                                    | 二元函数                                      |
| -------------- | ------------------------------------------- | --------------------------------------------- |
| 可导与可微     | 可导 $\iff$ 可微                            | 可微 $\Rightarrow$ 偏导数存在，反向不一定成立 |
| 可微与连续     | 可微 $\Rightarrow$ 连续，反向不一定成立     | 可微 $\Rightarrow$ 连续，反向不一定成立       |
| 导数存在与连续 | 可导 $\Rightarrow$ 连续                     | 偏导数存在与函数连续，互相都不能保证          |
| 导数连续与可微 | 导数连续 $\Rightarrow$ 可微，反向不一定成立 | 偏导数连续 $\Rightarrow$ 可微，反向不一定成立 |
| 连续与极限     | 连续 $\Rightarrow$ 极限存在                 | 连续 $\Rightarrow$ 二重极限存在               |

**多元函数常用推导链：**

$$
\boxed{\text{偏导数连续}\ \Rightarrow\ \text{可微}\ \Rightarrow\ \text{连续}\ \Rightarrow\ \text{二重极限存在}},
$$

$$
\boxed{\text{可微}\ \Rightarrow\ \text{偏导数存在}}.
$$

上面的“偏导数连续 $\Rightarrow$ 可微”采用前述邻域内偏导数存在的假设。**二重极限存在还不够，极限必须等于该点函数值，函数才在该点连续：**

$$
f\text{ 在 }(x_0,y_0)\text{ 连续}
\iff \lim_{(x,y)\to(x_0,y_0)}f(x,y)=f(x_0,y_0).
$$

### 区域内全微分恒为零

设 $f$ 在连通开区域 $D$ 内可微，则

$$
\boxed{\mathrm df\equiv0
\iff f_x\equiv f_y\equiv0
\iff f(x,y)\equiv C\quad((x,y)\in D)}.
$$

这里 $\mathrm df\equiv0$ 指对任意 $\mathrm dx,\mathrm dy$，全微分都为零。若定义域不连通，各连通分支上的常数可以不同。

### 复合函数求导与“位置”记号

对二元函数 $f(u,v)$，$f'_1$ 表示对**第一个位置** 求偏导，$f'_2$ 表示对**第二个位置** 求偏导：

$$
f'_1(u,v)=\frac{\partial f}{\partial u}(u,v),
\qquad
f'_2(u,v)=\frac{\partial f}{\partial v}(u,v).
$$

位置由参数的排列决定，与内函数叫什么、怎样依赖 $x,y$ 无关。若 $z=f(u(x,y),v(x,y))$，在相应可微条件下，

$$
\boxed{
\begin{aligned}
\frac{\partial z}{\partial x}&=f'_1(u,v)u_x+f'_2(u,v)v_x,\\
\frac{\partial z}{\partial y}&=f'_1(u,v)u_y+f'_2(u,v)v_y
\end{aligned}
}.
$$

求二阶偏导数时，既要对内函数的系数求导，也要对 $f'_1,f'_2$ 再用链式法则。例如在二阶连续可导时，

$$
\begin{aligned}
z_{xy}
={}&f''_{11}u_xu_y+f''_{12}u_xv_y\\
&+f''_{21}v_xu_y+f''_{22}v_xv_y\\
&+f'_1u_{xy}+f'_2v_{xy},
\end{aligned}
$$

其中所有 $f$ 的偏导数均在 $(u(x,y),v(x,y))$ 处取值。

#### 先求偏导再代入，与代入后求导

令 $g(x)=f(x,\varphi(x))$，则在相应可微条件下

$$
\boxed{g'(x)=f'_1(x,\varphi(x))+f'_2(x,\varphi(x))\varphi'(x)}.
$$

而

$$
\left.f_x(x,y)\right|_{y=\varphi(x)}=f'_1(x,\varphi(x)),
\qquad
\left.f_y(x,y)\right|_{y=\varphi(x)}=f'_2(x,\varphi(x)).
$$

**竖线表示先求偏导，再代入；若先代入 $y=\varphi(x)$，得到的是一元复合函数，求导时须计入第二个位置随 $x$ 的变化。** 只知道 $f(x,\varphi(x))$，通常也只能确定 $f$ 在这条曲线上的值，不能据此确定整个二元函数。

### 隐函数求导公式

以下假设 $F$ 在所讨论点的某邻域内具有连续一阶偏导数，各偏导数均在隐函数对应的点处取值。

#### 一元隐函数：$F(x,y)=0$

由方程 $F(x,y)=0$ 确定隐函数 $y=f(x)$，当 $F_y(x,y)\ne0$ 时，

$$
\boxed{\frac{\mathrm dy}{\mathrm dx}=-\frac{F_x(x,y)}{F_y(x,y)}}.
$$

对恒等式 $F(x,f(x))=0$ 求导，得到 $F_x+F_y\,y'=0$，移项即得上式。

#### 二元隐函数：$F(x,y,z)=0$

由方程 $F(x,y,z)=0$ 确定隐函数 $z=f(x,y)$，当 $F_z(x,y,z)\ne0$ 时，

$$
\boxed{
\frac{\partial z}{\partial x}=-\frac{F_x(x,y,z)}{F_z(x,y,z)},
\qquad
\frac{\partial z}{\partial y}=-\frac{F_y(x,y,z)}{F_z(x,y,z)}
}.
$$

**记忆：分母对因变量求偏导，分子对所求的自变量求偏导，前面加负号；分母必须非零。**

### 二元函数的无条件极值

以下讨论定义域的内点 $(x_0,y_0)$，极值允许为非严格极值：在某邻域内，$f(x,y)\ge f(x_0,y_0)$ 为极小值，$f(x,y)\le f(x_0,y_0)$ 为极大值。

#### 必要条件与可疑点

若 $f$ 在 $(x_0,y_0)$ 处的一阶偏导数存在，且在该点取得极值，则

$$
\boxed{f_x(x_0,y_0)=0,\qquad f_y(x_0,y_0)=0}.
$$

两偏导数均为零的点称为**驻点** 。驻点不一定是极值点，如 $f(x,y)=x^2-y^2$ 的原点。

**极值可疑点包括驻点和至少一个一阶偏导数不存在的点。** 偏导数不存在的点也可能取得极值，如 $f(x,y)=\sqrt{x^2+y^2}$ 在原点取得严格极小值，$f(x,y)=|x+y|$ 在原点取得非严格极小值。必要条件同样适用于三元及更多元函数：各一阶偏导数存在时，极值点处均为零。

#### 二阶偏导数判别法（充分条件）

设 $f$ 在 $(x_0,y_0)$ 的某邻域内具有二阶连续偏导数，且该点为驻点。记

$$
A=f_{xx}(x_0,y_0),\qquad B=f_{xy}(x_0,y_0),\qquad
C=f_{yy}(x_0,y_0),\qquad \Delta=AC-B^2.
$$

| 条件              | 结论                             |
| ----------------- | -------------------------------- |
| $\Delta>0$，$A>0$ | 严格极小值点                     |
| $\Delta>0$，$A<0$ | 严格极大值点                     |
| $\Delta<0$        | 非极值点（鞍点）                 |
| $\Delta=0$        | 判别法失效，须另用定义或其他方法 |

**记忆：先找驻点，再算 $AC-B^2$；正看 $A$，负无极值，零另判断。** 这一判别表针对二元函数，不能直接照搬到三元及更多元函数。

若 $\Delta=0$，极小、极大、非极值均可能出现，例如原点处的 $x^4+y^4$、$-x^4-y^4$、$x^4-y^4$。沿不同路径出现大于和小于该点函数值的情况，可排除极值；只验证有限条路径不能证明极值。

## <span style="color: #3498db;">第五部分：重积分</span>

### 被积函数为 1：二重积分等于区域面积

设 $D$ 为有界闭区域，面积为 $A$，则

$$
\boxed{\iint_D1\,\mathrm d\sigma=\iint_D1\,\mathrm dx\,\mathrm dy=A},
\qquad \mathrm d\sigma=\mathrm dx\,\mathrm dy.
$$

**记忆：被积函数为 $1$ 时，二重积分就是积分区域的面积。** 更一般地，对常数 $c$，有 $\iint_Dc\,\mathrm d\sigma=cA$。

### 二重积分的保序性与保号性

设 $f(x,y),g(x,y)$ 在 $D$ 上可积。若在 $D$ 上恒有

$$
f(x,y)\le g(x,y),
$$

则

$$
\boxed{\iint_Df(x,y)\,\mathrm d\sigma
\le\iint_Dg(x,y)\,\mathrm d\sigma}.
$$

**记忆：同一区域上，被积函数之间的大小关系在积分后仍保持。** 特别地，$f\ge0$ 时 $\iint_Df\,\mathrm d\sigma\ge0$；$f\le0$ 时 $\iint_Df\,\mathrm d\sigma\le0$。

#### 绝对值不等式

由 $-|f(x,y)|\le f(x,y)\le|f(x,y)|$，得

$$
\boxed{\left|\iint_Df(x,y)\,\mathrm d\sigma\right|
\le\iint_D|f(x,y)|\,\mathrm d\sigma}.
$$

### 二重积分的估值定理

设 $f(x,y)$ 在 $D$ 上可积，且

$$
m\le f(x,y)\le M,\qquad (x,y)\in D,
$$

则

$$
\boxed{mA\le\iint_Df(x,y)\,\mathrm d\sigma\le MA}.
$$

其中 $m,M$ 可取 $f$ 在 $D$ 上的最小值、最大值，也可取任意满足上述条件的下界、上界。该结论由保序性及常数的积分 $\iint_Dc\,\mathrm d\sigma=cA$ 得到。

**记忆：最小值乘面积不超过积分，积分不超过最大值乘面积。** 当 $A>0$ 时，积分平均值满足

$$
m\le\frac1A\iint_Df(x,y)\,\mathrm d\sigma\le M.
$$

### 二重积分的中值定理

设 $f(x,y)$ 在有界闭区域 $D$ 上连续，$D$ 连通，且面积 $A>0$，则在 $D$ 上至少存在一点 $(\xi,\eta)$，使得

$$
\boxed{\iint_Df(x,y)\,\mathrm d\sigma=f(\xi,\eta)A}.
$$

即区域上的积分平均值等于函数在区域内某一点的函数值：

$$
\frac1A\iint_Df(x,y)\,\mathrm d\sigma=f(\xi,\eta).
$$

**记忆：二重积分＝某点的函数值×区域面积。** 这与一元积分中值定理

$$
\int_a^bf(x)\,\mathrm dx=f(\xi)(b-a),\qquad \xi\in(a,b),
$$

形式对应：一元积分中的区间长度 $b-a$，在二重积分中换成区域面积 $A$。二重积分中的中值点满足 $(\xi,\eta)\in D$，不能预先指定为区域中心。

### 二重积分的对称性

设 $f(x,y)$ 在 $D$ 上可积。使用下列公式时，须先确认**积分区域关于相应的轴、直线或点对称** ，再比较两个对称点处的函数值。

**记忆：对称点处函数值相同，取对称的一半区域积分后乘 $2$；函数值相反，积分为 $0$。** 以下各式中的 $D_1$ 均按相应的对称方式选取。

#### ① 关于 y 轴对称

对称点为 $(x,y)$ 与 $(-x,y)$，取右半部分 $D_1=D\cap\{x\ge0\}$，则

$$
\boxed{
\iint_Df(x,y)\,\mathrm d\sigma=
\begin{cases}
2\displaystyle\iint_{D_1}f(x,y)\,\mathrm d\sigma,
& f(x,y)=f(-x,y),\\[4pt]
0, & f(x,y)=-f(-x,y).
\end{cases}}
$$

此时固定 $y$、只改变 $x$ 的符号，即判断 $f$ 关于 $x$ 的奇偶性。

#### 补充：关于直线 x = a 对称

对称点为 $(x,y)$ 与 $(2a-x,y)$，取直线右侧部分 $D_1=D\cap\{x\ge a\}$，则

$$
\boxed{
\iint_Df(x,y)\,\mathrm d\sigma=
\begin{cases}
2\displaystyle\iint_{D_1}f(x,y)\,\mathrm d\sigma,
& f(x,y)=f(2a-x,y),\\[4pt]
0, & f(x,y)=-f(2a-x,y).
\end{cases}}
$$

取 $a=0$ 就得到关于 $y$ 轴对称的情形。例如，$D$ 关于 $x=a$ 对称时，$\iint_D(x-a)\,\mathrm d\sigma=0$。

#### ② 关于 x 轴对称

对称点为 $(x,y)$ 与 $(x,-y)$，取上半部分 $D_1=D\cap\{y\ge0\}$，则

$$
\boxed{
\iint_Df(x,y)\,\mathrm d\sigma=
\begin{cases}
2\displaystyle\iint_{D_1}f(x,y)\,\mathrm d\sigma,
& f(x,y)=f(x,-y),\\[4pt]
0, & f(x,y)=-f(x,-y).
\end{cases}}
$$

此时固定 $x$、只改变 $y$ 的符号，即判断 $f$ 关于 $y$ 的奇偶性。

#### 补充：关于直线 y = a 对称

对称点为 $(x,y)$ 与 $(x,2a-y)$，取直线上侧部分 $D_1=D\cap\{y\ge a\}$，则

$$
\boxed{
\iint_Df(x,y)\,\mathrm d\sigma=
\begin{cases}
2\displaystyle\iint_{D_1}f(x,y)\,\mathrm d\sigma,
& f(x,y)=f(x,2a-y),\\[4pt]
0, & f(x,y)=-f(x,2a-y).
\end{cases}}
$$

取 $a=0$ 就得到关于 $x$ 轴对称的情形。

#### ③ 关于原点对称

对称点为 $(x,y)$ 与 $(-x,-y)$。可取上半部分 $D_1=D\cap\{y\ge0\}$，则

$$
\boxed{
\iint_Df(x,y)\,\mathrm d\sigma=
\begin{cases}
2\displaystyle\iint_{D_1}f(x,y)\,\mathrm d\sigma,
& f(x,y)=f(-x,-y),\\[4pt]
0, & f(x,y)=-f(-x,-y).
\end{cases}}
$$

**关于原点对称时，要同时将 $x,y$ 变号。** $D_1$ 应与其关于原点的对称部分拼成 $D$，不能任意选取一个面积为 $D$ 一半的子区域。

#### ④ 关于直线 y = x 对称

对称点为 $(x,y)$ 与 $(y,x)$，即交换 $x,y$。可取直线上侧部分 $D_1=D\cap\{y\ge x\}$，则

$$
\boxed{
\iint_Df(x,y)\,\mathrm d\sigma=
\begin{cases}
2\displaystyle\iint_{D_1}f(x,y)\,\mathrm d\sigma,
& f(x,y)=f(y,x),\\[4pt]
0, & f(x,y)=-f(y,x).
\end{cases}}
$$

**使用顺序：先看区域是否对称，再写出对称点，最后判断函数值相同还是相反。** 仅有区域对称，不能直接把积分写成一半区域积分的 $2$ 倍；还必须满足相应的函数值相等条件。

### 二重积分的轮换对称性（交换 x、y）

设 $D$ 关于直线 $y=x$ 对称，即交换 $x,y$ 后区域不变，且 $f$ 在 $D$ 上可积，则

$$
\boxed{\iint_Df(x,y)\,\mathrm d\sigma
=\iint_Df(y,x)\,\mathrm d\sigma}.
$$

**轮换对称性只要求区域在交换 $x,y$ 后不变，不要求 $f(x,y)=f(y,x)$。** 交换后得到的两个被积函数可以不同，但在同一区域上的积分相等。常见适用区域有圆盘 $x^2+y^2\le R^2$、正方形 $[a,b]\times[a,b]$、三角形 $x\ge0,\ y\ge0,\ x+y\le a$（$a>0$）。

#### 常用方法：交换后相加，再除以 2

记 $I=\iint_Df(x,y)\,\mathrm d\sigma$，则

$$
2I=\iint_D\bigl[f(x,y)+f(y,x)\bigr]\,\mathrm d\sigma,
$$

因此

$$
\boxed{I=\frac12\iint_D\bigl[f(x,y)+f(y,x)\bigr]\,\mathrm d\sigma}.
$$

若交换后的两项之和为常数 $C$，即 $f(x,y)+f(y,x)=C$，则

$$
\boxed{\iint_Df(x,y)\,\mathrm d\sigma=\frac C2A}.
$$

**记忆：区域不变，交换变量；两式相加，凑成简单函数。** 这里仍在整个 $D$ 上积分，与“取一半区域再乘 $2$”的公式分别使用。

### 二重积分的一般换元公式与雅可比行列式

作变量替换

$$
\begin{cases}
x=x(u,v),\\
y=y(u,v),
\end{cases}
$$

把 $uv$ 平面上的区域 $D'$ 映射到 $xy$ 平面上的积分区域 $D$。设变换在区域内部一一对应，具有一阶连续偏导数，且雅可比行列式非零，则在被积函数满足相应可积条件时，有

$$
\boxed{
\iint_D f(x,y)\,\mathrm dx\,\mathrm dy
=\iint_{D'}f\bigl(x(u,v),y(u,v)\bigr)
\left|\frac{\partial(x,y)}{\partial(u,v)}\right|
\,\mathrm du\,\mathrm dv
}.
$$

其中，**雅可比行列式（换元行列式）** 为

$$
\boxed{
\frac{\partial(x,y)}{\partial(u,v)}
=\begin{vmatrix}
\dfrac{\partial x}{\partial u}&\dfrac{\partial x}{\partial v}\\[5pt]
\dfrac{\partial y}{\partial u}&\dfrac{\partial y}{\partial v}
\end{vmatrix}
=x_u y_v-x_v y_u
}.
$$

#### 换元时三处一起换

1. **被积函数：** $f(x,y)\longrightarrow f\bigl(x(u,v),y(u,v)\bigr)$。
2. **积分区域：** $D\longrightarrow D'$，把原区域的边界、约束条件改写为 $u,v$ 的条件。
3. **面积微元：**

$$
\boxed{\mathrm dx\,\mathrm dy
=\left|\frac{\partial(x,y)}{\partial(u,v)}\right|
\,\mathrm du\,\mathrm dv}.
$$

**记忆：函数换、区域换、微元乘雅可比的绝对值。** 行列式本身可能为负，面积缩放因子要取绝对值。

雅可比的方向要与微元一致：从 $\mathrm dx\,\mathrm dy$ 换成 $\mathrm du\,\mathrm dv$，使用的是 $\partial(x,y)/\partial(u,v)$。若先算出了逆变换的雅可比，则在对应点、行列式非零时有

$$
\boxed{\left|\frac{\partial(x,y)}{\partial(u,v)}\right|
=\frac1{\left|\dfrac{\partial(u,v)}{\partial(x,y)}\right|}}.
$$

### 二重积分的极坐标换元

令

$$
\boxed{x=r\cos\theta,\qquad y=r\sin\theta},\qquad r\ge0.
$$

相应的雅可比行列式为

$$
\frac{\partial(x,y)}{\partial(r,\theta)}
=\begin{vmatrix}
\cos\theta&-r\sin\theta\\
\sin\theta&r\cos\theta
\end{vmatrix}
=r.
$$

因此，面积微元与积分公式分别为

$$
\boxed{\mathrm dx\,\mathrm dy=r\,\mathrm dr\,\mathrm d\theta},
$$

$$
\boxed{\iint_D f(x,y)\,\mathrm dx\,\mathrm dy
=\iint_{D'}f(r\cos\theta,r\sin\theta)\,r\,\mathrm dr\,\mathrm d\theta}.
$$

若新区域为 $\alpha\le\theta\le\beta$、$r_1(\theta)\le r\le r_2(\theta)$，则可写成

$$
\boxed{\iint_D f(x,y)\,\mathrm dx\,\mathrm dy
=\int_\alpha^\beta\mathrm d\theta
\int_{r_1(\theta)}^{r_2(\theta)}
f(r\cos\theta,r\sin\theta)\,r\,\mathrm dr}.
$$

**记忆：换成极坐标后，被积函数代入 $x=r\cos\theta,y=r\sin\theta$，面积微元还要额外乘 $r$。** 其中 $x^2+y^2=r^2$；角度范围及径向上下限由原积分区域确定。

极坐标在原点处雅可比为 $0$，选取角度区间的两端也可能对应同一条射线；这些边界上的重复或退化不影响通常的二重积分换元，但区域内部应避免重复覆盖。

## <span style="color: #3498db;">第六部分：微分方程</span>

### 考试选法：先看阶数，再看结构

**拿到题先看最高阶导数，再看能否分离变量、是否线性、系数是否为常数、是否缺少某个变量。** 初始条件一般在求出解的形式后使用，用来确定常数、分支和解所在区间。

#### 一阶方程怎么选

按下面的顺序尝试，哪种结构明显就优先用哪种；同一道题可能有不止一种解法。

1. **能否直接分离变量？** 能写成 $y'=f(x)g(y)$，就把含 $y$ 的项和 $\mathrm dy$ 放一侧，含 $x$ 的项和 $\mathrm dx$ 放另一侧。
2. **右端是否只含 $y/x$？** 若为 $y'=\varphi(y/x)$，用齐次型换元 $u=y/x$。例如 $y'=1+(y/x)^2$。
3. **是否对未知函数及其导数线性？** 能写成 $y'+p(x)y=q(x)$，直接用一阶线性通解；其中 $p,q$ 只能依赖自变量 $x$。
4. **交换 x、y 后是否更简单？** 若能写成 $\mathrm dx/\mathrm dy+P(y)x=Q(y)$，就把 $x$ 当作 $y$ 的函数，套线性公式。例如 $y\,\mathrm dx+(x-3y^2)\,\mathrm dy=0$。
5. **是否只多了一个 $y^n$？** 若为 $y'+p(x)y=q(x)y^n$，用伯努利换元 $z=y^{1-n}$，再解线性方程。

若原题给成 $P\,\mathrm dx+Q\,\mathrm dy=0$，且 $P_y,Q_x$ 容易计算，也可先检查是否为全微分方程。**齐次型与一阶线性不是互斥类别；能用更短的方法就优先选更短的方法。**

#### 二阶及高阶方程怎么选

| 看到的结构                               | 选用方法             | 第一步                                                  |
| ---------------------------------------- | -------------------- | ------------------------------------------------------- |
| $y''=f(x)$                               | 直接积分两次         | 先求 $y'$，再求 $y$，保留两个常数                       |
| $y''=F(x,y')$，不显含 $y$                | 降阶                 | 令 $v(x)=y'$，用 $y''=v'$                               |
| $y''=F(y,y')$，不显含 $x$                | 降阶                 | 令 $v(y)=y'$，用 $y''=v\,\mathrm dv/\mathrm dy$         |
| $y''=F(y)$                               | 降阶后积分           | 先得 $(y')^2/2=\int F(y)\,\mathrm dy+C_1$               |
| $y''+py'+qy=0$，$p,q$ 为常数             | 常系数齐次线性方程   | 解特征方程 $r^2+pr+q=0$                                 |
| $y''+py'+qy=f(x)$，$p,q$ 为常数          | 齐次通解加非齐次特解 | 先求 $Y$，再按右端形式设 $y_p$                          |
| $x^2y''+pxy'+qy=f(x)$，$p,q$ 为常数      | 欧拉方程换元         | 令 $t=\ln\lvert x\rvert$；齐次时也可试 $y=x^r$（$x>0$） |
| 已知高阶常系数齐次方程的若干解，反求方程 | 由解识别特征根及重数 | 如 $x$ 对应 $0$ 至少为二重根                            |

若多个特征同时满足，例如 $y''=F(y')$ 既不显含 $x$ 又不显含 $y$，通常先令 $v(x)=y'$，直接解 $v'=F(v)$ 更方便。

#### 非齐次方程的特解怎么设

对 $y''+py'+qy=f(x)$，先求特征根，再看右端：

- **多项式：** 按 $e^{0x}P_n(x)$ 处理，设 $y_p=x^kQ_n(x)$，比较 $0$ 是否为特征根。
- **指数乘多项式：** $f(x)=e^{\alpha x}P_n(x)$，设 $y_p=x^ke^{\alpha x}Q_n(x)$，$k$ 为 $\alpha$ 的特征根重数，不是根则取 $0$。
- **指数乘正弦、余弦：** 比较 $\alpha\pm\beta i$ 与特征根，设 $y_p=x^ke^{\alpha x}[Q(x)\cos\beta x+R(x)\sin\beta x]$。
- **几类函数相加：** 分别求特解，再相加。

**记忆：看右端、算根、查重复；重复几次，补几个 $x$。** 多项式的低次项要写全，三角型的正弦、余弦两项通常都要设。

#### 考场上的易错检查

- **线性看未知函数：** $y'+xy=x^2$ 是线性方程；$y'+y^2=x$ 含 $y^2$，不属于一阶线性方程。
- **两个“齐次”分清：** $y'=\varphi(y/x)$ 是齐次型；$y'+p(x)y=0$ 是线性齐次方程，识别标准不同。
- **换元记清自变量：** $v=v(x)$ 时 $y''=v'$；$v=v(y)$ 时 $y''=v\,\mathrm dv/\mathrm dy$。
- **除法之后查丢解：** 除以 $y$、$y'$、$g(y)$ 等之前，先记录它们等于 $0$ 的情形。
- **最后再用初始条件：** 如得到 $y=\pm\sqrt{x}$，还须用给定点选择分支；对数、根式及 $x=0$ 等限制也要检查。

### 可分离变量方程与丢解检查

对于

$$
y'=f(x)g(y),
$$

在 $g(y)\ne0$ 的范围内可分离变量，写成

$$
\boxed{\int\frac{\mathrm dy}{g(y)}=\int f(x)\,\mathrm dx+C}.
$$

**除以含未知函数的因子时，要检查该因子为 $0$ 是否给出原方程的解。** 若 $g(a)=0$，则常值函数 $y\equiv a$ 也是原方程的解，分离变量时可能将它漏掉。

例如，分离变量时若除以 $1+\sin u$，就要另外检查 $\sin u=-1$ 的情况。**通解与全部解应按题目要求区分** ：求全部解时，应把计算中遗漏且确实满足原方程的解补回。

### 齐次型微分方程：令 u = y/x

形如

$$
\boxed{\frac{\mathrm dy}{\mathrm dx}=\varphi\!\left(\frac yx\right)}
$$

的方程称为齐次型微分方程。令

$$
u=\frac yx,\qquad y=xu,\qquad y'=u+xu',
$$

可化为可分离变量方程

$$
\boxed{x\frac{\mathrm du}{\mathrm dx}=\varphi(u)-u}.
$$

在 $x\ne0$、$\varphi(u)-u\ne0$ 时，有

$$
\boxed{\int\frac{\mathrm du}{\varphi(u)-u}=\ln|x|+C}.
$$

最后代回 $u=y/x$。若 $\varphi(k)=k$，还应检查直线解 $y=kx$，避免因除以 $\varphi(u)-u$ 而丢解。

**“齐次型”指右端只依赖 $y/x$，与线性方程中右端为 $0$ 的“齐次”是不同的分类概念。**

### 一阶线性微分方程的通解

形如

$$
\boxed{y'+p(x)y=q(x)}
$$

的方程称为**一阶线性微分方程** 。设 $p(x),q(x)$ 在所讨论的区间上连续，则其通解为

$$
\boxed{
y=e^{-\int p(x)\,\mathrm dx}
\left[\int e^{\int p(x)\,\mathrm dx}q(x)\,\mathrm dx+C\right]
}.
$$

其中 $C$ 为任意常数。为避免嵌套积分中的常数混淆，可先固定 $p(x)$ 的一个原函数 $P(x)$，即 $P'(x)=p(x)$，写成

$$
\boxed{y=e^{-P(x)}\left[\int e^{P(x)}q(x)\,\mathrm dx+C\right]}.
$$

**记忆：先化标准形，外乘负指数，内积正指数乘右端，最后加常数。** 外面的 $e^{-P(x)}$ 要乘整个方括号，包括常数 $C$。

#### 当 p(x) 的积分为 ln|φ(x)| 时，可去掉通解中的绝对值

若可取

$$
P(x)=\int p(x)\,\mathrm dx=\ln|\varphi(x)|,
$$

且 $\varphi(x)$ 在所讨论的区间上连续、非零，则通解可直接写为

$$
\boxed{y=\frac1{\varphi(x)}
\left[\int\varphi(x)q(x)\,\mathrm dx+C\right]}.
$$

**记忆：积分得 $\ln|\varphi(x)|$，套通解时内乘 $\varphi(x)$、外除 $\varphi(x)$，可以不加绝对值。** 在该区间上 $\varphi(x)$ 的符号不变，$|\varphi(x)|$ 与 $\varphi(x)$ 只差一个固定的正负号，整体替换后可通过任意常数 $C$ 统一表示。

注意，指数恒等式仍是 $e^{\ln|\varphi(x)|}=|\varphi(x)|$；这里省略绝对值，是利用通解的等价表示，内、外两处应一起处理。

例如，$p(x)=1/x$ 时，$P(x)=\ln|x|$，于是

$$
\boxed{y=\frac1x\left[\int xq(x)\,\mathrm dx+C\right]},
\qquad x>0\text{ 或 }x<0.
$$

公式分别在不跨过 $0$ 的区间上使用，两侧的任意常数可分别选取。

#### 使用时注意

- **先把 $y'$ 的系数化为 $1$，再识别 $p(x),q(x)$。** 对 $a(x)y'+b(x)y=c(x)$，须在 $a(x)\ne0$ 的区间上先除以 $a(x)$，此时 $p(x)=b(x)/a(x)$、$q(x)=c(x)/a(x)$。
- $p(x)$ 是标准形中 $y$ 的系数，须保留其正负号。例如 $y'-2y=x$ 中，$p(x)=-2$，积分因子为 $e^{-2x}$。
- 当 $q(x)\equiv0$ 时，方程为一阶线性齐次方程，通解简化为 $\boxed{y=Ce^{-\int p(x)\,\mathrm dx}}$。
- 选取 $P(x)$ 时不必另加任意常数；更换原函数只会改变常数的表示，最终统一写一个任意常数 $C$。

### 交换自变量与因变量：把 x 看成 y 的函数

若直接求 $y(x)$ 不方便，可尝试把 $x$ 看成 $y$ 的函数，整理为

$$
\frac{\mathrm dx}{\mathrm dy}+P(y)x=Q(y).
$$

这是关于 $x(y)$ 的一阶线性方程，其通解为

$$
\boxed{x=e^{-\int P(y)\,\mathrm dy}
\left[\int e^{\int P(y)\,\mathrm dy}Q(y)\,\mathrm dy+C\right]}.
$$

**先看交换后能否化为熟悉的类型，再决定以哪个变量为自变量。** 由隐式关系还原 $y(x)$ 时，初始条件既能确定常数，也能确定正、负分支；局部使用反函数时还应检查相应导数非零。

### 伯努利方程：令 z = y 的 1−n 次方

形如

$$
\boxed{y'+p(x)y=q(x)y^n},\qquad n\ne0,1,
$$

的方程称为伯努利方程。按图片中的分类，此内容标注为数学一；其他类别可把它作为换元方法参考。

在有关幂函数有定义且 $y\ne0$ 的范围内，令

$$
z=y^{1-n},\qquad z'=(1-n)y^{-n}y',
$$

原方程化为一阶线性方程

$$
\boxed{z'+(1-n)p(x)z=(1-n)q(x)}.
$$

**记忆：除以 $y^n$，令 $z=y^{1-n}$，线性方程两边的系数都乘 $1-n$。** 解出 $z$ 后再还原 $y$，并检查变形时是否遗漏 $y=0$ 等解。

$n=0$ 时原方程本来就是一阶线性方程；$n=1$ 时可整理为 $y'+[p(x)-q(x)]y=0$。

### 二阶可降阶微分方程

以下各式均在相应函数有定义的区间内使用。按图片中的分类，这类内容标注为数学一、数学二。

#### 不显含 y：y″ = F(x, y′)

令 $v(x)=y'(x)$，则

$$
\boxed{\frac{\mathrm dv}{\mathrm dx}=F(x,v)}.
$$

先解一阶方程得到 $v=\psi(x,C_1)$，再积分：

$$
\boxed{y=\int\psi(x,C_1)\,\mathrm dx+C_2}.
$$

#### 不显含 x：y″ = F(y, y′)

在可局部以 $y$ 为自变量的范围内，令 $v(y)=y'$，使用

$$
\boxed{y''=\frac{\mathrm dv}{\mathrm dx}
=\frac{\mathrm dv}{\mathrm dy}\frac{\mathrm dy}{\mathrm dx}
=v\frac{\mathrm dv}{\mathrm dy}}.
$$

于是方程降阶为

$$
\boxed{v\frac{\mathrm dv}{\mathrm dy}=F(y,v)}.
$$

解出 $v=\psi(y,C_1)$ 后，再解 $y'=\psi(y,C_1)$。若继续分离变量，需检查除以 $v$ 或 $\psi$ 是否漏掉常值解。

**同样是令 $v=y'$：以 $x$ 为自变量时，$y''=\mathrm dv/\mathrm dx$；以 $y$ 为自变量时，$y''=v\,\mathrm dv/\mathrm dy$，不能漏掉因子 $v$。**

#### 特例：y″ = F(y)

可先降阶积分为

$$
\boxed{\frac12(y')^2=\int F(y)\,\mathrm dy+C_1},
$$

再依据初始条件和所讨论的区间选择 $y'$ 的分支，求解一阶方程。

### 全微分方程（恰当方程）

设 $P(x,y),Q(x,y)$ 在单连通开区域 $D$ 上具有一阶连续偏导数。若

$$
\boxed{\frac{\partial P}{\partial y}=\frac{\partial Q}{\partial x}},
$$

则存在函数 $U(x,y)$，使

$$
\mathrm dU=P(x,y)\,\mathrm dx+Q(x,y)\,\mathrm dy.
$$

此时方程

$$
P(x,y)\,\mathrm dx+Q(x,y)\,\mathrm dy=0
$$

称为全微分方程，解可写为

$$
\boxed{U(x,y)=C}.
$$

**使用要点：先比较 $P_y,Q_x$，再寻找满足 $U_x=P$、$U_y=Q$ 的原函数。** 可先对 $P$ 关于 $x$ 积分，写成

$$
U(x,y)=\int P(x,y)\,\mathrm dx+h(y),
$$

再用 $U_y=Q$ 确定 $h(y)$。对一个变量积分时，另一变量视为常数，因此此处须补函数 $h(y)$。

按图片中的分类，全微分方程标注为数学一。

### 二阶常系数齐次线性微分方程

对方程

$$
\boxed{y''+py'+qy=0},\qquad p,q\text{ 为常数},
$$

写出特征方程

$$
\boxed{r^2+pr+q=0},\qquad\Delta=p^2-4q.
$$

根据特征根选择通解：

$$
\boxed{
\begin{aligned}
\Delta>0:\quad &y=C_1e^{r_1x}+C_2e^{r_2x},\qquad r_1\ne r_2;\\[3pt]
\Delta=0:\quad &y=(C_1+C_2x)e^{rx},\qquad r=-p/2;\\[3pt]
\Delta<0:\quad &y=e^{\alpha x}(C_1\cos\beta x+C_2\sin\beta x),
\quad r=\alpha\pm\beta i,\ \beta>0.
\end{aligned}}
$$

**记忆：异实根分别写指数，重实根补乘 $x$，共轭复根写“指数乘正弦、余弦”。** $C_1,C_2$ 为独立的任意常数，两项基本解须线性无关。

### 线性微分方程解的结构与叠加原理

记 $L[y]=y''+py'+qy$，对应齐次方程为 $L[y]=0$。

- 若 $Y$ 为对应齐次方程的通解，$y_p$ 为 $L[y]=f(x)$ 的一个特解，则非齐次方程的通解为 $\boxed{y=Y+y_p}$。
- 若 $L[u]=L[v]=f(x)$，则 $\boxed{L[u-v]=0}$：同一非齐次方程的两个特解之差是对应齐次方程的解。
- 若 $L[u]=f_1(x)$、$L[v]=f_2(x)$，则 $\boxed{L[au+bv]=af_1(x)+bf_2(x)}$，其中 $a,b$ 为常数。
- 对齐次方程，解的任意线性组合仍为解；对同一个非齐次方程，两个解直接相加通常使右端变成 $2f(x)$。

### 待定系数法：指数乘多项式

对于

$$
y''+py'+qy=e^{\alpha x}P_n(x),
$$

其中 $P_n(x)$ 为 $n$ 次多项式，设特解

$$
\boxed{y_p=x^ke^{\alpha x}Q_n(x)}.
$$

$Q_n(x)$ 写成包含从 $x^n$ 到常数项的完整待定多项式；$k$ 由 $\alpha$ 在特征方程中的重数确定：

$$
\boxed{
k=\begin{cases}
0,&\alpha\text{ 不是特征根},\\
1,&\alpha\text{ 是单特征根},\\
2,&\alpha\text{ 是二重特征根}.
\end{cases}}
$$

没有指数因子时按 $\alpha=0$ 处理。**先看右端的 $\alpha$，再算特征根，最后比较是否重合、需要补几次 $x$。**

### 待定系数法：指数乘正弦、余弦及多项式

若右端为

$$
f(x)=e^{\alpha x}[P_m(x)\cos\beta x+P_n(x)\sin\beta x],
\qquad\beta>0,
$$

令 $\ell=\max\{m,n\}$，设特解

$$
\boxed{y_p=x^ke^{\alpha x}
\left[Q_\ell(x)\cos\beta x+R_\ell(x)\sin\beta x\right]}.
$$

$Q_\ell,R_\ell$ 是分别设置系数的、次数不超过 $\ell$ 的完整待定多项式；即使右端只有正弦或只有余弦，设特解时通常仍应同时写两项。

对实系数二阶方程：

$$
\boxed{
k=\begin{cases}
0,&\alpha\pm\beta i\text{ 不是特征根},\\
1,&\alpha\pm\beta i\text{ 是特征根}.
\end{cases}}
$$

**补乘 $x^k$ 是为了避免与齐次解重复。** 右端为几类函数之和时，可分别设特解，再相加。

### n 阶常系数齐次线性方程：由特征根写通解

对实系数 $n$ 阶常系数齐次线性方程，每个特征根按重数贡献相应的基本解：

$$
\boxed{r\text{ 为 }k\text{ 重实根}
\quad\Rightarrow\quad
e^{rx}(C_0+C_1x+\cdots+C_{k-1}x^{k-1})}.
$$

$$
\boxed{\alpha\pm\beta i\text{ 为 }k\text{ 重共轭复根}
\quad\Rightarrow\quad
e^{\alpha x}\sum_{j=0}^{k-1}x^j
[A_j\cos\beta x+B_j\sin\beta x]}.
$$

把所有根对应的项相加，即得通解，独立任意常数总数应为 $n$。

反过来，由已知解判断特征根时：

- 含解 $e^{rx}$，则 $r$ 至少为单根。
- 含解 $x^{k-1}e^{rx}$，则 $r$ 至少为 $k$ 重根。
- 含解 $e^{\alpha x}\cos\beta x$ 或 $e^{\alpha x}\sin\beta x$，则 $\alpha\pm\beta i$ 至少为单复根。
- 含解 $xe^{\alpha x}\cos\beta x$ 或 $xe^{\alpha x}\sin\beta x$，则 $\alpha\pm\beta i$ 至少为二重复根。

**反求方程时，先列必须包含的根及最低重数，再用方程阶数核对是否已经全部确定。**

### 欧拉方程：令 t = ln|x|

形如

$$
\boxed{x^2y''+pxy'+qy=f(x)},\qquad p,q\text{ 为常数},
$$

的方程称为欧拉方程。按图片中的分类，此内容标注为数学一。

在不跨过 $0$ 的区间内，令 $t=\ln|x|$，记 $Y(t)=y(x)$，则换元公式为

$$
\boxed{xy'=\frac{\mathrm dY}{\mathrm dt},\qquad
x^2y''=\frac{\mathrm d^2Y}{\mathrm dt^2}-\frac{\mathrm dY}{\mathrm dt}}.
$$

因此，$x>0$ 时可取 $x=e^t$，原方程化为

$$
\boxed{Y''+(p-1)Y'+qY=f(e^t)}.
$$

$x<0$ 时取 $x=-e^t$，右端改为 $f(-e^t)$。解出 $Y(t)$ 后，记得代回 $t=\ln|x|$。

对于齐次欧拉方程，也可在 $x>0$ 时直接试取 $y=x^r$，得到

$$
\boxed{r(r-1)+pr+q=0
\iff r^2+(p-1)r+q=0}.
$$

**特征式中的一次项系数是 $p-1$。** 两个不等实根对应 $C_1x^{r_1}+C_2x^{r_2}$；二重实根对应 $x^r(C_1+C_2\ln x)$；复根 $\alpha\pm\beta i$ 对应 $x^\alpha[C_1\cos(\beta\ln x)+C_2\sin(\beta\ln x)]$。

## <span style="color: #3498db;">第七部分：无穷级数</span>

### 常用麦克劳林展开（含通项）

下面的无穷级数在注明的区间内等于原函数；求极限时可截断为有限项，并加上相应余项。

#### 指数函数与几何级数

$$
e^x=\sum_{n=0}^{\infty}\frac{x^n}{n!}
=1+x+\frac{x^2}{2!}+\cdots+\frac{x^n}{n!}+\cdots,\qquad x\in\mathbb R.
$$

$$
\frac1{1+x}=\sum_{n=0}^{\infty}(-1)^nx^n
=1-x+x^2-x^3+\cdots+(-1)^nx^n+\cdots,\qquad |x|<1.
$$

$$
\frac1{1-x}=\sum_{n=0}^{\infty}x^n
=1+x+x^2+\cdots+x^n+\cdots,\qquad |x|<1.
$$

#### 对数函数

$$
\ln(1+x)=\sum_{n=1}^{\infty}(-1)^{n-1}\frac{x^n}{n}
=x-\frac{x^2}{2}+\frac{x^3}{3}-\cdots+(-1)^{n-1}\frac{x^n}{n}+\cdots,\qquad -1<x\le1.
$$

#### 正弦与余弦

$$
\sin x=\sum_{n=0}^{\infty}(-1)^n\frac{x^{2n+1}}{(2n+1)!}
=x-\frac{x^3}{3!}+\frac{x^5}{5!}-\cdots+(-1)^n\frac{x^{2n+1}}{(2n+1)!}+\cdots,\qquad x\in\mathbb R.
$$

$$
\cos x=\sum_{n=0}^{\infty}(-1)^n\frac{x^{2n}}{(2n)!}
=1-\frac{x^2}{2!}+\frac{x^4}{4!}-\cdots+(-1)^n\frac{x^{2n}}{(2n)!}+\cdots,\qquad x\in\mathbb R.
$$

#### 二项式展开

$$
(1+x)^\alpha=\sum_{n=0}^{\infty}\binom\alpha n x^n
=1+\alpha x+\frac{\alpha(\alpha-1)}{2!}x^2+\cdots+
\frac{\alpha(\alpha-1)\cdots(\alpha-n+1)}{n!}x^n+\cdots.
$$

其中 $\binom\alpha0=1$，$\alpha$ 为固定实常数。

| $\alpha$ 的范围       | 展开成立的 $x$ 范围             |
| --------------------- | ------------------------------- |
| $\alpha\le-1$         | $(-1,1)$                        |
| $-1<\alpha<0$         | $(-1,1]$                        |
| $\alpha>0$ 且不是整数 | $[-1,1]$                        |
| $\alpha$ 为正整数     | $\mathbb R$，展开为有限项多项式 |

$\alpha=0$ 时为常数函数 $1$。

#### 正切函数

$$
\tan x=x+\frac{x^3}{3}+\frac{2x^5}{15}+\frac{17x^7}{315}+\cdots,\qquad |x|<\frac\pi2.
$$

含通项的形式为：

$$
\tan x=\sum_{n=1}^{\infty}
\frac{(-1)^{n-1}2^{2n}(2^{2n}-1)B_{2n}}{(2n)!}x^{2n-1},\qquad |x|<\frac\pi2.
$$

$B_{2n}$ 为伯努利数，例如 $B_2=1/6$、$B_4=-1/30$、$B_6=1/42$；其定义为

$$
\frac{t}{e^t-1}=\sum_{m=0}^{\infty}B_m\frac{t^m}{m!}\qquad(|t|<2\pi),
$$

其中左侧在 $t=0$ 处按极限补定义为 $1$。

**常用计算优先记住 $\tan x=x+x^3/3+2x^5/15+o(x^5)$。**

#### 反正弦函数

$$
\arcsin x=\sum_{n=0}^{\infty}
\frac{(2n)!}{4^n(n!)^2(2n+1)}x^{2n+1},\qquad |x|\le1.
$$

即

$$
\arcsin x=x+\frac{x^3}{6}+\frac{3x^5}{40}+\frac{5x^7}{112}+\cdots+
\frac{(2n)!}{4^n(n!)^2(2n+1)}x^{2n+1}+\cdots.
$$

#### 反正切函数

$$
\arctan x=\sum_{n=0}^{\infty}(-1)^n\frac{x^{2n+1}}{2n+1},\qquad |x|\le1.
$$

即

$$
\arctan x=x-\frac{x^3}{3}+\frac{x^5}{5}-\frac{x^7}{7}+\cdots+
(-1)^n\frac{x^{2n+1}}{2n+1}+\cdots.
$$

## <span style="color: #3498db;">第八部分：空间解析几何</span>

### 平面二次曲线的判别式

对于一般二次曲线方程

$$
Ax^2+Bxy+Cy^2+Dx+Ey+F=0,
\qquad (A,B,C)\ne(0,0,0),
$$

计算二次项的判别式

$$
\boxed{\Delta=B^2-4AC}.
$$

在**非退化实曲线** 的前提下，有

| 判别式     | 图形类型       |
| ---------- | -------------- |
| $\Delta<0$ | 椭圆型，包括圆 |
| $\Delta=0$ | 抛物线型       |
| $\Delta>0$ | 双曲线型       |

**记忆：负椭圆、零抛物、正双曲。** 判别式用于判断类型；是否退化、是否存在实点，还须结合方程的其余系数判断。

#### 特别注意：只有二次项的方程

对于图片中的特殊形式

$$
Ax^2+Bxy+Cy^2=1,
$$

不能直接把 $\Delta=0$ 判为抛物线：该式没有一次项，此时可能表示两条平行直线或无实点。例如，$x^2=1$ 表示 $x=\pm1$ 两条直线，$-x^2=1$ 无实点。

该形式下，$\Delta<0$ 且 $A>0$ 时为实椭圆；$\Delta<0$ 且 $A<0$ 时无实点；$\Delta>0$ 时为双曲线。

## <span style="color: #3498db;">第九部分：曲线积分、曲面积分</span>

## <span style="color: #3498db;">第十部分：特殊公式</span>

### 三角恒等式

$$
\sec x=\frac1{\cos x},\qquad\csc x=\frac1{\sin x}
$$

$$
\sin^2x+\cos^2x=1,\qquad1+\tan^2x=\sec^2x,\qquad1+\cot^2x=\csc^2x
$$

各式须有定义：涉及正割、正切时 $\cos x\ne0$；涉及余割、余切时 $\sin x\ne0$。

### 根式与绝对值

$$
\boxed{\sqrt{a^2}=|a|}\qquad(a\in\mathbb R)
$$

算术平方根非负：当 $a\ge0$ 时结果为 $a$；当 $a<0$ 时结果为 $-a$。不能直接把 $\sqrt{a^2}$ 写成 $a$。

### 平方和公式

$$
1^2+2^2+\cdots+n^2=\sum_{k=1}^n k^2
=\frac{n(n+1)(2n+1)}6
\qquad(n\in\mathbb N^+).
$$

### 常用不等式

$$
x<\tan x<\frac4\pi x\qquad\left(0<x<\frac\pi4\right)
$$

$$
\sin x>\frac2\pi x\qquad\left(0<x<\frac\pi2\right)
$$

$$
\frac{x}{1+x}<\ln(1+x)<x\qquad(x>-1,\ x\ne0)
$$

对数不等式在 $x=0$ 时两边均取等号。

$$
\sqrt[3]{abc}\le\frac{a+b+c}{3}
\le\sqrt{\frac{a^2+b^2+c^2}{3}}
\qquad(a,b,c\ge0)
$$

### 斯特林公式（阶乘的渐近估计）

当 $n\to\infty$ 时，

$$
\boxed{n!\sim\sqrt{2\pi n}\left(\frac ne\right)^n}.
$$

这里 $\sim$ 表示两边比值趋于 $1$，可用于估计大整数的阶乘及计算含阶乘的极限。

取对数可得更精确的加法形式：

$$
\boxed{\ln(n!)=n\ln n-n+\frac12\ln(2\pi n)+o(1)}.
$$

因此也有常用的等价形式：

$$
\boxed{\ln(n!)\sim n\ln n-n\sim n\ln n}.
$$

**等价式描述相对误差趋于零；若题目中有相减抵消，应使用保留对数项和余项的加法形式。**

### 高斯积分（重点记忆）

$$
\boxed{\int_0^{+\infty}e^{-u^2}\,\mathrm du=\frac{\sqrt{\pi}}2}.
$$
