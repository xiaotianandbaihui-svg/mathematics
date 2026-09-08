# \(n\) 阶常系数齐次线性微分方程的通解

## 一、结论

设 \(n\ge1\)，\(I\) 是一个非空开区间，考虑实系数方程

$$
y^{(n)}+a_{n-1}y^{(n-1)}+\cdots+a_1y'+a_0y=0,
\tag{1}
$$

其特征多项式为

$$
P(t)=t^n+a_{n-1}t^{n-1}+\cdots+a_1t+a_0.
$$

设 \(P\) 的互不相同的实根为

$$
r_1,\ldots,r_p,
$$

重数依次为 \(m_1,\ldots,m_p\)；再从每一对非实共轭根中选取虚部为正的一个，记为

$$
\alpha_1+i\beta_1,\ldots,\alpha_q+i\beta_q
\qquad(\beta_j>0),
$$

重数依次为 \(k_1,\ldots,k_q\)。

那么方程 (1) 的全部实值解恰好是

$$
\boxed{
\begin{aligned}
y(x)
={}&
\sum_{i=1}^{p}
e^{r_i x}
\left(
A_{i,0}+A_{i,1}x+\cdots+A_{i,m_i-1}x^{m_i-1}
\right)
\\
&+
\sum_{j=1}^{q}
e^{\alpha_jx}
\Bigg[
\left(
B_{j,0}+B_{j,1}x+\cdots+B_{j,k_j-1}x^{k_j-1}
\right)\cos(\beta_jx)
\\
&\hspace{5.7em}
+
\left(
C_{j,0}+C_{j,1}x+\cdots+C_{j,k_j-1}x^{k_j-1}
\right)\sin(\beta_jx)
\Bigg],
\end{aligned}}
\tag{2}
$$

其中所有 \(A_{i,\ell},B_{j,\ell},C_{j,\ell}\) 都可以任意取实数。

下面直接证明两件事：

1. 方程的任何解都不会超出式 (2)；
2. 式 (2) 中任意选取这些实数，所得函数都满足方程。

整个证明不使用微分方程初值问题的存在唯一性定理。

---

## 二、先证明复数形式的结论

先允许方程的系数和解取复数值。

由代数基本定理，\(P\) 在复数范围内可以完全分解，并且所有根的重数之和为 \(n\)。

设 \(P\) 的互不相同的复根为

$$
\lambda_1,\ldots,\lambda_s,
$$

相应重数为 \(m_1,\ldots,m_s\)。我们要证明，方程的全部复值解恰好是

$$
\boxed{
y(x)=\sum_{\nu=1}^{s}e^{\lambda_\nu x}Q_\nu(x),
\qquad
\deg Q_\nu\le m_\nu-1,
}
\tag{3}
$$

其中每个 \(Q_\nu\) 都可以任意取满足次数限制的复系数多项式。零多项式当然也允许出现。

这里及下文中，为了简化表述，“多项式的次数不超过某数”总是把零多项式也包括在内。对于一个 \(k\) 阶方程，所说的“解”均指区间 \(I\) 上的 \(C^k\) 函数。

我们对方程的阶数 \(n\) 作归纳。

### 1. 一阶情形

一阶方程可以写成

$$
y'-\lambda y=0.
$$

因为

