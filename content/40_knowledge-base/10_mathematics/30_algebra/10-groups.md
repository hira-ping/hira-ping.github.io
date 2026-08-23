+++
title = "群"
weight = 10
date = 2026-08-23
+++

ℤ・ℚの構成（[ノート：整数・有理数（ℤ・ℚ）](40_knowledge-base/10_mathematics/20_set-theory/60-numbers/)）では、集合に演算を定義し、その演算が従う規則（結合律・単位元・逆元）を確認した。本ノートではそれを振り返り、**演算が従う規則そのものを公理として取り出す**。この抽象化によって生まれる構造が**群**である。

群は現代数学の最も基本的な代数的構造である。ℤの加法もℚの乗法も置換の合成も、群という一つの枠組みで統一して語ることができる。まず、演算を持つ集合という抽象的な対象を正確に定義することから始める。

---

{{< toc >}}

---

## 二項演算

群の定義に入る前に、演算を集合論の言葉で正確に定義する。

### 定義：二項演算

集合 $G$ 上の**二項演算**とは、写像

$$「\cdot」 :\; G \times G \to G$$

のことをいう。すなわち、$G$ の任意の二つの元 $a, b$ に対して、$G$ の元 $a \cdot b$ を対応させる規則である。

> **写像としての演算：** 二項演算を写像: $G \times G \to G$ と定義することで、$G$ の二元から $G$ の元が一意に定まるという条件が自動的に保証される。また、値域が $G$ 自身であること（$a \cdot b \in G$）を**閉じている**という。

**記法：** 二項演算は文脈に応じて $a \cdot b$、$ab$、$a + b$、$a \circ b$ などと書く。加法的な文脈（加法群）では $+$ を、乗法的な文脈では $\cdot$ または省略を使うことが多い。

---

## 群の定義

### 定義：群

集合 $G$ と $G$ 上の二項演算 $\cdot$ の組 $(G, \cdot)$ が**群**であるとは、以下の四つの公理をすべて満たすことをいう。

- **(G1) 閉性：** $\forall a, b \in G,\; a \cdot b \in G$
- **(G2) 結合律：** $\forall a, b, c \in G,\; (a \cdot b) \cdot c = a \cdot (b \cdot c)$
- **(G3) 単位元の存在：** $\exists e \in G,\; \forall a \in G,\; e \cdot a = a \cdot e = a$
- **(G4) 逆元の存在：** $\forall a \in G,\; \exists a^{-1} \in G,\; a \cdot a^{-1} = a^{-1} \cdot a = e$

> **(G1) は定義から自動：** 二項演算を写像: $G \times G \to G$ と定義した時点で閉性は保証されている。(G1) を明示するのは、演算の定義に閉性を含めない流儀との対比のためであり、どちらも論理的には等価である。本ノートでは二項演算の定義に閉性を込めているため、(G1) は以降省略しよい。

> **群の定義に必要なのは集合と写像だけ**である。順序も距離も位相使わない。

### 定義：可換群（アーベル群）

群 $(G, \cdot)$ が**可換群**（または**アーベル群**）であるとは、さらに次が成り立つことをいう。

**(G5) 交換律：** $\forall a, b \in G,\; a \cdot b = b \cdot a$

> 群は交換律を要求しない。(G2)〜(G4) のみを満たすが (G5) を満たさない群を**非可換群**という。後述の置換群はその例である。

---
## 基本的な例

### 例1：整数の加法群 $(\mathbb{Z}, +)$

ノート06で構成した $\mathbb{Z}$ と加法 $+$ を考える。

- **結合律：** $(a+b)+c = a+(b+c)$　✓
- **単位元：** $e = 0$、$a + 0 = 0 + a = a$　✓
- **逆元：** $a$ の逆元は $-a$、$a + (-a) = 0$　✓
- **可換：** $a + b = b + a$　✓

よって $(\mathbb{Z}, +)$ は可換群である。同様に $(\mathbb{Q}, +)$、$(\mathbb{R}, +)$ も可換群である。

### 例2：有理数の乗法群 $(\mathbb{Q} \setminus \{0\}, \times)$

