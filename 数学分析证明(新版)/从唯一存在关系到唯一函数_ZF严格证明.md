# 从唯一存在关系到唯一函数：ZF 严格证明

> 校订版。本文仿照“三栏逐行推导表”的视觉格式；形式演算固定为**带等词的经典一阶自然演绎** \(\mathrm{ND}_{=}\) 加 ZF。本文不是 Hilbert 系统 \(\mathrm{L1}\text{--}\mathrm{L3}+\mathrm{MP}\) 的逐行推导，因而不混用两套演算的名称。

---

## 1. 定理、语言与元语言约定

### 1.1 基础语言

对象语言为纯集合论语言

\[
\mathcal L_{\in}=\{\in,=\}.
\]

所有对象变量都在全体集合上取值。语言中没有函数符号、常量符号以及额外谓词符号。

固定一个元语言中的一阶公式

\[
\varphi(x,y),
\qquad
\operatorname{FV}(\varphi)\subseteq\{x,y\}.
\]

这里的 \(\varphi\) 是一个固定公式，不是对象语言变量，因此不写 \(\forall\varphi\)。本文不引入任何额外自由参数。式 \(\varphi(x,z)\) 表示把 \(\varphi(x,y)\) 中自由出现的 \(y\) 作避免捕获的代换 \(y:=z\)，其中 \(z\) 预先选为新鲜变量。

### 1.2 前提

定义公式缩写

\[
\boxed{
H_{\varphi}(E):\!\!\iff
\forall x\left(
x\in E\to
\exists y\left[
\varphi(x,y)\land
\forall z\bigl(\varphi(x,z)\to y=z\bigr)
\right]
\right).
}
\tag{H}
\]

### 1.3 最终目标

本文证明以下关于每个固定公式 \(\varphi(x,y)\) 的元定理：

\[
\boxed{
ZF\vdash
\forall E\left[
H_{\varphi}(E)\to
\exists F\left(
\operatorname{Real}_{\varphi}(F,E)
\land
\forall G\bigl(
\operatorname{Real}_{\varphi}(G,E)\to G=F
\bigr)
\right)
\right].
}
\tag{T}
\]

第 4 节会把 \(\operatorname{Real}_{\varphi}\) 完全定义为纯 \(\{\in,=\}\)-公式的缩写。

---

## 2. 逻辑演算及作用域规则

### 2.1 原始自然演绎规则

本文把下列规则作为所选演算 \(\mathrm{ND}_{=}\) 的原始规则：

\[
\land I,\ \land E_1,\ \land E_2,
\quad
\lor I_1,\ \lor I_2,\ \lor E,
\]

\[
\to I,\ \to E,
\quad
\leftrightarrow I,\ \leftrightarrow E_1,\ \leftrightarrow E_2,
\]

\[
\forall I,\ \forall E,
\quad
\exists I,\ \exists E,
\quad
=I,\ =\!Sub,\ \mathrm{Reit}.
\]

其中 \(=\!Sub\) 是莱布尼茨代换规则。等词对称性和传递性作为 \(=I,=\!Sub\) 的标准派生规则使用，并在依据栏明确标为 \(=\!Sym\)、\(=\!Trans\)。

为保证每个公式具有唯一语法分析，凡有限个 \(\land\) 省略内部括号时一律按左结合解析；\(\land\) 的结合优先级高于 \(\to\) 与 \(\leftrightarrow\)。因此书写 \(A\land B\land C\to D\) 只是 \(((A\land B)\land C)\to D\) 的括号缩写。关键定义另外显式写出括号。量词的辖域均由紧随其后的圆括号、方括号或花括号明确界定。

### 2.2 侧条件

1. \(\forall I\)：被推广变量不得自由出现于任何尚未解除的假设中。
2. \(\exists E\)：从 \(\exists x\,A(x)\) 开启子证明时使用的新见证 \(c\) 不得自由出现于目标结论，也不得自由出现于除子证明假设 \(A(c)\) 外的其他未解除假设中。
3. 分离、替换模式中的新集合变量不得自由出现于被实例化的筛选公式中。
4. 所有代换均作避免变量捕获的代换。

唯一存在不是原始量词。本文规定其定义性展开为

\[
\exists!x\,A(x)
:\!\!\iff
\exists x\left[
A(x)\land
\forall x'\bigl(A(x')\to x=x'\bigr)
\right],
\]

