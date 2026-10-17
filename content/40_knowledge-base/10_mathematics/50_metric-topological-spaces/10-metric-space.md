+++
title = "距離空間"
weight = 10
date = 2026-10-17
lastmod = 2026-10-17
+++

数直線 $\mathbb{R}$ の上では、二点 $x, y$ の距離として $|x - y|$ を使ってきた。連続性の定義やコーシー列の定義でも、すべてこの距離を通じて近いとか小さいという概念を定式化した。

平面 $\mathbb{R}^2$ や空間 $\mathbb{R}^3$ では、点と点の間の距離は三平方の定理によって自然に定まる。そしてその距離がいくつかの基本的な性質（非負性、同一点であれば距離ゼロ、対称性、三角不等式）を満たすことも直感的に明らかである。

この直感的に明らかな性質を公理として抽出し、それを満たす任意の集合を距離空間と定義する。そうすることで、$\mathbb{R}$・$\mathbb{R}^2$・$\mathbb{R}^3$、さらには関数の集合といった様々な空間が同一の枠組みで扱えるようになる。

---

{{< toc >}}

---

## 出発点：ユークリッド距離

### $\mathbb{R}$ の距離

数直線上の二点 $x, y \in \mathbb{R}$ の距離は、$|x - y|$ である。この関数は次の性質を持つ。

1. $|x - y| \geq 0$、かつ  $|x - y| = 0 \iff x = y$ （非負性、同一点であれば距離ゼロ）
2. $|x - y| = |y - x|$ （非負性、同一点であれば距離ゼロ）
3. $|x - z| \leq |x - y| + |y - z|$  （三角不等式）

実数直線での近い、収束する、連続といった概念は、すべてこの三性質だけを通じて定式化されていた。

### $\mathbb{R}^2$ のユークリッド距離

平面上の二点 $P = (x_1, x_2)$、$Q = (y_1, y_2)$ の距離は、三平方の定理より

$$d(P, Q) = \sqrt{(x_1 - y_1)^2 + (x_2 - y_2)^2}$$

である。この関数も同じ三性質を満たす。三角不等式 $d(P, R) \leq d(P, Q) + d(Q, R)$ は、$P$ から $R$ への直線距離は $Q$ を経由する距離を超えないという幾何的な意味を持つ。

### $\mathbb{R}^3$ のユークリッド距離

空間内の二点 $P = (x_1, x_2, x_3)$、$Q = (y_1, y_2, y_3)$ の距離も同様に

$$d(P, Q) = \sqrt{(x_1 - y_1)^2 + (x_2 - y_2)^2 + (x_3 - y_3)^2}$$

であり、同じ三性質を持つ。

### 共通性質の抽出

$\mathbb{R}$、$\mathbb{R}^2$、$\mathbb{R}^3$ を通じて、距離関数が共通して持つ性質は次の三つである：

- $|x-y| \geq 0$、等号 $\iff$ 同一点 (非負性・同一性)
- $|x-y| = |y-x|$ (対称性)
- $|x-z| \leq |x-y| + |y-z|$ (三角不等式)

これらを距離関数の公理として抽象化する。

---

## 距離空間の定義

### 定義：距離関数・距離空間

集合 $X$ 上の**距離関数**とは、写像 $d: X \times X \to \mathbb{R}$ であって、任意の $x, y, z \in X$ に対して以下の四条件を満たすものをいう：

1. **非負性：** $d(x, y) \geq 0$
2. **非退化性：** $d(x, y) = 0 \iff x = y$
3. **対称性：** $d(x, y) = d(y, x)$
4. **三角不等式：** $d(x, z) \leq d(x, y) + d(y, z)$

集合 $X$ と距離関数 $d$ の組 $(X, d)$ を**距離空間**という。$d$ が文脈から明らかなときは単に $X$ と書く。

> **非負性は冗長：** 非負性は他の三条件から導ける。$2d(x,y) = d(x,y) + d(y,x) \geq d(x,x) = 0$（対称性・三角不等式・非退化性を使用）。公理として明示するのは可読性のためである。

### 基本例

**例1：ユークリッド距離（$\mathbb{R}$）.** $d(x, y) = |x - y|$。
$\mathbb{R}$ の絶対値の性質から各公理が成立する。

