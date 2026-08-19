+++
title = "集合論（実践コレクション）"
weight = 10
date = 2026-08-09
lastmod = 2026-08-17
+++

---

{{< toc >}}

---

## 集合の包含と相等

### 集合の相等の証明テクニック
[← 公理的集合論の基礎](10_mathematics/10_foundations-of-mathematics/20_foundations_of_set-theory/)

$$A = B \iff A \subseteq B \land B \subseteq A$$

**使い方：** 2つの集合が等しいことを示す際の最も標準的なテンプレート。「$x \in A \implies x \in B$」と「$x \in B \implies x \in A$」の2段構えで証明する。外延性の公理から直接導かれる。

---

## 集合演算

### 分配律
[← 集合演算とド・モルガンの法則](10_mathematics/20_set-theory/10-operations/)

$$A \cap (B \cup C) = (A \cap B) \cup (A \cap C)$$

$$A \cup (B \cap C) = (A \cup B) \cap (A \cup C)$$

**使い方：** 集合演算を展開・くくり出しする際の基本公式。命題論理の分配律（$\land$ と $\lor$ の分配）に直接対応している。

**証明（第1式）.**

$$\begin{align*}
x \in A \cap (B \cup C)
&\iff x \in A \land (x \in B \lor x \in C) \\
&\iff (x \in A \land x \in B) \lor (x \in A \land x \in C) \\
&\iff x \in (A \cap B) \cup (A \cap C). \quad \square
\end{align*}$$

**証明（第2式）.**

$$\begin{align*}
x \in A \cup (B \cap C)
&\iff x \in A \lor (x \in B \land x \in C) \\
&\iff (x \in A \lor x \in B) \land (x \in A \lor x \in C) \\
&\iff x \in (A \cup B) \cap (A \cup C). \quad \square
\end{align*}$$

### ド・モルガンの法則（一般化）
[← 集合演算とド・モルガンの法則](10_mathematics/20_set-theory/10-operations/)

任意の集合族 $\{A_\lambda\}_{\lambda \in \Lambda}$ に対して成立する。

$$\begin{align*}
\left(\bigcup_{\lambda \in \Lambda} A_\lambda\right)^c 
&= \bigcap_{\lambda \in \Lambda} A_\lambda^c \\
\qquad \left(\bigcap_{\lambda \in \Lambda} A_\lambda\right)^c
&= \bigcup_{\lambda \in \Lambda} A_\lambda^c
\end{align*}$$

**使い方：** 「和集合の否定は、否定の共通部分」「共通部分の否定は、否定の和集合」。位相空間論（開集合・閉集合の性質）などで無限個の集合を扱う際に必須となる。

**証明（第1式）.**

$$\begin{align*}
x \in \left(\bigcup_{\lambda \in \Lambda} A_\lambda\right)^c
&\iff x \notin \bigcup_{\lambda \in \Lambda} A_\lambda \\
&\iff \lnot\,\exists \lambda \in \Lambda,\, x \in A_\lambda \\
&\iff \forall \lambda \in \Lambda,\, x \notin A_\lambda \\
&\iff \forall \lambda \in \Lambda,\, x \in A_\lambda^c \\
&\iff x \in \bigcap_{\lambda \in \Lambda} A_\lambda^c. \quad \square
\end{align*}$$
第2式も $\lnot\,\forall \iff \exists\,\lnot$ の論理的同値性を用いて同様に示せる。

---

## 順序対

### 順序対の特徴づけ定理
[← 写像](10_mathematics/20_set-theory/20-maps/)

$$\langle a, b \rangle = \langle c, d \rangle \iff a = c \land b = d$$

**使い方：** 順序対が等しいことを示す、あるいは順序対が等しいという仮定から成分同士の等しさを引き出すための唯一にして最強の道具。関係や写像の元（$\langle x, y \rangle$）を扱う証明では必ずと言っていいほど使う。

***証明.*** Kuratowskiの定義 $\langle a,b \rangle := \{\{a\}, \{a,b\}\}$ を用いる。
$(\Leftarrow)$ は自明。$(\Rightarrow)$ を示す。$\{\{a\},\{a,b\}\} = \{\{c\},\{c,d\}\}$ を仮定する。

**場合1:** $a = b$ のとき。左辺は $\{\{a\}\}$（単集合）。右辺も単集合だから $\{c\} = \{c,d\} = \{a\}$。よって $c = a$ かつ $d = a = b$。

