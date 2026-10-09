# 连续时间、无限时域、多输入 LQR 的最优性证明

本文用配方法证明最优反馈矩阵

$$
K_*=R^{-1}B^TP_*
$$

的来源，并直接比较不同候选矩阵 $P$ 对应的总代价。推导只使用乘积求导、矩阵乘法、积分和二次型，不要求掌握矩阵求导。

需要区分两个问题：

1. 对所有允许的输入函数 $u(t)$，证明 $u_*=-K_*x_*$ 达到全局最小代价。这是主体证明。
2. 对反馈族 $u_P=-R^{-1}B^TPx_P$，直接证明任何其他可行 $P$ 的代价都不低于 $P_*$。这是补充证明，用来回答“改变 $P$ 会不会更好”。

第二个问题只比较一个反馈族；第一个问题才覆盖所有允许的输入。

## 1. 问题、符号与适用条件

### 1.1 状态方程与代价函数

考虑线性定常系统：

$$
\dot x(t)=Ax(t)+Bu(t),\qquad x(0)=x_0.
\tag{1}
$$

代价函数为：

$$
J[u]=\frac12\int_0^\infty
\left[x(t)^TQx(t)+u(t)^TRu(t)\right]dt.
\tag{2}
$$

给定的是 $A、B、Q、R、x_0$，优化变量是整段输入函数 $u(t)$。输入改变时，满足式（1）的状态轨迹也会改变。

“无限时域”表示积分覆盖整个未来，不表示控制器等到无限远才开始纠正状态。

| 符号 | 维数 | 含义 |
|---|---|---|
| $x(t)$ | $n\times1$ | 状态列向量 |
| $u(t)$ | $m\times1$ | 输入列向量 |
| $A$ | $n\times n$ | 状态矩阵 |
| $B$ | $n\times m$ | 输入矩阵 |
| $Q$ | $n\times n$ | 状态代价权重 |
| $R$ | $m\times m$ | 输入代价权重 |
| $P$ | $n\times n$ | 证明中引入的常量对称矩阵 |
| $K$ | $m\times n$ | 状态反馈矩阵 |

多路输入统一排列为列向量。列向量也是矩阵，但 $u^TRu$ 是一个标量，因此可以作为总代价的被积项。

本文中的 $F(P)$ 表示一个矩阵表达式，不是反馈增益；反馈增益统一记为 $K$。

### 1.2 本文主体证明的条件

- $A、B、Q、R$ 不随时间变化。
- $Q=Q^T>0$，即任意非零 $x$ 都满足 $x^TQx>0$。
- $R=R^T>0$，即任意非零 $u$ 都满足 $u^TRu>0$。
- $(A,B)$ 可稳定：存在矩阵 $L$，使 $A-BL$ 的全部特征值实部小于零。
- 不对输入幅值、变化率等另外施加约束。

输入可取分段连续或局部平方可积的函数，使状态方程具有唯一的绝对连续解。若只允许连续输入，以下下界仍对每个连续候选成立，最终得到的最优反馈输入也连续。

下面使用一条标准的 Riccati 存在性定理：在上述条件下，连续时间代数 Riccati 方程存在唯一的对称正定稳定解。本文完整证明这个解为什么给出全局最优控制，但不另行证明该存在性定理。不能把“配方写得出来”本身当成稳定解一定存在的证明。

## 2. 引入辅助函数，不提前假定它就是最优代价

取一个暂时未知的常量对称矩阵：

$$
P=P^T,
$$

定义：

$$
W_P(x)=\frac12x^TPx.
\tag{3}
$$

目前，$W_P$ 只是用于整理等式的辅助函数。此时没有认定它等于最优代价，也没有认定任意 $P$ 都能给出代价下界。

我们希望找到一个合适的 $P$，把总代价写成：

$$
\text{只取决于初始状态的固定值}
+
\text{非负项}.
$$

如果存在一种允许的控制能让非负项为零，它就达到了所有候选控制共同的下界。

## 3. 计算辅助函数沿轨迹的导数

因为 $P$ 是常量，根据普通的乘积求导法则：

$$
\frac{dW_P}{dt}
=\frac12\left(\dot x^TPx+x^TP\dot x\right).
\tag{4}
$$

两项都是标量。利用 $P=P^T$：

$$
\dot x^TPx
=(\dot x^TPx)^T
=x^TP\dot x.
$$

因此：

$$
\frac{dW_P}{dt}=x^TP\dot x.
$$

代入 $\dot x=Ax+Bu$：

$$
\frac{dW_P}{dt}=x^TPAx+x^TPBu.
$$

由于标量等于其转置：

$$
x^TPAx=\frac12x^T(PA+A^TP)x,
$$

$$
x^TPBu=u^TB^TPx.
$$

得到：

$$
\boxed{
\frac{dW_P}{dt}
=\frac12x^T(A^TP+PA)x+u^TB^TPx.
}
\tag{5}
$$

