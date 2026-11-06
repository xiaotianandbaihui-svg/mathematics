# 分割与细度滤基：ZF 中可递归展开的定义与证明

> 符号风格参照《从唯一存在关系到唯一函数：ZF 严格证明》：对象语言为带等词的纯集合论语言；定义符号均为元语言缩写；所有量词均无界，取值范围写进公式；证明区分对象变量、存在见证及其作用域。本文以“与某个自然数存在双射”定义有限，构造“细度小于正阈值”的滤基。第 1 节集中展示定义，可单独阅读。原参考文件不属于本文的修改对象。

## 1. 可单独阅读的定义集中区

本节集中给出“有限、分割、细度条件、分割滤基”的正式定义，不依赖后文证明的阅读顺序。符号都是可递归展开的公式缩写；第 3 节给出基础编码，第 4 节起给出证明。所有量词均在全体集合上取值，取值条件写在括号内。

### 1.1 固定对象与成员层次

固定实数的集合编码：\(R\) 表示实数载体，\(L\) 表示严格小于关系的图，\(M\) 表示加法关系的图，\(o\) 表示加法零元。固定端点 \(a,b\)，满足 \(a<b\)。这些都是集合变量，最终在主定理中被量化；实数结构所需的完整假设在第 5 节展开。

| 符号 | 在本节中的读法 | 底层定义 |
|---|---|---|
| \(K(w,x,y)\) | \(w\) 是有序对“\(x,y\)”的集合编码 | D11 |
| \(\operatorname{At}(L,x,y)\) | 该有序对属于 \(L\)，即 \(x<y\) | D12 |
| \(\operatorname{Tri}(M,x,y,z)\) | 加法图记录“\(x+y=z\)” | D13 |
| \(\operatorname{Nat}(n)\) | \(n\) 是 von Neumann 自然数 | N1–N4 |
| \(\operatorname{Bij}(F,p,n)\) | \(F\) 是从 \(p\) 到 \(n\) 的双射图 | N5–N6 |

理解成员关系时区分：\(x\) 是一个分点；\(U\) 是由分点组成的一个分割；\(V\) 是由一批分割组成的集合；\(X\) 收集全部分割；\(B\) 收集各正阈值对应的那些 \(V\)。

### 1.2 有限：与某个自然数存在双射

\[
\boxed{
\operatorname{Fin}(p):\!\!\iff
\exists n\exists F\bigl(\operatorname{Nat}(n)\land\operatorname{Bij}(F,p,n)\bigr).
}
\tag{D14}
\]

这里自然数本身是集合。为解释数量直觉，可以把起始几个自然数写成

\[
0=\varnothing,\qquad 1=\{0\},\qquad 2=\{0,1\},\qquad 3=\{0,1,2\}.
\]

这行是说明记号；正式定义中，空集、后继、自然数集合均由第 3.3 节的关系公式展开，不把这些记号作为原始常量或函数项。

“\(F\) 是 \(p\) 到 \(n\) 的双射”要求：\(p\) 中每个元素恰好对应 \(n\) 中一个元素；不同元素对应不同元素；\(n\) 中的每个元素都被对应到。例如，存在到 \(3\) 的双射，就表达“恰有三个元素”。完整的函数图、单值、单射、满射条件在 N5–N6 中逐项写出。

本文采用这一基于数量的双射定义作为有限性的基本定义。分割的定义只要求这样的双射存在，不把某一双射作为分割的一部分，也不要求给分点预先选定编号。

### 1.3 非严格次序与正阈值

\[
\operatorname{LE}(R,L,x,y):\!\!\iff
((x\in R\land y\in R)\land(x=y\lor\operatorname{At}(L,x,y))).
\tag{D15}
\]

\[
\operatorname{Positive}(R,L,o,d):\!\!\iff
(d\in R\land\operatorname{At}(L,o,d)).
\tag{D16}
\]

`LE` 表示两个对象都是实数，且前者小于或等于后者；`Positive` 表示阈值是实数并严格大于零元。

### 1.4 区间、一个分割及全部分割

\[
\operatorname{Interval}(I,R,L,a,b):\!\!\iff
\forall x\bigl(x\in I\leftrightarrow
((x\in R\land\operatorname{LE}(R,L,a,x))\land\operatorname{LE}(R,L,x,b))\bigr).
\tag{D26}
\]

\[
\boxed{
\begin{aligned}
\operatorname{Part}(U,R,L,a,b):\!\!\iff{}&
\operatorname{Fin}(U)\land\operatorname{LE}(R,L,a,b)
\\&\land a\in U\land b\in U
\\&\land\forall x\bigl(x\in U\to
(\operatorname{LE}(R,L,a,x)\land\operatorname{LE}(R,L,x,b))\bigr).
\end{aligned}
}
\tag{D27}
\]

\[
\operatorname{Space}(X,R,L,a,b):\!\!\iff
\forall U\,(U\in X\leftrightarrow\operatorname{Part}(U,R,L,a,b)).
\tag{D28}
\]

依次表示：\(I\) 恰好是闭区间；\(U\) 是有限的分点集合、包含两个端点且全部位于区间内；\(X\) 恰好收集这些 \(U\)。D27 中的 `Fin` 就是 D14 的双射定义。

主问题假设 \(a<b\)。为统一辅助证明，D27 也允许 \(a=b\)，此时分割是端点的单点集。

### 1.5 相邻分点与细度小于阈值

\[
\boxed{
\begin{aligned}
\operatorname{Adjacent}(U,L,x,y):\!\!\iff{}&
((x\in U\land y\in U)\land\operatorname{At}(L,x,y))
\\&\land\neg\exists z\bigl((z\in U\land\operatorname{At}(L,x,z))\land\operatorname{At}(L,z,y)\bigr).
\end{aligned}
}
\tag{D29}
\]

`Adjacent` 表示 \(x,y\) 是分割中的两个递增分点，且两者之间不存在该分割的其他分点。

\[
\operatorname{Gap}(L,M,x,y,d):\!\!\iff
\exists v\,(\operatorname{Tri}(M,x,d,v)\land\operatorname{At}(L,y,v)).
\tag{D30}
\]

`Gap` 表达 \(y<x+d\)，也就是 \(y-x<d\)。它通过加法关系的存在见证表达距离条件，没有使用减法函数项。

\[
\boxed{
\begin{aligned}
\operatorname{Fine}(U,R,L,M,a,b,d):\!\!\iff{}&
(\operatorname{Part}(U,R,L,a,b)\land d\in R)
\\&\land\forall x\forall y
(\operatorname{Adjacent}(U,L,x,y)\to\operatorname{Gap}(L,M,x,y,d)).
\end{aligned}
}
\tag{D31}
\]

`Fine` 表示 \(U\) 是分割，\(d\) 是实数，且任意两个相邻分点的距离都小于 \(d\)。非退化有限分割的最大相邻距离存在，所以这正是通常的“细度小于 \(d\)”；对应证明在第 10 节。

### 1.6 一个阈值集合与整个分割滤基

\[
\begin{aligned}
\operatorname{Slice}(V,X,R,L,M,a,b,d):\!\!\iff
\forall U\bigl(U\in V\leftrightarrow
(U\in X\land\operatorname{Fine}(U,R,L,M,a,b,d))\bigr).
\end{aligned}
\tag{D32}
\]

这表示 \(V\) 恰好由 \(X\) 中细度小于 \(d\) 的全部分割组成。

\[
\boxed{
\begin{aligned}
\operatorname{Family}(B,X,R,L,M,o,a,b):\!\!\iff
\forall V\Bigl(V\in B\leftrightarrow
\exists d\forall U\Bigl[&
\operatorname{Positive}(R,L,o,d)
\\&\land\bigl(U\in V\leftrightarrow
(U\in X\land\operatorname{Fine}(U,R,L,M,a,b,d))\bigr)
\Bigr]\Bigr).
\end{aligned}
}
\tag{D33}
\]

这是所要求的 \(\exists d\forall U(\cdots)\) 形式：对整个成员 \(V\) 先选定同一个正阈值，再判断哪些分割 \(U\) 属于它。\(B\) 恰好收集所有这样的 \(V\)。这里没有要求分割包含某些预先固定的内部分点。

### 1.7 一般滤基的定义

\[
\boxed{
\begin{aligned}
\operatorname{FilterBase}(B,X):\!\!\iff{}&
\forall V\bigl(V\in B\to\forall U(U\in V\to U\in X)\bigr)
\\&\land\exists V\,(V\in B)
\\&\land\forall V\bigl(V\in B\to\exists U(U\in V)\bigr)
\\&\land\forall V\forall W\Bigl((V\in B\land W\in B)\to
\exists T\bigl(T\in B\land\forall U(U\in T\to(U\in V\land U\in W))\bigr)\Bigr).
\end{aligned}
}
\tag{D34}
\]

四个合取项分别表示：每个成员是 \(X\) 的子集；\(B\) 本身非空；每个成员非空；任意两个成员的交集包含一个成员。D34 已经只含成员关系和逻辑符号。

本文证明：满足 D28、D33 的 \(X,B\) 确实存在，并且满足 D34。各集合的存在性在第 8 节，滤基性质的逐项证明在第 9 节。

### 1.8 可选的最大细度关系

\[
\boxed{
\begin{aligned}
\operatorname{Mesh}(U,R,L,M,a,b,m):\!\!\iff{}&
\operatorname{Part}(U,R,L,a,b)\land\operatorname{At}(L,a,b)\land m\in R
\\&\land\exists x\exists y
(\operatorname{Adjacent}(U,L,x,y)\land\operatorname{Tri}(M,x,m,y))
\\&\land\forall x\forall y\forall h
\Bigl((\operatorname{Adjacent}(U,L,x,y)\land\operatorname{Tri}(M,x,h,y))
\to\operatorname{LE}(R,L,h,m)\Bigr).
\end{aligned}
}
\tag{D35}
\]

`Mesh` 要求 \(m\) 本身是某一相邻间距，并且不小于任何相邻间距。它是关系公式；存在唯一性及它与 `Fine` 的等价性在第 10 节证明。

