# \(n\) 阶常系数齐次线性微分方程通解的严格证明

> 本文证明的是**常系数**齐次线性微分方程的通解。对于一般的变系数齐次线性微分方程，通常不存在由特征根给出的这种统一显式公式。

## 相关条目

- [\(n\) 阶齐次线性微分方程初值问题的存在唯一性](./n阶齐次线性微分方程初值问题的存在唯一性.md)：本文在证明“所构造的解已经包含全部解”时使用该定理。

---

## 1. 定理陈述

设 \(n\ge 1\)，考虑实常系数齐次线性微分方程

$$
a_ny^{(n)}+a_{n-1}y^{(n-1)}+\cdots+a_1y'+a_0y=0,
\qquad a_n\ne0.
\tag{1}
$$

其特征多项式为

$$
P(\lambda)
=a_n\lambda^n+a_{n-1}\lambda^{n-1}
+\cdots+a_1\lambda+a_0.
\tag{2}
$$

设 \(P\) 的互不相同的实根为

$$
r_1,\ldots,r_p,
$$

相应的重数为

$$
m_1,\ldots,m_p.
$$

由于 \(P\) 的系数为实数，它的非实根成共轭对出现。从每一对共轭根中选取虚部为正的一个，记为

$$
\alpha_1+i\beta_1,\ldots,\alpha_t+i\beta_t,
\qquad \beta_j>0,
$$

相应的重数为

$$
q_1,\ldots,q_t.
$$

在复数范围内，特征多项式分解为

$$
P(\lambda)
=
a_n
\prod_{i=1}^{p}(\lambda-r_i)^{m_i}
\prod_{j=1}^{t}
\left[(\lambda-\alpha_j)^2+\beta_j^2\right]^{q_j}.
$$

由代数基本定理并比较等式两边的次数，

$$
\sum_{i=1}^{p}m_i+2\sum_{j=1}^{t}q_j=n.
\tag{3}
$$

我们要严格证明，方程 (1) 的全部实值解恰好是

$$
\boxed{
\begin{aligned}
y(x)
={}&
\sum_{i=1}^{p}e^{r_ix}
\left(
C_{i0}+C_{i1}x+\cdots+C_{i,m_i-1}x^{m_i-1}
\right)
\\
&+
\sum_{j=1}^{t}e^{\alpha_jx}
\sum_{k=0}^{q_j-1}x^k
\left(
A_{jk}\cos(\beta_jx)+B_{jk}\sin(\beta_jx)
\right),
\end{aligned}}
\tag{4}
$$

其中所有 \(C_{ik},A_{jk},B_{jk}\) 都是任意实常数。

完整证明必须完成以下三件事：

1. 证明式 (4) 中出现的函数确实满足方程；
2. 证明这些函数线性无关；
3. 证明方程的解空间只有 \(n\) 维，从而这些解没有遗漏任何其他解。

---

## 2. 预备结论一：多项式重根与各阶导数

本文多次使用高阶乘积求导公式

$$
(fg)^{(r)}
=
\sum_{\ell=0}^{r}
\binom{r}{\ell}f^{(\ell)}g^{(r-\ell)}.
$$

该公式可以由数学归纳法得到：\(r=0\) 时显然成立；对 \(r\) 阶公式两边再求一次导数，把所得的两个求和错位相加，再使用

$$
\binom{r}{\ell}+\binom{r}{\ell-1}
=\binom{r+1}{\ell},
$$

便得到 \(r+1\) 阶公式。

### 2.1 从重根推出低阶导数为零

按照重根的定义，\(x_0\) 是多项式 \(P(x)\) 的 \(m\) 重根，是指存在多项式 \(Q(x)\)，使得

$$
P(x)=(x-x_0)^mQ(x),
\qquad Q(x_0)\ne0.
\tag{5}
$$

任取整数 \(r\)，满足

$$
0\le r<m.
$$

对式 (5) 求 \(r\) 阶导数。由高阶乘积求导公式，

$$
P^{(r)}(x)
=
\sum_{\ell=0}^{r}
\binom{r}{\ell}
\left[(x-x_0)^m\right]^{(\ell)}
Q^{(r-\ell)}(x).
\tag{6}
$$

因为 \(0\le\ell\le r<m\)，所以

$$
\left[(x-x_0)^m\right]^{(\ell)}
=
\frac{m!}{(m-\ell)!}(x-x_0)^{m-\ell}.
\tag{7}
$$