**例2：ユークリッド距離（$\mathbb{R}^n$）.** $x = (x_1, \ldots, x_n)$、$y = (y_1, \ldots, y_n)$ に対し

$$d(x, y) = \sqrt{\sum_{i=1}^n (x_i - y_i)^2}$$

三角不等式はコーシー＝シュワルツの不等式から従う。$n = 1, 2, 3$ が上で見たユークリッド距離に対応する。

> **注：** ここでは $\mathbb{R}^n$ を $\mathbb{R}$ の $n$ 個の直積集合として直感的に扱う。ベクトル空間・ノルム空間としての厳密な構成は多変数関数の微積分で扱う。

**例3：離散距離.** 任意の集合 $X$ に対して

$$d(x, y) = \begin{cases} 0 & (x = y) \\ 1 & (x \neq y) \end{cases}$$

と定めると $(X, d)$ は距離空間になる。三角不等式：$x \neq z$ のとき左辺は $1$、右辺は少なくとも $1$。$x = z$ のとき左辺は $0$。

**例4：関数空間の一様距離.** $C([a,b])$ を閉区間 $[a,b]$ 上の連続関数全体とし、

$$d(f, g) = \sup_{x \in [a,b]} |f(x) - g(x)|$$

と定める。最大値定理より $d(f,g) < \infty$。各公理は $\mathbb{R}$ の絶対値から継承される。点が関数であっても距離空間が構成できる。

---

## 点列の収束

### 定義：収束

$(x_n)$ が $a \in X$ に**収束する**とは、

$$\forall \varepsilon > 0, \exists N \in \mathbb{N}, \forall n \geq N; d(x_n, a) < \varepsilon$$

が成り立つことをいい、$x_n \to a$ と書く。

### 命題1：極限の一意性

**証明.** $x_n \to a$ かつ $x_n \to b$ とすると、三角不等式より $d(a,b) \leq d(a, x_n) + d(x_n, b) < \varepsilon$ が任意の $\varepsilon > 0$ で成立。よって $a = b$。$\square$

---

## 開集合・閉集合

### 定義：開球

距離空間 $(X, d)$、点 $a \in X$、実数 $r > 0$ に対して、

$$B(a, r) = \{ x \in X \mid d(x, a) < r \}$$

を中心 $a$、半径 $r$ の**開球**という。

> $\mathbb{R}$ では $B(a, r) = (a-r, a+r)$（開区間）。$\mathbb{R}^2$ では境界を含まない円板、$\mathbb{R}^3$ では球の内部。

### 定義：開集合

$U \subseteq X$ が**開集合**であるとは、

$$\forall a \in U,\; \exists r > 0,\; B(a, r) \subseteq U$$

が成り立つことをいう。

> **直感（$\mathbb{R}^2$）：** 開集合の各点からは、少し動いても集合の外に出ない。境界を含まない円板はその典型例。一方、境界を含む閉円板の境界上の点では、どんな小さな開球も外にはみ出す。

### 命題2：開集合の基本性質

1. $\emptyset$ と $X$ は開集合である。
2. 任意個の開集合の合併は開集合である。
3. 有限個の開集合の共通部分は開集合である。

**証明.**

(1) $\emptyset$ は条件を空虚に満たす。$X$ は任意の $r > 0$ で $B(a,r) \subseteq X$。

(2) $a \in \bigcup_\lambda U_\lambda$ ならばある $U_\lambda$ に $a$ が属し、その $U_\lambda$ の開性よりある $r > 0$ で $B(a,r) \subseteq U_\lambda \subseteq \bigcup_\lambda U_\lambda$。

(3) $a \in \bigcap_{i=1}^n U_i$ ならば各 $i$ でそれぞれ $r_i > 0$ が存在して $B(a, r_i) \subseteq U_i$。$r = \min(r_1, \ldots, r_n) > 0$ とすると $B(a, r) \subseteq \bigcap_{i=1}^n U_i$。$\square$

> **有限性の必要性：** $\mathbb{R}$ で $U_n = (-1/n, 1/n)$ とすると各 $U_n$ は開集合だが 
> $$\bigcap_{n=1}^\infty U_n = \{0\}$$ は開集合でない。

### 定義：閉集合・閉包・内部

$F \subseteq X$ が**閉集合**であるとは、$X \setminus F$ が開集合であることをいう。