$\mathbb{Q}$ 全体では $0$ の逆元が存在しないため、$0$ を除く。

- **結合律：** $(ab)c = a(bc)$　✓
- **単位元：** $e = 1$　✓
- **逆元：** $a \neq 0$ の逆元は $1/a$　✓
- **可換：** $ab = ba$　✓

よって $(\mathbb{Q} \setminus \{0\}, \times)$ は可換群である。

> **$(\mathbb{Z} \setminus \{0\}, \times)$ は群でない：** たとえば $2$ の乗法逆元（ $1/2$ ）は $\mathbb{Z}$ に属さない。

### 例3：置換群 $S_n$

$n$ 個の元からなる集合 $\{1, 2, \ldots, n\}$ の上の全単射写像（**置換**）全体を $S_n$ と書き、写像の合成 $\circ$ を演算とする。

- **結合律：** 写像の合成は一般に結合的　✓
- **単位元：** 恒等写像 $\mathrm{id}$　✓
- **逆元：** 全単射の逆写像　✓
- **可換：** $n \geq 3$ のとき**一般に成立しない**

$n = 3$ の具体例を見る。$\sigma = \begin{pmatrix} 1 & 2 & 3 \\ 2 & 3 & 1 \end{pmatrix}$（巡回置換）、$\tau = \begin{pmatrix} 1 & 2 & 3 \\ 1 & 3 & 2 \end{pmatrix}$（2と3を入れ替え）とする。

$$\sigma \circ \tau : 1 \mapsto 1 \mapsto 2,\quad 2 \mapsto 3 \mapsto 1,\quad 3 \mapsto 2 \mapsto 3 \quad \Rightarrow \begin{pmatrix} 1 & 2 & 3 \\ 2 & 1 & 3 \end{pmatrix}$$

$$\tau \circ \sigma : 1 \mapsto 2 \mapsto 3,\quad 2 \mapsto 3 \mapsto 2,\quad 3 \mapsto 1 \mapsto 1 \quad \Rightarrow \begin{pmatrix} 1 & 2 & 3 \\ 3 & 2 & 1 \end{pmatrix}$$

$\sigma \circ \tau \neq \tau \circ \sigma$
だから
$S_3$
は非可換群である。
$|S_n| = n!$。

### 例4：有限群 $(\mathbb{Z}/n\mathbb{Z}, +)$

$n \in \mathbb{N}$ を固定し、$\mathbb{Z}$ 上の同値関係 $a \sim b \iff n \mid (a-b)$ による商集合

$$\mathbb{Z}/n\mathbb{Z} = \{[0], [1], \ldots, [n-1]\}$$

に加法 $[a] + [b] := [a+b]$ を定めると、これは位数 $n$ の可換群になる（well-definednessは[ノート：整数・有理数（ℤ・ℚ）](40_knowledge-base/10_mathematics/20_set-theory/60-numbers/)と同様に確認できる）。

$n = 4$ の場合の演算表：

$$ \begin{array}{c|cccc} + & [0] & [1] & [2] & [3] \\\hline [0] & [0] & [1] & [2] & [3] \\ [1] & [1] & [2] & [3] & [0] \\ [2] & [2] & [3] & [0] & [1] \\ [3] & [3] & [0] & [1] & [2] \end{array} $$

---

## 群の基本性質

### 命題1：単位元の一意性

群 $(G, \cdot)$ の単位元は一意に定まる。

**証明.**

$e$ と $e'$ がともに単位元であると仮定する。$e$ が単位元であることより $e \cdot e' = e'$ であり、同時に $e'$ が単位元であることより $e \cdot e' = e$ である。したがって $e = e \cdot e' = e'$。$\square$

