+++
title = "ZFC 公理系の論理式"
weight = 30
date = 2026-08-08
+++

ZFC の各公理を一階述語論理の論理式で厳密に記述する。言語は変数と基本述語 $\in$ のみからなり、等号 $=$ は論理記号として扱う。

---

{{< toc >}}

---

## 公理1：外延性の公理

$$\forall x, \forall y, \bigl(\forall z, (z \in x \leftrightarrow z \in y) \rightarrow x = y\bigr)$$

同じ要素をもつ集合は等しい。集合の同一性を外延（要素の集まり）によって定める。逆向き（$x = y \rightarrow \forall z,(z \in x \leftrightarrow z \in y)$）は等号の公理から従う。

>一階述語論理における等号の公理（代入原理）は、任意の論理式 $\phi$ と変数 $v$、項 $t_1, t_2$ について次を要請する。
>
>$$\vdash t_1 = t_2 \rightarrow (\phi[t_1/v] \leftrightarrow \phi[t_2/v])$$
>
>ここで、論理式 $\phi(v)$ を「$z \in v$」とする。$t_1$ に $x$、$t_2$ に $y$ を代入すると、以下が成り立つ。
>
>$$\vdash x = y \rightarrow (z \in x \leftrightarrow z \in y)$$
>
>変数 $z$ について全称例化を行えば、求める逆向きの含意が得られる。
>
>$$\vdash x = y \rightarrow \forall z,(z \in x \leftrightarrow z \in y)$$

---

## 公理2：空集合の公理

$$\exists x, \forall y, (y \notin x)$$

要素を一切もたない集合 $\emptyset$ の存在を保証する。外延性の公理により、この集合は一意に定まる。

> 性質 $P(x)$ を満たす $x$ が「ただ一つ存在する」という命題は、記号 $\exists!$ を用いて $\exists! x, P(x)$ と書き、**一意存在量化記号**と呼ぶ。一階述語論理において、これは $\exists$ と $\forall$ を組み合わせた以下の論理式として定義される。
>
> $$\exists x, (P(x) \land \forall y, (P(y) \to x=y))$$
>
> 空集合の公理は「要素をもたない集合の存在」を保証するが、それが「ただ一つ」であることは外延性の公理から導かれる。すなわち、$\forall y,(y \notin x)$ を満たす $x$ がただ一つ存在すること（$\exists! x, \forall y,(y \notin x)$）を示せる。
>
> 1. **存在:** 空集合の公理より、$\forall y,(y \notin x)$ を満たす集合 $x$ が存在する。
> 2. **一意性:** $x$ と $z$ を、ともに要素をもたない任意の集合とする。すなわち、$\forall y,(y \notin x)$ かつ $\forall y,(y \notin z)$ が成り立つと仮定する。
> このとき、任意の対象 $y$ について「$y \in x$」も「$y \in z$」も偽であるため、論理的同値 $y \in x \leftrightarrow y \in z$ は常に真となる。
> 外延性の公理より、すべての $y$ についてこれが成り立つならば $x = z$ である。
>
> したがって、要素を一切もたない集合はただ一つ存在し、我々はこの唯一の対象に $\emptyset$ という固有の記号を割り当てることができる。

> **注.** 無限の公理が保証する集合 $x$ に対して分出公理図式を $\phi(z) \equiv z \neq z$ で適用すれば $\emptyset$ が得られるため、空集合の公理を独立な公理としない流儀もある。

---

> **存在公理と一意性（記号の正当化）**
>
> これから述べる、対の公理、和集合の公理、冪集合の公理（および分出・置換公理）は、いずれもある条件 $\phi(z)$ を用いて「$\forall z,(z \in y \leftrightarrow \phi(z))$ を満たす集合 $y$ が存在する（$\exists y$）」という形で記述される。
>
> ここで**外延性の公理**を適用すると、要素が完全に一致する集合は等しいため、条件を満たす集合 $y$ は「ただ一つ存在する（$\exists! y$）」ことが自動的に導かれる（論理構造は空集合の一意性の証明と全く同じである）。
>
> 公理によって存在が、外延性によって一意性が保証されて初めて、我々はその唯一の対象に対して $\{x, y\}$、$\bigcup x$、$\mathcal{P}(x)$ といった固有の記号を割り当てることができる。

## 公理3：対の公理

$$\forall x, \forall y, \exists z, \forall w, (w \in z \leftrightarrow w = x \lor w = y)$$

任意の $x, y$ に対し、$x$ と $y$ のみを要素とする集合が存在する。前述の通り外延性の公理によりこれは一意に定まるため、これを $\{x, y\}$ と表記する。$x = y$ のとき $z = \{x\}$ となる（一元集合）。

---

## 公理4：和集合の公理

