# 高等数学习题笔记

## 已知极限求未知函数的极限（例 1.27）

**题目：** 已知

$$
\lim_{x\to0}\frac{\tan2x+xf(x)}{\sin(x^3)}=0,
$$

求 $\displaystyle\lim_{x\to0}\frac{2+f(x)}{x^2}$。

**解：** 因 $\sin(x^3)\sim x^3$，令

$$
\frac{\tan2x+xf(x)}{x^3}=\alpha(x)\to0.
$$

由 $\tan2x=2x+\frac83x^3+o(x^3)$，得

$$
\frac{2+f(x)}{x^2}
=\frac{2x-\tan2x}{x^3}+\alpha(x)
\longrightarrow\boxed{-\frac83}.
$$

**要点：** 脱帽法——将极限为 $0$ 的式子记为无穷小 $\alpha(x)$，再整理、展开。

## 指数差的无穷小阶数（例 1.19）

**题目：** $x\to0$ 时，$e^{\tan x}-e^{\sin x}$ 与 $x^n$ 为同阶无穷小，求 $n$。

**解：** 提取公因式，利用 $e^u-1\sim u$：

$$
\begin{aligned}
e^{\tan x}-e^{\sin x}
&=e^{\sin x}\bigl(e^{\tan x-\sin x}-1\bigr)\\
&\sim\tan x-\sin x\\
&=\tan x(1-\cos x)\\
&\sim x\cdot\frac{x^2}{2}=\frac{x^3}{2}.
\end{aligned}
$$

故 $\boxed{n=3}$。

## 对数求导求最大值点（例 1.10）

**题目：** $0<x<\frac12$，求 $y=x^6(1-x)^2(1-2x)^4$ 的最大值点。

**解：** 区间内 $y>0$，取对数求导：

$$
\ln y=6\ln x+2\ln(1-x)+4\ln(1-2x),
$$