到这里没有使用矩阵求导公式，只有乘积求导和转置规则。

## 4. 对输入进行矩阵配方

记瞬时代价为：

$$
\ell(x,u)=\frac12x^TQx+\frac12u^TRu.
$$

将它与式（5）相加：

$$
\ell+\dot W_P
=\frac12x^T(Q+A^TP+PA)x
+\frac12u^TRu+u^TB^TPx.
\tag{6}
$$

暂记：

$$
z=B^TPx\in\mathbb R^{m\times1}.
$$

需要配方的是：

$$
\frac12u^TRu+u^Tz.
$$

因为 $R$ 对称正定，$R^{-1}$ 存在且对称。直接展开：

$$
\begin{aligned}
&(u+R^{-1}z)^TR(u+R^{-1}z)\\
&=u^TRu+u^Tz+z^Tu+z^TR^{-1}z\\
&=u^TRu+2u^Tz+z^TR^{-1}z.
\end{aligned}
$$

其中 $u^Tz=z^Tu$，因为它们是同一个标量。于是：

$$
\frac12u^TRu+u^Tz
=\frac12(u+R^{-1}z)^TR(u+R^{-1}z)
-\frac12z^TR^{-1}z.
\tag{7}
$$

代回 $z=B^TPx$，并利用：

$$
z^TR^{-1}z=x^TPBR^{-1}B^TPx,
$$

可得：

$$
\boxed{
\begin{aligned}
\ell+\dot W_P
={}&\frac12
(u+R^{-1}B^TPx)^TR(u+R^{-1}B^TPx)\\
&+\frac12x^TF(P)x,
\end{aligned}
}
\tag{8}
$$

其中定义：

$$
\boxed{
F(P)=A^TP+PA+Q-PBR^{-1}B^TP.
}
\tag{9}
$$

式（8）对任意常量对称矩阵 $P$、任意允许的输入及其状态轨迹成立。此时没有把输入限制为线性反馈。

## 5. 为什么不能直接认定余项非负

一般情况下，$F(P)$ 不保证正定或半正定，即使 $P>0$ 也不保证。

例如取：

$$
A=0,\qquad B=I,\qquad Q=R=I,
$$

则：

$$
F(P)=I-P^2.
$$

选：

$$
P=
\begin{bmatrix}
1/2&0\\
0&2
\end{bmatrix}>0,
$$

得到：

$$
F(P)=
\begin{bmatrix}
3/4&0\\
0&-3
\end{bmatrix}.
$$

它是不定矩阵。因此，对任意 $P$，不能忽略式（8）的最后一项并声称已经得到代价下界。

这份证明接下来做的是：选择一个使余项对所有状态都为零的固定矩阵，而不是假定余项原本就非负。

## 6. 选择 Riccati 稳定解

要求：

$$
\boxed{
A^TP_*+P_*A-P_*BR^{-1}B^TP_*+Q=0.
}
\tag{10}
$$

这就是连续时间代数 Riccati 方程。式（10）表示：

$$
F(P_*)=0.
$$

取它的对称稳定解，并定义候选反馈矩阵：

$$
\boxed{
K_*=R^{-1}B^TP_*.
}
\tag{11}
$$

“稳定解”表示：

$$
A-BK_*
$$

的全部特征值实部小于零。不能只找出任意一个代数根就直接使用。

把这个 $P_*$ 固定下来，式（8）变成：

$$
\boxed{
\ell+\dot W_{P_*}
=\frac12(u+K_*x)^TR(u+K_*x).
}
\tag{12}
$$

注意这里仍然保留任意输入 $u$，还没有令 $u=-K_*x$。由于 $F(P_*)$ 是零矩阵，余项对于任何输入产生的任何状态轨迹都为零。

## 7. 先在有限时间上积分

定义：

$$
J_T[u]=\frac12\int_0^T(x^TQx+u^TRu)\,dt.
$$

对式（12）从 $0$ 积分到 $T$：

$$
J_T[u]+W_{P_*}(x(T))-W_{P_*}(x_0)
=\frac12\int_0^T(u+K_*x)^TR(u+K_*x)\,dt.
$$

整理：

$$
\boxed{
\begin{aligned}
J_T[u]
={}&\frac12x_0^TP_*x_0-\frac12x(T)^TP_*x(T)\\
&+\frac12\int_0^T(u+K_*x)^TR(u+K_*x)\,dt.
\end{aligned}
}
\tag{13}
$$

末端项还没有被省略。必须说明为什么在所比较的控制下，它确实趋于零。

## 8. 为什么有限代价保证末端项趋于零

先构造候选控制 $u_*=-K_*x_*$。由于 $A-BK_*$ 稳定，$x_*$ 和 $u_*$ 指数衰减，因此其总代价有限。

所以，总代价无穷大的控制不可能更好。以下只需比较 $J[u]<\infty$ 的候选输入。

因为 $Q>0$、$R>0$，存在正数 $q_{\min}$、$r_{\min}$，使：

