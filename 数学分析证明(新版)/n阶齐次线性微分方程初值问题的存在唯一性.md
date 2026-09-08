# \(n\) 阶齐次线性微分方程初值问题的存在唯一性

## 相关条目

- [范数：向量范数、诱导算子范数与积分不等式](./范数.md)：本文在 Picard 迭代、矩阵估计及有向积分处理中使用的范数工具。

---

## 1. 严格的定理陈述

### 定理

设 \(n\ge 1\)，\(a<b\)，并设

$$
p_0,p_1,\ldots,p_{n-1}\in C((a,b)).且\lim_{x->a^+}p_{0}(x)  、\lim_{x->a^+}p_{1}(x)、...、\lim_{x->a^+}p_{n}(x)存在。\lim_{x->b^-}p_{0}(x)  、\lim_{x->b^-}p_{1}(x)、...、\lim_{x->b^-}p_{n}(x)存在
$$

任取 \(x_0\in(a,b)\) 和任意实数

$$
c_0,c_1,\ldots,c_{n-1}.
$$

则初值问题

$$
y^{(n)}(x)
+p_{n-1}(x)y^{(n-1)}(x)
+\cdots
+p_1(x)y'(x)
+p_0(x)y(x)=0,
\qquad x\in(a,b),
\tag{1}
$$

$$
y^{(k)}(x_0)=c_k,
\qquad k=0,1,\ldots,n-1,
\tag{2}
$$

在 \(C^n((a,b))\) 中存在唯一解。

这里采用如下标准约定：

- \(y\in C^n((a,b))\) 是指 \(y\) 在 \((a,b)\) 内有直到 \(n\) 阶的导数

---

## 2. 化为一阶线性方程组

令

$$
Y(x)=
\begin{pmatrix}
y(x)\\
y'(x)\\
\vdots\\
y^{(n-1)}(x)
\end{pmatrix},
\qquad
\mathbf c=
\begin{pmatrix}
c_0\\
c_1\\
\vdots\\
c_{n-1}
\end{pmatrix}.
$$

定义 \(n\times n\) 矩阵函数

$$
A(x)=
\begin{pmatrix}
0&1&0&\cdots&0\\
0&0&1&\cdots&0\\
\vdots&\vdots&\vdots&\ddots&\vdots\\
0&0&0&\cdots&1\\
-p_0(x)&-p_1(x)&-p_2(x)&\cdots&-p_{n-1}(x)
\end{pmatrix}.
$$

当 \(n=1\) 时，上式按 \(A(x)=(-p_0(x))\) 理解。

于是原初值问题对应于

$$
Y'(x)=A(x)Y(x),
\qquad
Y(x_0)=\mathbf c.
\tag{3}
$$

由于每个 \(p_j\) 都在 \((a,b)\) 上连续，所以 \(A\in C((a,b);\mathbb R^{n\times n})\)。

固定 \(\mathbb R^n\) 上任意一个向量范数，并用相应的诱导矩阵范数。由连续函数在紧集上有界，存在有限常数

$$
L:=\sup_{x\in(a,b)}\|A(x)\|\ge 0.
\tag{4}
$$

再记

$$
R:=\max\{x_0-a,\ b-x_0\}.
\tag{5}
$$

---

## 3. Picard 逐次逼近与一致收敛

方程组 (3) 对应的积分方程是

$$
Y(x)=\mathbf c+\int_{x_0}^{x}A(t)Y(t)\,dt.
\tag{6}
$$

定义 Picard 迭代序列

$$
Z_0(x)\equiv\mathbf c,
$$

$$
Z_{m+1}(x)
=
\mathbf c+\int_{x_0}^{x}A(t)Z_m(t)\,dt,
\qquad m=0,1,2,\ldots.
\tag{7}
$$

由归纳法，每个 \(Z_m\) 都是 \([a,b]\) 上的连续向量函数。

令

$$
\Delta_m(x):=Z_{m+1}(x)-Z_m(x).
$$

我们证明：对所有 \(m\ge0\) 和 \(x\in[a,b]\)，都有

$$
\boxed{
\|\Delta_m(x)\|
\le
\|\mathbf c\|\,L^{m+1}
\frac{|x-x_0|^{m+1}}{(m+1)!}.
}
\tag{8}
$$

当 \(m=0\) 时，

$$
\begin{aligned}
\|\Delta_0(x)\|
&=
\left\|
\int_{x_0}^{x}A(t)\mathbf c\,dt
\right\|\\
&\le
\int_{\min\{x,x_0\}}^{\max\{x,x_0\}}
\|A(t)\|\,\|\mathbf c\|\,dt\\
&\le
\|\mathbf c\|L|x-x_0|,
\end{aligned}
$$

所以式 (8) 对 \(m=0\) 成立。

现设式 (8) 对 \(m-1\) 成立，其中 \(m\ge1\)。由式 (7)，