$$
\frac{y'}y=\frac6x-\frac2{1-x}-\frac8{1-2x}
=\frac{24x^2-28x+6}{x(1-x)(1-2x)}.
$$

令 $y'=0$，得 $x=\frac{7\pm\sqrt{13}}{12}$，区间内仅有

$$
\boxed{x_0=\frac{7-\sqrt{13}}{12}}.
$$

$x<x_0$ 时 $y'>0$，$x>x_0$ 时 $y'<0$，故 $x_0$ 为最大值点。

**要点：** 多项乘除、乘方的正函数，可取对数后求导。

## 幂和的 n 次方根极限（例 2.10）

**题目：** 设 $m$ 为固定正整数，$a_1,\ldots,a_m$ 为固定非负数，求

$$
\lim_{n\to\infty}\sqrt[n]{a_1^n+a_2^n+\cdots+a_m^n}.
$$

**解：** 令 $a=\max\{a_1,\ldots,a_m\}$，则

$$
a^n\le a_1^n+a_2^n+\cdots+a_m^n\le ma^n,
$$

开 $n$ 次方得

$$
a\le\sqrt[n]{a_1^n+a_2^n+\cdots+a_m^n}\le a\,m^{1/n}.
$$

因 $m^{1/n}\to1$，由夹逼准则得

$$
\boxed{\lim_{n\to\infty}\sqrt[n]{a_1^n+a_2^n+\cdots+a_m^n}
=\max\{a_1,\ldots,a_m\}}.
$$

## 余弦关系确定的数列极限（例 2.11）

**题目：** 设 $0<a_n,b_n<\frac\pi2$，$\cos a_n-a_n=\cos b_n$，且 $b_n\to0$，求

$$
\lim_{n\to\infty}a_n,\qquad\lim_{n\to\infty}\frac{a_n}{b_n^2}.
$$

**解：** 由 $\cos a_n-\cos b_n=a_n>0$，及 $\cos x$ 在 $(0,\pi/2)$ 上严格递减，得

$$
0<a_n<b_n\to0\quad\Rightarrow\quad\boxed{a_n\to0}.
$$

由 $1-\cos b_n=1-\cos a_n+a_n$，得

$$
\begin{aligned}
\frac{a_n}{b_n^2}
&=\frac{1-\cos b_n}{b_n^2}
\cdot\frac{a_n}{1-\cos a_n+a_n}\\
&=\frac{1-\cos b_n}{b_n^2}
\cdot\frac1{\dfrac{1-\cos a_n}{a_n}+1}
\longrightarrow\frac12\cdot1=\boxed{\frac12}.
\end{aligned}
$$

其中 $1-\cos t\sim t^2/2$，故 $(1-\cos a_n)/a_n\to0$。

## 对数递推数列：单调有界（例 2.14）

**题目：**

1. 证明方程 $x=2\ln(1+x)$ 在 $(0,+\infty)$ 内有唯一实根 $\xi$。
2. 任取 $x_1>\xi$，定义 $x_{n+1}=2\ln(1+x_n)$，证明数列收敛并求极限。

**解：** 令 $F(x)=x-2\ln(1+x)$，则

$$
F'(x)=\frac{x-1}{x+1}.
$$

$F$ 在 $(0,1)$ 上递减，在 $(1,+\infty)$ 上递增。又

$$
F(0)=0,\qquad F(1)=1-2\ln2<0,\qquad
\lim_{x\to+\infty}F(x)=+\infty,
$$

故正根唯一，且 $\xi>1$。

若 $x_n>\xi$，由 $F(x_n)>0$ 及对数函数递增，得

$$
\xi=2\ln(1+\xi)<x_{n+1}=2\ln(1+x_n)<x_n.
$$

由归纳法，$\{x_n\}$ 递减且以下界 $\xi$ 有界，故存在极限 $L\ge\xi$。递推式两边取极限：

$$
L=2\ln(1+L).
$$

由正根唯一性，$\boxed{\lim_{n\to\infty}x_n=\xi}$。

## 余弦递推数列：压缩估计（例 2.15）

**题目：**

1. 证明方程 $x=\cos x$ 在 $(0,\pi/3)$ 内有唯一实根 $a$。
2. 设 $-1\le x_1\le1$，定义 $x_{n+1}=\cos x_n$，证明 $x_n\to a$。

**解：** 令 $F(x)=\cos x-x$，则

$$
F(0)=1>0,\qquad F(\pi/3)=\frac12-\frac\pi3<0,
\qquad F'(x)=-\sin x-1<0.
$$

由零点定理及严格单调性，存在唯一 $a\in(0,\pi/3)$ 使 $a=\cos a$。

由 $x_1\in[-1,1]$，递推得 $x_n\in[\cos1,1]\subset(0,\pi/3)$（$n\ge2$）。由拉格朗日中值定理，

$$
|x_{n+1}-a|=|\cos x_n-\cos a|
\le\frac{\sqrt3}{2}|x_n-a|\qquad(n\ge2).
$$

反复迭代得

$$
|x_n-a|\le\left(\frac{\sqrt3}{2}\right)^{n-2}|x_2-a|
\longrightarrow0.
$$

故 $\boxed{\lim_{n\to\infty}x_n=a}$。

## 根式有理化求极限（题 1.7）

**题目：** 求 $\displaystyle\lim_{x\to0^+}\frac{1-\sqrt{\cos x}}{x(1-\cos\sqrt{x})}$。

**解：** 分子有理化，利用 $1-\cos t\sim t^2/2$：

$$
\begin{aligned}
\lim_{x\to0^+}\frac{1-\sqrt{\cos x}}{x(1-\cos\sqrt{x})}
&=\lim_{x\to0^+}\frac{1-\cos x}{x(1-\cos\sqrt{x})(1+\sqrt{\cos x})}\\
&=\lim_{x\to0^+}\frac{x^2/2}{x\cdot(x/2)\cdot(1+\sqrt{\cos x})}
=\boxed{\frac12}.
\end{aligned}
$$

## 相邻项比值判断数列极限（题 2.2）

**题目：** 设 $x_n>0$，且 $\displaystyle\lim_{n\to\infty}\frac{x_{n+1}}{x_n}=\frac12$，则（　）。

- A. $\lim x_n=0$
- B. $\lim x_n$ 存在，但不为零
- C. $\lim x_n$ 不存在
- D. $\lim x_n$ 可能存在，也可能不存在

**解：** 因 $x_{n+1}/x_n\to1/2<1$，充分大的 $n$ 满足

$$
0<x_{n+1}<x_n.
$$

故数列从某项起递减且有下界，存在极限 $A\ge0$。若 $A>0$，则

$$
\lim_{n\to\infty}\frac{x_{n+1}}{x_n}=\frac AA=1,
$$

与已知矛盾。因此 $\boxed{\lim_{n\to\infty}x_n=0}$，选 **A** 。

## 分式递推数列：单调有界（题 2.8）

**题目：** 设 $x_1=2$，$x_n+(x_n-4)x_{n-1}=3$（$n\ge2$），证明 $\lim x_n$ 存在，并求其值。

**解：** 整理得

$$
x_n=\frac{3+4x_{n-1}}{1+x_{n-1}}.
$$

由 $x_1=2$ 归纳得 $x_n>0$，且 $x_2=11/3>x_1$。若 $x_n>x_{n-1}$，则

$$
x_{n+1}-x_n
=\frac{x_n-x_{n-1}}{(1+x_n)(1+x_{n-1})}>0.
$$

故数列严格递增。又

$$
x_n=4-\frac1{1+x_{n-1}}<4\qquad(n\ge2),
$$

故数列有上界，由单调有界准则，存在极限 $A\ge2$。递推式两边取极限：

$$
A=\frac{3+4A}{1+A}
\quad\Rightarrow\quad A^2-3A-3=0.
$$

舍去负根，得

$$
\boxed{\lim_{n\to\infty}x_n=\frac{3+\sqrt{21}}2}.
$$

## 函数增量与微分之差的极限

**题目：** 设函数 $f(x)$ 在 $x=1$ 处可导，且 $\Delta f(1)$ 是 $f(x)$ 在 $x=1$ 处、自变量增量为 $\Delta x$ 时的函数值增量，则

$$
\lim_{\Delta x\to0}\frac{\Delta f(1)-\left.df\right|_{x=1}}{\Delta x}=\text{（　）}.
$$

- A. $f'(1)$
- B. $1$
- C. $\infty$
- D. $0$

**解法一：利用增量与微分的关系。** 一元函数可导即在该点可微，因此

$$
\Delta y=dy+o(\Delta x)
\quad\Rightarrow\quad
\Delta f(1)-\left.df\right|_{x=1}=o(\Delta x).
$$

所以

$$
\lim_{\Delta x\to0}\frac{\Delta f(1)-\left.df\right|_{x=1}}{\Delta x}
=\lim_{\Delta x\to0}\frac{o(\Delta x)}{\Delta x}
=\boxed{0}.
$$

选 **D** 。

**解法二：分别计算两项。** 由增量与微分的定义，

$$
\Delta f(1)=f(1+\Delta x)-f(1),\qquad
\left.df\right|_{x=1}=f'(1)dx=f'(1)\Delta x.
$$

于是

$$
\lim_{\Delta x\to0}\frac{\Delta f(1)}{\Delta x}=f'(1),\qquad
\lim_{\Delta x\to0}\frac{\left.df\right|_{x=1}}{\Delta x}=f'(1).
$$

故原式 $=f'(1)-f'(1)=0$。

**关键：增量与微分一般不相等，但它们的差是关于 $\Delta x$ 的高阶无穷小。**

## 反函数的二阶导数（例 4.7）

**题目：** 当 $x>0$ 时，设 $y=f(x)=3x^2+e^x$ 有反函数 $x=\varphi(y)$，则 $\varphi''(3+e)=$ **\_\_** 。

**解：** 使用反函数的二阶导数公式：

$$
\varphi''(y)=-\frac{f''(x)}{[f'(x)]^3},\qquad y=f(x).
$$

先找对应点。由于 $f(1)=3+e$，且 $x>0$ 时 $f'(x)=6x+e^x>0$，函数严格递增，所以 $y=3+e$ 唯一对应 $x=1$。

再求导：

$$
f'(x)=6x+e^x,\qquad f''(x)=6+e^x.
$$

代入得：

$$
\begin{aligned}
\varphi''(3+e)
&=-\frac{f''(1)}{[f'(1)]^3}\\
&=-\frac{6+e}{(6+e)^3}
=\boxed{-\frac1{(6+e)^2}}.
\end{aligned}
$$

**方法：不必求出反函数的显式表达式，先由 $y$ 找对应的 $x$，再代入反函数二阶导数公式。**

## 取对数求隐函数的二阶导数（例 4.11）

**题目：** 设函数 $y=y(x)$ 由方程 $xe^{f(y)}=e^y\ln2$ 确定，其中 $f$ 具有二阶导数，且 $f'(y)\ne1$，则 $\dfrac{d^2y}{dx^2}=$ **\_\_** 。

**解：** 因为 $e^y\ln2>0$ 且 $e^{f(y)}>0$，所以 $x>0$，可对方程两端取对数：

$$
\ln x+f(y)=y+\ln(\ln2).
$$

两端关于 $x$ 求导，注意 $y=y(x)$，得

$$
\frac1x+f'(y)y'=y'.
$$

由 $f'(y)\ne1$，解得

$$
y'=\frac1{x[1-f'(y)]}.
$$

对一阶导数关系再次关于 $x$ 求导：

$$
-\frac1{x^2}+f''(y)(y')^2+f'(y)y''=y''.
$$

整理并代入 $y'$：

$$
\begin{aligned}
y''
&=\frac{-\dfrac1{x^2}+f''(y)(y')^2}{1-f'(y)}\\
&=\frac{-\dfrac1{x^2}+\dfrac{f''(y)}{x^2[1-f'(y)]^2}}{1-f'(y)}\\
&=\boxed{-\frac{[1-f'(y)]^2-f''(y)}{x^2[1-f'(y)]^3}}.
\end{aligned}
$$

**关键：指数形式可先取对数简化；对 $f'(y)y'$ 求导时，同时使用乘积法则和链式法则，得到 $f''(y)(y')^2+f'(y)y''$。条件 $f'(y)\ne1$ 保证分母不为零。**

## 由同阶无穷小确定参数（题 8）

**题目：** 当 $x\to0$ 时，$e^x-\dfrac{1+ax^2}{1+bx}$ 与 $x^3$ 是同阶无穷小，则（　）。

- A. $a=\frac12,\ b=1$
- B. $a=-\frac12,\ b=1$
- C. $a=\frac12,\ b=-1$
- D. $a=-\frac12,\ b=-1$

**解：** 同阶要求与 $x^3$ 的比值趋于有限非零常数，因此一次项、二次项必须消失，三次项系数必须非零。先通分：

$$
e^x-\frac{1+ax^2}{1+bx}
=\frac{(1+bx)e^x-1-ax^2}{1+bx}.
$$

因分母趋于 $1$，只需展开分子：

$$
(1+bx)e^x-1-ax^2
=(1+b)x+\left(\frac12+b-a\right)x^2
+\left(\frac16+\frac b2\right)x^3+o(x^3).
$$

令前两项系数为零，得

$$
1+b=0,\qquad\frac12+b-a=0
\quad\Rightarrow\quad\boxed{b=-1,\quad a=-\frac12}.
$$

此时三次项系数为 $\frac16-\frac12=-\frac13\ne0$，故

$$
\lim_{x\to0}\frac{e^x-\dfrac{1-x^2/2}{1-x}}{x^3}=-\frac13.
$$

选 **D** 。

**要点：同阶要求比值极限有限且非零，不要求等于 $1$；确定参数后还须检查目标阶的系数非零。**

## 含变上限积分的函数：第一类间断点个数（题 12）

**题目：** 函数

$$
f(x)=\frac{(x^2-x)|x+1|e^{-1/x}}{\displaystyle\int_1^x t^2\sin t\,dt},
\qquad x\in[-\pi,\pi],
$$

的第一类间断点的个数为（　）。

- A. $0$
- B. $1$
- C. $2$
- D. $3$

**解：** 先找分母零点及指数项无定义的点。记

$$
F(x)=\int_1^x t^2\sin t\,dt.
$$

因 $t^2\sin t$ 为奇函数，$\int_0^x t^2\sin t\,dt$ 为偶函数，故 $F(-x)=F(x)$。在 $(0,\pi)$ 上，

$$
F'(x)=x^2\sin x>0,
$$

所以 $F$ 在 $[0,\pi]$ 上严格递增，且 $F(1)=0$。结合偶性可知，分母在 $[-\pi,\pi]$ 内仅在 $x=\pm1$ 处为零。因此只需检查 $-1,0,1$；其他点连续，端点按单侧连续理解。

**① $x=1$：可去间断点。** 由 $F'(1)=\sin1$，有 $F(x)\sim\sin1\,(x-1)$，于是

$$
\lim_{x\to1}f(x)
=\lim_{x\to1}\frac{x(x-1)|x+1|e^{-1/x}}{\sin1\,(x-1)}
=\frac{2}{e\sin1}.
$$

左右极限相等且有限，但原式在 $1$ 处无定义，故为可去间断点，属于第一类。

**② $x=-1$：跳跃间断点。** 由 $F'(-1)=-\sin1$，有

$$
F(x)\sim-\sin1\,(x+1),\qquad
(x^2-x)e^{-1/x}\to2e.
$$

因此

$$
\lim_{x\to-1^-}f(x)=\frac{2e}{\sin1},\qquad
\lim_{x\to-1^+}f(x)=-\frac{2e}{\sin1}.
$$

左右极限均有限但不相等，故为跳跃间断点，属于第一类。

**③ $x=0$：第二类间断点。** 分母满足

$$
F(0)=-\int_0^1t^2\sin t\,dt<0.
$$

当 $x\to0^+$ 时，$e^{-1/x}\to0$，故 $f(x)\to0$。当 $x\to0^-$ 时，令 $u=-1/x\to+\infty$，则

$$
(x^2-x)|x+1|e^{-1/x}\sim(-x)e^{-1/x}
=\frac{e^u}{u}\to+\infty.
$$

所以

$$
\lim_{x\to0^-}f(x)=-\infty,\qquad
\lim_{x\to0^+}f(x)=0.
$$

故 $0$ 为第二类间断点，不计入第一类。

综上，第一类间断点为 $-1$ 和 $1$，共 $\boxed{2}$ 个，选 **C** 。

**要点：先找全体可疑点；分母为零不一定是无穷间断点，还须比较分子的消失阶数。绝对值与 $e^{-1/x}$ 都要分别讨论左右极限。**

## 由函数列极限定义的函数：连续性（题 5）

**题目：** 讨论函数

$$
f(x)=\lim_{n\to\infty}\frac{x^{n+2}-x^{-n}}{x^n+x^{-n}}
$$

的连续性。

**解：** 原式含 $x^{-n}$，故首先要求 $x\ne0$。对固定的 $x\ne0$，分子、分母同乘 $x^n$：

$$
\frac{x^{n+2}-x^{-n}}{x^n+x^{-n}}
=\frac{x^{2n+2}-1}{x^{2n}+1}.
$$

根据 $|x|$ 与 $1$ 的大小关系分类：

- $0<|x|<1$ 时，$x^{2n}\to0$，故 $f(x)=-1$。
- $|x|>1$ 时，同除以 $x^{2n}$，得 $f(x)=\lim\dfrac{x^2-x^{-2n}}{1+x^{-2n}}=x^2$。
- $x=\pm1$ 时，每一项的分子均为 $0$，故 $f(\pm1)=0$。

因此

$$
\boxed{
f(x)=\begin{cases}
x^2,&|x|>1,\\
0,&x=\pm1,\\
-1,&0<|x|<1.
\end{cases}}
$$

在 $x=1$ 处，

$$
\lim_{x\to1^-}f(x)=-1,\qquad
\lim_{x\to1^+}f(x)=1,\qquad f(1)=0.
$$

在 $x=-1$ 处，

$$
\lim_{x\to-1^-}f(x)=1,\qquad
\lim_{x\to-1^+}f(x)=-1,\qquad f(-1)=0.
$$

所以 $x=\pm1$ 都是跳跃间断点；函数在

$$
(-\infty,-1)\cup(-1,0)\cup(0,1)\cup(1,+\infty)
$$

上连续。

**关于 $x=0$：** 原函数在 $0$ 处无定义，但 $\lim_{x\to0}f(x)=-1$，故 $0$ 是一个可去的空缺点（按将无定义点纳入间断点的教材约定，称为可去间断点）。补定义 $f(0)=-1$ 后，函数在 $0$ 处连续。

**要点：先固定 $x$ 求 $n\to\infty$ 的极限，得到分段函数，再讨论连续性；约去负幂不能自动扩大原函数的定义域。**

## 构造乘积辅助函数应用罗尔定理（例 6.5）

**题目：** 设 $f(x)$ 在 $[a,b]$ 上连续，在 $(a,b)$ 内可导，$f(a)=0$，$\alpha>0$。证明：存在 $\xi\in(a,b)$，使

$$
f(\xi)=\frac{b-\xi}{\alpha}f'(\xi).
$$

**分析：** 把结论改写为

$$
f'(\xi)-\frac{\alpha}{b-\xi}f(\xi)=0.
$$

这是 $f'+pf$ 的形式。希望构造 $F=wf$，使 $w'/w=-\alpha/(b-x)$，可取 $w(x)=(b-x)^\alpha$。

**证明：** 令

$$
F(x)=f(x)(b-x)^\alpha,\qquad x\in[a,b].
$$

因为 $\alpha>0$，$F$ 在 $[a,b]$ 上连续，在 $(a,b)$ 内可导，且

$$
F(a)=f(a)(b-a)^\alpha=0,\qquad F(b)=f(b)\cdot0^\alpha=0.
$$

由罗尔定理，存在 $\xi\in(a,b)$，使

$$
\begin{aligned}
0=F'(\xi)
&=f'(\xi)(b-\xi)^\alpha
-\alpha f(\xi)(b-\xi)^{\alpha-1}\\
&=(b-\xi)^{\alpha-1}\bigl[(b-\xi)f'(\xi)-\alpha f(\xi)\bigr].
\end{aligned}
$$

由于 $b-\xi>0$，可约去 $(b-\xi)^{\alpha-1}$，再除以 $\alpha>0$，得到

$$
\boxed{f(\xi)=\frac{b-\xi}{\alpha}f'(\xi)}.
$$

**要点：让 $f(a)=0$ 负责左端点，让因子 $(b-x)^\alpha$ 负责右端点，构造出两端同为零的辅助函数。即使 $0<\alpha<1$，也不必要求 $F$ 在端点 $b$ 可导；罗尔定理只要求开区间内可导。**

## 两次使用罗尔定理证明方程有两个根（例 6.7）

**题目：** 设函数 $f(x)$ 在 $[0,1]$ 上具有二阶导数，且

$$
f(1)>0,\qquad\lim_{x\to0^+}\frac{f(x)}x<0.
$$

证明：方程

$$
f(x)f''(x)+[f'(x)]^2=0
$$

在 $(0,1)$ 内至少存在两个不同实根。（题设中的比值极限按有限负数理解；端点导数按单侧导数理解。）

**分析：** 注意乘积求导：

$$
\bigl[f(x)f'(x)\bigr]'=f(x)f''(x)+[f'(x)]^2.
$$

因此令 $F=ff'$，目标变为证明 $F'$ 有两个不同零点。只要先找到 $F$ 的三个依次排列的零点，就能在两个相邻区间分别使用罗尔定理。

**证明：** 记

$$
L=\lim_{x\to0^+}\frac{f(x)}x<0.
$$

由 $f$ 在 $0$ 处连续，得

$$
f(0)=\lim_{x\to0^+}f(x)
=\lim_{x\to0^+}\left(x\frac{f(x)}x\right)=0.
$$

又由局部保号性，充分小的 $x>0$ 满足 $f(x)/x<0$，因而 $f(x)<0$。取这样的 $d\in(0,1)$，由 $f(d)<0<f(1)$ 及零点定理，存在 $b\in(d,1)$，使 $f(b)=0$。

在 $[0,b]$ 上对 $f$ 应用罗尔定理，由 $f(0)=f(b)=0$，存在 $c\in(0,b)$，使 $f'(c)=0$。

令

$$
F(x)=f(x)f'(x).
$$

由题设，$F$ 在 $[0,b]$ 上连续，在 $(0,b)$ 内可导，且

$$
F(0)=0,\qquad F(c)=0,\qquad F(b)=0.
$$

分别在 $[0,c]$ 和 $[c,b]$ 上对 $F$ 应用罗尔定理，存在

$$
\xi\in(0,c),\qquad\eta\in(c,b),
$$

使 $F'(\xi)=F'(\eta)=0$，即

$$
f(\xi)f''(\xi)+[f'(\xi)]^2=0,\qquad
f(\eta)f''(\eta)+[f'(\eta)]^2=0.
$$

因为 $0<\xi<c<\eta<b<1$，所以 $\xi,\eta$ 是所求方程在 $(0,1)$ 内的两个不同实根。

**要点：先用局部保号性和零点定理找 $f$ 的零点，再用罗尔定理找 $f'$ 的零点；两类零点共同构成 $F=ff'$ 的三个零点，最后分段使用罗尔定理。**

## 有限区间内导数有界推出函数有界（例 6.8）

**题目：** 若 $f(x)$ 在有限区间 $(a,b)$ 内可导，且 $f'(x)$ 有界，证明：$f(x)$ 在 $(a,b)$ 内有界。

**分析：** 遇到函数值与导数的关系，考虑拉格朗日中值定理。固定一个参考点 $x_0$，把任意 $f(x)$ 与固定值 $f(x_0)$ 联系起来。

**证明：** 因为 $f'$ 在 $(a,b)$ 内有界，存在常数 $K>0$，使

$$
|f'(t)|\le K,\qquad t\in(a,b).
$$

固定 $x_0\in(a,b)$。对任意 $x\in(a,b)$ 且 $x\ne x_0$，以 $x,x_0$ 为端点的闭区间包含于 $(a,b)$。$f$ 在这个闭区间上连续，在其内部可导，故由拉格朗日中值定理，存在介于 $x,x_0$ 之间的 $\xi$，使

$$
f(x)-f(x_0)=f'(\xi)(x-x_0).
$$

由三角不等式，

$$
\begin{aligned}
|f(x)|
&=\bigl|f(x_0)+f'(\xi)(x-x_0)\bigr|\\
&\le |f(x_0)|+|f'(\xi)|\,|x-x_0|\\
&\le |f(x_0)|+K|x-x_0|\\
&\le |f(x_0)|+K(b-a)=M.
\end{aligned}
$$

$x=x_0$ 时该估计也显然成立。由于 $M$ 为与 $x$ 无关的有限常数，故

$$
\boxed{|f(x)|\le M\quad\text{对所有 }x\in(a,b)\text{ 成立}},
$$

即 $f$ 在 $(a,b)$ 内有界。

**要点：不需要 $f$ 在端点 $a,b$ 有定义；在开区间内部截取闭区间即可使用中值定理。参考点 $x_0$ 必须固定，所得界 $M$ 不能依赖待估计的 $x$。**

**有限区间条件不能省略：** 在 $(0,+\infty)$ 上，$f(x)=x$ 的导数恒为 $1$，但函数无界。

## 构造乘积与商比较函数值（例 6.10）

**题目：** 设函数 $f(x)$ 满足 $f(0)=0$，且当 $x>0$ 时，

$$
f(x)<0,\qquad f'(x)<0,\qquad f''(x)>0.
$$

则当 $0<a<x<b$ 时，有（　）。

- A. $xf(x)>af(a)$
- B. $bf(b)>xf(x)$
- C. $xf(a)>af(x)$
- D. $xf(b)>bf(x)$

**解：选 D。**

**① 比较乘积，令 $g(x)=xf(x)$。** 当 $x>0$ 时，

$$
g'(x)=f(x)+xf'(x)<0.
$$

因此 $g$ 严格递减，由 $0<a<x<b$ 得

$$
g(b)<g(x)<g(a),
$$

即

$$
\boxed{bf(b)<xf(x)<af(a)}.
$$

所以 **A、B 均错误** 。

**② 比较交叉乘积，令 $h(x)=f(x)/x$。** 当 $x>0$ 时，

$$
h'(x)=\frac{xf'(x)-f(x)}{x^2}.
$$

分子是两个负数之差，不能仅由 $f<0$、$f'<0$ 判断符号，需要利用 $f''>0$，即 $f'$ 严格递增。

按教材在 $0$ 处连续的默认情形，对 $f$ 在 $[0,x]$ 上应用拉格朗日中值定理，存在 $\xi\in(0,x)$，使

$$
f(x)=f(x)-f(0)=xf'(\xi).
$$

由 $f''>0$，有 $f'(x)>f'(\xi)$，所以

$$
h'(x)=\frac{f'(x)-f'(\xi)}x>0.
$$

因此 $h$ 严格递增，由 $0<a<x<b$ 得

$$
\frac{f(a)}a<\frac{f(x)}x<\frac{f(b)}b.
$$

由于 $a,x,b$ 都为正，交叉相乘不改变不等号方向，得到

$$
\boxed{xf(a)<af(x),\qquad bf(x)<xf(b)}.
$$

所以 **C 错误，D 正确** 。

**要点：看到 $xf(x)$ 型乘积，构造 $g(x)=xf(x)$；看到 $xf(a)$ 与 $af(x)$ 型交叉乘积，先除以正数 $ax$，转成 $f(a)/a$ 与 $f(x)/x$ 的比较。商的导数符号不明显时，可用中值定理把函数增量换成导数。**

**严谨性补充：题面只写 $f(0)=0$，并不能单独保证在 $0$ 处连续。** 上面的教材证明在 $[0,x]$ 上使用中值定理需要这一条件。不过本题即使不补连续性，结论仍然成立，可这样证明 $h'>0$：

因为 $f$ 在 $(0,+\infty)$ 上递减且为负，右极限

$$
L=\lim_{t\to0^+}f(t)
$$

存在且为有限数，满足 $L\le0$。固定 $x>0$，对任意 $0<t<x$，由中值定理和 $f'$ 严格递增，

$$
f(x)-f(t)=f'(\eta)(x-t)<f'(x)(x-t),\qquad\eta\in(t,x).
$$

令 $t\to0^+$，得 $f(x)-L\le xf'(x)$。因此，记

$$
q(x)=xf'(x)-f(x),
$$

则对所有 $x>0$ 都有 $q(x)\ge-L\ge0$。又

$$
q'(x)=xf''(x)>0,
$$

所以 $q(x)>q(x/2)\ge0$，从而 $h'(x)=q(x)/x^2>0$。这也证明了原题条件下的结论。

## 原函数与定积分的存在性（例 8.3）

**题目：** 在区间 $[-1,2]$ 上，有以下四个结论：

① 函数

$$
f(x)=\begin{cases}
2,&x>0,\\
1,&x=0,\\
-1,&x<0
\end{cases}
$$

有原函数，但其定积分不存在。

② 函数

$$
f(x)=\begin{cases}
2x\sin\dfrac1{x^2}-\dfrac2x\cos\dfrac1{x^2},&x\ne0,\\
0,&x=0
\end{cases}
$$

有原函数，其定积分也存在。

③ 函数

$$
f(x)=\begin{cases}
\dfrac1x,&x\ne0,\\
0,&x=0
\end{cases}
$$

没有原函数，其定积分也不存在。

④ 函数

$$
f(x)=\begin{cases}
2x\cos\dfrac1x+\sin\dfrac1x,&x\ne0,\\
0,&x=0
\end{cases}
$$

有原函数，其定积分也存在。

正确结论的个数为（　）。

- A. $1$
- B. $2$
- C. $3$
- D. $4$

**解：** 本题的定积分指闭区间上的普通黎曼积分。

**① 错误：没有原函数，但定积分存在。** $x=0$ 是跳跃间断点，而导数具有介值性，不能出现跳跃间断点，所以 $f$ 在该区间上没有原函数。另一方面，$f$ 有界且只有一个间断点，故定积分存在，且

$$
\int_{-1}^2f(x)\,dx
=\int_{-1}^0(-1)\,dx+\int_0^2 2\,dx=3.
$$

**② 错误：有原函数，但定积分不存在。** 令

$$
F(x)=\begin{cases}
x^2\sin\dfrac1{x^2},&x\ne0,\\
0,&x=0.
\end{cases}
$$

当 $x\ne0$ 时直接求导得 $F'(x)=f(x)$；在 $0$ 处，

$$
F'(0)=\lim_{h\to0}\frac{F(h)-F(0)}h
=\lim_{h\to0}h\sin\frac1{h^2}=0=f(0).
$$

故 $F$ 是 $f$ 的原函数。但取 $x_n=1/\sqrt{2n\pi}\to0^+$，有

$$
f(x_n)=-\frac2{x_n}\to-\infty,
$$

所以 $f$ 在 $0$ 的邻域内无界，不满足黎曼可积的必要条件。

**③ 正确：没有原函数，定积分也不存在。** $f$ 在 $0$ 附近无界，故普通定积分不存在。若存在原函数 $F$，则在 $(0,2)$ 上必有

$$
F(x)=\ln x+C.
$$

当 $x\to0^+$ 时 $F(x)\to-\infty$，与 $F$ 在 $0$ 处可导从而连续矛盾，所以不存在跨越 $0$ 的原函数。

**④ 正确：有原函数，定积分也存在。** 令

$$
F(x)=\begin{cases}
x^2\cos\dfrac1x,&x\ne0,\\
0,&x=0.
\end{cases}
$$

当 $x\ne0$ 时 $F'(x)=f(x)$，且

$$
F'(0)=\lim_{h\to0}h\cos\frac1h=0=f(0).
$$

故 $F$ 是原函数。又在 $[-1,2]$ 上，

$$
|f(x)|\le2|x|+1\le5,
$$

且只有 $0$ 一个间断点，因此定积分存在。

综上，只有③④正确，共 $\boxed{2}$ 个，选 **B** 。

**要点：有原函数与黎曼可积不能相互推出。导数可以有振荡间断点；普通定积分存在则要求被积函数有界，不能直接用原函数代入端点来断言积分存在。**

## 函数与反函数的积分不等式（例 8.4）

**题目：** 设可导函数 $y=f(x)$ 在 $[0,+\infty)$ 上的值域是 $[0,+\infty)$，$f(0)=0$，$f'(x)>0$，$x=\varphi(y)$ 是 $y=f(x)$ 的反函数。记

$$
I=\int_0^a f(x)\,dx+\int_0^b\varphi(y)\,dy,
$$

其中常数 $a,b>0$。当 $a<\varphi(b)$ 时，则（　）。

- A. $I>ab$
- B. $I<ab$
- C. $I=ab$
- D. $I$ 与 $ab$ 的大小关系不确定

**解：** 因 $f$ 严格递增，$a<\varphi(b)$ 等价于 $f(a)<b$。函数与反函数的面积关系给出

$$
\int_0^a f(x)\,dx+\int_0^{f(a)}\varphi(y)\,dy=af(a).
$$

于是

$$
\begin{aligned}
I-ab
&=af(a)+\int_{f(a)}^b\varphi(y)\,dy-ab\\
&=\int_{f(a)}^b[\varphi(y)-a]\,dy.
\end{aligned}
$$

当 $f(a)<y<b$ 时，$\varphi(y)>\varphi(f(a))=a$，因此上式严格大于 $0$，即

$$
\boxed{I>ab}.
$$

选 **A** 。

**几何理解：** 在同一坐标系中，$x=\varphi(y)$ 与 $y=f(x)$ 表示同一条曲线。两项积分所表示的面积之和，比宽为 $a$、高为 $b$ 的矩形面积多出一块正面积。

**要点：遇到函数与反函数的积分之和，先用 $\int_0^a f+\int_0^{f(a)}\varphi=af(a)$ 配对，再利用单调性判断剩余积分的符号。**

## 利用换元与积分保序性比较大小（例 8.10）

**题目：** 设

$$
M=\int_0^{\pi/2}\sin(\sin x)\,dx,\qquad
N=\int_0^{\pi/2}\cos(\cos x)\,dx,
$$

则（　）。

- A. $M<1<N$
- B. $M<N<1$
- C. $N<M<1$
- D. $1<M<N$

**解：** 当 $x\in(0,\pi/2]$ 时，$\sin x>0$。由 $\sin u<u$（$u>0$），有

$$
\sin(\sin x)<\sin x.
$$

因此

$$
M<\int_0^{\pi/2}\sin x\,dx=1.
$$

对 $N$ 作换元 $x=\pi/2-t$，得

$$
N=\int_0^{\pi/2}\cos(\sin t)\,dt.
$$

当 $t\in(0,\pi/2]$ 时，$0\le\sin t<t\le\pi/2$，而余弦函数在 $[0,\pi/2]$ 上严格递减，所以

$$
\cos(\sin t)>\cos t.
$$

故

$$
N>\int_0^{\pi/2}\cos t\,dt=1.
$$

综上，$\boxed{M<1<N}$，选 **A** 。

**要点：不必求出积分值，选择容易计算的比较对象即可。换元 $x=\pi/2-t$ 可将正弦与余弦互换，从而得到
$\int_0^{\pi/2}g(\sin x)\,dx=\int_0^{\pi/2}g(\cos x)\,dx$（积分存在时）。**

## 含指数因子的变上限积分有界性（例 8.14）

**题目：** 设 $a>0$，函数 $f(x)$ 在 $[0,+\infty)$ 内连续有界，$C$ 为任意常数。证明：

$$
y(x)=e^{-ax}\left[\int_0^x f(t)e^{at}\,dt+C\right]
$$

在 $[0,+\infty)$ 内有界。

**证明：** 由 $f$ 有界，存在常数 $M>0$，使对任意 $t\ge0$，都有 $|f(t)|\le M$。当 $x\ge0$ 时，由三角不等式及积分估计，

$$
\begin{aligned}
|y(x)|
&\le |C|e^{-ax}+e^{-ax}\left|\int_0^x f(t)e^{at}\,dt\right|\\
&\le |C|e^{-ax}+e^{-ax}\int_0^x|f(t)|e^{at}\,dt\\
&\le |C|e^{-ax}+Me^{-ax}\int_0^x e^{at}\,dt\\
&=|C|e^{-ax}+\frac Ma(1-e^{-ax})\\
&\le |C|+\frac Ma.
\end{aligned}
$$

最后一步使用了 $a>0$、$x\ge0$，从而 $0<e^{-ax}\le1$。因此

$$
\boxed{|y(x)|\le |C|+\frac Ma\qquad(x\ge0)},
$$

右端是与 $x$ 无关的有限常数，故 $y$ 有界。

**要点：证明有界时，先对整体取绝对值，再用 $|f(t)|\le M$ 估计积分。保留外面的 $e^{-ax}$ 与积分结果相乘，才能消去 $e^{ax}$ 的增长。实际上还可得到更紧的界 $|y(x)|\le\max\{|C|,M/a\}$。**

## 两端分别比较判断反常积分收敛（例 8.15）

**题目：** 设 $a>b>0$，反常积分 $\displaystyle\int_0^{+\infty}\frac1{x^a+x^b}\,dx$ 收敛，则（　）。

- A. $a>1$ 且 $b>1$
- B. $a>1$ 且 $b<1$
- C. $a<1$ 且 $a+b>1$
- D. $a<1$ 且 $b<1$

**解：** 在 $x=1$ 处分成两段，分别考察 $0$ 和 $+\infty$：

$$
\frac1{x^a+x^b}\sim
\begin{cases}
\dfrac1{x^b},&x\to0^+,\\
\dfrac1{x^a},&x\to+\infty.
\end{cases}
$$

由 $p$ 型积分的判别结论，前一段收敛当且仅当 $b<1$，后一段收敛当且仅当 $a>1$。两段都收敛才行，故 $\boxed{a>1,\ b<1}$，选 **B** 。

**要点：分母中，零点附近由较小指数项主导，无穷远处由较大指数项主导。**

## 判断反常积分中发散的一项（例 8.17）

**题目：** 以下反常积分发散的是（　）。

- A. $\displaystyle\int_1^{+\infty}\left[\ln\left(1+\frac1x\right)-\frac1{1+x}\right]\,dx$
- B. $\displaystyle\int_0^{+\infty}\frac{\ln x}{1+x^2}\,dx$
- C. $\displaystyle\int_{-1}^1\frac{dx}{\sin x}$
- D. $\displaystyle\int_{-\infty}^{+\infty}\frac{\sin x}{1+x^2}\,dx$

**解：选 C。**

- **A 收敛：** 当 $x\to+\infty$ 时，

  $$
  \ln\left(1+\frac1x\right)-\frac1{1+x}
  =\left(\frac1x-\frac1{2x^2}+O(x^{-3})\right)
  -\left(\frac1x-\frac1{x^2}+O(x^{-3})\right)
  \sim\frac1{2x^2}.
  $$

- **B 收敛：** 在 $0$ 附近，$\dfrac{|\ln x|}{1+x^2}\sim|\ln x|$；在 $+\infty$ 处，$\dfrac{\ln x}{1+x^2}\sim\dfrac{\ln x}{x^2}$。两端的比较积分均收敛，故绝对收敛。
- **C 发散：** $x=0$ 为瑕点，且 $\dfrac1{\sin x}\sim\dfrac1x$（$x\to0$），两侧积分分别发散。不能因被积函数为奇函数就把积分记为 $0$。
- **D 收敛：** $\left|\dfrac{\sin x}{1+x^2}\right|\le\dfrac1{1+x^2}$，而后者在整个实轴上的积分收敛，故绝对收敛。

## 展开后分部积分抵消（例 9.7）

**题目：** 计算不定积分 $\displaystyle\int e^{2x}(\tan x+1)^2\,dx$。

**解：** 由 $\tan^2x+1=\sec^2x$，展开后分部积分：

$$
\begin{aligned}
\int e^{2x}(\tan x+1)^2\,dx
&=\int e^{2x}\sec^2x\,dx+2\int e^{2x}\tan x\,dx\\
&=\int e^{2x}\,d(\tan x)+2\int e^{2x}\tan x\,dx\\
&=e^{2x}\tan x-2\int e^{2x}\tan x\,dx
+2\int e^{2x}\tan x\,dx\\
&=\boxed{e^{2x}\tan x+C}.
\end{aligned}
$$

**要点：展开平方并用 $\tan^2x+1=\sec^2x$，分部积分后两项恰好抵消。**

## 换元后利用奇偶性计算定积分（例 9.15）

**题目：** 计算 $\displaystyle\int_0^1x\arcsin\sqrt{4x-4x^2}\,dx$。

**分析：** 配方得 $4x-4x^2=1-(1-2x)^2$，令 $t=1-2x$，将积分区间化为 $[-1,1]$，再利用奇偶性。

**解：** 令 $t=1-2x$，则 $x=(1-t)/2$，$dx=-dt/2$，于是

$$
\begin{aligned}
I
&=\frac14\int_{-1}^1(1-t)\arcsin\sqrt{1-t^2}\,dt\\
&=\frac14\int_{-1}^1\arcsin\sqrt{1-t^2}\,dt
-\frac14\int_{-1}^1t\arcsin\sqrt{1-t^2}\,dt\\
&=\frac12\int_0^1\arcsin\sqrt{1-t^2}\,dt.
\end{aligned}
$$

这里 $\arcsin\sqrt{1-t^2}$ 为偶函数，$t\arcsin\sqrt{1-t^2}$ 为奇函数，故第二项为 $0$，第一项可化为半区间积分的两倍。

当 $0\le t\le1$ 时，$\arcsin\sqrt{1-t^2}=\arccos t$，所以

$$
\int_0^1\arcsin\sqrt{1-t^2}\,dt
=\int_0^1\arccos t\,dt
=\left[t\arccos t-\sqrt{1-t^2}\right]_0^1=1.
$$

因此 $\boxed{I=\frac12}$。

**要点：先配方，再换元得到对称区间；奇函数部分积分为零。恒等式 $\arcsin\sqrt{1-t^2}=\arccos t$ 在这里用于 $[0,1]$，不能直接套到整个 $[-1,1]$。**

## 区间再现消去 x 因子（例 9.18）

**题目：** 设 $f(x)$ 在 $[0,1]$ 上连续，证明

$$
\int_0^\pi xf(\sin x)\,dx
=\frac\pi2\int_0^\pi f(\sin x)\,dx,
$$

并计算 $\displaystyle\int_0^\pi x\sin^9x\,dx$。

**证明：** 记 $I=\displaystyle\int_0^\pi xf(\sin x)\,dx$。令 $x=\pi-t$，利用 $\sin(\pi-t)=\sin t$，得

$$
\begin{aligned}
I
&=\int_\pi^0(\pi-t)f[\sin(\pi-t)](-dt)\\
&=\int_0^\pi(\pi-t)f(\sin t)\,dt\\
&=\pi\int_0^\pi f(\sin t)\,dt-\int_0^\pi tf(\sin t)\,dt\\
&=\pi\int_0^\pi f(\sin x)\,dx-I.
\end{aligned}
$$

移项得

$$
\boxed{\int_0^\pi xf(\sin x)\,dx
=\frac\pi2\int_0^\pi f(\sin x)\,dx}.
$$

**计算：** 取 $f(u)=u^9$，再利用对称性和华里士公式：

$$
\begin{aligned}
\int_0^\pi x\sin^9x\,dx
&=\frac\pi2\int_0^\pi\sin^9x\,dx\\
&=\pi\int_0^{\pi/2}\sin^9x\,dx\\
&=\pi\cdot\frac89\cdot\frac67\cdot\frac45\cdot\frac23\\
&=\boxed{\frac{128\pi}{315}}.
\end{aligned}
$$

**要点：$f(\sin x)$ 关于 $x=\pi/2$ 对称，令 $x=\pi-t$ 后与原积分相加，即可把因子 $x$ 换成区间中点 $\pi/2$。**

## 构造变限积分求函数平均值（例 10.8）

**题目：** 设 $f(x)$ 连续，且

$$
f(x+2)-f(x)=x,\qquad \int_0^2 f(x)\,dx=0,
$$

求 $f(x)$ 在 $[1,3]$ 上的平均值。

**分析：** 先用函数平均值公式：

$$
\bar f=\frac1{3-1}\int_1^3 f(x)\,dx
=\frac12\int_1^3 f(x)\,dx.
$$

观察到已知积分区间 $[0,2]$ 与目标区间 $[1,3]$ 的长度均为 $2$，且函数关系中出现 $f(x+2)-f(x)$，因此构造长度固定、两端同时移动的变限积分。

**解：** 记

$$
F(x)=\int_x^{x+2}f(t)\,dt.
$$

由变限积分求导公式，

$$
F'(x)=f(x+2)-f(x)=x,
$$

故

$$
F(x)=\frac12x^2+C.
$$

由 $F(0)=\displaystyle\int_0^2f(t)\,dt=0$，得 $C=0$，于是

$$
\int_1^3f(x)\,dx=F(1)=\frac12.
$$

因此所求平均值为

$$
\boxed{\bar f=\frac12F(1)=\frac14}.
$$

**要点：看到 $f(x+h)-f(x)$，可考虑构造 $F(x)=\int_x^{x+h}f(t)\,dt$，使 $F'(x)=f(x+h)-f(x)$。本题无需求出 $f(x)$；求出积分后，还要除以区间长度，才是平均值。**

## 阿基米德螺线的弧长（例 10.11）

**题目：** 求阿基米德螺线 $r=\theta$ 上，$\theta$ 从 $0$ 到 $2\pi$ 一段的弧长。

**分析：** 这是极坐标曲线的弧长问题，使用 [公式笔记](formula.md) 中的极坐标弧长公式：

$$
s=\int_\alpha^\beta\sqrt{r^2(\theta)+[r'(\theta)]^2}\,\mathrm d\theta.
$$

**解：** 因为 $r(\theta)=\theta$，$r'(\theta)=1$，所以

$$
s=\int_0^{2\pi}\sqrt{\theta^2+1}\,\mathrm d\theta.
$$

使用原函数

$$
\int\sqrt{1+\theta^2}\,\mathrm d\theta
=\frac12\left[\theta\sqrt{1+\theta^2}
+\ln\left|\theta+\sqrt{1+\theta^2}\right|\right]+C,
$$

得

$$
\begin{aligned}
s
&=\left[\frac\theta2\sqrt{1+\theta^2}
+\frac12\ln\left(\theta+\sqrt{1+\theta^2}\right)\right]_0^{2\pi}\\
&=\boxed{\pi\sqrt{1+4\pi^2}
+\frac12\ln\left(2\pi+\sqrt{1+4\pi^2}\right)}.
\end{aligned}
$$

这里 $\theta\ge0$，对数真数为正；下限 $\theta=0$ 时，两项均为 $0$，因为 $\ln1=0$。

### 补充：原函数中的对数项怎样得到

对 $\sqrt{1+\theta^2}$，令 $\theta=\tan t$，取 $t\in(-\pi/2,\pi/2)$。本题对应 $0\le t\le\arctan(2\pi)$，于是

$$
\mathrm d\theta=\sec^2t\,\mathrm dt,
\qquad\sqrt{1+\theta^2}=\sqrt{1+\tan^2t}=\sec t.
$$

因此

$$
\int\sqrt{1+\theta^2}\,\mathrm d\theta=\int\sec^3t\,\mathrm dt.
$$

记 $J=\int\sec^3t\,\mathrm dt$，取 $u=\sec t$、$\mathrm dv=\sec^2t\,\mathrm dt$，分部积分并整理：

$$
\begin{aligned}
J
&=\sec t\tan t-\int\sec t\tan^2t\,\mathrm dt\\
&=\sec t\tan t-\int\sec t(\sec^2t-1)\,\mathrm dt\\
&=\sec t\tan t-J+\int\sec t\,\mathrm dt.
\end{aligned}
$$

利用 $\int\sec t\,\mathrm dt=\ln|\sec t+\tan t|+C$，得

$$
J=\frac12\sec t\tan t+\frac12\ln|\sec t+\tan t|+C.
$$

再由 $\tan t=\theta$、$\sec t=\sqrt{1+\theta^2}$ 反换元，即得到上面的原函数。

**要点：先认准求弧长，用 $\sqrt{r^2+(r')^2}$，不能套极坐标面积公式 $\frac12\int r^2\,\mathrm d\theta$。计算 $\int\sqrt{1+\theta^2}\,\mathrm d\theta$ 时，可用 $\theta=\tan t$ 化为 $\int\sec^3t\,\mathrm dt$，分部积分后移项求出。**

## 含高斯积分的二元函数求导（例 13.5）

**题目：** 设函数

$$
f(x,y)=\int_0^{xy}e^{-xt^2}\,\mathrm dt,
$$

求 $f'_x(1,+\infty)$。

**解：** 记 $f(x,+\infty)=\displaystyle\lim_{y\to+\infty}f(x,y)$。在 $x=1$ 附近有 $x>0$，令

$$
u=\sqrt{x}\,t,\qquad
t=\frac{u}{\sqrt{x}},\qquad
\mathrm dt=\frac1{\sqrt{x}}\,\mathrm du,
$$

则上限 $t=xy$ 对应 $u=x^{3/2}y$，所以

$$
f(x,y)=\frac1{\sqrt{x}}\int_0^{x^{3/2}y}e^{-u^2}\,\mathrm du.
$$

固定 $x>0$，当 $y\to+\infty$ 时，$x^{3/2}y\to+\infty$。利用高斯积分

$$
\int_0^{+\infty}e^{-u^2}\,\mathrm du=\frac{\sqrt{\pi}}2,
$$

得

$$
f(x,+\infty)=\frac1{\sqrt{x}}\int_0^{+\infty}e^{-u^2}\,\mathrm du
=\frac{\sqrt{\pi}}{2\sqrt{x}}.
$$

再对 $x$ 求导，并代入 $x=1$：

$$
f'_x(1,+\infty)
=\left.\frac{\mathrm d}{\mathrm dx}\left(\frac{\sqrt{\pi}}{2\sqrt{x}}\right)\right|_{x=1}
=\left.-\frac{\sqrt{\pi}}{4x^{3/2}}\right|_{x=1}
=\boxed{-\frac{\sqrt{\pi}}4}.
$$

**要点：令 $u=\sqrt{x}\,t$，把 $e^{-xt^2}$ 化为标准形式 $e^{-u^2}$；换元时同时改写微分和积分上限。先求出 $f(x,+\infty)$ 的表达式，再求它在 $x=1$ 处的导数。**

## 二元复合函数的二阶偏导数（例 13.9）

**题目：** 设

$$
z=f(e^x\sin y,\ x^2+y^2),
$$

其中 $f$ 具有二阶连续偏导数，且 $f'_1(0,0)=1$、$f'_2(0,0)=-1$。求

$$
\left.\frac{\partial^2z}{\partial x\,\partial y}\right|_{(0,0)}.
$$

| 选项 | A | B | C | D |
| --- | --- | --- | --- | --- |
| 数值 | $0$ | $1$ | $2$ | $-1$ |

**解：** 令

$$
u=e^x\sin y,\qquad v=x^2+y^2,
$$

其中 $u$ 是 $f$ 的第一个位置，$v$ 是第二个位置。由链式法则，

$$
\frac{\partial z}{\partial x}
=e^x\sin y\,f'_1(u,v)+2x\,f'_2(u,v).
$$

再对 $y$ 求偏导，既要对乘在外面的系数求导，也要对 $f'_1,f'_2$ 求导：

$$
\begin{aligned}
\frac{\partial}{\partial y}\left(\frac{\partial z}{\partial x}\right)
={}&e^x\cos y\,f'_1(u,v)\\
&+e^x\sin y\left[e^x\cos y\,f''_{11}(u,v)+2y\,f''_{12}(u,v)\right]\\
&+2x\left[e^x\cos y\,f''_{21}(u,v)+2y\,f''_{22}(u,v)\right].
\end{aligned}
$$

在 $(x,y)=(0,0)$ 处，$u=v=0$，且

$$
e^x\sin y=0,\qquad 2x=0,\qquad e^x\cos y=1.
$$

因此含二阶偏导数的项全部消失。又因 $f$ 的二阶偏导数连续，混合偏导的次序可交换，故

$$
\left.\frac{\partial^2z}{\partial x\,\partial y}\right|_{(0,0)}
=f'_1(0,0)=\boxed{1},
$$

选 **B** 。

**要点：$f'_1,f'_2$ 表示对外层函数的第一个、第二个位置求偏导。连续求两次偏导时，每次都要使用乘积法则和链式法则；求导后再代入指定点，可利用为零的系数简化。**

## 沿曲线的复合函数求导与偏导数（例 13.10）

**题目：** 设

$$
f(x,e^x)=x+e^x,
\qquad
\left.f'_x(x,y)\right|_{y=e^x}=1+2e^x,
$$

求 $\displaystyle\left.f'_y(x,y)\right|_{y=e^x}$。

**解：** 对恒等式 $f(x,e^x)=x+e^x$ 两边关于 $x$ 求导。左侧是两个位置都随 $x$ 变化的复合函数，因此

$$
\frac{\mathrm d}{\mathrm dx}f(x,e^x)
=\left.f'_x(x,y)\right|_{y=e^x}
+\left.f'_y(x,y)\right|_{y=e^x}\,e^x
=1+e^x.
$$

代入已知的偏导数值，得

$$
1+2e^x+\left.f'_y(x,y)\right|_{y=e^x}\,e^x=1+e^x.
$$

因为 $e^x>0$，所以

$$
\boxed{\left.f'_y(x,y)\right|_{y=e^x}=-1}.
$$

**要点：$\left.f'_x(x,y)\right|_{y=e^x}$ 是先把 $y$ 当作独立变量求偏导，再代入 $y=e^x$；$\frac{\mathrm d}{\mathrm dx}f(x,e^x)$ 则必须包含第二个位置变化产生的链式法则项。**

**不能由 $f(x,e^x)=x+e^x$ 推出 $f(x,y)=x+y$。** 题目只给出了曲线 $y=e^x$ 上的函数值；沿该曲线相等的二元函数，在曲线外可以不同。

## 由全微分还原函数并判断极值（13.5）

**题目：** 设 $z_1=|x+y|$，$\mathrm dz_2=(3x^2+6x)\,\mathrm dx-(3y^2-6y)\,\mathrm dy$，则点 $(0,0)$（　）。

- A. 不是 $z_1$ 的极值点，也不是 $z_2$ 的极值点
- B. 是 $z_1$ 的极大值点，也是 $z_2$ 的极大值点
- C. 是 $z_1$ 的极小值点，是 $z_2$ 的极大值点
- D. 是 $z_1$ 的极小值点，也是 $z_2$ 的极小值点

**解：选 D。** 因为

$$
z_1(x,y)=|x+y|\ge0=z_1(0,0),
$$

所以原点是 $z_1$ 的极小值点。沿 $y=-x$ 时等号恒成立，故是**非严格极小值点** ；虽然原点处两个一阶偏导数均不存在，仍可由定义判断极值。

由全微分还原得

$$
z_2(x,y)=x^3+3x^2-y^3+3y^2+C.
$$

因此

$$
z_2(x,y)-z_2(0,0)=x^2(3+x)+y^2(3-y).
$$

当 $|x|<1$、$|y|<1$ 时，上式在非原点处严格大于 $0$，故原点是 $z_2$ 的严格极小值点。

也可用二阶判别法：原点处 $z_{2x}=z_{2y}=0$，且 $A=6$、$B=0$、$C=6$，故 $AC-B^2=36>0$、$A>0$，得到同样结论。

**要点：不可偏导的点也可能是极值点；由全微分还原函数时保留加法常数，比较函数值之差即可消去常数。**

## 二阶可导函数在极大值点的必要条件（例 5.2）

**题目：** 设函数 $f(x)$ 二阶可导，且在 $x=x_0$ 处取得极大值，则有（　）。

- A. $f''(x_0)<0$
- B. $f''(x_0)\le0$
- C. $f''(x_0)>0$
- D. $f''(x_0)\ge0$

**解：选 B。** 这里 $x_0$ 为定义域内点。由极值的必要条件，$f'(x_0)=0$。若 $f''(x_0)>0$，二阶导数判别法将推出该点为严格极小值点，与极大值矛盾，因此

$$
\boxed{f''(x_0)\le0}.
$$

等号可以成立：$f(x)=-x^4$ 在 $0$ 处取得极大值，但 $f''(0)=0$，所以不能选 A。

**要点：极大值加二阶可导，只能推出二阶导数非正；“驻点且二阶导数严格负”是极大值的充分条件。**

## 利用被积函数的正负性比较二重积分（例 14.1）

**题目：** 设平面闭区域 $D_i$（$i=1,2,3,4$）分别由下列曲线围成：

$$
\begin{aligned}
L_1&:\quad x^2+y^2=1,\\
L_2&:\quad x^2+y^2=2,\\
L_3&:\quad x^2+2y^2=2,\\
L_4&:\quad 2x^2+y^2=2.
\end{aligned}
$$

记

$$
I_i=\iint_{D_i}\left(1-x^2-\frac12y^2\right)\,\mathrm dx\,\mathrm dy,
$$

则 $\max\{I_1,I_2,I_3,I_4\}=$（　）。

| 选项 | A | B | C | D |
| --- | --- | --- | --- | --- |
| 积分 | $I_1$ | $I_2$ | $I_3$ | $I_4$ |

**解：选 D。** 令

$$
f(x,y)=1-x^2-\frac12y^2.
$$

由 $f(x,y)=0$ 得 $2x^2+y^2=2$，恰为 $D_4$ 的边界。因此

$$
\begin{cases}
f(x,y)>0, & (x,y)\text{ 在 }D_4\text{ 内部},\\
f(x,y)=0, & (x,y)\text{ 在 }D_4\text{ 边界上},\\
f(x,y)<0, & (x,y)\text{ 在 }D_4\text{ 外部}.
\end{cases}
$$

**比较 $I_1$ 与 $I_4$：** 因 $D_1\subset D_4$，增加的区域位于 $f>0$ 的范围内，故

$$
I_4-I_1=\iint_{D_4\setminus D_1}f(x,y)\,\mathrm dx\,\mathrm dy>0.
$$

**比较 $I_2$ 与 $I_4$：** 因 $D_4\subset D_2$，增加的区域位于 $f<0$ 的范围内，故

$$
I_2-I_4=\iint_{D_2\setminus D_4}f(x,y)\,\mathrm dx\,\mathrm dy<0.
$$

**比较 $I_3$ 与 $I_4$：** 两个椭圆区域互不包含，先消去公共区域 $D_3\cap D_4$，再比较各自多出的部分：

$$
\begin{aligned}
I_4-I_3
&=\iint_{D_4\setminus D_3}f(x,y)\,\mathrm dx\,\mathrm dy
-\iint_{D_3\setminus D_4}f(x,y)\,\mathrm dx\,\mathrm dy\\
&>0.
\end{aligned}
$$

其中第一项在 $D_4$ 内部积分，为正；第二项在 $D_4$ 外部积分，为负。两块差集都有正面积，所以相减后严格为正。

综上，

$$
\boxed{\max\{I_1,I_2,I_3,I_4\}=I_4}.
$$

**要点：同一被积函数在不同区域上的积分比较，先看函数的正负性，再看区域的包含关系。** 本题的 $D_4$ 恰好包含全部正值区域、排除全部负值区域；扩大到负值区域会减小积分，删去正值区域也会减小积分。区域互不包含时，先消去交集，再比较两个差集上的积分，无需直接计算二重积分。

## 设 u = x + y、v = y 计算二重积分（例 14.15）

**题目：** 设平面区域

$$
D=\{(x,y)\mid 0\le x\le1-y,\ 0\le y\le1\},
$$

计算

$$
I=\iint_De^{\frac{y}{x+y}}\,\mathrm d\sigma.
$$

**解：按 $u=x+y,\ v=y$ 换元。** 由

$$
u=x+y,\qquad v=y,
$$

得反变换

$$
x=u-v,\qquad y=v,
$$

且雅可比的绝对值为

$$
\left|\frac{\partial(x,y)}{\partial(u,v)}\right|
=\left|\begin{vmatrix}1&-1\\0&1\end{vmatrix}\right|=1,
\qquad \mathrm dx\,\mathrm dy=\mathrm du\,\mathrm dv.
$$

将原区域的条件代入，得到

$$
0\le u-v\le1-v,\qquad 0\le v\le1,
$$

即 $v\le u\le1$、$0\le v\le1$。为先对 $v$ 积分，改写为

$$
\boxed{D'=\{(u,v)\mid0\le u\le1,\ 0\le v\le u\}}.
$$

这是 $uv$ 平面上由 $v=0$、$v=u$、$u=1$ 围成的三角形。又 $y/(x+y)=v/u$，故

$$
\begin{aligned}
I
&=\iint_{D'}e^{v/u}\,\mathrm du\,\mathrm dv\\
&=\int_0^1\mathrm du\int_0^u e^{v/u}\,\mathrm dv\\
&=\int_0^1\left[u e^{v/u}\right]_{v=0}^{v=u}\,\mathrm du\\
&=\int_0^1u(e-1)\,\mathrm du\\
&=(e-1)\left[\frac{u^2}{2}\right]_0^1
=\boxed{\frac{e-1}{2}}.
\end{aligned}
$$

**要点：对 $v$ 积分时，$u$ 是常数，$\int e^{v/u}\,\mathrm dv=u e^{v/u}+C$，不要漏掉系数 $u$。** 换元后先写出区域 $0\le v\le u\le1$，再确定累次积分的上下限。

原点处被积函数未定义，可任意补定义；单个点的取值不影响积分。

## 交换 x、y 求一阶线性方程的特解（例 15.8）

**题目：** 微分方程

$$
y\,\mathrm dx+(x-3y^2)\,\mathrm dy=0
$$

满足初始条件 $y(1)=1$，求 $y$。

**选法：** 直接写成 $y'=y/(3y^2-x)$ 不便求解；把 $x$ 看成 $y$ 的函数，方程对 $x$ 为一阶线性。

**解：** 在初始点附近 $y\ne0$，将方程整理为

$$
\frac{\mathrm dx}{\mathrm dy}+\frac1y x=3y.
$$

利用一阶线性方程通解公式，取积分因子 $y$，得

$$
x=\frac1y\left(\int3y^2\,\mathrm dy+C\right)
=y^2+\frac Cy.
$$

代入 $x=1,y=1$，得到 $C=0$，所以 $x=y^2$，即 $y=\pm\sqrt{x}$。由 $y(1)=1$ 选择正分支，故

$$
\boxed{y=\sqrt{x}},\qquad x>0.
$$

**要点：初始条件既确定任意常数，也确定解的分支。** 遇到关于 $y(x)$ 难处理、关于 $x(y)$ 却线性的方程，可交换自变量与因变量。

## 一阶线性方程的解在无穷远处的极限（例 15.9）

**题目：** 设 $y=\varphi(x)$ 是微分方程

$$
y'+ey=\left(1-\frac1x\right)^x
$$

的一个解，求 $\displaystyle\lim_{x\to+\infty}\varphi(x)$。

选项为：A. $e$；B. $e^2$；C. $1/e$；D. $1/e^2$。

**选法：** 先用一阶线性通解表示 $\varphi(x)$，再把极限化为可用洛必达法则处理的比值。

**解：** 令

$$
h(x)=\left(1-\frac1x\right)^x,\qquad
\lim_{x\to+\infty}h(x)=e^{-1}.
$$

在解所在区间中固定 $x_0>1$，由线性方程的通解可写成

$$
\varphi(x)=e^{-ex}\left[C+\int_{x_0}^{x}e^{et}h(t)\,\mathrm dt\right]
=\frac{C+\displaystyle\int_{x_0}^{x}e^{et}h(t)\,\mathrm dt}{e^{ex}}.
$$

当 $x\to+\infty$ 时，分子、分母均趋于 $+\infty$。由洛必达法则及变上限积分求导，得到

$$
\begin{aligned}
\lim_{x\to+\infty}\varphi(x)
&=\lim_{x\to+\infty}\frac{e^{ex}h(x)}{e\,e^{ex}}\\
&=\frac1e\lim_{x\to+\infty}\left(1-\frac1x\right)^x\\
&=\boxed{\frac1{e^2}}.
\end{aligned}
$$

故选 **D** 。任意常数项 $Ce^{-ex}\to0$，所以结果不依赖具体选取的解。

**要点：先解方程，再求极限；不能未经论证就直接设 $\varphi'(x)\to0$。** 用定下限的积分表示原函数，还能明确洛必达法则中分子的求导过程。

## 由已知解反求四阶常系数齐次方程（例 15.19）

**题目：** 已知某四阶常系数齐次线性微分方程有特解

$$
y_1(x)=e^x\cos2x,\qquad y_2(x)=x,
$$

且方程中 $y^{(4)}$ 前的系数为 $1$，求该微分方程。

**选法：** 由解的形式识别特征根及其最低重数，再用“四阶”确定全部根。

**解：** 由 $e^x\cos2x$ 可知，特征方程必须包含一对共轭复根

$$
r=1\pm2i.
$$

又因为 $x=xe^{0x}$ 是解，$r=0$ 必须至少为二重根。上述根按重数已占满四阶方程的四个根，故特征多项式为

$$
\begin{aligned}
F(r)
&=r^2[r-(1+2i)][r-(1-2i)]\\
&=r^2[(r-1)^2+4]\\
&=r^4-2r^3+5r^2.
\end{aligned}
$$

由最高阶系数为 $1$，得到所求方程

$$
\boxed{y^{(4)}-2y^{(3)}+5y''=0}.
$$

**要点：解中出现 $x$，对应的是 $0$ 至少为二重根。** 一般地，出现 $x^{k-1}e^{rx}$，说明 $r$ 至少为 $k$ 重根；已知方程阶数后，要核对根的总重数。

## 欧拉方程化为常系数方程（例 15.20）

**题目：** 求欧拉方程

$$
x^2\frac{\mathrm d^2y}{\mathrm dx^2}
+4x\frac{\mathrm dy}{\mathrm dx}+2y=0,
\qquad x>0
$$

的通解。

**选法：** 二阶、一次、零次导数的系数依次带 $x^2,x,1$，属于欧拉方程，令 $t=\ln x$ 化为常系数方程。

**解：** 令 $x=e^t$，记 $Y(t)=y(e^t)$。由

$$
xy'=Y',\qquad x^2y''=Y''-Y',
$$

原方程化为

$$
Y''-Y'+4Y'+2Y=0,
\quad\text{即}\quad Y''+3Y'+2Y=0.
$$

其特征方程为

$$
r^2+3r+2=(r+1)(r+2)=0,
$$

得到 $r_1=-1,r_2=-2$，所以

$$
Y(t)=C_1e^{-t}+C_2e^{-2t}.
$$

代回 $t=\ln x$，得

$$
\boxed{y=\frac{C_1}{x}+\frac{C_2}{x^2}},\qquad x>0.
$$

**快捷方法：** 直接试取 $y=x^r$，得到

$$
r(r-1)+4r+2=r^2+3r+2=0,
$$

同样可写出上述通解。

**要点：欧拉方程换元后，一阶导数的系数由 $p$ 变为 $p-1$；求解结束后要把 $t$ 换回 $\ln x$。**
