+++
title = "集合族・添字集合"
weight = 40
date = 2026-08-11
+++

集合演算では $\bigcup_{\lambda \in \Lambda} A_\lambda$ や $\{A_\lambda\}_{\lambda \in \Lambda}$ という記法を予告なしに使った。本稿ではこれを遡って正当化する。添字付きの集合の族を写像として定義し、一般化された和・共通部分を公理から構成する。

---

{{< toc >}}

---

## 動機：有限個の和を超えて

和集合の公理は $\bigcup \mathcal{F}$（集合族 $\mathcal{F}$の全要素の合併）を与えるが、実際には、$\lambda$ というラベルを付けて集合の族を管理したい場面が頻繁に現れる。位相空間論では、開集合族の任意の和、測度論では可算個の集合の和が基本的な操作として登場する。

これを正確に扱うには、ラベルの集合（添字集合）と各ラベルに集合を対応させる規則（写像）という二つの概念が必要である。ともに写像の構成で整備した道具の自然な応用である。

---

## 集合族・添字族の定義

### 定義：集合族

集合 $\mathcal{F}$ の要素がすべて集合であるとき、$\mathcal{F}$ を**集合族**という。

> **注意：** ZFC ではすべての対象は集合であるから、これは任意の集合に当てはまる。集合族という言葉は、その要素を集合として扱うことを意識しているという文脈の宣言である。

### 定義：添字族・添字集合

集合 $\Lambda$（**添字集合**）から集合の集まりへの写像

$$A : \Lambda \to \mathcal{F}, \qquad \lambda \mapsto A_\lambda$$

を**添字族**といい、$\{A_\lambda\}_{\lambda \in \Lambda}$ または $(A_\lambda)_{\lambda \in \Lambda}$ と書く。

ここで $A$ は写像（すなわち、順序対の集合 $\{\langle \lambda, A_\lambda \rangle \mid \lambda \in \Lambda\}$）である。$A_\lambda$ は $A(\lambda)$の略記である。

> **写像としての実体：** $\{A_\lambda\}_{\lambda \in \Lambda}$ という記法は便利だが、その背後には写像 $A: \Lambda \to \mathcal{F}$ がある。ラベルを貼って集合を管理する操作が、ZFC の土台の上では写像一つとして構成される。

### 例

- $\Lambda = \{1, 2, 3\}$、$A_1 = \{a\}$、$A_2 = \{b, c\}$、$A_3 = \{a, c\}$：有限族
- $\Lambda = \mathbb{N}$（自然数全体）、$A_n = \{n, n+1, n+2, \ldots\}$：可算族
- $\Lambda = \mathbb{R}$、$A_r = (-r, r) \subseteq \mathbb{R}$：非可算族

---

## 一般化された和・共通部分の構成

### 定義：一般化された和集合

添字族 $\{A_\lambda\}_{\lambda \in \Lambda}$ に対し、

$$\bigcup_{\lambda \in \Lambda} A_\lambda := \bigcup \{A_\lambda \mid \lambda \in \Lambda\} = \{x \mid \exists \lambda \in \Lambda,\, x \in A_\lambda\}$$

**構成：** $\{A_\lambda \mid \lambda \in \Lambda\}$ は置換公理図式によって集合として存在する（写像 $A: \Lambda \to \mathcal{F}$ の像 $A[\Lambda]$）。和集合の公理により $\bigcup A[\Lambda]$ が存在する。

> **使用公理：** 置換公理図式（像の存在）+ 和集合の公理

### 定義：一般化された共通部分

$\Lambda \neq \emptyset$ のとき、

$$\bigcap_{\lambda \in \Lambda} A_\lambda := \{x \in \bigcup_{\lambda \in \Lambda} A_\lambda \mid \forall \lambda \in \Lambda,\, x \in A_\lambda\}$$

**構成：** まず $\bigcup_{\lambda \in \Lambda} A_\lambda$ が存在する（上記）。分出公理図式によりその部分集合として $\bigcap_{\lambda \in \Lambda} A_\lambda$ が存在する。