令 \(x=x_0\)。由于

$$
m-\ell\ge m-r\ge1,
$$

故式 (7) 在 \(x=x_0\) 处等于零。式 (6) 中每一项都等于零，所以

$$
P(x_0)=P'(x_0)=\cdots=P^{(m-1)}(x_0)=0.
\tag{8}
$$

当 \(r=m\) 时，式 (6) 中只有 \(\ell=m\) 对应的项在 \(x=x_0\) 处可能不为零，因而

$$
P^{(m)}(x_0)=m!Q(x_0)\ne0.
\tag{9}
$$

### 2.2 反过来，从低阶导数为零推出重根

多项式在 \(x_0\) 处的泰勒展开是有限恒等式：

$$
P(x)
=
\sum_{r=0}^{\deg P}
\frac{P^{(r)}(x_0)}{r!}(x-x_0)^r.
\tag{10}
$$

如果

$$
P(x_0)=P'(x_0)=\cdots=P^{(m-1)}(x_0)=0,
$$

那么式 (10) 可以提出因子 \((x-x_0)^m\)，所以 \(x_0\) 至少是 \(m\) 重根。如果进一步有

$$
P^{(m)}(x_0)\ne0,
$$

那么提出 \((x-x_0)^m\) 后剩余多项式在 \(x=x_0\) 处的值为

$$
\frac{P^{(m)}(x_0)}{m!}\ne0,
$$

所以 \(x_0\) 恰好是 \(m\) 重根。

因此得到等价判据

$$
\boxed{
x_0\text{ 是 }P\text{ 的 }m\text{ 重根}
\iff
\begin{cases}
P(x_0)=P'(x_0)=\cdots=P^{(m-1)}(x_0)=0,\\
P^{(m)}(x_0)\ne0.
\end{cases}}
\tag{11}
$$

后面既要使用式 (8)，也要使用式 (11) 的反方向。

---

## 3. 预备结论二：混合偏导数的换序

后面要对 \(e^{\lambda x}\) 先关于 \(x\) 求导，再关于参数 \(\lambda\) 求导，因此必须说明为什么这两个求导次序可以交换。

### 3.1 二阶混合偏导数换序

设 \(f(x,y)\in C^2\)，并固定一点 \((a,b)\)。取充分小的非零实数 \(h,k\)，定义矩形增量

$$
\begin{aligned}
R(h,k)
={}&f(a+h,b+k)-f(a+h,b)\\
&-f(a,b+k)+f(a,b).
\end{aligned}
\tag{12}
$$

固定 \(k\)，令

$$
g(x)=f(x,b+k)-f(x,b).
$$

对 \(g\) 使用一元中值定理，再对

$$
y\longmapsto \frac{\partial f}{\partial x}(a+\theta h,y)
$$

使用一次中值定理，可以得到某些 \(0<\theta,\eta<1\)，使得

$$
\frac{R(h,k)}{hk}
=
\frac{\partial}{\partial y}
\left(\frac{\partial f}{\partial x}\right)
(a+\theta h,b+\eta k).
\tag{13}
$$

反过来，固定 \(h\)，令

$$
v(y)=f(a+h,y)-f(a,y).
$$

先沿 \(y\) 方向、再沿 \(x\) 方向各使用一次中值定理，可以得到某些

$$
0<\theta_1,\eta_1<1,
$$

使得

$$
\frac{R(h,k)}{hk}
=
\frac{\partial}{\partial x}
\left(\frac{\partial f}{\partial y}\right)
(a+\theta_1h,b+\eta_1k).
\tag{14}
$$

式 (13) 与式 (14) 的左边相同。令 \(h,k\to0\)，并使用两个二阶混合偏导数的连续性，得到

$$
\boxed{
\frac{\partial}{\partial y}
\left(\frac{\partial f}{\partial x}\right)(a,b)
=
\frac{\partial}{\partial x}
\left(\frac{\partial f}{\partial y}\right)(a,b).
}
\tag{15}
$$

### 3.2 一个求导越过任意多个求导

先证明：如果 \(f\in C^{r+1}\)，那么

$$
\boxed{
\frac{\partial}{\partial y}
\left(\frac{\partial^r f}{\partial x^r}\right)
=
\frac{\partial^r}{\partial x^r}
\left(\frac{\partial f}{\partial y}\right).
}
\tag{16}
$$

