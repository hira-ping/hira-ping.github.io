+++
title = "写像"
weight = 20
date = 2026-08-09
+++

写像は数学で空気のように使われる概念だが、集合論の土台の上では順序対の集合として厳密に構成される。どの公理が使われているかを意識しながら、順序対 → 直積 → 関係 → 写像の順に組み上げていく。

---

{{< toc >}}

---

## ステップ1：順序対の定義

$a$ が第1成分、$b$ が第2成分という順序の情報を、集合の等号だけで実現する必要がある。Kuratowski の定義では、順序対 $\langle a, b \rangle$ を次の集合で表す。

$$\langle a, b \rangle := \{\{a\}, \{a, b\}\}$$

対の公理により $\{a\}$ と $\{a,b\}$ が存在し、再び対の公理によりこの集合が存在する。

### 順序対の特徴づけ定理

$$\langle a, b \rangle = \langle c, d \rangle \iff a = c \land b = d$$

**証明.** $(\Leftarrow)$ は明らか。$(\Rightarrow)$ を示す。$\{\{a\},\{a,b\}\} = \{\{c\},\{c,d\}\}$ を仮定する。

**場合1:** $a = b$ のとき。左辺は $\{\{a\}\}$（単集合）。$c \neq d$ とすると右辺は2要素集合となり矛盾。よって $c = d$。右辺は $\{\{c\}\}$ となるから $\{a\} = \{c\}$、すなわち $a = c$。また $b = a = c = d$。

**場合2:** $a \neq b$ のとき。$c = d$ とすると右辺は $\{\{c\}\}$（単集合）となるが、左辺は2要素集合なので矛盾。
よって $c \neq d$。$\{a\} \neq \{c,d\}$ だから $\{a\} = \{c\}$、すなわち $a = c$。
$\{a,b\} \neq \{c\}$ だから $\{a,b\} = \{c,d\}$。$a = c$ と合わせて $\{a,b\} = \{a,d\}$。$a \neq b$ より $b = d$。$\square$

> **使用公理:** 対の公理（$\{a\}, \{a,b\}, \langle a,b\rangle$ の存在）、外延性の公理（集合の等号）

---

## ステップ2：直積の定義

集合 $A, B$ に対して直積 $A \times B$ を構成する。

$a \in A$, $b \in B$ のとき、

$$\{a\} \subseteq A \cup B, \quad \{a,b\} \subseteq A \cup B$$

だから $\langle a,b \rangle = \{\{a\},\{a,b\}\} \in \mathcal{P}(\mathcal{P}(A \cup B))$。

よって分出公理により、以下が集合として存在する。

$$A \times B := \{ z \in \mathcal{P}(\mathcal{P}(A \cup B)) \mid \exists a \in A,\, \exists b \in B,\, z = \langle a, b \rangle \}$$

> **例:** $A = \{1,2\}$、$B = \{x,y\}$ のとき $A \times B = \{\langle 1,x\rangle, \langle 1,y\rangle, \langle 2,x\rangle, \langle 2,y\rangle\}$。

### 使用公理の整理

```
対の公理        → {a}, {a,b} の存在
和集合の公理    → A∪B の存在
冪集合の公理    → P(A∪B), P(P(A∪B)) の存在
分出公理図式    → A×B を P(P(A∪B)) から切り出す
```
---

## ステップ3：二項関係の定義

$A \times B$ の部分集合 $R \subseteq A \times B$ を $A$ から $B$ への**二項関係**という。$\langle a,b\rangle \in R$ のとき「 $a \mathrel{R} b$ 」と書く。

$A$ 上の二項関係が下表の定義を満たすとき、その関係は対応する性質を持つと言う。もちろん、ある関係が常にそれらの性質を持っているとは限らない。

| 性質 | 定義 |
| :--- | :--- |
| 反射律 | $\forall a \in A,\; a \mathrel{R} a$ |
| 対称律 | $\forall a,b \in A,\; a \mathrel{R} b \Rightarrow b \mathrel{R} a$ |
| 推移律 | $\forall a,b,c \in A,\; (a \mathrel{R} b \land b \mathrel{R} c) \Rightarrow a \mathrel{R} c$ |
| 反対称律 | $\forall a,b \in A,\; (a \mathrel{R} b \land b \mathrel{R} a) \Rightarrow a = b$ |

反射律・対称律・推移律をすべて満たすとき**同値関係**、反射律・反対称律・推移律をすべて満たすとき**半順序関係**という。

---

## ステップ4：写像の定義

二項関係 $F \subseteq A \times B$ が次を満たすとき、$F$ を $A$ から $B$ への**写像**（関数）といい $f: A \to B$ と書く。

