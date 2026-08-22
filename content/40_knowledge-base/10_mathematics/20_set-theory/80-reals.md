+++
title = "実数（ℝ）"
weight = 80
date = 2026-08-11
lastmod = 2026-08-12
+++

$\mathbb{Q}$ を出発点に、実数全体の集合 $\mathbb{R}$ を構成する。有理数直線には穴があり（$\sqrt{2}$ や $\pi$ が存在しない）、この穴を埋める操作を集合論的に厳密に定式化するのが本ノートの目的である。構成法としてデデキント切断とコーシー列の二つを扱い、構成から従う基本性質を整理する。

本ノートは公理的集合論と解析学の接続点に位置する。実数が体であり、全順序集合であり、完備であるという基本性質を論理式の言葉で確認する。

解析学のノートでは $\mathbb{R}$ を所与のものとして展開していくが、実数のこれらの性質を公理（完備順序体の公理）として最初から導入して解析学を展開する立場と ZFC から段階的に構成する立場は、論理的に等価である。

---

{{< toc >}}

---

## 有理数直線の穴

$\mathbb{Q}$ は加減乗除のすべてが定義された順序体であるが、直線として見たとき、いたるところに穴が空いている。

**具体例：** $S = \{q \in \mathbb{Q} \mid q^2 < 2\}$ という有理数の集合を考える。$S$ は上に有界である（たとえば $2$ は上界）。しかし $S$ の上限（最小上界）が $\mathbb{Q}$ の中に存在しない。

> **確認：$\sqrt{2} \notin \mathbb{Q}$** $\sqrt{2} = p/q$（既約分数）と仮定すると $p^2 = 2q^2$。左辺は $2$ の倍数だから $p$ は偶数、$p = 2k$ とおくと $4k^2 = 2q^2$、すなわち $q^2 = 2k^2$。同様に $q$ も偶数となり、$p/q$ が既約であることに矛盾する。$\square$

上に有界な集合が上限をもたないというある種の不完全さが $\mathbb{Q}$ の穴の正体である。実数の構成とは、この穴を塞いだ順序体 $\mathbb{R}$ を構成することである。

### 上限・下限の言葉の準備

以降の議論で使う言葉を整理しておく。$A \subseteq \mathbb{Q}$ とする。

- $b \in \mathbb{Q}$ が $A$ の**上界**であるとは、$\forall a \in A,\, a \leq b$ が成り立つことをいう。
- $A$ が**上に有界**であるとは、$A$ の上界が少なくとも一つ存在することをいう。
- $A$ の**上限**（最小上界）$\sup A$ とは、$A$ の上界の中で最小のものをいう。

下界・下に有界・下限（最大下界）も同様に定義される。

---

## デデキント切断による構成

### デデキント切断の定義

$\mathbb{Q}$ の部分集合 $\alpha$ が以下の3条件をすべて満たすとき、$\alpha$ を**デデキント切断** という。

1. **非自明性：** $\alpha \neq \emptyset$ かつ $\alpha \neq \mathbb{Q}$
2. **下方閉性：** $p \in \alpha$ かつ $q < p$ ならば $q \in \alpha$（切断は左側を取る）
3. **最大元を持たない：** $p \in \alpha$ ならば $p < r$ となる $r \in \alpha$ が存在する

直感的には、$\alpha$ は有理数直線を左側と右側に切り分けたときの左側の部分であり、切断点自体は $\alpha$ に含まれない。

> **例（有理数に対応する切断）：** $r \in \mathbb{Q}$ に対し $\alpha_r := \{q \in \mathbb{Q} \mid q < r\}$ と定めると、$\alpha_r$ はデデキント切断である。
>
> - *非自明性：* $r - 1 \in \alpha_r$ かつ $r \notin \alpha_r$。
> - *下方閉性：* $q < p < r$ ならば $q < r$、すなわち $q \in \alpha_r$。
> - *最大元なし：* $p < r$ ならば $p < (p+r)/2 < r$、すなわち $(p+r)/2 \in \alpha_r$。