$$\forall x, \exists y, \forall z, \bigl(z \in y \leftrightarrow \exists w, (w \in x \land z \in w)\bigr)$$

集合族 $x$ に対し、その要素の要素をすべて集めた集合が存在する。外延性の公理により一意に定まるため、その集合を $\bigcup x$ と表記する。
なお、二項和 $A \cup B$ は、対の公理で $\{A, B\}$ を得てから $\bigcup\{A, B\}$ とすることで定義される。

---

## 公理5：冪集合の公理

$$\forall x, \exists y, \forall z, \bigl(z \in y \leftrightarrow \forall w, (w \in z \rightarrow w \in x)\bigr)$$

任意の $x$ に対し、$x$ の部分集合をすべて集めた集合が存在する。外延性の公理により一意に定まるため、これを $\mathcal{P}(x)$ と表記する。

---

## 公理6：無限の公理

$$\exists x, \bigl(\emptyset \in x \;\land\; \forall y, (y \in x \rightarrow y \cup \{y\} \in x)\bigr)$$

$\emptyset$ を含み、$y$ を含めば $y \cup \{y\}$ も含む帰納的集合が存在する。これにより自然数全体 $\omega$ の存在が保証される（$\omega$ の構成は[ノート：自然数](40_knowledge-base/10_mathematics/20_set-theory/50-naturals/)で扱う）。

$\emptyset$ や $\cup$ を略記として使わない展開形：

$$\exists x, \Bigl(\exists e,\bigl(\forall z, z \notin e \land e \in x\bigr) \;\land\; \forall y,\bigl(y \in x \rightarrow \exists s,(\forall z,(z \in s \leftrightarrow z \in y \lor z = y) \land s \in x)\bigr)\Bigr)$$

---

## 公理7：分出公理図式

$\phi(z, p_1, \ldots, p_n)$ を $y$ を自由変数として含まない任意の論理式とする。

$$\forall A, \forall p_1 \cdots \forall p_n, \exists y, \forall z, \bigl(z \in y \leftrightarrow z \in A \land \phi(z, p_1, \ldots, p_n)\bigr)$$

既存の集合 $A$ から条件 $\phi$ を満たす要素を切り出した部分集合 $\{z \in A \mid \phi(z)\}$ の存在を保証する。素朴集合論の無制限内包原理（$\{x \mid \phi(x)\}$ を無条件に集合とみなすこと）を制限し、ラッセルのパラドックスを回避する。

$\phi$ が任意の論理式を動くため、これは単一の公理ではなく論理式ごとに一つの公理を与える無限の族（公理図式）である。

---

## 公理8：置換公理図式

$\phi(x, y, p_1, \ldots, p_n)$ を任意の論理式とする。

$$\forall A, \forall p_1 \cdots \forall p_n, \Bigl[\forall x \in A, \exists! y, \phi(x, y) \;\rightarrow\; \exists B, \forall y, \bigl(y \in B \leftrightarrow \exists x \in A, \phi(x, y)\bigr)\Bigr]$$

$\phi$ が $A$ 上の関数的対応（各 $x \in A$ に $y$ が一意に対応）を定めるとき、その像 $\{y \mid \exists x \in A, \phi(x, y)\}$ が集合として存在する。分出公理図式が「既存集合からの切り出し」であるのに対し、置換公理図式は「写し」によって新たな集合を得る。

---

## 公理9：正則性の公理

$$\forall x, \Bigl(\exists y, (y \in x) \;\rightarrow\; \exists y \in x, \forall z, (z \in y \rightarrow z \notin x)\Bigr)$$

空でない集合 $x$ は、$x$ との共通要素をもたない要素（$\in$-極小元）をもつ。$x \in x$ や $x \in y \in x$ のような循環的帰属を排除し、集合の世界に「底」のある階層構造（累積階層 $V = \bigcup_{\alpha} V_\alpha$）を与える。

---

## 公理10：選択公理

$$\forall x, \Bigl(\forall y \in x, (y \neq \emptyset) \;\rightarrow\; \exists f, \forall y \in x, (f(y) \in y)\Bigr)$$

空でない集合を要素とする集合 $x$ に対し、各 $y \in x$ から一つずつ要素を選ぶ関数（選択関数）$f$ が存在する。$f$ が関数であることを展開した形（$f$ を順序対の集合としてとらえる）：

$$\forall x, \Bigl(\forall y \in x, \exists z, (z \in y) \;\rightarrow\; \exists f, \forall y \in x, \exists! z, \bigl(z \in y \land \langle y, z \rangle \in f\bigr)\Bigr)$$

ここで $\langle y, z \rangle$ はクラトフスキー順序対 $\{\{y\}, \{y, z\}\}$ の略記。

選択公理は ZFC の他の公理から独立であり（コーエンによる強制法で示される）、数学の多くの場面で暗黙に使われている。