对 \(r\) 作归纳。

当 \(r=1\) 时，式 (16) 就是二阶换序定理。

假设式 (16) 对某个 \(r\ge1\) 成立。现设 \(f\in C^{r+2}\)，则

$$
u(x,y)=\frac{\partial^r f}{\partial x^r}
$$

属于 \(C^2\)。对 \(u\) 使用二阶换序定理，并使用归纳假设：

$$
\begin{aligned}
\frac{\partial}{\partial y}
\left(\frac{\partial^{r+1}f}{\partial x^{r+1}}\right)
&=
\frac{\partial}{\partial y}
\left[
\frac{\partial}{\partial x}
\left(\frac{\partial^r f}{\partial x^r}\right)
\right]\\
&=
\frac{\partial}{\partial x}
\left[
\frac{\partial}{\partial y}
\left(\frac{\partial^r f}{\partial x^r}\right)
\right]\\
&=
\frac{\partial}{\partial x}
\left[
\frac{\partial^r}{\partial x^r}
\left(\frac{\partial f}{\partial y}\right)
\right]\\
&=
\frac{\partial^{r+1}}{\partial x^{r+1}}
\left(\frac{\partial f}{\partial y}\right).
\end{aligned}
$$

所以式 (16) 对所有正整数 \(r\) 成立。

### 3.3 高阶混合偏导数换序

设 \(j,k\) 是正整数，且 \(f\in C^{j+k}\)。我们证明

$$
\boxed{
\frac{\partial^k}{\partial y^k}
\left(\frac{\partial^j f}{\partial x^j}\right)
=
\frac{\partial^j}{\partial x^j}
\left(\frac{\partial^k f}{\partial y^k}\right).
}
\tag{17}
$$

这里 \(f\in C^{j+k}\) 的含义是：按照任意顺序取得的、总阶数不超过 \(j+k\) 的偏导数都存在并且连续；此定义本身并没有预先假设不同求导顺序所得的结果相等。

固定 \(j\)，对 \(k\) 作归纳。

当 \(k=1\) 时，式 (17) 就是式 (16)。

假设式 (17) 对某个 \(k\ge1\) 成立。现设 \(f\in C^{j+k+1}\)。由式 (16)，

$$
\frac{\partial}{\partial y}
\left(\frac{\partial^j f}{\partial x^j}\right)
=
\frac{\partial^j}{\partial x^j}
\left(\frac{\partial f}{\partial y}\right).
$$

所以

$$
\begin{aligned}
\frac{\partial^{k+1}}{\partial y^{k+1}}
\left(\frac{\partial^j f}{\partial x^j}\right)
&=
\frac{\partial^k}{\partial y^k}
\left[
\frac{\partial}{\partial y}
\left(\frac{\partial^j f}{\partial x^j}\right)
\right]\\
&=
\frac{\partial^k}{\partial y^k}
\left[
\frac{\partial^j}{\partial x^j}
\left(\frac{\partial f}{\partial y}\right)
\right].
\end{aligned}
$$

因为

$$
\frac{\partial f}{\partial y}\in C^{j+k},
$$

所以可以对它使用归纳假设：

$$
\begin{aligned}
\frac{\partial^{k+1}}{\partial y^{k+1}}
\left(\frac{\partial^j f}{\partial x^j}\right)
&=
\frac{\partial^j}{\partial x^j}
\left[
\frac{\partial^k}{\partial y^k}
\left(\frac{\partial f}{\partial y}\right)
\right]\\
&=
\frac{\partial^j}{\partial x^j}
\left(\frac{\partial^{k+1}f}{\partial y^{k+1}}\right).
\end{aligned}
$$

因此式 (17) 对所有正整数 \(j,k\) 成立。

这里的连续性条件非常重要：每次交换相邻的两次求导，都是对某个中间函数使用二阶换序定理。若总共要求 \(j+k\) 次导数，则假设 \(f\in C^{j+k}\) 保证每一个中间函数都具有所需的连续二阶偏导数。

### 3.4 \(e^{\lambda x}\) 满足换序所需的连续性

为了避免循环论证，先不使用任何换序结论，直接证明按任意次序求出的偏导数都连续。

设 \(R(x,\lambda)\) 是任意二元多项式。直接使用乘积求导公式可得