$$
x^TQx\ge q_{\min}\|x\|^2,\qquad
u^TRu\ge r_{\min}\|u\|^2.
$$

因此有限代价意味着：

$$
\int_0^\infty\|x(t)\|^2dt<\infty,\qquad
\int_0^\infty\|u(t)\|^2dt<\infty.
\tag{14}
$$

由 $\dot x=Ax+Bu$：

$$
\|\dot x\|^2
\le 2\|A\|^2\|x\|^2+2\|B\|^2\|u\|^2,
$$

所以：

$$
\int_0^\infty\|\dot x(t)\|^2dt<\infty.
\tag{15}
$$

这里 $\|x\|^2=x_1^2+\cdots+x_n^2$。令：

$$
g(t)=\|x(t)\|^2.
$$

其导数为：

$$
g'(t)=2x(t)^T\dot x(t).
$$

对绝对连续的轨迹，上式在几乎处处成立，足以用于下列积分。由柯西–施瓦茨不等式：

$$
\begin{aligned}
\int_0^\infty |g'(t)|dt
&\le 2\int_0^\infty\|x(t)\|\,\|\dot x(t)\|dt\\
&\le
2\sqrt{\int_0^\infty\|x(t)\|^2dt}
\sqrt{\int_0^\infty\|\dot x(t)\|^2dt}\\
&<\infty.
\end{aligned}
$$

于是 $g(t)$ 有有限极限。又因为 $g(t)\ge0$ 且其积分有限，这个极限只能是零；如果极限为某个正数，后续时间上的积分就会发散。

因此：

$$
x(t)\longrightarrow0.
$$

对于任何固定的有限矩阵 $P$，特别是 $P_*$：

$$
\boxed{
\frac12x(T)^TPx(T)\longrightarrow0.
}
\tag{16}
$$

这一步说明末端项消失的条件，不是无条件地把它删除。

## 9. 对所有输入建立共同下界，并证明可达到

在式（13）中令 $T\to\infty$，得到：

$$
\boxed{
J[u]
=\frac12x_0^TP_*x_0
+\frac12\int_0^\infty(u+K_*x)^TR(u+K_*x)\,dt.
}
\tag{17}
$$

因为 $R>0$，积分项非负，所以：

$$
\boxed{
\forall u\text{，若 }J[u]<\infty,\qquad
J[u]\ge\frac12x_0^TP_*x_0.
}
\tag{18}
$$

对候选控制：

$$
u_*=-K_*x_*,
$$

有 $u_*+K_*x_*=0$，故：

$$
\boxed{
J[u_*]=\frac12x_0^TP_*x_0.
}
\tag{19}
$$

式（18）与式（19）共同说明：

$$
\boxed{
\forall u,\qquad J[u]\ge J[u_*].
}
\tag{20}
$$

有限代价的输入由式（18）覆盖，无穷大代价的输入也不可能更好。因此，这是对所有允许输入的全局最优性证明。

最终得到：

$$
\boxed{
u_*(t)=-K_*x_*(t),\qquad K_*=R^{-1}B^TP_*,
}
$$

以及最优代价函数：

$$
\boxed{
V(x_0)=\min_{u(\cdot)}J[u]=\frac12x_0^TP_*x_0.
}
\tag{21}
$$

辅助函数等于最优代价，是证明的结果，而不是开始时已经认定的前提。

## 10. 为什么固定辅助矩阵不意味着只得到“固定 P 下最优”

原始问题优化的是 $u(t)$。矩阵 $P$ 没有出现在原始状态方程或原始代价定义中。

固定 $P_*$ 后，式（17）仍然适用于任意输入 $v(t)$。把它产生的轨迹明确记为 $x_v(t)$：

$$
\boxed{
J[v]-J[u_*]
=\frac12\int_0^\infty
(v+K_*x_v)^TR(v+K_*x_v)\,dt
\ge0.
}
\tag{22}
$$

这个输入可以来自另一套线性反馈、非线性反馈、时变控制或其他允许的控制方式。不同控制产生不同轨迹，但二次型对任何轨迹都非负。

所以，固定 $P_*$ 固定的是一个对所有控制都有效的下界，没有缩小可选输入的范围。

如果另一套反馈为 $v=-K'x_v$，则式（22）进一步变成：

$$
J[v]-J[u_*]
=\frac12\int_0^\infty
x_v^T(K_*-K')^TR(K_*-K')x_v\,dt
\ge0.
\tag{23}
$$

不能通过更换另一套反馈而突破这个下界。

## 11. 补充证明：直接比较不同 P 对应的总代价

这一节专门回答：如果把 $P$ 当作反馈参数，改变它后，会不会利用 $F(P)$ 中的负项得到更低的总代价？

### 11.1 无平方项的表达式在什么条件下成立

对于任意常量对称 $P$，式（8）积分后，在有限代价条件下给出：

