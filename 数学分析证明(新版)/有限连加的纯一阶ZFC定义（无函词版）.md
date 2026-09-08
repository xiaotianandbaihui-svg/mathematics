# 有限连加的纯一阶 ZFC 定义（无函词版）

## 1. 形式语言

严格来说，“使用 ZFC”与“除等号外不允许任何谓词”不能同时成立，因为 ZFC 必须使用二元关系符号

$$
\in.
$$

因此本文采用的基础语言是

$$
\mathcal L_{\in}=\{\in,=\},
$$

其中：

- \(\in\) 是唯一的非逻辑谓词；
- \(=\) 是逻辑等词；
- 没有常量符号；
- 没有函数符号；
- 没有其他原始谓词。

逻辑联结词以

$$
\neg,\qquad\to,\qquad\forall
$$

为基础。

本文出现的 \(\operatorname{Nat}\)、\(\operatorname{Seq}\)、\(\operatorname{Val}\) 等都不是新增的原始谓词，而只是可以消去的公式缩写。

---

## 2. 逻辑缩写

定义

$$
\varphi\land\psi
\quad:\Longleftrightarrow\quad
\neg(\varphi\to\neg\psi),
$$

$$
\varphi\lor\psi
\quad:\Longleftrightarrow\quad
\neg\varphi\to\psi,
$$

$$
\varphi\leftrightarrow\psi
\quad:\Longleftrightarrow\quad
(\varphi\to\psi)\land(\psi\to\varphi),
$$

$$
\exists x\,\varphi
\quad:\Longleftrightarrow\quad
\neg\forall x\,\neg\varphi.
$$

唯一存在定义为

$$
\exists!x\,\varphi(x)
\quad:\Longleftrightarrow\quad
\exists x\left[
\varphi(x)\land
\forall y\bigl(\varphi(y)\to y=x\bigr)
\right],
$$

其中 \(y\) 是不在 \(\varphi\) 中发生变量捕获的新变量。

---

## 3. 空集、子集、后继和自然数

### 3.1 空集

$$
\boxed{
\operatorname{Empty}(e)
\quad:\Longleftrightarrow\quad
\forall x\,\neg(x\in e).
}
$$

### 3.2 子集

$$
\boxed{
\operatorname{Sub}(x,y)
\quad:\Longleftrightarrow\quad
\forall z\,(z\in x\to z\in y).
}
$$

### 3.3 单元素集

$$
\boxed{
\operatorname{Sing}(x,s)
\quad:\Longleftrightarrow\quad
\forall z\,(z\in s\leftrightarrow z=x).
}
$$

### 3.4 无序对

$$
\boxed{
\operatorname{UPair}(x,y,p)
\quad:\Longleftrightarrow\quad
\forall z\left[
z\in p\leftrightarrow(z=x\lor z=y)
\right].
}
$$

### 3.5 后继

$$
\boxed{
\operatorname{Succ}(x,y)
\quad:\Longleftrightarrow\quad
\forall z\left[
z\in y\leftrightarrow(z\in x\lor z=x)
\right].
}
$$

它表达

$$
y=x\cup\{x\},
$$

但右边只用于解释，并不是基础语言中的函数项。

### 3.6 归纳集

$$
\boxed{
\begin{aligned}
\operatorname{Ind}(w)
\quad:\Longleftrightarrow\quad&
\exists e\bigl(
\operatorname{Empty}(e)\land e\in w
\bigr)
\\
&\land
\forall x\left[
x\in w\to
\exists y\bigl(
\operatorname{Succ}(x,y)\land y\in w
\bigr)
\right].
\end{aligned}
}
$$

### 3.7 自然数集

$$
\boxed{
\operatorname{Omega}(w)
\quad:\Longleftrightarrow\quad
\operatorname{Ind}(w)
\land
\forall v\bigl(
\operatorname{Ind}(v)\to\operatorname{Sub}(w,v)
\bigr).
}
$$

这表示 \(w\) 是最小归纳集。

### 3.8 自然数

