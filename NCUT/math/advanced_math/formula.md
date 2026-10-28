# 高等数学公式笔记

**知识点目录**

- [第一部分：函数、极限、连续](#section-1)
  - [复合函数的奇偶性](#section-1-1)
  - [反三角函数的定义域与值域](#section-1-2)
  - [数列极限](#section-1-3)
  - [函数极限的 24 种定义](#section-1-4)
  - [极限存在的等价表述](#section-1-5)
  - [极限的局部保号性](#section-1-6)
  - [有界性常用结论](#section-1-7)
  - [无穷小的比较](#section-1-8)
  - [常用等价无穷小](#section-1-9)
  - [小 o 的运算规则](#section-1-10)
  - [五个函数的大小关系与三阶差值](#section-1-11)
  - [常见无穷大的增长速度比较](#section-1-12)
  - [常见极限](#section-1-13)
  - [连续性的性质](#section-1-14)
  - [间断点分类](#section-1-15)
- [第二部分：一元函数微分学及其应用](#section-2)
  - [函数在一点可导的充要条件](#section-2-1)
  - [基本求导公式](#section-2-2)
  - [莱布尼茨公式](#section-2-3)
  - [反函数求导公式与 arcsin x 的求导](#section-2-4)
  - [罗尔定理与推广](#section-2-5)
  - [拉格朗日中值定理](#section-2-6)
  - [柯西中值定理](#section-2-7)
  - [泰勒公式与两种余项](#section-2-8)
  - [截断为有限阶泰勒公式](#section-2-9)
  - [驻点、导数符号、极值点与单调性的关系](#section-2-10)
  - [一元函数极值的必要条件](#section-2-11)
  - [极值的二阶导数判别法](#section-2-12)
  - [极值的高阶导数判别法](#section-2-13)
  - [曲线的凹凸性](#section-2-14)
  - [斜渐近线](#section-2-15)
  - [曲率与曲率半径](#section-2-16)
- [第三部分：一元函数积分学及其应用](#section-3)
  - [原函数的存在性](#section-3-1)
  - [常用不定积分公式](#section-3-2)
  - [有理函数积分：部分分式分解](#section-3-3)
  - [定积分存在的充分条件](#section-3-4)
  - [定积分的极限表达式](#section-3-5)
  - [定积分的保号性、保序性与绝对值不等式](#section-3-6)
  - [周期函数在一个周期内的积分](#section-3-7)
  - [区间再现公式](#section-3-8)
  - [正弦、余弦幂次的定积分](#section-3-9)
  - [定积分的估值定理](#section-3-10)
  - [积分中值定理](#section-3-11)
  - [变上限积分求导](#section-3-12)
  - [区间内部有瑕点的反常积分](#section-3-13)
  - [由无穷远处的函数极限初步判断积分敛散性](#section-3-14)
  - [两类常用的 p 型积分](#section-3-15)
  - [反常积分小常识：对数、幂函数与指数函数的增长比较](#section-3-16)
  - [反常积分的比较判别法](#section-3-17)
  - [反常积分比较判别法的极限形式](#section-3-18)
  - [反常积分的绝对收敛与条件收敛](#section-3-19)
  - [狄利克雷判别法](#section-3-20)
  - [定积分的几何应用：平面图形的面积](#section-3-21)
  - [旋转体体积：柱壳法](#section-3-22)
  - [绕任意定直线旋转的体积](#section-3-23)
  - [平面曲边梯形的形心坐标](#section-3-24)
  - [平面曲线的弧长](#section-3-25)
  - [旋转曲面的面积](#section-3-26)
- [第四部分：多元函数微分学](#section-4)
  - [二重极限的判断：直线、幂曲线与极坐标](#section-4-1)
  - [全增量、可微与全微分](#section-4-2)
  - [可微的必要条件、充分条件与判别步骤](#section-4-3)
  - [一元函数与多元函数的性质关系](#section-4-4)
  - [区域内全微分恒为零](#section-4-5)
  - [复合函数求导与“位置”记号](#section-4-6)
  - [隐函数求导公式](#section-4-7)
  - [二元函数的无条件极值](#section-4-8)
  - [方向导数：先将方向向量单位化](#section-4-9)
  - [梯度与方向导数的最大值](#section-4-10)
  - [向量场的散度与旋度](#section-4-11)
- [第五部分：重积分](#section-5)
  - [被积函数为 1：二重积分等于区域面积](#section-5-1)
  - [二重积分的保序性与保号性](#section-5-2)
  - [二重积分的估值定理](#section-5-3)
  - [二重积分的中值定理](#section-5-4)
  - [二重积分的对称性](#section-5-5)
  - [二重积分的轮换对称性](#section-5-6)
  - [二重积分的一般换元公式与雅可比行列式](#section-5-7)
  - [二重积分的极坐标换元](#section-5-8)
- [第六部分：微分方程](#section-6)
  - [考试选法：先看阶数，再看结构](#section-6-1)
  - [可分离变量方程与丢解检查](#section-6-2)
  - [齐次型微分方程：令 u = y/x](#section-6-3)
  - [一阶线性微分方程的通解](#section-6-4)
  - [交换自变量与因变量：把 x 看成 y 的函数](#section-6-5)
  - [伯努利方程：令 z = y 的 1−n 次方](#section-6-6)
  - [二阶可降阶微分方程](#section-6-7)
  - [全微分方程](#section-6-8)
  - [二阶常系数齐次线性微分方程](#section-6-9)
  - [线性微分方程解的结构与叠加原理](#section-6-10)
  - [待定系数法：指数乘多项式](#section-6-11)
  - [待定系数法：指数乘正弦、余弦及多项式](#section-6-12)
  - [n 阶常系数齐次线性方程：由特征根写通解](#section-6-13)
  - [欧拉方程：令 t = ln|x|](#section-6-14)
- [第七部分：无穷级数](#section-7)
  - [无穷级数与部分和：用部分和的极限定义级数的和](#section-7-1)
  - [等比级数](#section-7-2)
  - [无穷级数的基本性质](#section-7-3)
  - [正项级数及其敛散性判别](#section-7-4)
  - [调和级数与相邻项的调和平均数](#section-7-5)
  - [p 级数及其敛散性](#section-7-6)
  - [交错级数与莱布尼茨判别法](#section-7-7)
  - [绝对收敛与条件收敛](#section-7-8)
  - [交错 p 级数的敛散性](#section-7-9)
  - [函数项级数、收敛点与收敛域](#section-7-10)
  - [幂级数的定义与系数](#section-7-11)
  - [幂级数的阿贝尔定理：收敛点以内绝对收敛](#section-7-12)
  - [幂级数的收敛半径与端点](#section-7-13)
  - [不缺项幂级数：由系数求收敛半径](#section-7-14)
  - [缺项幂级数：对完整通项使用比值法或根值法](#section-7-15)
  - [一般函数项级数：绝对值判别后的补充检查](#section-7-16)
  - [幂级数的运算法则](#section-7-17)
  - [幂级数的恒等变形](#section-7-18)
  - [幂级数变形：收敛半径与收敛域的变化](#section-7-19)
  - [幂级数和函数的连续性与端点性质](#section-7-20)
  - [幂级数展开与泰勒系数：任意阶可导还不够](#section-7-21)
  - [常用麦克劳林展开](#section-7-22)
  - [两条常用幂级数求和公式](#section-7-23)
  - [傅里叶级数](#fourier-series)
- [第八部分：空间解析几何](#section-8)
  - [平面二次曲线的判别式](#section-8-1)
  - [向量的坐标、模与方向余弦](#section-8-2)
  - [数量积、向量积与混合积](#section-8-3)
  - [空间平面方程与平面束](#section-8-4)
  - [空间直线方程](#section-8-5)
  - [点到直线、平面的距离](#section-8-6)
  - [直线与平面的位置关系及夹角](#section-8-7)
  - [空间曲线及其在坐标面上的投影](#section-8-8)
  - [常见二次曲面与柱面](#section-8-9)
  - [旋转曲面的方程](#section-8-10)
  - [空间曲线的切线与法平面](#section-8-11)
  - [空间曲面的切平面与法线](#section-8-12)
- [第九部分：曲线积分、曲面积分](#section-9)
- [第十部分：特殊公式](#section-10)
  - [三角恒等式](#section-10-1)
  - [根式与绝对值](#section-10-2)
  - [平方和公式](#section-10-3)
  - [常用不等式](#section-10-4)
  - [斯特林公式](#section-10-5)
  - [高斯积分](#section-10-6)
  - [零的阶乘](#section-10-7)

## <span style="color: #3498db;">第一部分：函数、极限、连续</span> <span id="section-1"></span>

### 复合函数的奇偶性 <span id="section-1-1"></span>

$f(g(x))$ 的定义域须关于原点对称。**内偶则偶，内奇则外。**

| 内函数 $g$ | 外函数 $f$ | 复合函数 |
| ---------- | ---------- | -------- |
| 偶         | 任意       | 偶       |
| 奇         | 奇         | 奇       |
| 奇         | 偶         | 偶       |

外函数非奇非偶时，“内奇则外”不能直接判断。零函数既奇又偶。

### 反三角函数的定义域与值域 <span id="section-1-2"></span>

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

### 数列极限 <span id="section-1-3"></span>

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

### 函数极限的 24 种定义 <span id="section-1-4"></span>

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

### 极限存在的等价表述 <span id="section-1-5"></span>

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

### 极限的局部保号性 <span id="section-1-6"></span>

设 $\lim_{x\to x_0}f(x)=A\in\mathbb R$，下述“附近”指充分小的去心邻域。

- $A>0$（$A<0$）$\Rightarrow$ 附近 $f(x)>0$（$f(x)<0$）。
- $A\ne0$ $\Rightarrow$ 附近 $f(x)$ 与 $A$ 同号，且 $|f(x)|>|A|/2$。
- 附近 $f(x)\ge0$（$f(x)\le0$）$\Rightarrow A\ge0$（$A\le0$）。即使函数严格正、负，极限仍可能为 $0$。
- $A=0$ 时，无法判断附近函数的符号。

同样适用于单侧及无穷远趋近。

#### 牢记：脱帽严格不等号，戴帽非严格不等号 <span id="section-1-6-1"></span>

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

### 有界性常用结论 <span id="section-1-7"></span>

- **有限极限存在 $\Rightarrow$ 在相应趋近区域内局部有界** ，反之不成立，如 $\sin(1/x)$ 在 $x\to0$ 时。
- 闭区间上的连续函数有界，并取得最大值、最小值。
- $(a,b)$ 上连续，且两端单侧极限均有限 $\Rightarrow$ 在 $(a,b)$ 上有界。
- $f,g$ 有界 $\Rightarrow f\pm g,fg$ 有界；若另有 $|g|\ge m>0$，则 $f/g$ 有界。

局部有界不等于全域有界；上、下界不唯一，最大、最小值唯一。

### 无穷小的比较 <span id="section-1-8"></span>

设在自变量的同一变化过程中，$\alpha(x)\to0$、$\beta(x)\to0$，且比较分母 $\beta(x)\ne0$。**比较无穷小的阶，就是通过比值的极限比较它们趋于 $0$ 的速度。**

#### 高阶、低阶、同阶与等价无穷小 <span id="section-1-8-1"></span>

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

#### 等价不等于相等 <span id="section-1-8-2"></span>

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

#### k 阶无穷小 <span id="section-1-8-3"></span>

若存在 $k>0$ 和有限非零常数 $c$，使

$$
\boxed{\lim\frac{\alpha(x)}{[\beta(x)]^k}=c,\qquad0<|c|<\infty},
$$

则称 **$\alpha(x)$ 是 $\beta(x)$ 的 $k$ 阶无穷小** ，也即 $\alpha\sim c\beta^k$。

例如 $x\to0$ 时，$1-\cos x\sim x^2/2$，所以 $1-\cos x$ 是 $x$ 的二阶无穷小；$x-\sin x\sim x^3/6$，所以 $x-\sin x$ 是 $x$ 的三阶无穷小。

相对于 $\beta$，$k>1$ 时为高阶，$k=1$ 时为同阶，$0<k<1$ 时为低阶。$k$ 非整数时须保证 $\beta^k$ 在所讨论的趋近过程中有定义。

### 常用等价无穷小 <span id="section-1-9"></span>

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

### 小 $o$ 的运算规则 <span id="section-1-10"></span>

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

### 五个函数的大小关系与三阶差值 <span id="section-1-11"></span>

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

### 常见无穷大的增长速度比较 <span id="section-1-12"></span>

固定常数 $\alpha,\beta>0$、$a>1$；$f\ll g$ 表示 $f/g\to0$。

$$
(\ln x)^\alpha\ll x^\beta\ll a^x\qquad(x\to+\infty)
$$

$$
(\ln n)^\alpha\ll n^\beta\ll a^n\ll n!\ll n^n\qquad(n\to\infty)
$$

**对数 → 正幂 → 指数 → 阶乘 → 自身幂，增长越来越快。**

### 常见极限 <span id="section-1-13"></span>

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

### 连续性的性质 <span id="section-1-14"></span>

内点 $x_0$ 处：

$$
f\text{ 在 }x_0\text{ 处连续}
\iff\lim_{x\to x_0^-}f(x)=\lim_{x\to x_0^+}f(x)=f(x_0).
$$

- **四则运算：** $f,g$ 在 $x_0$ 处连续，则 $f\pm g,fg$ 也连续；若 $g(x_0)\ne0$，则 $f/g$ 也连续。
- **复合函数：** $\varphi$ 在 $x_0$ 处连续，$f$ 在 $u_0=\varphi(x_0)$ 处连续，则 $f(\varphi(x))$ 在 $x_0$ 处连续。
- **反函数：** $f$ 在区间 $I$ 上严格单调且连续，则反函数在 $f(I)$ 上连续，且单调性与 $f$ 相同。
- **局部保号：** $f$ 在 $x_0$ 处连续且 $f(x_0)>0$（$<0$），则存在 $\delta>0$，使 $|x-x_0|<\delta$ 时 $f(x)>0$（$<0$）。

#### 绝对值与连续、可导的关系 <span id="section-1-14-1"></span>

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

### 间断点分类 <span id="section-1-15"></span>

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

## <span style="color: #3498db;">第二部分：一元函数微分学及其应用</span> <span id="section-2"></span>

### 函数在一点可导的充要条件 <span id="section-2-1"></span>

#### 单侧导数 <span id="section-2-1-1"></span>

**左导数** ：增量 $\Delta x\to0^-$，从 $x_0$ 左侧趋近。

$$
f'_-(x_0)=\lim_{\Delta x\to0^-}\frac{f(x_0+\Delta x)-f(x_0)}{\Delta x}
$$

**右导数** ：增量 $\Delta x\to0^+$，从 $x_0$ 右侧趋近。

$$
f'_+(x_0)=\lim_{\Delta x\to0^+}\frac{f(x_0+\Delta x)-f(x_0)}{\Delta x}
$$

$f'_-(x_0)$、$f'_+(x_0)$ 分别称为 $f(x)$ 在 $x_0$ 处的左导数、右导数，统称为**单侧导数** 。导数存在要求上述极限为有限值。

#### 可导的充要条件 <span id="section-2-1-2"></span>

$$
\boxed{f'(x_0)\text{ 存在}\iff f'_-(x_0)\text{ 与 }f'_+(x_0)\text{ 均存在且相等}}
$$

此时：

$$
f'(x_0)=f'_-(x_0)=f'_+(x_0)
$$

**实际意义：左右两侧的瞬时变化率均存在且相等。**

**几何意义：曲线在该点有斜率有限的切线，可以是斜切线，也可以是水平切线。** 竖直切线的斜率不是有限值，不能据此认为函数在该点可导。

#### 可导与连续的关系 <span id="section-2-1-3"></span>

**可导一定连续，连续不一定可导。** 连续是可导的必要条件，可导是连续的充分条件；不连续则一定不可导。

例如，$f(x)=|x|$ 在 $x=0$ 处连续，但左导数 $f'_-(0)=-1$、右导数 $f'_+(0)=1$，左右导数不相等，因此在该点不可导。

#### 可微、增量与微分 <span id="section-2-1-4"></span>

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

### 基本求导公式 <span id="section-2-2"></span>

#### 幂函数、指数函数与对数函数 <span id="section-2-2-1"></span>

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

#### 对数绝对值与复合函数 <span id="section-2-2-2"></span>

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

#### 三角函数与反三角函数 <span id="section-2-2-3"></span>

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

#### 两个常用对数复合函数 <span id="section-2-2-4"></span>

$$
\left[\ln\left(x+\sqrt{x^2+1}\right)\right]'=\frac1{\sqrt{x^2+1}}\qquad(x\in\mathbb R)
$$

$$
\left[\ln\left(x+\sqrt{x^2-1}\right)\right]'=\frac1{\sqrt{x^2-1}}\qquad(x>1)
$$

### 莱布尼茨公式（高阶导数） <span id="section-2-3"></span>

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

### 反函数求导公式与 arcsin x 的求导 <span id="section-2-4"></span>

#### 反函数的一阶、二阶导数 <span id="section-2-4-1"></span>

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

#### 例：y = arcsin x 的求导过程 <span id="section-2-4-2"></span>

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

### 罗尔定理与推广 <span id="section-2-5"></span>

#### 罗尔定理 <span id="section-2-5-1"></span>

设 $a<b$，且 $f$ 同时满足：

1. 在 $[a,b]$ 上连续；
2. 在 $(a,b)$ 内可导；
3. $f(a)=f(b)$。

则至少存在一点 $\xi\in(a,b)$，使

$$
\boxed{f'(\xi)=0}.
$$

**牢记：闭区间连续、开区间可导、两端函数值相等。三个条件须同时满足，结论中的 $\xi$ 在区间内部，且不一定唯一。** 几何意义：至少有一条水平切线。常用于证明导数存在零点，也可通过构造辅助函数来证明等式。

#### 推广的罗尔定理 <span id="section-2-5-2"></span>

设 $f$ 在 $(a,b)$ 内可导，且两端极限相同：

$$
\lim_{x\to a^+}f(x)=\lim_{x\to b^-}f(x)=A.
$$

则至少存在 $\xi\in(a,b)$，使 $f'(\xi)=0$。这里 $(a,b)$ 可以是有限区间，也可以是无穷区间；无穷端点处取相应的无穷远极限。$A$ 可以是有限实数，也可以是 $+\infty$ 或 $-\infty$，但两端必须趋于**同一个** 值（无穷大时也须同号）。

**牢记：端点函数值相等，可推广为两端极限相等。** 有限端点处不要求原函数有定义；若两端极限一个为 $+\infty$、另一个为 $-\infty$，则不能使用这个结论。

#### 罗尔定理推论：函数与导数的实根个数 <span id="section-2-5-3"></span>

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

#### 实系数奇次多项式至少有一个实根 <span id="section-2-5-4"></span>

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

### 拉格朗日中值定理 <span id="section-2-6"></span>

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

### 柯西中值定理 <span id="section-2-7"></span>

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

### 泰勒公式与两种余项 <span id="section-2-8"></span>

**思想：用多项式近似表示函数。** $n$ 阶泰勒多项式为

$$
T_n(x)=\sum_{k=0}^n\frac{f^{(k)}(x_0)}{k!}(x-x_0)^k,
\qquad f^{(0)}=f.
$$

#### 带拉格朗日余项的泰勒公式 <span id="section-2-8-1"></span>

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

#### 带佩亚诺余项的泰勒公式 <span id="section-2-8-2"></span>

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

#### 麦克劳林公式的两种余项 <span id="section-2-8-3"></span>

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

### 截断为有限阶泰勒公式 <span id="section-2-9"></span>

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

### 驻点、导数符号、极值点与单调性的关系 <span id="section-2-10"></span>

#### 一、某一点的导数与单调性 <span id="section-2-10-1"></span>

1. $f'(x_0)=0$：只能说明 $x_0$ 是驻点，不能说明是极值点，也不能判断邻域内的单调性。
2. $f'(x_0)>0$：只能说明在充分小的邻域内，$x_0$ 左侧函数值小于 $f(x_0)$，右侧函数值大于 $f(x_0)$，**不能推出整个邻域单调递增** 。
3. $f'(x_0)<0$：与上述相反，同样**不能推出整个邻域单调递减** 。

**原因：** 一点导数的符号不代表邻域内导数的符号，导数可能在任意小的邻域内不断变号，导致函数振荡。

#### 二、极值点与单调性的关系 <span id="section-2-10-2"></span>

1. 极大值点：只要求存在某个邻域，使 $f(x)\le f(x_0)$。
2. 极小值点：只要求存在某个邻域，使 $f(x)\ge f(x_0)$。
3. **即使是极值点，也不能推出左右邻域分别单调。** 函数在极值点两侧仍然可能无限振荡。
4. 若函数在内点可导且取得极值，则该点导数必为 $0$（费马定理）；**反过来不成立** 。

#### 三、什么时候才能判断单调性？ <span id="section-2-10-3"></span>

- 某区间内处处 $f'(x)>0$ $\Rightarrow$ 该区间严格单调递增。
- 某区间内处处 $f'(x)<0$ $\Rightarrow$ 该区间严格单调递减。
- 若 $f'$ 在 $x_0$ 连续，且 $f'(x_0)>0$（或小于 $0$），则可以推出某个邻域内严格单调递增（或递减）。

### 一元函数极值的必要条件 <span id="section-2-11"></span>

设 $x_0$ 是定义域内点。若 $f$ 在 $x_0$ 处可导且取得极值，则 $f'(x_0)=0$；若还二阶可导，则

$$
\begin{aligned}
x_0\text{ 为极大值点}&\Rightarrow f'(x_0)=0,\quad f''(x_0)\le0,\\
x_0\text{ 为极小值点}&\Rightarrow f'(x_0)=0,\quad f''(x_0)\ge0.
\end{aligned}
$$

**必要条件中的二阶导数允许等于零，不能写成严格不等号。** 如 $f(x)=-x^4$ 在 $0$ 处取极大值，但 $f''(0)=0$。这些必要条件不能反推极值：$f(x)=x^3$ 在 $0$ 处一、二阶导数均为零，却没有极值。

### 极值的二阶导数判别法 <span id="section-2-12"></span>

设 $x_0$ 为定义域内点，$f$ 在 $x_0$ 的某邻域内可导，且 $f''(x_0)$ 存在。若 $f'(x_0)=0$、$f''(x_0)\ne0$，则：

- **$f''(x_0)<0$：$f$ 在 $x_0$ 处取得极大值 $f(x_0)$。**
- **$f''(x_0)>0$：$f$ 在 $x_0$ 处取得极小值 $f(x_0)$。**

**记忆：一阶为零，二阶看正负；负为极大，正为极小。**

若 $f''(x_0)=0$，此判别法失效，不能据此判断是否有极值；可改用一阶导数在该点两侧的符号变化判断。

### 极值的高阶导数判别法（第三充分条件） <span id="section-2-13"></span>

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

### 曲线的凹凸性 <span id="section-2-14"></span>

设 $f(x)$ 在区间 $I$ 上连续，对 $I$ 上任意两个不同的点 $x_1,x_2$：

#### 凹（凹弧） <span id="section-2-14-1"></span>

若恒有

$$
\boxed{f\left(\frac{x_1+x_2}{2}\right)<\frac{f(x_1)+f(x_2)}2},
$$

则称 $y=f(x)$ 在 $I$ 上的图形是**凹的（凹弧）** 。几何意义：**图形上任意弧段位于对应弦的下方** ，形状如 $\cup$，例如 $y=x^2$。

#### 凸（凸弧） <span id="section-2-14-2"></span>

若恒有

$$
\boxed{f\left(\frac{x_1+x_2}{2}\right)>\frac{f(x_1)+f(x_2)}2},
$$

则称 $y=f(x)$ 在 $I$ 上的图形是**凸的（凸弧）** 。几何意义：**图形上任意弧段位于对应弦的上方** ，形状如 $\cap$，例如 $y=-x^2$。

#### 区分不等式中的两个量 <span id="section-2-14-3"></span>

- $f\left(\dfrac{x_1+x_2}{2}\right)$：**横坐标中点处的函数值** ，对应的点在曲线上。
- $\dfrac{f(x_1)+f(x_2)}2$：**两端函数值的平均值** ，对应的是弦的中点纵坐标。

**记忆：凹在弦下，凸在弦上。**

#### 拐点的三阶导数判别法 <span id="section-2-14-4"></span>

设 $x_0$ 为定义域内点，$f$ 在 $x_0$ 的某邻域内二阶可导，且 $f'''(x_0)$ 存在。若

$$
\boxed{f''(x_0)=0,\qquad f'''(x_0)\ne0},
$$

则曲线在 $x_0$ 两侧的凹凸性发生改变，**$(x_0,f(x_0))$ 是拐点** 。

**记忆：二阶为零、三阶非零，可判定拐点。** 这是充分条件；若三阶导数也为零，仍可能有拐点，需进一步判断两侧凹凸性。例如 $y=x^5$ 在原点有拐点，但 $f'''(0)=0$。

#### 拐点的高阶导数判别法（第三充分条件） <span id="section-2-14-5"></span>

设 $x_0$ 为定义域内点，$f$ 在 $x_0$ 处 $n$ 阶可导，且

$$
f''(x_0)=f'''(x_0)=\cdots=f^{(n-1)}(x_0)=0,\qquad
f^{(n)}(x_0)\ne0,\qquad n\ge3.
$$

**从二阶导数开始，找到首次非零导数：若其阶数 $n$ 为奇数，则 $(x_0,f(x_0))$ 是拐点。** 不要求 $f'(x_0)=0$。

若首次非零导数的阶数 $n$ 为偶数，则二阶导数在该点两侧同号，凹凸性不改变，该点不是拐点。

**与极值判别区分：极值从一阶开始找首次非零导数，偶数阶有极值；拐点从二阶开始找，奇数阶有拐点。** 若始终未找到非零导数，不能用此法直接判断。

### 斜渐近线 <span id="section-2-15"></span>

#### 当 x 趋于正无穷 <span id="section-2-15-1"></span>

若

$$
\lim_{x\to+\infty}\frac{f(x)}x=a_1\ne0,\qquad
\lim_{x\to+\infty}[f(x)-a_1x]=b_1,
$$

其中 $a_1,b_1$ 均为有限常数，则 **$y=a_1x+b_1$ 是曲线 $y=f(x)$ 在正无穷方向的斜渐近线** 。

#### 当 x 趋于负无穷 <span id="section-2-15-2"></span>

若

$$
\lim_{x\to-\infty}\frac{f(x)}x=a_2\ne0,\qquad
\lim_{x\to-\infty}[f(x)-a_2x]=b_2,
$$

其中 $a_2,b_2$ 均为有限常数，则 **$y=a_2x+b_2$ 是曲线 $y=f(x)$ 在负无穷方向的斜渐近线** 。

#### 两个方向为同一条斜渐近线 <span id="section-2-15-3"></span>

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

### 曲率与曲率半径（数学一、数学二） <span id="section-2-16"></span>

设 $y=y(x)$ 二阶可导，则曲线在点 $(x,y(x))$ 处的**曲率** 为：

$$
\boxed{k=\frac{|y''|}{[1+(y')^2]^{3/2}}}
$$

当 $y''\ne0$ 时，**曲率半径** 为：

$$
\boxed{R=\frac1k=\frac{[1+(y')^2]^{3/2}}{|y''|}}
$$

**曲率表示曲线的弯曲程度：曲率越大，曲率半径越小。**

## <span style="color: #3498db;">第三部分：一元函数积分学及其应用</span> <span id="section-3"></span>

### 原函数的存在性 <span id="section-3-1"></span>

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

### 常用不定积分公式 <span id="section-3-2"></span>

以下 $C$ 为任意常数，公式在被积函数有定义的各个区间内使用；含参数 $a$ 的公式统一取 $a>0$。

#### 三角函数的积分 <span id="section-3-2-1"></span>

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

#### 反正切型与反正弦型 <span id="section-3-2-2"></span>

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

#### 根式分母的对数型 <span id="section-3-2-3"></span>

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

#### 平方差分母 <span id="section-3-2-4"></span>

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

#### 半圆根式 <span id="section-3-2-5"></span>

$$
\boxed{\int\sqrt{a^2-x^2}\,\mathrm dx
=\frac{a^2}{2}\arcsin\frac xa+\frac x2\sqrt{a^2-x^2}+C}
\qquad(|x|<a).
$$

#### 三角函数平方：先降幂或用恒等式 <span id="section-3-2-6"></span>

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

#### 指数函数与正弦、余弦乘积的积分 <span id="section-3-2-7"></span>

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

### 有理函数积分：部分分式分解 <span id="section-3-3"></span>

对有理函数 $P(x)/Q(x)$，**先化为真分式** ：若 $\deg P\ge\deg Q$，先做多项式除法，将其写为“多项式 + 真分式”。再把分母在实数范围内分解为一次因式和不可约二次因式，按下列规则设待定系数。

#### ① 一次单因式 <span id="section-3-3-1"></span>

分母中的一次单因式 $ax+b$ 对应一项

$$
\frac{A}{ax+b}.
$$

#### ② k 重一次因式 <span id="section-3-3-2"></span>

分母中的 $(ax+b)^k$ 对应 $k$ 项：

$$
\frac{A_1}{ax+b}+\frac{A_2}{(ax+b)^2}
+\cdots+\frac{A_k}{(ax+b)^k}.
$$

#### ③ 不可约二次单因式 <span id="section-3-3-3"></span>

分母中的二次单因式 $px^2+qx+r$（$p\ne0$，$q^2-4pr<0$）对应一项

$$
\frac{Ax+B}{px^2+qx+r}.
$$

#### ④ k 重不可约二次因式 <span id="section-3-3-4"></span>

分母中的 $(px^2+qx+r)^k$（$q^2-4pr<0$）对应 $k$ 项：

$$
\frac{A_1x+B_1}{px^2+qx+r}
+\frac{A_2x+B_2}{(px^2+qx+r)^2}
+\cdots+\frac{A_kx+B_k}{(px^2+qx+r)^k}.
$$

上述一次因式要求 $a\ne0$，$k$ 为正整数，各分子中的系数分别待定。

#### 例：两类重因式同时出现 <span id="section-3-3-5"></span>

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

### 定积分存在的充分条件 <span id="section-3-4"></span>

设 $a<b$，$f$ 在闭区间 $[a,b]$ 上有定义。满足以下条件中的**任意一条** ，即可保证定积分 $\displaystyle\int_a^b f(x)\,\mathrm dx$ 存在（黎曼可积）：

1. **闭区间上连续** ：$f$ 在 $[a,b]$ 上连续。
2. **闭区间上单调** ：$f$ 在 $[a,b]$ 上单调，不要求连续。
3. **有界且只有有限个间断点** ：$f$ 在 $[a,b]$ 上有界，且间断点只有有限个。

**以上均为充分条件，不是必要条件。** 定积分存在不要求函数处处连续；第三条中的“有界”不能省略。

**必要条件：定积分存在必有界。** 若 $f$ 在 $[a,b]$ 上黎曼可积，则 $f$ 在该闭区间上必有界；反过来，仅有界不能保证可积。因此，**有界是黎曼可积的必要不充分条件** 。这里讨论普通定积分，不包括反常积分。

### 定积分的极限表达式（等分区间，取右端点） <span id="section-3-5"></span>

设 $a<b$，$f$ 在 $[a,b]$ 上黎曼可积（例如在该闭区间上连续），则

$$
\boxed{
\int_a^b f(x)\,\mathrm dx
=\lim_{n\to\infty}\frac{b-a}{n}
\sum_{i=1}^{n}f\left(a+\frac{i(b-a)}{n}\right)
}
$$

将 $[a,b]$ 等分为 $n$ 个小区间，每个小区间的宽度为 $\Delta x=\dfrac{b-a}{n}$，第 $i$ 个小区间的右端点为 $x_i=a+\dfrac{i(b-a)}{n}$。因此，上式就是 $\lim_{n\to\infty}\sum_{i=1}^{n}f(x_i)\Delta x$。

#### 特殊情形：积分区间为 $[0,1]$ <span id="section-3-5-1"></span>

取 $a=0$、$b=1$，若 $f(x)$ 在 $[0,1]$ 上黎曼可积，则

$$
\boxed{
\int_0^1 f(x)\,\mathrm dx
=\lim_{n\to\infty}\frac1n\sum_{i=1}^{n}f\left(\frac in\right)
}
$$

此时小区间宽度为 $\Delta x=\dfrac1n$，右端点为 $x_i=\dfrac in$。求和式极限中出现“$\dfrac1n\sum_{i=1}^{n}f\left(\dfrac in\right)$”时，可识别为上述定积分。

### 定积分的保号性、保序性与绝对值不等式 <span id="section-3-6"></span>

以下均设 $a<b$，$f(x)$、$g(x)$ 在 $[a,b]$ 上黎曼可积；函数之间的不等式要求对所有 $x\in[a,b]$ 成立。

#### 保号性 <span id="section-3-6-1"></span>

$$
\boxed{
f(x)\ge0
\quad\Longrightarrow\quad
\int_a^b f(x)\,\mathrm dx\ge0
}
$$

#### 保序性 <span id="section-3-6-2"></span>

$$
\boxed{
f(x)\le g(x)
\quad\Longrightarrow\quad
\int_a^b f(x)\,\mathrm dx
\le\int_a^b g(x)\,\mathrm dx
}
$$

#### 绝对值不等式 <span id="section-3-6-3"></span>

$$
\boxed{
\left|\int_a^b f(x)\,\mathrm dx\right|
\le\int_a^b |f(x)|\,\mathrm dx
}
$$

**积分的绝对值不大于绝对值的积分。** $f(x)$ 黎曼可积时，$|f(x)|$ 也黎曼可积。

### 周期函数在一个周期内的积分 <span id="section-3-7"></span>

设 $f$ 是以 $T>0$ 为周期的连续函数，则对任意实数 $a$，

$$
\boxed{\int_a^{a+T}f(x)\,\mathrm dx=\int_0^T f(x)\,\mathrm dx}.
$$

**在长度为一个周期的区间上的定积分，与区间的起点位置无关。**

### 区间再现公式 <span id="section-3-8"></span>

设 $f$ 在 $[a,b]$ 上连续，令 $t=a+b-x$，则

$$
\boxed{\int_a^b f(x)\,\mathrm dx=\int_a^b f(a+b-x)\,\mathrm dx}.
$$

**记忆：用“上下限之和减去 $x$”替换 $x$，积分区间和积分值不变。**

### 正弦、余弦幂次的定积分（华里士公式） <span id="section-3-9"></span>

#### 区间 $[0,\pi/2]$ <span id="section-3-9-1"></span>

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

#### 区间 $[0,\pi]$ <span id="section-3-9-2"></span>

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

#### 区间 $[0,2\pi]$ <span id="section-3-9-3"></span>

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

### 定积分的估值定理 <span id="section-3-10"></span>

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

### 积分中值定理 <span id="section-3-11"></span>

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

#### 推广：带权积分中值定理（例 11.1） <span id="section-3-11-1"></span>

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

### 变上限积分求导（微积分基本定理） <span id="section-3-12"></span>

#### 可积则变上限积分连续 <span id="section-3-12-1"></span>

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

#### 连续则变上限积分可导 <span id="section-3-12-2"></span>

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

#### 上下限都是函数时的求导公式 <span id="section-3-12-3"></span>

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

### 区间内部有瑕点的反常积分 <span id="section-3-13"></span>

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

### 由无穷远处的函数极限初步判断积分敛散性 <span id="section-3-14"></span>

设 $f$ 在 $[1,+\infty)$ 的任意有限闭子区间上可积，则

| $\displaystyle\lim_{x\to+\infty}f(x)$ | $\displaystyle\int_1^{+\infty}f(x)\,\mathrm dx$ |
| ------------------------------------- | ----------------------------------------------- |
| 无穷（$\pm\infty$）                   | 一定发散                                        |
| 非零常数                              | 一定发散                                        |
| $0$                                   | 可能收敛，也可能发散，需进一步判断              |

例如 $1/x^2$ 与 $1/x$ 在无穷远处都趋于 $0$，但在 $[1,+\infty)$ 上的积分分别收敛、发散。

**注意：若已知函数极限存在，积分收敛则该极限必为 $0$；一般情况下，不能由积分收敛直接推出 $f(x)\to0$，因为函数极限可能不存在。**

### 两类常用的 p 型积分 <span id="section-3-15"></span>

设 $p\in\mathbb R$。

#### 从 0 到 1：考察零点附近 <span id="section-3-15-1"></span>

$$
\boxed{\int_0^1\frac1{x^p}\,\mathrm dx
\begin{cases}
\text{收敛，值为 }\dfrac1{1-p},&p<1,\\
\text{发散},&p\ge1.
\end{cases}}
$$

当 $p>0$ 时，$x=0$ 是瑕点；当 $p\le0$ 时，被积函数可在 $0$ 处连续补定义，积分也收敛。

#### 从 1 到正无穷：考察无穷远处 <span id="section-3-15-2"></span>

$$
\boxed{\int_1^{+\infty}\frac1{x^p}\,\mathrm dx
\begin{cases}
\text{收敛，值为 }\dfrac1{p-1},&p>1,\\
\text{发散},&p\le1.
\end{cases}}
$$

**记忆：零点附近 $p<1$ 收敛，无穷远处 $p>1$ 收敛；临界值 $p=1$ 两者都发散。** 这两类积分常用作比较判别法的参照。

### 反常积分小常识：对数、幂函数与指数函数的增长比较 <span id="section-3-16"></span>

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

#### 例：指数衰减压过幂函数增长 <span id="section-3-16-1"></span>

设 $a>0$、$p>0$，判断 $\displaystyle\int_1^{+\infty}x^pe^{-ax}\,\mathrm dx$ 的敛散性。取比较函数 $g(x)=1/x^2$，则

$$
\lim_{x\to+\infty}\frac{x^pe^{-ax}}{1/x^2}
=\lim_{x\to+\infty}\frac{x^{p+2}}{e^{ax}}=0.
$$

因为 $\int_1^{+\infty}x^{-2}\,\mathrm dx$ 收敛，由极限比较判别法，**原积分收敛** 。注意：仅知道被积函数趋于 $0$ 还不能判断积分收敛，必须进一步比较。

#### 例：无穷远处用 $x^a$ 控制 $\ln x$ <span id="section-3-16-2"></span>

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

#### 例：零点附近用 $1/x^a$ 控制 $|\ln x|$ <span id="section-3-16-3"></span>

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

#### 常用积分：对数绝对值 <span id="section-3-16-4"></span>

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

#### 常见结论：零点附近的对数除以幂函数 <span id="section-3-16-5"></span>

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

#### 常见结论：无穷远处的对数除以幂函数 <span id="section-3-16-6"></span>

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

### 反常积分的比较判别法 <span id="section-3-17"></span>

#### 无穷区间上的比较判别法 <span id="section-3-17-1"></span>

设 $f(x),g(x)$ 在 $[a,+\infty)$ 上连续，且 $0\le f(x)\le g(x)$，则

$$
\boxed{\int_a^{+\infty}g(x)\,\mathrm dx\text{ 收敛}
\ \Longrightarrow\ \int_a^{+\infty}f(x)\,\mathrm dx\text{ 收敛}},
$$

$$
\boxed{\int_a^{+\infty}f(x)\,\mathrm dx\text{ 发散}
\ \Longrightarrow\ \int_a^{+\infty}g(x)\,\mathrm dx\text{ 发散}}.
$$

#### 无界函数的比较判别法（瑕积分） <span id="section-3-17-2"></span>

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

### 反常积分比较判别法的极限形式 <span id="section-3-18"></span>

#### 无穷区间的情形 <span id="section-3-18-1"></span>

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

#### 瑕积分的情形 <span id="section-3-18-2"></span>

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

### 反常积分的绝对收敛与条件收敛 <span id="section-3-19"></span>

设 $f$ 在 $[1,+\infty)$ 的任意有限闭子区间上可积。

- **绝对收敛：** $\displaystyle\int_1^{+\infty}|f(x)|\,\mathrm dx$ 收敛。
- **条件收敛：** $\displaystyle\int_1^{+\infty}f(x)\,\mathrm dx$ 收敛，但 $\displaystyle\int_1^{+\infty}|f(x)|\,\mathrm dx$ 发散。

**绝对收敛一定推出原积分收敛；原积分收敛不一定绝对收敛。**

### 狄利克雷判别法（反常积分） <span id="section-3-20"></span>

设 $f$ 在 $[a,+\infty)$ 的任意有限闭子区间上可积，且变上限积分有界，即存在常数 $M>0$，使

$$
\left|\int_a^t f(x)\,\mathrm dx\right|\le M\qquad(t\ge a).
$$

若 $g(x)$ 在 $[a,+\infty)$ 上单调，且 $\lim_{x\to+\infty}g(x)=0$，则

$$
\boxed{\int_a^{+\infty}f(x)g(x)\,\mathrm dx\text{ 收敛}}.
$$

**直观记忆：振荡抵消 + 单调衰减到零 $\Longrightarrow$ 积分收敛。** 其中“振荡抵消”的准确条件是 $\int_a^t f(x)\,\mathrm dx$ 有界，仅有 $f(x)$ 自身有界或正负交替还不够。该判别法保证收敛，不直接判断是否绝对收敛。

#### 常见结论：正弦、余弦除以幂函数 <span id="section-3-20-1"></span>

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

### 定积分的几何应用：平面图形的面积 <span id="section-3-21"></span>

#### 直角坐标：上减下 <span id="section-3-21-1"></span>

设 $f(x)$、$g(x)$ 在 $[a,b]$ 上连续，且 $f(x)\ge g(x)$，则由两条曲线 $y=f(x)$、$y=g(x)$ 及直线 $x=a$、$x=b$ 围成的图形面积为

$$
\boxed{S=\int_a^b[f(x)-g(x)]\,\mathrm dx}.
$$

**记忆：上方曲线减下方曲线。** 面积微元为 $\mathrm dS=[f(x)-g(x)]\,\mathrm dx$；上下限 $a,b$ 是区域在 $x$ 轴上的投影端点。

若两条曲线在区间内交换上下位置，应在交点处分段，或写为

$$
S=\int_a^b|f(x)-g(x)|\,\mathrm dx.
$$

#### 极坐标：外半径平方减内半径平方 <span id="section-3-21-2"></span>

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

### 旋转体体积：柱壳法（重点记忆） <span id="section-3-22"></span>

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

#### 何时比圆环法更方便 <span id="section-3-22-1"></span>

**已知 $y=y(x)$、绕 $y$ 轴旋转时，优先考虑柱壳法。** 它直接对 $x$ 积分，通常不必反解 $x=x(y)$；当反函数难求，或圆环法需要按 $y$ 分段时，柱壳法往往更简便。

| 方法   | 小条与旋转轴的关系 | 体积微元                                                             |
| ------ | ------------------ | -------------------------------------------------------------------- |
| 柱壳法 | 平行于旋转轴       | $\mathrm dV=2\pi\times\text{半径}\times\text{高度}\times\text{厚度}$ |
| 圆环法 | 垂直于旋转轴       | $\mathrm dV=\pi(\text{外半径}^2-\text{内半径}^2)\times\text{厚度}$   |

**柱壳法不一定在所有题目中都更简单，应选边界表达和分段更方便的方法。** 上式中的 $0\le a<b$ 保证 $x$ 就是柱壳半径；若区域跨越 $y$ 轴，旋转后可能重叠，不能简单把 $x$ 换成 $|x|$ 后对整个区间积分，否则可能重复计算体积。

### 绕任意定直线旋转的体积（重点公式） <span id="section-3-23"></span>

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

#### 记忆与理解：圆盘面积乘轴向厚度 <span id="section-3-23-1"></span>

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

#### 特例与使用提醒 <span id="section-3-23-2"></span>

- 绕 $x$ 轴：取 $A=0,B=1,C=0$，得到 $V=\pi\int_a^b f^2(x)\,\mathrm dx$。
- 绕水平直线 $y=k$：取 $A=0,B=1,C=-k$，得到 $V=\pi\int_a^b[f(x)-k]^2\,\mathrm dx$。
- 若某条垂直于旋转轴的直线与曲线有两个或更多交点，不能直接套用此式；应先分析截面，用圆环法等方法处理，避免重复计算。

### 平面曲边梯形的形心坐标 <span id="section-3-24"></span>

设 $f(x)$ 在 $[a,b]$ 上连续且非负，平面区域为

$$
D=\{(x,y)\mid a\le x\le b,\ 0\le y\le f(x)\},
$$

其面积 $S=\int_a^b f(x)\,\mathrm dx>0$。形心是区域的几何中心；若薄片面密度均匀，形心与质心重合。

#### 公式与二重积分化简过程 <span id="section-3-24-1"></span>

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

### 平面曲线的弧长 <span id="section-3-25"></span>

以下曲线设为光滑或分段光滑，分段光滑时将各段弧长相加。参数或极角区间应将所求曲线描绘一次；若重复描绘，积分会累计重复经过的长度。

#### 弧长微元：从勾股关系出发 <span id="section-3-25-1"></span>

对曲线上的微小位移，弧长微元满足

$$
\boxed{\mathrm ds=\sqrt{(\mathrm dx)^2+(\mathrm dy)^2}}.
$$

这里表示微元关系；一段有限曲线的弧长通常不等于两端点间的直线距离。

#### 直角坐标方程 $y=y(x)$ <span id="section-3-25-2"></span>

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

#### 参数方程 $x=x(t),\ y=y(t)$ <span id="section-3-25-3"></span>

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

#### 极坐标方程 $r=r(\theta)$ <span id="section-3-25-4"></span>

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

### 旋转曲面的面积（侧面积） <span id="section-3-26"></span>

设平面曲线光滑或分段光滑，绕 $x$ 轴旋转一周。以下按所求曲面不重复覆盖的情形计算；分段光滑时，各段面积相加。这里只计算曲线旋转形成的**侧面积** ，不额外加入端面圆盘的面积。

#### 核心微元公式 <span id="section-3-26-1"></span>

曲线上一点到 $x$ 轴的距离为 $|y|$，因此

$$
\boxed{\mathrm dS=2\pi|y|\,\mathrm ds},
\qquad
\boxed{S=\int_L2\pi|y|\,\mathrm ds}.
$$

**记忆：在弧长微元 $\mathrm ds$ 上，乘“旋转一周的圆周长”$2\pi|y|$。** 半径取到旋转轴的距离，所以需要绝对值；$\mathrm ds$ 是曲线弧长微元，不能直接换成 $\mathrm dx$。

#### ① 直角坐标：$y=f(x)$，$a\le x\le b$ <span id="section-3-26-2"></span>

由 $\mathrm ds=\sqrt{1+[f'(x)]^2}\,\mathrm dx$，得

$$
\boxed{S=2\pi\int_a^b|f(x)|\sqrt{1+[f'(x)]^2}\,\mathrm dx}.
$$

相对于直角坐标弧长公式，被积函数多乘了 $2\pi|f(x)|$。

#### ② 参数方程：$x=x(t),\ y=y(t)$，$\alpha\le t\le\beta$ <span id="section-3-26-3"></span>

参数区间应将所求曲线描绘一次。由参数方程的弧长微元，得

$$
\boxed{S=2\pi\int_\alpha^\beta|y(t)|
\sqrt{[x'(t)]^2+[y'(t)]^2}\,\mathrm dt}.
$$

图片中 $x'(t)\ne0$ 是采用 $x$ 作中间变量的充分条件；直接使用上述弧长微元时，只需满足相应的光滑、正则和不重复覆盖条件。

#### ③ 极坐标：$r=r(\theta)$，$\alpha\le\theta\le\beta$ <span id="section-3-26-4"></span>

因 $y=r(\theta)\sin\theta$，到 $x$ 轴的距离为 $|r(\theta)\sin\theta|$，所以

$$
\boxed{S=2\pi\int_\alpha^\beta|r(\theta)\sin\theta|
\sqrt{r^2(\theta)+[r'(\theta)]^2}\,\mathrm d\theta}.
$$

**极坐标中，绕 $x$ 轴旋转的半径是 $|r\sin\theta|$，不是单独的 $|r|$。** $\sqrt{r^2+(r')^2}$ 来自弧长公式，不能漏掉 $r'$。

三种形式都来自同一关系：**侧面积 = 沿曲线累加“圆周长 × 弧长微元”** 。如果改为绕 $y$ 轴旋转，半径改为 $|x|$，即 $\mathrm dS=2\pi|x|\,\mathrm ds$。

## <span style="color: #3498db;">第四部分：多元函数微分学</span> <span id="section-4"></span>

### 二重极限的判断：直线、幂曲线与极坐标 <span id="section-4-1"></span>

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

#### 例：所有直线路径极限相同，二重极限仍可能不存在 <span id="section-4-1-1"></span>

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

### 全增量、可微与全微分 <span id="section-4-2"></span>

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

### 可微的必要条件、充分条件与判别步骤 <span id="section-4-3"></span>

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

### 一元函数与多元函数的性质关系 <span id="section-4-4"></span>

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

### 区域内全微分恒为零 <span id="section-4-5"></span>

设 $f$ 在连通开区域 $D$ 内可微，则

$$
\boxed{\mathrm df\equiv0
\iff f_x\equiv f_y\equiv0
\iff f(x,y)\equiv C\quad((x,y)\in D)}.
$$

这里 $\mathrm df\equiv0$ 指对任意 $\mathrm dx,\mathrm dy$，全微分都为零。若定义域不连通，各连通分支上的常数可以不同。

### 复合函数求导与“位置”记号 <span id="section-4-6"></span>

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

#### 先求偏导再代入，与代入后求导 <span id="section-4-6-1"></span>

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

### 隐函数求导公式 <span id="section-4-7"></span>

以下假设 $F$ 在所讨论点的某邻域内具有连续一阶偏导数，各偏导数均在隐函数对应的点处取值。

#### 一元隐函数：$F(x,y)=0$ <span id="section-4-7-1"></span>

由方程 $F(x,y)=0$ 确定隐函数 $y=f(x)$，当 $F_y(x,y)\ne0$ 时，

$$
\boxed{\frac{\mathrm dy}{\mathrm dx}=-\frac{F_x(x,y)}{F_y(x,y)}}.
$$

对恒等式 $F(x,f(x))=0$ 求导，得到 $F_x+F_y\,y'=0$，移项即得上式。

#### 二元隐函数：$F(x,y,z)=0$ <span id="section-4-7-2"></span>

由方程 $F(x,y,z)=0$ 确定隐函数 $z=f(x,y)$，当 $F_z(x,y,z)\ne0$ 时，

$$
\boxed{
\frac{\partial z}{\partial x}=-\frac{F_x(x,y,z)}{F_z(x,y,z)},
\qquad
\frac{\partial z}{\partial y}=-\frac{F_y(x,y,z)}{F_z(x,y,z)}
}.
$$

**记忆：分母对因变量求偏导，分子对所求的自变量求偏导，前面加负号；分母必须非零。**

### 二元函数的无条件极值 <span id="section-4-8"></span>

以下讨论定义域的内点 $(x_0,y_0)$，极值允许为非严格极值：在某邻域内，$f(x,y)\ge f(x_0,y_0)$ 为极小值，$f(x,y)\le f(x_0,y_0)$ 为极大值。

#### 必要条件与可疑点 <span id="section-4-8-1"></span>

若 $f$ 在 $(x_0,y_0)$ 处的一阶偏导数存在，且在该点取得极值，则

$$
\boxed{f_x(x_0,y_0)=0,\qquad f_y(x_0,y_0)=0}.
$$

两偏导数均为零的点称为**驻点** 。驻点不一定是极值点，如 $f(x,y)=x^2-y^2$ 的原点。

**极值可疑点包括驻点和至少一个一阶偏导数不存在的点。** 偏导数不存在的点也可能取得极值，如 $f(x,y)=\sqrt{x^2+y^2}$ 在原点取得严格极小值，$f(x,y)=|x+y|$ 在原点取得非严格极小值。必要条件同样适用于三元及更多元函数：各一阶偏导数存在时，极值点处均为零。

#### 二阶偏导数判别法（充分条件） <span id="section-4-8-2"></span>

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

### 方向导数：先将方向向量单位化（仅数学一） <span id="section-4-9"></span>

设 $P_0=(x_0,y_0,z_0)$，方向 $l$ 的单位向量为

$$
\boldsymbol e=(\cos\alpha,\cos\beta,\cos\gamma),\qquad |\boldsymbol e|=1.
$$

沿从 $P_0$ 出发的射线，方向导数定义为

$$
\boxed{D_{\boldsymbol e}u(P_0)
=\lim_{t\to0^+}\frac{u(P_0+t\boldsymbol e)-u(P_0)}{t}}.
$$

分母 $t$ 表示沿该方向走过的距离。若 $u$ 在 $P_0$ **可微**，则

$$
\boxed{D_{\boldsymbol e}u(P_0)
=u_x(P_0)\cos\alpha+u_y(P_0)\cos\beta+u_z(P_0)\cos\gamma}.
$$

由全增量公式 $u(P_0+t\boldsymbol e)-u(P_0)=t(u_x\cos\alpha+u_y\cos\beta+u_z\cos\gamma)+o(t)$，除以 $t$ 取极限即得。

若题目给出非零向量 $\boldsymbol v=(a,b,c)$，须先取

$$
\boldsymbol e=\frac{\boldsymbol v}{|\boldsymbol v|}
=\frac{(a,b,c)}{\sqrt{a^2+b^2+c^2}}.
$$

给出从 $A$ 指向 $B$ 的方向时，用 $\overrightarrow{AB}=B-A$，再单位化。二元函数同理：$D_{\boldsymbol e}u=u_x\cos\alpha+u_y\sin\alpha$，其中 $\alpha$ 为有向方向与 $x$ 轴正向的角。

**条件：** 仅有偏导数存在，不能保证上述计算公式成立；不可微时应回到定义。对可微函数，反向后的方向导数变号。

### 梯度与方向导数的最大值（仅数学一） <span id="section-4-10"></span>

对可微标量函数 $u$，梯度为向量

$$
\boxed{\operatorname{grad}u=\nabla u=(u_x,u_y,u_z)}.
$$

因此，对任意单位方向 $\boldsymbol e$，

$$
\boxed{D_{\boldsymbol e}u=\nabla u\cdot\boldsymbol e
=|\nabla u|\cos\theta},
$$

其中 $\theta$ 为非零梯度与该方向的夹角。在固定点处：

| 方向（梯度非零时） | 方向导数 | 含义 |
| --- | --- | --- |
| $\boldsymbol e=\nabla u/|\nabla u|$ | $|\nabla u|$ | 增长最快，取得最大值 |
| $\boldsymbol e=-\nabla u/|\nabla u|$ | $-|\nabla u|$ | 减小最快，取得最小值 |
| $\boldsymbol e\perp\nabla u$ | $0$ | 沿该方向的一阶变化率为零 |

若 $\nabla u(P_0)=\boldsymbol0$，所有方向导数都为 $0$，此时不能指定唯一的最快增长方向，也不能仅据此判断极值。

**几何意义：** 在正则等值面 $u(x,y,z)=C$ 上，$\nabla u\ne\boldsymbol0$ 时，梯度垂直于该点的切平面；二元函数的梯度垂直于正则等值曲线。

常用运算（函数可微，商式另须 $v\ne0$）：

$$
\begin{aligned}
\nabla(u\pm v)&=\nabla u\pm\nabla v,\\
\nabla(uv)&=v\nabla u+u\nabla v,\\
\nabla\left(\frac uv\right)&=\frac{v\nabla u-u\nabla v}{v^2},\\
\nabla\varphi(u)&=\varphi'(u)\nabla u.
\end{aligned}
$$

### 向量场的散度与旋度（仅数学一） <span id="section-4-11"></span>

设向量场 $\boldsymbol A=P\boldsymbol i+Q\boldsymbol j+R\boldsymbol k$ 具有连续一阶偏导数。

**散度是标量：**

$$
\boxed{\operatorname{div}\boldsymbol A
=\nabla\cdot\boldsymbol A=P_x+Q_y+R_z}.
$$

散度反映单位体积的净流出强度；正值表示局部净流出，负值表示局部净流入。

**旋度是向量：**

$$
\boxed{\operatorname{rot}\boldsymbol A
=\nabla\times\boldsymbol A
=\begin{vmatrix}
\boldsymbol i&\boldsymbol j&\boldsymbol k\\
\partial/\partial x&\partial/\partial y&\partial/\partial z\\
P&Q&R
\end{vmatrix}
=(R_y-Q_z,\ P_z-R_x,\ Q_x-P_y)}.
$$

旋度描述局部旋转的方向与强度。**记忆：标量函数求梯度得到向量；向量场求散度得到标量，求旋度得到向量。**

## <span style="color: #3498db;">第五部分：重积分</span> <span id="section-5"></span>

### 被积函数为 1：二重积分等于区域面积 <span id="section-5-1"></span>

设 $D$ 为有界闭区域，面积为 $A$，则

$$
\boxed{\iint_D1\,\mathrm d\sigma=\iint_D1\,\mathrm dx\,\mathrm dy=A},
\qquad \mathrm d\sigma=\mathrm dx\,\mathrm dy.
$$

**记忆：被积函数为 $1$ 时，二重积分就是积分区域的面积。** 更一般地，对常数 $c$，有 $\iint_Dc\,\mathrm d\sigma=cA$。

### 二重积分的保序性与保号性 <span id="section-5-2"></span>

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

#### 绝对值不等式 <span id="section-5-2-1"></span>

由 $-|f(x,y)|\le f(x,y)\le|f(x,y)|$，得

$$
\boxed{\left|\iint_Df(x,y)\,\mathrm d\sigma\right|
\le\iint_D|f(x,y)|\,\mathrm d\sigma}.
$$

### 二重积分的估值定理 <span id="section-5-3"></span>

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

### 二重积分的中值定理 <span id="section-5-4"></span>

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

### 二重积分的对称性 <span id="section-5-5"></span>

设 $f(x,y)$ 在 $D$ 上可积。使用下列公式时，须先确认**积分区域关于相应的轴、直线或点对称** ，再比较两个对称点处的函数值。

**记忆：对称点处函数值相同，取对称的一半区域积分后乘 $2$；函数值相反，积分为 $0$。** 以下各式中的 $D_1$ 均按相应的对称方式选取。

#### ① 关于 y 轴对称 <span id="section-5-5-1"></span>

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

#### 补充：关于直线 x = a 对称 <span id="section-5-5-2"></span>

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

#### ② 关于 x 轴对称 <span id="section-5-5-3"></span>

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

#### 补充：关于直线 y = a 对称 <span id="section-5-5-4"></span>

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

#### ③ 关于原点对称 <span id="section-5-5-5"></span>

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

#### ④ 关于直线 y = x 对称 <span id="section-5-5-6"></span>

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

### 二重积分的轮换对称性（交换 x、y） <span id="section-5-6"></span>

设 $D$ 关于直线 $y=x$ 对称，即交换 $x,y$ 后区域不变，且 $f$ 在 $D$ 上可积，则

$$
\boxed{\iint_Df(x,y)\,\mathrm d\sigma
=\iint_Df(y,x)\,\mathrm d\sigma}.
$$

**轮换对称性只要求区域在交换 $x,y$ 后不变，不要求 $f(x,y)=f(y,x)$。** 交换后得到的两个被积函数可以不同，但在同一区域上的积分相等。常见适用区域有圆盘 $x^2+y^2\le R^2$、正方形 $[a,b]\times[a,b]$、三角形 $x\ge0,\ y\ge0,\ x+y\le a$（$a>0$）。

#### 常用方法：交换后相加，再除以 2 <span id="section-5-6-1"></span>

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

### 二重积分的一般换元公式与雅可比行列式 <span id="section-5-7"></span>

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

#### 换元时三处一起换 <span id="section-5-7-1"></span>

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

### 二重积分的极坐标换元 <span id="section-5-8"></span>

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

## <span style="color: #3498db;">第六部分：微分方程</span> <span id="section-6"></span>

### 考试选法：先看阶数，再看结构 <span id="section-6-1"></span>

**拿到题先看最高阶导数，再看能否分离变量、是否线性、系数是否为常数、是否缺少某个变量。** 初始条件一般在求出解的形式后使用，用来确定常数、分支和解所在区间。

#### 一阶方程怎么选 <span id="section-6-1-1"></span>

按下面的顺序尝试，哪种结构明显就优先用哪种；同一道题可能有不止一种解法。

1. **能否直接分离变量？** 能写成 $y'=f(x)g(y)$，就把含 $y$ 的项和 $\mathrm dy$ 放一侧，含 $x$ 的项和 $\mathrm dx$ 放另一侧。
2. **右端是否只含 $y/x$？** 若为 $y'=\varphi(y/x)$，用齐次型换元 $u=y/x$。例如 $y'=1+(y/x)^2$。
3. **是否对未知函数及其导数线性？** 能写成 $y'+p(x)y=q(x)$，直接用一阶线性通解；其中 $p,q$ 只能依赖自变量 $x$。
4. **交换 x、y 后是否更简单？** 若能写成 $\mathrm dx/\mathrm dy+P(y)x=Q(y)$，就把 $x$ 当作 $y$ 的函数，套线性公式。例如 $y\,\mathrm dx+(x-3y^2)\,\mathrm dy=0$。
5. **是否只多了一个 $y^n$？** 若为 $y'+p(x)y=q(x)y^n$，用伯努利换元 $z=y^{1-n}$，再解线性方程。

若原题给成 $P\,\mathrm dx+Q\,\mathrm dy=0$，且 $P_y,Q_x$ 容易计算，也可先检查是否为全微分方程。**齐次型与一阶线性不是互斥类别；能用更短的方法就优先选更短的方法。**

#### 二阶及高阶方程怎么选 <span id="section-6-1-2"></span>

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

#### 非齐次方程的特解怎么设 <span id="section-6-1-3"></span>

对 $y''+py'+qy=f(x)$，先求特征根，再看右端：

- **多项式：** 按 $e^{0x}P_n(x)$ 处理，设 $y_p=x^kQ_n(x)$，比较 $0$ 是否为特征根。
- **指数乘多项式：** $f(x)=e^{\alpha x}P_n(x)$，设 $y_p=x^ke^{\alpha x}Q_n(x)$，$k$ 为 $\alpha$ 的特征根重数，不是根则取 $0$。
- **指数乘正弦、余弦：** 比较 $\alpha\pm\beta i$ 与特征根，设 $y_p=x^ke^{\alpha x}[Q(x)\cos\beta x+R(x)\sin\beta x]$。
- **几类函数相加：** 分别求特解，再相加。

**记忆：看右端、算根、查重复；重复几次，补几个 $x$。** 多项式的低次项要写全，三角型的正弦、余弦两项通常都要设。

#### 考场上的易错检查 <span id="section-6-1-4"></span>

- **线性看未知函数：** $y'+xy=x^2$ 是线性方程；$y'+y^2=x$ 含 $y^2$，不属于一阶线性方程。
- **两个“齐次”分清：** $y'=\varphi(y/x)$ 是齐次型；$y'+p(x)y=0$ 是线性齐次方程，识别标准不同。
- **换元记清自变量：** $v=v(x)$ 时 $y''=v'$；$v=v(y)$ 时 $y''=v\,\mathrm dv/\mathrm dy$。
- **除法之后查丢解：** 除以 $y$、$y'$、$g(y)$ 等之前，先记录它们等于 $0$ 的情形。
- **最后再用初始条件：** 如得到 $y=\pm\sqrt{x}$，还须用给定点选择分支；对数、根式及 $x=0$ 等限制也要检查。

### 可分离变量方程与丢解检查 <span id="section-6-2"></span>

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

### 齐次型微分方程：令 u = y/x <span id="section-6-3"></span>

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

### 一阶线性微分方程的通解 <span id="section-6-4"></span>

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

#### 当 p(x) 的积分为 ln|φ(x)| 时，可去掉通解中的绝对值 <span id="section-6-4-1"></span>

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

#### 使用时注意 <span id="section-6-4-2"></span>

- **先把 $y'$ 的系数化为 $1$，再识别 $p(x),q(x)$。** 对 $a(x)y'+b(x)y=c(x)$，须在 $a(x)\ne0$ 的区间上先除以 $a(x)$，此时 $p(x)=b(x)/a(x)$、$q(x)=c(x)/a(x)$。
- $p(x)$ 是标准形中 $y$ 的系数，须保留其正负号。例如 $y'-2y=x$ 中，$p(x)=-2$，积分因子为 $e^{-2x}$。
- 当 $q(x)\equiv0$ 时，方程为一阶线性齐次方程，通解简化为 $\boxed{y=Ce^{-\int p(x)\,\mathrm dx}}$。
- 选取 $P(x)$ 时不必另加任意常数；更换原函数只会改变常数的表示，最终统一写一个任意常数 $C$。

### 交换自变量与因变量：把 x 看成 y 的函数 <span id="section-6-5"></span>

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

### 伯努利方程：令 z = y 的 1−n 次方 <span id="section-6-6"></span>

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

### 二阶可降阶微分方程 <span id="section-6-7"></span>

以下各式均在相应函数有定义的区间内使用。按图片中的分类，这类内容标注为数学一、数学二。

#### 不显含 y：y″ = F(x, y′) <span id="section-6-7-1"></span>

令 $v(x)=y'(x)$，则

$$
\boxed{\frac{\mathrm dv}{\mathrm dx}=F(x,v)}.
$$

先解一阶方程得到 $v=\psi(x,C_1)$，再积分：

$$
\boxed{y=\int\psi(x,C_1)\,\mathrm dx+C_2}.
$$

#### 不显含 x：y″ = F(y, y′) <span id="section-6-7-2"></span>

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

#### 特例：y″ = F(y) <span id="section-6-7-3"></span>

可先降阶积分为

$$
\boxed{\frac12(y')^2=\int F(y)\,\mathrm dy+C_1},
$$

再依据初始条件和所讨论的区间选择 $y'$ 的分支，求解一阶方程。

### 全微分方程（恰当方程） <span id="section-6-8"></span>

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

### 二阶常系数齐次线性微分方程 <span id="section-6-9"></span>

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

### 线性微分方程解的结构与叠加原理 <span id="section-6-10"></span>

记 $L[y]=y''+py'+qy$，对应齐次方程为 $L[y]=0$。

- 若 $Y$ 为对应齐次方程的通解，$y_p$ 为 $L[y]=f(x)$ 的一个特解，则非齐次方程的通解为 $\boxed{y=Y+y_p}$。
- 若 $L[u]=L[v]=f(x)$，则 $\boxed{L[u-v]=0}$：同一非齐次方程的两个特解之差是对应齐次方程的解。
- 若 $L[u]=f_1(x)$、$L[v]=f_2(x)$，则 $\boxed{L[au+bv]=af_1(x)+bf_2(x)}$，其中 $a,b$ 为常数。
- 对齐次方程，解的任意线性组合仍为解；对同一个非齐次方程，两个解直接相加通常使右端变成 $2f(x)$。

### 待定系数法：指数乘多项式 <span id="section-6-11"></span>

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

### 待定系数法：指数乘正弦、余弦及多项式 <span id="section-6-12"></span>

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

### n 阶常系数齐次线性方程：由特征根写通解 <span id="section-6-13"></span>

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

### 欧拉方程：令 t = ln|x| <span id="section-6-14"></span>

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

## <span style="color: #3498db;">第七部分：无穷级数</span> <span id="section-7"></span>

### 无穷级数与部分和：用部分和的极限定义级数的和 <span id="section-7-1"></span>

给定数列 $\{u_n\}$，称

$$
\sum_{n=1}^{\infty}u_n=u_1+u_2+\cdots+u_n+\cdots
$$

为无穷级数，$u_n$ 为其通项。前 $n$ 项之和称为**部分和**：

$$
\boxed{S_n=\sum_{k=1}^{n}u_k=u_1+u_2+\cdots+u_n}.
$$

若部分和数列 $\{S_n\}$ 有有限极限 $S$，则称级数收敛，其和为 $S$，即

$$
\boxed{\lim_{n\to\infty}S_n=S=\sum_{n=1}^{\infty}u_n}.
$$

若 $\{S_n\}$ 没有有限极限，则称级数发散，包括部分和趋于正、负无穷或振荡的情况。

**记忆：级数的敛散性取决于部分和 $S_n$ 在 $n\to\infty$ 时是否有有限极限。**

### 等比级数（几何级数） <span id="section-7-2"></span>

设首项 $a\ne0$、公比为 $q$，则等比级数为

$$
\sum_{n=1}^{\infty}aq^{n-1}=a+aq+aq^2+\cdots.
$$

当 $q\ne1$ 时，其部分和为

$$
\boxed{S_n=\frac{a(1-q^n)}{1-q}}.
$$

因此有

$$
\boxed{
\begin{cases}
\displaystyle\sum_{n=1}^{\infty}aq^{n-1}=\dfrac{a}{1-q},&|q|<1,\\[6pt]
\displaystyle\sum_{n=1}^{\infty}aq^{n-1}\text{ 发散},&|q|\ge1.
\end{cases}
}
$$

**记忆：公比绝对值小于 $1$ 才收敛，和为“首项除以 $1$ 减公比”。** 若 $a=0$，则各项均为 $0$，级数收敛且和为 $0$。

### 无穷级数的基本性质 <span id="section-7-3"></span>

#### 性质 1：收敛级数的线性组合仍收敛 <span id="section-7-3-1"></span>

若 $\displaystyle\sum_{n=1}^{\infty}u_n$ 与 $\displaystyle\sum_{n=1}^{\infty}v_n$ 均收敛，则对任意常数 $a,b$，有

$$
\boxed{
\sum_{n=1}^{\infty}(au_n\pm bv_n)
=a\sum_{n=1}^{\infty}u_n\pm b\sum_{n=1}^{\infty}v_n
}.
$$

即两个收敛级数可以逐项相加、相减，也可以乘常数。

| 逐项相加或相减的两个级数 | 所得级数的敛散性             |
| ------------------------ | ---------------------------- |
| 收敛与收敛               | 收敛                         |
| 收敛与发散               | 发散                         |
| 发散与发散               | 不一定，可能收敛，也可能发散 |

#### 性质 2：改变有限项不影响敛散性 <span id="section-7-3-2"></span>

改变、增加或删去级数的任意有限项，**不会改变级数的敛散性**，但可能改变收敛级数的和。

例如，去掉前 $m$ 项后，尾级数与原级数同敛散；原级数收敛时，尾级数的和等于原级数的和减去前 $m$ 项之和。

#### 性质 3：收敛级数加括号后仍收敛，且和不变 <span id="section-7-3-3"></span>

加括号指保持原有顺序，把相邻的有限项合并成一项。若 $\displaystyle\sum_{n=1}^{\infty}u_n$ 收敛，则加括号后的级数仍收敛，且其和不变。例如

$$
\boxed{
\sum_{n=1}^{\infty}(u_{2n-1}+u_{2n})
=(u_1+u_2)+(u_3+u_4)+\cdots
=\sum_{n=1}^{\infty}u_n
}.
$$

由此得到逆否命题：

$$
\boxed{\text{加括号后的级数发散}\ \Longrightarrow\ \text{原级数发散}}.
$$

**重点记忆：加括号后发散，则原级数一定发散；加括号后收敛，原级数不一定收敛。**

反例：原级数 $1-1+1-1+\cdots$ 发散，但加括号后 $(1-1)+(1-1)+\cdots=0$ 收敛。

#### 性质 4：级数收敛的必要条件是通项趋于零 <span id="section-7-3-4"></span>

$$
\boxed{\sum_{n=1}^{\infty}u_n\text{ 收敛}\ \Longrightarrow\ \lim_{n\to\infty}u_n=0}.
$$

因为收敛时 $S_n\to S$，所以 $u_n=S_n-S_{n-1}\to S-S=0$。

反过来，若通项不趋于 $0$（极限非零或不存在），则级数一定发散：

$$
\boxed{u_n\not\to0\ \Longrightarrow\ \sum_{n=1}^{\infty}u_n\text{ 发散}}.
$$

**注意：通项趋于零只是收敛的必要条件，不是充分条件。** 例如调和级数 $\displaystyle\sum_{n=1}^{\infty}\frac1n$ 发散，虽然 $\displaystyle\lim_{n\to\infty}\frac1n=0$。

### 正项级数及其敛散性判别 <span id="section-7-4"></span>

#### 正项级数的定义 <span id="section-7-4-1"></span>

若通项 $u_n\ge0$，$n=1,2,\ldots$，则称

$$
\boxed{\sum_{n=1}^{\infty}u_n\text{ 为正项级数}}.
$$

其部分和 $S_n=\displaystyle\sum_{k=1}^{n}u_k$ 满足

$$
S_{n+1}-S_n=u_{n+1}\ge0,
$$

因此，**正项级数的部分和数列 $\{S_n\}$ 单调非减。**

#### 收敛原则：部分和数列有界是收敛的充要条件 <span id="section-7-4-2"></span>

$$
\boxed{
\sum_{n=1}^{\infty}u_n\text{ 收敛}
\iff \{S_n\}\text{ 有界}
}.
$$

由于 $S_n\ge0$，这里有界等价于**有上界**，即存在与 $n$ 无关的常数 $M$，使得

$$
\boxed{S_n=\sum_{k=1}^{n}u_k\le M,\qquad\forall n\ge1}.
$$

**理由：部分和数列单调非减，有上界时由单调有界定理可知其有有限极限；反之，部分和数列收敛则必有界。**

若正项级数的部分和数列无上界，则 $S_n\to+\infty$，级数发散。

#### 比较判别法 <span id="section-7-4-3"></span>

给定两个正项级数 $\displaystyle\sum_{n=1}^{\infty}u_n$ 和 $\displaystyle\sum_{n=1}^{\infty}v_n$，若从某一项起有

$$
\boxed{0\le u_n\le v_n,\qquad n\ge N},
$$

则有：

$$
\boxed{
\sum_{n=1}^{\infty}v_n\text{ 收敛}
\quad\Longrightarrow\quad
\sum_{n=1}^{\infty}u_n\text{ 收敛}
},
$$

$$
\boxed{
\sum_{n=1}^{\infty}u_n\text{ 发散}
\quad\Longrightarrow\quad
\sum_{n=1}^{\infty}v_n\text{ 发散}
}.
$$

**记忆：大级数收敛，小级数也收敛；小级数发散，大级数也发散。**

只需从某一项起满足大小关系，因为前面的有限项不影响级数的敛散性。

**注意：大级数发散，不能据此判定小级数；小级数收敛，也不能据此判定大级数。**

#### 比较判别法的极限形式 <span id="section-7-4-4"></span>

给定两个正项级数 $\displaystyle\sum_{n=1}^{\infty}u_n$ 和 $\displaystyle\sum_{n=1}^{\infty}v_n$，其中 $v_n>0$。设

$$
\boxed{\lim_{n\to\infty}\frac{u_n}{v_n}=A}.
$$

根据 $A$ 的取值，分为三种情况：

| 比值极限      | 可以得到的结论                           |
| ------------- | ---------------------------------------- |
| $A=0$         | 若 $\sum v_n$ 收敛，则 $\sum u_n$ 也收敛 |
| $A=+\infty$   | 若 $\sum v_n$ 发散，则 $\sum u_n$ 也发散 |
| $0<A<+\infty$ | $\sum u_n$ 与 $\sum v_n$ 同敛散          |

特别地，当 $u_n\sim v_n$，即 $A=1$ 时，两个正项级数同敛散。

**记忆：同阶正项同敛散；若 $u_n$ 比 $v_n$ 小得多，用 $v_n$ 的收敛推 $u_n$ 收敛；若 $u_n$ 比 $v_n$ 大得多，用 $v_n$ 的发散推 $u_n$ 发散。** 表格前两种情况均不能随意反推。

#### 比值判别法（达朗贝尔判别法） <span id="section-7-4-5"></span>

设 $\displaystyle\sum_{n=1}^{\infty}u_n$ 为正项级数，且从某一项起 $u_n>0$。若

$$
\boxed{\lim_{n\to\infty}\frac{u_{n+1}}{u_n}=\rho},
$$

则

$$
\boxed{
\begin{cases}
\displaystyle\sum_{n=1}^{\infty}u_n\text{ 收敛},&0\le\rho<1,\\[4pt]
\displaystyle\sum_{n=1}^{\infty}u_n\text{ 发散},&\rho>1\text{（含 }+\infty\text{）}.
\end{cases}
}
$$

**注意：$\rho=1$ 时，比值判别法不能判定敛散性。** 例如 $\sum1/n$ 发散、$\sum1/n^2$ 收敛，但两者的相邻项比值极限均为 $1$。

**适用提示：通项含阶乘、指数或连乘积时，先尝试计算相邻项的比值，往往便于约分。**

#### 根值判别法（柯西判别法） <span id="section-7-4-6"></span>

设 $\displaystyle\sum_{n=1}^{\infty}u_n$ 为正项级数。若

$$
\boxed{\lim_{n\to\infty}\sqrt[n]{u_n}=\rho},
$$

则

$$
\boxed{
\begin{cases}
\displaystyle\sum_{n=1}^{\infty}u_n\text{ 收敛},&0\le\rho<1,\\[4pt]
\displaystyle\sum_{n=1}^{\infty}u_n\text{ 发散},&\rho>1\text{（含 }+\infty\text{）}.
\end{cases}
}
$$

当 $\rho<1$ 时，可取 $\rho<q<1$，由极限的定义，从某一项起有

$$
0\le\sqrt[n]{u_n}<q
\quad\Longrightarrow\quad0\le u_n<q^n.
$$

因为等比级数 $\sum q^n$ 收敛，由比较判别法可知 $\sum u_n$ 收敛。

**注意：$\rho=1$ 时，根值判别法也不能判定敛散性。** 例如 $\sum1/n$ 与 $\sum1/n^2$ 的根值极限均为 $1$，但敛散性不同。

**记忆：比值、根值都与 $1$ 比较，小于 $1$ 收敛，大于 $1$ 发散，等于 $1$ 无法判定。** 通项整体含 $n$ 次幂时，根值法通常便于化简。

#### 积分判别法 <span id="section-7-4-7"></span>

设 $\displaystyle\sum_{n=1}^{\infty}u_n$ 为正项级数。若存在定义在 $[1,+\infty)$ 上的**非负、连续、单调非增**函数 $f(x)$，使得

$$
u_n=f(n),\qquad n=1,2,\ldots,
$$

则级数与对应反常积分同敛散：

$$
\boxed{
\sum_{n=1}^{\infty}u_n\text{ 收敛}
\iff\int_1^{+\infty}f(x)\,\mathrm dx\text{ 收敛}
}.
$$

由 $f$ 非负且单调非增，可比较矩形面积与曲线下方面积，得到

$$
\boxed{
\int_1^{N+1}f(x)\,\mathrm dx
\le\sum_{n=1}^{N}f(n)
\le f(1)+\int_1^N f(x)\,\mathrm dx
}.
$$

因此，部分和是否有上界，与反常积分是否收敛一致。

**注意：积分判别法判断的是同敛散，不表示级数的和等于积分值。** 若上述条件只从某个正整数起成立，也可从该处开始使用积分判别法，有限项不影响敛散性。

### 调和级数与相邻项的调和平均数 <span id="section-7-5"></span>

调和级数为

$$
\boxed{\sum_{n=1}^{\infty}\frac1n
=1+\frac12+\frac13+\cdots\text{，发散}}.
$$

两个正数 $a,b$ 的调和平均数为

$$
\boxed{H(a,b)=\frac{2}{\frac1a+\frac1b}=\frac{2ab}{a+b}}.
$$

对调和级数的通项 $u_n=\dfrac1n$，从第二项起，每一项都是左右相邻两项的调和平均数：

$$
\boxed{
H(u_{n-1},u_{n+1})
=\frac{2}{\frac1{u_{n-1}}+\frac1{u_{n+1}}}
=\frac{2}{(n-1)+(n+1)}
=\frac1n=u_n
},\qquad n\ge2.
$$

### p 级数及其敛散性（重点记忆） <span id="section-7-6"></span>

级数

$$
\boxed{\sum_{n=1}^{\infty}\frac1{n^p}}
$$

称为 **$p$ 级数**，其中 $p$ 为实数。调和级数 $\displaystyle\sum_{n=1}^{\infty}\frac1n$ 是 $p=1$ 时的特殊情况。

其敛散性为

$$
\boxed{
\sum_{n=1}^{\infty}\frac1{n^p}
\begin{cases}
\text{发散},&p\le1,\\
\text{收敛},&p>1.
\end{cases}
}
$$

**记忆：以 $1$ 为分界，$p>1$ 收敛，$p\le1$ 发散；边界 $p=1$ 的调和级数发散。**

可与下列反常积分对照记忆：

$$
\boxed{
\int_1^{+\infty}\frac1{x^p}\,\mathrm dx
\begin{cases}
\text{发散},&p\le1,\\
\text{收敛，值为 }\dfrac1{p-1},&p>1.
\end{cases}
}
$$

注意：上述级数与反常积分的敛散条件相同，但不能据此认为收敛时两者的值相等。

### 交错级数与莱布尼茨判别法 <span id="section-7-7"></span>

形如

$$
\sum_{n=1}^{\infty}(-1)^{n-1}u_n
=u_1-u_2+u_3-u_4+\cdots,\qquad u_n>0,
$$

的级数称为**交错级数**。

若同时满足以下两个条件：

1. $\{u_n\}$ 单调非增，即 $u_{n+1}\le u_n$；
2. $\displaystyle\lim_{n\to\infty}u_n=0$；

则由莱布尼茨判别法，有

$$
\boxed{
\left.
\begin{gathered}
u_{n+1}\le u_n,\\
\lim_{n\to\infty}u_n=0
\end{gathered}
\right\}
\quad\Longrightarrow\quad
\sum_{n=1}^{\infty}(-1)^{n-1}u_n\text{ 收敛}
}.
$$

**记忆：交错级数，正的幅值单调不增且趋于零，则收敛。** 只要从某一项起单调非增即可，有限项不影响敛散性。

判断单调性时，可以直接比较 $u_{n+1}$ 与 $u_n$；若能写成 $u_n=f(n)$，也可通过 $f'(x)$ 的符号判断。

**注意：这两个条件合起来是收敛的充分条件。** 若 $u_n$ 不单调，不能直接判定级数发散；但若 $u_n$ 不趋于 $0$，则由级数收敛的必要条件可知交错级数一定发散。

### 绝对收敛与条件收敛 <span id="section-7-8"></span>

设 $\displaystyle\sum_{n=1}^{\infty}u_n$ 为任意项级数。

**绝对收敛：** 若加绝对值后的级数收敛，即

$$
\boxed{\sum_{n=1}^{\infty}|u_n|\text{ 收敛}},
$$

则称 $\displaystyle\sum_{n=1}^{\infty}u_n$ **绝对收敛**。

**条件收敛：** 若原级数收敛，但加绝对值后的级数发散，即

$$
\boxed{
\sum_{n=1}^{\infty}u_n\text{ 收敛，且 }
\sum_{n=1}^{\infty}|u_n|\text{ 发散}
},
$$

则称 $\displaystyle\sum_{n=1}^{\infty}u_n$ **条件收敛**。

#### 绝对收敛必收敛 <span id="section-7-8-1"></span>

$$
\boxed{
\sum_{n=1}^{\infty}|u_n|\text{ 收敛}
\quad\Longrightarrow\quad
\sum_{n=1}^{\infty}u_n\text{ 收敛}
}.
$$

**记忆：加绝对值后收敛，则原级数一定收敛。** 反过来不一定成立，条件收敛就是反例。

判断步骤：先考察 $\sum|u_n|$；若收敛，原级数绝对收敛；若发散，还需判断 $\sum u_n$，原级数收敛才称为条件收敛。

#### 收敛级数逐项相加的结论 <span id="section-7-8-2"></span>

以下“和”指逐项相加得到的级数 $\displaystyle\sum_{n=1}^{\infty}(u_n+v_n)$。

| $\sum u_n$ | $\sum v_n$ | $\sum(u_n+v_n)$                        |
| ---------- | ---------- | -------------------------------------- |
| 绝对收敛   | 绝对收敛   | 绝对收敛                               |
| 绝对收敛   | 条件收敛   | 条件收敛                               |
| 条件收敛   | 条件收敛   | 一定收敛，可能绝对收敛，也可能条件收敛 |

第一条由 $|u_n+v_n|\le|u_n|+|v_n|$ 得到。第二条中，若和级数绝对收敛，由 $|v_n|\le|u_n+v_n|+|u_n|$ 就会推出 $\sum|v_n|$ 收敛，与条件收敛矛盾。

两个条件收敛级数相加时，例如取 $u_n=(-1)^{n-1}/n$：若 $v_n=-u_n$，则和级数各项为 $0$，绝对收敛；若 $v_n=u_n$，则和级数为 $\sum2(-1)^{n-1}/n$，仍条件收敛。

### 交错 p 级数的敛散性 <span id="section-7-9"></span>

$$
\boxed{
\sum_{n=1}^{\infty}(-1)^{n-1}\frac1{n^p}
\begin{cases}
\text{绝对收敛},&p>1,\\
\text{条件收敛},&0<p\le1,\\
\text{发散},&p\le0.
\end{cases}
}
$$

当 $p>0$ 时，$1/n^p$ 单调递减且趋于 $0$，由莱布尼茨判别法知交错级数收敛；加绝对值后为 $p$ 级数，仅在 $p>1$ 时收敛。当 $p\le0$ 时，通项不趋于 $0$，故发散。

**重点例子：交错调和级数 $\displaystyle\sum_{n=1}^{\infty}\frac{(-1)^{n-1}}n$ 条件收敛。**

### 函数项级数、收敛点与收敛域 <span id="section-7-10"></span>

设各函数 $u_n(x)$ 定义在公共集合 $I$ 上，则

$$
\sum_{n=0}^{\infty}u_n(x)
=u_0(x)+u_1(x)+u_2(x)+\cdots
$$

称为**函数项级数**。固定 $x=\xi\in I$ 后，它就成为一个数项级数 $\sum u_n(\xi)$。

- 若 $\sum u_n(\xi)$ 收敛，称 $\xi$ 为该函数项级数的**收敛点**。
- 若 $\sum u_n(\xi)$ 发散，称 $\xi$ 为该函数项级数的**发散点**。
- 所有收敛点组成的集合称为该函数项级数的**收敛域**，即

  $$
  \boxed{D=\left\{x\in I:\sum_{n=0}^{\infty}u_n(x)\text{ 收敛}\right\}}.
  $$

**注意：一般函数项级数的收敛域不一定是区间。** 幂级数的收敛域具有下面所述的特殊结构。

### 幂级数的定义与系数 <span id="section-7-11"></span>

形如

$$
\boxed{
\sum_{n=0}^{\infty}a_n(x-x_0)^n
=a_0+a_1(x-x_0)+a_2(x-x_0)^2+\cdots
}
$$

的函数项级数称为**以 $x_0$ 为中心的幂级数**，其中 $a_n$ 为与 $x$ 无关的常数，称为幂级数的**系数**。

当 $x_0=0$ 时，标准形式为

$$
\boxed{\sum_{n=0}^{\infty}a_nx^n
=a_0+a_1x+a_2x^2+\cdots+a_nx^n+\cdots}.
$$

**要点：系数可以依赖 $n$，不能依赖 $x$；常数项对应 $n=0$。** 实际级数也可以从 $n=1$、$n=2$ 等开始，缺少的幂次按系数为 $0$ 处理。例如，系数中含 $\ln n$ 时须注意起始下标和分母是否有定义。

### 幂级数的阿贝尔定理：收敛点以内绝对收敛 <span id="section-7-12"></span>

考虑幂级数 $\displaystyle\sum_{n=0}^{\infty}a_nx^n$。

#### 在一点收敛，则该点以内绝对收敛 <span id="section-7-12-1"></span>

若级数在 $x=x_1\ne0$ 处收敛，则对满足 $|x|<|x_1|$ 的一切 $x$，都有

$$
\boxed{\sum_{n=0}^{\infty}a_nx^n\text{ 绝对收敛}}.
$$

**证明：** 由 $\sum a_nx_1^n$ 收敛，得 $a_nx_1^n\to0$，所以存在 $M>0$ 使 $|a_nx_1^n|\le M$。令 $q=|x/x_1|<1$，则

$$
|a_nx^n|=|a_nx_1^n|\left|\frac{x}{x_1}\right|^n
\le Mq^n.
$$

由等比级数 $\sum Mq^n$ 收敛及比较判别法，结论成立。

#### 在一点发散，则该点以外发散 <span id="section-7-12-2"></span>

若级数在 $x=x_2\ne0$ 处发散，则对满足 $|x|>|x_2|$ 的一切 $x$，都有

$$
\boxed{\sum_{n=0}^{\infty}a_nx^n\text{ 发散}}.
$$

**理由：** 若某个满足 $|x|>|x_2|$ 的点处收敛，由上一结论，在其内部的 $x_2$ 处应绝对收敛，与已知矛盾。

**记忆：一点收敛，内部绝对收敛；一点发散，外部全部发散。** 这里的“内部、外部”按到展开中心的距离判断；等号处不能由定理直接判断。

对一般形式 $\sum a_n(x-x_0)^n$，相应地将条件改为

$$
|x-x_0|<|x_1-x_0|\quad\text{或}\quad
|x-x_0|>|x_2-x_0|.
$$

### 幂级数的收敛半径与端点 <span id="section-7-13"></span>

对幂级数 $\displaystyle\sum_{n=0}^{\infty}a_n(x-x_0)^n$，存在收敛半径 $R\in[0,+\infty]$，使得

$$
\boxed{
\begin{cases}
|x-x_0|<R\text{ 时，绝对收敛},\\
|x-x_0|>R\text{ 时，发散}.
\end{cases}
}
$$

- $R=0$：只在中心 $x=x_0$ 处收敛。
- $R=+\infty$：在整个实数轴上绝对收敛。
- $0<R<+\infty$：先确定开区间 $(x_0-R,x_0+R)$，再把两个端点分别代回原级数判断。

有限正收敛半径时，收敛域可能为

$$
(x_0-R,x_0+R),\quad [x_0-R,x_0+R),\quad
(x_0-R,x_0+R],\quad [x_0-R,x_0+R].
$$

**端点可以绝对收敛、条件收敛或发散，必须分别检查。** 幂级数若条件收敛，只可能出现在有限正收敛半径对应的端点。

#### 由已知点的敛散性估计收敛半径 <span id="section-7-13-1"></span>

对 $\displaystyle\sum_{n=0}^{\infty}a_n(x-x_0)^n$，若已知它在 $x=x_1$ 处的敛散性，则

$$
\boxed{
\begin{aligned}
x_1\text{ 处收敛}&\quad\Longrightarrow\quad R\ge|x_1-x_0|,\\
x_1\text{ 处发散}&\quad\Longrightarrow\quad R\le|x_1-x_0|,\\
x_1\text{ 处条件收敛}&\quad\Longrightarrow\quad R=|x_1-x_0|.
\end{aligned}
}
$$

**理由：** 收敛点不能位于收敛半径之外；发散点不能位于收敛半径之内；条件收敛点既不能在内部绝对收敛，也不能在外部发散，因此必在边界上。

**注意：前两式都可能取等号。** 即使已知某点绝对收敛，也只能推出 $R\ge|x_1-x_0|$，不能直接改成严格大于。中心为 $0$ 时，上述距离简化为 $|x_1|$。

### 不缺项幂级数：由系数求收敛半径 <span id="section-7-14"></span>

考虑标准形式

$$
\sum_{n=0}^{\infty}a_n(x-x_0)^n.
$$

这里“不缺项”指各次幂依次出现，且从某项起系数均非零，便于使用相邻系数的比值。

#### 比值法或根值法 <span id="section-7-14-1"></span>

若以下某个极限存在（允许为 $+\infty$）：

$$
\rho=\lim_{n\to\infty}\left|\frac{a_{n+1}}{a_n}\right|
\qquad\text{或}\qquad
\rho=\lim_{n\to\infty}\sqrt[n]{|a_n|},
$$

则收敛半径为

$$
\boxed{
R=\begin{cases}
\dfrac1\rho,&0<\rho<+\infty,\\[4pt]
+\infty,&\rho=0,\\
0,&\rho=+\infty.
\end{cases}
}
$$

以比值法为例，令 $u_n(x)=a_n(x-x_0)^n$，对 $x\ne x_0$，有

$$
\lim_{n\to\infty}\left|\frac{u_{n+1}(x)}{u_n(x)}\right|
=\rho|x-x_0|.
$$

当 $0<\rho<+\infty$ 时，令 $\rho|x-x_0|<1$，便得绝对收敛的开区间

$$
\boxed{x_0-\frac1\rho<x<x_0+\frac1\rho}.
$$

**步骤：先求 $R$，再写 $(x_0-R,x_0+R)$，最后将两个端点分别代回原级数，确定收敛域。** 中心不在原点时，要用 $x-x_0$ 平移；$R=0$ 或 $R=+\infty$ 时按前述特殊情况处理。

**注意：比值法要求分母系数最终非零；极限不存在时，不能直接套用上述极限公式。** 根值法取的是 $\sqrt[n]{|a_n|}$，不是 $\sqrt[n]{a_n}$。

### 缺项幂级数：对完整通项使用比值法或根值法 <span id="section-7-15"></span>

例如 $\sum a_n(x-x_0)^{2n}$ 只有偶次幂，属于缺项幂级数。此时 $n$ 只是求和下标，实际幂次为 $2n$，不能直接把 $\lim|a_{n+1}/a_n|$ 的倒数当作关于 $x$ 的收敛半径。

可令 $t=(x-x_0)^2$，先求关于 $t$ 的收敛条件，再换回 $x$；也可直接对完整通项 $u_n(x)$ 计算

$$
L(x)=\lim_{n\to\infty}\left|\frac{u_{n+1}(x)}{u_n(x)}\right|
\qquad\text{或}\qquad
L(x)=\lim_{n\to\infty}\sqrt[n]{|u_n(x)|}.
$$

令 $L(x)<1$ 得到绝对收敛范围，再检查边界；若比值中出现零分母，须单独处理对应的 $x$，或改用根值法。

**例：** 对级数

$$
\sum_{n=1}^{\infty}\frac{2^n}{n}(x-x_0)^{2n},
$$

在 $x\ne x_0$ 时，完整通项的比值极限为

$$
L(x)=\lim_{n\to\infty}2\frac{n}{n+1}|x-x_0|^2
=2|x-x_0|^2.
$$

由 $L(x)<1$ 得 $|x-x_0|<1/\sqrt2$，故 $R=1/\sqrt2$；两端点处均变为 $\sum1/n$，发散。中心处各项为 $0$，收敛，因此收敛域为 $(x_0-1/\sqrt2,x_0+1/\sqrt2)$。

### 一般函数项级数：绝对值判别后的补充检查 <span id="section-7-16"></span>

对一般的 $\sum u_n(x)$，先限制在各项的公共定义域内，固定 $x$，考察正项级数

$$
\sum|u_n(x)|.
$$

若可计算比值或根值极限 $L(x)$，则

| 极限条件                 | 对原级数 $\sum u_n(x)$ 的结论 |
| ------------------------ | ----------------------------- |
| $L(x)<1$                 | 绝对收敛                      |
| $L(x)>1$（含 $+\infty$） | 发散，因通项不趋于 $0$        |
| $L(x)=1$ 或极限不存在    | 该方法不能判定，需要另找方法  |

**不能把所有一般函数项级数都按“求一个开区间，再检查两个端点”处理。** 一般函数项级数的收敛域可能不是区间；$L(x)=1$ 的点也可能组成整个区间。

对尚未判定的点，应代回原级数，用比较判别法、莱布尼茨判别法或部分和等方法继续判断。若 $\sum|u_n(x)|$ 发散，原级数仍可能条件收敛；把所有收敛点合在一起，才能得到完整收敛域。

### 幂级数的运算法则 <span id="section-7-17"></span>

设

$$
A(x)=\sum_{n=0}^{\infty}a_nx^n,\qquad
B(x)=\sum_{n=0}^{\infty}b_nx^n,
$$

收敛半径分别为 $R_a,R_b$。以下加减、乘积等式均在公共收敛开区间 $|x|<\min\{R_a,R_b\}$ 内成立。

#### 数乘 <span id="section-7-17-1"></span>

$$
\boxed{
k\sum_{n=0}^{\infty}a_nx^n
=\sum_{n=0}^{\infty}ka_nx^n
},\qquad |x|<R_a.
$$

$k\ne0$ 时收敛半径仍为 $R_a$；$k=0$ 时所得零级数的收敛半径为 $+\infty$。

#### 逐项相加、相减 <span id="section-7-17-2"></span>

$$
\boxed{
\sum_{n=0}^{\infty}a_nx^n\pm\sum_{n=0}^{\infty}b_nx^n
=\sum_{n=0}^{\infty}(a_n\pm b_n)x^n
}.
$$

若 $R_a\ne R_b$，则和、差级数的收敛半径均为

$$
\boxed{R_{\pm}=\min\{R_a,R_b\}}.
$$

若 $R_a=R_b$，只能保证 $R_{\pm}\ge\min\{R_a,R_b\}$，系数抵消可能使收敛半径增大。

#### 相乘：柯西乘积 <span id="section-7-17-3"></span>

$$
\boxed{
\left(\sum_{n=0}^{\infty}a_nx^n\right)
\left(\sum_{n=0}^{\infty}b_nx^n\right)
=\sum_{n=0}^{\infty}\left(\sum_{i=0}^{n}a_i b_{n-i}\right)x^n
}.
$$

乘积级数的系数为 $c_n=\sum_{i=0}^{n}a_i b_{n-i}$，其收敛半径满足

$$
\boxed{R_{\mathrm{乘积}}\ge\min\{R_a,R_b\}}.
$$

**注意：乘积的收敛半径不一定等于两者半径的最小值，即使 $R_a\ne R_b$ 也不能直接写等号。** 端点处能否使用上述运算，应另行检查收敛条件。

### 幂级数的恒等变形 <span id="section-7-18"></span>

#### 通项、下标一起变 <span id="section-7-18-1"></span>

$$
\boxed{
\sum_{n=k}^{\infty}a_nx^n
=\sum_{n=k+l}^{\infty}a_{n-l}x^{n-l}
},\qquad k\ge0,\quad l\in\mathbb Z.
$$

#### 只变下标，不变通项 <span id="section-7-18-2"></span>

$$
\boxed{
\begin{aligned}
\sum_{n=k}^{\infty}a_nx^n
&=a_kx^k+a_{k+1}x^{k+1}+\cdots+a_{k+l-1}x^{k+l-1}
+\sum_{n=k+l}^{\infty}a_nx^n
\end{aligned}
},\qquad k\ge0,\quad l\ge1.
$$

#### 只变通项，不变下标 <span id="section-7-18-3"></span>

$$
\boxed{
\sum_{n=k}^{\infty}a_nx^n
=x^l\sum_{n=k}^{\infty}a_nx^{n-l}
},\qquad k,l\in\mathbb Z,\quad 0\le l\le k.
$$

### 幂级数变形：收敛半径与收敛域的变化 <span id="section-7-19"></span>

已知 $\sum a_n(x-x_1)^n$ 的敛散性，讨论变形后级数时，应分别检查**展开中心、系数、幂次以及端点**。

#### 平移展开中心与乘以有限次幂 <span id="section-7-19-1"></span>

保持系数 $a_n$ 不变，将

$$
\sum_{n=0}^{\infty}a_n(x-x_1)^n
\quad\text{改为}\quad
\sum_{n=0}^{\infty}a_n(x-x_2)^n,
$$

相当于平移自变量，**收敛半径不变，收敛域整体平移 $x_2-x_1$**。若半径为 $R$，新的收敛开区间为 $(x_2-R,x_2+R)$。

对固定非负整数 $k$，乘以 $(x-x_0)^k$，即

$$
\sum_{n=0}^{\infty}a_n(x-x_0)^n
\quad\longrightarrow\quad
\sum_{n=0}^{\infty}a_n(x-x_0)^{n+k},
$$

也不改变收敛半径和收敛域：当 $x\ne x_0$ 时只是各项乘以同一个非零常数，在中心处两级数也都收敛。提出公共因子时，可按同样思路处理。

#### 逐项求导：半径不变，端点可能丢失 <span id="section-7-19-2"></span>

若 $S(x)=\sum_{n=0}^{\infty}a_n(x-x_0)^n$ 的收敛半径为 $R>0$，则在 $|x-x_0|<R$ 内可逐项求导：

$$
\boxed{S'(x)=\sum_{n=1}^{\infty}na_n(x-x_0)^{n-1}}.
$$

求导后幂级数的收敛半径仍为 $R$。再乘以 $x-x_0$，得到

$$
\sum_{n=1}^{\infty}na_n(x-x_0)^n,
$$

其收敛半径也为 $R$。

**逐项求导后，收敛域可能缩小；变化只可能发生在端点，内部仍绝对收敛。**

例如，$\sum_{n=1}^{\infty}x^n/n$ 的收敛域为 $[-1,1)$；求导后得到 $\sum_{n=1}^{\infty}x^{n-1}$，收敛域为 $(-1,1)$，但半径均为 $1$。

#### 逐项积分：半径不变，端点可能增加 <span id="section-7-19-3"></span>

在 $|x-x_0|<R$ 内，可从中心到 $x$ 逐项积分：

$$
\boxed{
\int_{x_0}^{x}S(t)\,\mathrm dt
=\sum_{n=0}^{\infty}\frac{a_n}{n+1}(x-x_0)^{n+1}
}.
$$

积分后幂级数的收敛半径仍为 $R$，**收敛域可能扩大；变化只可能发生在端点**。

例如，$\sum_{n=0}^{\infty}x^n$ 的收敛域为 $(-1,1)$；从 $0$ 到 $x$ 逐项积分得到 $\sum_{n=0}^{\infty}x^{n+1}/(n+1)$，收敛域为 $[-1,1)$。

**记忆：平移、乘以有限次幂、逐项求导、逐项积分，都不改变收敛半径；端点敛散性须按变形后的通项重新判断。** 求导或积分后收敛域也可能保持不变，不能把“可能缩小、扩大”理解为必然变化。

### 幂级数和函数的连续性与端点性质 <span id="section-7-20"></span>

设幂级数 $\sum_{n=0}^{\infty}a_nx^n$ 的收敛半径为 $R>0$、收敛域为 $I$，和函数为 $S(x)$。

**$S(x)$ 在整个收敛域 $I$ 上连续，所含端点按单侧连续理解。** 特别地，若 $0<R<+\infty$，且级数在右端点 $x=R$ 处收敛，则

$$
\boxed{\lim_{x\to R^-}S(x)=S(R)}.
$$

若级数在左端点 $x=-R$ 处收敛，则

$$
\boxed{\lim_{x\to-R^+}S(x)=S(-R)}.
$$

在收敛开区间内部，$S$ 可任意次逐项求导，且导数的和等于和函数的导数；在收敛域内的任意有限闭区间上，$S$ 连续可积。

若端点属于原级数的收敛域，从 $0$ 到该端点的逐项积分等式也成立。**逐项求导等式只保证在开区间内部成立，不能直接推广到端点。**

### 幂级数展开与泰勒系数：任意阶可导还不够 <span id="section-7-21"></span>

#### 泰勒级数与麦克劳林级数的定义 <span id="section-7-21-1"></span>

若函数 $f$ 在 $x=x_0$ 处存在任意阶导数，则称

$$
\begin{aligned}
&f(x_0)+f'(x_0)(x-x_0)+\frac{f''(x_0)}{2!}(x-x_0)^2+\cdots\\
&\qquad+\frac{f^{(n)}(x_0)}{n!}(x-x_0)^n+\cdots
=\sum_{n=0}^{\infty}\frac{f^{(n)}(x_0)}{n!}(x-x_0)^n
\end{aligned}
$$

为 $f$ 在 $x_0$ 处的**泰勒级数**，其系数为

$$
\boxed{a_n=\frac{f^{(n)}(x_0)}{n!}},\qquad n=0,1,2,\ldots.
$$

特别地，$x_0=0$ 时，称

$$
f(0)+f'(0)x+\frac{f''(0)}{2!}x^2+\cdots
+\frac{f^{(n)}(0)}{n!}x^n+\cdots
=\sum_{n=0}^{\infty}\frac{f^{(n)}(0)}{n!}x^n
$$

为 $f$ 的**麦克劳林级数**，此时 $a_n=f^{(n)}(0)/n!$，约定 $f^{(0)}=f$、$0!=1$。

当相应级数的和等于 $f(x)$ 时，称为将 $f$ **展开成幂级数**：

$$
\boxed{f(x)=\sum_{n=0}^{\infty}\frac{f^{(n)}(x_0)}{n!}(x-x_0)^n}.
$$

**级数收敛本身还不足以保证其和等于原函数；还须验证泰勒余项趋于 $0$。**

#### 从幂级数表示确定系数 <span id="section-7-21-2"></span>

若 $f$ 在 $0$ 的某邻域内能表示为收敛的幂级数

$$
f(x)=\sum_{n=0}^{\infty}a_nx^n,
$$

则在收敛区间内部可逐项求导，从而系数必为

$$
\boxed{a_n=\frac{f^{(n)}(0)}{n!}},\qquad n=0,1,2,\ldots.
$$

因此，该展开必为麦克劳林展开：

$$
f(x)=f(0)+f'(0)x+\frac{f''(0)}{2!}x^2+\cdots
=\sum_{n=0}^{\infty}\frac{f^{(n)}(0)}{n!}x^n.
$$

一般展开中心为 $x_0$ 时，系数相应为 $a_n=f^{(n)}(x_0)/n!$。

**注意：任意阶可导，只保证可以写出泰勒级数，不保证该级数收敛，也不保证它收敛到原函数。** 对给定的 $x$，设

$$
R_N(x)=f(x)-\sum_{n=0}^{N}\frac{f^{(n)}(x_0)}{n!}(x-x_0)^n,
$$

则等于原函数的充要条件是

$$
\boxed{
f(x)=\sum_{n=0}^{\infty}\frac{f^{(n)}(x_0)}{n!}(x-x_0)^n
\iff\lim_{N\to\infty}R_N(x)=0
}.
$$

**反例：**

$$
f(x)=\begin{cases}
e^{-1/x^2},&x\ne0,\\
0,&x=0.
\end{cases}
$$

该函数处处任意阶可导，且 $f^{(n)}(0)=0$ 对所有 $n\ge0$ 成立。因此在 $0$ 处的泰勒级数恒为 $0$，虽然处处收敛，却在所有 $x\ne0$ 处都不等于 $f(x)$。

### 常用麦克劳林展开（含通项） <span id="section-7-22"></span>

以下十组幂级数在注明的范围内等于原函数。

#### ① 指数函数 <span id="section-7-22-1"></span>

$$
e^x=\sum_{n=0}^{\infty}\frac{x^n}{n!}
=1+x+\frac{x^2}{2!}+\cdots+\frac{x^n}{n!}+\cdots,
\qquad -\infty<x<+\infty.
$$

#### ② $1/(1+x)$ <span id="section-7-22-2"></span>

$$
\frac1{1+x}=\sum_{n=0}^{\infty}(-1)^nx^n
=1-x+x^2-x^3+\cdots+(-1)^nx^n+\cdots,
\qquad -1<x<1.
$$

#### ③ $1/(1-x)$ <span id="section-7-22-3"></span>

$$
\frac1{1-x}=\sum_{n=0}^{\infty}x^n
=1+x+x^2+\cdots+x^n+\cdots,
\qquad -1<x<1.
$$

#### ④ 对数函数 <span id="section-7-22-4"></span>

$$
\ln(1+x)=\sum_{n=1}^{\infty}(-1)^{n-1}\frac{x^n}{n}
=x-\frac{x^2}{2}+\frac{x^3}{3}-\frac{x^4}{4}+\cdots
+(-1)^{n-1}\frac{x^n}{n}+\cdots,
\qquad -1<x\le1.
$$

$$
\sum_{n=1}^{\infty}\frac{(-x)^n}{n}=-\ln(1+x),
\qquad -1<x\le1.
$$

$$
\sum_{n=1}^{\infty}(-1)^{n-1}\frac{(-x)^n}{n}
=\ln(1-x),\qquad -1\le x<1.
$$

$$
\sum_{n=1}^{\infty}\frac{x^n}{n}=-\ln(1-x),
\qquad -1\le x<1.
$$

分母为 $2n$ 时，先提出常数 $1/2$：

$$
\boxed{\frac12\ln(1+x)
=\sum_{n=1}^{\infty}(-1)^{n-1}\frac{x^n}{2n}},
\qquad -1<x\le1.
$$

#### ⑤ 正弦函数 <span id="section-7-22-5"></span>

$$
\sin x=\sum_{n=0}^{\infty}(-1)^n\frac{x^{2n+1}}{(2n+1)!}
=x-\frac{x^3}{3!}+\frac{x^5}{5!}-\frac{x^7}{7!}+\cdots
+(-1)^n\frac{x^{2n+1}}{(2n+1)!}+\cdots,
\qquad -\infty<x<+\infty.
$$

#### ⑥ 余弦函数 <span id="section-7-22-6"></span>

$$
\cos x=\sum_{n=0}^{\infty}(-1)^n\frac{x^{2n}}{(2n)!}
=1-\frac{x^2}{2!}+\frac{x^4}{4!}-\frac{x^6}{6!}+\cdots
+(-1)^n\frac{x^{2n}}{(2n)!}+\cdots,
\qquad -\infty<x<+\infty.
$$

#### ⑦ 二项式展开 <span id="section-7-22-7"></span>

$$
(1+x)^\alpha=\sum_{n=0}^{\infty}C_\alpha^n x^n
=1+\alpha x+\frac{\alpha(\alpha-1)}{2!}x^2+\cdots+
\frac{\alpha(\alpha-1)\cdots(\alpha-n+1)}{n!}x^n+\cdots.
$$

其中 $\alpha$ 为固定实常数，且

$$
C_\alpha^0=1,\qquad
C_\alpha^n=\frac{\alpha(\alpha-1)\cdots(\alpha-n+1)}{n!}
\quad(n\ge1).
$$

展开成立的范围为

$$
\begin{cases}
x\in(-1,1),&\alpha\le-1,\\
x\in(-1,1],&-1<\alpha<0,\\
x\in[-1,1],&\alpha>0\text{ 且 }\alpha\notin\mathbb N_+,\\
x\in(-\infty,+\infty),&\alpha\in\mathbb N_+.
\end{cases}
$$

$\alpha=0$ 时为常数函数 $1$，级数只有常数项，收敛于整个实数轴。$\alpha\in\mathbb N_+$ 时展开为有限项多项式。

**二项式展开至少记住前三项：$1+\alpha x+\alpha(\alpha-1)x^2/2$。**

#### ⑧ 反正切函数 <span id="section-7-22-8"></span>

$$
\boxed{\arctan x=\sum_{n=0}^{\infty}(-1)^n\frac{x^{2n+1}}{2n+1}}
=x-\frac{x^3}{3}+\frac{x^5}{5}-\cdots,
\qquad -1\le x\le1.
$$

**识别：** 奇数次幂、分母为奇数 $2n+1$（没有阶乘）、符号交错。可由

$$
(\arctan x)'=\frac1{1+x^2}
=\sum_{n=0}^{\infty}(-1)^nx^{2n},\qquad |x|<1
$$

从 $0$ 到 $x$ 逐项积分得到；两端点另行检验，分别收敛到 $\pm\pi/4$。

#### ⑨ 指数函数的偶数项：双曲余弦 <span id="section-7-22-9"></span>

$$
\boxed{\frac{e^x+e^{-x}}2=\sum_{n=0}^{\infty}\frac{x^{2n}}{(2n)!}}
=1+\frac{x^2}{2!}+\frac{x^4}{4!}+\cdots,
\qquad -\infty<x<+\infty.
$$

左侧也记作 $\cosh x$。将 $e^x$ 与 $e^{-x}$ 的展开相加再除以 $2$，奇数项抵消，只保留偶数项。

#### ⑩ 指数函数的奇数项：双曲正弦 <span id="section-7-22-10"></span>

$$
\boxed{\frac{e^x-e^{-x}}2=\sum_{n=0}^{\infty}\frac{x^{2n+1}}{(2n+1)!}}
=x+\frac{x^3}{3!}+\frac{x^5}{5!}+\cdots,
\qquad -\infty<x<+\infty.
$$

左侧也记作 $\sinh x$。将 $e^x$ 与 $e^{-x}$ 的展开相减再除以 $2$，偶数项抵消，只保留奇数项。

#### 按通项特征识别和函数 <span id="section-7-22-11"></span>

先把幂次、分母、起始下标和符号配成标准形式，再识别和函数。

| 通项特征                          | 对应和函数        | 成立范围        |
| --------------------------------- | ----------------- | --------------- |
| $(-1)^{n-1}x^n/n$，$n\ge1$        | $\ln(1+x)$        | $-1<x\le1$      |
| $(-1)^{n-1}x^n/(2n)$，$n\ge1$     | $\frac12\ln(1+x)$ | $-1<x\le1$      |
| $(-1)^nx^{2n+1}/(2n+1)$，$n\ge0$  | $\arctan x$       | $-1\le x\le1$   |
| $x^n/n!$，$n\ge0$                 | $e^x$             | $x\in\mathbb R$ |
| $x^{2n}/(2n)!$，$n\ge0$           | $(e^x+e^{-x})/2$  | $x\in\mathbb R$ |
| $(-1)^nx^{2n}/(2n)!$，$n\ge0$     | $\cos x$          | $x\in\mathbb R$ |
| $x^{2n+1}/(2n+1)!$，$n\ge0$       | $(e^x-e^{-x})/2$  | $x\in\mathbb R$ |
| $(-1)^nx^{2n+1}/(2n+1)!$，$n\ge0$ | $\sin x$          | $x\in\mathbb R$ |

**记忆：** 分母有 $n$ 常想到对数，有奇数 $2n+1$ 且符号交错想到反正切；分母有阶乘时，再看幂次奇偶和是否有 $(-1)^n$。偶数次幂、有交错符号对应余弦，奇数次幂、有交错符号对应正弦；没有交错符号时，对应指数函数的偶数项或奇数项。

### 两条常用幂级数求和公式（重点记忆） <span id="section-7-23"></span>

$$
\boxed{\sum_{n=1}^{\infty}\frac{x^n}{n}=-\ln(1-x)},
\qquad -1\le x<1.
$$

$$
\boxed{\sum_{n=1}^{\infty}nx^{n-1}=\frac1{(1-x)^2}},
\qquad -1<x<1.
$$

**记忆方法：** 从等比级数

$$
\sum_{n=0}^{\infty}x^n=\frac1{1-x},\qquad |x|<1
$$

出发，在收敛区间内从 $0$ 到 $x$ 逐项积分，得到第一式；逐项求导，得到第二式。

第一式在 $x=-1$ 处为交错调和级数，和为 $-\ln2$，所以包含左端点；在 $x=1$ 处为调和级数，发散。第二式在 $x=\pm1$ 处通项均不趋于 $0$，两端点都不包含。

第二式两边乘以 $x$，还得到常用变形：

$$
\boxed{\sum_{n=1}^{\infty}nx^n=\frac{x}{(1-x)^2}},
\qquad -1<x<1.
$$

### 傅里叶级数（仅数学一） <span id="fourier-series"></span>

#### 周期为 2l 的傅里叶系数与展开式 <span id="section-7-24-1"></span>

设 $l>0$，$f(x)$ 是周期为 $2l$ 的周期函数，且在 $[-l,l]$ 上可积。定义傅里叶系数

$$
\boxed{a_n=\frac1l\int_{-l}^{l}f(x)\cos\frac{n\pi x}{l}\,\mathrm dx},
\qquad n=0,1,2,\ldots,
$$

$$
\boxed{b_n=\frac1l\int_{-l}^{l}f(x)\sin\frac{n\pi x}{l}\,\mathrm dx},
\qquad n=1,2,3,\ldots.
$$

特别地，令 $n=0$，有

$$
\boxed{a_0=\frac1l\int_{-l}^{l}f(x)\,\mathrm dx}.
$$

称

$$
\boxed{\frac{a_0}{2}+\sum_{n=1}^{\infty}
\left(a_n\cos\frac{n\pi x}{l}+b_n\sin\frac{n\pi x}{l}\right)}
$$

为 $f$ 的傅里叶级数，记作

$$
f(x)\sim\frac{a_0}{2}+\sum_{n=1}^{\infty}
\left(a_n\cos\frac{n\pi x}{l}+b_n\sin\frac{n\pi x}{l}\right).
$$

这里 $\sim$ 表示右侧是由 $f$ 的傅里叶系数组成的级数，**不是等价无穷小符号，也不保证级数处处收敛到 $f(x)$**。级数收敛时，将其和记为 $S(x)$。

**记忆：** 系数积分前是 $1/l$，展开式的常数项是 $a_0/2$；周期为 $2\pi$ 时取 $l=\pi$，三角函数中的 $n\pi x/l$ 就变为 $nx$。

#### 狄利克雷收敛定理 <span id="section-7-24-2"></span>

设 $f$ 是周期为 $2l$ 的可积函数，且在 $[-l,l]$ 上满足：

1. 连续，或只有有限个第一类间断点（左右极限均存在且有限）。
2. 至多只有有限个极值点。

则其傅里叶级数处处收敛。按周期延拓理解左右极限时，统一写为

$$
\boxed{S(x)=\frac{f(x-0)+f(x+0)}2}.
$$

在一个周期内，具体为

$$
\boxed{
S(x)=\begin{cases}
f(x),&-l<x<l,\ x\text{ 为连续点},\\[4pt]
\dfrac{f(x-0)+f(x+0)}2,&-l<x<l,\ x\text{ 为间断点},\\[8pt]
\dfrac{f(-l+0)+f(l-0)}2,&x=\pm l.
\end{cases}
}
$$

**重点：和函数取左右极限的平均值。** 在连续点才有 $S(x)=f(x)$；在间断点，$S(x)$ 不由该点单独指定的函数值决定。周期端点 $\pm l$ 的左右极限分别来自本周期两端的内部，不能直接取 $[f(-l)+f(l)]/2$。

#### 奇函数：正弦级数 <span id="section-7-24-3"></span>

若 $f$ 为奇函数，则 $f(x)\cos(n\pi x/l)$ 为奇函数，$f(x)\sin(n\pi x/l)$ 为偶函数。因此

$$
\boxed{a_0=a_n=0},\qquad n\ge1,
$$

$$
\boxed{b_n=\frac2l\int_0^l f(x)\sin\frac{n\pi x}{l}\,\mathrm dx},
\qquad n=1,2,\ldots.
$$

其展开式为正弦级数：

$$
\boxed{f(x)\sim\sum_{n=1}^{\infty}b_n\sin\frac{n\pi x}{l}}.
$$

#### 偶函数：余弦级数 <span id="section-7-24-4"></span>

若 $f$ 为偶函数，则 $f(x)\sin(n\pi x/l)$ 为奇函数，$f(x)\cos(n\pi x/l)$ 为偶函数。因此

$$
\boxed{b_n=0},\qquad n\ge1,
$$

$$
\boxed{a_0=\frac2l\int_0^l f(x)\,\mathrm dx},
$$

$$
\boxed{a_n=\frac2l\int_0^l f(x)\cos\frac{n\pi x}{l}\,\mathrm dx},
\qquad n=1,2,\ldots.
$$

其展开式为余弦级数：

$$
\boxed{f(x)\sim\frac{a_0}{2}
+\sum_{n=1}^{\infty}a_n\cos\frac{n\pi x}{l}}.
$$

**记忆：奇函数只留正弦项，偶函数只留常数项和余弦项。** 利用奇偶性将积分区间由 $[-l,l]$ 缩为 $[0,l]$ 后，系数积分前的因子变为 $2/l$。是否能将展开符号写成等号，仍须根据收敛定理判断 $S(x)$ 是否等于 $f(x)$。

#### 周期奇延拓与半区间正弦展开 <span id="section-7-24-5"></span>

设 $f$ 仅定义在 $[0,l]$ 上。要将它展开为正弦级数，先作奇延拓，再作周期延拓。

在一个周期内定义

$$
F_{\mathrm o}(x)=\begin{cases}
f(x),&0<x<l,\\
-f(-x),&-l<x<0,\\
0,&x=0,\ \pm l,
\end{cases}
$$

再令

$$
\boxed{F_{\mathrm o}(x+2l)=F_{\mathrm o}(x)}.
$$

图形上，先将 $(0,l)$ 内的曲线**关于原点对称**到 $(-l,0)$，再将所得图形以 $2l$ 为周期左右重复。

**端点约定：** 为使延拓后的函数在全轴上同时满足奇性和 $2l$ 周期性，将所有 $x=kl$（$k\in\mathbb Z$）处的值取为 $0$。原函数在 $0,l$ 两点的取值不影响傅里叶系数，但正弦级数在这两点的和恒为 $0$。

因为 $F_{\mathrm o}$ 为奇函数，所以得到 $f$ 的半区间正弦展开

$$
\boxed{f(x)\sim\sum_{n=1}^{\infty}b_n\sin\frac{n\pi x}{l}},
\qquad 0<x<l,
$$

其中

$$
\boxed{b_n=\frac2l\int_0^l f(x)\sin\frac{n\pi x}{l}\,\mathrm dx},
\qquad n=1,2,3,\ldots.
$$

在延拓函数满足狄利克雷条件时，区间内部连续点处级数和为 $f(x)$，间断点处为左右极限的平均值；端点处

$$
\boxed{S_{\mathrm{正弦}}(0)=S_{\mathrm{正弦}}(l)=0}.
$$

因此，正弦展开在原区间端点处是否等于原函数，还要看 $f(0)$、$f(l)$ 是否为 $0$。

#### 周期偶延拓与半区间余弦展开 <span id="section-7-24-6"></span>

设 $f$ 定义在 $[0,l]$ 上。要将它展开为余弦级数，先作偶延拓：

$$
F_{\mathrm e}(x)=\begin{cases}
f(x),&0\le x\le l,\\
f(-x),&-l\le x<0,
\end{cases}
$$

再令

$$
\boxed{F_{\mathrm e}(x+2l)=F_{\mathrm e}(x)}.
$$

图形上，先将 $[0,l]$ 内的曲线**关于纵轴对称**到 $[-l,0]$，再以 $2l$ 为周期左右重复。

因为 $F_{\mathrm e}$ 为偶函数，所以得到 $f$ 的半区间余弦展开

$$
\boxed{f(x)\sim\frac{a_0}{2}+\sum_{n=1}^{\infty}a_n\cos\frac{n\pi x}{l}},
\qquad 0\le x\le l,
$$

其中

$$
\boxed{a_0=\frac2l\int_0^l f(x)\,\mathrm dx},
$$

$$
\boxed{a_n=\frac2l\int_0^l f(x)\cos\frac{n\pi x}{l}\,\mathrm dx},
\qquad n=1,2,3,\ldots.
$$

在延拓函数满足狄利克雷条件时，内部连续点处级数和为 $f(x)$，间断点处仍取左右极限的平均值。由于偶延拓及周期延拓，端点处有

$$
\boxed{S_{\mathrm{余弦}}(0)=f(0+0),\qquad
S_{\mathrm{余弦}}(l)=f(l-0)}.
$$

在上述收敛条件下，若 $f$ 在 $[0,l]$ 上连续，则余弦展开在整个 $[0,l]$ 上都收敛到 $f(x)$。

**选法：** 题目要求正弦级数，就作周期奇延拓；要求余弦级数，就作周期偶延拓。两种展开都只用 $[0,l]$ 上的积分，周期均为 $2l$；端点处的级数和须按各自的延拓方式判断。

## <span style="color: #3498db;">第八部分：空间解析几何</span> <span id="section-8"></span>

### 平面二次曲线的判别式 <span id="section-8-1"></span>

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

#### 特别注意：只有二次项的方程 <span id="section-8-1-1"></span>

对于图片中的特殊形式

$$
Ax^2+Bxy+Cy^2=1,
$$

不能直接把 $\Delta=0$ 判为抛物线：该式没有一次项，此时可能表示两条平行直线或无实点。例如，$x^2=1$ 表示 $x=\pm1$ 两条直线，$-x^2=1$ 无实点。

该形式下，$\Delta<0$ 且 $A>0$ 时为实椭圆；$\Delta<0$ 且 $A<0$ 时无实点；$\Delta>0$ 时为双曲线。

### 向量的坐标、模与方向余弦 <span id="section-8-2"></span>

向量既有大小又有方向；自由向量只由大小和方向决定，与起点位置无关。

$$
\boldsymbol a=(a_x,a_y,a_z)=a_x\boldsymbol i+a_y\boldsymbol j+a_z\boldsymbol k,
\qquad |\boldsymbol a|=\sqrt{a_x^2+a_y^2+a_z^2}.
$$

若 $A=(x_1,y_1,z_1)$、$B=(x_2,y_2,z_2)$，则

$$
\overrightarrow{AB}=(x_2-x_1,y_2-y_1,z_2-z_1).
$$

非零向量与三个坐标轴正向的夹角 $\alpha,\beta,\gamma\in[0,\pi]$ 称为方向角，其余弦为方向余弦：

$$
\boxed{\cos\alpha=\frac{a_x}{|\boldsymbol a|},\quad
\cos\beta=\frac{a_y}{|\boldsymbol a|},\quad
\cos\gamma=\frac{a_z}{|\boldsymbol a|}},\qquad
\cos^2\alpha+\cos^2\beta+\cos^2\gamma=1.
$$

与 $\boldsymbol a$ 同向的单位向量为

$$
\boldsymbol a^0=\frac{\boldsymbol a}{|\boldsymbol a|}
=(\cos\alpha,\cos\beta,\cos\gamma).
$$

**注意：** 零向量没有确定的方向角，不能单位化。

### 数量积、向量积与混合积 <span id="section-8-3"></span>

以下夹角公式中的向量均非零，向量夹角 $\theta\in[0,\pi]$。

#### 数量积：求夹角、判垂直、求投影

$$
\boxed{\boldsymbol a\cdot\boldsymbol b
=a_xb_x+a_yb_y+a_zb_z
=|\boldsymbol a||\boldsymbol b|\cos\theta}.
$$

因此

$$
\cos\theta=\frac{\boldsymbol a\cdot\boldsymbol b}{|\boldsymbol a||\boldsymbol b|},
\qquad \boldsymbol a\perp\boldsymbol b\iff\boldsymbol a\cdot\boldsymbol b=0.
$$

$\boldsymbol a$ 在 $\boldsymbol b$ 方向上的**数量投影**为

$$
\operatorname{Prj}_{\boldsymbol b}\boldsymbol a
=\frac{\boldsymbol a\cdot\boldsymbol b}{|\boldsymbol b|}
=|\boldsymbol a|\cos\theta.
$$

数量投影可以为负；对应的**向量投影**为

$$
\operatorname{proj}_{\boldsymbol b}\boldsymbol a
=\frac{\boldsymbol a\cdot\boldsymbol b}{|\boldsymbol b|^2}\boldsymbol b.
$$

#### 向量积：求法向量、判平行、求面积

$$
\boxed{\boldsymbol a\times\boldsymbol b
=\begin{vmatrix}
\boldsymbol i&\boldsymbol j&\boldsymbol k\\
a_x&a_y&a_z\\b_x&b_y&b_z
\end{vmatrix}
=(a_yb_z-a_zb_y,\ a_zb_x-a_xb_z,\ a_xb_y-a_yb_x)}.
$$

结果垂直于 $\boldsymbol a,\boldsymbol b$，方向由右手定则确定，且

$$
|\boldsymbol a\times\boldsymbol b|=|\boldsymbol a||\boldsymbol b|\sin\theta,
\qquad \boldsymbol b\times\boldsymbol a=-\boldsymbol a\times\boldsymbol b.
$$

$$
\boxed{\boldsymbol a\parallel\boldsymbol b\iff\boldsymbol a\times\boldsymbol b=\boldsymbol0},
\qquad S_{\text{平行四边形}}=|\boldsymbol a\times\boldsymbol b|,
\quad S_{\text{三角形}}=\tfrac12|\boldsymbol a\times\boldsymbol b|.
$$

平行的稳妥表述是 $\boldsymbol a=\lambda\boldsymbol b$；分量比 $a_x/b_x=a_y/b_y=a_z/b_z$ 仅在分母非零时可直接使用。

#### 混合积：求体积、判共面

$$
\boxed{[\boldsymbol a\boldsymbol b\boldsymbol c]
=(\boldsymbol a\times\boldsymbol b)\cdot\boldsymbol c
=\begin{vmatrix}a_x&a_y&a_z\\b_x&b_y&b_z\\c_x&c_y&c_z\end{vmatrix}}.
$$

$$
V_{\text{平行六面体}}=|[\boldsymbol a\boldsymbol b\boldsymbol c]|,
\qquad V_{\text{四面体}}=\tfrac16|[\boldsymbol a\boldsymbol b\boldsymbol c]|.
$$

三向量共面（线性相关）当且仅当混合积为零。**体积须取绝对值，混合积本身有正负。**

### 空间平面方程与平面束 <span id="section-8-4"></span>

确定平面的两个要素：平面上一点 $P_0=(x_0,y_0,z_0)$、非零法向量 $\boldsymbol n=(A,B,C)$。

| 形式 | 方程与条件 |
| --- | --- |
| 一般式 | $Ax+By+Cz+D=0$，$(A,B,C)\ne\boldsymbol0$ |
| 点法式 | $A(x-x_0)+B(y-y_0)+C(z-z_0)=0$ |
| 截距式 | $x/a+y/b+z/c=1$，$abc\ne0$ |

点法式来自 $\overrightarrow{P_0P}\cdot\boldsymbol n=0$。截距式的三个轴截点为 $(a,0,0),(0,b,0),(0,0,c)$。

过不共线的三点 $P_1,P_2,P_3$ 的平面，可取

$$
\boldsymbol n=\overrightarrow{P_1P_2}\times\overrightarrow{P_1P_3},
\qquad
\begin{vmatrix}
x-x_1&y-y_1&z-z_1\\
x_2-x_1&y_2-y_1&z_2-z_1\\
x_3-x_1&y_3-y_1&z_3-z_1
\end{vmatrix}=0.
$$

**平面束：** 设 $\pi_1=0,\pi_2=0$ 为两个相交平面，其法向量不平行，则包含交线的所有平面为

$$
\boxed{\lambda\pi_1+\mu\pi_2=0,\qquad(\lambda,\mu)\ne(0,0)}.
$$

写作 $\pi_1+k\pi_2=0$ 时漏掉 $\pi_2=0$，写作 $\pi_2+k\pi_1=0$ 时漏掉 $\pi_1=0$；求指定平面时须检查遗漏项。

### 空间直线方程 <span id="section-8-5"></span>

确定直线的两个要素：直线上一点 $P_0$、非零方向向量 $\boldsymbol\tau=(l,m,n)$。

**向量式与参数式（优先使用）：**

$$
\boxed{(x,y,z)=(x_0,y_0,z_0)+t(l,m,n)},\quad t\in\mathbb R,
$$

即 $x=x_0+lt,\ y=y_0+mt,\ z=z_0+nt$。

**点向式（对称式）：** 当 $lmn\ne0$ 时，

$$
\frac{x-x_0}{l}=\frac{y-y_0}{m}=\frac{z-z_0}{n}.
$$

若某个方向分量为零，就将对应坐标固定。例如 $l=0$、$mn\ne0$ 时写成 $x=x_0,\ (y-y_0)/m=(z-z_0)/n$，不作除以零的运算。

**两点式：** 取不同两点 $P_1,P_2$，令 $\boldsymbol\tau=P_2-P_1$，代入参数式或点向式。

**一般式：** 两个法向量不平行的平面相交成直线：

$$
\begin{cases}
A_1x+B_1y+C_1z+D_1=0,\\
A_2x+B_2y+C_2z+D_2=0.
\end{cases}
\qquad
\boxed{\boldsymbol\tau=\boldsymbol n_1\times\boldsymbol n_2}.
$$

转换成参数式时，先求叉积得方向，再从方程组中取一个点。

### 点到直线、平面的距离 <span id="section-8-6"></span>

**点到直线：** $M$ 为给定点，$P_0$ 在直线 $L$ 上，$\boldsymbol\tau$ 为直线的非零方向向量，则

$$
\boxed{d(M,L)=\frac{|\overrightarrow{P_0M}\times\boldsymbol\tau|}{|\boldsymbol\tau|}}.
$$

推导：由这两个向量张成的平行四边形面积 $S=|\boldsymbol\tau|d$，以面积除以底边长度即得。

**点到平面：** $M=(x_1,y_1,z_1)$ 到 $Ax+By+Cz+D=0$ 的距离为

$$
\boxed{d=\frac{|Ax_1+By_1+Cz_1+D|}{\sqrt{A^2+B^2+C^2}}}.
$$

这是连接向量在平面法向量方向上数量投影的绝对值。平面内点代入得零。

二维情形：点 $(x_1,y_1)$ 到直线 $Ax+By+C=0$ 的距离为

$$
d=\frac{|Ax_1+By_1+C|}{\sqrt{A^2+B^2}},\qquad (A,B)\ne(0,0).
$$

### 直线与平面的位置关系及夹角 <span id="section-8-7"></span>

设两直线的方向向量为 $\boldsymbol\tau_1,\boldsymbol\tau_2$，两平面的法向量为 $\boldsymbol n_1,\boldsymbol n_2$，均非零。

| 对象 | 方向条件 | 夹角公式（$0\le\theta\le\pi/2$） |
| --- | --- | --- |
| 两直线 | 同向或反向：$\boldsymbol\tau_1\times\boldsymbol\tau_2=\boldsymbol0$；方向正交：$\boldsymbol\tau_1\cdot\boldsymbol\tau_2=0$ | $\cos\theta=\dfrac{|\boldsymbol\tau_1\cdot\boldsymbol\tau_2|}{|\boldsymbol\tau_1||\boldsymbol\tau_2|}$ |
| 两平面 | 法向量平行：$\boldsymbol n_1\times\boldsymbol n_2=\boldsymbol0$；垂直：$\boldsymbol n_1\cdot\boldsymbol n_2=0$ | $\cos\theta=\dfrac{|\boldsymbol n_1\cdot\boldsymbol n_2|}{|\boldsymbol n_1||\boldsymbol n_2|}$ |
| 直线与平面 | 垂直：$\boldsymbol\tau\times\boldsymbol n=\boldsymbol0$；方向平行于平面：$\boldsymbol\tau\cdot\boldsymbol n=0$ | $\sin\theta=\dfrac{|\boldsymbol\tau\cdot\boldsymbol n|}{|\boldsymbol\tau||\boldsymbol n|}$ |

**记忆：线线、面面用余弦，线面用正弦；取绝对值得到不超过 $\pi/2$ 的夹角。**

方向条件之外，还要用点判断位置：

- 两直线方向平行时，取一条线上的点代入另一条线，区分重合与严格平行；方向正交时，若要求相交垂直，还须验证有交点。
- 两平面的法向量平行时，代入一点，区分重合与严格平行。
- $\boldsymbol\tau\cdot\boldsymbol n=0$ 时，若直线上一点在平面内，则整条线在平面内；否则严格平行。
- $\boldsymbol\tau\cdot\boldsymbol n\ne0$ 时，直线与平面有唯一交点，代入直线参数式即可求出。

### 空间曲线及其在坐标面上的投影 <span id="section-8-8"></span>

空间曲线常表示为两个曲面的交线，或用一个参数表示：

$$
\Gamma:\begin{cases}F(x,y,z)=0,\\G(x,y,z)=0,\end{cases}
\qquad
\boldsymbol r(t)=(\varphi(t),\psi(t),\omega(t)),\quad t\in I.
$$

局部选某个坐标作为参数，须满足相应的隐函数条件。

求坐标面上的正投影时，**先消去垂直于该坐标面的变量，再把投影点的该坐标设为零**：

| 投影面 | 消去变量 | 投影曲线的表示 |
| --- | --- | --- |
| $xOy$ | $z$ | $\varphi(x,y)=0,\ z=0$ |
| $yOz$ | $x$ | $\psi(y,z)=0,\ x=0$ |
| $xOz$ | $y$ | $\chi(x,z)=0,\ y=0$ |

消元得到的方程可能只描述一个包含实际投影的集合；还须保留原曲线的取值范围、根号条件等约束。**不能直接在原方程中令 $z=0$ 来求 $xOy$ 投影，那通常是在求曲线与坐标面的交点。**

### 常见二次曲面与柱面 <span id="section-8-9"></span>

以下 $a,b,c,p,q>0$，默认中心或顶点在原点；其他位置可先平移坐标。判断形状时，固定一个坐标，看截线。

| 曲面 | 标准方程 | 识别与截面 |
| --- | --- | --- |
| 椭球面 | $x^2/a^2+y^2/b^2+z^2/c^2=1$ | 三个平方项均为正；$a=b=c$ 时为球面 |
| 单叶双曲面 | $x^2/a^2+y^2/b^2-z^2/c^2=1$ | 两正一负；负号对应 $z$ 轴，$z=k$ 截面均为椭圆 |
| 双叶双曲面 | $x^2/a^2-y^2/b^2-z^2/c^2=1$ | 一正两负；沿正号对应的 $x$ 轴分成两叶，$|x|\ge a$ |
| 椭圆抛物面 | $z=x^2/(2p)+y^2/(2q)$ | 向 $z$ 正向开口；$z=k>0$ 截面为椭圆，竖直截面为抛物线 |
| 椭圆锥面 | $x^2/a^2+y^2/b^2=z^2/c^2$ | 沿 $z$ 轴的双锥，$z=0$ 时仅一个顶点 |
| 双曲抛物面（马鞍面） | $z=-x^2/(2p)+y^2/(2q)$ | 水平非零截面为双曲线，$x=k$、$y=k$ 截面为抛物线 |
| 双曲抛物面的另一形式 | $z=xy$ | $z=k\ne0$ 为双曲线；$z=0$ 为两相交直线 |

例如 $z=y^2-x^2=(y+x)(y-x)$，令 $u=y+x,\ v=y-x$ 可写成 $z=uv$；若要将该变换解释为纯旋转，须对新坐标作归一化。

**柱面：** 直线沿定曲线平行移动形成的曲面。方程中缺少某个坐标时，该坐标可自由变化，母线平行于该坐标轴。

| 方程 | 曲面名称 | 母线方向 |
| --- | --- | --- |
| $x^2/a^2+y^2/b^2=1$ | 椭圆柱面；$a=b$ 时为圆柱面 | 平行于 $z$ 轴 |
| $x^2/a^2-y^2/b^2=1$ | 双曲柱面 | 平行于 $z$ 轴 |
| $y=ax^2$，$a>0$ | 抛物柱面 | 平行于 $z$ 轴 |

**易错：** $z^2=x^2+y^2$ 表示整个双锥；$z=\sqrt{x^2+y^2}$ 只表示上半锥。单叶、双叶双曲面须先把右侧化为 $1$ 再按符号判断。

### 旋转曲面的方程 <span id="section-8-10"></span>

曲线绕定直线旋转一周形成旋转曲面。核心不变量是：**沿轴方向的位置不变，到轴的距离不变**。

母线在含旋转轴的坐标面内时，可用到轴的距离替换其径向坐标。例如将 $xOz$ 平面中的母线

$$
x=f(z),\qquad y=0
$$

绕 $z$ 轴旋转，得

$$
\boxed{x^2+y^2=f(z)^2},
$$

并保留母线对 $z$ 的限制。若母线写为 $F(x,z)=0$，径向坐标 $x$ 有正负时，应检查 $F(\rho,z)=0$ 或 $F(-\rho,z)=0$，其中 $\rho=\sqrt{x^2+y^2}$，避免丢失分支。

**绕任意直线：** 设旋转轴过 $M_0$，方向为 $\boldsymbol\tau\ne\boldsymbol0$，母线点为 $M_1$，旋转后的点为 $P$。同一纬圆上的点满足

$$
\boxed{\begin{cases}
\boldsymbol\tau\cdot(P-M_1)=0,\\
|P-M_0|^2=|M_1-M_0|^2.
\end{cases}}
$$

第一式固定沿轴的位置，第二式固定到轴上定点的距离。再与母线方程联立，消去 $M_1$ 的坐标，得到旋转曲面方程，并保留消元过程中产生的范围条件。

### 空间曲线的切线与法平面 <span id="section-8-11"></span>

**参数方程：** 设曲线 $\boldsymbol r(t)=(x(t),y(t),z(t))$ 在 $t_0$ 处可导，$P_0=\boldsymbol r(t_0)$，且

$$
\boldsymbol\tau=\boldsymbol r'(t_0)=(x'(t_0),y'(t_0),z'(t_0))\ne\boldsymbol0.
$$

则

$$
\boxed{\text{切线：}\quad P=P_0+s\boldsymbol\tau,\ s\in\mathbb R},
$$

$$
\boxed{\text{法平面：}\quad
x'(t_0)(x-x_0)+y'(t_0)(y-y_0)+z'(t_0)(z-z_0)=0}.
$$

切线的方向向量就是法平面的法向量。切线对称式只在对应分量非零时使用。

**两曲面交线：** 设 $F,G$ 在 $P_0$ 邻域内具有连续一阶偏导数，且两梯度在该点不平行，则

$$
\boxed{\boldsymbol\tau=\nabla F(P_0)\times\nabla G(P_0)}.
$$

将此向量代入上述切线、法平面公式即可。若

$$
\frac{\partial(F,G)}{\partial(y,z)}(P_0)
=\begin{vmatrix}F_y&F_z\\G_y&G_z\end{vmatrix}_{P_0}\ne0,
$$

则局部也可写为 $x=x,\ y=y(x),\ z=z(x)$，以 $(1,y'(x_0),z'(x_0))$ 为切向量。叉积为零时，上述方法失效，不能直接断定曲线没有切线。

### 空间曲面的切平面与法线 <span id="section-8-12"></span>

**隐式曲面：** 设 $F(x,y,z)=0$ 在 $P_0$ 邻域内具有连续一阶偏导数，且 $\nabla F(P_0)\ne\boldsymbol0$，则

$$
\boldsymbol n=\nabla F(P_0)=(F_x(P_0),F_y(P_0),F_z(P_0)).
$$

$$
\boxed{\text{切平面：}\quad
F_x(P_0)(x-x_0)+F_y(P_0)(y-y_0)+F_z(P_0)(z-z_0)=0},
$$

$$
\boxed{\text{法线：}\quad P=P_0+s\nabla F(P_0),\ s\in\mathbb R}.
$$

**显式曲面：** 对 $z=f(x,y)$，设 $f$ 在 $(x_0,y_0)$ 处可微，$z_0=f(x_0,y_0)$，可取法向量

$$
\boldsymbol n=(f_x(x_0,y_0),f_y(x_0,y_0),-1),
$$

于是切平面为

$$
\boxed{z-z_0=f_x(x_0,y_0)(x-x_0)+f_y(x_0,y_0)(y-y_0)},
$$

法线为 $(x,y,z)=(x_0,y_0,z_0)+s(f_x,f_y,-1)$，其中偏导数均在 $(x_0,y_0)$ 处取值。

若要法向量朝上，可取 $(-f_x,-f_y,1)$；朝下则取 $(f_x,f_y,-1)$。法向量反向不改变切平面和法线，但会改变定向。

**选法：** 曲线求切线先找切向量，曲面求切平面先找法向量；求法平面用曲线切向量，求法线用曲面法向量。

本次补充依据：`Pictures/1` 中编号 1004—1021 的 18 张照片。仅整理照片中可辨认的正文与批注；截断的例 17.2、例 17.6 未补写题干。

## <span style="color: #3498db;">第九部分：曲线积分、曲面积分</span> <span id="section-9"></span>

## <span style="color: #3498db;">第十部分：特殊公式</span> <span id="section-10"></span>

### 三角恒等式 <span id="section-10-1"></span>

$$
\sec x=\frac1{\cos x},\qquad\csc x=\frac1{\sin x}
$$

$$
\sin^2x+\cos^2x=1,\qquad1+\tan^2x=\sec^2x,\qquad1+\cot^2x=\csc^2x
$$

各式须有定义：涉及正割、正切时 $\cos x\ne0$；涉及余割、余切时 $\sin x\ne0$。

### 根式与绝对值 <span id="section-10-2"></span>

$$
\boxed{\sqrt{a^2}=|a|}\qquad(a\in\mathbb R)
$$

算术平方根非负：当 $a\ge0$ 时结果为 $a$；当 $a<0$ 时结果为 $-a$。不能直接把 $\sqrt{a^2}$ 写成 $a$。

### 平方和公式 <span id="section-10-3"></span>

$$
1^2+2^2+\cdots+n^2=\sum_{k=1}^n k^2
=\frac{n(n+1)(2n+1)}6
\qquad(n\in\mathbb N^+).
$$

### 常用不等式 <span id="section-10-4"></span>

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
\frac{3}{\frac1a+\frac1b+\frac1c}
\le\sqrt[3]{abc}\le\frac{a+b+c}{3}
\le\sqrt{\frac{a^2+b^2+c^2}{3}}
\qquad(a,b,c>0)
$$

从左到右依次为**调和平均数、几何平均数、算术平均数、平方平均数**；等号成立当且仅当 $a=b=c$。

一般地，$m$ 个正数 $a_1,\ldots,a_m$ 的调和平均数为“倒数的算术平均数再取倒数”：

$$
\boxed{H=\frac{m}{\displaystyle\sum_{i=1}^{m}\frac1{a_i}}}.
$$

### 斯特林公式（阶乘的渐近估计） <span id="section-10-5"></span>

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

### 高斯积分（重点记忆） <span id="section-10-6"></span>

$$
\boxed{\int_0^{+\infty}e^{-u^2}\,\mathrm du=\frac{\sqrt{\pi}}2}.
$$

### 零的阶乘 <span id="section-10-7"></span>

$$
\boxed{0!=1}.
$$