$$\forall a \in A,\; \exists! b \in B,\; \langle a, b \rangle \in F$$

（$A$ の各元に対し、$B$ の元がちょうど一つ対応する。参照：一意存在量化記号）

$f(a)$ は $\langle a,b\rangle \in F$ となる一意な $b$ として定義される。写像の実体は順序対の集合である。

> **例:** $f: \{1,2\} \to \{3,4\}$、$f(1)=3$、$f(2)=4$ の実体は $F = \{\langle 1,3\rangle, \langle 2,4\rangle\}$ という集合。

### 定義域・終域・値域

写像 $f: A \to B$ において：

- $A$ を $f$ の**定義域**という。
- $B$ を $f$ の**終域**という。
- 像 $f(A) \subseteq B$ を $f$ の**値域**という。

> **終域と値域の違い：** 終域 $B$ と値域 $f(A)$ は一般に異なる。値域は終域の部分集合 $f(A) \subseteq B$ であり、等号が成り立つのは $f$ が全射のとき（すなわち $f(A) = B$ のとき）に限る。終域は写像の行き先として許される範囲を宣言するものであり、実際に到達する値域とは別の概念である。

### 恒等写像

集合 $A$ に対して、**恒等写像** $\mathrm{id}_A: A \to A$ を

$$\mathrm{id}_A(a) := a \quad (\forall a \in A)$$

で定める。順序対の集合としての実体は、$A$ の対角集合

$$\mathrm{id}_A := \{ \langle a, a \rangle \mid a \in A \} = \{ z \in A \times A \mid \exists a \in A,\, z = \langle a, a \rangle \} \subseteq A \times A$$

であり、分出公理によって $A \times A$ から切り出せる。$\forall a \in A,\, \exists! b \in A,\, \langle a,b\rangle \in \mathrm{id}_A$（一意な $b$ は $a$ 自身）が成り立つので、これは確かに写像の定義を満たす。

恒等写像は常に全単射であり、任意の写像 $f: A \to B$ に対して

$$f \circ \mathrm{id}_A = f, \qquad \mathrm{id}_B \circ f = f$$

が成り立つ。逆写像の定義（後述）はこの $\mathrm{id}_A$ を基準にする：$f^{-1} \circ f = \mathrm{id}_A$、$f \circ f^{-1} = \mathrm{id}_B$。

---

## 単射・全射・全単射

写像 $f: A \to B$ に対して：

**単射:** $\forall a_1, a_2 \in A,\; f(a_1) = f(a_2) \Rightarrow a_1 = a_2$

異なる元は異なる先に送られる。

**全射:** $\forall b \in B,\; \exists a \in A,\; f(a) = b$

$B$ のすべての元が届く先として現れる。

**全単射:** 単射かつ全射。

全単射 $f: A \to B$ が存在するとき、$A$ と $B$ は**対等**であるといい $A \sim B$ と書く。これは集合の大きさを比較する概念（濃度）の基礎をなす。

### 合成写像と逆写像

$f: A \to B$、$g: B \to C$ のとき、**合成写像** $g \circ f: A \to C$ を

$$(g \circ f)(a) := g(f(a))$$

で定める。実体は $\{\langle a, g(f(a))\rangle \mid a \in A\} \subseteq A \times C$。

$f: A \to B$ が全単射のとき、**逆写像** $f^{-1}: B \to A$ を

$$f^{-1}(b) := \text{「 $f(a) = b$ となる一意な $a$ 」}$$

で定める。$f^{-1} \circ f = \mathrm{id}_A$、$f \circ f^{-1} = \mathrm{id}_B$（$\mathrm{id}$ は恒等写像）が成り立つ。

---

## 像と逆像

写像 $f: A \to B$ に対して、部分集合 $S \subseteq A$ および $T \subseteq B$ の像・逆像を定める。

### 像

$$f(S) := \{b \in B \mid \exists a \in S,\; f(a) = b\}$$

$S$ の元を $f$ で送った先全体の集合。分出公理により $B$ から切り出せる。

> **例:** $f: \mathbb{Z} \to \mathbb{Z}$、$f(n) = n^2$、$S = \{-2,-1,0,1,2\}$ のとき $f(S) = \{0,1,4\}$。

### 逆像

$$f^{-1}(T) := \{a \in A \mid f(a) \in T\}$$

$T$ の元に届く$A$ の元全体の集合。分出公理により $A$ から切り出せる。$f$ が全単射でなくても逆像は定義できる点に注意する。

> **例:** $f: \mathbb{Z} \to \mathbb{Z}$、 $f(n) = n^2$、$T = \{1, 4\}$ のとき $f^{-1}(T) = \{-2,-1,1,2\}$。

