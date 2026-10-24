# 概率论公式笔记

## <span style="color: #3498db;">第一章：随机事件与概率</span>

### 事件的包含：B 发生必然导致 A 发生

$$
\boxed{A\supseteq B\iff B\subseteq A
\iff B\text{ 发生必然导致 }A\text{ 发生}}.
$$

### 互不相容事件（互斥事件）：不能同时发生

$$
\boxed{A\cap B=\varnothing}.
$$

若 $A,B$ 互斥，则两者不能同时发生，但可以都不发生。

若 $A_1,A_2,\ldots,A_n$ **两两互不相容** ，即

$$
A_i\cap A_j=\varnothing,\qquad i\ne j,
$$

则它们并集的概率等于各事件概率之和：

$$
\boxed{P(A_1\cup A_2\cup\cdots\cup A_n)
=P(A_1)+P(A_2)+\cdots+P(A_n)
=\sum_{i=1}^{n}P(A_i)}.
$$

注意，这里要求两两交集都为空，仅有 $A_1\cap A_2\cap\cdots\cap A_n=\varnothing$ 不够。

### 对立事件：互斥且并集为全集

$A,B$ 互为对立事件，必须同时满足

$$
\boxed{A\cap B=\varnothing,\qquad A\cup B=\Omega}.
$$

此时 $B=\overline A$、$A=\overline B$，每次试验中两者**恰好发生一个** 。

### 分配律

交对并的分配律：

$$
\boxed{A\cap(B\cup C)=(A\cap B)\cup(A\cap C)}.
$$

并对交的分配律：

$$
\boxed{A\cup(B\cap C)=(A\cup B)\cap(A\cup C)}.
$$

### 德摩根律（对偶律）

$$
\boxed{\overline{A\cup B}=\overline A\cap\overline B},
$$

$$
\boxed{\overline{A\cap B}=\overline A\cup\overline B}.
$$

### 概率的加法公式

以下用 $AB$ 简记 $A\cap B$，$ABC$ 简记 $A\cap B\cap C$。

两个事件：

$$
\boxed{P(A\cup B)=P(A)+P(B)-P(AB)}.
$$

三个事件：

$$
\boxed{
\begin{aligned}
P(A\cup B\cup C)
&=P(A)+P(B)+P(C)\\
&\quad-P(AB)-P(AC)-P(BC)+P(ABC).
\end{aligned}}
$$

**记忆：单个相加，两两相减，三个相交再加回。** 加法公式适用于一般事件，不要求互不相容。

### 概率的减法公式

$A-B=A\cap\overline B$，表示 $A$ 发生而 $B$ 不发生，则

$$
\boxed{P(A-B)=P(A)-P(AB)}.
$$

若 $B\subseteq A$，则 $AB=B$，可简化为 $P(A-B)=P(A)-P(B)$。

### 条件概率与两个事件的乘法公式

当 $P(A)>0$ 时，$A$ 已发生条件下 $B$ 发生的条件概率为

$$
\boxed{P(B\mid A)=\frac{P(AB)}{P(A)}}.
$$

因此，乘法公式为

$$
\boxed{P(AB)=P(A)P(B\mid A)},\qquad P(A)>0.
$$

同理，也有

$$
\boxed{P(AB)=P(B)P(A\mid B)},\qquad P(B)>0.
$$

### 条件概率的加法与减法公式

设 $P(C)>0$，则在同一条件 $C$ 下，概率的加法、减法公式仍成立。

并事件：

$$
\boxed{P(A\cup B\mid C)
=P(A\mid C)+P(B\mid C)-P(AB\mid C)}.
$$

差事件：

$$
\boxed{P(A-B\mid C)=P(A\mid C)-P(AB\mid C)}.
$$

**记忆：把普通概率公式中的每一项都加上同一个条件 $C$。** $P(A\cup B\mid C)$ 表示在 $C$ 已发生的条件下，$A,B$ 至少发生一个的概率。

### n 个事件的乘法公式

设 $n\ge2$，若

$$
P(A_1A_2\cdots A_{n-1})>0,
$$

则

$$
\boxed{
\begin{aligned}
P(A_1A_2\cdots A_n)
&=P(A_1)P(A_2\mid A_1)P(A_3\mid A_1A_2)\\
&\quad\cdots P(A_n\mid A_1A_2\cdots A_{n-1}).
\end{aligned}}
$$

**记忆：第一个事件直接写概率；从第二个开始，每一项都以前面所有事件同时发生为条件。** 上述正概率条件保证公式中的各个条件概率都有定义。

### 完备事件组：两两不相容且并集为全集

若事件 $B_1,B_2,\ldots,B_n$ 同时满足