$$
\boxed{
\operatorname{Nat}(n)
\quad:\Longleftrightarrow\quad
\exists w\bigl(
\operatorname{Omega}(w)\land n\in w
\bigr).
}
$$

所以没有把 \(\omega\) 当作原始常量符号。

---

## 4. 有序对和三元组

### 4.1 Kuratowski 有序对

使用集合编码

$$
\langle x,y\rangle=\{\{x\},\{x,y\}\}.
$$

正式公式为

$$
\boxed{
\begin{aligned}
\operatorname{OP}(x,y,p)
\quad:\Longleftrightarrow\quad
\exists s\exists u\bigl[
&\operatorname{Sing}(x,s)
\\
&\land\operatorname{UPair}(x,y,u)
\\
&\land\operatorname{UPair}(s,u,p)
\bigr].
\end{aligned}
}
$$

它表示 \(p\) 是编码后的有序对 \(\langle x,y\rangle\)。

### 4.2 三元组

采用编码

$$
\langle x,y,z\rangle
:=
\langle\langle x,y\rangle,z\rangle.
$$

正式公式为

$$
\boxed{
\operatorname{Triple}(x,y,z,t)
\quad:\Longleftrightarrow\quad
\exists p\bigl(
\operatorname{OP}(x,y,p)
\land
\operatorname{OP}(p,z,t)
\bigr).
}
$$

---

## 5. 函数图和有限序列

### 5.1 函数取值关系

$$
\boxed{
\operatorname{Val}(f,x,y)
\quad:\Longleftrightarrow\quad
\exists p\bigl(
p\in f\land\operatorname{OP}(x,y,p)
\bigr).
}
$$

它表示函数图 \(f\) 中包含有序对 \(\langle x,y\rangle\)。

### 5.2 函数图

$$
\boxed{
\begin{aligned}
\operatorname{Fun}(f)
\quad:\Longleftrightarrow\quad&
\forall p\left[
p\in f\to
\exists x\exists y\,\operatorname{OP}(x,y,p)
\right]
\\
&\land
\forall x\forall y\forall z
\left[
\bigl(
\operatorname{Val}(f,x,y)
\land
\operatorname{Val}(f,x,z)
\bigr)
\to y=z
\right].
\end{aligned}
}
$$

第一部分排除函数图中的“垃圾元素”，第二部分保证同一输入至多有一个输出。

### 5.3 定义域

$$
\boxed{
\operatorname{Dom}(f,d)
\quad:\Longleftrightarrow\quad
\forall x\left[
x\in d
\leftrightarrow
\exists y\,\operatorname{Val}(f,x,y)
\right].
}
$$

### 5.4 有限序列

$$
\boxed{
\begin{aligned}
\operatorname{Seq}(a,n,A)
\quad:\Longleftrightarrow\quad&
\operatorname{Nat}(n)
\land\operatorname{Fun}(a)
\land\operatorname{Dom}(a,n)
\\
&\land
\forall x\forall y
\bigl(
\operatorname{Val}(a,x,y)\to y\in A
\bigr).
\end{aligned}
}
$$

当 \(n\) 是 von Neumann 自然数时，

$$
n=\{0,1,\ldots,n-1\}.
$$

因此 \(\operatorname{Seq}(a,n,A)\) 表示 \(a\) 是一个具有 \(n\) 项的 \(A\)-值有限序列。

---

## 6. 二元运算图

### 6.1 运算取值关系

设 \(g\) 是由三元组编码的集合。定义

$$
\boxed{
\operatorname{OpVal}(g,x,y,z)
\quad:\Longleftrightarrow\quad
\exists t\bigl(
t\in g\land\operatorname{Triple}(x,y,z,t)
\bigr).
}
$$

它表示按照运算图 \(g\)，输入 \(x,y\) 的结果是 \(z\)。

### 6.2 二元运算