$$
\frac{\partial}{\partial x}
\left(R(x,\lambda)e^{\lambda x}\right)
=
\left(
\frac{\partial R}{\partial x}(x,\lambda)
+\lambda R(x,\lambda)
\right)e^{\lambda x},
$$

以及

$$
\frac{\partial}{\partial\lambda}
\left(R(x,\lambda)e^{\lambda x}\right)
=
\left(
\frac{\partial R}{\partial\lambda}(x,\lambda)
+xR(x,\lambda)
\right)e^{\lambda x}.
$$

两个括号中的函数仍然是关于 \((x,\lambda)\) 的多项式。因此，从

$$
e^{\lambda x}=1\cdot e^{\lambda x}
$$

开始，无论下一次选择对 \(x\) 求导还是对 \(\lambda\) 求导，所得函数始终具有

$$
R(x,\lambda)e^{\lambda x}
$$

的形式，其中 \(R\) 是某个二元多项式。对求导总次数作归纳可知：按照任意有限次序得到的每一个偏导数都存在，并且是“多项式乘以 \(e^{\lambda x}\)”的形式，因而关于 \((x,\lambda)\) 连续。

下面再把“先对 \(x\) 求 \(n\) 阶导数、再对 \(\lambda\) 求 \(m\) 阶导数”的结果明确写出。先对 \(x\) 求 \(n\) 阶导数：

$$
\frac{\partial^n}{\partial x^n}e^{\lambda x}
=\lambda^ne^{\lambda x}.
\tag{18}
$$

再对 \(\lambda\) 求 \(m\) 阶导数。由高阶乘积求导公式，

$$
\boxed{
\begin{aligned}
&\frac{\partial^m}{\partial\lambda^m}
\left(
\frac{\partial^n}{\partial x^n}e^{\lambda x}
\right)\\
&=
e^{\lambda x}
\sum_{\ell=0}^{\min\{m,n\}}
\binom{m}{\ell}
\frac{n!}{(n-\ell)!}
\lambda^{n-\ell}x^{m-\ell}.
\end{aligned}}
\tag{19}
$$

式 (19) 右边是有限个如下形式函数的和：

$$
c\,\lambda^a x^b e^{\lambda x},
$$

其中 \(a,b\) 是非负整数，\(c\) 是常数。多项式、指数函数及它们的有限次乘积与有限和都连续，所以式 (19) 关于 \((x,\lambda)\) 连续。

前面的归纳已经证明，\(e^{\lambda x}\) 按任意顺序取得的有限阶混合偏导数都存在且连续；式 (19) 则明确给出了其中一种顺序的结果。因此式 (17) 可以应用于 \(e^{\lambda x}\)：

$$
\boxed{
\frac{\partial^k}{\partial\lambda^k}
\left(
\frac{\partial^j}{\partial x^j}e^{\lambda x}
\right)
=
\frac{\partial^j}{\partial x^j}
\left(
\frac{\partial^k}{\partial\lambda^k}e^{\lambda x}
\right).
}
\tag{20}
$$

对于复数 \(\lambda\)，函数 \(\lambda\mapsto e^{\lambda x}\) 是整函数，而且式 (18)—(20) 都可以直接按相同的有限求导公式验证。因此这些等式对复数 \(\lambda\) 仍然成立。

---

## 4. 从特征根构造复值解

对任意复数 \(\lambda\)，都有

$$
\frac{d^s}{dx^s}e^{\lambda x}
=\lambda^se^{\lambda x}.
\tag{21}
$$

因此

$$
\begin{aligned}
&a_n\frac{d^n}{dx^n}e^{\lambda x}
+a_{n-1}\frac{d^{n-1}}{dx^{n-1}}e^{\lambda x}
+\cdots
+a_1\frac{d}{dx}e^{\lambda x}
+a_0e^{\lambda x}\\
&=
\left(
a_n\lambda^n+a_{n-1}\lambda^{n-1}
+\cdots+a_1\lambda+a_0
\right)e^{\lambda x}\\
&=P(\lambda)e^{\lambda x}.
\end{aligned}
\tag{22}
$$

重要的是，式 (22) 对任意 \(\lambda\) 都成立。现在才能对它关于参数 \(\lambda\) 求导；不能先把 \(\lambda\) 固定成某个特征根，再把这个固定常数当作变量求导。

对式 (22) 关于 \(\lambda\) 求 \(k\) 阶导数。由于式 (20)，左边变为

