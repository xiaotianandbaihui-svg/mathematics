# \(n\) 阶非齐次线性微分方程初值问题的存在唯一性

## 相关条目

- [范数：向量范数、诱导算子范数与积分不等式](./范数.md)
- [\(n\) 阶齐次线性微分方程初值问题的存在唯一性](./n阶齐次线性微分方程初值问题的存在唯一性.md)

---

## 1. 定理的严格陈述

### 定理

设 \(n\geq 1\)，\(a,b\in\mathbb R\) 且 \(a<b\)，并设

$$
p_0,p_1,\ldots,p_{n-1},f\in C((a,b)).
$$

假定下列端点单侧极限都存在，并且都是有限实数：

$$
\lim_{x\to a^+}p_j(x),\qquad
\lim_{x\to b^-}p_j(x),
\qquad j=0,1,\ldots,n-1,
$$

以及

$$
\lim_{x\to a^+}f(x),\qquad
\lim_{x\to b^-}f(x).
$$

任取 \(x_0\in(a,b)\) 和任意实数

$$
c_0,c_1,\ldots,c_{n-1}.
$$

则初值问题

$$
y^{(n)}(x)
+\sum_{j=0}^{n-1}p_j(x)y^{(j)}(x)
=f(x),
\qquad x\in(a,b),
\tag{1}
$$

$$
y^{(k)}(x_0)=c_k,
\qquad k=0,1,\ldots,n-1,
\tag{2}
$$

在 \(C^n((a,b))\) 中存在唯一解。

这里约定 \(y^{(0)}:=y\)。因此式 (1) 对 \(n=1\) 也具有明确含义。

这里从始至终只在开区间 \((a,b)\) 上讨论函数。端点单侧极限的假设只用于推出有关函数在 \((a,b)\) 上有界；证明中不把这些函数定义到端点上。

---

## 2. 本文采用的范数及其基本不等式

对向量 \(u=(u_1,\ldots,u_n)^{\mathsf T}\in\mathbb R^n\)，采用欧氏范数

$$
\|u\|_2
:=
\left(\sum_{i=1}^n u_i^2\right)^{1/2}.
\tag{3}
$$

对矩阵 \(M=(m_{ij})\in\mathbb R^{n\times n}\)，采用 Frobenius 范数

$$
\|M\|_F
:=
\left(\sum_{i=1}^n\sum_{j=1}^n m_{ij}^2\right)^{1/2}.
\tag{4}
$$

当 \(n\geq2\) 时，Frobenius 范数不是由欧氏向量范数诱导出来的算子范数；本文也不把它作为诱导范数使用。不过，下面的相容性不等式成立：

$$
\boxed{\|Mu\|_2\leq \|M\|_F\|u\|_2.}
\tag{5}
$$

事实上，由柯西—施瓦茨不等式，

$$
\left(\sum_{j=1}^n m_{ij}u_j\right)^2
\leq
\left(\sum_{j=1}^n m_{ij}^2\right)
\left(\sum_{j=1}^n u_j^2\right).
$$

对 \(i\) 求和可得

$$
\begin{aligned}
\|Mu\|_2^2
&=
\sum_{i=1}^n
\left(\sum_{j=1}^n m_{ij}u_j\right)^2\\
&\leq
\sum_{i=1}^n
\left(\sum_{j=1}^n m_{ij}^2\right)\|u\|_2^2\\
&=
\|M\|_F^2\|u\|_2^2.
\end{aligned}
$$

两边开平方即得到式 (5)。

Frobenius 范数还满足三角不等式

$$
\boxed{\|M+N\|_F\leq\|M\|_F+\|N\|_F.}
\tag{6}
$$

这是因为把矩阵的全部元素依次排列后，Frobenius 范数就是相应有限维向量的欧氏范数。也可以直接由柯西—施瓦茨不等式计算：

$$
\begin{aligned}
\|M+N\|_F^2
&=
\|M\|_F^2
+2\sum_{i,j}m_{ij}n_{ij}
+\|N\|_F^2\\
&\leq
\|M\|_F^2
+2\|M\|_F\|N\|_F
+\|N\|_F^2\\
&=
\bigl(\|M\|_F+\|N\|_F\bigr)^2.
\end{aligned}
$$

对于两个 \(n\times n\) 矩阵，Frobenius 范数还满足