$$
\boxed{
\begin{aligned}
\operatorname{BinOp}(A,g)
\quad:\Longleftrightarrow\quad&
\forall t\Bigl[
t\in g\to
\exists x\exists y\exists z
\bigl(
x\in A\land y\in A\land z\in A
\\
&\hspace{10em}\land
\operatorname{Triple}(x,y,z,t)
\bigr)
\Bigr]
\\
&\land
\forall x\forall y
\Bigg[
(x\in A\land y\in A)
\to
\exists z
\Bigg(
z\in A
\land\operatorname{OpVal}(g,x,y,z)
\\
&\hspace{8em}\land
\forall r\left[
\bigl(
r\in A\land\operatorname{OpVal}(g,x,y,r)
\bigr)
\to r=z
\right]
\Bigg)
\Bigg].
\end{aligned}
}
$$

它同时保证：

1. \(g\) 中没有不合法的三元组；
2. 对每个 \(x,y\in A\)，运算结果存在；
3. 运算结果唯一；
4. 运算结果仍属于 \(A\)。

### 6.3 结合律

$$
\boxed{
\begin{aligned}
\operatorname{Assoc}(A,g)
\quad:\Longleftrightarrow\quad
\forall x\forall y\forall z
\forall u\forall v\forall r\forall s
\Big[
&\bigl(
x\in A\land y\in A\land z\in A
\\
&\land u\in A\land v\in A
\land r\in A\land s\in A
\\
&\land\operatorname{OpVal}(g,x,y,u)
\\
&\land\operatorname{OpVal}(g,u,z,r)
\\
&\land\operatorname{OpVal}(g,y,z,v)
\\
&\land\operatorname{OpVal}(g,x,v,s)
\bigr)
\to r=s
\Big].
\end{aligned}
}
$$

它表达

$$
(x\mathbin{\circ}y)\mathbin{\circ}z
=
x\mathbin{\circ}(y\mathbin{\circ}z),
$$

其中 \(\circ\) 仅用于解释。

### 6.4 半群

$$
\boxed{
\operatorname{Semigroup}(A,g)
\quad:\Longleftrightarrow\quad
\operatorname{BinOp}(A,g)
\land
\operatorname{Assoc}(A,g).
}
$$

---

## 7. 递推累加关系

现在定义从下标 \(0\) 一直加到下标 \(n\) 的有限连加。

首先定义不包含任何代数前提的递推关系：