$$
\begin{aligned}
J[u]
={}&\frac12x_0^TPx_0\\
&+\frac12\int_0^\infty
(u+R^{-1}B^TPx)^TR(u+R^{-1}B^TPx)\,dt\\
&+\frac12\int_0^\infty x^TF(P)x\,dt.
\end{aligned}
\tag{24}
$$

只有当选择：

$$
\boxed{
u_P=-R^{-1}B^TPx_P
}
\tag{25}
$$

时，中间的平方项才为零。这时才能写：

$$
\boxed{
J(P)
=\frac12x_0^TPx_0
+\frac12\int_0^\infty x_P^TF(P)x_P\,dt.
}
\tag{26}
$$

这里的 $J(P)$ 是简写，实际表示原始代价 $J[u_P]$。改变 $P$，控制律与轨迹 $x_P$ 都会改变。

式（26）不能用于输入仍然任意的情况。

### 11.2 状态方程中的 A-GP 是怎么来的

定义：

$$
G=BR^{-1}B^T.
\tag{27}
$$

将式（25）的控制律代入原状态方程：

$$
\begin{aligned}
\dot x_P
&=Ax_P+Bu_P\\
&=Ax_P+B(-R^{-1}B^TPx_P)\\
&=(A-BR^{-1}B^TP)x_P\\
&=(A-GP)x_P.
\end{aligned}
$$

因此：

$$
\boxed{
\dot x_P=(A-GP)x_P.
}
\tag{28}
$$

下标 $P$ 只是标记，表示采用该候选反馈后的状态轨迹；不是 $x$ 乘 $P$，也不是对 $P$ 求导。

式（28）依赖于选用式（25）的反馈律。对于任意未指定的输入，状态方程仍然是 $\dot x=Ax+Bu$。

### 11.3 比较任意候选 P 与稳定解 P*

固定 Riccati 稳定解 $P_*$。再取任意对称候选 $P$，只要求它在当前初始状态下产生有限总代价。所有稳定的候选反馈都包含在内。

记：

$$
\Delta=P-P_*,
\qquad
A_P=A-GP.
\tag{29}
$$

因为 $F(P_*)=0$：

$$
J(P_*)=\frac12x_0^TP_*x_0.
$$

由式（26）：

$$
\boxed{
J(P)-J(P_*)
=\frac12x_0^T\Delta x_0
+\frac12\int_0^\infty x_P^TF(P)x_P\,dt.
}
\tag{30}
$$

不能只看式（30）某一项的正负。接下来将两项一起整理。

### 11.4 展开关键恒等式

由于：

$$
F(P)=A^TP+PA+Q-PGP,
$$

而：

$$
F(P_*)=A^TP_*+P_*A+Q-P_*GP_*=0,
$$

两式相减：

$$
\begin{aligned}
F(P)
&=A^T\Delta+\Delta A-PGP+P_*GP_*\\
&=A^T\Delta+\Delta A
-P_*G\Delta-\Delta GP_*-\Delta G\Delta.
\end{aligned}
\tag{31}
$$

另一方面，因为 $G=G^T$、$P=P^T$：

$$
\begin{aligned}
A_P^T\Delta+\Delta A_P+\Delta G\Delta
&=(A-GP)^T\Delta+\Delta(A-GP)+\Delta G\Delta\\
&=A^T\Delta+\Delta A
-PG\Delta-\Delta GP+\Delta G\Delta\\
&=A^T\Delta+\Delta A
-P_*G\Delta-\Delta GP_*-\Delta G\Delta.
\end{aligned}
$$

因此：

$$
\boxed{
F(P)=A_P^T\Delta+\Delta A_P+\Delta G\Delta.
}
\tag{32}
$$

### 11.5 用状态方程处理积分

沿着候选轨迹 $\dot x_P=A_Px_P$：

$$
\begin{aligned}
\frac{d}{dt}(x_P^T\Delta x_P)
&=\dot x_P^T\Delta x_P+x_P^T\Delta\dot x_P\\
&=x_P^T(A_P^T\Delta+\Delta A_P)x_P.
\end{aligned}
$$

利用式（32）：

$$
\boxed{
x_P^TF(P)x_P
=\frac{d}{dt}(x_P^T\Delta x_P)
+x_P^T\Delta G\Delta x_P.
}
\tag{33}
$$

候选控制代价有限，所以由第 8 节，$x_P(t)\to0$。积分式（33）：

$$
\begin{aligned}
\int_0^\infty x_P^TF(P)x_P\,dt
&=\left[x_P^T\Delta x_P\right]_0^\infty
+\int_0^\infty x_P^T\Delta G\Delta x_P\,dt\\
&=-x_0^T\Delta x_0
+\int_0^\infty x_P^T\Delta G\Delta x_P\,dt.
\end{aligned}
$$

代入式（30），初始项抵消：

$$
\boxed{
J(P)-J(P_*)
=\frac12\int_0^\infty x_P^T\Delta G\Delta x_P\,dt.
}
\tag{34}
$$