$A \subseteq X$ に対して、$A$ を含む最小の閉集合を $A$ の**閉包** $\overline{A}$、$A$ に含まれる最大の開集合を $A$ の**内部** $A^\circ$ という：

$$\overline{A} = \bigcap \{ F \mid F \text{ は閉集合},\; A \subseteq F \}, \qquad A^\circ = \bigcup \{ U \mid U \text{ は開集合},\; U \subseteq A \}$$

> **$\mathbb{R}^2$ での直感：** 
>
>開円板 $U = \{x^2+y^2 < 1\}$ に対し 
>$\overline{U} = \{x^2+y^2 \leq 1\}$（閉円板）、
>$U^\circ = U$。
>
>閉円板 $F = \{x^2+y^2 \leq 1\}$ に対し $\overline{F} = F$、
>$F^\circ = \{x^2+y^2 < 1\}$。
>
>境界円周 $\partial = \overline{A} \setminus A^\circ$ が縁に対応する。

### 命題3：閉包と内部の特徴づけ

#### 閉包の特徴づけ

$$\overline{A} = \{ x \in X \mid \forall r > 0,\; B(x, r) \cap A \neq \emptyset \}$$

**証明.** 右辺を $C$ とおく。$\overline{A} \subseteq C$ と $C \subseteq \overline{A}$ をそれぞれ示す。

**$\overline{A} \subseteq C$ の証明（対偶を示す）：**

$x \notin C$ と仮定する。$C$ の条件を満たさないので、ある $r > 0$ が存在して $B(x, r) \cap A = \emptyset$ となる。

これは $A$ が $B(x, r)$ の外側、すなわち $A \subseteq X \setminus B(x, r)$ であることを意味する。

開球 $B(x, r)$ は開集合であるから、その補集合 $X \setminus B(x, r)$ は閉集合である。

閉包 $\overline{A}$ は$A$ を含むすべての閉集合の共通部分であるため、当然この閉集合 $X \setminus B(x, r)$ にも含まれる。

つまり $\overline{A} \subseteq X \setminus B(x, r)$ であり、これは $B(x, r)$ の中心である $x$ が $\overline{A}$ に属さない（$x \notin \overline{A}$）ことを示している。対偶が示されたため、$\overline{A} \subseteq C$ である。

**$C \subseteq \overline{A}$ の証明：**

$F$ を$A$ を含む任意の閉集合（すなわち $A \subseteq F$）とする。

$C \subseteq F$ であることを、対偶 $x \notin F \Rightarrow x \notin C$ によって示す。

$x \notin F$ とすると、$x \in X \setminus F$ である。$F$ は閉集合なので、$X \setminus F$ は開集合である。

開集合の定義より、ある $r > 0$ が存在して $B(x, r) \subseteq X \setminus F$ となる。

いま $A \subseteq F$ であるから、補集合をとると $X \setminus F \subseteq X \setminus A$ となり、よって $B(x, r) \subseteq X \setminus A$ が成り立つ。

これは $B(x, r) \cap A = \emptyset$ を意味するため、$x \notin C$ である。

したがって、対偶より $C \subseteq F$ が示された。

この議論は、$A$ を含むすべての閉集合 $F$ に対して成り立つため、$C$ はそれらの共通部分である $\overline{A}$ にも含まれる。すなわち $C \subseteq \overline{A}$ である。$\square$

#### 内部の特徴づけ

$$A^\circ = \{ x \in X \mid \exists r > 0,\; B(x, r) \subseteq A \}$$

**証明.** 右辺の集合を $I$ とおき、$A^\circ \subseteq I$ と $I \subseteq A^\circ$ の両方を示す。

**$A^\circ \subseteq I$ の証明：**

$x \in A^\circ$ とすると、定義より $A^\circ$ 自身が $A$ に含まれる開集合である。

開集合の定義より、ある $r > 0$ が存在して $B(x, r) \subseteq A^\circ$ となる。

$A^\circ \subseteq A$ であるため、$B(x, r) \subseteq A$ も成り立つ。したがって $x \in I$ である。

**$I \subseteq A^\circ$ の証明：**

$x \in I$ とすると、ある $r > 0$ が存在して $B(x, r) \subseteq A$ となる。