$$
\boxed{
\begin{aligned}
&\operatorname{Acc}(A,g,a,n,s)
\\
:\Longleftrightarrow\quad&
\operatorname{Nat}(n)
\\
&\land
\exists q\exists P\exists o\exists b
\Bigg[
\operatorname{Succ}(n,q)
\\
&\qquad\land\operatorname{Seq}(a,q,A)
\land\operatorname{Seq}(P,q,A)
\\
&\qquad\land\operatorname{Empty}(o)
\\
&\qquad\land\operatorname{Val}(a,o,b)
\land\operatorname{Val}(P,o,b)
\\
&\qquad\land\operatorname{Val}(P,n,s)
\\
&\qquad\land
\forall k
\Bigg(
k\in n
\to
\exists k'\exists u\exists v\exists r
\Big[
\operatorname{Succ}(k,k')
\\
&\hspace{13em}\land
\operatorname{Val}(P,k,u)
\\
&\hspace{13em}\land
\operatorname{Val}(a,k',v)
\\
&\hspace{13em}\land
\operatorname{OpVal}(g,u,v,r)
\\
&\hspace{13em}\land
\operatorname{Val}(P,k',r)
\Big]
\Bigg)
\Bigg].
\end{aligned}
}
$$

其含义是：

$$
P(0)=a(0),
$$

$$
P(k+1)=P(k)\mathbin{\circ}a(k+1)
\qquad(k<n),
$$

以及

$$
P(n)=s.
$$

这些含函数符号的式子只用于解释；正式定义全部使用 \(\operatorname{Val}\)、\(\operatorname{Succ}\) 和 \(\operatorname{OpVal}\)。

---

## 8. 两种有限连加

### 8.1 固定括号顺序的有限连加

$$
\boxed{
\operatorname{LIncSum}(A,g,a,n,s)
\quad:\Longleftrightarrow\quad
\operatorname{BinOp}(A,g)
\land
\operatorname{Acc}(A,g,a,n,s).
}
$$

它定义的是固定为左结合的结果：

$$
(((a(0)\mathbin{\circ}a(1))
\mathbin{\circ}a(2))
\cdots)
\mathbin{\circ}a(n).
$$

只要 \(g\) 是二元运算，递推结果就存在且唯一；这里不需要结合律。

### 8.2 通常意义下的有限连加

$$
\boxed{
\operatorname{IncSum}(A,g,a,n,s)
\quad:\Longleftrightarrow\quad
\operatorname{Semigroup}(A,g)
\land
\operatorname{Acc}(A,g,a,n,s).
}
$$

当 \(\operatorname{IncSum}(A,g,a,n,s)\) 成立时，通常记作

$$
s=\sum_{k=0}^{n}a(k).
$$

这个等式不是基础语言中的原始公式，而是上述关系公式的数学缩写。

由于 \(g\) 满足结合律，改变有限表达式中的括号不会改变结果。

---

## 9. 边界检查

### 9.1 \(n=0\)

此时 \(q\) 是 \(0\) 的后继，\(a\) 和 \(P\) 都只有下标 \(0\)。

递推条件

$$
\forall k\,(k\in n\to\cdots)
$$

为空真，因此

$$
P(0)=a(0),
\qquad
s=P(0)=a(0).
$$

所以

$$
\sum_{k=0}^{0}a(k)=a(0).
$$

### 9.2 \(n=1\)

递推只有 \(k=0\) 这一步：

$$
P(1)=P(0)\mathbin{\circ}a(1)
=a(0)\mathbin{\circ}a(1).
$$

### 9.3 \(n=2\)

$$
P(2)
=
\bigl(a(0)\mathbin{\circ}a(1)\bigr)
\mathbin{\circ}a(2).
$$

若 \(g\) 满足结合律，则它也等于

$$
a(0)\mathbin{\circ}
\bigl(a(1)\mathbin{\circ}a(2)\bigr).
$$

---

## 10. 存在唯一性定理

ZFC 可以证明：

$$
\boxed{
\begin{aligned}
\forall A\forall g\forall a\forall n
\Bigg[
&\operatorname{Semigroup}(A,g)
\land\operatorname{Nat}(n)
\\
&\land
\exists q\bigl(
\operatorname{Succ}(n,q)
\land\operatorname{Seq}(a,q,A)
\bigr)
\\
&\to
\exists!s\,
\operatorname{IncSum}(A,g,a,n,s)
\Bigg].
\end{aligned}
}
$$

证明使用自然数有限递归定理：

1. 初始值 \(P(0)=a(0)\) 由 \(a\) 的函数性质唯一确定；
2. 若 \(P(k)\) 已确定，则由于 \(g\) 是二元运算，

   $$
   P(k+1)=P(k)\mathbin{\circ}a(k+1)
   $$

   存在且唯一；
3. 对 \(k\) 作自然数归纳，得到唯一的累加函数图 \(P\)；
4. \(P(n)\) 存在且唯一，因此最终结果 \(s\) 存在且唯一。

定义本身只规定合法的 \(P,s\) 必须满足什么；真正保证它们存在且唯一的是 ZFC 中的有限递归定理。

以上四点是有限递归定理在通常数学语言中的证明提纲，并不是逐行只使用 MP 规则写出的希尔伯特式形式证明。本文完整展开的是“连加关系及其所用公式缩写”；若还要把有限递归定理的证明也展开为希尔伯特系统中的每一行推演，需要另行形式化 ZFC 公理、自然数归纳定理和递归定理。

---

## 11. 整数连加

若 \(A\) 取为按照 ZFC 构造的整数集合，\(g\) 取为整数加法的运算图，则已经可以证明

$$
\operatorname{Semigroup}(A,g).
$$

这时

$$
\operatorname{IncSum}(A,g,a,n,s)
$$

就表示整数序列的有限连加。

整数加法还满足交换律，但交换律不是上述有序连加定义所必需的。

---

## 12. 完全展开性

本文所有大写名称均为以下公式的分层缩写：

$$
\operatorname{IncSum}
\longrightarrow
\operatorname{Semigroup},\operatorname{Acc},
$$

$$
\operatorname{LIncSum}
\longrightarrow
\operatorname{BinOp},\operatorname{Acc},
$$

$$
\operatorname{Semigroup}
\longrightarrow
\operatorname{BinOp},\operatorname{Assoc},
$$

$$
\operatorname{BinOp}
\longrightarrow
\operatorname{Triple},\operatorname{OpVal},
$$

$$
\operatorname{Assoc}
\longrightarrow
\operatorname{OpVal},
$$

$$
\operatorname{Acc}
\longrightarrow
\operatorname{Nat},\operatorname{Succ},
\operatorname{Seq},\operatorname{Empty},
\operatorname{Val},\operatorname{OpVal},
$$

$$
\operatorname{Seq}
\longrightarrow
\operatorname{Nat},\operatorname{Fun},\operatorname{Dom},\operatorname{Val},
$$

$$
\operatorname{Fun}
\longrightarrow
\operatorname{OP},\operatorname{Val},
$$

$$
\operatorname{Dom}
\longrightarrow
\operatorname{Val},
$$

$$
\operatorname{OpVal}
\longrightarrow
\operatorname{Triple},
$$

$$
\operatorname{Val}
\longrightarrow
\operatorname{OP},
$$

$$
\operatorname{Triple}
\longrightarrow
\operatorname{OP},
$$

$$
\operatorname{OP}
\longrightarrow
\operatorname{Sing},\operatorname{UPair},
$$

$$
\operatorname{Nat}
\longrightarrow
\operatorname{Omega},
$$

$$
\operatorname{Omega}
\longrightarrow
\operatorname{Ind},\operatorname{Sub},
$$

$$
\operatorname{Ind}
\longrightarrow
\operatorname{Empty},\operatorname{Succ}.
$$

按照这个顺序逐层替换以后，最终公式中只剩下：

$$
\boxed{
\in,\quad =,\quad \neg,\quad\to,\quad\forall
}
$$

以及变量和括号。

因此没有引入任何函数符号、常量符号或额外的原始谓词。

逐层替换公式缩写时，必须先把缩写内部的约束变量改名为尚未使用的新变量，从而避免变量捕获。这只是约束变量的换名，不改变公式的逻辑意义。

---

## 13. 参考依据

1. [《数理逻辑：证明及其限度（第二版）》](<D:/1_All_Things_Is_Here/math/math_/数理逻辑/数理逻辑：证明及其限度（第二版） (郝兆宽, 杨睿之, 杨跃)).pdf>)：

   - 第 1.4 节：函数作为特殊二元关系；
   - 定义 7.1.1：自然数上的递归定义；
   - 引理 7.1.10：有界连加的递归可定义性。

2. Lean mathlib 的机器形式化：

   - [`Finset.sum_empty`](https://leanprover-community.github.io/mathlib4_docs/Mathlib/Algebra/BigOperators/Group/Finset/Defs.html#Finset.sum_empty)：空和等于加法单位元；
   - [`Finset.range`](https://leanprover-community.github.io/mathlib4_docs/Mathlib/Data/Finset/Range.html#Finset.range)：`range n` 对应 \(0,\ldots,n-1\)；
   - [`Finset.sum_range_succ`](https://leanprover-community.github.io/mathlib4_docs/Mathlib/Algebra/BigOperators/Group/Finset/Basic.html#Finset.sum_range_succ)：

     $$
     \sum_{k<n+1}a(k)
     =
     \left(\sum_{k<n}a(k)\right)+a(n).
     $$

3. ZFC 的自然数递归定理保证累加函数图 \(P\) 的存在性和唯一性。