由于 $G=BR^{-1}B^T$、$\Delta=\Delta^T$：

$$
\boxed{
J(P)-J(P_*)
=\frac12\int_0^\infty
(B^T\Delta x_P)^TR^{-1}(B^T\Delta x_P)\,dt
\ge0.
}
\tag{35}
$$

式（35）对任意上述可行候选 $P$ 成立，没有要求它满足 Riccati 方程，也没有要求 $F(P)$ 非负。

所以，虽然其他 $P$ 的余项可能为负，把初始项、轨迹变化和积分项一起比较后，总代价仍然不会低于 $P_*$。

这证明 $P_*$ 在该反馈参数族中达到全局最小值；对所有允许输入的全局最优性则已经由第 9 节证明。

对于某个固定的初始状态，代价相同不一定意味着候选矩阵 $P$ 完全相同；式（35）不需要主张所有反馈参数都具有唯一性。

## 12. 一个可以直接手算的例子

取：

$$
\dot x=u,\qquad x(0)=1,
$$

$$
J=\frac12\int_0^\infty(x^2+u^2)\,dt.
$$

此时 $A=0、B=1、Q=R=1$，用标量 $p$ 表示矩阵 $P$：

$$
F(p)=1-p^2.
$$

Riccati 方程给出 $p=\pm1$。反馈为 $u=-px$，闭环为 $\dot x=-px$，因此稳定解是：

$$
p_*=1,\qquad u_*=-x,\qquad J_*=\frac12.
$$

对任意稳定候选 $p>0$：

$$
x_p(t)=e^{-pt},\qquad u_p(t)=-pe^{-pt}.
$$

直接从原始代价计算：

$$
\begin{aligned}
J(p)
&=\frac12\int_0^\infty(1+p^2)e^{-2pt}\,dt\\
&=\frac{1+p^2}{4p}\\
&=\frac12+\frac{(p-1)^2}{4p}.
\end{aligned}
$$

所以：

$$
J(p)-J(1)=\frac{(p-1)^2}{4p}\ge0.
$$

例如 $p=2$ 时，$F(2)=-3$ 确实为负。但：

$$
J(2)
=1-\frac32\int_0^\infty e^{-4t}dt
=1-\frac38
=\frac58
>\frac12.
$$

“余项出现负数”不等于“总代价比最优值更低”；初始项和轨迹也随 $p$ 一起改变。

## 13. 实际求解顺序与边界

实际使用时：

1. 建立状态方程，确定 $A、B$。
2. 选择权重矩阵 $Q、R$。
3. 求解连续时间代数 Riccati 方程，选择稳定解 $P_*$。
4. 计算 $K_*=R^{-1}B^TP_*$。
5. 运行时根据当前状态计算 $u_*=-K_*x$。

这里的全局最优针对给定的线性模型、给定的代价与无输入约束问题。如果加入输入饱和、变化率约束或改变动力学模型，不能直接声称同一控制律仍是新问题的全局最优。

对于由非线性轮足模型在直立附近线性化得到的 $A、B$，数学上的全局最优属于这个线性模型；它不会自动扩大原机械模型线性近似的适用范围。

### Q 允许半正定时

常见的更一般版本允许 $Q\ge0$。此时通常要求 $(A,B)$ 可稳定，并要求 $(Q^{1/2},A)$ 可检测：以 $Q^{1/2}x$ 作为观测量时，所有不可观测模态都必须稳定。

配方、Riccati 方程与代价差公式保持不变，但第 8 节不能直接通过 $Q>0$ 推出整个状态平方可积；需要使用可检测性处理末端条件。本文完整展开的是 $Q>0$ 的证明，不把半正定情形的末端论证省略后当作已证明。

## 附录 A. 无穷积分的柯西收敛准则及其应用

本附录补充第 8 节使用的收敛论证。这里证明的是“反常积分的柯西收敛准则”，它与用于估计积分大小的“柯西–施瓦茨不等式”是两个不同结果。

### A.1 准则的准确表述

设实值函数 $f(t)$ 在每个有限区间 $[a,T]$ 上可积。记截断积分：

$$
S(T)=\int_a^T f(t)\,dt.
$$

反常积分收敛的定义是：存在有限实数 $I$，使：

$$
\lim_{T\to\infty}S(T)=I.
$$

此时记：

$$
\int_a^\infty f(t)\,dt=I.
$$

无穷积分的柯西收敛准则为：

$$
\boxed{
\int_a^\infty f(t)\,dt\text{ 收敛}
\iff
\forall\varepsilon>0,\ \exists T_\varepsilon\ge a,\
\forall t_2\ge t_1\ge T_\varepsilon,\
\left|\int_{t_1}^{t_2}f(t)\,dt\right|<\varepsilon.
}
\tag{A1}
$$

它表示：只要积分区间的两个端点都足够靠后，无论这段区间有多长，积分的绝对值都能够小于指定的 $\varepsilon$。