開球 $B(x, r)$ はそれ自体が開集合であり、かつ $A$ に含まれるため、$A$ に含まれるすべての開集合の和集合である $A^\circ$ に含まれる。

したがって $x \in B(x, r) \subseteq A^\circ$ となり、$x \in A^\circ$ である。$\square$

### 定義：集積点と導集合

距離空間 $(X, d)$ と部分集合 $A \subseteq X$ について、点 $x \in X$ が $A$ の**集積点**であるとは、

$$\forall r > 0; (B(x, r) \setminus \{x\}) \cap A \neq \emptyset$$

が成り立つことをいう。すなわち、$x$ を中心とするどんなに小さな開球を考えても、その中に $x$ とは異なる $A$ の点が必ず存在することである。$A$ の集積点全体の集合を $A$ の**導集合**といい、$A'$ で表す。

$x \in A$ であるが $A$ の集積点でないものを $A$ の**孤立点**という。

> **関数の極限とのつながり：** $x \to a$ の関数の極限を定義する際、$x \neq a$ での振る舞いを考える必要があった。このため、$x \neq a$ を保ちつついくらでも近づける点すなわち集積点でのみ、極限操作が意味を持つ。

### 命題4：閉包と集積点の関係

1. $\overline{A} = A \cup A'$
2. $A$ が閉集合 $\iff A' \subseteq A$（$A$ は自身の集積点をすべて含む）

**証明.**

(1) 命題3（閉包の特徴づけ）より、$x \in \overline{A}$ は「$\forall r > 0,\; B(x,r) \cap A \neq \emptyset$」と同値である。
もし $x \in A$ ならば常にこの条件を満たすので、$A \subseteq \overline{A}$ は自明に成り立つ。
一方 $x \notin A$ の場合、$B(x,r) \cap A$ に $x$ 自身が含まれることはないため、
$$B(x,r) \cap A = (B(x,r) \setminus \{x\}) \cap A$$ となる。

したがって、$x \notin A$ のとき $x \in \overline{A}$ であることは $x \in A'$ であることと同値である。これらを合わせて $\overline{A} = A \cup A'$ を得る。

(2) $A$ が閉集合であることは、$A = \overline{A}$ であることと同値である（※閉包 $\overline{A}$ は、$A$ を含む最小の閉集合として定義されるため、$A$ 自身が閉集合であれば $\overline{A} = A$ となり、逆に $\overline{A} = A$ であれば $\overline{A}$ は閉集合の共通部分なので $A$ も閉集合となる）。

(1) よりこれは $A = A \cup A'$ と同値である。この等式は一見すると強い条件に見えるが、そもそも $\overline{A}$ は常に $A$ を含んでいるため、等号が成り立つのは、付け足される集積点 $A'$ がすべて $A$ の内側に収まっている場合、すなわち $A' \subseteq A$ の場合に限られる。$\square$

### 命題5：閉集合と点列

$F \subseteq X$ が閉集合 $\iff$ $F$ 内の任意の収束点列の極限が $F$ に属する。

**証明.**

**（$\Rightarrow$）** 点列 $(x_n)$ を $F$ 内の点列（すべての $n$ で $x_n \in F$）とし、極限 $x$ に収束する（$x_n \to x$）と仮定する。このとき $x \in F$ となることを示す。

任意の半径 $r > 0$ に対し、開球 $B(x, r)$ を考える。点列の収束の定義より、ある番号 $N$ が存在して、すべての $n \geq N$ に対して $d(x_n, x) < r$ が成り立つ。これはすなわち $x_n \in B(x, r)$ を意味する。

前提より $x_n \in F$ でもあるから、$x_n \in B(x, r) \cap F$ となる。よって $B(x, r) \cap F \neq \emptyset$ であり、中心 $x$ の任意の開球は必ず $F$ と交わる。

したがって、命題3（閉包の特徴づけ）より $x \in \overline{F}$ である。いま $F$ は閉集合であるため $F = \overline{F}$ であり、ゆえに $x \in F$ である。

**（$\Leftarrow$）** 対偶を示す。

すなわち、$F$ が閉集合でないならば、$F$ 内のある点列が収束するが、その極限は $F$ に属さないことを示す。