### 像と逆像の非対称性

写像 $f: A \to B$、$S, S' \subseteq A$、$T, T' \subseteq B$ に対して、像と逆像のふるまいには顕著な違いがある。**逆像はすべての集合演算（$\cup, \cap, \setminus, ^c$）を保存する**が、**像は $\cup$ 以外との相性が悪く、一般には包含関係しか成り立たない。**

ここではその決定的な違いが現れる性質のみを抜粋する（その他の基本的な公式は[実践コレクション：集合論](#)を参照）。

#### 1. 像の基本補題
- **$a \in S \implies f(a) \in f(S)$**

#### 2. 共通部分の保存
- **逆像:** $f^{-1}(T \cap T') = f^{-1}(T) \cap f^{-1}(T')$
- **像:** $f(S \cap S') \subseteq f(S) \cap f(S')$ （※一般に等号は成立しない）

#### 3. 差集合の保存
- **逆像:** $f^{-1}(T \setminus T') = f^{-1}(T) \setminus f^{-1}(T')$
- **像:** $f(S \setminus S') \supseteq f(S) \setminus f(S')$ （※一般に等号は成立しない）

#### 4. 像と逆像の合成（往復）
一度写して戻す、あるいは戻して写すと、元の集合から情報が欠落する（あるいは余分なものが混ざる）ことがある。
- **引き戻し:** $f^{-1}(f(S)) \supseteq S$ （※等号成立は $f$ が単射のとき）
- **押し出し:** $f(f^{-1}(T)) \subseteq T$ （※等号成立は $f$ が全射のとき）

> **なぜ逆像の方が行儀がよいのか？**
>
> この決定的な違いの理由は、定義の条件式の構造にある。
>
> 逆像の定義は量化記号を含まない：
> $$a \in f^{-1}(T) \iff f(a) \in T$$
> だから $\cap$ や $\setminus$ との交換が、命題論理の同値変形だけで一行で示せる。
>
> 一方、像の定義には存在量化子（$\exists$）が入る：
> $$b \in f(S) \iff \exists a \in S,\; f(a) = b$$
> $\cap$ で等号が一般に成立しない理由は、$\exists$ が $\land$ と無条件には交換できないことに帰着する。一般に
> $$\not\vdash (\exists v\,\phi \land \exists v\,\psi) \to \exists v\,(\phi \land \psi)$$
> であり、$S$ についての $\exists$ と $S'$ についての $\exists$ を一つの $\exists$ にまとめることはできない（異なる $a$ が同じ $b$ に飛ぶ可能性があるため）。

#### 重要な証明と反例

**証明（像の基本補題）**

像に関する命題の土台となるのが、この一見自明に見える命題である。一階述語論理のレベルで厳密に証明し、なぜ逆が成り立たないのかを確認しておく。

写像 $f: A \to B$ と部分集合 $S \subseteq A$ について、任意の $a \in A$ に対し次が成り立つことを示す。

$$a \in S \implies f(a) \in f(S)$$

$a \in S$ を仮定する。自明な等式 $f(a) = f(a)$ と組み合わせることで、以下が成り立つ。

$$a \in S \land f(a) = f(a)$$

ここから存在汎化（$\exists$-導入）を行えば、次が得られる。

$$\exists x, a \in S \land f(a) = f(a)$$

あるいは同じ意味だが、$\exists x \in S, f(x) = f(a)$（量化記号への条件付けの記法）

像の定義 $f(S) := \{b \in B \mid \exists x \in S,\; f(x) = b\}$ において $b$ を $f(a)$ と置けば、上の論理式は $f(a)$ が $f(S)$ に属するための条件そのものである。したがって $f(a) \in f(S)$ が導かれる。$\square$

**逆が成り立たない理由**

この命題の逆、すなわち

$$f(a) \in f(S) \implies a \in S$$

は、一般には**偽**である。

$f(a) \in f(S)$ が意味するのは、$S$ の中に、$a$ と同じ行き先になる要素 $x$ が（少なくとも一つ）存在することだけであり、$a$ 自身が $S$ に入っていることまでは保証しないためである。

**反例:**
$A = \{1, 2\}, B = \{0\}$ とし、$f(1) = 0, f(2) = 0$ という写像を考える。
部分集合 $S = \{1\}$ とし、$a = 2$ とする。
- 像は $f(S) = \{f(1)\} = \{0\}$ である。
- $f(a) = f(2) = 0$ なので、$f(a) \in f(S)$ は真である。
- しかし、$a = 2 \notin \{1\} = S$ なので、$a \in S$ は偽である。

逆が成り立つ（$f(a) \in f(S) \implies a \in S$ が言える）ためには、$f$ が**単射**（行き先が同じなら元の要素も同じ）であるという追加の制約が必要である。

> **注記：素朴な記法 $\{f(a) \mid a \in S\}$ の危うさ**
> 
>数学の教科書には、像の定義が $f(S) = \{f(a) \mid a \in S\}$ と記述されていることがある。しかし、公理的集合論の厳密な立場から言えば、この記法は不正確である。
> 
> ZFCにおいて集合を構成する場合（分出公理）、必ずどの既存の集合からどのような論理式で切り出すかを明示しなければならない。
>正しくは、終域 $B$ を母集合とし、存在量化子 $\exists$ を用いて
>
> $$ f(S) = \{ b \in B \mid \exists a \in S, f(a) = b \} $$
>
>と構成される。
> 
> $\exists$ を隠蔽してしまう $\{f(a) \mid a \in S\}$ という定義で考えると、定理の証明で行き詰まるおそれがある。像のふるまいが逆像に比べて直感に反する（$\cap$ や $\setminus$ を一般には保存しない）本質的な理由は、この$\exists$の非可換性にあるからである。

---

**証明（像の共通部分は包含のみ）**

$$\begin{align*}
b \in f(S \cap S') &\iff \exists a,\; a \in S \land a \in S' \land f(a) = b \\
&\implies (\exists a \in S,\; f(a) = b) \land (\exists a \in S',\; f(a) = b) \\
&\iff b \in f(S) \cap f(S').
\end{align*}$$

逆方向は一般に成立しない。

反例： $f: \{1,2\} \to \{0\}$、$f(1)=f(2)=0$、$S=\{1\}, S'=\{2\}$ のとき $f(S \cap S') = \emptyset$ だが $f(S) \cap f(S') = \{0\}$。$\square$

---

**証明（像の差集合は包含のみ）.**

$b \in f(S) \setminus f(S')$ と仮定する。
1. $b \in f(S) \iff \exists a \in S,\, f(a) = b$
2. $b \notin f(S') \iff \lnot (\exists x \in S',\, f(x) = b) \iff \forall x \in S',\, f(x) \neq b$

(1)より $f(a) = b$ となる $a \in S$ が存在する。もし $a \in S'$ とすると、(2)の全称命題より $f(a) \neq b$ となり矛盾する。よって $a \notin S'$ である。
以上より、この $a$ は $a \in S \setminus S'$ であり $f(a) = b$ を満たすため、像の定義より $b \in f(S \setminus S')$ となる。
逆方向は一般に成立しない。

反例： $f: \{1,2\} \to \{0\}$、$f(1)=f(2)=0$、$S=\{1,2\}, S'=\{1\}$ のとき $f(S \setminus S') = \{0\}$ だが $f(S) \setminus f(S') = \emptyset$。$\square$

---

**証明（像と逆像の往復）.**

$f^{-1}(f(S)) \supseteq S$ の証明：

$a \in S \implies f(a) \in f(S) \iff a \in f^{-1}(f(S))$。

（逆方向の反例： $f: \{1,2\} \to \{0\}$、$f(1)=f(2)=0$、$S=\{1\}$ のとき $f^{-1}(f(S)) = \{1,2\} \supsetneq S$）

$f(f^{-1}(T)) \subseteq T$ の証明：

$b \in f(f^{-1}(T)) \iff \exists a \in f^{-1}(T),\; f(a) = b \iff \exists a,\; f(a) \in T \land f(a) = b \implies b \in T$。

（逆方向の反例： $f: \{1\} \to \{0,1\}$、$f(1)=0$、$T=\{0,1\}$ のとき $f(f^{-1}(T)) = \{0\} \subsetneq T$）$\square$

> 逆像の方が像より性質がよい理由は、定義の条件式の構造にある。
>
> 逆像の定義は量化記号を含まない：
> $$a \in f^{-1}(T) \iff f(a) \in T$$
> だから $\cup$・$\cap$・補集合との交換が、論理式の同値変換だけで一行で示せる。
>
> 一方、像の定義には $\exists$ が入る：
> $$b \in f(S) \iff \exists a \in S,\; f(a) = b$$
> $\cap$ で等号が一般に成立しない理由は、$\exists$ が $\land$ と交換できないことに帰着する。一般に
> $$\not\vdash (\exists v,\phi \land \exists v,\psi) \to \exists v,(\phi \land \psi)$$
> であり、$S$ についての $\exists$ と $S'$ についての $\exists$ を一つの $\exists$ にまとめることはできない。
>
>これが $f(S \cap S') \subseteq f(S) \cap f(S')$ で等号が一般に成立しない本質的な理由である。