不能只检查某一个固定长度的区间。准则要求对所有足够靠后的端点组合成立。

下面分别证明必要性和充分性。

### A.2 必要性：收敛必然满足尾段积分条件

假设：

$$
S(T)\longrightarrow I.
$$

给定任意 $\varepsilon>0$。由极限定义，存在 $T_\varepsilon$，使所有 $T\ge T_\varepsilon$ 都满足：

$$
|S(T)-I|<\frac{\varepsilon}{2}.
$$

对于任意 $t_2\ge t_1\ge T_\varepsilon$，根据定积分的可加性：

$$
\int_{t_1}^{t_2}f(t)\,dt=S(t_2)-S(t_1).
$$

由三角不等式：

$$
\begin{aligned}
\left|\int_{t_1}^{t_2}f(t)\,dt\right|
&=|S(t_2)-S(t_1)|\\
&=|(S(t_2)-I)-(S(t_1)-I)|\\
&\le |S(t_2)-I|+|S(t_1)-I|\\
&<\frac{\varepsilon}{2}+\frac{\varepsilon}{2}\\
&=\varepsilon.
\end{aligned}
$$

必要性得证。

### A.3 充分性：尾段积分条件保证存在有限极限

现在假设式（A1）右侧的条件成立。需要证明存在一个有限实数 $I$，使所有实数上限 $T\to\infty$ 时，$S(T)\to I$。

这个方向分成两步：先得到一个候选极限，再证明所有截断上限都趋向它。

**第一步：构造收敛的截断积分数列。**

取：

$$
t_n=a+n,\qquad s_n=S(t_n)=\int_a^{a+n}f(t)\,dt.
$$

给定任意 $\varepsilon>0$，由假设选出 $T_\varepsilon$。再选择足够大的整数 $N$，使 $a+N\ge T_\varepsilon$。

对于任意整数 $n\ge m\ge N$：

$$
\begin{aligned}
|s_n-s_m|
&=\left|\int_{a+m}^{a+n}f(t)\,dt\right|\\
&<\varepsilon.
\end{aligned}
$$

若 $m>n$，交换两者即可得到相同结论。因此 $(s_n)$ 是一个实数柯西数列。

由实数的完备性，实数柯西数列必收敛，所以存在有限实数 $I$，使：

$$
s_n\longrightarrow I.
$$

这里明确使用了实数完备性；从“数列是柯西列”到“存在实数极限”由这条基础性质保证。

**第二步：把数列上的收敛推广到任意实数上限。**

仅有 $S(a+n)\to I$ 还不足以完成证明，因为反常积分要求所有足够大的实数上限 $T$ 都趋于同一个极限。

给定任意 $\varepsilon>0$。

由尾段积分条件，存在 $T_0$，使：

$$
t_2\ge t_1\ge T_0
\quad\Longrightarrow\quad
\left|\int_{t_1}^{t_2}f(t)\,dt\right|
<\frac{\varepsilon}{2}.
$$

又因为 $s_n\to I$，存在整数 $N_1$，使：

$$
n\ge N_1
\quad\Longrightarrow\quad
|s_n-I|<\frac{\varepsilon}{2}.
$$

现在任取一个实数 $T\ge T_0$。选择足够大的整数 $n$，使：

$$
n\ge N_1,\qquad a+n\ge T.
$$

此时 $a+n$ 与 $T$ 都不小于 $T_0$，所以：

$$
|S(T)-s_n|
=\left|\int_T^{a+n}f(t)\,dt\right|
<\frac{\varepsilon}{2}.
$$

再由三角不等式：

$$
\begin{aligned}
|S(T)-I|
&\le |S(T)-s_n|+|s_n-I|\\
&<\frac{\varepsilon}{2}+\frac{\varepsilon}{2}\\
&=\varepsilon.
\end{aligned}
$$

这个结论对所有 $T\ge T_0$ 都成立。因此：

$$
\boxed{
\lim_{T\to\infty}S(T)=I.
}
$$

充分性得证，式（A1）的充要性证明完成。

### A.4 与绝对收敛的关系

一般准则要求的是：

$$
\left|\int_{t_1}^{t_2}f(t)\,dt\right|<\varepsilon.
$$

它不要求：

$$
\int_{t_1}^{t_2}|f(t)|\,dt<\varepsilon.
$$

后者是更强的条件，不能把两者混为一谈。

不过，如果已经知道：

$$
\int_a^\infty |f(t)|\,dt<\infty,
$$

就可以把必要性应用于非负函数 $|f|$，得到足够靠后的区间满足：

$$
\int_{t_1}^{t_2}|f(t)|\,dt<\varepsilon.
$$

再利用：

$$
\left|\int_{t_1}^{t_2}f(t)\,dt\right|
\le \int_{t_1}^{t_2}|f(t)|\,dt,
$$

便得到 $f$ 的柯西条件。由充分性：