$$
\Delta_m(x)
=
\int_{x_0}^{x}A(t)\Delta_{m-1}(t)\,dt.
$$

因此

$$
\begin{aligned}
\|\Delta_m(x)\|
&\le
\int_{\min\{x,x_0\}}^{\max\{x,x_0\}}
\|A(t)\|\,\|\Delta_{m-1}(t)\|\,dt\\
&\le
\|\mathbf c\|\frac{L^{m+1}}{m!}
\int_{\min\{x,x_0\}}^{\max\{x,x_0\}}
|t-x_0|^m\,dt\\
&=
\|\mathbf c\|L^{m+1}
\frac{|x-x_0|^{m+1}}{(m+1)!}.
\end{aligned}
$$

归纳完成。

由 \(|x-x_0|\le R\)，可得

$$
\sup_{x\in[a,b]}\|\Delta_m(x)\|
\le
\|\mathbf c\|
\frac{(LR)^{m+1}}{(m+1)!}.
\tag{9}
$$

而数项级数

$$
\sum_{m=0}^{\infty}
\|\mathbf c\|
\frac{(LR)^{m+1}}{(m+1)!}
=
\|\mathbf c\|\bigl(e^{LR}-1\bigr)
$$

收敛。由 Weierstrass 判别法，函数项级数

$$
\sum_{m=0}^{\infty}\Delta_m(x)
$$

在 \([a,b]\) 上绝对且一致收敛。又因为

$$
Z_N
=
Z_0+\sum_{m=0}^{N-1}\Delta_m,
$$

所以存在连续向量函数 \(Y\)，使得

$$
Z_N\longrightarrow Y
$$

在 \([a,b]\) 上一致成立。

注意，上述写法没有除以 \(L\)，所以 \(L=0\) 时同样有效；此时 \(A\equiv0\)，迭代序列事实上从一开始就是常向量 \(\mathbf c\)。

---

## 4. 极限函数满足积分方程

因为 \(Z_m\to Y\) 一致，并且 \(\|A(t)\|\le L\)，所以

$$
\begin{aligned}
&\sup_{x\in[a,b]}
\left\|
\int_{x_0}^{x}A(t)\bigl(Z_m(t)-Y(t)\bigr)\,dt
\right\|\\
&\qquad\le
LR\,
\sup_{t\in[a,b]}\|Z_m(t)-Y(t)\|
\longrightarrow0.
\end{aligned}
\tag{10}
$$

在式 (7) 中令 \(m\to\infty\)，便得到

$$
Y(x)
=
\mathbf c+\int_{x_0}^{x}A(t)Y(t)\,dt.
\tag{11}
$$

由于 \(A\) 和 \(Y\) 都连续，函数 \(t\mapsto A(t)Y(t)\) 连续。由微积分基本定理，式 (11) 给出

$$
Y'(x)=A(x)Y(x)
$$

在 \((a,b)\) 上成立，并在端点处按相应的单侧导数成立；同时 \(Y(x_0)=\mathbf c\)。因此方程组 (3) 至少存在一个解。

---



## 5. 唯一性证明

设 \(U,V\in C^1([a,b];\mathbb R^n)\) 都满足方程组 (3)。令

$$
H:=U-V.
$$

则

$$
H(x_0)=0,
\qquad
H(x)=\int_{x_0}^{x}A(t)H(t)\,dt.
\tag{14}
$$

因为 \(H\) 连续且 \([a,b]\) 紧，常数

$$
C:=\max_{x\in[a,b]}\|H(x)\|
$$

是有限的。

下面证明：对每个整数 \(q\ge1\) 和每个 \(x\in[a,b]\)，都有

$$
\|H(x)\|
\le
C\frac{L^q|x-x_0|^q}{q!}.
\tag{15}
$$

先由 \(\|H(t)\|\le C\) 和式 (14) 得到

$$
\|H(x)\|
\le
\int_{\min\{x,x_0\}}^{\max\{x,x_0\}}LC\,dt
=CL|x-x_0|,
$$

所以式 (15) 对 \(q=1\) 成立。若式 (15) 对某个 \(q\ge1\) 成立，则由式 (14)，

$$
\begin{aligned}
\|H(x)\|
&\le
\int_{\min\{x,x_0\}}^{\max\{x,x_0\}}
\|A(t)\|\,\|H(t)\|\,dt\\
&\le
\frac{CL^{q+1}}{q!}
\int_{\min\{x,x_0\}}^{\max\{x,x_0\}}
|t-x_0|^q\,dt\\
&=
C\frac{L^{q+1}|x-x_0|^{q+1}}{(q+1)!}.
\end{aligned}
$$

所以式 (15) 对一切 \(q\ge1\) 成立。

固定任意 \(x\in[a,b]\)。由于对每个固定的 \(r\ge0\) 都有