---

## 2. 语言、证明范围与展开约定

### 2.1 对象语言

\[
\mathcal L_{\in}=\{\in,=\}.
\]

所有对象变量都在全体集合上取值。原始对象语言没有函数符号、常量符号或额外谓词。式中 `Empty`、`Fin`、`Part` 等名称全部是下文给出右端公式的元语言缩写。

正式公式不使用有界量词，不使用唯一存在量词，不使用集合描述式作项，不使用下标表示取函数值。字母 \(o\) 是一个对象变量，稍后表示加法零元，不能与原始常量符号混淆。

定义展开时必须先将右端的束缚变量改成不与外部变量冲突的新鲜变量，再作避免捕获的代换。定义集中区先展示主要概念，其底层缩写在后文给出。依赖图无环，允许按引用逐层展开，不允许循环定义。有限多个合取省略内括号时按左结合解析；量词辖域由紧随其后的括号确定。

逻辑符号允许使用 \(\neg,\land,\lor,\to,\leftrightarrow,\forall,\exists\)。若还要压缩逻辑基底，则采用

\[
(P\land Q)\equiv\neg(P\to\neg Q),\qquad
(P\lor Q)\equiv(\neg P\to Q),
\]
\[
(P\leftrightarrow Q)\equiv((P\to Q)\land(Q\to P)),\qquad
\exists x\,P\equiv\neg\forall x\,\neg P.
\]

这里 \(P,Q\) 是元语言中的公式占位符，不是对象语言中的变量。因此最终可只保留原子式 \(x\in y,x=y\)，以及 \(\neg,\to,\forall\) 和括号。

### 2.2 实数的序与加法也必须有集合编码

只展开“有限”，却把 \(x<y\)、\(x+\delta\)、\(\|U\|\) 留作未解释的原始符号，不能得到纯 \(\{\in,=\}\)-语言。

本文使用四个集合参数：

| 参数 | 数学解释 | 正式地位 |
|---|---|---|
| \(R\) | 实数的载体集合 | 对象变量 |
| \(L\) | 严格小于关系的图 | 对象变量；其成员为有序对编码 |
| \(M\) | 加法关系的图 | 对象变量；其成员编码“两个输入、一个输出” |
| \(o\) | 加法零元 | 对象变量 |

第 5 节把所需的“非平凡、稠密、Dedekind 完备的线性有序交换群”条件全部写成纯集合论公式的缩写。主定理对所有满足这些条件的 \(R,L,M,o\) 成立；取通常实数的序加结构，就是所需结论。

这是一条关于集合编码结构的闭合条件定理。本文不另行从自然数、整数、有理数重建某一种特定的实数编码；也不引入未定义的 `RealField` 谓词。结构参数及其全部假设都出现在最终闭式中。

证明任意细分割存在时使用上确界法。这样不必把自然数倍、除法、取整或编号序列作为额外的未展开函数项。

### 2.3 演算与依据栏

采用带等词的经典一阶自然演绎 \(\mathrm{ND}_{=}\) 加 ZF。使用合取、析取、蕴含、双条件、全称量词、存在量词的引入与消去，等词自反性及代换，以及经典否定规则。对称性、传递性、命题逻辑重排均是这些规则的派生规则。

- 全称引入：被推广变量不能自由出现于未解除的假设。
- 存在消去：见证必须新鲜，不能出现在消去后的结论或无关的未解除假设中。
- 分离：新输出集合变量不能自由出现于筛选公式。
- 表中“定义展开／折回”是元语言操作，不是一条新增集合论公理。

证明表是带有已证引理的自然演绎证明展开。一个单元格可能明确列出一段有限推导，不冒称为机器证明器逐条核验过的原始规则证书。

## 3. 基本集合编码

以下定义中的所有量词均为无界量词。

\[
\operatorname{Empty}(e):\!\!\iff\forall u\,\neg(u\in e).
\tag{D1}
\]

\[
\operatorname{NE}(p):\!\!\iff\exists u\,(u\in p).
\tag{D2}
\]

\[
\operatorname{Sub}(p,q):\!\!\iff
\forall u\,(u\in p\to u\in q).
\tag{D3}
\]

\[
\operatorname{Pow}(P,p):\!\!\iff
\forall u\,(u\in P\leftrightarrow\operatorname{Sub}(u,p)).
\tag{D4}
\]

\[
\operatorname{Sing}(s,x):\!\!\iff
\forall u\,(u\in s\leftrightarrow u=x).
\tag{D5}
\]

\[
\operatorname{Pair}(d,x,y):\!\!\iff
\forall u\,(u\in d\leftrightarrow(u=x\lor u=y)).
\tag{D6}
\]

\[
\operatorname{Adjoin}(t,s,x):\!\!\iff
\forall u\,(u\in t\leftrightarrow(u\in s\lor u=x)).
\tag{D7}
\]

\[
\operatorname{UnionTwo}(t,p,q):\!\!\iff
\forall u\,(u\in t\leftrightarrow(u\in p\lor u\in q)).
\tag{D8}
\]

\[
\operatorname{Inter}(t,p,q):\!\!\iff
\forall u\,(u\in t\leftrightarrow(u\in p\land u\in q)).
\tag{D9}
\]

\[
\operatorname{Remove}(t,p,x):\!\!\iff
\forall u\,(u\in t\leftrightarrow(u\in p\land\neg(u=x))).
\tag{D10}
\]

\[
K(w,x,y):\!\!\iff
\exists s\exists d\bigl((\operatorname{Sing}(s,x)
\land\operatorname{Pair}(d,x,y))\land\operatorname{Pair}(w,s,d)\bigr).
\tag{D11}
\]

\[
\operatorname{At}(F,x,y):\!\!\iff
\exists w\,(w\in F\land K(w,x,y)).
\tag{D12}
\]

\[
\operatorname{Tri}(M,x,y,z):\!\!\iff
\exists v\exists w\bigl((K(v,x,y)\land K(w,v,z))\land w\in M\bigr).
\tag{D13}
\]

因此 `At` 与 `Tri` 都是关系公式，绝不是 \(F(x)\) 一类函数项。

### 3.1 集合存在的依据

| 构造 | 存在依据 | 唯一性依据 |
|---|---|---|
| 空集 | 空集公理；或在任一既有集合上用恒假公式分离 | 外延 |
| 单点集、无序对 | 配对 | 外延 |
| `Adjoin`、`UnionTwo` | 单点集、配对与并集 | 外延 |
| `Inter`、`Remove` | 在已有集合上分离 | 外延 |
| `Pow` | 幂集 | 外延 |
| `K` | 三次配对 | 外延及内层编码唯一性 |

实际使用的分离模式为：对每个固定公式 \(\psi(u)\)，允许它带有已列出的集合参数，若新变量 \(B\) 不自由出现于 \(\psi\)，则

\[
\forall A\exists B\forall u
\bigl(u\in B\leftrightarrow(u\in A\land\psi(u))\bigr).
\tag{SEP}
\]

这是模式表示，不是对公式作对象语言量化；自由参数取全称闭包。后文每一次分离都会指出母集。没有无条件集合概括。

### 3.2 有序对编码的两个引理

\[
\forall x\forall y\exists w
\bigl(K(w,x,y)\land\forall v(K(v,x,y)\to v=w)\bigr).
\tag{K-Exist}
\]

\[
\forall w\forall x\forall y\forall u\forall v
\bigl((K(w,x,y)\land K(w,u,v))\to(x=u\land y=v)\bigr).
\tag{K-Inj}
\]

第一式由配对与外延得到。第二式的展开证明如下：