$$
\boxed{
\int_a^\infty |f(t)|\,dt<\infty
\quad\Longrightarrow\quad
\int_a^\infty f(t)\,dt\text{ 收敛}.
}
\tag{A2}
$$

这说明绝对收敛蕴含收敛；反过来一般不成立。

### A.5 用于 LQR 证明中的 g(t)

第 8 节已经通过柯西–施瓦茨不等式证明：

$$
\int_0^\infty |g'(t)|\,dt<\infty,
\qquad
g(t)=\|x(t)\|^2.
$$

现在把式（A2）中的 $f$ 取为 $g'$，可知存在有限实数 $L$，使：

$$
\int_0^T g'(t)\,dt\longrightarrow L.
$$

由于 $g$ 在有限区间上绝对连续，积分与导数之间满足：

$$
g(T)-g(0)=\int_0^T g'(t)\,dt.
$$

因此：

$$
\boxed{
g(T)\longrightarrow g(0)+L.
}
\tag{A3}
$$

这严格证明了：如果 $\int_0^\infty |g'|<\infty$，那么 $g(t)$ 存在有限极限。

但这一点本身还不能断言极限是零。例如 $g(t)\equiv1$ 满足 $\int_0^\infty|g'|=0$，极限却为 $1$。

在 LQR 的证明中，还知道：

$$
g(t)\ge0,\qquad \int_0^\infty g(t)\,dt<\infty.
$$

设 $g(t)\to c$。由非负性，$c\ge0$。若 $c>0$，则存在 $T_1$，使所有 $t\ge T_1$ 都满足：

$$
g(t)\ge\frac c2.
$$

于是：

$$
\int_{T_1}^\infty g(t)\,dt
\ge \int_{T_1}^\infty\frac c2\,dt
=\infty,
$$

与已知积分有限矛盾。因此只能有：

$$
\boxed{
g(t)\to0,\qquad x(t)\to0.
}
\tag{A4}
$$

由此，任意固定矩阵 $P$ 对应的末端项 $x(T)^TPx(T)$ 都趋于零。

这段论证使用的顺序是：

1. 柯西–施瓦茨不等式给出 $\int_0^\infty|g'|<\infty$。
2. 积分的柯西收敛准则保证 $\int_0^\infty g'$ 收敛，从而 $g$ 有有限极限。
3. 再结合 $g\ge0$ 且 $\int_0^\infty g<\infty$，确定该极限只能是零。

## 附录 B. 实数数列的柯西收敛准则

附录 A 在证明无穷积分的充分性时，使用了“实数柯西数列必收敛”。本附录从实数的上确界性质出发证明它，不把这一结论本身当作前提。

### B.1 定理与基础性质

对于实数数列 $(a_n)$：

$$
\boxed{
a_n\text{ 收敛于某个有限实数}
\iff
\forall\varepsilon>0,\ \exists N,\
\forall m,n\ge N,\quad |a_n-a_m|<\varepsilon.
}
\tag{B1}
$$

右侧称为柯西条件。它要求从足够靠后的位置开始，任意两项都足够接近，而不仅仅是相邻两项接近。

左侧的收敛定义是：存在有限实数 $a$，使：

$$
\forall\varepsilon>0,\ \exists N,\
\forall n\ge N,\quad |a_n-a|<\varepsilon.
$$

两者的差别是：收敛定义已经涉及极限 $a$，而柯西条件只比较数列自身的项，不要求预先知道极限。

充分性证明使用实数的一条基础性质：

> 任意非空且有上界的实数集合，都存在实数上确界，即最小上界。

这叫上确界性质，是实数完备性的一种表述。由它也能得到下确界的存在性：对于非空且有下界的集合 $E$，

$$
\inf E=-\sup\{-y:y\in E\}.
$$

其中 $\inf E$ 是最大的下界。下确界与上确界不一定属于集合本身。

### B.2 必要性：收敛数列一定满足柯西条件

假设：

$$
a_n\longrightarrow a.
$$

对任意 $\varepsilon>0$，存在整数 $N$，使：

$$
n\ge N\quad\Longrightarrow\quad
|a_n-a|<\frac{\varepsilon}{2}.
$$

于是任取 $m,n\ge N$：

$$
\begin{aligned}
|a_n-a_m|
&=|(a_n-a)-(a_m-a)|\\
&\le |a_n-a|+|a_m-a|\\
&<\frac{\varepsilon}{2}+\frac{\varepsilon}{2}\\
&=\varepsilon.
\end{aligned}
$$

必要性得证。

### B.3 充分性：柯西数列一定存在实数极限

现在只假设柯西条件成立，不预先假设极限存在。

**第一步：证明整个数列有界。**

在柯西条件中取 $\varepsilon=1$。存在整数 $N_0$，使：

$$
m,n\ge N_0\quad\Longrightarrow\quad|a_n-a_m|<1.
$$

固定 $m=N_0$，则所有 $n\ge N_0$ 都满足：

$$
|a_n-a_{N_0}|<1.
$$

由三角不等式：