> **例（無理数に対応する切断）：** $\alpha := \{q \in \mathbb{Q} \mid q < 0 \text{ または } (q \geq 0 \text{ かつ } q^2 < 2)\}$ と定めると、これは $\sqrt{2}$ に対応するデデキント切断である。この切断の右端に対応する有理数は $\mathbb{Q}$ に存在しない。

### 実数の定義

$$\mathbb{R} := \{\alpha \subseteq \mathbb{Q} \mid \alpha \text{ はデデキント切断}\}$$

すなわち、**実数とはデデキント切断のことである**。各実数 $\alpha \in \mathbb{R}$ の実体は有理数の集合である。

### 順序の定義

$\alpha, \beta \in \mathbb{R}$ に対して、

$$\alpha \leq \beta \iff \alpha \subseteq \beta$$

と定める。包含関係が実数の順序に対応する。

### $\mathbb{Q}$ の $\mathbb{R}$ への埋め込み

写像 $\iota: \mathbb{Q} \to \mathbb{R}$ を $\iota(r) := \alpha_r = \{q \in \mathbb{Q} \mid q < r\}$ で定める。$\iota$ は単射な順序保存写像であり、$\mathbb{Q}$ を $\mathbb{R}$ の中に自然に埋め込む。以降、$r \in \mathbb{Q}$ と $\alpha_r \in \mathbb{R}$ を同一視する。

### 加法の定義

$\alpha, \beta \in \mathbb{R}$ に対して、

$$\alpha + \beta := \{p + q \mid p \in \alpha,\, q \in \beta\}$$

と定める。$\alpha + \beta$ がデデキント切断であることを確認する。

1. **非自明性：** $\alpha, \beta$ それぞれ空でなく $\mathbb{Q}$ 全体でもないから、$\alpha + \beta \neq \emptyset$。また $\alpha, \beta$ の各上界 $a, b$ に対し $a + b \notin \alpha + \beta$（$p \in \alpha$ ならば $p < a$、$q \in \beta$ ならば $q < b$ だから $p + q < a + b$）。
2. **下方閉性：** $r = p + q \in \alpha + \beta$（$p \in \alpha$, $q \in \beta$）とし、$s < r$ とする。$s - q < p$ だから $\alpha$ の下方閉性より $s - q \in \alpha$。よって $s = (s - q) + q \in \alpha + \beta$。
3. **最大元なし：** $r = p + q \in \alpha + \beta$ に対し、$\alpha$ の最大元なし条件から $p < p' \in \alpha$ をとれば $r < p' + q \in \alpha + \beta$。

加法の可換律・結合律は定義から明らか。加法単位元は $0_\mathbb{R} = \alpha_0 = \\{q \in \mathbb{Q} \mid q < 0\\}$。加法の逆元（$-\alpha$）は次で定める：

$$-\alpha := \{q \in \mathbb{Q} \mid \exists r \notin \alpha,\, q < -r\}$$

### 乗法の定義

乗法は非負実数の場合を先に定め、符号で場合分けする。$\alpha, \beta \geq 0_\mathbb{R}$ のとき、

$$\alpha \cdot \beta := \{q \in \mathbb{Q} \mid q < 0\} \cup \{p \cdot q \mid p \in \alpha,\, p \geq 0,\, q \in \beta,\, q \geq 0\}$$

一般の $\alpha, \beta \in \mathbb{R}$ に対しては符号で場合分けして定める。乗法単位元は $1_\mathbb{R} = \alpha_1$。

---

## コーシー列による構成

デデキント切断とは全く異なるアプローチとして、コーシー列による構成がある。アイデアは、**$\sqrt{2}$ を近似する有理数列 $1, 1.4, 1.41, 1.414, \ldots$ 全体を $\sqrt{2}$ そのものと同一視する**ことである。