$$
\frac{r^q}{q!}\longrightarrow0
\qquad(q\to\infty),
$$
![alt text](image.png)
在式 (15) 中令 \(q\to\infty\)，得到

$$
\|H(x)\|=0.
$$

故 \(H\equiv0\)，即 \(U\equiv V\)。因此一阶初值问题 (3) 的解唯一。

任意一个原标量初值问题的解都会产生一个满足 (3) 的向量解，所以一阶方程组的唯一性立即推出原 \(n\) 阶标量初值问题的唯一性。定理得证。

---

## 6. 推论：解空间为 \(n\) 维，并存在一组基本解系

对 \(j=1,\ldots,n\)，取第 \(j\) 个标准基向量 \(e_j\) 作为方程组在 \(x_0\) 处的初值。由上面的存在唯一性定理，得到唯一的标量解 \(\varphi_j\)，满足

$$
\varphi_j^{(k)}(x_0)=\delta_{k+1,j},
\qquad
k=0,1,\ldots,n-1.
\tag{16}
$$

它们在 \(x_0\) 处的 Wronskian（朗斯基）行列式为

$$
W(\varphi_1,\ldots,\varphi_n)(x_0)
=
\det I_n
=1,
$$

所以 \(\varphi_1,\ldots,\varphi_n\) 线性无关。

若 \(y\) 是方程 (1) 的任意解，并记

$$
c_k=y^{(k)}(x_0),
\qquad k=0,\ldots,n-1,
$$

则

$$
\widetilde y
=
\sum_{j=1}^{n}c_{j-1}\varphi_j
$$

与 \(y\) 具有完全相同的 \(n\) 个初始值。由唯一性，

$$
y=\widetilde y.
$$

因此，方程 (1) 在 \([a,b]\) 上的解空间恰好是 \(n\) 维的，而

$$
\{\varphi_1,\ldots,\varphi_n\}
$$

构成一组基本解系。

---

## 8. 条件的准确范围

1. 对一般形式

   $$
   a_n(x)y^{(n)}+\cdots+a_0(x)y=0,
   $$

   若各 \(a_j\) 连续且 \(a_n(x)\neq0\) 对所有 \(x\in[a,b]\) 成立，则可除以 \(a_n\)，化为本定理的首一形式。

2. 如果最高阶系数允许为零，就不能保证任意初值都有解。例如

   $$
   xy'(x)-y(x)=0
   $$

   在 \(x_0=0\) 处要求 \(y(0)=1\) 时不可能有解，因为方程在 \(x=0\) 处强制给出 \(y(0)=0\)。

3. 对任意区间 \(I\) 而不只是闭区间，只要 \(p_0,\ldots,p_{n-1}\) 在 \(I\) 上连续，就可以先在每个含 \(x_0\) 的紧子区间上应用上述定理，再利用唯一性把这些局部结果拼接起来，从而得到整个 \(I\) 上的唯一解。

---

## 最终结论

原证明的 Picard 迭代部分可以作为存在性证明的主体，但它没有完成所声称的唯一性，也遗漏了从向量解恢复 \(C^n\) 标量解等必要步骤。补上上述论证后，才能严格得到：

$$
\boxed{
\text{连续系数的首一 }n\text{ 阶线性齐次方程，对任意 }n\text{ 个初始值，在给定区间上存在唯一解。}
}
$$


## 朗斯基行列式和函数的相关性
![alt text](image-3.png)
用反证法证明，图片的仅做参考
## n阶齐次方程组一定有n个线性无关的解
![alt text](image-4.png)
## 线性无关则朗斯基行列式不为0
![alt text](image-6.png)
的确是反证法，但不是视频里那么反证的。其方法还是可以做一下参考
[视频链接](https://www.bilibili.com/video/BV1N4qnYiEeB/?)
## 对于n阶线性微分方程
![alt text](image-5.png)
这个定理的表述不太完整。其实应该是**任意线性叠加后同初值的解** 这里就比如取t0，c1，c2...,cn任意取  只要x(t0)=c~1~x~1~(t~0~)+c~2~x~2~(t~0~)+...+c~n~x~n~(t~0~) 那么这组系数和这n个线性无关的式子组合出来的新式子就是我们的x(t)。  （利用前面的微分方程截得存在唯一性证明的）

也正是因为前面说的朗斯基行列式不为0，那么x~1~(t0)  x~2~(t0) ... x~n~(t0)不可能同时为0，不然就存在一个t0让朗斯基行列式为0了（行列式的第一行全部为0，自然行列式就为0了）。

线性代数的知识告诉我们，初值方程一定有解，得到一组{ci}，再利用微分方程解的存在唯一性，那现在对于任意一个解，就一定存在一组{ci}让这组{ci}和x~i~(t)的组合得到这个解。
## 相关则朗斯基行列式为0
![alt text](image-7.png)