$$
\boxed{B_i\cap B_j=\varnothing\quad(i\ne j),\qquad
\bigcup_{i=1}^{n}B_i=\Omega},
$$

则称它们构成一个**完备事件组** ，也称样本空间的一个划分。

**记忆：两两不相容，合起来覆盖全集。** 每次试验中，$B_1,\ldots,B_n$ 恰好发生一个。用于下面的全概率公式和贝叶斯公式时，要求各 $P(B_i)>0$。

### 全概率公式

设 $B_1,B_2,\ldots,B_n$ 构成完备事件组，且 $P(B_i)>0$，则对任意事件 $A$，有

$$
\boxed{P(A)=\sum_{i=1}^{n}P(B_i)P(A\mid B_i)}.
$$

即

$$
P(A)=P(B_1)P(A\mid B_1)+\cdots+P(B_n)P(A\mid B_n).
$$

**记忆：按完备事件组分类，每类的概率乘该类中 $A$ 发生的条件概率，再把各类结果相加。**

### 贝叶斯公式

设 $B_1,B_2,\ldots,B_n$ 构成完备事件组，各 $P(B_i)>0$，且 $P(A)>0$，则

$$
\boxed{
P(B_i\mid A)
=\frac{P(B_iA)}{P(A)}
=\frac{P(B_i)P(A\mid B_i)}
{\displaystyle\sum_{j=1}^{n}P(B_j)P(A\mid B_j)}
},\qquad i=1,2,\ldots,n.
$$

分子对应指定的第 $i$ 类，分母按全概率公式对所有类别求和，因此用 $j$ 作为求和下标。

**记忆：已知结果 $A$ 发生，反求它来自第 $i$ 类 $B_i$ 的概率。** 全概率公式由各类算总体，贝叶斯公式在结果发生后重新计算各类的条件概率。

### 两个事件相互独立

$$
\boxed{A,B\text{ 相互独立}\iff P(AB)=P(A)P(B)}.
$$

即两个事件同时发生的概率，等于它们各自发生的概率之积。

#### 独立事件取对立后仍独立

若 $A,B$ 相互独立，则下列各对事件也相互独立：

$$
\boxed{A,\overline B;\qquad\overline A,B;\qquad
\overline A,\overline B}.
$$

即

$$
\boxed{P(A\overline B)=P(A)[1-P(B)]},
$$

$$
\boxed{P(\overline A B)=[1-P(A)]P(B)},
$$

$$
\boxed{P(\overline A\,\overline B)=[1-P(A)][1-P(B)]}.
$$

**记忆：独立的两个事件，任意一个或两个换成对立事件后，仍然独立。**

### 伯努利试验与 n 重伯努利试验

若一次试验只区分 $A$ 发生与 $A$ 不发生这两种对立的结果，即 $A$ 与 $\overline A$，则称其为**伯努利试验** 。通常把 $A$ 发生称为“成功”，并记

$$
P(A)=p,\qquad P(\overline A)=1-p.
$$

将同一伯努利试验**独立重复进行 $n$ 次** ，且每次 $A$ 发生的概率均为 $p$，称为 **n 重伯努利试验** 。

**要点：每次只有两类结果、各次相互独立、成功概率 $p$ 保持不变。**

### n 重伯努利试验：二项分布概率公式

设 $X$ 表示 $n$ 次试验中事件 $A$ 发生的次数，则 $X$ 服从参数为 $n,p$ 的二项分布，记为

$$
\boxed{X\sim B(n,p)}.
$$

事件 $A$ **恰好发生 $k$ 次** 的概率为

$$
\boxed{P(X=k)=\binom nk p^k(1-p)^{n-k}},
\qquad k=0,1,\ldots,n,
$$

其中

$$
\binom nk=\frac{n!}{k!(n-k)!}.
$$

**记忆：选出 $k$ 次成功的位置，乘 $k$ 次成功与其余 $n-k$ 次失败的概率。** 上式通常在 $0<p<1$ 时使用；$p=0$ 时 $X=0$ 几乎必然成立，$p=1$ 时 $X=n$ 几乎必然成立。

## <span style="color: #3498db;">第二章：随机变量及其分布</span>

## <span style="color: #3498db;">第三章：多维随机变量及其分布</span>

## <span style="color: #3498db;">第四章：随机变量的数字特征</span>

## <span style="color: #3498db;">第五章：大数定律和中心极限定理</span>

## <span style="color: #3498db;">第六章：数理统计的基本概念</span>

## <span style="color: #3498db;">第七章：参数估计</span>

## <span style="color: #3498db;">第八章：假设检验</span>