> **使用公理：** 分出公理図式（$\bigcup_{\lambda \in \Lambda} A_\lambda$ からの切り出し）

> **$\Lambda = \emptyset$ の場合：** $\bigcap_{\lambda \in \emptyset} A_\lambda$ をすべての集合を要素とする集合と解釈したくなるが、これは真のクラスであり ZFC の集合ではない。添字集合が空のとき一般化された共通部分は定義しないのが標準的な扱いである（あるいは文脈に応じた全体集合 $U$ のもとで $\bigcap_{\lambda \in \emptyset} A_\lambda := U$ と定める）。

---

## 基本性質

### 命題1：単調性

$\Lambda' \subseteq \Lambda$ ならば、

$$\bigcup_{\lambda \in \Lambda'} A_\lambda \subseteq \bigcup_{\lambda \in \Lambda} A_\lambda, \qquad \bigcap_{\lambda \in \Lambda} A_\lambda \subseteq \bigcap_{\lambda \in \Lambda'} A_\lambda$$

**証明（和集合）.** $x \in \bigcup_{\lambda \in \Lambda'} A_\lambda$ ならば $\exists \lambda \in \Lambda',\, x \in A_\lambda$$。$$\Lambda' \subseteq \Lambda$ より $\lambda \in \Lambda$ でもあるから $x \in \bigcup_{\lambda \in \Lambda} A_\lambda$。$\square$

**証明（共通部分）.** $x \in \bigcap_{\lambda \in \Lambda} A_\lambda$ ならば $\forall \lambda \in \Lambda,\, x \in A_\lambda$。$\Lambda' \subseteq \Lambda$ より特に $\forall \lambda \in \Lambda',\, x \in A_\lambda$、すなわち $x \in \bigcap_{\lambda \in \Lambda'} A_\lambda$。$\square$

> 和では添字が増えると大きくなり、共通部分では添字が増えると小さくなる。これは直感と一致する。

### 命題2：分配律（和と共通部分の交換）

$$A \cap \bigcup_{\lambda \in \Lambda} A_\lambda = \bigcup_{\lambda \in \Lambda} (A \cap A_\lambda)$$

$$A \cup \bigcap_{\lambda \in \Lambda} A_\lambda = \bigcap_{\lambda \in \Lambda} (A \cup A_\lambda) \qquad (\Lambda \neq \emptyset)$$

**証明（第1式）.**

$$
\begin{aligned}
x \in A \cap \bigcup_{\lambda \in \Lambda} A_\lambda
&\iff x \in A \land \exists \lambda \in \Lambda,\, x \in A_\lambda \\
&\iff \exists \lambda \in \Lambda,\, (x \in A \land x \in A_\lambda) \\
&\iff \exists \lambda \in \Lambda,\, x \in A \cap A_\lambda \\
&\iff x \in \bigcup_{\lambda \in \Lambda} (A \cap A_\lambda). \quad \square
\end{aligned}
$$

**証明（第2式）.**

$$
\begin{aligned}
x \in A \cup \bigcap_{\lambda \in \Lambda} A_\lambda
&\iff x \in A \lor \forall \lambda \in \Lambda,\, x \in A_\lambda \\
&\iff \forall \lambda \in \Lambda,\, (x \in A \lor x \in A_\lambda) \\
&\iff \forall \lambda \in \Lambda,\, x \in A \cup A_\lambda \\
&\iff x \in \bigcap_{\lambda \in \Lambda} (A \cup A_\lambda). \quad \square
\end{aligned}
$$

> **注意（第2式）：** $\Lambda = \emptyset$ のとき左辺は $A \cup \bigcap_{\lambda \in \emptyset} A_\lambda$ だが、$\bigcap_{\lambda \in \emptyset}$ は未定義なので成立しない。

### 命題3：一般化されたド・モルガンの法則

全体集合 $U$ を固定し、$A \subseteq U$ に対して $A^c := U \setminus A$ とおく。

$$\left(\bigcup_{\lambda \in \Lambda} A_\lambda\right)^c = \bigcap_{\lambda \in \Lambda} A_\lambda^c, \qquad \left(\bigcap_{\lambda \in \Lambda} A_\lambda\right)^c = \bigcup_{\lambda \in \Lambda} A_\lambda^c \qquad (\Lambda \neq \emptyset)$$

**証明（第1式）.**

$$
\begin{aligned}
x \in \left(\bigcup_{\lambda \in \Lambda} A_\lambda\right)^c
&\iff x \notin \bigcup_{\lambda \in \Lambda} A_\lambda \\
&\iff \lnot\,\exists \lambda \in \Lambda,\, x \in A_\lambda \\
&\iff \forall \lambda \in \Lambda,\, x \notin A_\lambda \\
&\iff \forall \lambda \in \Lambda,\, x \in A_\lambda^c \\
&\iff x \in \bigcap_{\lambda \in \Lambda} A_\lambda^c. \quad \square
\end{aligned}
$$

第2式も同様。

> これは[ノート：集合演算とド・モルガンの法則](40_knowledge-base/10_mathematics/20_set-theory/10-operations/)で証明した有限版の自然な一般化であり、証明の構造は全く同じである。そこでは定義を先取りして使っていたが、ここで正当化される。

---

## 直積の一般化

2集合の直積 $A \times B$ を任意の添字族に拡張する。

### 定義：直積（一般）

添字族 $\{A_\lambda\}_{\lambda \in \Lambda}$ に対し、**直積**を

$$\prod_{\lambda \in \Lambda} A_\lambda := \left\{f : \Lambda \to \bigcup_{\lambda \in \Lambda} A_\lambda \;\middle|\; \forall \lambda \in \Lambda,\, f(\lambda) \in A_\lambda\right\}$$

と定義する。すなわち、各成分 $f(\lambda)$ が $A_\lambda$ に属するような写像 $f$ の全体である。

$f \in \prod_{\lambda \in \Lambda} A_\lambda$ を**選択関数**ともいう。

> **構成と選択公理の役割** 
>
>$\Lambda$ から $\bigcup_{\lambda \in \Lambda} A_\lambda$ への写像全体の集合は、冪集合公理と分出公理により（親集合として）存在する。この親集合から任意の写像 $f$ を所与のものとして考えたとき、「$\forall \lambda \in \Lambda,\, f(\lambda) \in A_\lambda$」という判定条件は、$f$ を変数とする一階述語論理の式として記述できる。
>
>したがって、$f$ が具体的にどのようなルールで要素を選んでいるか（そのルールが具体的な式で書き下せるか否か）に関わらず、分出公理図式によってこの判定条件をパスする $f$ のみを親集合から切り出して、直積という集合を構成できる。
>
>ただし、ここで分出公理が保証するのは、あくまで条件を満たす $f$ を集めた集合を構成する手順までである。各 $A_\lambda$ が空でない（$\forall \lambda \in \Lambda,\, A_\lambda \neq \emptyset$）という前提のもとで、この判定条件をパスする写像 $f$ が少なくとも1つは存在する（すなわち $\prod_{\lambda \in \Lambda} A_\lambda \neq \emptyset$ である）と強引に保証するのが、選択公理の役割である。

> **なぜ終域が $\bigcup A_\lambda$ なのか？**
>
> 各 $\lambda$ ごとに行き先 $A_\lambda$ が決まっているのに、わざわざ全部混ぜた巨大な和集合 $\bigcup A_\lambda$を終域とするのは、少し大雑把で無理やりな定義に見えるかもしれない。しかし、これには ZFC のルール（分出公理）上の明確な理由がある。
>
> ZFC では条件を満たすものを集めて集合を作る際、何もない空間からいきなり集めることはできず、すでに存在が保証されている親集合 $X$ の中から $\{ x \in X \mid \text{条件} \}$ という形で切り出さなければならない。
>
> ここでは直積の要素として写像 $f$ たちを集めたいが、写像たちを閉じ込めるための安全な親集合が必要になる。そこで、とりあえず全部の要素をごちゃ混ぜにした一番大きな箱（$\bigcup A_\lambda$）を用意し、そこへの写像全体の集合を親集合として確保したうえで、実は各 $\lambda$ ごとにちゃんと対応する $A_\lambda$ に入っているという厳しい条件（$\forall \lambda, f(\lambda) \in A_\lambda$）で後から絞り込むというテクニックを使っているのである。
> （より厳密に書けば、親集合として冪集合 $\mathcal{P}\left(\Lambda \times \bigcup A_\lambda\right)$ を用いて切り出している。）

### 例： $\Lambda = \{1, 2\}$ のとき

$f \in \prod_{\lambda \in \{1,2\}} A_\lambda$ は $f(1) \in A_1$$、$$f(2) \in A_2$ を満たす写像。$f \leftrightarrow \langle f(1), f(2) \rangle$ という対応により、$\prod_{\lambda \in \{1,2\}} A_\lambda \cong A_1 \times A_2$。

### 選択公理との関係

$$\Lambda \neq \emptyset \land \forall \lambda \in \Lambda,\, A_\lambda \neq \emptyset \implies \prod_{\lambda \in \Lambda} A_\lambda \neq \emptyset$$

これが**選択公理**（ZFC の公理10）の内容に他ならない。
有限個のとき（$|\Lambda| < \infty$）は選択公理なしに証明できる。
無限個の空でない集合の族に対して全成分から同時に一つ選べることは、
他の公理からは導けない。それを保証するのが選択公理である。

> 直積の空でなさと選択公理の関係は、この先の解析・位相・代数のいたるところで暗黙に使われる。「ここで選択公理を使っている」と気づけることが、ZFC からの論理の鎖を丁寧に追う意義の一つである。

---

## 添字の変換

### 命題4：添字の置き換え

全単射 $\sigma: \Lambda' \to \Lambda$ があるとき、

$$\bigcup_{\lambda \in \Lambda} A_\lambda = \bigcup_{\mu \in \Lambda'} A_{\sigma(\mu)}, \qquad \bigcap_{\lambda \in \Lambda} A_\lambda = \bigcap_{\mu \in \Lambda'} A_{\sigma(\mu)}$$

**証明（和集合）.** $x \in \bigcup_{\lambda \in \Lambda} A_\lambda \iff \exists \lambda \in \Lambda,\, x \in A_\lambda \iff \exists \mu \in \Lambda',\, x \in A_{\sigma(\mu)}$（$\sigma$ が全射であることを使う）。$\square$

> **意味：** 添字集合を変えても、（全単射の意味での）同型性が保たれていれば和・共通部分は変わらない。添字のラベルは本質ではなく、集合の族の構造が本質である。

---

集合族・添字集合は単独では抽象的に見えるが、距離空間・位相空間・ベクトル空間のいずれもが集合族を扱う道具の上に立っている。位相空間の定義で任意の和に閉じているという条件は、一般化された和集合 $\bigcup_{\lambda \in \Lambda} U_\lambda$ が定義されていなければ述べることができない。

---

## 記法の整理

| 記法 | 意味 |
|:-----|:-----|
| $\{A_\lambda\}_{\lambda \in \Lambda}$ | 添字集合 $\Lambda$ による添字族（写像 $\lambda \mapsto A_\lambda$）|
| $(A_\lambda)_{\lambda \in \Lambda}$ | 同上（順序を強調したいときに使う）|
| $\bigcup_{\lambda \in \Lambda} A_\lambda$ | 添字族の一般化された和集合 |
| $\bigcap_{\lambda \in \Lambda} A_\lambda$ | 添字族の一般化された共通部分（$\Lambda \neq \emptyset$）|
| $\prod_{\lambda \in \Lambda} A_\lambda$ | 添字族の一般化された直積（選択関数の集合）|
| $\bigcup \mathcal{F}$ | 集合族 $\mathcal{F}$ の和集合（和集合の公理の直接適用）|

$\bigcup \mathcal{F}$$ と $$\bigcup_{\lambda \in \Lambda} A_\lambda$ は同じ集合を指す（$\mathcal{F} = \{A_\lambda \mid \lambda \in \Lambda\}$ のとき）。前者は公理の直接適用、後者は添字を明示した書き方である。