$$
|a_n|\le |a_{N_0}|+|a_n-a_{N_0}|<|a_{N_0}|+1.
$$

所以尾部有界。前面只有有限项，也有界。例如取：

$$
C=\max\{|a_1|,\ldots,|a_{N_0}|\}+1,
$$

则对所有 $n$，都有：

$$
|a_n|\le C.
$$

**第二步：用每个尾部的上下确界构造候选极限。**

定义从第 $N$ 项开始的尾部集合：

$$
E_N=\{a_n:n\ge N\}.
$$

它非空且有界，因此存在有限实数：

$$
\ell_N=\inf E_N,\qquad h_N=\sup E_N.
$$

对任意 $n\ge N$：

$$
\ell_N\le a_n\le h_N.
$$

所有 $\ell_N$ 都位于 $[-C,C]$ 内。因此可以再次使用上确界性质，定义实数：

$$
\boxed{
a=\sup\{\ell_N:N=1,2,\ldots\}.
}
\tag{B2}
$$

下面证明这个 $a$ 就是极限。

先证明，对每个 $N$：

$$
\boxed{\ell_N\le a\le h_N.}
\tag{B3}
$$

左边由 $a$ 的定义立即成立。

为证明右边，固定 $N$，再任取整数 $k$。选择 $j\ge\max\{k,N\}$，则 $a_j$ 同时属于 $E_k$ 和 $E_N$，所以：

$$
\ell_k\le a_j\le h_N.
$$

因此，对所有 $k$ 都有 $\ell_k\le h_N$，即 $h_N$ 是集合 $\{\ell_k\}$ 的一个上界。由于 $a$ 是这个集合的最小上界：

$$
a\le h_N.
$$

式（B3）得证。

**第三步：柯西条件使尾部区间的宽度任意小。**

给定任意 $\varepsilon>0$，由柯西条件选择 $N$，使所有 $m,n\ge N$ 都满足：

$$
|a_n-a_m|<\frac{\varepsilon}{2}.
$$

特别地：

$$
a_n<a_m+\frac{\varepsilon}{2}.
$$

固定 $m$，右侧是所有尾部元素 $a_n$ 的上界，因此：

$$
h_N\le a_m+\frac{\varepsilon}{2}.
$$

这对所有 $m\ge N$ 都成立。等价地，$h_N-\varepsilon/2$ 是尾部集合 $E_N$ 的一个下界。因为 $\ell_N$ 是最大的下界：

$$
h_N-\frac{\varepsilon}{2}\le\ell_N.
$$

从而：

$$
\boxed{h_N-\ell_N\le\frac{\varepsilon}{2}.}
\tag{B4}
$$

这里是“$\le$”，因为上下确界可能没有被数列实际取到。选择 $\varepsilon/2$ 保证下一步仍得到严格小于 $\varepsilon$。

**第四步：验证候选实数 a 满足极限定义。**

由式（B3），$a\in[\ell_N,h_N]$。而对所有 $n\ge N$，也有 $a_n\in[\ell_N,h_N]$。

两者在同一个区间中，所以：

$$
|a_n-a|
\le h_N-\ell_N
\le\frac{\varepsilon}{2}
<\varepsilon.
$$

因此：

$$
\forall\varepsilon>0,\ \exists N,\
\forall n\ge N,\quad |a_n-a|<\varepsilon.
$$

这正是：

$$
\boxed{a_n\longrightarrow a.}
$$

充分性得证。结合必要性，实数数列的柯西收敛准则得证。

### B.4 证明中用到了什么

必要性只使用极限定义和三角不等式。

充分性使用：

1. 柯西条件保证有界。
2. 实数的上确界性质保证能够构造一个实数 $a$。
3. 柯西条件保证尾部区间宽度趋于零，从而所有尾部元素都趋于这个 $a$。

因此，没有用“柯西数列必收敛”来证明它自身，也没有把收敛子列的存在性作为另一个未展开的步骤。

实数的完备性是必要基础。若把极限要求限制在有理数中，柯西条件就不足以保证收敛于该数系中的元素。例如逐位截断 $\sqrt2$ 的小数得到的有理数数列是柯西数列，但它没有有理数极限。

### B.5 不能只检查相邻项之差

仅有：

$$
|a_{n+1}-a_n|\longrightarrow0
$$

不能保证收敛。

例如：

$$
a_n=\sum_{k=1}^n\frac1k.
$$

相邻项之差满足：

$$
a_{n+1}-a_n=\frac1{n+1}\longrightarrow0.
$$

但取两个足够靠后的下标 $n$ 和 $2n$：

$$
a_{2n}-a_n
=\sum_{k=n+1}^{2n}\frac1k
\ge n\cdot\frac1{2n}
=\frac12.
$$

因此，无论从多大的 $N$ 开始，都能找到 $m,n\ge N$，使两项之差至少为 $1/2$，不满足柯西条件。

这说明准则中的“任意两项”不能替换成“相邻两项”。