**場合2:** $a \neq b$ のとき。$\{a,b\}$ は2要素集合だから $\{c\}$ と等しくない。よって $\{a\} = \{c\}$（すなわち $a = c$）かつ $\{a,b\} = \{c,d\}$。$a = c$ と合わせて $\{a,b\} = \{a,d\}$。$a \neq b$ より $b = d$。$\square$

## 写像

### 像の基本補題
[← 写像](10_mathematics/20_set-theory/20-maps/)

$$a \in S \implies f(a) \in f(S)$$

**使い方：** 像が絡む包含関係の証明で、元 $a$ を取って $f(a)$ が像に属することを示す際の基本ステップ。(1)(10) など、像の性質の多くはこの補題に帰着する。

**証明:**
$a \in S$ を仮定する。自明な等式 $f(a) = f(a)$ と組み合わせることで、以下が成り立つ。

$$a \in S \land f(a) = f(a)$$

ここから存在汎化（$\exists$-導入）を行えば、次が得られる。

$$\exists x \in S,\; f(x) = f(a)$$

像の定義 $f(S) := \{b \in B \mid \exists x \in S,\; f(x) = b\}$ において $b$ を $f(a)$ と置けば、上の論理式はまさに $f(a)$ が $f(S)$ に属するための条件そのものである。したがって $f(a) \in f(S)$ が導かれる。$\square$

**逆が成り立たない理由:**
逆命題 $f(a) \in f(S) \implies a \in S$ は、写像が単射でない限り一般には**偽**である。
$f(a) \in f(S)$ が意味するのは「$S$ の中に、$a$ と同じ行き先になる要素 $x$ が存在する」ことだけであり、「$a$ 自身が $S$ に入っている」ことまでは保証しないためである。

**反例:** $A = \{1, 2\}, B = \{0\}$ とし、$f(1) = 0, f(2) = 0$ という写像を考える。
部分集合 $S = \{1\}$ とし、$a = 2$ とすると、$f(a) = f(2) = 0 \in f(S)$ は真であるが、$a = 2 \notin \{1\} = S$ なので $a \in S$ は偽となる。$\square$

### 像・逆像の基本性質
[← 写像](10_mathematics/20_set-theory/20-maps/)

$f: A \to B$、$S, S' \subseteq A$、$T, T' \subseteq B$ に対して以下が成り立つ。

> **考え方：** 逆像は論理式に $\exists$ を含まないため、すべての演算（$\cup, \cap, \setminus, ^c$）と完全に交換可能（等号成立）である。像は $\exists$ を含むため、$\cup$ 以外との交換では一般に包含関係しか成り立たない。

**像について：**

| 番号 | 命題 | 注意 |
|------|------|------|
| (1) | $S \subseteq S' \Rightarrow f(S) \subseteq f(S')$ | 逆は $f$ が単射のとき成立 |
| (2) | $f(S \cup S') = f(S) \cup f(S')$ | 等号成立 |
| (3) | $f(S \cap S') \subseteq f(S) \cap f(S')$ | 等号は $f$ が単射のとき成立 |
| (4) | $f(S \setminus S') \supseteq f(S) \setminus f(S')$ | 等号は $f$ が単射のとき成立 |

**(1)の証明:**

$y \in f(S)$ とすると、像の定義より $\exists x \in S,\, f(x) = y$ である。$S \subseteq S'$ より $x \in S'$ でもあるから、$\exists x \in S',\, f(x) = y$ が成り立つ。したがって $y \in f(S')$。$\square$

**(2)の証明:**