| 步骤 | 推导内容 | 依据 |
|---|---|---|
| K1 | 对两个 `K` 公式分别取新鲜见证 \(s,d,s',d'\) | 存在消去；分别满足单点集、内层无序对、外层无序对条件 |
| K2 | 对任意 \(r\)，\(\forall t(t\in w\to r\in t)\) 当且仅当 \(r=x\) | 外层成员仅为 \(s,d\)；\(x\) 属于二者；反向用 \(s\in w\) 与 `Sing` |
| K3 | 同一个条件也当且仅当 \(r=u\)，故 \(x=u\) | 对第二组见证重复 K2；代入 \(r=x\) |
| K4 | 对任意 \(r\)，\(r\in d\) 当且仅当 \(\exists t(t\in w\land r\in t)\) | 正向取 \(t=d\)；反向按 \(t=s\) 或 \(t=d\) 分支；\(s\) 的元素也属于 \(d\) |
| K5 | 对 \(d'\) 同样成立，因此 \(d=d'\) | K4 与外延 |
| K6 | 若 \(y=x\)，则 \(d\) 仅有元素 \(x\)，从 \(v\in d'=d\) 得 \(v=x=y\) | `Pair`、等词代换 |
| K7 | 若 \(\neg(y=x)\)，由 \(y\in d'=\{u,v\}\) 的成员公式和 \(u=x\) 得 \(y=v\) | 析取消去与否定消去；这里花括号仅是解释文字 |
| K8 | 得 \(x=u\land y=v\)，关闭全部存在见证与假设，再全称引入 | 两个分支覆盖经典排中律；结论不含辅助见证 |

### 3.3 自然数的集合论展开

后继通过“向一个集合添入它自身”定义：

\[
\operatorname{Succ}(s,n):\!\!\iff\operatorname{Adjoin}(s,n,n).
\tag{N1}
\]

归纳集包含空集，并对后继封闭：

\[
\begin{aligned}
\operatorname{Inductive}(I):\!\!\iff{}&
\exists e(\operatorname{Empty}(e)\land e\in I)
\\&\land\forall n\bigl(n\in I\to\exists s(\operatorname{Succ}(s,n)\land s\in I)\bigr).
\end{aligned}
\tag{N2}
\]

自然数集合是包含于每个归纳集的归纳集：

\[
\operatorname{Omega}(W):\!\!\iff
\operatorname{Inductive}(W)\land
\forall I(\operatorname{Inductive}(I)\to\operatorname{Sub}(W,I)).
\tag{N3}
\]

\[
\operatorname{Nat}(n):\!\!\iff
\exists W(\operatorname{Omega}(W)\land n\in W).
\tag{N4}
\]

N3 并没有写出“所有归纳集组成的集合”，也没有把真类当作集合取交。第 4.1 节从一个由无穷公理提供的归纳集出发，用分离证明这样的 \(W\) 存在唯一。

### 3.4 函数图与双射的展开

\[
\begin{aligned}
\operatorname{Map}(F,p,q):\!\!\iff{}&
\forall w\bigl(w\in F\to\exists x\exists y((x\in p\land y\in q)\land K(w,x,y))\bigr)
\\&\land\forall x\bigl(x\in p\to\exists y(y\in q\land\operatorname{At}(F,x,y))\bigr)
\\&\land\forall x\forall y\forall z
\bigl((\operatorname{At}(F,x,y)\land\operatorname{At}(F,x,z))\to y=z\bigr).
\end{aligned}
\tag{N5}
\]

三个条件依次是：图中每个成员都编码正确类型的有序对；定义域 \(p\) 内的每个输入都有输出；相同输入的输出唯一。第一条也排除了定义域外的输入、陪域外的输出以及非有序对的垃圾成员。

\[
\boxed{
\begin{aligned}
\operatorname{Bij}(F,p,q):\!\!\iff{}&\operatorname{Map}(F,p,q)
\\&\land\forall x\forall y\forall z
\bigl((\operatorname{At}(F,x,z)\land\operatorname{At}(F,y,z))\to x=y\bigr)
\\&\land\forall y\bigl(y\in q\to\exists x(x\in p\land\operatorname{At}(F,x,y))\bigr).
\end{aligned}
}
\tag{N6}
\]

后两个合取项分别是单射性与满射性。把 N6、N5、N4、N3、N2、N1 和 D1–D13 递归代入 D14，便得到只含 \(\in,=\) 和逻辑符号的有限性公式。所有参数都被量词或 D14 的参数 \(p\) 约束，没有使用“有限的自然数”来循环定义有限。

### 3.5 新增的 ZF 公理使用

无穷公理采用存在归纳集的形式：

\[
\exists I\,\operatorname{Inductive}(I).
\tag{Infinity}
\]

本篇还用正则公理推出没有集合属于自身。所用形式为

\[
\forall S\Bigl(\operatorname{NE}(S)\to
\exists x\bigl(x\in S\land\forall y(y\in x\to\neg(y\in S))\bigr)\Bigr).
\tag{Foundation}
\]

两式中的缩写均已定义。证明过程中仍然不使用选择公理。

## 4. 基于双射的有限性：基础引理与证明

本节始终以第 1.2 节的 D14 为定义：存在一个自然数 \(n\)，并存在从待测集合到 \(n\) 的双射。归纳原则是从这个定义推出的证明工具。

### 4.1 自然数集合存在唯一，并满足归纳原则

由无穷公理取新鲜归纳集 \(J\)。在 \(J\) 上使用分离，得到新鲜集合 \(W\)，满足

\[
\forall n\Bigl(n\in W\leftrightarrow
\bigl(n\in J\land\forall I(\operatorname{Inductive}(I)\to n\in I)\bigr)\Bigr).
\tag{Omega-Construct}
\]

逐项验证 N3：

| 步骤 | 推导 | 依据 |
|---|---|---|
| O1 | 空集属于 \(J\)，也属于每一个归纳集 | N2；不同的空集见证由外延相等 |
| O2 | 空集属于 \(W\) | Omega-Construct |
| O3 | 假设 \(n\in W\)，取满足 `Succ(s,n)` 的 \(s\) | 配对、并集及 D7、N1；\(s\) 新鲜 |
| O4 | \(s\in J\)，且 \(s\) 属于每个归纳集 | \(n\) 属于这些归纳集；其后继闭包取得的结果与 \(s\) 由外延唯一性相等 |
| O5 | \(s\in W\)，故 `Inductive(W)` | Omega-Construct；先存在引入后关闭 \(s\)，再推广 \(n\) |
| O6 | \(\forall I(\operatorname{Inductive}(I)\to\operatorname{Sub}(W,I))\) | Omega-Construct 直接给出逐元素包含 |
| O7 | `Omega(W)` | O5、O6；折回 N3 |

若 \(W,V\) 都满足 N3，则各自的最小性给出相互包含，外延给 \(W=V\)。引入存在式后关闭 \(W,J\) 的构造见证，得到

\[
\exists W\bigl(\operatorname{Omega}(W)\land
\forall V(\operatorname{Omega}(V)\to V=W)\bigr).
\tag{Omega-Unique}
\]

由 N2–N4 和后继唯一性，空集是自然数，且自然数的后继仍是自然数。

自然数归纳模式也从 N3 导出。固定一个元语言公式 \(\theta(n)\)，允许它带明确固定的参数。若

\[
\forall e(\operatorname{Empty}(e)\to\theta(e)),
\]
\[
\forall n\forall s\bigl(((\operatorname{Nat}(n)\land\theta(n))\land\operatorname{Succ}(s,n))\to\theta(s)\bigr),
\]

则

\[
\forall n(\operatorname{Nat}(n)\to\theta(n)).
\tag{Nat-Ind}
\]

证明：取满足 N3 的 \(W\)，在 \(W\) 上分离满足 \(\theta\) 的成员，得到 \(H\)。空集由第一前提属于 \(H\)。若 \(n\in H\)，则 \(n\in W\)，故是自然数；其后继属于 \(W\)，第二前提又使它满足 \(\theta\)，所以属于 \(H\)。因此 `Inductive(H)`。N3 的最小性给 \(W\subseteq H\)，故 \(W\) 中每个成员都满足 \(\theta\)。任意满足 `Nat` 的对象，由 Omega-Unique 都属于这个 \(W\)。推广后关闭 \(H,W\) 的见证，得到 Nat-Ind。这里量化的只是集合，不量化公式 \(\theta\)。

### 4.2 没有集合属于自身

\[
\forall n\,\neg(n\in n).
\tag{No-Self}
\]

固定 \(n\)，用配对取单点集 \(S\)。它非空，因为 \(n\in S\)。正则公理提供 \(x\in S\)，使 \(x\) 与 \(S\) 没有共同成员。单点集的成员条件给 \(x=n\)。若 \(n\in n\)，那么 \(n\) 同时属于 \(x\) 与 \(S\)，矛盾。关闭正则公理见证与单点集见证，推广 \(n\)。后面只用它保证：后继 \(n\cup\{n\}\) 中新添的元素 \(n\) 原先不属于 \(n\)。

### 4.3 空集有限

\[
\forall e(\operatorname{Empty}(e)\to\operatorname{Fin}(e)).
\tag{F-Empty}
\]

固定空集 \(e\)。第 4.1 节给 `Nat(e)`。取函数图本身也为 \(e\)。N5 的类型、总定义及单值条件和 N6 的单射、满射条件都成立：所有需要输入、输出或图成员的前件都不成立。因此 `Bij(e,e,e)`。在 D14 中以 \(n=e,F=e\) 为见证，得到 `Fin(e)`。这里“从空集到空集的空函数”是按 N5–N6 逐项验证的。

### 4.4 添入一个元素保持有限：直接延长双射

\[
\forall p\forall x\forall q
\bigl((\operatorname{Fin}(p)\land\operatorname{Adjoin}(q,p,x))\to\operatorname{Fin}(q)\bigr).
\tag{F-Adjoin}
\]

固定前件。若 \(x\in p\)，则 D7 与外延给 \(q=p\)，结论由等词代换得到。

以下假设 \(x\notin p\)。由 D14 取新鲜 \(n,F\)，满足 `Nat(n)` 与 `Bij(F,p,n)`。取自然数后继 \(m\)，满足 `Succ(m,n)`；由第 4.1 节，`Nat(m)`。取有序对编码 \(w\)，满足 \(K(w,x,n)\)，并向 \(F\) 添入 \(w\)，得到 \(G\)。这是把新元素 \(x\) 对应到新标签 \(n\)。

| 检查项 | 对 \(G\) 的验证 | 依据 |
|---|---|---|
| 图的类型 | 旧图成员的输入属于 \(p\subseteq q\)，输出属于 \(n\subseteq m\)；新增成员的输入为 \(x\in q\)，输出为 \(n\in m\) | D7、N1、N5、K-Inj |
| 对 \(q\) 总定义 | 输入若属于 \(p\)，用旧图的输出；输入若为 \(x\)，用新增有序对 | D7 的成员两分支 |
| 单值 | 两个旧输出由原图单值性相等；两个新输出均为 \(n\)；旧、新图不能具有同一个输入，否则 \(x\in p\) | N5、\(x\notin p\)、K-Inj |
| 单射 | 两个旧输入用原图单射性；两个新输入均为 \(x\)；旧、新图的输出不能相等，因为旧输出属于 \(n\)，新输出为 \(n\)，而 \(n\notin n\) | N6、No-Self |
| 对 \(m\) 满射 | 任取 \(y\in m\)，由后继定义分成 \(y\in n\) 或 \(y=n\)；前者用旧图的满射性，后者用新增有序对 | N1、N6 |

因此 `Bij(G,q,m)`。以 \(m,G\) 为 D14 的见证得到 `Fin(q)`，然后依次关闭 \(G,w,m,F,n\) 的存在子证明。两种关于 \(x\in p\) 的分支合并，解除前件并推广 \(p,x,q\)，即得 F-Adjoin。由 F-Empty 和 F-Adjoin，单点集有限。

### 4.5 从双射定义导出有限集归纳模式

固定元语言公式 \(\theta(p)\)。假设已经证明空集满足 \(\theta\)，并且

\[
\forall s\forall x\forall t
\bigl(((\operatorname{Fin}(s)\land\theta(s))\land\operatorname{Adjoin}(t,s,x))\to\theta(t)\bigr).
\]

要证明

\[
\forall p(\operatorname{Fin}(p)\to\theta(p)).
\tag{F-Ind}
\]

对自然数应用 Nat-Ind，归纳的元语言公式是

\[
\Theta(n):\!\!\iff\forall p\forall F(\operatorname{Bij}(F,p,n)\to\theta(p)).
\]

这里 \(\Theta\) 是针对任意已固定 \(\theta\) 临时使用的公式模板，不是一个带有隐藏参数的新增对象谓词。

**空集步。** 若 \(e\) 为空且 `Bij(F,p,e)`，那么 \(p\) 也为空：否则由总定义性，从任一 \(x\in p\) 取得 \(y\in e\)，矛盾。于是基步假设给 \(\theta(p)\)，推广 \(p,F\) 得 \(\Theta(e)\)。

**后继步。** 假设 `Nat(n)`、\(\Theta(n)\) 及 `Succ(m,n)`，任取满足 `Bij(F,p,m)` 的 \(p,F\)。因为 \(n\in m\)，满射性给出新鲜 \(x\in p\)，使 `At(F,x,n)`。

在 \(p\) 上分离去掉 \(x\)，得到 \(q\)，满足 `Remove(q,p,x)`。再在 \(F\) 上分离，得到 \(G\)，满足

\[
\forall w\Bigl(w\in G\leftrightarrow
\bigl(w\in F\land\exists u\exists v((u\in q\land v\in n)\land K(w,u,v))\bigr)\Bigr).
\tag{Restrict-Bij}
\]

下面验证 `Bij(G,q,n)`，不能只说“限制一下仍是双射”。

| 检查项 | 推导 |
|---|---|
| 类型 | Restrict-Bij 本身给出：成员是输入属于 \(q\)、输出属于 \(n\) 的有序对 |
| 总定义 | 任取 \(u\in q\)。原图给输出 \(v\in m\)。若 \(v=n\)，原图单射性和 `At(F,x,n)` 给 \(u=x\)，与 \(u\in q\) 矛盾。所以由后继成员条件得 \(v\in n\)，相应图成员被保留在 \(G\) |
| 单值、单射 | \(G\) 的图成员都属于 \(F\)，故直接继承原图相应性质 |
| 满射 | 任取 \(v\in n\)，原图满射性给 \(u\in p\) 及 `At(F,u,v)`。若 \(u=x\)，由原图单值性得 \(v=n\)，从 \(v\in n\) 得 \(n\in n\)，与 No-Self 矛盾。因此 \(u\in q\)，相应图成员属于 \(G\) |

由 `Nat(n)` 与该双射，D14 给 `Fin(q)`；归纳假设 \(\Theta(n)\) 给 \(\theta(q)\)。因为 \(x\in p\)，逐元素可得 `Adjoin(p,q,x)`。由本节假设的添入步骤，得到 \(\theta(p)\)。先关闭 \(G,q,x\) 的见证，再解除原双射假设、推广 \(p,F\)，得到 \(\Theta(m)\)。

Nat-Ind 因而给所有自然数都满足 \(\Theta\)。最后任取有限 \(p\)，由 D14 取得自然数 \(n\) 及双射 \(F\)，实例化 \(\Theta(n)\) 得 \(\theta(p)\)；关闭见证并推广，得到 F-Ind。此证明先使用自然数归纳，再推出有限集归纳，没有循环调用待证的有限集性质。

### 4.6 后文使用的有限性引理及其证明

**子集引理。**

\[
\forall p\forall q
\bigl((\operatorname{Fin}(p)\land\operatorname{Sub}(q,p))\to\operatorname{Fin}(q)\bigr).
\tag{F-Sub}
\]

对性质 \(\theta(p):\!\!\iff\forall q(\operatorname{Sub}(q,p)\to\operatorname{Fin}(q))\) 使用 F-Ind。空集的子集为空集，基步成立。设 \(p\) 已有该性质，\(t\) 是向 \(p\) 添入 \(x\) 的结果，并取 \(q\subseteq t\)。在 \(q\) 上分离去掉 \(x\)，得到 \(v\)。逐元素可得 \(v\subseteq p\)，故 `Fin(v)`。若 \(x\in q\)，则 `Adjoin(q,v,x)`，用 F-Adjoin；若 \(x\notin q\)，则 \(q=v\)，用等词代换。因此 \(q\) 有限。两分支完成归纳步。

**并集引理。** 两个有限集的并有限。固定有限的 \(p\)，对另一集合 \(q\) 用 F-Ind：空集步的并就是 \(p\)；若向 \(q\) 添入 \(x\)，则相应的并也是向原来的并添入 \(x\)。这些相等都由逐元素等价及外延得到，再用 F-Adjoin。并集的存在由配对与并集公理保证。

**有限像引理。** 固定一个集合 \(D\)、一个集合 \(E\) 和公式 \(\psi(x,y)\)，假设每个 \(x\in D\) 在 \(E\) 内有唯一满足 \(\psi\) 的 \(y\)。若 \(p\subseteq D\) 且 `Fin(p)`，则在 \(E\) 上分离得到的精确像有限。

证明时取性质：“若 \(s\subseteq D\)，则它在 \(E\) 内的精确像有限”。空集的像为空。添入步中，若添入结果仍包含于 \(D\)，则原集合也包含于 \(D\)，且所添元素属于 \(D\)；取该元素的唯一像，新的精确像就是向旧像添入此像，用 F-Adjoin。若添入结果不包含于 \(D\)，待证蕴含直接成立。存在性一律在 \(E\) 上分离；无需选择公理。

**有限积引理。** 两个有限集的有序对集合有限。其集合存在性可由两者的并、两次幂集及分离取得：若两坐标都属于并集，则 Kuratowski 对属于这个并集的二次幂集。固定第一个有限集合，对第二个集合用 F-Ind：空集步得到空积；添入一个元素时，增加的一层是第一个集合在“与这个元素配对”关系下的有限像，再用并集引理。

**有限线性序的极值引理。** 非空有限集上的线性序具有最小与最大成员。固定序的载体 \(D\)，对性质“若 \(s\) 是 \(D\) 的子集，则 \(s\) 为空集，或同时有最小与最大成员”用 F-Ind。基步选空集分支。添入步中，若结果不包含于 \(D\)，待证蕴含直接成立；否则原集合及所添元素都在 \(D\) 中。此时若原集合为空，新集合为单点集；否则取已有最小、最大成员，分别用全序比较所添元素与它们，按比较结果选出新极值。由传递性逐元素验证界性质；极值属于新集合。没有给元素编号。

## 5. 实数序加结构的纯集合论假设

以下仍然只是在定义缩写；每个缩写向前递归展开后都只有 \(\in,=\) 及逻辑符号。

### 5.1 序、加法及上确界

`LE` 与 `Positive` 已在第 1.3 节给出（D15、D16）；以下补齐用于证明的结构条件。





\[
\operatorname{Upper}(u,S,R,L):\!\!\iff
u\in R\land\forall x(x\in S\to\operatorname{LE}(R,L,x,u)).
\tag{D17}
\]

\[
\operatorname{Sup}(c,S,R,L):\!\!\iff
\operatorname{Upper}(c,S,R,L)
\land\forall u(\operatorname{Upper}(u,S,R,L)\to\operatorname{LE}(R,L,c,u)).
\tag{D18}
\]

严格线性序：

\[
\begin{aligned}
\operatorname{Order}(R,L):\!\!\iff{}&
\forall w(w\in L\to\exists x\exists y((x\in R\land y\in R)\land K(w,x,y)))
\\&\land\forall x\,\neg\operatorname{At}(L,x,x)
\\&\land\forall x\forall y\forall z((\operatorname{At}(L,x,y)\land\operatorname{At}(L,y,z))\to\operatorname{At}(L,x,z))
\\&\land\forall x\forall y((x\in R\land y\in R)\to((x=y\lor\operatorname{At}(L,x,y))\lor\operatorname{At}(L,y,x))).
\end{aligned}
\tag{D19}
\]

加法图具有正确类型、处处有定义且单值：

\[
\begin{aligned}
\operatorname{AddGraph}(R,M):\!\!\iff{}&
\forall w\Bigl(w\in M\to
\exists x\exists y\exists z\exists v
\bigl(((x\in R\land y\in R)\land z\in R)\land(K(v,x,y)\land K(w,v,z))\bigr)\Bigr)
\\&\land\forall x\forall y\Bigl((x\in R\land y\in R)\to
\exists z\bigl((z\in R\land\operatorname{Tri}(M,x,y,z))
\land\forall t(\operatorname{Tri}(M,x,y,t)\to t=z)\bigr)\Bigr).
\end{aligned}
\tag{D20}
\]

零元、交换律、结合律及逆元：

\[
\begin{aligned}
\operatorname{GroupLaws}(R,M,o):\!\!\iff{}&o\in R
\\&\land\forall x(x\in R\to(\operatorname{Tri}(M,x,o,x)\land\operatorname{Tri}(M,o,x,x)))
\\&\land\forall x\forall y\forall z(\operatorname{Tri}(M,x,y,z)\to\operatorname{Tri}(M,y,x,z))
\\&\land\forall x\forall y\forall z\forall u\forall v\forall w
\Bigl(((\operatorname{Tri}(M,x,y,u)\land\operatorname{Tri}(M,u,z,v))\land\operatorname{Tri}(M,y,z,w))\to\operatorname{Tri}(M,x,w,v)\Bigr)
\\&\land\forall x(x\in R\to\exists y(y\in R\land\operatorname{Tri}(M,x,y,o))).
\end{aligned}
\tag{D21}
\]

平移保序：

\[
\begin{aligned}
\operatorname{Translate}(R,L,M):\!\!\iff
\forall x\forall y\forall z\forall u\forall v
\Bigl(&((\operatorname{At}(L,x,y)\land z\in R)
\land\operatorname{Tri}(M,x,z,u))
\land\operatorname{Tri}(M,y,z,v)
\to\operatorname{At}(L,u,v)\Bigr).
\end{aligned}
\tag{D22}
\]

稠密性：

\[
\operatorname{Dense}(R,L):\!\!\iff
\forall x\forall y\bigl(\operatorname{At}(L,x,y)\to
\exists z((z\in R\land\operatorname{At}(L,x,z))\land\operatorname{At}(L,z,y))\bigr).
\tag{D23}
\]

Dedekind 完备性：

\[
\operatorname{Complete}(R,L):\!\!\iff
\forall S\Bigl(((\operatorname{Sub}(S,R)\land\operatorname{NE}(S))
\land\exists u\,\operatorname{Upper}(u,S,R,L))
\to\exists c\,\operatorname{Sup}(c,S,R,L)\Bigr).
\tag{D24}
\]

总假设：

\[
\boxed{
\begin{aligned}
\operatorname{Context}(R,L,M,o):\!\!\iff{}&
\operatorname{Order}(R,L)\land\operatorname{AddGraph}(R,M)
\\&\land\operatorname{GroupLaws}(R,M,o)\land\operatorname{Translate}(R,L,M)
\\&\land\operatorname{Dense}(R,L)\land\operatorname{Complete}(R,L)
\\&\land\exists d\,\operatorname{Positive}(R,L,o,d).
\end{aligned}
}
\tag{D25}
\]

### 5.2 关于通常代数记号的使用边界

解释文字可以把 `At(L,x,y)` 读作“\(x<y\)”，把 `Tri(M,x,y,z)` 读作“\(x+y=z\)”。这些仅是阅读辅助；带标签的定义及最终定理使用关系公式。

从 D20、D21 得到的每个和或逆元，都通过存在消去引入；它们不是对象语言中自动存在的函数值。`At` 的坐标类型由 D19、K-Inj 得到；`Tri` 的坐标类型由 D20、两次 K-Inj 得到。

## 6. 序加结构的辅助引理

本节固定满足 `Context(R,L,M,o)` 的参数。说明文字中的不等号与加法等式，均按第 5.2 节翻译；正式结论保持关系式。

### 6.1 序的基本推论

由不可反性与传递性，严格小于具有不对称性：若两个相反方向都成立，传递性给出某元素严格小于自身，矛盾。结合全序，得到 `LE` 的反对称性、传递性，以及一个非严格比较与一个严格比较组合后的严格传递性。每个结论均通过 D15 中“等于或严格小于”的两分支推出。

例如，由 \(\operatorname{LE}(R,L,x,y)\) 和 \(\operatorname{At}(L,y,z)\)：若 \(x=y\)，等词代换；若 \(x<y\)，用严格传递性。其余混合情况同理，分别在等号分支代换，在严格分支用传递性。

### 6.2 平移可逆与加法消去

若 `Tri(M,x,z,u)`、`Tri(M,y,z,v)`，且相关坐标属于 \(R\)，则

\[
\operatorname{At}(L,x,y)\leftrightarrow\operatorname{At}(L,u,v).
\tag{G-Order}
\]

正向是 D22。反向取 \(z\) 的逆元 \(n\)，再取 \(u+n\)、\(v+n\) 的关系见证。以下说明第一见证恰为 \(x\)：由 `Tri(M,x,z,u)`、`Tri(M,u,n,r)`、`Tri(M,z,n,o)`，D21 的结合律得到 `Tri(M,x,o,r)`；而零元律给 `Tri(M,x,o,x)`，单值性推出 \(r=x\)。另一见证同理为 \(y\)。把 \(u<v\) 平移 \(n\)，即得 \(x<y\)。在结论不含 \(n,r\) 等见证后关闭存在子证明。

同一计算证明消去律：若两个加法输出相等，则平移逆元后原输入相等。交换律使这一论证也适用于固定左输入。

### 6.3 差值关系的存在唯一性

\[
\forall x\forall y\Bigl((x\in R\land y\in R)\to
\exists h\bigl((h\in R\land\operatorname{Tri}(M,x,h,y))
\land\forall k(\operatorname{Tri}(M,x,k,y)\to k=h)\bigr)\Bigr).
\tag{G-Difference}
\]

存在性：取 \(x\) 的逆元 \(n\)，再取满足 `Tri(M,n,y,h)` 的 \(h\)。由 `Tri(M,x,n,o)`、`Tri(M,o,y,y)` 和结合律，得到 `Tri(M,x,h,y)`。唯一性由固定左输入的消去律得到。最后引入所需存在式，关闭全部局部见证，再推广 \(x,y\)。

若 `Tri(M,x,h,y)` 且 \(x<y\)，则 \(o<h\)：把 `Tri(M,x,o,x)` 与该关系作 G-Order 的比较，使用交换律把固定左输入改成固定右输入。

对这样的差值 \(h\)，同样由平移可逆得

\[
\operatorname{Gap}(L,M,x,y,d)\leftrightarrow\operatorname{At}(L,h,d)
\tag{G-Gap}
\]

其中假设 \(d\in R\)。具体地，取 \(x+d\) 的唯一输出 \(v\)；`Gap` 就是 \(y<v\)，而 \(y=x+h\)，故经同一平移的反向与正向恰好等价于 \(h<d\)。

### 6.4 正阈值下的局部左右延伸

第一条结论：

\[
\begin{aligned}
\forall c\forall d\Bigl((c\in R\land\operatorname{Positive}(R,L,o,d))\to
\exists v\bigl(& (v\in R\land\operatorname{At}(L,v,c))
\land\operatorname{Gap}(L,M,v,c,d)\bigr)\Bigr).
\end{aligned}
\tag{G-Left}
\]

证明：由 G-Difference 和交换律取得 \(r\)，使 `Tri(M,r,d,c)`。因为 \(o<d\)，将它平移 \(r\)，得 \(r<c\)。由稠密性选取 \(v\)，使 \(r<v<c\)。取 \(v+d\) 的输出 \(w\)；把 \(r<v\) 平移 \(d\)，得 \(c<w\)。于是 \(w\) 是 `Gap(L,M,v,c,d)` 的存在见证。先引入关于 \(v\) 的目标存在式，再关闭所有辅助见证。

第二条结论：

\[
\begin{aligned}
\forall c\forall b\forall d\Bigl((\operatorname{At}(L,c,b)\land\operatorname{Positive}(R,L,o,d))\to
\exists t\bigl(& (\operatorname{At}(L,c,t)\land\operatorname{LE}(R,L,t,b))
\land\operatorname{Gap}(L,M,c,t,d)\bigr)\Bigr).
\end{aligned}
\tag{G-Right}
\]

证明：取 `Tri(M,c,d,w)`。正性及平移给 \(c<w\)。比较 \(b,w\)：若 \(b\le w\)，取 \(u=b\)；否则取 \(u=w\)。在两支中都有 \(c<u\)、\(u\le b\)、\(u\le w\)。稠密性给 \(c<t<u\)，故 \(t\le b\) 且 \(t<w\)，后者连同 `Tri(M,c,d,w)` 就给出 `Gap`。两个比较分支分别引入同一个目标存在式，再析取消去；没有使用未定义的 `min` 函数项。

### 6.5 阈值单调性

\[
\begin{aligned}
\forall U\forall a\forall b\forall d\forall e\Bigl(
(&\operatorname{Fine}(U,R,L,M,a,b,d)\land\operatorname{LE}(R,L,d,e))
\to\operatorname{Fine}(U,R,L,M,a,b,e)\Bigr).
\end{aligned}
\tag{G-Monotone}
\]

证明：`Part` 条件不变，\(e\in R\) 从 `LE` 得到。任取相邻分点 \(x,y\)。已有见证 \(v\) 满足 \(x+d=v\)、\(y<v\)。取 \(x+e=w\)。若 \(d=e\)，单值性给 \(v=w\)；若 \(d<e\)，由交换律和平移保序给 \(v<w\)。两支都推出 \(y<w\)，故 `Gap` 对 \(e\) 成立。关闭存在见证，推广 \(x,y\)，折回 `Fine`。

### 6.6 上确界的逼近性质

\[
\begin{aligned}
\forall S\forall c\forall v\Bigl(
(&\operatorname{Sup}(c,S,R,L)\land\operatorname{At}(L,v,c))
\to\exists x(x\in S\land\operatorname{At}(L,v,x))\Bigr).
\end{aligned}
\tag{G-SupApprox}
\]

假设结论不成立。任取 \(x\in S\)，则 \(x\le c\)，因而 \(x\in R\)。由全序及不存在 \(v<x\)，得到 \(x\le v\)。所以 \(v\) 是 \(S\) 的上界。上确界定义给 \(c\le v\)，与 \(v<c\) 矛盾。经典反证给出目标存在式。该推导没有选择一个同时适用于所有 \(v\) 的函数。

## 7. 任意正阈值下存在足够细的有限分割

本节是基成员非空性的核心证明。固定 `Context(R,L,M,o)`，并固定端点 \(a,b\) 满足 `At(L,a,b)`。

### 7.1 添入一个新的右端点

假设

\[
\operatorname{Fine}(U,R,L,M,a,x,d),\quad
\operatorname{At}(L,x,y),\quad
\operatorname{Gap}(L,M,x,y,d).
\]

取 `Adjoin(V,U,y)` 的唯一结果。则

\[
\operatorname{Fine}(V,R,L,M,a,y,d).
\tag{P-Extend}
\]

| 步骤 | 推导内容 | 依据 |
|---|---|---|
| E1 | `Fin(V)` | `Fine` 给 `Fin(U)`；F-Adjoin |
| E2 | \(a\in V\land y\in V\) | \(a\in U\) 与 `Adjoin` |
| E3 | `Part(V,R,L,a,y)` | 原成员位于 \(a,x\) 之间，且 \(x<y\)；新成员是 \(y\)；逐元素两分支验证边界 |
| E4 | 任取 \(r,s\)，假设 `Adjacent(V,L,r,s)` | 开启全称条件的子证明 |
| E5 | \(r\ne y\)，从而 \(r\in U\) | 若 \(r=y\)，由 \(r<s\) 与 E3 给 \(s\le y\)，矛盾；再展开 `Adjoin` |
| E6 | 若 \(s\ne y\)，则 `Adjacent(U,L,r,s)` | 此时 \(s\in U\)；若 \(U\) 中有中间点，它也属于 \(V\)，与相邻矛盾 |
| E7 | 在 E6 分支中得 `Gap(L,M,r,s,d)` | 原 `Fine` |
| E8 | 若 \(s=y\)，则 \(r=x\) | 原分割给 \(r\le x\)；若 \(r<x\)，点 \(x\in U\subseteq V\) 严格位于 \(r,y\) 之间，矛盾；全序留下等号 |
| E9 | 在 E8 分支中得 `Gap(L,M,r,s,d)` | 主假设中的 `Gap(L,M,x,y,d)` 与等词代换 |
| E10 | 对所有相邻点满足 `Gap` | 关闭两分支，关闭 E4，推广 \(r,s\) |
| E11 | `Fine(V,R,L,M,a,y,d)` | E3、原来的 \(d\in R\)、E10，D31 |

如果需要存在式，先由 E11 引入 \(\exists V\)，再关闭 `Adjoin` 构造时的见证。表中将 \(U\subseteq V\) 写在解释栏，仅指 D7 直接给出的逐元素蕴含。

### 7.2 可达到的端点组成一个集合

固定一个正阈值 \(d\)，即假设 `Positive(R,L,o,d)`。在已有集合 \(R\) 上使用分离，得到新集合 \(S\)，满足

\[
\boxed{
\forall x\Bigl(x\in S\leftrightarrow
\bigl((x\in R\land\operatorname{LE}(R,L,a,x))
\land(\operatorname{LE}(R,L,x,b)\land\exists U\,\operatorname{Fine}(U,R,L,M,a,x,d))\bigr)\Bigr).
}
\tag{Reach}
\]

筛选公式不含 \(S\)。其中 \(\exists U\) 可以是无界量词；分离公理并不要求筛选公式的量词有界。

取 \(a\) 的单点集 \(U\)。它由 F-Empty、F-Adjoin 有限；它满足 `Part(U,R,L,a,a)`。不可能有两个严格递增的相邻分点，所以 D31 的全称蕴含成立。因而 `Fine(U,R,L,M,a,a,d)`，由 Reach 得 \(a\in S\)。

同时，Reach 给 \(\operatorname{Sub}(S,R)\)，并且 \(b\) 是 \(S\) 的上界。因此 D24 适用，存在新鲜 \(c\) 满足

\[
\operatorname{Sup}(c,S,R,L).
\]

由于 \(a\in S\)，上界性给 \(a\le c\)。由于 \(b\) 是上界，最小上界性给 \(c\le b\)。所以 \(c\) 也位于区间内。

### 7.3 上确界本身可以达到

由 G-Left 取得新鲜 \(v\)，满足

\[
v\in R,\qquad
\operatorname{At}(L,v,c),\qquad
\operatorname{Gap}(L,M,v,c,d).
\]

由 G-SupApprox，取得新鲜 \(x\)，满足

\[
x\in S,\qquad\operatorname{At}(L,v,x).
\]

上界性给 \(x\le c\)。分两种情况。

| 分支 | 推导 | 结果 |
|---|---|---|
| \(x=c\) | 由 \(x\in S\) 作等词代换 | \(c\in S\) |
| \(x<c\) | Reach 给某个 `Fine(U,R,L,M,a,x,d)`。由 `Gap(L,M,v,c,d)` 取 \(v+d=w\) 且 \(c<w\)；再取 \(x+d=t\)。把 \(v<x\) 平移 \(d\)，得 \(w<t\)，故 \(c<t\)，即 `Gap(L,M,x,c,d)`。应用 P-Extend 添入 \(c\)，得到 `Fine(V,R,L,M,a,c,d)`。结合 \(a\le c\le b\)，用 Reach。 | \(c\in S\) |

两个分支的结论相同。每个分支在使用自己的见证后，先得不含它们的结论 \(c\in S\)，再关闭存在子证明。关闭 \(x,v\) 的见证，得到 \(c\in S\)。

### 7.4 上确界必为右端点

已有 \(c\le b\)。假设 \(c\ne b\)，则 \(c<b\)。由 G-Right 取得新鲜 \(t\)，满足

\[
\operatorname{At}(L,c,t),\qquad
\operatorname{LE}(R,L,t,b),\qquad
\operatorname{Gap}(L,M,c,t,d).
\]

由 \(c\in S\) 与 Reach，取一个到达 \(c\) 的细分割，应用 P-Extend 添入 \(t\)，得到到达 \(t\) 的细分割。又有 \(a\le c<t\le b\)，所以 Reach 给 \(t\in S\)。

但 \(c\) 是 \(S\) 的上界，故 \(t\le c\)，与 \(c<t\) 矛盾。解除 \(c\ne b\) 的假设，得到 \(c=b\)。由 \(c\in S\) 得 \(b\in S\)，再次展开 Reach 得到

\[
\exists U\,\operatorname{Fine}(U,R,L,M,a,b,d).
\]

此结论不含 \(S,c\)，因此先关闭上确界见证 \(c\)，再关闭 Reach 的集合见证 \(S\)。解除阈值正性的假设并推广 \(d\)，得到

\[
\boxed{
\forall d\bigl(\operatorname{Positive}(R,L,o,d)
\to\exists U\,\operatorname{Fine}(U,R,L,M,a,b,d)\bigr).
}
\tag{P-FineExists}
\]

它是在 `Context(R,L,M,o)` 与 `At(L,a,b)` 这两个固定假设下证明的；在最终闭式中，这两个假设会一起解除。整个论证未使用选择公理，也未从一个未经证明的“足够大的整数”开始。

## 8. 区间、分割空间与基族都是实际存在的集合

仍在第 7 节的固定结构与端点假设下。不能仅写“令集合等于满足条件的所有对象”，必须给出分离的母集。

### 8.1 区间集合

在 \(R\) 上按条件

\[
\operatorname{LE}(R,L,a,x)\land\operatorname{LE}(R,L,x,b)
\]

分离，得到 \(I\)，它满足 D26。若 \(J\) 也满足 D26，则对任意 \(x\)，\(x\in I\) 与 \(x\in J\) 等价，外延给 \(I=J\)。

### 8.2 分割空间

取新鲜 \(P\) 满足 `Pow(P,I)`，在 \(P\) 上按 `Part(U,R,L,a,b)` 分离，得到 \(X\)：

\[
\forall U\bigl(U\in X\leftrightarrow(U\in P\land\operatorname{Part}(U,R,L,a,b))\bigr).
\]

若 `Part(U,R,L,a,b)` 成立，则对任意 \(x\in U\)，D27 给区间边界，D26 给 \(x\in I\)，所以 `Sub(U,I)`；由 `Pow(P,I)` 得 \(U\in P\)。因此上式等价于

\[
\forall U\,(U\in X\leftrightarrow\operatorname{Part}(U,R,L,a,b)),
\]

即 `Space(X,R,L,a,b)`。它的唯一性也由成员双条件及外延得到。后续使用 \(X\) 时，\(P\) 只是其构造的局部见证，最终将关闭。

### 8.3 固定阈值对应的集合

对任意集合 \(d\)，在已有集合 \(X\) 上按 `Fine(U,R,L,M,a,b,d)` 分离，得到唯一的 \(V\)，满足 `Slice(V,X,R,L,M,a,b,d)`。

这一步不需要先假定 \(d\) 是正数；正性只在证明 \(V\) 非空及把它纳入滤基时使用。

在通常的一阶非空论域中，D33 右侧等价于

\[
\exists d\bigl(\operatorname{Positive}(R,L,o,d)
\land\operatorname{Slice}(V,X,R,L,M,a,b,d)\bigr).
\tag{Slice-Equiv}
\]

正向：对存在见证 \(d\)，把全称式实例化到任意已有集合，例如 \(X\)，取得 `Positive`；另取任意新鲜 \(U\)，消去合取得到成员双条件，再全称引入，得到 `Slice`。反向：固定见证 \(d\)，对任意 \(U\) 将 `Positive` 与 `Slice` 的实例合取，再全称引入 \(U\)，最后存在引入 \(d\)。各方向在输出存在式后关闭见证。

### 8.4 整个基族

取新鲜 \(Q\) 满足 `Pow(Q,X)`。在 \(Q\) 上按以下公式分离：

\[
\exists d\forall U\left[
\operatorname{Positive}(R,L,o,d)
\land\bigl(U\in V\leftrightarrow(U\in X\land\operatorname{Fine}(U,R,L,M,a,b,d))\bigr)
\right].
\tag{BaseMember}
\]

得到集合 \(B\)。BaseMember 的自由变量是 \(V,X,R,L,M,o,a,b\)，不含输出集合变量 \(B\)，满足分离侧条件。

若 BaseMember 对某个 \(V\) 成立，则取其阈值见证，对任意 \(U\) 从成员双条件得到 \(U\in V\to U\in X\)。所以 `Sub(V,X)`，进而 \(V\in Q\)。因此分离结果中的母集限制可消去，恰好得到 `Family(B,X,R,L,M,o,a,b)`。

若另一个 \(C\) 满足同一个 `Family` 公式，那么对任意 \(V\)，\(V\in B\) 与 \(V\in C\) 都等价于 BaseMember。外延给 \(B=C\)。这也说明基族不依赖任何临时选取的幂集见证。

## 9. 对滤基四个合取项的逐条证明

固定已经构造的 \(X,B\)，假设

\[
\operatorname{Space}(X,R,L,a,b),\qquad
\operatorname{Family}(B,X,R,L,M,o,a,b).
\]

本节每个子证明都在相同的结构与端点假设下进行。

### 9.1 每个成员是 \(X\) 的子集

| 步骤 | 严格公式 | 依据 |
|---|---|---|
| B1 | \([V\in B]\) | 任取 \(V\)，开启蕴含引入子证明 |
| B2 | \(\exists d(\operatorname{Positive}(R,L,o,d)\land\operatorname{Slice}(V,X,R,L,M,a,b,d))\) | D33、Slice-Equiv |
| B3 | \([\operatorname{Positive}(R,L,o,d)\land\operatorname{Slice}(V,X,R,L,M,a,b,d)]\) | 对 B2 存在消去；\(d\) 新鲜 |
| B4 | \([U\in V]\) | 任取新鲜 \(U\)，开启子证明 |
| B5 | \(U\in X\land\operatorname{Fine}(U,R,L,M,a,b,d)\) | B3 中的 D32 实例与 B4 |
| B6 | \(U\in X\) | 合取消去 |
| B7 | \(\forall U(U\in V\to U\in X)\) | 解除 B4，推广 \(U\) |
| B8 | \(\forall V(V\in B\to\forall U(U\in V\to U\in X))\) | B7 不含 \(d\)，关闭 B3；解除 B1；推广 \(V\) |

### 9.2 基族本身非空

| 步骤 | 严格公式 | 依据 |
|---|---|---|
| B9 | \(\exists d\,\operatorname{Positive}(R,L,o,d)\) | D25 的最后一个合取项 |
| B10 | \([\operatorname{Positive}(R,L,o,d)]\) | 存在消去；\(d\) 新鲜 |
| B11 | \(\exists V\,\operatorname{Slice}(V,X,R,L,M,a,b,d)\) | 第 8.3 节，在 \(X\) 上分离 |
| B12 | \([\operatorname{Slice}(V,X,R,L,M,a,b,d)]\) | 存在消去；\(V\) 新鲜 |
| B13 | \(V\in B\) | B10、B12、Slice-Equiv、D33；存在见证取 \(d\) |
| B14 | \(\exists V(V\in B)\) | B13，存在引入 |
| B15 | \(\exists V(V\in B)\) | 先关闭 B12，再关闭 B10；目标不含这两个局部见证 |

这一条只需构造一个成员。这个成员自身是否非空，由下一条统一证明。

### 9.3 每个基成员非空

| 步骤 | 严格公式 | 依据 |
|---|---|---|
| B16 | \([V\in B]\) | 任取 \(V\)，开启子证明 |
| B17 | \(\exists d(\operatorname{Positive}(R,L,o,d)\land\operatorname{Slice}(V,X,R,L,M,a,b,d))\) | D33、Slice-Equiv |
| B18 | \([\operatorname{Positive}(R,L,o,d)\land\operatorname{Slice}(V,X,R,L,M,a,b,d)]\) | 存在消去；\(d\) 新鲜 |
| B19 | \(\exists U\,\operatorname{Fine}(U,R,L,M,a,b,d)\) | P-FineExists、B18 的正性 |
| B20 | \([\operatorname{Fine}(U,R,L,M,a,b,d)]\) | 存在消去；\(U\) 新鲜 |
| B21 | \(\operatorname{Part}(U,R,L,a,b)\) | D31，合取消去 |
| B22 | \(U\in X\) | D28、B21 |
| B23 | \(U\in V\) | B18 的 D32、B20、B22 |
| B24 | \(\exists U(U\in V)\) | 存在引入 |
| B25 | \(\forall V(V\in B\to\exists U(U\in V))\) | 依次关闭 B20、B18，解除 B16，再全称引入 \(V\) |

### 9.4 两个基成员的交集本身也是基成员

任取 \(V,W\)，假设 \(V\in B\land W\in B\)。分别由 D33 与 Slice-Equiv 取新鲜正阈值 \(d,e\)，使

\[
\operatorname{Slice}(V,X,R,L,M,a,b,d),\qquad
\operatorname{Slice}(W,X,R,L,M,a,b,e).
\]

全序给出 \(d\le e\) 或 \(e\le d\)。这里不用 `min` 函数项，直接分支。

**第一支：假设 `LE(R,L,d,e)`。**

由 G-Monotone，对任意 \(U\) 有

\[
\operatorname{Fine}(U,R,L,M,a,b,d)
\to\operatorname{Fine}(U,R,L,M,a,b,e).
\]

结合两个 `Slice`，对任意 \(U\) 得 \(U\in V\to U\in W\)。于是

\[
\forall U\bigl(U\in V\leftrightarrow(U\in V\land U\in W)\bigr).
\]

取目标见证 \(T=V\)。因为 \(V\in B\)，得到

\[
\exists T\bigl(T\in B\land\operatorname{Inter}(T,V,W)\bigr).
\]

**第二支：假设 `LE(R,L,e,d)`。**

同样由 G-Monotone 得 \(U\in W\to U\in V\)。取目标见证 \(T=W\)，得到同一个存在式。

两个分支的结论完全一致，故由析取消去得到该存在式；随后关闭阈值 \(e,d\) 的存在见证。解除 \(V\in B\land W\in B\) 的假设并推广 \(V,W\)，得到较强结论

\[
\boxed{
\forall V\forall W\bigl((V\in B\land W\in B)\to
\exists T(T\in B\land\operatorname{Inter}(T,V,W))\bigr).
}
\tag{B-Intersection}
\]

展开 `Inter`，只取其正向蕴含，就得到 D34 最后一个合取项。这里等价于通常“取两个阈值中较小者”，但没有引入下标族或最小值函数。

### 9.5 合并

将 B8、B15、B25 和 B-Intersection 推出的包含条件合取，按 D34 折回，得到

\[
\operatorname{FilterBase}(B,X).
\tag{B-Final}
\]

构造与证明中完全没有要求一个足够细的分割必须包含某个预先固定的内部分点。成员条件只由正阈值及相邻间距决定。

## 10. 与“最大子区间长度小于阈值”的严格对应

本节排除另一种可能的隐含跳跃：有限分割的最大相邻距离为什么存在，以及 D31 为什么正好表达通常的细度条件。

### 10.1 最大相邻距离的关系式

最大细度关系 `Mesh` 已在第 1.8 节给出（D35），本节证明它的存在唯一性及其与 `Fine` 的对应。

它要求 \(m\) 是某一相邻间距，并且不小于所有相邻间距。它是关系公式，不是函数项。

### 10.2 至少存在一对相邻分点

假设 `Part(U,R,L,a,b)` 且 \(a<b\)。在 \(U\) 上分离得到集合 \(Y\)：

\[
\forall y\,(y\in Y\leftrightarrow(y\in U\land\operatorname{At}(L,a,y))).
\]

因为 \(b\in Y\)，\(Y\) 非空。由 F-Sub，\(Y\) 有限。由第 4.6 节有限线性序的极值引理，取 \(Y\) 的最小成员 \(y\)。若存在 \(z\in U\) 满足 \(a<z<y\)，则 \(z\in Y\)，与 \(y\) 最小矛盾。因此 `Adjacent(U,L,a,y)`。

### 10.3 相邻间距组成非空有限集

在 \(R\) 上分离得到 \(D\)：

\[
\forall h\Bigl(h\in D\leftrightarrow
\bigl(h\in R\land\exists x\exists y
(\operatorname{Adjacent}(U,L,x,y)\land\operatorname{Tri}(M,x,h,y))\bigr)\Bigr).
\tag{Distances}
\]

集合存在的母集是 \(R\)。以下逐项说明有限性，不把“只有有限多个相邻对”作为未证明的断言。

1. 由有限积引理，\(U\) 与自身的有序对集合 \(C\) 有限。
2. 在 \(C\) 上分离相邻对，得到有限子集 \(E\)，使用 F-Sub。
3. 每个 \(w\in E\) 的两个坐标由 K-Inj 唯一确定；对应差值由 G-Difference 存在唯一。
4. 以 \(R\) 为输出母集，对该差值关系使用有限像引理，所得精确像有限。
5. 这个精确像与 Distances 中的 \(D\) 有同样成员，因此由外延相等，故 `Fin(D)`。

第 10.2 节给出相邻对，G-Difference 给出其差值，故 \(D\) 非空。所有成员都属于 \(R\)，因此由有限线性序的极值引理，\(D\) 有最大成员 \(m\)。它满足 D35。

若 \(m,n\) 均满足 D35，利用各自“是一个相邻间距”的见证，代入对方的上界条件，得到 \(m\le n\) 与 \(n\le m\)。反对称性给 \(m=n\)。所以最大细度作为关系值存在唯一。

### 10.4 细度条件的等价性

在 `Context` 假设下，成立

\[
\boxed{
\begin{aligned}
\forall U\forall a\forall b\forall m\forall d\Bigl(
(&\operatorname{Mesh}(U,R,L,M,a,b,m)\land d\in R)
\to\bigl(\operatorname{Fine}(U,R,L,M,a,b,d)
\leftrightarrow\operatorname{At}(L,m,d)\bigr)\Bigr).
\end{aligned}
}
\tag{Mesh-Equiv}
\]

正向：D35 给出一对实现最大间距 \(m\) 的相邻分点。把它代入 `Fine`，得到该对满足 `Gap`，再由 G-Gap 得 \(m<d\)。

反向：假设 \(m<d\)。任取一对相邻分点，取其唯一差值 \(h\)。D35 给 \(h\le m\)，与 \(m<d\) 组合得 \(h<d\)，由 G-Gap 得 `Gap`。关闭差值见证并推广这对分点。D35 已给 `Part`，前件给 \(d\in R\)，于是得到 `Fine`。

因此本篇的基族确实是按通常“最大相邻间距趋于零”定义的基族，而不是仅有类似外观的另一个关系族。

## 11. 最终闭式与见证作用域

### 11.1 主定理

\[
\boxed{
\begin{aligned}
ZF\vdash\forall R\forall L\forall M\forall o\forall a\forall b\Bigl(
(&\operatorname{Context}(R,L,M,o)\land\operatorname{At}(L,a,b))
\to\exists I\exists X\exists B\Bigl[
\\&\operatorname{Interval}(I,R,L,a,b)
\land\operatorname{Space}(X,R,L,a,b)
\\&\land\operatorname{Family}(B,X,R,L,M,o,a,b)
\land\operatorname{FilterBase}(B,X)
\\&\land\forall J(\operatorname{Interval}(J,R,L,a,b)\to J=I)
\\&\land\forall Y(\operatorname{Space}(Y,R,L,a,b)\to Y=X)
\\&\land\forall C(\operatorname{Family}(C,X,R,L,M,o,a,b)\to C=B)
\Bigr]\Bigr).
\end{aligned}
}
\tag{T}
\]

外层结构参数及端点全部被量化，最终没有额外自由参数。唯一性针对区间、分割空间和基族分别陈述；没有暗中使用唯一存在量词。

### 11.2 从局部构造闭合到 T

| 步骤 | 操作 | 作用域检查 |
|---|---|---|
| C1 | 固定任意 \(R,L,M,o,a,b\)，假设 T 的前件 | 这些是最后才推广的参数，不是语言常量 |
| C2 | 第 8.1 节取 \(I\)，第 8.2 节依次取 \(P,X\)，第 8.4 节依次取 \(Q,B\) | 每个见证新鲜；存在依据分别是分离、幂集、分离、幂集、分离 |
| C3 | 第 8 节给各成员刻画及唯一性；第 9 节给 `FilterBase` | 第 7 节使用过的 \(S,c\) 等局部见证已在 P-FineExists 前关闭 |
| C4 | 合取 T 方括号内全部内容，依次存在引入 \(B,X,I\) | 此时目标是完整的 \(\exists I\exists X\exists B\) 式，不再自由含构造见证 |
| C5 | 按反向顺序关闭 C2 的 \(B,Q,X,P,I\) 存在子证明 | C4 的目标不含其自由出现，满足存在消去侧条件 |
| C6 | 解除 T 的前件假设，按 \(b,a,o,M,L,R\) 的顺序全称引入 | 得到 T 所写的外层量词次序；不存在含这些变量的未解除假设 |

本篇使用外延、配对、并集、幂集及分离进行集合构造；第 4 节另外使用无穷公理构造自然数集合，并用正则公理保证没有集合属于自身。实数结构的通常构造属于 ZF 背景。本条件定理不需要选择公理，也不需要以替换公理选择一整族阈值见证。

## 12. 与“子集族有极大成员”有限性定义的关系

为对应前面讨论过的表达，再给出该性质的无界量词版本：

\[
\begin{aligned}
\operatorname{TarskiFinite}(p):\!\!\iff
\forall H\Bigl((\operatorname{NE}(H)
\land\forall s(s\in H\to\operatorname{Sub}(s,p)))
\to\exists s\bigl(s\in H\land
\forall t((t\in H\land\operatorname{Sub}(s,t))\to s=t)\bigr)\Bigr).
\end{aligned}
\tag{D36}
\]

这里的极大成员只要求在所选的 \(H\) 内没有严格包含它的成员，并不要求它包含 \(H\) 的所有成员。

### 12.1 D14 推出 D36

首先，有限集的幂集有限：对 \(p\) 用 F-Ind。空集的幂集是只含空集的单点集，故有限。向 \(p\) 添入 \(x\) 后，新幂集的每个成员要么是旧的子集，要么是向一个旧子集添入 \(x\) 的结果；反向这些结果都是新集合的子集。因此新幂集等于旧幂集与其“添入 \(x\)”精确像的并。用有限像及有限并引理，归纳步成立。

其次，一个非空有限集合族在包含关系下具有极大成员。用 F-Ind 证明“空族或存在极大成员”：空族步直接成立；添入新成员 \(t\) 时，若原族为空则选 \(t\)。否则取原族的极大成员 \(s\)：若 \(s\subseteq t\)，选 \(t\)；若不包含，仍选 \(s\)。第一种选择中，若旧成员 \(v\) 包含 \(t\)，则也包含 \(s\)，原极大性给 \(v=s\)，从 \(s\subseteq t\subseteq v=s\) 得 \(t=v\)。第二种选择中，新成员不包含 \(s\)，旧成员又不能严格包含 \(s\)，所以极大性保留。

现在假设 `Fin(p)`，并任取 D36 前提中的 \(H\)。它是有限幂集的子集，由 F-Sub 有限，又由前提非空，所以存在所需极大成员。得到 `TarskiFinite(p)`。

### 12.2 D36 推出基于双射的 D14

假设 `TarskiFinite(p)`。取 \(p\) 的幂集 \(P\)，再在 \(P\) 上分离得到 \(H\)，满足

\[
\forall s\bigl(s\in H\leftrightarrow(s\in P\land\operatorname{Fin}(s))\bigr).
\]

其中 `Fin` 始终按 D14 展开为“与某自然数存在双射”。由 F-Empty，空集属于 \(H\)，故 \(H\) 非空；它的每个成员都是 \(p\) 的子集。因此 D36 给某个极大成员 \(s\in H\)，尤其 `Fin(s)`。

若存在 \(x\in p\) 而 \(x\notin s\)，取向 \(s\) 添入 \(x\) 的结果 \(t\)。由 F-Adjoin，`Fin(t)`；又逐元素有 \(t\subseteq p\)，所以 \(t\in H\)。因为 \(s\subseteq t\)，极大性给 \(s=t\)，与 \(x\in t\) 且 \(x\notin s\) 矛盾。

因此 \(p\subseteq s\)。另一方面 \(s\in H\) 给 \(s\subseteq p\)，外延得 \(p=s\)，由 `Fin(s)` 得 `Fin(p)`。关闭 \(s,H,P\) 等见证，得到 D36 蕴含 D14。这一方向使用的是已经通过延长双射证明的 F-Adjoin。

由此，在 ZF 中

\[
\forall p\,(\operatorname{Fin}(p)\leftrightarrow\operatorname{TarskiFinite}(p)).
\tag{Finite-Equiv}
\]

这说明 D36 与基于双射的 D14 在 ZF 中等价，且不需要选择公理。本文的分割定义实际采用的是 D14；本节只证明它与另一种有限性刻画的关系。

## 13. 递归展开清单与检查边界

### 13.1 无循环依赖

| 定义层 | 记号 | 展开后依赖 |
|---|---|---|
| 直接原子层 | `Empty`、`NE`、`Sub`、`Sing`、`Pair`、`Adjoin`、`UnionTwo`、`Inter`、`Remove` | 只有 \(\in,=\) 及逻辑符号 |
| 直接原子层 | `FilterBase`（D34） | 右端已经完整展开 |
| 自然数与函数图 | `Succ`、`Inductive`、`Omega`、`Nat`、`Map`、`Bij` | N1–N6；最终依赖基本集合编码 |
| 数量意义的有限性 | `Fin`（D14） | `Nat` 与 `Bij`；二者各自展开，不依赖 `Fin` |
| 集合编码 | `Pow`、`K`、`At`、`Tri` | D3、D5、D6、D11 |
| 序加结构 | `LE`、`Positive`、`Upper`、`Sup`、`Order`、`AddGraph`、`GroupLaws`、`Translate`、`Dense`、`Complete`、`Context` | 本层无环的依赖及集合编码 |
| 分割与阈值 | `Interval`、`Part`、`Space`、`Adjacent`、`Gap`、`Fine` | `Fin`、序加关系及本层无环的依赖 |
| 滤基构造 | `Slice`、`Family` | `Positive`、`Fine`；`Family` 的右端直接写出成员双条件 |
| 附加解释 | `Mesh`、`TarskiFinite` | 前面定义；不被主定理反向依赖 |

展开算法是：选择一个定义调用；把其右端全部束缚变量改为新鲜变量；代入实际变量；替换调用；重复直到没有定义调用。定义集中区的前向引用不构成循环；依赖图是有限有向无环图，因此沿定义依赖递归展开必终止。它不是“假定这些符号也算原始语言”。

### 13.2 三种成员层次

在主定理的解释中，关系是：

- 一个分点 \(x\) 是分割 \(U\) 的元素；
- 一个分割 \(U\) 是某个阈值集合 \(V\) 的元素，同时也是分割空间 \(X\) 的元素；
- 一个阈值集合 \(V\) 是基族 \(B\) 的元素。

正式地，`Part` 保证分点属于区间；`Slice` 保证成员是满足细度条件的分割；`Family` 保证基族恰好收集全部正阈值对应的集合。

### 13.3 与固定分点加细方式的区别

本篇没有使用下面的成员条件来定义滤基：

\[
\exists p\bigl(p\in X\land\forall U(U\in V\leftrightarrow(U\in X\land\operatorname{Sub}(p,U)))\bigr).
\]

该式要求每个成员分割包含某个固定 \(p\)，会额外固定内部分点。D33 则只固定一个正阈值。分割可以极细而避开某个预先指定的内部分点，因此这两种构造不能直接混同。

### 13.4 语义及逻辑检查

| 检查项 | 本文处理 |
|---|---|
| “有限”是否仍是黑箱 | D14 明确采用自然数双射；N1–N6 继续展开自然数、函数图与双射；第 4 节推导所需性质 |
| 是否把实数运算当作原始符号 | D11–D25 给集合编码及结构条件；正式定义中没有加法、减法或细度函数项 |
| 是否有无条件集合概括 | 每次构造给出母集：\(R\)、某个已有集合、它的幂集或有限积 |
| 阈值是否依赖单个分割 | D33 的量词顺序为 \(\exists d\forall U\)，对整个成员统一选阈值 |
| 每个正阈值的成员非空是否已证明 | 第 7 节从完备性与序加性质证明 P-FineExists；第 9.3 节应用 |
| 是否证明通常最大细度存在 | 第 10 节证明非空有限间距集、最大值存在唯一，以及 Mesh-Equiv |
| 是否用到选择公理 | 没有；每个见证均在局部子证明中消去，没有选择一族见证函数 |
| 最终是否有自由变量 | T 的全部结构参数、端点及构造结果都有明确量词 |
| 是否声称完全机器形式化 | 没有；这是可展开的一阶定义及有明确引理依据的数学证明，未声称经过证明助手内核检验 |

### 13.5 定义层的机械语法检查

已对 D1–D36 及 N1–N6 共 42 条定义的右端进行一阶公式语法解析，检查每个定义的实参数量和自由变量集合，并检查所有定义调用都有对应定义、依赖图无环；集中区允许前向引用。对 T 作避免变量捕获的递归展开后，所得公式没有自由变量，没有剩余定义调用，原子式只含成员关系或等词。定义标签唯一，公式分隔符配对，正式定义未使用有界量词。

这项检查验证的是语法、参数和展开链；各证明步骤的数学有效性仍由前文所列公理、推理与引理支持，不等同于证明助手内核认证。