$$
\|MN\|_F\leq\|M\|_F\|N\|_F,
$$

当 \(n=1\) 时上式恒取等号；当 \(n\geq2\) 时，等号一般不成立。例如，取

$$
M=N=I_n,
$$

则

$$
\|MN\|_F=\sqrt n
<
n=\|M\|_F\|N\|_F.
$$

下面证明上述不等式。若

$$
M=(m_{ik}),\qquad N=(n_{kj}),
$$

则由柯西—施瓦茨不等式，

$$
\begin{aligned}
\|MN\|_F^2
&=
\sum_{i,j}\left(\sum_km_{ik}n_{kj}\right)^2\\
&\leq
\sum_{i,j}
\left(\sum_km_{ik}^2\right)
\left(\sum_\ell n_{\ell j}^2\right)\\
&=
\left(\sum_{i,k}m_{ik}^2\right)
\left(\sum_{k,j}n_{kj}^2\right)\\
&=
\|M\|_F^2\|N\|_F^2.
\end{aligned}
$$

本文的 Picard 估计只需要式 (5)，不需要使用矩阵乘积的这个不等式。

此外，若 \(g\colon[\alpha,\beta]\to\mathbb R^n\) 连续，则

$$
\left\|\int_\alpha^\beta g(t)\,dt\right\|_2
\leq
\int_\alpha^\beta\|g(t)\|_2\,dt.
\tag{7}
$$

为证明式 (7)，记

$$
v:=\int_\alpha^\beta g(t)\,dt.
$$

若 \(v=0\)，结论显然。若 \(v\neq0\)，令 \(e=v/\|v\|_2\)，则

$$
\begin{aligned}
\|v\|_2
&=e^{\mathsf T}v\\
&=\int_\alpha^\beta e^{\mathsf T}g(t)\,dt\\
&\leq
\int_\alpha^\beta
\bigl|e^{\mathsf T}g(t)\bigr|\,dt\\
&\leq
\int_\alpha^\beta
\|e\|_2\|g(t)\|_2\,dt\\
&=
\int_\alpha^\beta\|g(t)\|_2\,dt.
\end{aligned}
$$

最后一个不等式仍由柯西—施瓦茨不等式得到。

对于有向积分，式 (7) 给出

$$
\left\|\int_{x_0}^{x}g(t)\,dt\right\|_2
\leq
\int_{J_x}\|g(t)\|_2\,dt,
\tag{8}
$$

其中

$$
J_x:=
\begin{cases}
[x_0,x],&x\geq x_0,\\
[x,x_0],&x<x_0.
\end{cases}
\tag{9}
$$

因为 \(x,x_0\in(a,b)\)，所以 \(J_x\subset(a,b)\)。

---

## 3. 端点极限推出全局有界性

先说明端点条件在证明中的作用。

设 \(g\in C((a,b))\)，并且

$$
\lim_{x\to a^+}g(x),\qquad
\lim_{x\to b^-}g(x)
$$

都是有限实数。分别记这两个极限为 \(\alpha\) 和 \(\beta\)。在极限定义中取误差 \(1\)，并在必要时缩小所得的两个端点邻域，可取

$$
0<\delta_a<\frac{b-a}{3},
\qquad
0<\delta_b<\frac{b-a}{3},
$$

使得

$$
|g(x)-\alpha|<1,
\qquad a<x<a+\delta_a,
$$

以及

$$
|g(x)-\beta|<1,
\qquad b-\delta_b<x<b.
$$

所以

$$
|g(x)|<|\alpha|+1
$$

在左端邻域成立，而

$$
|g(x)|<|\beta|+1
$$

在右端邻域成立。

中间部分

$$
[a+\delta_a,b-\delta_b]
$$

是包含于 \((a,b)\) 的紧区间。由于 \(g\) 在其上连续，存在有限常数 \(B_0\)，使得

$$
|g(x)|\leq B_0,
\qquad
x\in[a+\delta_a,b-\delta_b].
$$

取

$$
B:=|\alpha|+|\beta|+B_0+2,
$$

便有

$$
|g(x)|\leq B,
\qquad x\in(a,b).
$$

因此 \(g\) 在整个 \((a,b)\) 上有界。由实数的确界原理，