### コーシー列の定義

有理数列 $(a_n)_{n \in \mathbb{N}}$ が**コーシー列**であるとは、

$$\forall \varepsilon \in \mathbb{Q}_{>0}\, \exists N \in \mathbb{N}\, \forall m, n \geq N,\; |a_m - a_n| < \varepsilon$$

が成り立つことをいう。
ここで $|\cdot|$ は $\mathbb{Q}$ 上の絶対値であり、
$\mathbb{Q}$
の演算のみで定義される。

### 同値関係の定義

$\mathbb{Q}$ 上のコーシー列全体を $\mathcal{C}$ とする。$\mathcal{C}$ 上の関係を次で定める：

$$(a_n) \sim (b_n) \iff \forall \varepsilon \in \mathbb{Q}_{>0}, \exists N \in \mathbb{N}, \forall n \geq N; |a_n - b_n| < \varepsilon$$

**同値関係の確認：**

- **反射律：** 
$|a_n - a_n| = 0 < \varepsilon$。$\checkmark$
- **対称律：**
$|a_n - b_n| < \varepsilon \Rightarrow |b_n - a_n| < \varepsilon$。$\checkmark$
- **推移律：**
$|a_n - b_n| < \varepsilon/2$ かつ 
$|b_n - c_n| < \varepsilon/2$ ならば三角不等式より 
$|a_n - c_n| < \varepsilon$。$\checkmark$

### 実数の定義

$$\mathbb{R} := \mathcal{C} / {\sim}$$

コーシー列 $(a_n)$ の同値類 $[(a_n)]$ が一つの実数を表す。

### $\mathbb{Q}$ の埋め込み

定数列 $\iota(r) := [(r, r, r, \ldots)]$ により $\mathbb{Q}$ を $\mathbb{R}$ に埋め込む。

### 加法・乗法の定義

$$[(a_n)] + [(b_n)] := [(a_n + b_n)], \qquad [(a_n)] \cdot [(b_n)] := [(a_n \cdot b_n)]$$

**Well-definedness の確認（加法）：** $(a_n) \sim (a_n')$ かつ $(b_n) \sim (b_n')$ とする。

$$|(a_n + b_n) - (a_n' + b_n')| \leq |a_n - a_n'| + |b_n - b_n'|$$

各項を $\varepsilon/2$ 未満にできるから、和も $\varepsilon$ 未満にできる。$\square$

**Well-definedness の確認（乗法）：** コーシー列は有界であることを用いる。

$$|a_n b_n - a_n' b_n'| \leq |a_n||b_n - b_n'| + |b_n'||a_n - a_n'| \leq M|b_n - b_n'| + M'|a_n - a_n'|$$

各項を適切に小さくできるから、積も任意の $\varepsilon > 0$ より小さくできる。$\square$

> **コーシー列の有界性：** 
$(a_n)$ がコーシー列ならば、$\varepsilon = 1$
に対して $N$ をとると $n \geq N$
で $|a_n - a_N| < 1$。
よって $|a_n| \leq |a_N| + 1$。
有限個の項 $|a_1|, \ldots, |a_{N-1}|$ と $|a_N| + 1$
の最大値が上界 $M$ となる。

---

## 二つの構成の比較

二つの構成は見た目が全く異なるが、どちらも後述の基本性質（定理1・2・3）を満たす。両者が順序体として同型であることは完備順序体の一意性定理が保証する。

使い分けの観点では、デデキント切断は順序と上限性質が定義から直接見えるという利点がある。
実際、$\alpha \leq \beta \iff \alpha \subseteq \beta$ という順序の定義は明快であり、
$\sup A = \bigcup_{\alpha \in A} \alpha$ という上限の構成も自然に従う。
一方、コーシー列による構成は加法・乗法の定義が成分ごとで均一であり、またコーシー列の同値類として完備化するというアイデアが距離空間一般に自然に拡張できるという利点がある。
距離空間の完備化の理論はコーシー列の構成を直接一般化したものであり、$\mathbb{Q} \to \mathbb{R}$ はその最も基本的な例に位置づけられる。

