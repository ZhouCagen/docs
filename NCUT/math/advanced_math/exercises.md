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

与已知矛盾。因此 $\boxed{\lim_{n\to\infty}x_n=0}$，选 **A**。

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
