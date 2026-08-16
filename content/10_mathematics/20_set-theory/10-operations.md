+++
title = "集合演算とド・モルガンの法則"
weight = 10
date = 2026-08-09
+++

ZFC の公理から集合演算（和・共通部分・差・冪集合）を正当化し、演算法則をすべて証明する。
「この演算が集合として存在すること」と「その演算が特定の法則を満たすこと」を区別しながら進める。

---

{{< toc >}}

---

## 集合演算の公理的正当化

各演算が集合として存在することを、どの公理が保証しているかを明示する。

### 和集合 $A \cup B$

$$A \cup B := \{x \mid x \in A \lor x \in B\}$$

**構成：** 対の公理により $\\{A, B\\}$ が存在する。和集合の公理により $\bigcup\\{A, B\\}$ が存在する。

$$A \cup B = \bigcup\{A, B\} = \{x \mid \exists z \in \{A,B\},\, x \in z\} = \{x \mid x \in A \lor x \in B\}$$

> **使用公理:** 対の公理 + 和集合の公理

---

### 共通部分 $A \cap B$

$$A \cap B := \{x \in A \mid x \in B\}$$

**構成：** 分出公理図式を $A$ に適用し、条件 $\phi(x) := x \in B$ で切り出す。

素朴には $\\{x \mid x \in A \land x \in B\\}$ と書きたくなるが、ZFC では必ず既存の集合（ここでは $A$）から切り出す形をとる。$A$ と $B$ の役割は対称だが、構成の手続き上はどちらか一方を母集合に選ぶ。外延性の公理により結果は同じ集合になる。

> **使用公理:** 分出公理図式

---

### 差集合 $A \setminus B$

$$A \setminus B := \{x \in A \mid x \notin B\}$$

**構成：** 分出公理図式を $A$ に適用し、条件 $\phi(x) := x \notin B$ で切り出す。

> **使用公理:** 分出公理図式

---

### 冪集合 $\mathcal{P}(A)$

$$\mathcal{P}(A) := \{x \mid x \subseteq A\}$$

**構成：** 冪集合の公理が直接保証する。

> **例:** 
$A = \\{a, b\\}$ のとき $\mathcal{P}(A) = \\{\emptyset, \\{a\\}, \\{b\\}, \\{a,b\\}\\}$
。一般に $|A| = n$ ならば $|\mathcal{P}(A)| = 2^n$。（ただし、$|A|$ は集合の要素の個数を表す。）

> **使用公理:** 冪集合の公理

---

### まとめ

| 演算 | 記法 | 使用公理 |
| :---: | :---: | :--- |
| 和集合 | $A \cup B$ | 対の公理・和集合の公理 |
| 共通部分 | $A \cap B$ | 分出公理図式 |
| 差集合 | $A \setminus B$ | 分出公理図式 |
| 冪集合 | $\mathcal{P}(A)$ | 冪集合の公理 |

---

## 集合演算の法則

集合 $A, B, C$ に対して以下が成り立つ。証明はすべて「$x$ が左辺に属する $\iff$ $x$ が右辺に属する」という要素の言い換えによる。

### 可換律

$$A \cup B = B \cup A, \qquad A \cap B = B \cap A$$

**証明（和集合）**

$$\begin{align*}
  & x \in A \cup B \\
\iff{} & x \in A \lor x \in B \\
\iff{} & x \in B \lor x \in A \\
\iff{} & x \in B \cup A. \quad \square
\end{align*}$$

**証明（共通部分）**

$$\begin{align*}
  & x \in A \cap B \\
\iff{} & x \in A \land x \in B \\
\iff{} & x \in B \land x \in A \\
\iff{} & x \in B \cap A. \quad \square
\end{align*}$$

---

### 結合律

$$(A \cup B) \cup C = A \cup (B \cup C), \qquad (A \cap B) \cap C = A \cap (B \cap C)$$

**証明（和集合）**

$$\begin{align*}
  & x \in (A \cup B) \cup C \\
\iff{} & (x \in A \lor x \in B) \lor x \in C \\
\iff{} & x \in A \lor (x \in B \lor x \in C) \\
\iff{} & x \in A \cup (B \cup C). \quad \square
\end{align*}$$

**証明（共通部分）**

$$\begin{align*}
  & x \in (A \cap B) \cap C \\
\iff{} & (x \in A \land x \in B) \land x \in C \\
\iff{} & x \in A \land (x \in B \land x \in C) \\
\iff{} & x \in A \cap (B \cap C). \quad \square
\end{align*}$$