---

## 基本性質

構成から従う $\mathbb{R}$ の基本性質を定理としてまとめる。

### 定理1：$\mathbb{R}$ は体である

$\mathbb{R}$ は加法と乗法について以下を満たす。

- 加法について可換群をなす（結合律・可換律・単位元 $0$ の存在・逆元の存在）
- 乗法について $0$ を除く元が可換群をなす（結合律・可換律・単位元 $1$ の存在・逆元の存在）
- 分配律：$\alpha(\beta + \gamma) = \alpha\beta + \alpha\gamma$

### 定理2：$\mathbb{R}$ は全順序集合である

$\mathbb{R}$ の任意の二元 $\alpha, \beta$ に対して $\alpha \leq \beta$ または $\beta \leq \alpha$ が成り立つ（全順序性）。さらに順序は体の演算と整合する：

- $\alpha < \beta \Rightarrow \alpha + \gamma < \beta + \gamma$
- $\alpha > 0$ かつ $\beta > 0 \Rightarrow \alpha\beta > 0$

すなわち $\mathbb{R}$ は**順序体** である。

### 定理3：上限性質

$\emptyset \neq A \subseteq \mathbb{R}$ が上に有界ならば、$\sup A$ が $\mathbb{R}$ に存在する。

**（デデキント切断による証明）**

$\alpha^* := \bigcup_{\alpha \in A} \alpha$ と定める。$\alpha^*$ がデデキント切断であることを確認する。

1. *非自明性：* 
$A \neq \emptyset$ より $\alpha^* \neq \emptyset$。
$A$ の上界 $\beta \in \mathbb{R}$ が存在するから各 $\alpha \in A$ について $\alpha \subseteq \beta$、
よって $\alpha^* \subseteq \beta \subsetneq \mathbb{Q}$。
2. *下方閉性：* 
$p \in \alpha^*$ ならば、
ある $\alpha \in A$ に対し 
$p \in \alpha$。
$q < p$ ならば、 $\alpha$
の下方閉性から $q \in \alpha \subseteq \alpha^*$。
3. *最大元なし：*
$p \in \alpha^*$ ならば、
ある$\alpha \in A$ に対し
$p \in \alpha$。
$\alpha$
の最大元なし条件から
$p < r \in \alpha \subseteq \alpha^*$。

よって $\alpha^* \in \mathbb{R}$。

$\alpha^*$ が $A$ の上限であることを確認する。

- **上界：**
各 $\alpha \in A$ について 
$\alpha \subseteq \alpha^*$、
すなわち $\alpha \leq \alpha^*$。
- *最小性：* 
$\beta < \alpha^*$
（すなわち $\beta \subsetneq \alpha^*$）ならば、
ある $p \in \alpha^* \setminus \beta$ が存在する。
$p \in \alpha^*$ よりある $\alpha \in A$ に対し
$p \in \alpha$。
$p \notin \beta$ だから $\alpha \not\subseteq \beta$、
すなわち $\beta$ は $A$ の上界でない。

ゆえに $\alpha^* = \sup A$。$\square$

> **$\mathbb{Q}$ との対比：** $\mathbb{Q}$ では $A = \\{q \in \mathbb{Q} \mid q^2 < 2\\}$ の上限が存在しなかった。$\mathbb{R}$ では $\bigcup_{\alpha \in A} \alpha$ が $\sqrt{2}$ に対応する切断として存在する。

この上限性質を $\mathbb{R}$ の**完備性**と呼ぶ。$\mathbb{Q}$ は体であり全順序集合でもあるが、この完備性を欠く。$\mathbb{R}$ はこの性質を持つことで穴のない直線になる。