其中 \(x'\) 是避免捕获的新鲜变量。

### 2.3 表格中的子证明记号

- \([A]^\alpha\)：开启编号为 \(\alpha\) 的临时假设子证明；
- “关闭 \(\alpha\)，\(\to I\)”：解除该假设；
- “关闭 \(\alpha\)，\(\exists E\)”：解除以新鲜见证开启的存在消去子证明。

因此，表格中的见证字母不会被当作无条件存在的全局常量。

---

## 3. 实际使用的 ZF 公理

| 名称 | 严格公理公式 | 本文用途 |
|---|---|---|
| 外延 | \(\forall A\forall B[\forall u(u\in A\leftrightarrow u\in B)\to A=B]\) | 证明各集合编码及函数图唯一 |
| 配对 | \(\forall a\forall b\exists c\forall u[u\in c\leftrightarrow(u=a\lor u=b)]\) | 构造单点集、无序对及 Kuratowski 有序对 |
| 并集 | \(\forall A\exists U\forall u[u\in U\leftrightarrow\exists v(v\in A\land u\in v)]\) | 构造包含 \(E\) 与像集的并集 |
| 幂集 | \(\forall A\exists P\forall u[u\in P\leftrightarrow\forall v(v\in u\to v\in A)]\) | 构造笛卡尔积的母集 |

### 3.1 分离公理模式

对每个公式 \(\psi(w,q_1,\ldots,q_n)\)，若新集合变量 \(B\) 不自由出现于 \(\psi\)，则有公理：

\[
\boxed{
\forall q_1\cdots\forall q_n\forall A
\exists B\forall w\left[
w\in B\leftrightarrow
\bigl(w\in A\land\psi(w,q_1,\ldots,q_n)\bigr)
\right].
}
\tag{Sep}_{\psi}
\]

### 3.2 替换公理模式

本文明确采用标准的“函数式精确像形式”。对每个公式 \(\theta(x,y,q_1,\ldots,q_n)\)，若新集合变量 \(B\) 不自由出现于 \(\theta\)，则有公理：

\[
\boxed{
\begin{aligned}
\forall q_1\cdots\forall q_n\forall A\Bigl(&
\forall x\bigl(
x\in A\to
\exists y[\theta(x,y,q_1,\ldots,q_n)
\land
\forall z(\theta(x,z,q_1,\ldots,q_n)\to y=z)]
\bigr)
\\
&\to
\exists B\forall u\bigl[
u\in B\leftrightarrow
\exists x(x\in A\land\theta(x,u,q_1,\ldots,q_n))
\bigr]
\Bigr).
\end{aligned}
}
\tag{Rep}_{\theta}
\]

该形式与常见的“先得到包含所有值的集合”形式在分离模式下等价。本文既然已经明确选用精确像形式，后文可以直接得到精确像集。

本文不使用选择公理、无穷公理和正则公理。

---

## 4. 全部定义性缩写

以下记号全部是元语言中的公式缩写。把右侧逐项替入即可消去它们；它们不是 \(\mathcal L_{\in}\) 中新增的谓词。

### 4.1 单点集、无序对和 Kuratowski 有序对

\[
\operatorname{Sing}(s,x)
:\!\!\iff
\forall r(r\in s\leftrightarrow r=x).
\tag{D1}
\]

\[
\operatorname{UnordPair}(d,x,y)
:\!\!\iff
\forall r[r\in d\leftrightarrow(r=x\lor r=y)].
\tag{D2}
\]

\[
\boxed{
\begin{aligned}
K(w,x,y):\!\!\iff
\exists s\exists d\bigl[&
\bigl(\operatorname{Sing}(s,x)
\land
\operatorname{UnordPair}(d,x,y)\bigr)
\land
\operatorname{UnordPair}(w,s,d)
\bigr].
\end{aligned}
}
\tag{D3}
\]

完全展开的 \(K\) 只含 \(\in,=,\land,\lor,\leftrightarrow,\forall,\exists\)。在证明第 5 节的唯一存在之后，才把 \(K(w,x,y)\) 解释为 \(w=\langle x,y\rangle\)。

### 4.2 关系、单值性、定义域和值满足性

\[
\operatorname{Rel}(F):\!\!\iff
\forall w\left[
w\in F\to\exists x\exists y\,K(w,x,y)
\right].
\tag{D4}
\]

\[
\boxed{
\begin{aligned}
\operatorname{SV}(F):\!\!\iff
\forall w_1\forall w_2\forall x\forall y_1\forall y_2\Bigl[&
\bigl(w_1\in F\land K(w_1,x,y_1)\bigr)
\\
&\land \bigl(w_2\in F\land K(w_2,x,y_2)\bigr)
\to y_1=y_2
\Bigr].
\end{aligned}
}
\tag{D5}
\]

\[
\operatorname{Fun}(F):\!\!\iff
\operatorname{Rel}(F)\land\operatorname{SV}(F).
\tag{D6}
\]

\[
\operatorname{Dom}(F,E):\!\!\iff
\forall x\left[
x\in E\leftrightarrow
\exists w\exists y(w\in F\land K(w,x,y))
\right].
\tag{D7}
\]

\[
\operatorname{Ran}(F,R):\!\!\iff
\forall y\left[
y\in R\leftrightarrow
\exists w\exists x(w\in F\land K(w,x,y))
\right].
\tag{D8}
\]

\[
\operatorname{Sat}_{\varphi}(F):\!\!\iff
\forall w\forall x\forall y\left[
w\in F\land K(w,x,y)\to\varphi(x,y)
\right].
\tag{D9}
\]

\[
\boxed{
\operatorname{Real}_{\varphi}(F,E):\!\!\iff
\operatorname{Fun}(F)
\land
\bigl(\operatorname{Dom}(F,E)
\land
\operatorname{Sat}_{\varphi}(F)\bigr).
}
\tag{D10}
\]

---

## 5. 引理 A：Kuratowski 有序对固定坐标下存在唯一

### 5.1 存在性

| 步骤 | 严格公式 | 纯底层公理/推理规则及代入说明 |
|---:|---|---|
| T5.1 | \(\exists s\forall r[r\in s\leftrightarrow(r=x\lor r=x)]\) | 配对公理，代入 \(a:=x,b:=x\) |
| T5.2 | \(\exists s\,\operatorname{Sing}(s,x)\) | T5.1；对任意 \(r\)，由 \(r=x\lor r=x\) 经 \(\lor E\) 得 \(r=x\)，反向由 \(\lor I_1\)；再作定义替换 D1 |
| T5.3 | \([\operatorname{Sing}(s_0,x)]^{\alpha}\) | 对 T5.2 开启 \(\exists E\) 子证明；\(s_0\) 新鲜 |
| T5.4 | \(\exists d\,\operatorname{UnordPair}(d,x,y)\) | 配对公理，代入 \(a:=x,b:=y\)，再作定义替换 D2 |
| T5.5 | \([\operatorname{UnordPair}(d_0,x,y)]^{\beta}\) | 对 T5.4 开启 \(\exists E\) 子证明；\(d_0\) 新鲜 |
| T5.6 | \(\exists w\,\operatorname{UnordPair}(w,s_0,d_0)\) | 配对公理，代入 \(a:=s_0,b:=d_0\)，再作定义替换 D2 |
| T5.7 | \([\operatorname{UnordPair}(w_0,s_0,d_0)]^{\gamma}\) | 对 T5.6 开启 \(\exists E\) 子证明；\(w_0\) 新鲜 |
| T5.8 | \(\operatorname{Sing}(s_0,x)\land\operatorname{UnordPair}(d_0,x,y)\) | T5.3、T5.5，\(\land I\) |
| T5.9 | \(\operatorname{Sing}(s_0,x)\land\operatorname{UnordPair}(d_0,x,y)\land\operatorname{UnordPair}(w_0,s_0,d_0)\) | T5.8、T5.7，\(\land I\) |
| T5.10 | \(K(w_0,x,y)\) | T5.9；D3，依次 \(\exists I\)，见证 \(s_0,d_0\) |
| T5.11 | \(\exists w\,K(w,x,y)\) | T5.10，\(\exists I\)，见证 \(w_0\) |
| T5.12 | \(\exists w\,K(w,x,y)\) | T5.6 与子证明 \(\gamma\) 的 T5.7–T5.11，关闭 \(\gamma\)，\(\exists E\) |
| T5.13 | \(\exists w\,K(w,x,y)\) | T5.4 与子证明 \(\beta\) 的 T5.5–T5.12，关闭 \(\beta\)，\(\exists E\)；结论不含 \(d_0\) |
| T5.14 | \(\exists w\,K(w,x,y)\) | T5.2 与子证明 \(\alpha\) 的 T5.3–T5.13，关闭 \(\alpha\)，\(\exists E\)；结论不含 \(s_0\) |
| T5.15 | \(\forall x\forall y\exists w\,K(w,x,y)\) | T5.14，依次 \(\forall I\)；\(x,y\) 不自由出现于未解除假设 |

### 5.2 固定坐标时的唯一性

| 步骤 | 严格公式 | 纯底层公理/推理规则及代入说明 |
|---:|---|---|
| T5.16 | \([K(w,x,y)]^{\delta}\) | 开启 \(\to I\) 子证明 |
| T5.17 | \([K(w',x,y)]^{\varepsilon}\) | 在 \(\delta\) 内开启第二个 \(\to I\) 子证明；\(w'\) 任意 |
| T5.18 | \([\operatorname{Sing}(s,x)\land\operatorname{UnordPair}(d,x,y)\land\operatorname{UnordPair}(w,s,d)]^{\eta}\) | T5.16、D3，依次开启两个 \(\exists E\) 子证明；\(s,d\) 新鲜，合并标为 \(\eta\) |
| T5.19 | \([\operatorname{Sing}(s',x)\land\operatorname{UnordPair}(d',x,y)\land\operatorname{UnordPair}(w',s',d')]^{\iota}\) | T5.17、D3，依次开启两个 \(\exists E\) 子证明；\(s',d'\) 新鲜，合并标为 \(\iota\) |
| T5.20 | \(\forall r(r\in s\leftrightarrow r=x)\) | T5.18，依次两次 \(\land E_1\)，D1 |
| T5.21 | \(\forall r(r\in s'\leftrightarrow r=x)\) | T5.19，依次两次 \(\land E_1\)，D1 |
| T5.22 | \(r\in s\leftrightarrow r=x\) | T5.20，\(\forall E\) |
| T5.23 | \(r\in s'\leftrightarrow r=x\) | T5.21，\(\forall E\) |
| T5.24 | \(r\in s\to r\in s'\) | 假设 \(r\in s\)；T5.22 正向得 \(r=x\)，T5.23 反向得 \(r\in s'\)；关闭假设，\(\to I\) |
| T5.25 | \(r\in s'\to r\in s\) | 假设 \(r\in s'\)；T5.23 正向得 \(r=x\)，T5.22 反向得 \(r\in s\)；关闭假设，\(\to I\) |
| T5.26 | \(r\in s\leftrightarrow r\in s'\) | T5.24、T5.25，\(\leftrightarrow I\) |
| T5.27 | \(\forall r(r\in s\leftrightarrow r\in s')\) | T5.26，\(\forall I\) |
| T5.28 | \(s=s'\) | T5.27，外延公理，\(\to E\) |
| T5.29 | \(\forall r[r\in d\leftrightarrow(r=x\lor r=y)]\) | T5.18，先 \(\land E_1\) 后 \(\land E_2\)，D2 |
| T5.30 | \(\forall r[r\in d'\leftrightarrow(r=x\lor r=y)]\) | T5.19，先 \(\land E_1\) 后 \(\land E_2\)，D2 |
| T5.31 | \(\forall r(r\in d\leftrightarrow r\in d')\) | 对任意 \(r\)，由 T5.29、T5.30 的两个方向依次使用 \(\forall E,\leftrightarrow E,\to E,\leftrightarrow I\)，最后 \(\forall I\) |
| T5.32 | \(d=d'\) | T5.31，外延公理，\(\to E\) |
| T5.33 | \(\forall r[r\in w\leftrightarrow(r=s\lor r=d)]\) | T5.18，\(\land E_2\)，D2 |
| T5.34 | \(\forall r[r\in w'\leftrightarrow(r=s'\lor r=d')]\) | T5.19，\(\land E_2\)，D2 |
| T5.35 | \(\forall r(r\in w\leftrightarrow r\in w')\) | T5.28、T5.32 代入 T5.34；再由 T5.33 与代入后的公式逐向使用 \(\leftrightarrow E,\to E,\leftrightarrow I,\forall I\) |
| T5.36 | \(w=w'\) | T5.35，外延公理，\(\to E\) |
| T5.37 | \(w=w'\) | 关闭 \(\iota\)，依次应用两次 \(\exists E\)；T5.36 不含 \(s',d'\) |
| T5.38 | \(w=w'\) | 关闭 \(\eta\)，依次应用两次 \(\exists E\)；T5.37 不含 \(s,d\) |
| T5.39 | \(K(w',x,y)\to w=w'\) | 关闭 \(\varepsilon\)，\(\to I\) |
| T5.40 | \(\forall w'[K(w',x,y)\to w=w']\) | T5.39，\(\forall I\)；\(w'\) 不自由出现于其他未解除假设 |
| T5.41 | \(K(w,x,y)\to\forall w'[K(w',x,y)\to w=w']\) | 关闭 \(\delta\)，\(\to I\) |
| T5.42 | \(\forall w\{K(w,x,y)\to\forall w'[K(w',x,y)\to w=w']\}\) | T5.41，\(\forall I\) |

### 5.3 合并存在性与唯一性

| 步骤 | 严格公式 | 纯底层公理/推理规则及代入说明 |
|---:|---|---|
| T5.43 | \(\exists w\,K(w,x,y)\) | T5.15，依次 \(\forall E\)，代入固定的 \(x,y\) |
| T5.44 | \([K(w_*,x,y)]^{\zeta}\) | 对 T5.43 开启新的 \(\exists E\) 子证明；\(w_*\) 新鲜 |
| T5.45 | \(\forall w'[K(w',x,y)\to w_*=w']\) | T5.42，\(\forall E\)，代入 \(w:=w_*\) |
| T5.46 | \(K(w_*,x,y)\land\forall w'[K(w',x,y)\to w_*=w']\) | T5.44、T5.45，\(\land I\) |
| T5.47 | \(\exists w\{K(w,x,y)\land\forall w'[K(w',x,y)\to w=w']\}\) | T5.46，\(\exists I\)，见证 \(w_*\) |
| T5.48 | \(\exists w\{K(w,x,y)\land\forall w'[K(w',x,y)\to w=w']\}\) | T5.43 与子证明 \(\zeta\) 的 T5.44–T5.47，关闭 \(\zeta\)，\(\exists E\) |
| T5.49 | \(\forall x\forall y\exists w\{K(w,x,y)\land\forall w'[K(w',x,y)\to w=w']\}\) | T5.48，依次 \(\forall I\)；\(x,y\) 不自由出现于未解除假设 |

由 T5.49 得到：

\[
\boxed{
\forall x\forall y
\exists w\left[
K(w,x,y)\land
\forall w'(K(w',x,y)\to w=w')
\right].
}
\tag{K1}
\]

T5.43–T5.48 明确显示：先实例化 T5.15，再对所得存在式开启一个新的 \(\exists E\) 子证明；并没有把 T5.15 本身误当成已经打开的子证明。

---

## 6. 引理 B：Kuratowski 有序对的坐标单射性

目标：

\[
\boxed{
\forall w\forall x\forall y\forall x'\forall y'
\left[
K(w,x,y)\land K(w,x',y')
\to(x=x'\land y=y')
\right].
}
\tag{K2}
\]

| 步骤 | 严格公式 | 纯底层公理/推理规则及代入说明 |
|---:|---|---|
| T6.1 | \([K(w,x,y)\land K(w,x',y')]^{\kappa}\) | 开启 \(\to I\) 子证明 |
| T6.2 | \(K(w,x,y)\) | T6.1，\(\land E_1\) |
| T6.3 | \(K(w,x',y')\) | T6.1，\(\land E_2\) |
| T6.4 | \([\operatorname{Sing}(s,x)\land\operatorname{UnordPair}(d,x,y)\land\operatorname{UnordPair}(w,s,d)]^{\lambda}\) | T6.2、D3，依次开启两个 \(\exists E\) 子证明；\(s,d\) 新鲜 |
| T6.5 | \([\operatorname{Sing}(s',x')\land\operatorname{UnordPair}(d',x',y')\land\operatorname{UnordPair}(w,s',d')]^{\mu}\) | T6.3、D3，依次开启两个 \(\exists E\) 子证明；\(s',d'\) 新鲜 |
| T6.6 | \(s\in w\) | T6.4 外层无序对公式，\(\forall E\) 代入 \(s\)，由 \(s=s\) 经 \(\lor I_1,\leftrightarrow E_2,\to E\) |
| T6.7 | \(s=s'\lor s=d'\) | T6.5 外层无序对公式，\(\forall E\) 代入 \(s\)，再由 T6.6 经 \(\leftrightarrow E_1,\to E\) |
| T6.8 | \(x'\in s'\) | T6.5 的 Sing 公式，\(\forall E\) 代入 \(x'\)，由 \(x'=x'\) 经 \(\leftrightarrow E_2,\to E\) |
| T6.9 | \(x'\in d'\) | T6.5 的内层无序对公式，\(\forall E\) 代入 \(x'\)，由 \(x'=x'\) 经 \(\lor I_1,\leftrightarrow E_2,\to E\) |
| T6.10 | \([s=s']^{\nu_1}\) | 对 T6.7 第一支开启 \(\lor E\) 子证明 |
| T6.11 | \(x'\in s\) | T6.8、T6.10，\(=\!Sub\) |
| T6.12 | \(x'=x\) | T6.4 的 Sing 公式，\(\forall E\) 代入 \(x'\)，再由 T6.11 经 \(\leftrightarrow E_1,\to E\) |
| T6.13 | \([s=d']^{\nu_2}\) | 对 T6.7 第二支开启 \(\lor E\) 子证明 |
| T6.14 | \(x'\in s\) | T6.9、T6.13，\(=\!Sub\) |
| T6.15 | \(x'=x\) | T6.4 的 Sing 公式，\(\forall E\) 代入 \(x'\)，再由 T6.14 经 \(\leftrightarrow E_1,\to E\) |
| T6.16 | \(x'=x\) | T6.7 与子证明 \(\nu_1,\nu_2\)，关闭两支，\(\lor E\) |
| T6.17 | \(x=x'\) | T6.16，\(=\!Sym\) |
| T6.18a | \([r\in d]^{\theta_1}\) | 开启正向 \(\to I\) 子证明；\(r\) 任意 |
| T6.18b | \(d\in w\) | T6.4 的外层无序对公式，\(\forall E\) 代入 \(d\)；由 \(d=d\) 经 \(\lor I_2,\leftrightarrow E_2,\to E\) |
| T6.18c | \(d\in w\land r\in d\) | T6.18b、T6.18a，\(\land I\) |
| T6.18d | \(\exists v(v\in w\land r\in v)\) | T6.18c，\(\exists I\)，见证 \(v:=d\) |
| T6.18e | \(r\in d\to\exists v(v\in w\land r\in v)\) | 关闭 \(\theta_1\)，\(\to I\) |
| T6.18f | \([\exists v(v\in w\land r\in v)]^{\theta_2}\) | 开启反向 \(\to I\) 子证明 |
| T6.18g | \([v\in w\land r\in v]^{\theta_3}\) | 对 T6.18f 开启 \(\exists E\) 子证明；\(v\) 新鲜 |
| T6.18h | \(v=s\lor v=d\) | T6.4 的外层无序对公式与 T6.18g 中 \(v\in w\)，\(\forall E,\leftrightarrow E_1,\to E\) |
| T6.18i | \([v=s]^{\theta_4}\) | 对 T6.18h 第一支开启 \(\lor E\) 子证明 |
| T6.18j | \(r\in s\) | T6.18g 中 \(r\in v\) 与 T6.18i，\(=\!Sub\) |
| T6.18k | \(r=x\) | T6.4 的 Sing 公式与 T6.18j，\(\forall E,\leftrightarrow E_1,\to E\) |
| T6.18l | \(x\in d\) | T6.4 的内层无序对公式，\(\forall E\) 代入 \(x\)；由 \(x=x\) 经 \(\lor I_1,\leftrightarrow E_2,\to E\) |
| T6.18m | \(r\in d\) | T6.18k、T6.18l，\(=\!Sub\) |
| T6.18n | \([v=d]^{\theta_5}\) | 对 T6.18h 第二支开启 \(\lor E\) 子证明 |
| T6.18o | \(r\in d\) | T6.18g 中 \(r\in v\) 与 T6.18n，\(=\!Sub\) |
| T6.18p | \(r\in d\) | T6.18h 与子证明 \(\theta_4,\theta_5\)，关闭两支，\(\lor E\) |
| T6.18q | \(r\in d\) | T6.18f 与子证明 \(\theta_3\) 的 T6.18g–T6.18p，关闭 \(\theta_3\)，\(\exists E\) |
| T6.18r | \(\exists v(v\in w\land r\in v)\to r\in d\) | 关闭 \(\theta_2\)，\(\to I\) |
| T6.18s | \(r\in d\leftrightarrow\exists v(v\in w\land r\in v)\) | T6.18e、T6.18r，\(\leftrightarrow I\) |
| T6.18t | \(\forall r[r\in d\leftrightarrow\exists v(v\in w\land r\in v)]\) | T6.18s，\(\forall I\) |
| T6.19a | \([r\in d']^{\theta'_1}\) | 开启正向 \(\to I\) 子证明；\(r\) 任意 |
| T6.19b | \(d'\in w\) | T6.5 的外层无序对公式，\(\forall E\) 代入 \(d'\)；由 \(d'=d'\) 经 \(\lor I_2,\leftrightarrow E_2,\to E\) |
| T6.19c | \(d'\in w\land r\in d'\) | T6.19b、T6.19a，\(\land I\) |
| T6.19d | \(\exists v(v\in w\land r\in v)\) | T6.19c，\(\exists I\)，见证 \(v:=d'\) |
| T6.19e | \(r\in d'\to\exists v(v\in w\land r\in v)\) | 关闭 \(\theta'_1\)，\(\to I\) |
| T6.19f | \([\exists v(v\in w\land r\in v)]^{\theta'_2}\) | 开启反向 \(\to I\) 子证明 |
| T6.19g | \([v\in w\land r\in v]^{\theta'_3}\) | 对 T6.19f 开启 \(\exists E\) 子证明；\(v\) 新鲜 |
| T6.19h | \(v=s'\lor v=d'\) | T6.5 的外层无序对公式与 T6.19g 中 \(v\in w\)，\(\forall E,\leftrightarrow E_1,\to E\) |
| T6.19i | \([v=s']^{\theta'_4}\) | 对 T6.19h 第一支开启 \(\lor E\) 子证明 |
| T6.19j | \(r\in s'\) | T6.19g 中 \(r\in v\) 与 T6.19i，\(=\!Sub\) |
| T6.19k | \(r=x'\) | T6.5 的 Sing 公式与 T6.19j，\(\forall E,\leftrightarrow E_1,\to E\) |
| T6.19l | \(x'\in d'\) | T6.5 的内层无序对公式，\(\forall E\) 代入 \(x'\)；由 \(x'=x'\) 经 \(\lor I_1,\leftrightarrow E_2,\to E\) |
| T6.19m | \(r\in d'\) | T6.19k、T6.19l，\(=\!Sub\) |
| T6.19n | \([v=d']^{\theta'_5}\) | 对 T6.19h 第二支开启 \(\lor E\) 子证明 |
| T6.19o | \(r\in d'\) | T6.19g 中 \(r\in v\) 与 T6.19n，\(=\!Sub\) |
| T6.19p | \(r\in d'\) | T6.19h 与子证明 \(\theta'_4,\theta'_5\)，关闭两支，\(\lor E\) |
| T6.19q | \(r\in d'\) | T6.19f 与子证明 \(\theta'_3\) 的 T6.19g–T6.19p，关闭 \(\theta'_3\)，\(\exists E\) |
| T6.19r | \(\exists v(v\in w\land r\in v)\to r\in d'\) | 关闭 \(\theta'_2\)，\(\to I\) |
| T6.19s | \(r\in d'\leftrightarrow\exists v(v\in w\land r\in v)\) | T6.19e、T6.19r，\(\leftrightarrow I\) |
| T6.19t | \(\forall r[r\in d'\leftrightarrow\exists v(v\in w\land r\in v)]\) | T6.19s，\(\forall I\) |
| T6.20 | \(\forall r(r\in d\leftrightarrow r\in d')\) | T6.18t、T6.19t；逐向使用 \(\leftrightarrow E,\to E\)，再 \(\leftrightarrow I,\forall I\) |
| T6.21 | \(d=d'\) | T6.20，外延公理，\(\to E\) |
| T6.22 | \(y\in d\) | T6.4 的内层无序对公式，\(\forall E\) 代入 \(y\)，由 \(y=y\) 经 \(\lor I_2,\leftrightarrow E_2,\to E\) |
| T6.23 | \(y\in d'\) | T6.22、T6.21，\(=\!Sub\) |
| T6.24 | \(y=x'\lor y=y'\) | T6.5 的内层无序对公式，\(\forall E\) 代入 \(y\)，与 T6.23 经 \(\leftrightarrow E_1,\to E\) |
| T6.25 | \(y'\in d'\) | T6.5 的内层无序对公式，\(\forall E\) 代入 \(y'\)，由 \(y'=y'\) 经 \(\lor I_2,\leftrightarrow E_2,\to E\) |
| T6.26 | \(y'\in d\) | T6.25、T6.21，\(=\!Sub\) |
| T6.27 | \(y'=x\lor y'=y\) | T6.4 的内层无序对公式，\(\forall E\) 代入 \(y'\)，与 T6.26 经 \(\leftrightarrow E_1,\to E\) |
| T6.28 | \([y=y']^{\rho_1}\) | 对 T6.24 第二支开启 \(\lor E\) 子证明 |
| T6.29 | \(y=y'\) | T6.28，重申 |
| T6.30 | \([y=x']^{\rho_2}\) | 对 T6.24 第一支开启 \(\lor E\) 子证明 |
| T6.31 | \(y=x\) | T6.30、T6.16，\(=\!Trans\) |
| T6.32 | \([y'=x]^{\sigma_1}\) | 对 T6.27 第一支开启 \(\lor E\) 子证明 |
| T6.33 | \(y'=y\) | T6.32、T6.31，\(=\!Trans\) 与 \(=\!Sym\) |
| T6.34 | \(y=y'\) | T6.33，\(=\!Sym\) |
| T6.35 | \([y'=y]^{\sigma_2}\) | 对 T6.27 第二支开启 \(\lor E\) 子证明 |
| T6.36 | \(y=y'\) | T6.35，\(=\!Sym\) |
| T6.37 | \(y=y'\) | T6.27 与子证明 \(\sigma_1,\sigma_2\)，关闭两支，\(\lor E\) |
| T6.38 | \(y=y'\) | T6.24 与子证明 \(\rho_2\) 的 T6.30–T6.37 以及 \(\rho_1\) 的 T6.28–T6.29，关闭两支，\(\lor E\) |
| T6.39 | \(x=x'\land y=y'\) | T6.17、T6.38，\(\land I\) |
| T6.40 | \(x=x'\land y=y'\) | 关闭 \(\mu\)，依次两次 \(\exists E\)；结论不含 \(s',d'\) |
| T6.41 | \(x=x'\land y=y'\) | 关闭 \(\lambda\)，依次两次 \(\exists E\)；结论不含 \(s,d\) |
| T6.42 | \(K(w,x,y)\land K(w,x',y')\to(x=x'\land y=y')\) | 关闭 \(\kappa\)，\(\to I\) |
| T6.43 | 公式 (K2) | T6.42，依次 \(\forall I\) |

---

## 7. 引理 C：笛卡尔积集合存在

定义以下缩写：

\[
\operatorname{ERUnion}(U,E,R):\!\!\iff
\forall a[a\in U\leftrightarrow(a\in E\lor a\in R)].
\tag{D11}
\]

\[
\operatorname{Pow}(P,A):\!\!\iff
\forall a[a\in P\leftrightarrow\forall r(r\in a\to r\in A)].
\tag{D12}
\]

\[
\operatorname{Prod}(C,E,R):\!\!\iff
\forall w\left[
w\in C\leftrightarrow
\exists x\exists y\bigl((x\in E\land y\in R)\land K(w,x,y)\bigr)
\right].
\tag{D13}
\]

目标：

\[
\boxed{\forall E\forall R\exists!C\,\operatorname{Prod}(C,E,R).}
\tag{P1}
\]

### 7.1 构造母集

| 步骤 | 严格公式 | 纯底层公理/推理规则及代入说明 |
|---:|---|---|
| T7.1 | \(\exists A\forall v[v\in A\leftrightarrow(v=E\lor v=R)]\) | 配对公理，代入 \(a:=E,b:=R\) |
| T7.2 | \([\forall v(v\in A_0\leftrightarrow(v=E\lor v=R))]^{\tau}\) | 对 T7.1 开启 \(\exists E\) 子证明；\(A_0\) 新鲜 |
| T7.3 | \(\exists U\forall a[a\in U\leftrightarrow\exists v(v\in A_0\land a\in v)]\) | 并集公理，代入 \(A:=A_0\) |
| T7.4 | \([\forall a(a\in U_0\leftrightarrow\exists v(v\in A_0\land a\in v))]^{\upsilon}\) | 对 T7.3 开启 \(\exists E\) 子证明；\(U_0\) 新鲜 |
| T7.5 | \(a\in U_0\to(a\in E\lor a\in R)\) | T7.4 正向取 \(v\)；T7.2 给出 \(v=E\lor v=R\)；两支用 \(=\!Sub,\lor E\) |
| T7.6 | \(a\in E\to a\in U_0\) | 取 T7.4 中存在见证 \(v:=E\)；由 T7.2 得 \(E\in A_0\) |
| T7.7 | \(a\in R\to a\in U_0\) | 取 T7.4 中存在见证 \(v:=R\)；由 T7.2 得 \(R\in A_0\) |
| T7.8 | \((a\in E\lor a\in R)\to a\in U_0\) | T7.6、T7.7，\(\lor E\) |
| T7.9 | \(a\in U_0\leftrightarrow(a\in E\lor a\in R)\) | T7.5、T7.8，\(\leftrightarrow I\) |
| T7.10 | \(\operatorname{ERUnion}(U_0,E,R)\) | T7.9，\(\forall I\)，D11 |
| T7.11 | \(\exists V\,\operatorname{Pow}(V,U_0)\) | 幂集公理，代入 \(A:=U_0\)，D12 |
| T7.12 | \([\operatorname{Pow}(V_0,U_0)]^{\phi_1}\) | 对 T7.11 开启 \(\exists E\) 子证明；\(V_0\) 新鲜 |
| T7.13 | \(\exists W\,\operatorname{Pow}(W,V_0)\) | 幂集公理，代入 \(A:=V_0\)，D12 |
| T7.14 | \([\operatorname{Pow}(W_0,V_0)]^{\phi_2}\) | 对 T7.13 开启 \(\exists E\) 子证明；\(W_0\) 新鲜 |

### 7.2 母集充分大

令

\[
\psi_C(w,E,R):\!\!\iff
\exists x\exists y\bigl((x\in E\land y\in R)\land K(w,x,y)\bigr).
\tag{D14}
\]

| 步骤 | 严格公式 | 纯底层公理/推理规则及代入说明 |
|---:|---|---|
| T7.15 | \([\psi_C(w,E,R)]^{\chi_0}\) | 开启 \(\to I\) 子证明 |
| T7.16 | \([x\in E\land y\in R\land K(w,x,y)]^{\chi_1}\) | T7.15，依次两个 \(\exists E\)，取新鲜 \(x,y\)，合并标记子证明 \(\chi_1\) |
| T7.17 | \(x\in U_0\) | T7.16、T7.10，\(\land E,\forall E,\leftrightarrow E_2,\lor I_1,\to E\) |
| T7.18 | \(y\in U_0\) | T7.16、T7.10，\(\land E,\forall E,\leftrightarrow E_2,\lor I_2,\to E\) |
| T7.19 | \([\operatorname{Sing}(s,x)\land\operatorname{UnordPair}(d,x,y)\land\operatorname{UnordPair}(w,s,d)]^{\chi_2}\) | T7.16 中的 \(K\)，D3，依次两个 \(\exists E\)，取新鲜 \(s,d\)，合并标记子证明 \(\chi_2\) |
| T7.20 | \(\forall r(r\in s\to r\in U_0)\) | 由 Sing：任取 \(r\in s\)，得到 \(r=x\)，再用 T7.17 与 \(=\!Sub\)，最后 \(\to I,\forall I\) |
| T7.21 | \(s\in V_0\) | T7.12、D12，\(\forall E,\leftrightarrow E_2,\to E\) |
| T7.22 | \(\forall r(r\in d\to r\in U_0)\) | 由内层无序对：\(r\in d\) 给出 \(r=x\lor r=y\)，两支分别用 T7.17、T7.18 与 \(=\!Sub\)，再 \(\lor E,\to I,\forall I\) |
| T7.23 | \(d\in V_0\) | T7.12、D12，\(\forall E,\leftrightarrow E_2,\to E\) |
| T7.24 | \(\forall r(r\in w\to r\in V_0)\) | 由外层无序对：\(r\in w\) 给出 \(r=s\lor r=d\)，两支分别用 T7.21、T7.23 与 \(=\!Sub\)，再 \(\lor E,\to I,\forall I\) |
| T7.25 | \(w\in W_0\) | T7.14、D12，\(\forall E,\leftrightarrow E_2,\to E\) |
| T7.26 | \(w\in W_0\) | 关闭 \(\chi_2\)，依次两个 \(\exists E\)；结论不含 \(s,d\) |
| T7.27 | \(w\in W_0\) | 关闭 \(\chi_1\)，依次两个 \(\exists E\)；结论不含 \(x,y\) |
| T7.28 | \(\psi_C(w,E,R)\to w\in W_0\) | 关闭 \(\chi_0\)，\(\to I\) |
| T7.29 | \(\forall w[\psi_C(w,E,R)\to w\in W_0]\) | T7.28，\(\forall I\) |

### 7.3 分离产品

实际代入分离模式的是把 D14 中的 (K) 按 D3 完全展开后的纯 \(\{\in,=\}\)-公式，记作 \(\widehat\psi_C\)。新集合变量 \(C\) 不自由出现于该公式。

| 步骤 | 严格公式 | 纯底层公理/推理规则及代入说明 |
|---:|---|---|
| T7.30 | \(\exists C\forall w[w\in C\leftrightarrow(w\in W_0\land\psi_C(w,E,R))]\) | 分离模式实例：母集 \(A:=W_0\)，参数 \(E,R\)，筛选公式 \(\widehat\psi_C\) |
| T7.31 | \([\forall w(w\in C_0\leftrightarrow(w\in W_0\land\psi_C(w,E,R)))]^{\omega}\) | 对 T7.30 开启 \(\exists E\) 子证明；\(C_0\) 新鲜 |
| T7.32 | \(w\in C_0\to\psi_C(w,E,R)\) | T7.31，\(\forall E,\leftrightarrow E_1,\to E,\land E_2\) |
| T7.33 | \(\psi_C(w,E,R)\to w\in C_0\) | 假设 \(\psi_C\)；由 T7.29 得 \(w\in W_0\)；\(\land I\) 后用 T7.31 的反向；关闭假设，\(\to I\) |
| T7.34 | \(w\in C_0\leftrightarrow\psi_C(w,E,R)\) | T7.32、T7.33，\(\leftrightarrow I\) |
| T7.35 | \(\operatorname{Prod}(C_0,E,R)\) | T7.34，\(\forall I\)，D13、D14 |
| T7.36 | \(\exists C\,\operatorname{Prod}(C,E,R)\) | T7.35，\(\exists I\)，见证 \(C_0\) |
| T7.37 | \(\exists C\,\operatorname{Prod}(C,E,R)\) | T7.30 与子证明 \(\omega\) 的 T7.31–T7.36，关闭 \(\omega\)，\(\exists E\) |
| T7.38 | \(\exists C\,\operatorname{Prod}(C,E,R)\) | 关闭 \(\phi_2\)，\(\exists E\)；结论不含 \(W_0\) |
| T7.39 | \(\exists C\,\operatorname{Prod}(C,E,R)\) | 关闭 \(\phi_1\)，\(\exists E\)；结论不含 \(V_0\) |
| T7.40 | \(\exists C\,\operatorname{Prod}(C,E,R)\) | 关闭 \(\upsilon\)，\(\exists E\)；结论不含 \(U_0\) |
| T7.41 | \(\exists C\,\operatorname{Prod}(C,E,R)\) | 关闭 \(\tau\)，\(\exists E\)；结论不含 \(A_0\) |

### 7.4 产品的唯一性及存在见证闭合

| 步骤 | 严格公式 | 纯底层公理/推理规则及代入说明 |
|---:|---|---|
| T7.42 | \([\operatorname{Prod}(C,E,R)\land\operatorname{Prod}(C',E,R)]^{\pi_1}\) | 开启唯一性子证明 |
| T7.43 | \(w\in C\leftrightarrow\psi_C(w,E,R)\) | T7.42 左合取，D13、D14，\(\forall E\) |
| T7.44 | \(w\in C'\leftrightarrow\psi_C(w,E,R)\) | T7.42 右合取，D13、D14，\(\forall E\) |
| T7.45 | \(w\in C\to w\in C'\) | 假设 \(w\in C\)；T7.43 正向得 \(\psi_C\)，T7.44 反向得 \(w\in C'\)；关闭假设，\(\to I\) |
| T7.46 | \(w\in C'\to w\in C\) | 假设 \(w\in C'\)；T7.44 正向得 \(\psi_C\)，T7.43 反向得 \(w\in C\)；关闭假设，\(\to I\) |
| T7.47 | \(w\in C\leftrightarrow w\in C'\) | T7.45、T7.46，\(\leftrightarrow I\) |
| T7.48 | \(\forall w(w\in C\leftrightarrow w\in C')\) | T7.47，\(\forall I\) |
| T7.49 | \(C=C'\) | T7.48，外延公理，\(\to E\) |
| T7.50 | \((\operatorname{Prod}(C,E,R)\land\operatorname{Prod}(C',E,R))\to C=C'\) | 关闭 \(\pi_1\)，\(\to I\) |
| T7.51 | \(\forall C\forall C'[(\operatorname{Prod}(C,E,R)\land\operatorname{Prod}(C',E,R))\to C=C']\) | T7.50，依次 \(\forall I\) |
| T7.52 | \([\operatorname{Prod}(C_*,E,R)]^{\pi_2}\) | 对 T7.41 的 \(\exists C\operatorname{Prod}(C,E,R)\) 开启 \(\exists E\) 子证明；\(C_*\) 新鲜 |
| T7.53 | \(\forall C'[\operatorname{Prod}(C',E,R)\to C_*=C']\) | 任取 \(C'\)，假设 \(\operatorname{Prod}(C',E,R)\)，与 T7.52 合取后用 T7.51；关闭假设并作 \(\forall I\) |
| T7.54 | \(\operatorname{Prod}(C_*,E,R)\land\forall C'[\operatorname{Prod}(C',E,R)\to C_*=C']\) | T7.52、T7.53，\(\land I\) |
| T7.55 | \(\exists C\{\operatorname{Prod}(C,E,R)\land\forall C'[\operatorname{Prod}(C',E,R)\to C=C']\}\) | T7.54，\(\exists I\)，见证 \(C_*\) |
| T7.56 | \(\exists C\{\operatorname{Prod}(C,E,R)\land\forall C'[\operatorname{Prod}(C',E,R)\to C=C']\}\) | T7.41 与子证明 \(\pi_2\) 的 T7.52–T7.55，关闭 \(\pi_2\)，\(\exists E\) |
| T7.57 | \(\exists!C\,\operatorname{Prod}(C,E,R)\) | T7.56，按第 2.2 节的 \(\exists!\) 定义替换 |
| T7.58 | \(\forall E\forall R\exists!C\,\operatorname{Prod}(C,E,R)\) | T7.57，依次 \(\forall I\)；\(E,R\) 不自由出现于未解除假设 |

T7.58 即公式 (P1)。证明 (P1) 后才把唯一的 \(C\) 记为 \(E\times R\)。

---

## 8. 替换产生精确的 \(\varphi\)-像集

定义：

\[
Q_{\varphi}(R,E):\!\!\iff
\forall y\left[
y\in R\leftrightarrow
\exists x(x\in E\land\varphi(x,y))
\right].
\tag{D15}
\]

| 步骤 | 严格公式 | 纯底层公理/推理规则及代入说明 |
|---:|---|---|
| T8.1 | \([H_{\varphi}(E)]^{\mathfrak h}\) | 主证明临时前提 |
| T8.2 | \(H_{\varphi}(E)\to\exists R\,Q_{\varphi}(R,E)\) | 精确像替换模式，取 \(A:=E\)、\(\theta(x,y):=\varphi(x,y)\)，并作定义替换 D15；输出变量 \(R\notin\operatorname{FV}(\varphi)\) |
| T8.3 | \(\exists R\,Q_{\varphi}(R,E)\) | T8.1、T8.2，\(\to E\) |

| 步骤 | 严格公式 | 纯底层公理/推理规则及代入说明 |
|---:|---|---|
| T8.4 | \([Q_{\varphi}(R,E)\land Q_{\varphi}(S,E)]^{\mathfrak q}\) | 开启像集唯一性子证明 |
| T8.5 | \(y\in R\leftrightarrow\exists x(x\in E\land\varphi(x,y))\) | T8.4 左合取，D15，\(\forall E\) |
| T8.6 | \(y\in S\leftrightarrow\exists x(x\in E\land\varphi(x,y))\) | T8.4 右合取，D15，\(\forall E\) |
| T8.7 | \(y\in R\to y\in S\) | 假设 \(y\in R\)；T8.5 正向取得中间存在式，T8.6 反向取得 \(y\in S\)；关闭假设，\(\to I\) |
| T8.8 | \(y\in S\to y\in R\) | 假设 \(y\in S\)；T8.6 正向取得中间存在式，T8.5 反向取得 \(y\in R\)；关闭假设，\(\to I\) |
| T8.9 | \(y\in R\leftrightarrow y\in S\) | T8.7、T8.8，\(\leftrightarrow I\) |
| T8.10 | \(\forall y(y\in R\leftrightarrow y\in S)\) | T8.9，\(\forall I\) |
| T8.11 | \(R=S\) | T8.10，外延公理，\(\to E\) |
| T8.12 | \((Q_{\varphi}(R,E)\land Q_{\varphi}(S,E))\to R=S\) | 关闭 \(\mathfrak q\)，\(\to I\) |
| T8.13 | \(\forall R\forall S[(Q_{\varphi}(R,E)\land Q_{\varphi}(S,E))\to R=S]\) | T8.12，依次 \(\forall I\) |
| T8.14 | \([Q_{\varphi}(R_1,E)]^{\mathfrak r_1}\) | 对 T8.3 开启一个独立的 \(\exists E\) 子证明；\(R_1\) 新鲜 |
| T8.15 | \(\forall S[Q_{\varphi}(S,E)\to R_1=S]\) | 任取 \(S\)，假设 \(Q_{\varphi}(S,E)\)，与 T8.14 合取后使用 T8.13；关闭假设并作 \(\forall I\) |
| T8.16 | \(\exists R\{Q_{\varphi}(R,E)\land\forall S[Q_{\varphi}(S,E)\to R=S]\}\) | T8.14、T8.15，\(\land I\)，再 \(\exists I\)，见证 \(R_1\) |
| T8.17 | \(\exists!R\,Q_{\varphi}(R,E)\) | T8.3 与子证明 \(\mathfrak r_1\) 的 T8.14–T8.16，关闭 \(\mathfrak r_1\)，\(\exists E\)，再按第 2.2 节定义替换 |
| T8.18 | \([Q_{\varphi}(R_0,E)]^{\mathfrak r}\) | 对 T8.3 重新开启主构造所需的 \(\exists E\) 子证明；\(R_0\) 新鲜 |

在证明值域公式之前，本文称 \(R_0\) 为“精确 \(\varphi\)-像集”，不把它预先称为函数的陪域。

---

## 9. 分离构造函数图像

定义：

\[
\begin{aligned}
\chi(w,E,R):\!\!\iff
\exists x\exists y\bigl(&
\bigl((x\in E\land y\in R)\land K(w,x,y)\bigr)
\land\varphi(x,y)
\bigr),
\end{aligned}
\tag{D16}
\]

\[
\Xi(w,E):\!\!\iff
\exists x\exists y\bigl(
\bigl(x\in E\land\varphi(x,y)\bigr)\land K(w,x,y)
\bigr),
\tag{D17}
\]

\[
\operatorname{Graph}_{\varphi}(F,E):\!\!\iff
\forall w[w\in F\leftrightarrow\Xi(w,E)].
\tag{D18}
\]

| 步骤 | 严格公式 | 纯底层公理/推理规则及代入说明 |
|---:|---|---|
| T9.1 | \(\exists C\,\operatorname{Prod}(C,E,R_0)\) | 引理 \(\mathrm{(P1)}\)，\(\forall E\) 两次，代入 \(E,R_0\)，再取存在部分 |
| T9.2 | \([\operatorname{Prod}(C_0,E,R_0)]^{\mathfrak c}\) | 对 T9.1 开启 \(\exists E\) 子证明；\(C_0\) 新鲜 |
| T9.3 | \(\exists F\forall w[w\in F\leftrightarrow(w\in C_0\land\chi(w,E,R_0))]\) | 分离模式实例；母集 \(A:=C_0\)，参数 \(E,R_0\)，实际筛选公式为 D16 中展开 D3 后的纯公式；输出变量 \(F\) 不自由出现于筛选公式 |
| T9.4 | \([\forall w(w\in F_0\leftrightarrow(w\in C_0\land\chi(w,E,R_0)))]^{\mathfrak f}\) | 对 T9.3 开启 \(\exists E\) 子证明；\(F_0\) 新鲜 |
| T9.5 | \(\chi(w,E,R_0)\to w\in C_0\) | D16 给出 D14 的见证；T9.2、D13、D14 的反向给出成员关系；用 \(\exists E,\exists I,\forall E,\leftrightarrow E_2,\to E\) |
| T9.6 | \(w\in F_0\to\chi(w,E,R_0)\) | T9.4，\(\forall E,\leftrightarrow E_1,\to E,\land E_2\) |
| T9.7 | \(\chi(w,E,R_0)\to w\in F_0\) | 假设 \(\chi\)，由 T9.5 得 \(w\in C_0\)，合取后使用 T9.4 反向，再关闭假设 |
| T9.8 | \(w\in F_0\leftrightarrow\chi(w,E,R_0)\) | T9.6、T9.7，\(\leftrightarrow I\) |
| T9.9 | \(\chi(w,E,R_0)\to\Xi(w,E)\) | D16 取见证 \(x,y\)，删除合取项 \(y\in R_0\)，按 D17 作 \(\exists I\) |
| T9.10 | \(\Xi(w,E)\to\chi(w,E,R_0)\) | D17 取见证 \(x,y\)；由 T8.18、D15 及 \(x\in E\land\varphi(x,y)\) 得 \(y\in R_0\)；按 D16 作 \(\exists I\) |
| T9.11 | \(w\in F_0\leftrightarrow\Xi(w,E)\) | T9.8–T9.10，逐向使用 \(\leftrightarrow E,\to E\)，再 \(\leftrightarrow I\) |
| T9.12 | \(\operatorname{Graph}_{\varphi}(F_0,E)\) | T9.11，\(\forall I\)，D18 |

### 9.1 固定坐标下的图像刻画

| 步骤 | 严格公式 | 纯底层公理/推理规则及代入说明 |
|---:|---|---|
| T9.13 | \([K(w,x,y)]^{\mathfrak k}\) | 开启 \(\to I\) 子证明 |
| T9.14 | \([w\in F_0]^{\mathfrak m}\) | 在 \(\mathfrak k\) 内开启正向 \(\to I\) 子证明 |
| T9.15 | \(\Xi(w,E)\) | T9.12、D18、T9.14，\(\forall E,\leftrightarrow E_1,\to E\) |
| T9.16 | \([a\in E\land\varphi(a,b)\land K(w,a,b)]^{\mathfrak a}\) | T9.15、D17，依次两个 \(\exists E\)，取新鲜 \(a,b\)，合并标记子证明 \(\mathfrak a\) |
| T9.17 | \(x=a\land y=b\) | T9.13、T9.16 中的 \(K(w,a,b)\)，引理 (K2) 的实例 |
| T9.18 | \(x\in E\) | T9.16、T9.17，\(\land E,=\!Sub\) |
| T9.19 | \(\varphi(x,y)\) | T9.16、T9.17，对公式 \(\varphi\) 使用两次 \(=\!Sub\) |
| T9.20 | \(x\in E\land\varphi(x,y)\) | T9.18、T9.19，\(\land I\) |
| T9.21 | \(x\in E\land\varphi(x,y)\) | 关闭 \(\mathfrak a\)，依次两个 \(\exists E\)；结论不含 \(a,b\) |
| T9.22 | \(w\in F_0\to(x\in E\land\varphi(x,y))\) | 关闭 \(\mathfrak m\)，\(\to I\) |
| T9.23 | \([x\in E\land\varphi(x,y)]^{\mathfrak n}\) | 在 \(\mathfrak k\) 内开启反向 \(\to I\) 子证明 |
| T9.24 | \(\Xi(w,E)\) | T9.23、T9.13，以 \(x,y\) 为 D17 的存在见证，\(\exists I\) |
| T9.25 | \(w\in F_0\) | T9.12、D18、T9.24，\(\forall E,\leftrightarrow E_2,\to E\) |
| T9.26 | \((x\in E\land\varphi(x,y))\to w\in F_0\) | 关闭 \(\mathfrak n\)，\(\to I\) |
| T9.27 | \(w\in F_0\leftrightarrow(x\in E\land\varphi(x,y))\) | T9.22、T9.26，\(\leftrightarrow I\) |
| T9.28 | \(K(w,x,y)\to[w\in F_0\leftrightarrow(x\in E\land\varphi(x,y))]\) | 关闭 \(\mathfrak k\)，\(\to I\) |
| T9.29 | \(\forall w\forall x\forall y\{K(w,x,y)\to[w\in F_0\leftrightarrow(x\in E\land\varphi(x,y))]\}\) | T9.28，依次 \(\forall I\) |

---

## 10. 校验函数性质

### 10.1 关系性

| 步骤 | 严格公式 | 纯底层公理/推理规则及代入说明 |
|---:|---|---|
| T10.1 | \([w\in F_0]^{\alpha_1}\) | 开启 \(\to I\) 子证明 |
| T10.2 | \(\Xi(w,E)\) | T9.12、D18、T10.1，\(\forall E,\leftrightarrow E_1,\to E\) |
| T10.3 | \([x\in E\land\varphi(x,y)\land K(w,x,y)]^{\alpha_{1a}}\) | T10.2、D17，依次两个 \(\exists E\)，取新鲜 \(x,y\)，合并标记子证明 \(\alpha_{1a}\) |
| T10.4 | \(K(w,x,y)\) | T10.3，\(\land E_2\) |
| T10.5 | \(\exists x\exists y\,K(w,x,y)\) | T10.4，依次 \(\exists I\) |
| T10.6 | \(\exists x\exists y\,K(w,x,y)\) | 关闭 \(\alpha_{1a}\)，依次两个 \(\exists E\) |
| T10.7 | \(w\in F_0\to\exists x\exists y\,K(w,x,y)\) | 关闭 \(\alpha_1\)，\(\to I\) |
| T10.8 | \(\operatorname{Rel}(F_0)\) | T10.7，\(\forall I\)，D4 |

### 10.2 单值性

| 步骤 | 严格公式 | 纯底层公理/推理规则及代入说明 |
|---:|---|---|
| T10.9 | \([\bigl(w_1\in F_0\land K(w_1,x,y_1)\bigr)\land\bigl(w_2\in F_0\land K(w_2,x,y_2)\bigr)]^{\alpha_2}\) | 开启 \(\to I\) 子证明；分组与 D5 完全一致 |
| T10.10 | \(x\in E\land\varphi(x,y_1)\) | T10.9、T9.29 的实例，\(\land E,\forall E,\to E,\leftrightarrow E_1\) |
| T10.11 | \(x\in E\land\varphi(x,y_2)\) | T10.9、T9.29 的实例，\(\land E,\forall E,\to E,\leftrightarrow E_1\) |
| T10.12 | \(x\in E\) | T10.10，\(\land E_1\) |
| T10.13 | \(\exists y_0[\varphi(x,y_0)\land\forall z(\varphi(x,z)\to y_0=z)]\) | T8.1、H，\(\forall E\) 代入 \(x\)，再与 T10.12 使用 \(\to E\) |
| T10.14 | \([\varphi(x,y_0)\land\forall z(\varphi(x,z)\to y_0=z)]^{\alpha_3}\) | 对 T10.13 开启 \(\exists E\) 子证明；\(y_0\) 新鲜 |
| T10.15 | \(\varphi(x,y_1)\) | T10.10，\(\land E_2\) |
| T10.16 | \(\varphi(x,y_1)\to y_0=y_1\) | T10.14，\(\land E_2,\forall E\)，代入 \(z:=y_1\) |
| T10.17 | \(y_0=y_1\) | T10.15、T10.16，\(\to E\) |
| T10.18 | \(\varphi(x,y_2)\) | T10.11，\(\land E_2\) |
| T10.19 | \(\varphi(x,y_2)\to y_0=y_2\) | T10.14，\(\land E_2,\forall E\)，代入 \(z:=y_2\) |
| T10.20 | \(y_0=y_2\) | T10.18、T10.19，\(\to E\) |
| T10.21 | \(y_1=y_2\) | T10.17、T10.20，\(=\!Sym,=\!Trans\) |
| T10.22 | \(y_1=y_2\) | T10.13 与子证明 \(\alpha_3\) 的 T10.14–T10.21，关闭 \(\alpha_3\)，\(\exists E\) |
| T10.23 | \((\bigl(w_1\in F_0\land K(w_1,x,y_1)\bigr)\land\bigl(w_2\in F_0\land K(w_2,x,y_2)\bigr))\to y_1=y_2\) | 关闭 \(\alpha_2\)，\(\to I\) |
| T10.24 | \(\operatorname{SV}(F_0)\) | T10.23，依次 \(\forall I\)，D5 |
| T10.25 | \(\operatorname{Fun}(F_0)\) | T10.8、T10.24，\(\land I\)，D6 |

### 10.3 定义域

| 步骤 | 严格公式 | 纯底层公理/推理规则及代入说明 |
|---:|---|---|
| T10.26 | \([\exists w\exists y(w\in F_0\land K(w,x,y))]^{\beta_1}\) | 开启正向 \(\to I\) 子证明 |
| T10.27 | \([w\in F_0\land K(w,x,y)]^{\beta_{1a}}\) | T10.26，依次两个 \(\exists E\)，取新鲜 \(w,y\)，合并标记子证明 \(\beta_{1a}\) |
| T10.28 | \(x\in E\land\varphi(x,y)\) | T10.27、T9.29，\(\forall E,\to E,\leftrightarrow E_1,\to E\) |
| T10.29 | \(x\in E\) | T10.28，\(\land E_1\) |
| T10.30 | \(x\in E\) | 关闭 \(\beta_{1a}\)，依次两个 \(\exists E\) |
| T10.31 | \((\exists w\exists y(w\in F_0\land K(w,x,y)))\to x\in E\) | 关闭 \(\beta_1\)，\(\to I\) |
| T10.32 | \([x\in E]^{\beta_2}\) | 开启反向 \(\to I\) 子证明 |
| T10.33 | \(\exists y[\varphi(x,y)\land\forall z(\varphi(x,z)\to y=z)]\) | T8.1、H，\(\forall E\) 后与 T10.32 使用 \(\to E\) |
| T10.34 | \([\varphi(x,y)\land\forall z(\varphi(x,z)\to y=z)]^{\beta_3}\) | 对 T10.33 开启 \(\exists E\) 子证明；\(y\) 新鲜 |
| T10.35 | \(\varphi(x,y)\) | T10.34，\(\land E_1\) |
| T10.36 | \(\exists w\,K(w,x,y)\) | 引理 K1 的存在部分，\(\forall E\) 代入 \(x,y\) |
| T10.37 | \([K(w,x,y)]^{\beta_4}\) | 对 T10.36 开启 \(\exists E\) 子证明；\(w\) 新鲜 |
| T10.38 | \(w\in F_0\leftrightarrow(x\in E\land\varphi(x,y))\) | T9.29，\(\forall E\) 后与 T10.37 使用 \(\to E\) |
| T10.39 | \(x\in E\land\varphi(x,y)\) | T10.32、T10.35，\(\land I\) |
| T10.40 | \(w\in F_0\) | T10.38、T10.39，\(\leftrightarrow E_2,\to E\) |
| T10.41 | \(w\in F_0\land K(w,x,y)\) | T10.40、T10.37，\(\land I\) |
| T10.42 | \(\exists w\exists y(w\in F_0\land K(w,x,y))\) | T10.41，依次 \(\exists I\) |
| T10.43 | \(\exists w\exists y(w\in F_0\land K(w,x,y))\) | T10.36 与子证明 \(\beta_4\) 的 T10.37–T10.42，关闭 \(\beta_4\)，\(\exists E\) |
| T10.44 | \(\exists w\exists y(w\in F_0\land K(w,x,y))\) | T10.33 与子证明 \(\beta_3\) 的 T10.34–T10.43，关闭 \(\beta_3\)，\(\exists E\) |
| T10.45 | \(x\in E\to\exists w\exists y(w\in F_0\land K(w,x,y))\) | 关闭 \(\beta_2\)，\(\to I\) |
| T10.46 | \(x\in E\leftrightarrow\exists w\exists y(w\in F_0\land K(w,x,y))\) | T10.45、T10.31，\(\leftrightarrow I\) |
| T10.47 | \(\operatorname{Dom}(F_0,E)\) | T10.46，\(\forall I\)，D7 |

### 10.4 值域

| 步骤 | 严格公式 | 纯底层公理/推理规则及代入说明 |
|---:|---|---|
| T10.48 | \([\exists w\exists x(w\in F_0\land K(w,x,y))]^{\gamma_1}\) | 开启正向 \(\to I\) 子证明 |
| T10.49 | \([w\in F_0\land K(w,x,y)]^{\gamma_{1a}}\) | T10.48，依次两个 \(\exists E\)，取新鲜 \(w,x\)，合并标记子证明 \(\gamma_{1a}\) |
| T10.50 | \(x\in E\land\varphi(x,y)\) | T10.49、T9.29，\(\forall E,\to E,\leftrightarrow E_1,\to E\) |
| T10.51 | \(\exists x(x\in E\land\varphi(x,y))\) | T10.50，\(\exists I\) |
| T10.52 | \(y\in R_0\) | T8.18、D15、T10.51，\(\forall E,\leftrightarrow E_2,\to E\) |
| T10.53 | \(y\in R_0\) | 关闭 \(\gamma_{1a}\)，依次两个 \(\exists E\) |
| T10.54 | \((\exists w\exists x(w\in F_0\land K(w,x,y)))\to y\in R_0\) | 关闭 \(\gamma_1\)，\(\to I\) |
| T10.55 | \([y\in R_0]^{\gamma_2}\) | 开启反向 \(\to I\) 子证明 |
| T10.56 | \(\exists x(x\in E\land\varphi(x,y))\) | T8.18、D15、T10.55，\(\forall E,\leftrightarrow E_1,\to E\) |
| T10.57 | \([x\in E\land\varphi(x,y)]^{\gamma_3}\) | 对 T10.56 开启 \(\exists E\) 子证明；\(x\) 新鲜 |
| T10.58 | \(\exists w\,K(w,x,y)\) | 引理 K1 的存在部分，\(\forall E\) 代入 \(x,y\) |
| T10.59 | \([K(w,x,y)]^{\gamma_4}\) | 对 T10.58 开启 \(\exists E\) 子证明；\(w\) 新鲜 |
| T10.60 | \(w\in F_0\leftrightarrow(x\in E\land\varphi(x,y))\) | T9.29，\(\forall E\) 后与 T10.59 使用 \(\to E\) |
| T10.61 | \(w\in F_0\) | T10.60、T10.57，\(\leftrightarrow E_2,\to E\) |
| T10.62 | \(w\in F_0\land K(w,x,y)\) | T10.61、T10.59，\(\land I\) |
| T10.63 | \(\exists w\exists x(w\in F_0\land K(w,x,y))\) | T10.62，依次 \(\exists I\) |
| T10.64 | \(\exists w\exists x(w\in F_0\land K(w,x,y))\) | T10.58 与子证明 \(\gamma_4\) 的 T10.59–T10.63，关闭 \(\gamma_4\)，\(\exists E\) |
| T10.65 | \(\exists w\exists x(w\in F_0\land K(w,x,y))\) | T10.56 与子证明 \(\gamma_3\) 的 T10.57–T10.64，关闭 \(\gamma_3\)，\(\exists E\) |
| T10.66 | \(y\in R_0\to\exists w\exists x(w\in F_0\land K(w,x,y))\) | 关闭 \(\gamma_2\)，\(\to I\) |
| T10.67 | \(y\in R_0\leftrightarrow\exists w\exists x(w\in F_0\land K(w,x,y))\) | T10.66、T10.54，\(\leftrightarrow I\) |
| T10.68 | \(\operatorname{Ran}(F_0,R_0)\) | T10.67，\(\forall I\)，D8 |

### 10.5 值满足性

| 步骤 | 严格公式 | 纯底层公理/推理规则及代入说明 |
|---:|---|---|
| T10.69 | \([w\in F_0\land K(w,x,y)]^{\delta_1}\) | 开启 \(\to I\) 子证明 |
| T10.70 | \(w\in F_0\leftrightarrow(x\in E\land\varphi(x,y))\) | T9.29 与 T10.69 中的 \(K\)，\(\forall E,\to E\) |
| T10.71 | \(x\in E\land\varphi(x,y)\) | T10.69 中的 \(w\in F_0\) 与 T10.70，\(\leftrightarrow E_1,\to E\) |
| T10.72 | \(\varphi(x,y)\) | T10.71，\(\land E_2\) |
| T10.73 | \(w\in F_0\land K(w,x,y)\to\varphi(x,y)\) | 关闭 \(\delta_1\)，\(\to I\) |
| T10.74 | \(\operatorname{Sat}_{\varphi}(F_0)\) | T10.73，依次 \(\forall I\)，D9 |
| T10.75 | \(\operatorname{Real}_{\varphi}(F_0,E)\) | T10.25、T10.47、T10.74，依次 \(\land I\)，D10 |

---

## 11. 唯一性

### 11.1 精确图像的唯一性

| 步骤 | 严格公式 | 纯底层公理/推理规则及代入说明 |
|---:|---|---|
| T11.1 | \([\operatorname{Graph}_{\varphi}(G,E)]^{\epsilon_1}\) | 开启 \(\to I\) 子证明 |
| T11.2 | \(w\in F_0\leftrightarrow\Xi(w,E)\) | T9.12、D18，\(\forall E\) |
| T11.3 | \(w\in G\leftrightarrow\Xi(w,E)\) | T11.1、D18，\(\forall E\) |
| T11.4 | \(w\in F_0\to w\in G\) | 假设 \(w\in F_0\)；T11.2 正向得 \(\Xi(w,E)\)，T11.3 反向得 \(w\in G\)；关闭假设，\(\to I\) |
| T11.5 | \(w\in G\to w\in F_0\) | 假设 \(w\in G\)；T11.3 正向得 \(\Xi(w,E)\)，T11.2 反向得 \(w\in F_0\)；关闭假设，\(\to I\) |
| T11.6 | \(w\in F_0\leftrightarrow w\in G\) | T11.4、T11.5，\(\leftrightarrow I\) |
| T11.7 | \(\forall w(w\in F_0\leftrightarrow w\in G)\) | T11.6，\(\forall I\) |
| T11.8 | \(F_0=G\) | T11.7，外延公理，\(\to E\) |
| T11.9 | \(G=F_0\) | T11.8，\(=\!Sym\) |
| T11.10 | \(\operatorname{Graph}_{\varphi}(G,E)\to G=F_0\) | 关闭 \(\epsilon_1\)，\(\to I\) |
| T11.11 | \(\forall G[\operatorname{Graph}_{\varphi}(G,E)\to G=F_0]\) | T11.10，\(\forall I\) |

### 11.2 任意实现函数都具有精确图像

在主前提 \(H_{\varphi}(E)\) 下证明：

\[
\operatorname{Real}_{\varphi}(G,E)\to
\operatorname{Graph}_{\varphi}(G,E).
\tag{R2G}
\]

| 步骤 | 严格公式 | 纯底层公理/推理规则及代入说明 |
|---:|---|---|
| T11.12 | \([\operatorname{Real}_{\varphi}(G,E)]^{\epsilon_2}\) | 开启 \(\to I\) 子证明 |
| T11.13 | \([w\in G]^{\epsilon_3}\) | 开启 \(w\in G\to\Xi(w,E)\) 子证明 |
| T11.14 | \(\operatorname{Rel}(G)\) | T11.12、D10、D6，\(\land E\) |
| T11.15 | \(\exists x\exists y\,K(w,x,y)\) | T11.14、D4、T11.13，\(\forall E,\to E\) |
| T11.16 | \([K(w,x,y)]^{\epsilon_4}\) | T11.15，依次两个 \(\exists E\)，取新鲜 \(x,y\) |
| T11.17 | \(\exists u\exists z(u\in G\land K(u,x,z))\) | 以 \(u:=w,z:=y\) 为见证，由 T11.13、T11.16，\(\land I,\exists I\) |
| T11.18 | \(x\in E\) | T11.12、D10、D7、T11.17，\(\land E,\forall E,\leftrightarrow E_2,\to E\) |
| T11.19 | \(\varphi(x,y)\) | T11.12、D10、D9、T11.13、T11.16，\(\land E,\forall E,\to E\) |
| T11.20 | \(\Xi(w,E)\) | T11.18、T11.19、T11.16，以 \(x,y\) 为 D17 见证，\(\exists I\) |
| T11.21 | \(\Xi(w,E)\) | 关闭 T11.16 中两个 \(\exists E\) 子证明 |
| T11.22 | \(w\in G\to\Xi(w,E)\) | 关闭 \(\epsilon_3\)，\(\to I\) |
| T11.23 | \([\Xi(w,E)]^{\epsilon_5}\) | 开启 \(\Xi(w,E)\to w\in G\) 子证明 |
| T11.24 | \([x\in E\land\varphi(x,y)\land K(w,x,y)]^{\epsilon_6}\) | T11.23、D17，依次两个 \(\exists E\)，取新鲜 \(x,y\) |
| T11.25 | \(\exists u\exists z(u\in G\land K(u,x,z))\) | T11.12、D10、D7 与 T11.24 中 \(x\in E\)，\(\forall E,\leftrightarrow E_1,\to E\) |
| T11.26 | \([u\in G\land K(u,x,z)]^{\epsilon_7}\) | T11.25，依次两个 \(\exists E\)，取新鲜 \(u,z\) |
| T11.27 | \(\varphi(x,z)\) | T11.12、D10、D9、T11.26，\(\land E,\forall E,\to E\) |
| T11.28 | \(\varphi(x,y)\) | T11.24，\(\land E\) |
| T11.29 | \(\exists y_0[\varphi(x,y_0)\land\forall q(\varphi(x,q)\to y_0=q)]\) | T8.1、H 与 T11.24 中 \(x\in E\)，\(\forall E,\to E\)；束缚变量改名为新鲜 \(q\) |
| T11.30a | \([\varphi(x,y_0)\land\forall q(\varphi(x,q)\to y_0=q)]^{\epsilon_8}\) | 对 T11.29 开启 \(\exists E\) 子证明；\(y_0\) 新鲜 |
| T11.30b | \(\forall q(\varphi(x,q)\to y_0=q)\) | T11.30a，\(\land E_2\) |
| T11.30c | \(\varphi(x,y)\to y_0=y\) | T11.30b，\(\forall E\)，代入 \(q:=y\) |
| T11.30d | \(y_0=y\) | T11.28、T11.30c，\(\to E\) |
| T11.30e | \(\varphi(x,z)\to y_0=z\) | T11.30b，\(\forall E\)，代入 \(q:=z\) |
| T11.30f | \(y_0=z\) | T11.27、T11.30e，\(\to E\) |
| T11.30g | \(y=z\) | T11.30d、T11.30f，\(=\!Sym,=\!Trans\) |
| T11.30h | \(y=z\) | T11.29 与子证明 \(\epsilon_8\) 的 T11.30a–T11.30g，关闭 \(\epsilon_8\)，\(\exists E\) |
| T11.31 | \(K(u,x,y)\) | T11.26 中的 \(K(u,x,z)\) 与 T11.30h，\(=\!Sub\) |
| T11.32 | \(w=u\) | T11.24 中的 \(K(w,x,y)\)、T11.31 与引理 K1 的固定坐标唯一性 |
| T11.33 | \(w\in G\) | T11.26 中 \(u\in G\) 与 T11.32，\(=\!Sub\) |
| T11.34 | \(w\in G\) | 关闭 T11.26 中两个 \(\exists E\) 子证明 |
| T11.35 | \(w\in G\) | 关闭 T11.24 中两个 \(\exists E\) 子证明 |
| T11.36 | \(\Xi(w,E)\to w\in G\) | 关闭 \(\epsilon_5\)，\(\to I\) |
| T11.37 | \(w\in G\leftrightarrow\Xi(w,E)\) | T11.22、T11.36，\(\leftrightarrow I\) |
| T11.38 | \(\operatorname{Graph}_{\varphi}(G,E)\) | T11.37，\(\forall I\)，D18 |
| T11.39 | \(\operatorname{Real}_{\varphi}(G,E)\to\operatorname{Graph}_{\varphi}(G,E)\) | 关闭 \(\epsilon_2\)，\(\to I\) |

由 T11.39 与 T11.11：

| 步骤 | 严格公式 | 纯底层公理/推理规则及代入说明 |
|---:|---|---|
| T11.40 | \(\operatorname{Real}_{\varphi}(G,E)\to\operatorname{Graph}_{\varphi}(G,E)\) | T11.39 |
| T11.41 | \(\operatorname{Graph}_{\varphi}(G,E)\to G=F_0\) | T11.10 |
| T11.42 | \(\operatorname{Real}_{\varphi}(G,E)\to G=F_0\) | 假设 Real；T11.40、T11.41 两次 \(\to E\)；再关闭假设，\(\to I\) |
| T11.43 | \(\forall G[\operatorname{Real}_{\varphi}(G,E)\to G=F_0]\) | T11.42，\(\forall I\) |
| T11.44 | \(\operatorname{Real}_{\varphi}(F_0,E)\land\forall G[\operatorname{Real}_{\varphi}(G,E)\to G=F_0]\) | T10.75、T11.43，\(\land I\) |

---

## 12. 所有存在见证的最终闭合

这一节专门检查主证明中 \(R_0,C_0,F_0\) 的作用域，避免把存在见证误当成全局常元。

令

\[
\Omega(F,E):\!\!\iff
\operatorname{Real}_{\varphi}(F,E)
\land
\bigl(\forall G[\operatorname{Real}_{\varphi}(G,E)\to G=F]\bigr).
\tag{D19}
\]

| 步骤 | 严格公式 | 纯底层公理/推理规则及代入说明 |
|---:|---|---|
| T12.1 | \(\Omega(F_0,E)\) | T11.44，D19 |
| T12.2 | \(\exists F\,\Omega(F,E)\) | T12.1，\(\exists I\)，见证 \(F_0\) |
| T12.3 | \(\exists F\,\Omega(F,E)\) | T9.3 与子证明 \(\mathfrak f\) 的 T9.4–T12.2，关闭 \(\mathfrak f\)，\(\exists E\)；结论不含 \(F_0\) |
| T12.4 | \(\exists F\,\Omega(F,E)\) | T9.1 与子证明 \(\mathfrak c\) 的 T9.2–T12.3，关闭 \(\mathfrak c\)，\(\exists E\)；结论不含 \(C_0\) |
| T12.5 | \(\exists F\,\Omega(F,E)\) | T8.3 与子证明 \(\mathfrak r\) 的 T8.18–T12.4，关闭 \(\mathfrak r\)，\(\exists E\)；结论不含 \(R_0\) |
| T12.6 | \(H_{\varphi}(E)\to\exists F\,\Omega(F,E)\) | 关闭主假设 \(\mathfrak h\)，\(\to I\) |
| T12.7 | \(\forall E[H_{\varphi}(E)\to\exists F\,\Omega(F,E)]\) | T12.6，\(\forall I\)；此时没有含 \(E\) 的未解除假设 |

T12.7 就是定理 (T)。所有构造中的辅助见证 \(s,d,w,A_0,U_0,V_0,W_0,C_0,R_0,F_0\) 均已在相应子证明中关闭。

---

## 13. 纯一阶性检查

最终闭式 T12.7 中出现的符号

\[
H_{\varphi},\quad
\Omega,\quad
\operatorname{Real}_{\varphi},\quad
\operatorname{Fun},\quad
\operatorname{Rel},\quad
\operatorname{SV},\quad
\operatorname{Dom},\quad
\operatorname{Sat}_{\varphi},\quad
K
\]

全部已经在 D1–D10、D19 中给出右侧定义。按定义从外到内机械替换后，T12.7 只含：

\[
\in,\ =,\ \land,\ \lor,\ \to,\ \leftrightarrow,\ \forall,\ \exists
\]

以及固定公式 \(\varphi(x,y)\) 内原有的逻辑符号；不存在自由变量、函数项 \(F(x)\)、未约束的额外参数或对象语言中的“公式量词” \(\forall\varphi\)。若把 \(\leftrightarrow\) 再展开为两个蕴含的合取，则非逻辑符号只剩 \(\in,=\)。

---

## 14. 空集边界校验

若 \(E\) 无元素，即 \(\forall x\,\neg(x\in E)\)，则 H 中每个蕴含式的前件 \(x\in E\) 为假，故 H 成立。D15 推出精确像集 \(R_0\) 无元素；D18 推出 \(F_0\) 无元素。空关系满足关系性和单值性，其定义域也是无元素的集合，故仍满足定理。证明中只在已经假设 \(x\in E\) 后使用 H 取得 \(y\)，因此没有在此边界情形非法选取见证。

---

## 15. 五轮审校记录

| 轮次 | 校验对象 | 校验结果 |
|---:|---|---|
| 1 | 语法、自由变量和量词闭包 | 未引入额外自由参数；固定 \(\operatorname{FV}(\varphi)\subseteq\{x,y\}\)；最终只对 \(E,F,G\) 等对象变量量化 |
| 2 | 逻辑演算与子证明作用域 | 已固定 \(\mathrm{ND}_{=}\)；主构造见证及有序对见证均标注新鲜条件；T12 显式逐层关闭 \(F_0,C_0,R_0\) |
| 3 | ZF 公理模式实例 | 已明确采用精确像替换形式；两次分离均有既存母集；输出集合变量不自由出现于筛选公式；实际实例使用展开后的纯公式 |
| 4 | 函数性质与唯一性 | 已证明关系性、单值性、定义域、值域和值满足性；又证明任何实现函数具有同一精确图像，外延公理给出唯一性 |
| 5 | 风格、术语和边界 | 采用稳定步骤号与三栏表；区分像集、值域和陪域；不使用函数项 \(F(x)\)；空集边界通过 |

因此，在本文明确声明的形式演算 \(\mathrm{ND}_{=}+ZF\) 下，定理 \(\mathrm{(T)}\) 的集合论构造、量词作用域、函数性质和唯一性均已闭合。