$$
\sup_{x\in(a,b)}|g(x)|<\infty.
\tag{10}
$$

把上述结论分别用于 \(p_0,\ldots,p_{n-1},f\)，便知这些函数全都在 \((a,b)\) 上有界。

---

## 4. 化为一阶非齐次线性方程组

令

$$
Y(x)=
\bigl(y^{(j-1)}(x)\bigr)_{j=1}^{n},
\qquad
\mathbf c=
\bigl(c_{j-1}\bigr)_{j=1}^{n}.
\tag{11}
$$

这里两个量都按列向量理解。

定义

$$
A(x)=
\begin{pmatrix}
0&1&0&\cdots&0\\
0&0&1&\cdots&0\\
\vdots&\vdots&\vdots&\ddots&\vdots\\
0&0&0&\cdots&1\\
-p_0(x)&-p_1(x)&-p_2(x)&\cdots&-p_{n-1}(x)
\end{pmatrix},
\tag{12}
$$

以及

$$
F(x)=
\begin{pmatrix}
0\\
0\\
\vdots\\
0\\
f(x)
\end{pmatrix}.
\tag{13}
$$

当 \(n=1\) 时，式 (12) 和式 (13) 分别按

$$
A(x)=(-p_0(x)),\qquad F(x)=(f(x))
$$

理解。

于是原初值问题对应于

$$
Y'(x)=A(x)Y(x)+F(x),
\qquad
Y(x_0)=\mathbf c.
\tag{14}
$$

由 \(p_0,\ldots,p_{n-1},f\) 的连续性可知

$$
A\in C((a,b);\mathbb R^{n\times n}),
\qquad
F\in C((a,b);\mathbb R^n).
$$

而且

$$
\|A(x)\|_F^2
=
(n-1)+\sum_{j=0}^{n-1}|p_j(x)|^2,
\qquad
\|F(x)\|_2=|f(x)|.
\tag{15}
$$

因此可定义有限常数

$$
L:=\sup_{x\in(a,b)}\|A(x)\|_F<\infty,
\tag{16}
$$

$$
K:=\sup_{x\in(a,b)}\|F(x)\|_2<\infty,
\tag{17}
$$

以及

$$
R:=\sup_{x\in(a,b)}|x-x_0|<\infty.
\tag{18}
$$

这里对每个 \(x\in(a,b)\) 都有

$$
|x-x_0|<b-a,
$$

所以式 (18) 中的确界的确有限。

注意，式 (16)—(18) 取得都是开区间上的确界。

---

## 5. Picard 逐次逼近

方程组 (14) 对应的积分方程是

$$
Y(x)
=
\mathbf c
+\int_{x_0}^{x}\bigl(A(t)Y(t)+F(t)\bigr)\,dt.
\tag{19}
$$

在 \((a,b)\) 上定义 Picard 迭代序列

$$
Z_0(x)\equiv\mathbf c,
\tag{20}
$$

$$
Z_{m+1}(x)
=
\mathbf c
+\int_{x_0}^{x}\bigl(A(t)Z_m(t)+F(t)\bigr)\,dt,
\qquad m=0,1,2,\ldots.
\tag{21}
$$

由归纳法，每个

$$
Z_m\colon(a,b)\to\mathbb R^n
$$

都是连续函数。

令

$$
\Delta_m(x):=Z_{m+1}(x)-Z_m(x),
\tag{22}
$$

并记

$$
M:=L\|\mathbf c\|_2+K.
\tag{23}
$$

下面证明：对所有 \(m\geq0\) 和所有 \(x\in(a,b)\)，都有

$$
\boxed{
\|\Delta_m(x)\|_2
\leq
ML^m\frac{|x-x_0|^{m+1}}{(m+1)!}.
}
\tag{24}
$$

这里 \(m=0\) 时 \(L^0=1\)。

当 \(m=0\) 时，由式 (20)—(21)、向量三角不等式、式 (5) 和式 (8)，