> **完備性という言葉について：** 完備という言葉は文脈によって複数の意味をもつ。距離空間論ではすべてのコーシー列が収束するという意味で使われる。本ノートで定義した上限性質（デデキント完備性）はこれとは形式的に異なる定義だが、$\mathbb{R}$ においては同値であることが[ノート：数列と極限](40_knowledge-base/10_mathematics/40_analysis/10-sequences/)で示される。

### 定理4：アルキメデスの原理

任意の実数 $x \in \mathbb{R}$ に対して、$n > x$ となる自然数 $n \in \mathbb{N}$ が存在する。

同値な言い換えとして、任意の $\varepsilon \in \mathbb{R}_{>0}$ に対して $1/n < \varepsilon$ となる $n \in \mathbb{N}$ が存在する。

**証明.** 対偶を仮定する。すなわち、ある $x \in \mathbb{R}$ が存在して、すべての $n \in \mathbb{N}$ に対し $n \leq x$ が成り立つとする。このとき $\mathbb{N}$ は上に有界だから、完備性（定理3）より $\sup \mathbb{N}$ が $\mathbb{R}$ に存在する。$\sup \mathbb{N} - 1$ は $\mathbb{N}$ の上界でないから、ある $n \in \mathbb{N}$ が存在して $n > \sup \mathbb{N} - 1$、すなわち $n + 1 > \sup \mathbb{N}$。しかし $n + 1 \in \mathbb{N}$ だから $\sup \mathbb{N}$ が上限であることに矛盾する。$\square$

> $1/n$ をいくらでも小さくできるという形は、$\varepsilon$-$\delta$ 論法や数列の収束の議論で繰り返し使われる。

### 定理5：有理数の稠密性

任意の実数 $\alpha < \beta$ に対して、$\alpha < q < \beta$ となる有理数 $q \in \mathbb{Q}$ が存在する。

**証明.** アルキメデスの原理より、$1/n < \beta - \alpha$ となる $n \in \mathbb{N}$ が存在する。集合 $\{k \in \mathbb{Z} \mid k \leq n\alpha\}$ は上に有界だから完備性より上限をもち、それは整数なので最大元 $\lfloor n\alpha \rfloor$ が存在する。$m := \lfloor n\alpha \rfloor + 1$（$n\alpha$ を超える最小の整数）とおくと、$m - 1 \leq n\alpha < m$ だから $\alpha < m/n$。また $m \leq n\alpha + 1 < n\beta$（$1/n < \beta - \alpha$ より）だから $m/n < \beta$。よって $q := m/n \in \mathbb{Q}$ が $\alpha < q < \beta$ を満たす。$\square$

> 有理数の稠密性は、直感的には $\mathbb{Q}$ が $\mathbb{R}$ の骨格をなしていることを示す。どれだけ近い二つの実数の間にも有理数が存在する。一方で $\mathbb{R} \setminus \mathbb{Q}$（無理数全体）も稠密であり、有理数と無理数は $\mathbb{R}$ 上に複雑に入り混じっている。

---

## 完備順序体の一意性

定理1・2・3（体・全順序・上限性質）をすべて満たす順序体は、同型の意味でただ一つである。これにより、デデキント切断で構成しようとコーシー列で構成しようと、得られる $\mathbb{R}$ は本質的に同じ対象であることが保証される。$\mathbb{R}$ とはこの3条件を満たすただ一つの構造のことであり、構成はその存在証明に相当する。

> **注：** この一意性の証明は体論・順序体論の言葉で行われる。概略としては、完備順序体 $F$ には $\mathbb{Q}$ が順序体として一意に埋め込まれ（$\mathbb{Q}$ は素体であるため）、さらに完備性から $F$ の各元が $\mathbb{Q}$ の下界の上限として一意に定まることを示す。詳細は[ノート：完備順序体の一意性](40_knowledge-base/10_mathematics/20_set-theory/90-completeness-uniqueness/)を参照。