$F$ が閉集合でないとすると、補集合 $X \setminus F$ は開集合ではない。開集合の定義の否定より、ある点 $a \in X \setminus F$ が存在して、任意の半径 $r > 0$ に対し開球 $B(a, r)$ は $X \setminus F$ に含まれない（$B(a, r) \not\subseteq X \setminus F$）。

これは、任意の $r > 0$ に対して $B(a, r)$ が必ず $F$ の点を含む（$B(a, r) \cap F \neq \emptyset$）ことを意味する。
そこで、各自然数 $n \in \mathbb{N}$ に対して $r = 1/n$ とし、交わり $B(a, 1/n) \cap F$ から点を一つ選んで $x_n$ とおく。

構成より、すべての $n$ について $x_n \in F$ である。また $x_n \in B(a, 1/n)$ だから $d(x_n, a) < 1/n$ であり、$n \to \infty$ とすると $x_n \to a$ に収束する。

しかし、$a \in X \setminus F$ だから、極限 $a$ は $F$ に属さない（$a \notin F$）。これで対偶が示された。$\square$

---

## 連続性

### 定義：連続写像

$f: (X, d_X) \to (Y, d_Y)$ が点 $a \in X$ で**連続**であるとは、

$$\forall \varepsilon > 0, \exists \delta > 0, \forall x \in X; d_X(x, a) < \delta \Rightarrow d_Y(f(x), f(a)) < \varepsilon$$

が成り立つことをいう。

>[ノート：連続性](40_knowledge-base/10_mathematics/40_analysis/20-continuity/)の定義と見比べると、$|x-a|$ が 
$d_X(x,a)$ に、
$|f(x)-f(a)|$ が 
$d_Y(f(x),f(a))$ に置き換わっただけである。

### 命題6：連続性の同値な特徴づけ

以下は同値：

(1) $f$ は $a$ で連続（$\varepsilon$-$\delta$）

(2) $x_n \to a \Rightarrow f(x_n) \to f(a)$（点列）

$f$ が $X$ 全体で連続であることは次とも同値：

(3) $Y$ の任意の開集合の逆像が $X$ の開集合（開集合による特徴づけ）

**証明.**

**(1 $\iff$ 2)** 局所的な点 $a$ での連続性と点列による特徴づけについては、[ノート：連続性](40_knowledge-base/10_mathematics/40_analysis/20-continuity/)の対応する証明において 
$|\cdot|$ を $d_X, d_Y$ に置き換えればそのまま成立する。

**(全域での 1 $\iff$ 3)** ここでは全域での連続性と開集合による特徴づけの同値性を示す。

**（$\Rightarrow$）** $V \subseteq Y$ を任意の開集合とする。$f^{-1}(V)$ が $X$ の開集合であることを示す。
任意の $x \in f^{-1}(V)$ をとると、$f(x) \in V$ である。$V$ は開集合だから、ある $\varepsilon > 0$ が存在して $B_Y(f(x), \varepsilon) \subseteq V$ となる。

仮定より $f$ は全域で連続なので、当然 $x$ でも連続である。したがって、この $\varepsilon$ に対してある $\delta > 0$ が存在し、$x' \in B_X(x, \delta)$ ならば $f(x') \in B_Y(f(x), \varepsilon)$ が成り立つ。

これは $f(B_X(x, \delta)) \subseteq B_Y(f(x), \varepsilon) \subseteq V$、すなわち $B_X(x, \delta) \subseteq f^{-1}(V)$ を意味する。任意の点 $x$ について条件を満たす開球が存在するため、$f^{-1}(V)$ は開集合である。

> 逆像 $f^{-1}(V)$ の包含関係の操作については、[像・逆像の基本性質](/collection/set-theory/#像逆像の基本性質) を参照。

**（$\Leftarrow$）** 任意の $x \in X$ と任意の $\varepsilon > 0$ をとる。$f$ が $x$ で連続（条件1）であることを示す。

開球 $B_Y(f(x), \varepsilon)$ は $Y$ の開集合である。仮定(3)より、その逆像 $U = f^{-1}(B_Y(f(x), \varepsilon))$ は $X$ の開集合となる。

$f(x) \in B_Y(f(x), \varepsilon)$ だから、当然 $x \in U$ である。

$U$ は開集合なので、ある $\delta > 0$ が存在して $B_X(x, \delta) \subseteq U$ が成り立つ。

これは「$x' \in B_X(x, \delta)$ ならば $x' \in f^{-1}(B_Y(f(x), \varepsilon))$」、すなわち「$d_X(x', x) < \delta$ ならば $d_Y(f(x'), f(x)) < \varepsilon$」を意味する。

