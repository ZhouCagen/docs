# 高等数学公式笔记

## 常用等价无穷小

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

## 复合函数的奇偶性

$f(g(x))$ 的定义域须关于原点对称。**内偶则偶，内奇则外。**

| 内函数 $g$ | 外函数 $f$ | 复合函数 |
| ---------- | ---------- | -------- |
| 偶         | 任意       | 偶       |
| 奇         | 奇         | 奇       |
| 奇         | 偶         | 偶       |

外函数非奇非偶时，“内奇则外”不能直接判断。零函数既奇又偶。

## 反三角函数的定义域与值域

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

## 三角恒等式

$$
\sec x=\frac1{\cos x},\qquad\csc x=\frac1{\sin x}
$$

$$
\sin^2x+\cos^2x=1,\qquad1+\tan^2x=\sec^2x,\qquad1+\cot^2x=\csc^2x
$$

各式须有定义：涉及正割、正切时 $\cos x\ne0$；涉及余割、余切时 $\sin x\ne0$。

## 五个函数的大小关系与三阶差值

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

## 函数极限的 24 种定义

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

任意给定 $\varepsilon>0$ 或 $M>0$，存在 $\delta>0$ 或 $X>0$，使**所有满足输入条件的 $x$ 都满足输出条件**。$\delta,X$ 不能依赖具体的 $x$。

本笔记中 $\infty$ 表示绝对值无限增大；“极限存在”默认指有限极限。$x\to x_0$ 时不要求 $f(x_0)$ 有定义。

## 极限存在的等价表述

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

## 极限的局部保号性

设 $\lim_{x\to x_0}f(x)=A\in\mathbb R$，下述“附近”指充分小的去心邻域。

- $A>0$（$A<0$）$\Rightarrow$ 附近 $f(x)>0$（$f(x)<0$）。
- $A\ne0$ $\Rightarrow$ 附近 $f(x)$ 与 $A$ 同号，且 $|f(x)|>|A|/2$。
- 附近 $f(x)\ge0$（$f(x)\le0$）$\Rightarrow A\ge0$（$A\le0$）。即使函数严格正、负，极限仍可能为 $0$。
- $A=0$ 时，无法判断附近函数的符号。

同样适用于单侧及无穷远趋近。

## 有界性常用结论

- **有限极限存在 $\Rightarrow$ 在相应趋近区域内局部有界**，反之不成立，如 $\sin(1/x)$ 在 $x\to0$ 时。
- 闭区间上的连续函数有界，并取得最大值、最小值。
- $(a,b)$ 上连续，且两端单侧极限均有限 $\Rightarrow$ 在 $(a,b)$ 上有界。
- $f,g$ 有界 $\Rightarrow f\pm g,fg$ 有界；若另有 $|g|\ge m>0$，则 $f/g$ 有界。

局部有界不等于全域有界；上、下界不唯一，最大、最小值唯一。

## 无穷小的比较

同一趋近过程中，$\alpha,\beta\to0$，比较分母非零：

| 比值极限                             | $\alpha$ 相对于 $\beta$ |
| ------------------------------------ | ----------------------- | -------- | ---- |
| $\alpha/\beta\to0$                   | 高阶，$\alpha=o(\beta)$ |
| $\lvert\alpha/\beta\rvert\to+\infty$ | 低阶                    |
| $\alpha/\beta\to c$，$0<             | c                       | <\infty$ | 同阶 |
| $\alpha/\beta\to1$                   | 等价，$\alpha\sim\beta$ |

$$
\frac{\alpha}{\beta^k}\to c,\quad k>0,\quad0<|c|<\infty
\quad\Rightarrow\quad\alpha\text{ 是 }\beta\text{ 的 }k\text{ 阶无穷小}
$$

$k$ 非整数时须保证 $\beta^k$ 有定义。等价必同阶，同阶未必等价；并非任意两个无穷小都能按上表比阶。

## 八个常用麦克劳林公式

$x\to0$，$\alpha$ 为固定实常数；对数与一般实数幂要求 $1+x>0$。

$$
\sin x=x-\frac{x^3}{3!}+o(x^3)
$$

$$
\cos x=1-\frac{x^2}{2!}+\frac{x^4}{4!}+o(x^4)
$$

$$
\arcsin x=x+\frac{x^3}{3!}+o(x^3)
$$

$$
\tan x=x+\frac{x^3}{3}+o(x^3)
$$

$$
\arctan x=x-\frac{x^3}{3}+o(x^3)
$$

$$
\ln(1+x)=x-\frac{x^2}{2}+\frac{x^3}{3}+o(x^3)
$$

$$
e^x=1+x+\frac{x^2}{2!}+\frac{x^3}{3!}+o(x^3)
$$

$$
(1+x)^\alpha=1+\alpha x+\frac{\alpha(\alpha-1)}{2!}x^2+o(x^2)
$$

**相减须展开到抵消后首个非零项；截断或换元时，余项阶数也要相应调整。**

## 常见无穷大的增长速度比较

固定常数 $\alpha,\beta>0$、$a>1$；$f\ll g$ 表示 $f/g\to0$。

$$
(\ln x)^\alpha\ll x^\beta\ll a^x\qquad(x\to+\infty)
$$

$$
(\ln n)^\alpha\ll n^\beta\ll a^n\ll n!\ll n^n\qquad(n\to\infty)
$$

**对数 → 正幂 → 指数 → 阶乘 → 自身幂，增长越来越快。**

## 带佩亚诺余项的泰勒公式

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

## 小 $o$ 的运算规则

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

## 常见极限

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

## 连续性的性质

内点 $x_0$ 处：

$$
f\text{ 在 }x_0\text{ 处连续}
\iff\lim_{x\to x_0^-}f(x)=\lim_{x\to x_0^+}f(x)=f(x_0).
$$

- **四则运算：** $f,g$ 在 $x_0$ 处连续，则 $f\pm g,fg$ 也连续；若 $g(x_0)\ne0$，则 $f/g$ 也连续。
- **复合函数：** $\varphi$ 在 $x_0$ 处连续，$f$ 在 $u_0=\varphi(x_0)$ 处连续，则 $f(\varphi(x))$ 在 $x_0$ 处连续。
- **反函数：** $f$ 在区间 $I$ 上严格单调且连续，则反函数在 $f(I)$ 上连续，且单调性与 $f$ 相同。
- **局部保号：** $f$ 在 $x_0$ 处连续且 $f(x_0)>0$（$<0$），则存在 $\delta>0$，使 $|x-x_0|<\delta$ 时 $f(x)>0$（$<0$）。

## 间断点分类

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

## 数列极限

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

## 平方和公式

$$
1^2+2^2+\cdots+n^2=\sum_{k=1}^n k^2
=\frac{n(n+1)(2n+1)}6
\qquad(n\in\mathbb N^+).
$$

## 常用不等式

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