$$
\begin{aligned}
\|\Delta_0(x)\|_2
&=
\left\|
\int_{x_0}^{x}
\bigl(A(t)\mathbf c+F(t)\bigr)\,dt
\right\|_2\\
&\leq
\int_{J_x}
\bigl\|A(t)\mathbf c+F(t)\bigr\|_2\,dt\\
&\leq
\int_{J_x}
\left(
\|A(t)\mathbf c\|_2+\|F(t)\|_2
\right)\,dt\\
&\leq
\int_{J_x}
\left(
\|A(t)\|_F\|\mathbf c\|_2+\|F(t)\|_2
\right)\,dt\\
&\leq
\bigl(L\|\mathbf c\|_2+K\bigr)|x-x_0|\\
&=
M|x-x_0|.
\end{aligned}
\tag{25}
$$

所以式 (24) 对 \(m=0\) 成立。

现设式 (24) 对 \(m-1\) 成立，其中 \(m\geq1\)。由式 (21)，非齐次项 \(F\) 在相邻两次迭代作差时相消，故

$$
\Delta_m(x)
=
\int_{x_0}^{x}A(t)\Delta_{m-1}(t)\,dt.
\tag{26}
$$

于是

$$
\begin{aligned}
\|\Delta_m(x)\|_2
&\leq
\int_{J_x}
\|A(t)\Delta_{m-1}(t)\|_2\,dt\\
&\leq
\int_{J_x}
\|A(t)\|_F\|\Delta_{m-1}(t)\|_2\,dt\\
&\leq
\frac{ML^m}{m!}
\int_{J_x}|t-x_0|^m\,dt\\
&=
ML^m\frac{|x-x_0|^{m+1}}{(m+1)!}.
\end{aligned}
\tag{27}
$$

归纳完成。

上述估计没有除以 \(L\)，所以 \(L=0\) 时同样有效。事实上，本题的伴随矩阵含有上超对角线上的 \(1\)，故当 \(n\geq2\) 时必有 \(L>0\)；只有 \(n=1\) 时才可能出现 \(L=0\)。

---

## 6. 在开区间上的一致收敛

由式 (18) 和式 (24)，

$$
\sup_{x\in(a,b)}\|\Delta_m(x)\|_2
\leq
MR\frac{(LR)^m}{(m+1)!}.
\tag{28}
$$

数项级数

$$
\sum_{m=0}^{\infty}
MR\frac{(LR)^m}{(m+1)!}
\tag{29}
$$

收敛。事实上，对每个 \(m\geq0\)，

$$
0\leq
\frac{(LR)^m}{(m+1)!}
\leq
\frac{(LR)^m}{m!},
$$

而指数级数

$$
\sum_{m=0}^{\infty}\frac{(LR)^m}{m!}
$$

收敛。

由 Weierstrass 判别法，函数项级数

$$
\sum_{m=0}^{\infty}\Delta_m(x)
\tag{30}
$$

在开区间 \((a,b)\) 上绝对且一致收敛。Weierstrass 判别法并不要求函数的定义域是闭区间或紧集。

又因为

$$
Z_N
=
Z_0+\sum_{m=0}^{N-1}\Delta_m,
\tag{31}
$$

所以存在向量函数

$$
Y\colon(a,b)\to\mathbb R^n,
$$

使得

$$
\sup_{x\in(a,b)}\|Z_N(x)-Y(x)\|_2
\longrightarrow0.
\tag{32}
$$

即 \(Z_N\to Y\) 在 \((a,b)\) 上一致成立。每个 \(Z_N\) 都连续，而连续函数列的一致极限仍然连续，因此

$$
Y\in C((a,b);\mathbb R^n).
\tag{33}
$$

---

## 7. 极限函数满足积分方程

由式 (5)、式 (16) 和式 (18)，对每个 \(m\) 都有

$$
\begin{aligned}
&\sup_{x\in(a,b)}
\left\|
\int_{x_0}^{x}
A(t)\bigl(Z_m(t)-Y(t)\bigr)\,dt
\right\|_2\\
&\qquad\leq
LR\,
\sup_{t\in(a,b)}
\|Z_m(t)-Y(t)\|_2
\longrightarrow0.
\end{aligned}
\tag{34}
$$

在式 (21) 中令 \(m\to\infty\)。等式左侧的 \(Z_{m+1}\) 和右侧的 \(Z_m\) 都一致收敛于 \(Y\)，而非齐次项 \(F\) 与 \(m\) 无关。因此对每个 \(x\in(a,b)\)，

$$
Y(x)
=
\mathbf c
+\int_{x_0}^{x}\bigl(A(t)Y(t)+F(t)\bigr)\,dt.
\tag{35}
$$