これは $f$ が $x$ で連続であることの定義（$\varepsilon$-$\delta$）である。$\square$

> 条件(3)は距離関数 $d$ を参照しない。開集合だけで連続性が定義できるということが、位相空間への入口になる。

### 命題7：合成写像の連続性

$f$ が $a$ で連続、$g$ が $f(a)$ で連続 $\Rightarrow$ $g \circ f$ が $a$ で連続。

**証明.** $x_n \to a \Rightarrow f(x_n) \to f(a) \Rightarrow g(f(x_n)) \to g(f(a))$。$\square$

---

## コーシー列と完備性

### 定義：コーシー列

$(x_n)$ が**コーシー列**であるとは、

$$\forall \varepsilon > 0, \exists N \in \mathbb{N}, \forall m, n \geq N; d(x_m, x_n) < \varepsilon$$

が成り立つことをいう。

### 命題8：収束点列はコーシー列

**証明.** $x_n \to a$ として $N$ を $n \geq N$ で $d(x_n, a) < \varepsilon/2$ となるようにとれば、$m, n \geq N$ で三角不等式より $d(x_m, x_n) < \varepsilon$。$\square$

### 定義：完備距離空間

$(X, d)$ が**完備**であるとは、$X$ 内のすべてのコーシー列が $X$ 内の点に収束することをいう。

### 命題9：$\mathbb{R}$ の完備性

$(\mathbb{R}, |\cdot|)$ 
は完備である。

**証明.** [ノート：数列と極限](http://localhost:1313/40_knowledge-base/10_mathematics/40_analysis/10-sequences/#%E5%AE%9A%E7%90%868%E3%82%B3%E3%83%BC%E3%82%B7%E3%83%BC%E3%81%AE%E5%8F%8E%E6%9D%9F%E5%88%A4%E5%AE%9A%E6%B3%95)で証明済み。$\square$

$\mathbb{R}^n$ もユークリッド距離について完備である（各成分が $\mathbb{R}$ のコーシー列になることから従う）。一方、次の例は完備でない。

**$(\mathbb{Q}, |\cdot|)$：** $\sqrt{2}$ に収束する有理数列はコーシー列だが極限が $\mathbb{Q}$ に属さない。

**$((0,1), |\cdot|)$：** 
$x_n = 1/n$ はコーシー列だが極限 $0 \notin (0,1)$。$\mathbb{R}$ の部分集合として距離を引き継いだ場合、端点が抜けている開区間は完備でない。

> **完備性は位相的性質ではない（距離に依存する）：**
> $(0,1)$ 自体は $\mathbb{R}$ と同相（連続な全単射 $\mathbb{R} \to (0,1)$ が存在する）であり、完備かどうかは位相的性質ではなく距離の選び方に依存する性質であることを示唆している（そもそも完備性の定義の土台となるコーシー列が、距離関数 $d$ によって定義される）。
> 
> 開区間 $(0,1)$ と数直線 $\mathbb{R}$ 全体は、連続に伸び縮みさせることで完全に重なる（同相である）ため、空間のつながり方としては全く同じとみなされる。
> しかし、通常の定規 $|\cdot|$ で測ると $(0,1)$ は完備ではない。完備かどうかは空間のつながり方ではなく、空間全体にわたる一様な近さの尺度である距離関数 $d$ の選び方に依存する性質である（そもそも完備性の定義の土台となるコーシー列が、距離の測り方によって変化する概念だからである）。

**$(C([a,b]),\, d_\infty)$：** $[a,b]$ 上の連続関数全体の集合

$$C([a,b]) := \{f: [a,b] \to \mathbb{R} \mid f \text{ は連続}\}$$

に対して、一様距離（sup ノルム距離）

$$d_\infty(f, g) := \sup_{x \in [a,b]} |f(x) - g(x)|$$

を定義すると $(C([a,b]), d_\infty)$ は距離空間をなす。$d_\infty(f_n, f) \to 0$ は $f_n$ が $f$ に一様収束することと同値である。さらに $C([a,b])$ は完備距離空間でもある。