$$
\begin{aligned}
&a_n\frac{d^n}{dx^n}\left(x^ke^{\lambda x}\right)
+a_{n-1}\frac{d^{n-1}}{dx^{n-1}}
\left(x^ke^{\lambda x}\right)
+\cdots\\
&\qquad
+a_1\frac{d}{dx}\left(x^ke^{\lambda x}\right)
+a_0x^ke^{\lambda x}.
\end{aligned}
\tag{23}
$$

右边由高阶乘积求导公式变为

$$
\frac{\partial^k}{\partial\lambda^k}
\left(P(\lambda)e^{\lambda x}\right)
=
e^{\lambda x}
\sum_{\ell=0}^{k}
\binom{k}{\ell}
\frac{d^\ell P}{d\lambda^\ell}(\lambda)
x^{k-\ell}.
\tag{24}
$$

设 \(\lambda_0\) 是 \(P\) 的 \(m\) 重根。由重根判据，

$$
P(\lambda_0)=P'(\lambda_0)
=\cdots=
\frac{d^{m-1}P}{d\lambda^{m-1}}(\lambda_0)=0.
\tag{25}
$$

当 \(0\le k<m\) 时，式 (24) 中的每个 \(\ell\) 都满足

$$
0\le\ell\le k<m.
$$

所以令 \(\lambda=\lambda_0\) 后，式 (24) 的每一项都等于零。由式 (23) 得

$$
\begin{aligned}
&a_n\frac{d^n}{dx^n}\left(x^ke^{\lambda_0x}\right)
+a_{n-1}\frac{d^{n-1}}{dx^{n-1}}
\left(x^ke^{\lambda_0x}\right)
+\cdots\\
&\qquad
+a_1\frac{d}{dx}\left(x^ke^{\lambda_0x}\right)
+a_0x^ke^{\lambda_0x}
=0.
\end{aligned}
$$

因此，一个 \(m\) 重特征根 \(\lambda_0\) 产生 \(m\) 个复值解

$$
\boxed{
e^{\lambda_0x},\;
xe^{\lambda_0x},\;
\ldots,\;
x^{m-1}e^{\lambda_0x}.
}
\tag{26}
$$

---

## 5. 把复根对应的解化为实值解

### 5.1 实根

如果 \(r_i\) 是 \(m_i\) 重实根，由式 (26) 得到

$$
e^{r_ix},\;
xe^{r_ix},\;
\ldots,\;
x^{m_i-1}e^{r_ix}.
\tag{27}
$$

它们的任意实线性组合为

$$
e^{r_ix}
\left(
C_{i0}+C_{i1}x+\cdots+C_{i,m_i-1}x^{m_i-1}
\right).
\tag{28}
$$

### 5.2 共轭复根

因为 \(P\) 的系数都是实数，

$$
P(\overline{\lambda})=\overline{P(\lambda)}.
$$

相同关系对 \(P\) 的各阶导数也成立，所以非实根必成共轭对出现，并且一对共轭根的重数相同。

设

$$
\lambda=\alpha+i\beta,
\qquad \beta>0,
$$

是一个 \(q\) 重根。由式 (26)，对于 \(0\le k<q\)，

$$
x^ke^{(\alpha+i\beta)x}
$$

是复值解。由欧拉公式，

$$
\begin{aligned}
x^ke^{(\alpha+i\beta)x}
&=
x^ke^{\alpha x}
\left(\cos(\beta x)+i\sin(\beta x)\right)\\
&=
x^ke^{\alpha x}\cos(\beta x)
+i\,x^ke^{\alpha x}\sin(\beta x).
\end{aligned}
\tag{29}
$$

如果 \(z=u+iv\) 满足方程 (1)，因为方程的所有系数都是实数，将 \(z=u+iv\) 代入并分别比较实部、虚部可得：\(u\) 和 \(v\) 都满足方程 (1)。

因此一对 \(q\) 重共轭根 \(\alpha\pm i\beta\) 产生 \(2q\) 个实值解

$$
\boxed{
x^ke^{\alpha x}\cos(\beta x),\qquad
x^ke^{\alpha x}\sin(\beta x),
\qquad 0\le k<q.
}
\tag{30}
$$

它们的任意实线性组合为

$$
e^{\alpha x}
\sum_{k=0}^{q-1}x^k
\left(
A_k\cos(\beta x)+B_k\sin(\beta x)
\right).
\tag{31}
$$