$$
\bigl(e^{-\lambda x}y(x)\bigr)'
=
e^{-\lambda x}\bigl(y'(x)-\lambda y(x)\bigr),
$$

所以 \(y'-\lambda y=0\) 当且仅当

$$
\bigl(e^{-\lambda x}y(x)\bigr)'=0.
$$

区间上导数恒为 \(0\) 的函数是常数，因此

$$
y(x)=Ce^{\lambda x}.
$$

这正是式 (3) 在 \(n=1\) 时的结论。

### 2. 降低一阶

现在设结论对所有 \(n-1\) 阶常系数齐次线性方程都成立，并考虑一个 \(n\) 阶方程。

任取 \(P\) 的一个根 \(\lambda\)。用附录中的带余除法将 \(P(t)\) 除以 \(t-\lambda\)，可得

$$
P(t)=(t-\lambda)\widetilde P(t)+r,
$$

其中余式 \(r\) 是常数。令 \(t=\lambda\)，便有

$$
r=P(\lambda)=0.
$$

因为 \(P\) 是 \(n\) 次首一多项式，所以商 \(\widetilde P\) 是下面这个 \(n-1\) 次首一多项式：

$$
\widetilde P(t)
=
t^{n-1}+b_{n-2}t^{n-2}+\cdots+b_1t+b_0,
$$

使得

$$
P(t)=(t-\lambda)\widetilde P(t).
\tag{4}
$$

对任意 \(n\) 次可微函数 \(y\)，令

$$
z=y'-\lambda y.
\tag{5}
$$

于是对 \(j=0,1,\ldots,n-1\)，都有

$$
z^{(j)}=y^{(j+1)}-\lambda y^{(j)}.
\tag{6}
$$

将式 (6) 代入

$$
z^{(n-1)}+b_{n-2}z^{(n-2)}+\cdots+b_1z'+b_0z,
$$

所得表达式就是

$$
\begin{aligned}
&(y^{(n)}-\lambda y^{(n-1)})
+b_{n-2}(y^{(n-1)}-\lambda y^{(n-2)})
+\cdots
+b_0(y'-\lambda y).
\end{aligned}
$$

其中各阶导数的系数，恰好就是多项式

$$
(t-\lambda)\widetilde P(t)=P(t)
$$

的各项系数。因此恒有

$$
\begin{aligned}
&z^{(n-1)}+b_{n-2}z^{(n-2)}+\cdots+b_1z'+b_0z
\\
&\qquad
=
y^{(n)}+a_{n-1}y^{(n-1)}+\cdots+a_1y'+a_0y.
\end{aligned}
\tag{7}
$$

也就是说，

$$
\boxed{
y\text{ 满足原来的 }n\text{ 阶方程}
\quad\Longleftrightarrow\quad
z=y'-\lambda y\text{ 满足 }\widetilde P\text{ 对应的 }n-1\text{ 阶方程}.
}
\tag{8}
$$

这里没有使用任何存在唯一性结论；式 (8) 只是把式 (5) 直接代入后得到的恒等式。

### 3. 一个需要用到的积分事实

设 \(\delta\ne0\)，并设

$$
R(x)=r_0+r_1x+\cdots+r_dx^d
$$

是多项式。存在一个次数不超过 \(d\) 的多项式

$$
S(x)=s_0+s_1x+\cdots+s_dx^d
$$

满足

$$
S'(x)+\delta S(x)=R(x).
\tag{9}
$$

事实上，先令

$$
s_d=\frac{r_d}{\delta},
$$

再依次向下令

$$
s_j
=
\frac{r_j-(j+1)s_{j+1}}{\delta}
\qquad(j=d-1,d-2,\ldots,0),
$$

直接比较各次幂的系数，就得到式 (9)。

于是

$$
\bigl(e^{\delta x}S(x)\bigr)'
=e^{\delta x}R(x),
$$

从而对任意固定的 \(x_0\in I\)，

$$
\int_{x_0}^{x}e^{\delta t}R(t)\,dt
=
e^{\delta x}S(x)-e^{\delta x_0}S(x_0).
\tag{10}
$$

这个事实说明：当 \(\delta\ne0\) 时，\(e^{\delta x}\) 乘以一个次数不超过 \(d\) 的多项式，积分后仍然是 \(e^{\delta x}\) 乘以一个次数不超过 \(d\) 的多项式，再加一个常数。

### 4. 原方程的任何解都有式 (3) 的形式

设所选根 \(\lambda\) 在 \(P\) 中的重数为 \(m\)。由式 (4)：

- \(\lambda\) 在 \(\widetilde P\) 中的重数为 \(m-1\)；当 \(m=1\) 时，它不再是 \(\widetilde P\) 的根；
- 其余每个根 \(\mu\ne\lambda\) 的重数保持不变，仍记为 \(m_\mu\)。

这是因为若

$$
P(t)=(t-\lambda)^mH(t),
\qquad
H(\lambda)\ne0,
$$

那么

$$
\widetilde P(t)=(t-\lambda)^{m-1}H(t);
$$

而对 \(\mu\ne\lambda\)，因子 \(t-\lambda\) 在 \(t=\mu\) 处不为 \(0\)，除去这个因子不会改变 \(\mu\) 的重数。

现在设 \(y\) 是原方程的任意一个解，并令 \(z=y'-\lambda y\)。由式 (8)，\(z\) 满足 \(\widetilde P\) 对应的 \(n-1\) 阶方程。根据归纳假设，

$$
z(x)
=
e^{\lambda x}R_\lambda(x)
+
\sum_{\mu\ne\lambda}e^{\mu x}R_\mu(x),
\tag{11}
$$

其中

$$
\deg R_\mu\le m_\mu-1.
\tag{12}
$$

当 \(m\ge2\) 时，还有 \(\deg R_\lambda\le m-2\)；当 \(m=1\) 时，式 (11) 中的第一项省略。

由 \(z=y'-\lambda y\)，有

$$
\bigl(e^{-\lambda x}y(x)\bigr)'=e^{-\lambda x}z(x).
$$

因此

$$
y(x)
=
e^{\lambda x}
\left[
C+\int_{x_0}^{x}e^{-\lambda t}z(t)\,dt
\right].
\tag{13}
$$

把式 (11) 代入：

- 对根 \(\lambda\) 对应的部分，只需积分 \(R_\lambda(t)\)。所得仍为多项式，并且次数不超过 \(m-1\)；
- 对每个 \(\mu\ne\lambda\)，式 (10) 适用于

  $$
  \delta=\mu-\lambda\ne0.
  $$

  因而这部分积分后，是

  $$
  e^{(\mu-\lambda)x}S_\mu(x)
  $$

  加一个常数，其中

  $$
  \deg S_\mu\le m_\mu-1.
  $$

式 (13) 外面还有因子 \(e^{\lambda x}\)，所以这些非常数项变成

$$
e^{\mu x}S_\mu(x).
$$

所有积分产生的常数与式 (13) 中的 \(C\) 合并后，只会增加 \(e^{\lambda x}\) 前面的常数项。因此

$$
y(x)
=
e^{\lambda x}Q_\lambda(x)
+
\sum_{\mu\ne\lambda}e^{\mu x}Q_\mu(x),
$$

其中

$$
\deg Q_\lambda\le m-1,
\qquad
\deg Q_\mu\le m_\mu-1.
$$

这正是式 (3)。所以原方程的任何解都已经包含在式 (3) 中。

### 5. 式 (3) 中的任意选择都确实给出解

反过来，任意选取满足次数限制的多项式，写成

$$
y(x)
=
e^{\lambda x}Q_\lambda(x)
+
\sum_{\mu\ne\lambda}e^{\mu x}Q_\mu(x),
\tag{14}
$$

其中

$$
\deg Q_\lambda\le m-1,
\qquad
\deg Q_\mu\le m_\mu-1.
$$

仍令 \(z=y'-\lambda y\)。直接求导得到

$$
z(x)
=
e^{\lambda x}Q_\lambda'(x)
+
\sum_{\mu\ne\lambda}
e^{\mu x}
\left[
Q_\mu'(x)+(\mu-\lambda)Q_\mu(x)
\right].
\tag{15}
$$

当 \(m=1\) 时，\(Q_\lambda\) 是常数，因而 \(Q_\lambda'=0\)；当 \(m\ge2\) 时，\(Q_\lambda'\) 为零多项式或次数不超过 \(m-2\)。并且

$$
\deg\!\left(
Q_\mu'+(\mu-\lambda)Q_\mu
\right)
\le m_\mu-1.
$$

所以式 (15) 正好具有归纳假设给出的 \(\widetilde P\) 方程的解的形式。由归纳假设，\(z\) 满足这个 \(n-1\) 阶方程；再由恒等式 (8)，\(y\) 满足原来的 \(n\) 阶方程。

因此，式 (3) 没有混入任何不是解的函数。结合上一小节，复数形式的通解已经证完。

---

## 三、化为实数形式

现在回到实系数方程 (1)。

实系数多项式的非实根成共轭对出现，并且一对共轭根的重数相同。复数形式的结论已经证明，下面只需把共轭根对应的项写成实函数。

### 1. 每个实解都能写成式 (2)

设 \(y\) 是实值解。把它看成复值解，由式 (3)，它可以写成各个

$$
e^{\lambda x}Q_\lambda(x)
$$

之和。由于 \(y=\operatorname{Re}y\)，可以对这个和逐项取实部。

对实根 \(r\)，

$$
\operatorname{Re}\!\left(e^{rx}Q_r(x)\right)
=
e^{rx}\operatorname{Re}Q_r(x),
$$

其多项式部分仍为相同次数范围内的实系数多项式。

对一对非实根

$$
\alpha+i\beta,
\qquad
\alpha-i\beta,
\qquad
\beta>0,
$$

设它们在式 (3) 中对应的两个多项式分别为

$$
Q_+(x)=a(x)+ib(x),
\qquad
Q_-(x)=c(x)+id(x),
$$

其中 \(a,b,c,d\) 都是实系数多项式。直接计算可得

$$
\begin{aligned}
&\operatorname{Re}\!\left(
e^{(\alpha+i\beta)x}Q_+(x)
+
e^{(\alpha-i\beta)x}Q_-(x)
\right)
\\
&\qquad
=
e^{\alpha x}
\left[
\bigl(a(x)+c(x)\bigr)\cos(\beta x)
+
\bigl(d(x)-b(x)\bigr)\sin(\beta x)
\right].
\end{aligned}
\tag{16}
$$

两个新多项式的次数都没有超过这一对根的重数减 \(1\)。所以每个实解都具有式 (2) 的形式。

### 2. 式 (2) 中的任意选择都给出实解

对任意实系数多项式 \(A(x),B(x)\)，都有

$$
e^{\alpha x}
\left[
A(x)\cos(\beta x)+B(x)\sin(\beta x)
\right]
=
\operatorname{Re}\!\left(
e^{(\alpha+i\beta)x}\bigl(A(x)-iB(x)\bigr)
\right).
\tag{17}
$$

只要 \(A,B\) 的次数不超过根 \(\alpha+i\beta\) 的重数减 \(1\)，式 (3) 已经证明右边括号内的复函数满足原方程。因为方程的系数都是实数，复值解的实部仍然满足原方程。

实根对应的各项也已经包含在式 (3) 中。最后，方程是线性的，因此这些解的任意有限和仍是解。于是式 (2) 中任意选取所有实系数，所得函数都满足方程 (1)。

至此，式 (2) 确实给出了方程 (1) 的全部实值解。

---

## 附录：多项式带余除法

本附录独立于上面的微分方程证明。

### 定理

设 \(F,G\in\mathbb C[t]\) 且 \(G\ne0\)。那么存在唯一的多项式 \(Q,R\)，使得

$$
F=GQ+R,
$$

并且

$$
R=0
\qquad\text{或}\qquad
\deg R<\deg G.
$$

这里 \(Q\) 称为商，\(R\) 称为余式。特别地，当 \(G\) 是非零常数时，余式只能为 \(0\)。

### 存在性证明

先单独处理 \(F=0\)：此时取 \(Q=R=0\) 即可。

以下设 \(F\ne0\)，记

$$
m:=\deg F,
\qquad
d:=\deg G,
$$

并对非负整数 \(m\) 作强归纳。

若 \(m<d\)，取

$$
Q=0,
\qquad
R=F,
$$

结论成立。

现在设 \(m\ge d\)。设 \(F,G\) 的最高次项分别为

$$
a_mt^m,
\qquad
b_dt^d,
$$

其中 \(a_m,b_d\ne0\)。令

$$
F_1(t)
:=
F(t)-\frac{a_m}{b_d}t^{m-d}G(t).
$$

右边两个 \(m\) 次项恰好抵消，所以

$$
F_1=0
\qquad\text{或}\qquad
\deg F_1<m.
$$

- 若 \(F_1=0\)，取 \(Q_1=R=0\)；
- 若 \(F_1\ne0\)，由强归纳假设，存在 \(Q_1,R\) 使得

  $$
  F_1=GQ_1+R,
  \qquad
  R=0\ \text{或}\ \deg R<\deg G.
  $$

因此在两种情况下都有

$$
F_1=GQ_1+R,
\qquad
R=0\ \text{或}\ \deg R<\deg G.
$$

由 \(F_1\) 的定义，

$$
\begin{aligned}
F
&=
F_1+\frac{a_m}{b_d}t^{m-d}G\\
&=
G\left(
Q_1+\frac{a_m}{b_d}t^{m-d}
\right)+R.
\end{aligned}
$$

所以取

$$
Q
:=
Q_1+\frac{a_m}{b_d}t^{m-d},
$$

就完成了归纳步骤。商和余式的存在性得证。

### 唯一性证明

假设另有两组商和余式满足

$$
F=GQ+R
=G\widetilde Q+\widetilde R,
$$

其中每个余式都为 \(0\) 或次数小于 \(\deg G\)。两式相减得

$$
G(Q-\widetilde Q)
=
\widetilde R-R.
$$

若 \(Q-\widetilde Q\ne0\)，则左边是非零多项式，并且

$$
\deg\!\bigl(G(Q-\widetilde Q)\bigr)
=
\deg G+\deg(Q-\widetilde Q)
\ge\deg G.
$$

但是，右边若非零，其次数必小于 \(\deg G\)；右边若为零，也不可能等于左边的非零多项式。两种情况都产生矛盾。

因此

$$
Q=\widetilde Q,
$$

再代回原等式便有

$$
R=\widetilde R.
$$

所以商与余式都是唯一的。定理得证。