因为 \(A,Y,F\) 都在 \((a,b)\) 上连续，所以

$$
t\longmapsto A(t)Y(t)+F(t)
$$

在 \((a,b)\) 上连续。由微积分基本定理，式 (35) 给出

$$
Y\in C^1((a,b);\mathbb R^n),
$$

并且

$$
Y'(x)=A(x)Y(x)+F(x),
\qquad x\in(a,b).
\tag{36}
$$

令 \(x=x_0\)，式 (35) 中的积分为零，所以

$$
Y(x_0)=\mathbf c.
\tag{37}
$$

因此一阶非齐次初值问题 (14) 至少存在一个解。

---

## 8. 从向量解恢复 \(C^n\) 标量解

把上面得到的向量解写成

$$
Y=(Y_j)_{j=1}^{n}.
$$

这里仍按列向量理解。

令

$$
y:=Y_1.
\tag{38}
$$

方程组 (36) 的前 \(n-1\) 行给出

$$
Y_j'=Y_{j+1},
\qquad j=1,2,\ldots,n-1.
\tag{39}
$$

当 \(n=1\) 时，式 (39) 中的指标集合为空，不需要添加任何等式。

由于每个 \(Y_j\in C^1((a,b))\)，由式 (38) 及式 (39) 逐次得到

$$
y^{(k)}=Y_{k+1},
\qquad k=0,1,\ldots,n-1.
\tag{40}
$$

特别地，\(y^{(n-1)}=Y_n\in C^1((a,b))\)，所以

$$
y\in C^n((a,b)).
$$

方程组最后一行给出

$$
\begin{aligned}
y^{(n)}
&=Y_n'\\
&=-\sum_{j=0}^{n-1}p_jY_{j+1}+f\\
&=-\sum_{j=0}^{n-1}p_jy^{(j)}+f.
\end{aligned}
\tag{41}
$$

这正是方程 (1)。又由式 (37) 和式 (40)，

$$
y^{(k)}(x_0)=c_k,
\qquad k=0,1,\ldots,n-1.
$$

因此原标量初值问题至少存在一个 \(C^n((a,b))\) 解。

---

## 9. 一阶方程组解的唯一性

设

$$
U,V\in C^1((a,b);\mathbb R^n)
$$

都满足

$$
Y'=AY+F,\qquad Y(x_0)=\mathbf c.
$$

令

$$
H:=U-V.
$$

则非齐次项相消，并且

$$
H'(x)=A(x)H(x),
\qquad
H(x_0)=0.
\tag{42}
$$

因此

$$
H(x)=\int_{x_0}^{x}A(t)H(t)\,dt.
\tag{43}
$$

这里不能未经证明就假定 \(H\) 在整个开区间 \((a,b)\) 上有界。为此，固定任意一个 \(x\in(a,b)\)，并采用式 (9) 定义的闭线段 \(J_x\)。因为 \(H\) 在 \(J_x\) 上连续，所以

$$
C_x:=\sup_{t\in J_x}\|H(t)\|_2<\infty.
\tag{44}
$$

下面证明：对每个整数 \(q\geq1\) 和每个 \(s\in J_x\)，都有

$$
\boxed{
\|H(s)\|_2
\leq
C_x\frac{L^q|s-x_0|^q}{q!}.
}
\tag{45}
$$

注意，对任意 \(s\in J_x\)，连接 \(s\) 与 \(x_0\) 的闭线段 \(J_s\) 都包含在 \(J_x\) 中。

当 \(q=1\) 时，由式 (43)，

$$
\begin{aligned}
\|H(s)\|_2
&\leq
\int_{J_s}\|A(t)H(t)\|_2\,dt\\
&\leq
\int_{J_s}\|A(t)\|_F\|H(t)\|_2\,dt\\
&\leq
LC_x|s-x_0|.
\end{aligned}
\tag{46}
$$

所以式 (45) 对 \(q=1\) 成立。

现设式 (45) 对某个 \(q\geq1\) 成立。再次利用式 (43)，

$$
\begin{aligned}
\|H(s)\|_2
&\leq
\int_{J_s}\|A(t)\|_F\|H(t)\|_2\,dt\\
&\leq
\frac{C_xL^{q+1}}{q!}
\int_{J_s}|t-x_0|^q\,dt\\
&=
C_x\frac{L^{q+1}|s-x_0|^{q+1}}{(q+1)!}.
\end{aligned}
\tag{47}
$$