到这里，每一个基本函数都已经被证明满足方程。方程左边关于 \(y,y',\ldots,y^{(n)}\) 是线性的，所以这些基本解的任意有限实线性组合仍然满足方程。因此式 (4) 中任意选择常数所得到的函数都满足方程。下面证明这些解线性无关。

---

## 6. 所构造的 \(n\) 个解线性无关
![alt text](image-8.png)
先在复数范围内证明。

如果所讨论的定义区间 \(I\) 不包含 \(0\)，固定任意 \(x_0\in I\)，并令

$$
t=x-x_0.
$$

对于每个根 \(\lambda\) 和每个非负整数 \(k\)，有

$$
\begin{aligned}
x^ke^{\lambda x}
&=(t+x_0)^ke^{\lambda(t+x_0)}\\
&=
e^{\lambda x_0}
\sum_{h=0}^{k}
\binom{k}{h}x_0^{k-h}t^he^{\lambda t}.
\end{aligned}
$$

对于固定的 \(\lambda\)，这是从函数

$$
e^{\lambda t},\;te^{\lambda t},\ldots,t^ke^{\lambda t}
$$

到原来函数的三角形线性变换，其对角系数均为 \(e^{\lambda x_0}\ne0\)，所以该变换可逆。因此，只需证明以 \(t=0\) 为初值点的函数组线性无关。为简化记号，下面仍把变量 \(t\) 写成 \(x\)。

设特征多项式的所有互不相同的复根为

$$
\lambda_1,\ldots,\lambda_s,
$$

重数依次为

$$
\mu_1,\ldots,\mu_s.
$$

由代数基本定理，

$$
\sum_{\nu=1}^{s}\mu_\nu=n.
\tag{32}
$$

考虑以下 \(n\) 个复值函数：

$$
f_{\nu,k}(x)=x^ke^{\lambda_\nu x},
\qquad
1\le\nu\le s,\quad 0\le k<\mu_\nu.
\tag{33}
$$

构造一个 \(n\times n\) 矩阵：它的列用二元指标 \((\nu,k)\) 标记，第 \(\ell\) 行对应在 \(x=0\) 处的 \(\ell\) 阶导数，其中

$$
\ell=0,1,\ldots,n-1.
$$

由高阶乘积求导公式，

$$
f_{\nu,k}^{(\ell)}(0)
=
\begin{cases}
0,&\ell<k,\\[2mm]
\dfrac{\ell!}{(\ell-k)!}\lambda_\nu^{\ell-k},
&\ell\ge k.
\end{cases}
\tag{34}
$$

假设这个矩阵不可逆，则其转置矩阵存在一个非零零空间向量。也就是说，存在不全为零的复数

$$
c_0,c_1,\ldots,c_{n-1},
$$

使得对于每个 \(\nu\) 和每个 \(0\le k<\mu_\nu\)，都有

$$
\sum_{\ell=k}^{n-1}
c_\ell
\frac{\ell!}{(\ell-k)!}
\lambda_\nu^{\ell-k}
=0.
\tag{35}
$$

定义多项式

$$
H(z)=c_0+c_1z+\cdots+c_{n-1}z^{n-1}.
\tag{36}
$$

直接求导可得

$$
\frac{d^kH}{dz^k}(\lambda_\nu)
=
\sum_{\ell=k}^{n-1}
c_\ell
\frac{\ell!}{(\ell-k)!}
\lambda_\nu^{\ell-k}.
\tag{37}
$$

由式 (35)，

$$
H(\lambda_\nu)=H'(\lambda_\nu)
=\cdots=
\frac{d^{\mu_\nu-1}H}{dz^{\mu_\nu-1}}(\lambda_\nu)
=0.
\tag{38}
$$

由第 2 节的重根判据，\(\lambda_\nu\) 至少是 \(H\) 的 \(\mu_\nu\) 重根。因此

$$
\prod_{\nu=1}^{s}(z-\lambda_\nu)^{\mu_\nu}
$$

整除 \(H(z)\)。但这个乘积的次数为

$$
\sum_{\nu=1}^{s}\mu_\nu=n,
$$

而由式 (36)，

$$
\deg H\le n-1.
$$

所以只能有 \(H\equiv0\)，从而

$$
c_0=c_1=\cdots=c_{n-1}=0,
$$

这与所选向量非零矛盾。因此上述初值矩阵可逆。

更明确地说，若式 (33) 中的函数存在一个线性关系，则把该关系依次求 \(0,1,\ldots,n-1\) 阶导数并令 \(x=0\)，便得到“初值矩阵乘以系数向量等于零”。因为初值矩阵可逆，系数向量只能是零向量。因此式 (33) 中的 \(n\) 个复值函数线性无关。

对于一对共轭根 \(\alpha\pm i\beta\)，记

$$
z_k=x^ke^{(\alpha+i\beta)x},
\qquad
\overline{z_k}=x^ke^{(\alpha-i\beta)x}.
$$

将这一对函数替换为

$$
\frac{z_k+\overline{z_k}}{2}
=x^ke^{\alpha x}\cos(\beta x)
$$

和

$$
\frac{z_k-\overline{z_k}}{2i}
=x^ke^{\alpha x}\sin(\beta x).
$$

这个替换是可逆的，因为

$$
z_k
=x^ke^{\alpha x}\cos(\beta x)
+i\,x^ke^{\alpha x}\sin(\beta x),
$$

$$
\overline{z_k}
=x^ke^{\alpha x}\cos(\beta x)
-i\,x^ke^{\alpha x}\sin(\beta x).
$$

可逆的线性替换不会破坏线性无关性。因此式 (27) 与式 (30) 给出的全部实值函数线性无关。

---

## 7. 为什么这些解已经是全部解

设 \(I\) 是一个开区间，记方程 (1) 在 \(I\) 上的全部实值解组成的向量空间为 \(S\)。固定 \(x_0\in I\)，定义线性映射

$$
\begin{aligned}
\Phi:S&\longrightarrow\mathbb R^n,\\
y&\longmapsto
\left(
y(x_0),y'(x_0),\ldots,y^{(n-1)}(x_0)
\right).
\end{aligned}
\tag{39}
$$

由 \(n\) 阶线性微分方程初值问题的存在唯一性：

1. 对任意给定的 \(n\) 个初值，都存在一个解，所以 \(\Phi\) 是满射；
2. 两个解具有相同初值时必定相同，特别地，初值全部为零的解只能是零解，所以 \(\Phi\) 是单射。

因此 \(\Phi\) 是线性同构，从而

$$
\boxed{\dim S=n.}
\tag{40}
$$

第 5 节已经构造出

$$
\sum_{i=1}^{p}m_i+2\sum_{j=1}^{t}q_j=n
$$

个实值解；第 6 节已经证明它们线性无关。因此这 \(n\) 个解构成 \(S\) 的一组基。

所以每个实值解都能够唯一写成这些函数的实线性组合，也就是

$$
\boxed{
\begin{aligned}
y(x)
={}&
\sum_{i=1}^{p}e^{r_ix}
\left(
C_{i0}+C_{i1}x+\cdots+C_{i,m_i-1}x^{m_i-1}
\right)
\\
&+
\sum_{j=1}^{t}e^{\alpha_jx}
\sum_{k=0}^{q_j-1}x^k
\left(
A_{jk}\cos(\beta_jx)+B_{jk}\sin(\beta_jx)
\right).
\end{aligned}}
$$

这正是所要证明的通解公式。

---

## 8. 证明的逻辑链条

整个证明可以概括为

$$
\begin{aligned}
&\text{多项式重根判据}
\\
&\Longrightarrow
\text{参数求导与 }x\text{ 求导可以换序}
\\
&\Longrightarrow
m\text{ 重根 }\lambda
\text{ 产生 }
e^{\lambda x},xe^{\lambda x},\ldots,x^{m-1}e^{\lambda x}
\\
&\Longrightarrow
\text{共轭复根给出相应的正弦、余弦实值解}
\\
&\Longrightarrow
\text{得到 }n\text{ 个线性无关的实值解}
\\
&\Longrightarrow
\dim S=n
\\
&\Longrightarrow
\text{这些解构成全部解的一组基。}
\end{aligned}
$$

需要特别注意：

1. 只证明式 (4) 中的函数满足方程，还不足以称其为通解；
2. 必须再证明这些函数线性无关，并证明解空间的维数为 \(n\)；
3. 参数求导时，必须先保留任意参数 \(\lambda\)，求导完成后才能令 \(\lambda\) 等于某个特征根；
4. 式 (4) 是常系数方程的结论，不能直接推广到任意变系数方程。

---
---
另外一个通解证明方法，就是用到了连续求和：
![alt text](image-11.png)