述語論理の法則 $\exists x\,(P(x) \lor Q(x)) \iff \exists x\,P(x) \lor \exists x\,Q(x)$ を用いる。
$$\begin{align*}
y \in f(S \cup S') &\iff \exists x \in S \cup S',\, f(x) = y \\
&\iff \exists x,\, (x \in S \lor x \in S') \land f(x) = y \\
&\iff \exists x,\, (x \in S \land f(x) = y) \lor (x \in S' \land f(x) = y) \\
&\iff (\exists x \in S,\, f(x) = y) \lor (\exists x \in S',\, f(x) = y) \\
&\iff y \in f(S) \lor y \in f(S') \\
&\iff y \in f(S) \cup f(S'). \quad \square
\end{align*}$$

**(3)の証明:**

述語論理の法則 $\exists x\,(P(x) \land Q(x)) \implies \exists x\,P(x) \land \exists x\,Q(x)$ を用いる（逆は一般に不成立）。
$$\begin{align*}
y \in f(S \cap S') &\iff \exists x \in S \cap S',\, f(x) = y \\
&\iff \exists x,\, (x \in S \land x \in S') \land f(x) = y \\
&\implies (\exists x \in S,\, f(x) = y) \land (\exists x \in S',\, f(x) = y) \\
&\iff y \in f(S) \land y \in f(S') \\
&\iff y \in f(S) \cap f(S'). \quad \square
\end{align*}$$

**(4)の証明:**

$$\begin{align*}
y \in f(S) \setminus f(S') &\iff y \in f(S) \land y \notin f(S') \\
&\iff (\exists x \in S,\, f(x) = y) \land (\forall z \in S',\, f(z) \neq y) \\
&\implies \exists x \in S,\, (f(x) = y \land x \notin S') \quad \text{（※} x \in S' \text{とすると矛盾するため）} \\
&\iff \exists x \in S \setminus S',\, f(x) = y \\
&\iff y \in f(S \setminus S'). \quad \square
\end{align*}$$

**逆像について：**

| 番号 | 命題 | 注意 |
|------|------|------|
| (5) | $T \subseteq T' \Rightarrow f^{-1}(T) \subseteq f^{-1}(T')$ | 逆は $f$ が全射のとき成立 |
| (6) | $f^{-1}(T \cup T') = f^{-1}(T) \cup f^{-1}(T')$ | 等号成立 |
| (7) | $f^{-1}(T \cap T') = f^{-1}(T) \cap f^{-1}(T')$ | 等号成立 |
| (8) | $f^{-1}(T \setminus T') = f^{-1}(T) \setminus f^{-1}(T')$ | 等号成立 |
| (9) | $f^{-1}(T^c) = (f^{-1}(T))^c$ | 等号成立 |

**(5)の証明:**

$x \in f^{-1}(T) \iff f(x) \in T$。$T \subseteq T'$ より $f(x) \in T'$ であり、逆像の定義から $x \in f^{-1}(T')$。$\square$

**(6)の証明:**

$$\begin{align*}
x \in f^{-1}(T \cup T') &\iff f(x) \in T \cup T' \\
&\iff f(x) \in T \lor f(x) \in T' \\
&\iff x \in f^{-1}(T) \lor x \in f^{-1}(T') \\
&\iff x \in f^{-1}(T) \cup f^{-1}(T'). \quad \square
\end{align*}$$

**(7)の証明:**

$$\begin{align*}
x \in f^{-1}(T \cap T') &\iff f(x) \in T \cap T' \\
&\iff f(x) \in T \land f(x) \in T' \\
&\iff x \in f^{-1}(T) \land x \in f^{-1}(T') \\
&\iff x \in f^{-1}(T) \cap f^{-1}(T'). \quad \square
\end{align*}$$

**(8)の証明:**

$$\begin{align*}
x \in f^{-1}(T \setminus T') &\iff f(x) \in T \setminus T' \\
&\iff f(x) \in T \land f(x) \notin T' \\
&\iff x \in f^{-1}(T) \land x \notin f^{-1}(T') \\
&\iff x \in f^{-1}(T) \setminus f^{-1}(T'). \quad \square
\end{align*}$$

**(9)の証明:**

$$\begin{align*}
x \in f^{-1}(T^c) &\iff f(x) \in T^c \\
&\iff f(x) \notin T \\
&\iff x \notin f^{-1}(T) \\
&\iff x \in (f^{-1}(T))^c. \quad \square
\end{align*}$$

**像と逆像の関係：**

| 番号 | 命題 | 注意 |
|------|------|------|
| (10) | $f^{-1}(f(S)) \supseteq S$ | 等号は $f$ が単射のとき成立 |
| (11) | $f(f^{-1}(T)) \subseteq T$ | 等号は $f$ が全射のとき成立 |

**(10)の証明:**

$x \in S$ を任意にとる。像の基本補題より $f(x) \in f(S)$ である。

逆像の定義 $y \in f^{-1}(T) \iff f(y) \in T$ において $y=x, T=f(S)$ と置くことで、$x \in f^{-1}(f(S))$ が得られる。したがって $S \subseteq f^{-1}(f(S))$。$\square$

**(11)の証明:**

$$\begin{align*}
y \in f(f^{-1}(T)) &\iff \exists x \in f^{-1}(T),\, f(x) = y \\
&\iff \exists x,\, (f(x) \in T \land f(x) = y) \\
&\implies y \in T. \quad \square
\end{align*}$$

### 像と逆像の三条件同値（ガロア接続）
[写像](10_mathematics/20_set-theory/20-maps/)

写像 $f: X \to Y$ と部分集合 $S \subseteq X$、$T \subseteq Y$ に対して、以下の3条件はすべて同値である。

$$\begin{alignat}{2}
&\text{(i)} \quad & &\forall x \in S,\; f(x) \in T \\
&\text{(ii)} \quad & &f(S) \subseteq T \\
&\text{(iii)} \quad & &S \subseteq f^{-1}(T)
\end{alignat}$$

**使い方：** 連続性の証明（$\varepsilon$-$\delta$ 論法を開集合で翻訳する部分）で暗黙に使われている等価性。「任意の元に対して条件が成り立つ」という要素ごとの条件を、像・逆像の包含関係へと自由に書き換えられる。この「像と逆像の包含関係がいったりきたりできる性質」はガロア接続（随伴性）とも呼ばれる。

> **ガロア接続の読み方：** (ii) は「$f$ で送ると $T$ に収まる」を像の言葉で書き、(iii) は同じことを逆像の言葉で書いている。(i) は要素ごとの条件であり、これら三者が一致することで、定義と性質の橋渡しが可能になる。

**出発点：厳密な定義**

- 像の定義：$y \in f(S) \iff \exists x \in S; f(x) = y$（言い換えると「$x \in S$ ならば $f(x) \in f(S)$」が成り立つ）
- 逆像の定義：$x \in f^{-1}(T) \iff f(x) \in T$
- 部分集合の定義：$P \subseteq Q \iff (\forall p \in P \Rightarrow p \in Q)$

---

**(i) $\Rightarrow$ (ii) の証明**

「任意の $x \in S$ について $f(x) \in T$」と仮定する。任意の $y \in f(S)$ をとる。像の定義より、ある $x \in S$ が存在して $y = f(x)$ と書ける。仮定より $f(x) \in T$ なので $y \in T$。よって $f(S) \subseteq T$。$\square$

**(ii) $\Rightarrow$ (i) の証明**

$f(S) \subseteq T$ と仮定する。任意の $x \in S$ をとる。像の基本補題より $f(x) \in f(S)$。仮定より $f(S) \subseteq T$ なので $f(x) \in T$。$\square$

---

**(i) $\Rightarrow$ (iii) の証明**

「任意の $x \in S$ について $f(x) \in T$」と仮定する。逆像の定義（$f(x) \in T \iff x \in f^{-1}(T)$）をそのまま適用すると「任意の $x \in S$ について $x \in f^{-1}(T)$」となる。これは部分集合の定義そのものであり、$S \subseteq f^{-1}(T)$ が示された。$\square$

**(iii) $\Rightarrow$ (i) の証明**

$S \subseteq f^{-1}(T)$ と仮定する。任意の $x \in S$ をとると、仮定より $x \in f^{-1}(T)$。逆像の定義を適用すると $f(x) \in T$。$\square$

---

## 同値関係と商集合

### 同値類の基本性質
[← 同値関係・同値類・商集合](10_mathematics/20_set-theory/30-equivalence/)

$\sim$ を $A$ 上の同値関係とする。
1. **代表元の取り替え:** $a \sim b \iff [a] = [b]$
2. **非交差性:** $[a] \neq [b] \implies [a] \cap [b] = \emptyset$

**使い方：** 商集合を扱う証明の基礎。特に (1) は、同値関係の仮定（$a \sim b$）を集合の等号（$[a] = [b]$）に変換する、あるいはその逆を行うための重要ツール。代数学（剰余群など）で頻出する。

**証明（性質1）.**

$(\Rightarrow)$ $a \sim b$ を仮定する。

$x \in [a]$ とすると $x \sim a$。推移律より $x \sim b$、すなわち $x \in [b]$。よって $[a] \subseteq [b]$。

対称律より $b \sim a$ だから同様に $[b] \subseteq [a]$。ゆえに $[a] = [b]$。

$(\Leftarrow)$ $[a] = [b]$ を仮定する。反射律より $a \in [a] = [b]$、すなわち $a \sim b$。$\square$

**証明（性質2）.**

対偶を示す。$x \in [a] \cap [b]$ とすると $x \sim a$ かつ $x \sim b$。

対称律より $a \sim x$、推移律より $a \sim b$。性質1より $[a] = [b]$。$\square$

### Well-definedness の証明テンプレート
[← 同値関係・同値類・商集合](10_mathematics/20_set-theory/30-equivalence/)

商集合 $A/{\sim}$ 上の演算を $[a] \star [b] := [a \ast b]$ と定義する際、以下が成り立つことを示さなければならない。

$$a \sim a' \land b \sim b' \implies a \ast b \sim a' \ast b'$$

**使い方：** 自分で新しい商集合（整数の構成、有理数の構成、剰余群、商位相空間など）を作り、そこに元の集合の演算を落とし込むときの確認事項。これを成立しないと、代表元の選び方によって計算結果が変わってしまう壊れた演算になる。

---

## 自然数

### 数学的帰納法の原理
[← 自然数](10_mathematics/20_set-theory/50-naturals/)

自然数 $\omega$ に関する性質（述語）$P(n)$ について、以下が成り立つ。

$$P(0) \land (\forall n \in \omega,\; P(n) \Rightarrow P(S(n))) \implies \forall n \in \omega,\; P(n)$$

**使い方：** 自然数全体に関する全称命題 $\forall n \in \omega$ を証明するときに極めて有用な手法。ZFCの枠組みでは、$\omega$ がすべての帰納的集合の共通部分として構成されたことから、公理ではなく定理として導かれる。

**証明.**

性質 $P$ を満たす自然数の集合を $A = \{n \in \omega \mid P(n)\}$ とする。

仮定より $0 \in A$ であり、かつ $n \in A \Rightarrow S(n) \in A$ が成り立つため、$A$ は帰納的集合の定義を満たす。

自然数全体 $\omega$ は、すべての帰納的集合に属する要素を集めたものとして定義されているため、帰納的集合である $A$ に対して $\omega \subseteq A$ が成り立つ。

$A \subseteq \omega$ は定義より明らかなので $A = \omega$ となり、すべての自然数で $P(n)$ が真であることが示された。$\square$

## 有限集合の性質

集合 $A$ が**有限集合**であるとは、ある自然数 $n \in \omega$ が存在して、$A$ と $n$ の間に全単射が存在すること（$A \sim n$）をいう。有限集合に関する直感的な事実は、すべて自然数の帰納法を用いて厳密に証明される。

### 有限集合の和集合の要素数（包除原理）
[← 自然数](10_mathematics/20_set-theory/50-naturals/)

有限集合
$A, B$ の要素数をそれぞれ
$|A|, |B|$と書くとき、和集合
$A \cup B$ も有限集合であり、その要素数について以下が成り立つ。

$$|A \cup B| = |A| + |B| - |A \cap B|$$

**使い方：** 2つの集合を合わせた要素数を数える際の基本公式（包除原理）。

**証明（全単射の構成による厳密な証明）.**

まず、互いに素（$X \cap Y = \emptyset$）
な有限集合 $X, Y$ について、
**$|X \cup Y| = |X| + |Y|$** が成り立つこと（加法性）を補題として示す。

$|X| = n, |Y| = m$ とすると、
定義より全単射 $f: X \to n$ と $g: Y \to m$ が存在する（ここで $n, m$ はフォン・ノイマン順序数であり、$n = \{0, \ldots, n-1\}$ である）。

新しい写像 $h: X \cup Y \to n + m$ を次のように構成する。
- $x \in X$ のときは、$h(x) = f(x)$
- $x \in Y$ のときは、$h(x) = n + g(x)$

$X$ と $Y$ は交わらないため $h$ は well-defined であり、
かつ $f, g$ が全単射であることから
$h$ も $X \cup Y$ から $\{0, \ldots, n+m-1\}$ への全単射となる。
したがって $|X \cup Y| = n + m = |X| + |Y|$ である。（補題終）

次に、一般の有限集合 $A, B$ について考える。

和集合 $A \cup B$ は、交わらない2つの集合の和として $A \cup (B \setminus A)$ と分割できる。

上の補題より、

$$|A \cup B| = |A| + |B \setminus A| \quad \cdots (1)$$

また、集合 $B$ 自身も、交わらない2つの集合の和として $(B \setminus A) \cup (A \cap B)$ と分割できる。

同じく補題より、

$$|B| = |B \setminus A| + |A \cap B|$$

これを移項すると（※要素数は自然数なので通常の引き算が成立する）、

$$|B \setminus A| = |B| - |A \cap B| \quad \cdots (2)$$

(2) を (1) に代入すると、

$$|A \cup B| = |A| + |B| - |A \cap B|$$

が得られる。$\square$

### 鳩の巣原理
[← 自然数](10_mathematics/20_set-theory/50-naturals/)

自然数 $m, n \in \omega$ について、$m > n$ ならば、$m$ から $n$ への単射は存在しない。
（したがって、要素数が $m$ の有限集合から $n$ の有限集合への単射も存在しない）。

> **注記：自然数を「集合」として扱う記法について**
>
> ここで「$m$ から $n$ への単射」と書かれているのはタイポや比喩ではない。[ノート：自然数](10_mathematics/20_set-theory/50-naturals)で見た通り、ZFCにおける自然数はフォン・ノイマンの順序数として $n = \{0, 1, \ldots, n-1\}$ と定義される。つまり、自然数 $n$ はちょうど $n$ 個の要素をもつ集合そのものである。したがって、写像 $f: m \to n$ とは、文字通り要素数 $m$ の集合から要素数 $n$ の集合への写像を意味している。

**使い方：** 要するに、部屋の数より人の数の方が多いなら、必ず誰か2人は同じ部屋に入るということ。存在証明（重複するペアが$\exists$すること）を示すための強力なツールとなる。

***証明.***

部屋の数 $n$ に関する数学的帰納法で示す。

**ベースケース（$n=0$）：**

$n=0$（空集合 $\emptyset$）とする。$m > 0$ ならば $m$ は空ではない。空でない集合から空集合への写像は存在しないため、単射も存在しない。よって成立。

**帰納ステップ：**

ある $k \in \omega$ で定理が成り立つと仮定し、$n = S(k) = k+1$ の場合を考える。

$m > k+1$ となる $m$ から $k+1$ への単射 $f: m \to k+1$ が存在したと仮定して矛盾を導く。

$k$ を像に持つ元がある場合、それを $x \in m$ とする（すなわち $f(x) = k$）。

$m$ から $x$ を除いた集合 $m \setminus \{x\}$ は要素数 $m-1$ であり、$f$ は単射だから $f$ を $m \setminus \{x\}$ に制限した写像 $f'$ の値域は $(k+1) \setminus \{k\} = k$ となる。

すると $f'$ は要素数 $m-1$ の集合から $k$ への単射となるが、$m > k+1 \implies m-1 > k$ であるため、これは帰納法の仮定（要素数 $k$ への単射は存在しない）に矛盾する。

よって $n = k+1$ でも単射は存在せず、すべての自然数 $n$ で定理が成り立つ。$\square$

### 有限集合上の自己単射・自己全射
[← 写像](10_mathematics/20_set-theory/20-maps/)

有限集合 $A$ から $A$ 自身への写像 $f: A \to A$ について、以下の3つは同値である。

1. $f$ は単射である
2. $f$ は全射である
3. $f$ は全単射である

**使い方：** 有限集合の上では、単射であることと全射であることが等価になる（無限集合では成り立たない）。代数学で全単射（置換）になることを示す際、単射であることさえ示せば自動的に全射も言えるため、証明の労力が半分になる。

**証明.**

$(1 \implies 2)$ を示す（これが最も重要）。

$A$ の要素数を $n$ とする。もし $f$ が全射でないとすると、像 $f(A)$ は $A$ の真部分集合となり、その要素数 $m$ は $m < n$ となる。

すると $f$ は、要素数 $n$ の集合 $A$ から、要素数 $m$ の集合 $f(A)$ への単射ということになるが、$n > m$ であるため、これは鳩の巣原理に矛盾する。したがって $f$ は全射でなければならない。

$(2 \implies 1)$ も同様に要素数を比較することで示される。$\square$

## 順序関係
### 上限（下限）と最大値（最小値）の関係
[← 順序関係](10_mathematics/20_set-theory/70-order-relations/)

空でない部分集合 $S \subset \mathbb{R}$ について、上限 $\sup S$ が存在し、かつ $\sup S \in S$ ならば、$\sup S = \max S$ である。
同様に、下限 $\inf S$ が存在し、かつ $\inf S \in S$ ならば、$\inf S = \min S$ である。

**証明.**
$M = \sup S$ とおく。ある実数 $m$ が $S$ の最大値（$\max S$）であるための定義は、以下の2条件を同時に満たすことである。

1. $m \in S$ （$m$ 自身が集合の要素である）
1. $\forall x \in S, x \leq m$ （$m$ が $S$ の上界である）

$M$ についてこのこれらを確認する。

条件1について：仮定 $\sup S \in S$ より、$M \in S$ であり満たされる。

条件2について：$M$ は $S$ の最小の上界である。上限である以上、当然 $S$ の上界としての性質をもつため、$\forall x \in S, x \leq M$ を満たす。

したがって、$M$ は最大値の定義を満たしており、$M = \max S$ が成り立つ。