所以式 (45) 对所有 \(q\geq1\) 成立。

现在仍固定原来的 \(x\)，在式 (45) 中取 \(s=x\)，得到

$$
\|H(x)\|_2
\leq
C_x\frac{\bigl(L|x-x_0|\bigr)^q}{q!},
\qquad q\geq1.
\tag{48}
$$

对于每个固定的 \(r\geq0\)，都有

$$
\frac{r^q}{q!}\longrightarrow0
\qquad(q\to\infty).
$$

故在式 (48) 中令 \(q\to\infty\)，可得

$$
\|H(x)\|_2=0.
$$

于是 \(H(x)=0\)。由于 \(x\in(a,b)\) 是任意的，所以

$$
H\equiv0,
$$

即 \(U\equiv V\)。因此一阶非齐次初值问题 (14) 的解唯一。

---

## 10. 原标量初值问题解的唯一性

设 \(y,\widetilde y\in C^n((a,b))\) 都满足方程 (1) 和初值条件 (2)。构造

$$
Y=
\bigl(y^{(j-1)}\bigr)_{j=1}^{n},
\qquad
\widetilde Y=
\bigl(\widetilde y^{(j-1)}\bigr)_{j=1}^{n}.
$$

这里仍将二者视为列向量。

则 \(Y\) 和 \(\widetilde Y\) 都满足同一个一阶初值问题

$$
Y'=AY+F,\qquad Y(x_0)=\mathbf c.
$$

由第 9 节的一阶方程组唯一性，

$$
Y\equiv\widetilde Y.
$$

比较第一分量便得到

$$
y\equiv\widetilde y.
$$

至此，存在性和唯一性全部得证。

---

## 11. 齐次与非齐次情形的关系

若 \(y_1,y_2\) 都是非齐次方程 (1) 的解，则

$$
h:=y_1-y_2
$$

满足相应的齐次方程

$$
h^{(n)}
+\sum_{j=0}^{n-1}p_jh^{(j)}
=0.
$$

因此，若 \(y_p\) 是非齐次方程的一个特解，则非齐次方程的全部解构成集合

$$
y_p+\mathcal H,
$$

其中 \(\mathcal H\) 是相应齐次方程的解空间。换言之，非齐次方程的全部解构成以齐次解空间为方向空间的仿射空间。

反过来，若 \(h\in\mathcal H\)，则由线性性，\(y_p+h\) 仍然满足原非齐次方程。因此这里确实是两个集合之间的相等，而不只是单向包含。

非齐次方程本身通常有无穷多个解；唯一性只在给定 \(n\) 个初始值以后成立。

---

## 12. 一般非首一形式

考虑

$$
\sum_{j=0}^{n}a_j(x)y^{(j)}(x)
=g(x).
\tag{49}
$$

若 \(a_0,\ldots,a_n,g\in C((a,b))\)，并且

$$
a_n(x)\neq0,\qquad x\in(a,b),
$$

则在 \((a,b)\) 内可以除以 \(a_n(x)\)，得到

$$
y^{(n)}
+\sum_{j=0}^{n-1}\frac{a_j(x)}{a_n(x)}y^{(j)}
=\frac{g(x)}{a_n(x)}.
\tag{50}
$$

要直接应用本文在整个开区间上的一次性 Picard 估计，还需保证

$$
\frac{a_j}{a_n},
\qquad
\frac{g}{a_n}
$$

在两个端点处都有有限的单侧极限。一个常用的充分条件是：各 \(a_j,g\) 都有有限端点单侧极限，并且 \(a_n\) 的两个端点单侧极限都不等于零。

---

## 最终结论

设首一 \(n\) 阶非齐次线性微分方程的所有系数和非齐次项都在开区间 \((a,b)\) 上连续，并且在两个端点处都有有限的单侧极限。则对任意内点 \(x_0\in(a,b)\) 以及任意 \(n\) 个初始值，该初值问题在 \(C^n((a,b))\) 中存在唯一解。

证明始终在开区间 \((a,b)\) 上进行；端点极限只负责保证全局有界性，所有全局界均通过开区间上的确界取得。