---

### 分配律

$$A \cap (B \cup C) = (A \cap B) \cup (A \cap C), \qquad A \cup (B \cap C) = (A \cup B) \cap (A \cup C)$$

**証明（第1式）**

$$\begin{align*}
  & x \in A \cap (B \cup C) \\
\iff{} & x \in A \land (x \in B \lor x \in C) \\
\iff{} & (x \in A \land x \in B) \lor (x \in A \land x \in C) \\
\iff{} & x \in (A \cap B) \cup (A \cap C). \quad \square
\end{align*}$$

**証明（第2式）**

$$\begin{align*}
  & x \in A \cup (B \cap C) \\
\iff{} & x \in A \lor (x \in B \land x \in C) \\
\iff{} & (x \in A \lor x \in B) \land (x \in A \lor x \in C) \\
\iff{} & x \in (A \cup B) \cap (A \cup C). \quad \square
\end{align*}$$

---

### 補集合の基本性質

以下では全体集合 $U$ を固定し、$A \subseteq U$ に対して補集合を $A^c := U \setminus A$ と定める。

$$A \cup A^c = U, \qquad A \cap A^c = \emptyset, \qquad (A^c)^c = A$$

**証明（第1式）**

$$\begin{align*}
  & x \in A \cup A^c \\
\iff{} & x \in A \lor x \notin A
\end{align*}$$

これは恒真であり、$x \in U$ と同値（$U$ が全体集合のため）。$\square$

**証明（第2式）**

$$\begin{align*}
  & x \in A \cap A^c \\
\iff{} & x \in A \land x \notin A
\end{align*}$$

これは恒偽であり、いかなる $x$ も属さないから $A \cap A^c = \emptyset$。$\square$

**証明（第3式）**

$$\begin{align*}
  & x \in (A^c)^c \\
\iff{} & x \notin A^c \\
\iff{} & \lnot(x \notin A) \\
\iff{} & x \in A. \quad \square
\end{align*}$$

---

### ド・モルガンの法則

$${(A \cup B)^c = A^c \cap B^c, \qquad (A \cap B)^c = A^c \cup B^c}$$

**証明（第1式）**

$$\begin{align*}
  & x \in (A \cup B)^c \\
\iff{} & x \notin A \cup B \\
\iff{} & \lnot(x \in A \lor x \in B) \\
\iff{} & x \notin A \land x \notin B \\
\iff{} & x \in A^c \land x \in B^c \\
\iff{} & x \in A^c \cap B^c. \quad \square
\end{align*}$$

**証明（第2式）**

$$\begin{align*}
  & x \in (A \cap B)^c \\
\iff{} & x \notin A \cap B \\
\iff{} & \lnot(x \in A \land x \in B) \\
\iff{} & x \notin A \lor x \notin B \\
\iff{} & x \in A^c \lor x \in B^c \\
\iff{} & x \in A^c \cup B^c. \quad \square
\end{align*}$$

> **ド・モルガンの法則の読み方:** 和の補集合は補集合の共通部分。共通部分の補集合は補集合の和。論理式での $\lnot(P \lor Q) \iff \lnot P \land \lnot Q$ と対応しており、集合と論理の対称性が現れている。

---

### 一般化されたド・モルガンの法則

有限個だけでなく、任意の集合族 $\\{A_\lambda\\}_{\lambda \in \Lambda}$ に対しても成立する。

$$\left(\bigcup_{\lambda \in \Lambda} A_\lambda\right)^c = \bigcap_{\lambda \in \Lambda} A_\lambda^c, \qquad \left(\bigcap_{\lambda \in \Lambda} A_\lambda\right)^c = \bigcup_{\lambda \in \Lambda} A_\lambda^c$$

**証明（第1式）**

$$\begin{align*}
  & x \in \left(\bigcup_{\lambda \in \Lambda} A_\lambda\right)^c \\
\iff{} & x \notin \bigcup_{\lambda \in \Lambda} A_\lambda \\
\iff{} & \lnot\,\exists \lambda \in \Lambda,\, x \in A_\lambda \\
\iff{} & \forall \lambda \in \Lambda,\, x \notin A_\lambda \\
\iff{} & \forall \lambda \in \Lambda,\, x \in A_\lambda^c \\
\iff{} & x \in \bigcap_{\lambda \in \Lambda} A_\lambda^c. \quad \square
\end{align*}$$

第2式も同様に示せる。