> 「ただ一つ存在する」という命題の定義（[ノート：一階述語論理の記法と推論規則](40_knowledge-base/10_mathematics/10_foundations-of-mathematics/10_logics/#%E4%B8%80%E6%84%8F%E5%AD%98%E5%9C%A8%E9%87%8F%E5%8C%96%E8%A8%98%E5%8F%B7)）に従った丁寧な証明は以下の通り。このようなロジックは暗黙の了解として省略されていることがほとんどである。


まず、「$x$ が群 $G$ の単位元である」という性質を $P(x)$ と定義する。

$$P(x) \iff \forall a \in G, (x \cdot a = a \land a \cdot x = a)$$

このとき、証明すべき命題「$\exists! e \in G, P(e)$」は、以下の論理式と同値である。

$$(\exists e \in G, P(e)) \land (\forall e_1, \forall e_2 \in G, ((P(e_1) \land P(e_2)) \to e_1 = e_2))$$

**(i) 存在の証明 $(\exists e \in G, P(e))$**

群 $(G, \cdot)$ の定義（単位元の公理）より、性質 $P(e)$ を満たす元 $e \in G$ が少なくとも1つ存在する。

(**ii)一意性の証明  $(\forall e_1, \forall e_2 \in G, ((P(e_1) \land P(e_2)) \to e_1 = e_2))$**

$e_1$ と $e_2$ を群 $G$ の任意の元とし、これらがともに単位元の性質を満たす、すなわち $P(e_1)$ および $P(e_2)$ が真であると仮定する。

1. 仮定 $P(e_1)$ より、すべての $a \in G$ について $e_1 \cdot a = a \cdot e_1 = a$ が成り立つ。
    ここで $a = e_2$ を代入すると、
    $$e_1 \cdot e_2 = e_2$$
    
2. 同時に、仮定 $P(e_2)$ より、すべての $a \in G$ について $e_2 \cdot a = a \cdot e_2 = a$ が成り立つ。
    ここで $a = e_1$ を代入すると、
    $$e_1 \cdot e_2 = e_1$$
    
3. 上記2つの結果より、
$$e_1 = e_1 \cdot e_2 = e_2$$
となり、$e_1 = e_2$ が導かれた。

存在と一意性の両方が示されたため、群の単位元はただ一つ存在する。 $\square$

### 命題2：逆元の一意性

群 $(G, \cdot)$ において、各元 $a \in G$ の逆元は一意に定まる。

**証明.**

$b, c$ がともに $a$ の逆元であるとする。

$$b = b \cdot e = b \cdot (a \cdot c) = (b \cdot a) \cdot c = e \cdot c = c \quad \square$$

### 命題3：逆元の逆元

$\forall a \in G,\; (a^{-1})^{-1} = a$

**証明.**

$a^{-1}$ の逆元の定義より $a^{-1} \cdot a = e$。逆元の一意性（命題2）より $(a^{-1})^{-1} = a$。$\square$

### 命題4：積の逆元

$\forall a, b \in G,\; (a \cdot b)^{-1} = b^{-1} \cdot a^{-1}$

**証明.**

$$(a \cdot b) \cdot (b^{-1} \cdot a^{-1}) = a \cdot (b \cdot b^{-1}) \cdot a^{-1} = a \cdot e \cdot a^{-1} = a \cdot a^{-1} = e$$

逆元の一意性より $(a \cdot b)^{-1} = b^{-1} \cdot a^{-1}$。$\square$

> **順序の逆転：** $(ab)^{-1} = b^{-1}a^{-1}$ であって $a^{-1}b^{-1}$ ではない。非可換群では順序が本質的である。「ズボンとパンツを脱ぐ順序は、履いた順序の逆」という比喩が有名（ウソ）。

### 命題5：簡約律

- $a \cdot b = a \cdot c \Rightarrow b = c$（左簡約律）
- $b \cdot a = c \cdot a \Rightarrow b = c$（右簡約律）

**証明（左）.**

両辺に左から $a^{-1}$ を掛ける：$a^{-1} \cdot (a \cdot b) = a^{-1} \cdot (a \cdot c)$。結合律より $(a^{-1} \cdot a) \cdot b = (a^{-1} \cdot a) \cdot c$、すなわち $e \cdot b = e \cdot c$、よって $b = c$。$\square$

---

## 部分群

### 定義：部分群

群 $(G, \cdot)$ の部分集合 $H \subseteq G$ が $G$ の**部分群**であるとは、$H$ が $G$ と同じ演算について群をなすことをいう。記号：$H \leq G$。

### 定理1：部分群の判定条件

$H \subseteq G$、$H \neq \emptyset$ が部分群であることは、次の二条件と同値である：

1.  $\forall a, b \in H,\; a \cdot b \in H$（演算について閉じている）
2.  $\forall a \in H,\; a^{-1} \in H$（逆元について閉じている）

**証明.**

部分群ならば明らかに1・2が成立する。逆に1・2を仮定する。

$H \neq \emptyset$ だから $\exists a \in H$。2より $a^{-1} \in H$。

1より $e = a \cdot a^{-1} \in H$。
結合律は $G$ で成立するから $H$ でも成立する。
よって $H$ は群の公理をすべて満たす。$\square$

**例：**
- $\{0\}$ と $\mathbb{Z}$ はともに $(\mathbb{Z}, +)$ の部分群（自明な部分群）
- $n\mathbb{Z} = \{nk \mid k \in \mathbb{Z}\}$ は $(\mathbb{Z}, +)$ の部分群（$n$ の倍数全体）
- $S_n$の偶置換全体 $A_n$（交代群）は $S_n$ の部分群
  - $|A_n| = n!/2$

> **実践的な判定法：**
> 上記の条件1と2は、まとめて「$\forall a, b \in H,\; a \cdot b^{-1} \in H$」という一つの条件に圧縮できる。実際の証明では、この1ステップの条件を示す方が記述が短くなり便利である（加法群の場合は $a - b \in H$ を示すことになる）。

---

## 準同型と同型

群の構造を保つ写像を定義する。

### 定義：群準同型

群 $(G, \cdot)$ と $(H, \ast)$ に対し、写像 $\varphi: G \to H$ が**群準同型**であるとは、

$$\forall a, b \in G,\; \varphi(a \cdot b) = \varphi(a) \ast \varphi(b)$$

が成り立つことをいう。すなわち「演算してから写す」と「写してから演算する」が一致する。

### 定義：群同型

準同型 $\varphi: G \to H$ が全単射であるとき、$\varphi$ を**群同型**といい、$G \cong H$ と書く。

> **同型の意味：** $G \cong H$ は、$G$ と $H$ は元の名前こそ違うが、群としての構造が完全に同じ」ということを意味する。つまり、群という枠組みの中であれば、$G$ と $H$ は区別しなくてよいということ。

### 命題6：準同型の基本性質

群準同型 $\varphi: G \to H$ に対して：

1. $\varphi(e_G) = e_H$（単位元は単位元に移る）
2. $\varphi(a^{-1}) = \varphi(a)^{-1}$（逆元は逆元に移る）

**証明.**

1. $\varphi(e_G) = \varphi(e_G \cdot e_G) = \varphi(e_G) \ast \varphi(e_G)$。両辺に $\varphi(e_G)^{-1}$ を右から掛けると $e_H = \varphi(e_G)$。
2. $\varphi(a) \ast \varphi(a^{-1}) = \varphi(a \cdot a^{-1}) = \varphi(e_G) = e_H$。逆元の一意性より $\varphi(a^{-1}) = \varphi(a)^{-1}$。$\square$

### 定義：核と像

準同型 $\varphi: G \to H$ に対して：

- **核**（kernel）：$\ker \varphi := \{a \in G \mid \varphi(a) = e_H\}$
- **像**（image）：$\mathrm{Im}\, \varphi := \{h \in H \mid \exists a \in G,\; \varphi(a) = h\}$

> **記法の厳密性：**
> 像の定義は $\{\varphi(a) \mid a \in G\}$ と書かれることもあるが、それは略記であり、分出公理の母集合と存在量化子 $\exists$ が見えにくくなっている。

### 命題7：核と単射性

$\ker \varphi = \{e_G\}$ であることと、$\varphi$ が単射であることは同値である。

**証明.**

$\varphi(a) = \varphi(b)$ とする。

$\varphi(a \cdot b^{-1}) = \varphi(a) \ast \varphi(b)^{-1} = e_H$。
よって $a \cdot b^{-1} \in \ker \varphi$。

$\ker \varphi = \{e_G\}$ ならば $a \cdot b^{-1} = e_G$、すなわち $a = b$。

逆は明らか。$\square$
