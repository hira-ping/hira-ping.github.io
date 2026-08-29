+++
title = "固有値・固有ベクトル"
weight = 40
date = 2026-08-29
+++

本ノートでは固有空間の理論を展開する。固有値・固有ベクトルは行列が最も単純に作用する方向を捉えるための概念であり、対角化はその構造を活用する計算技術である。本ノートの到達点はスペクトル定理（エルミート行列は常にユニタリ行列で対角化可能であること）であり、ここで内積と行列式の理論が統合される。

---

{{< toc >}}

---

## 固有値と固有ベクトル

### 定義：固有値・固有ベクトル

$A \in \mathrm{M}_n(\mathbb{C})$ とする。スカラー $\lambda \in \mathbb{C}$ と零でないベクトル $\mathbf{v} \in \mathbb{C}^n$ が

$$A\mathbf{v} = \lambda \mathbf{v}$$

を満たすとき、$\lambda$ を $A$ の**固有値**、$\mathbf{v}$ を $\lambda$ に対応する**固有ベクトル**という。

> **幾何的意味：**
>
> 固有ベクトルは $A$ による線形写像で方向が変わらないベクトルである。
> 固有値 $\lambda \in \mathbb{C}$ を極形式 $\lambda = re^{i\theta}$（$r = |\lambda| \geq 0$、$\theta = \arg\lambda$）で表すと、$A\mathbf{v} = \lambda\mathbf{v}$ の作用は次の二段階に分解される：
>
> 1. **スケール変化**：絶対値 $r = |\lambda|$ 
>倍にベクトルを伸縮する。
>$r > 1$ なら拡大、
>$0 < r < 1$ なら縮小、
>$r = 0$ なら零ベクトルに潰す。
> 2. **位相の回転**：偏角 $\theta$ だけ複素数倍による回転が生じる。$\theta = 0$（$\lambda > 0$）なら同じ向き、$\theta = \pi$（$\lambda < 0$）なら逆向き、一般の $\theta$ では複素平面上で角度 $\theta$ の回転として現れる。
>
> 実固有値の場合（$\theta = 0$ または $\pi$）は実数軸上の伸縮・反転に対応し、複素固有値の場合はスケール変化と回転が合成された螺旋的な作用となる。

> **固有値の幾何的（物理的）意味：$\mathbb{R}^n$ の矢印から $\mathbb{C}^n$ の波へ**
>
> 実ベクトル空間 $\mathbb{R}^n$ では、ベクトルは空間の静的な矢印であり、固有値 $\lambda \in \mathbb{R}$ はその矢印を同じ向きに伸ばす（$\lambda > 0$）、または逆向きに伸ばす（$\lambda < 0$）スケール変換を意味する。
>
> 一方、複素ベクトル空間 $\mathbb{C}^n$ においては、ベクトルを振幅と位相（タイミングのズレ）を持った振動のセットとして解釈すると直観的である。このとき、複素固有値を極形式で $\lambda = re^{i\theta}$ と表すと、固有値の作用は全体の振幅を $r$ 倍にスケールし、位相を一斉に $\theta$ だけ進める（または遅らせる）操作になる。
>
> 固有ベクトルとは、行列 $A$ による複雑な成分の混ぜ合わせが、その特定の状態に対しては単なる一律の増幅と位相シフト（$re^{i\theta}$ 倍）という単純な作用になるような、特別な振動のパッケージを指している。

### 固有値の求め方（特性多項式）

$A\mathbf{v} = \lambda\mathbf{v}$ かつ $\mathbf{v} \neq \mathbf{0}$ は、$(A - \lambda I)\mathbf{v} = \mathbf{0}$ が非自明解を持つことと同値。rank-nullity 定理より、これは $A - \lambda I$ が正則でないこと、すなわち

$$\det(A - \lambda I) = 0$$

と同値。$\det(A - \lambda I)$ は $\lambda$ の $n$ 次多項式であり、$A$ の**特性多項式**という。

$$p_A(\lambda) := \det(A - \lambda I)$$

特性多項式の根が固有値の全体である。

**$2 \times 2$ の場合：**

$$A = \begin{pmatrix} a & b \\ c & d \end{pmatrix} \Rightarrow p_A(\lambda) = \det\begin{pmatrix} a-\lambda & b \\ c & d-\lambda \end{pmatrix} = \lambda^2 - (a+d)\lambda + (ad-bc)$$

$$= \lambda^2 - \mathrm{tr}(A)\lambda + \det(A)$$

ここで $\mathrm{tr}(A) = a + d$ は $A$ の**トレース**（対角成分の和）。

### 固有空間

固有値 $\lambda$ に対し、対応する固有ベクトル全体と零ベクトルを合わせた集合

$$V_\lambda := \ker(A - \lambda I) = \{\mathbf{v} \in \mathbb{C}^n \mid A\mathbf{v} = \lambda\mathbf{v}\}$$

を $\lambda$ の**固有空間**という。$V_\lambda$ は $\mathbb{C}^n$ の部分空間であり、$\dim V_\lambda \geq 1$。

**計算例：**

$$A = \begin{pmatrix} 3 & 1 \\ 1 & 3 \end{pmatrix}$$

特性多項式：$p_A(\lambda) = \lambda^2 - 6\lambda + 8 = (\lambda-2)(\lambda-4)$。固有値は $\lambda_1 = 2$、$\lambda_2 = 4$。

$\lambda_1 = 2$：$(A - 2I)\mathbf{v} = \mathbf{0}$ を解く。

$$\begin{pmatrix} 1 & 1 \\ 1 & 1 \end{pmatrix}\mathbf{v} = \mathbf{0} \Rightarrow V_2 = \mathrm{span}\left\{\begin{pmatrix}1\\-1\end{pmatrix}\right\}$$

$\lambda_2 = 4$：$(A - 4I)\mathbf{v} = \mathbf{0}$ を解く。

$$\begin{pmatrix} -1 & 1 \\ 1 & -1 \end{pmatrix}\mathbf{v} = \mathbf{0} \Rightarrow V_4 = \mathrm{span}\left\{\begin{pmatrix}1\\1\end{pmatrix}\right\}$$

---

## 対角化

### 定義：対角化可能

$A \in \mathrm{M}_n(\mathbb{C})$ が**対角化可能**であるとは、正則行列 $P$ と対角行列 $\Lambda$ が存在して

$$P^{-1}AP = \Lambda = \begin{pmatrix} \lambda_1 & & \\ & \ddots & \\ & & \lambda_n \end{pmatrix}$$

となることをいう。このとき $A = P\Lambda P^{-1}$。

> **基底変換としての解釈：**
>
> $A = P\Lambda P^{-1}$、あるいは $P^{-1}AP = \Lambda$ という式は、線形写像の基底変換の視点から見るとよくわかる。任意のベクトル $\mathbf{x}$ に対する $A$ の作用 $A\mathbf{x}$ を、$A = P\Lambda P^{-1}$ と分解して右から順に読むと：
>
> 1. **$P^{-1}\mathbf{x}$（視点の乗り換え）：** 標準基底での座標 $\mathbf{x}$ を、固有ベクトル $\{\mathbf{p}_1, \ldots, \mathbf{p}_n\}$ を基底とする新しい座標系 $\mathbf{y}$ に変換する。
> 2. **$\Lambda\mathbf{y}$（独立したスカラー倍）：** 新しい座標系においては、行列の作用は成分同士が混ざり合う複雑なものではなく、第 $i$ 成分を単に $\lambda_i$ 倍するという独立した操作（対角行列 $\Lambda$）になる。
> 3. **$P(\Lambda\mathbf{y})$（元の視点への復帰）：** 各成分を定数倍した後の結果を、再び標準基底の座標系に戻す。
>
> すなわち対角化とは、行列 $A$ の作用が、単なる各成分の独立したスカラー倍（$\Lambda$）として見えるような、最も都合の良い視点（固有ベクトル基底 $P$）を見つける操作である。

### 定理1：対角化の条件

$A \in \mathrm{M}_n(\mathbb{C})$ が対角化可能であることは、$\mathbb{C}^n$ が $A$ の固有ベクトルからなる基底をもつことと同値である。そのとき $P$ の列が固有ベクトル、$\Lambda$ の対角成分が対応する固有値となる。

**証明.**

$P = (\mathbf{p}_1 \mid \cdots \mid \mathbf{p}_n)$（列ベクトル表示）とすると、$AP = P\Lambda$ は

$$A\mathbf{p}_j = \lambda_j \mathbf{p}_j \qquad (j = 1,\ldots,n)$$

と同値。$P$ が正則 $\iff$ $\mathbf{p}_1,\ldots,\mathbf{p}_n$ が基底をなす。$\square$

### 命題2：異なる固有値に属する固有ベクトルは線形独立

固有値 $\lambda_1,\ldots,\lambda_k$ が互いに異なるとき、それぞれに属する固有ベクトル $\mathbf{v}_1,\ldots,\mathbf{v}_k$ は線形独立。

**証明.**

帰納法で示す。

$k=1$ は明らか（$\mathbf{v}_1 \neq \mathbf{0}$）。
$k-1$ まで成立と仮定し、$\sum_{i=1}^k c_i \mathbf{v}_i = \mathbf{0}$ とする。

両辺に $A$ を作用させると $\sum_i c_i \lambda_i \mathbf{v}_i = \mathbf{0}$。
元の式の $\lambda_k$ 倍を引くと

$$\sum_{i=1}^{k-1} c_i(\lambda_i - \lambda_k)\mathbf{v}_i = \mathbf{0}$$

帰納法の仮定より
$c_i(\lambda_i - \lambda_k) = 0$（$i < k$）。
$\lambda_i \neq \lambda_k$ だから
$c_i = 0$（$i < k$）。
元の式に戻ると
$c_k \mathbf{v}_k = \mathbf{0}$、$\mathbf{v}_k \neq \mathbf{0}$
より $c_k = 0$。$\square$

> **系：** $n$ 次行列が $n$ 個の異なる固有値を持てば対角化可能。

**対角化の計算例（上の $A$ の続き）：**

$$P = \begin{pmatrix} 1 & 1 \\ -1 & 1 \end{pmatrix}, \qquad P^{-1}AP = \begin{pmatrix} 2 & 0 \\ 0 & 4 \end{pmatrix}$$

確認：$$AP = \begin{pmatrix}3&1\\1&3\end{pmatrix}\begin{pmatrix}1&1\\-1&1\end{pmatrix} = \begin{pmatrix}2&4\\-2&4\end{pmatrix} = \begin{pmatrix}1&1\\-1&1\end{pmatrix}\begin{pmatrix}2&0\\0&4\end{pmatrix} = P\Lambda$$

### 対角化の利点：行列のべき乗

$A = P\Lambda P^{-1}$ のとき

$$A^k = P\Lambda^k P^{-1} = P\begin{pmatrix}\lambda_1^k&&\\&\ddots&\\&&\lambda_n^k\end{pmatrix}P^{-1}$$

一般の行列の $k$ 乗は $O(n^3 \log k)$ の計算が必要だが、対角化されていれば対角成分を $k$ 乗するだけ。漸化式・微分方程式の解法・マルコフ連鎖の長期挙動など、いたるところで使われる。

---
## スペクトル定理

### 定義：エルミート行列・ユニタリ行列

- $A^* = A$（$A^* := \bar{A}^T$：複素共役転置）を満たす行列を**エルミート行列**という。
- $U^* U = I$（$\iff U^* = U^{-1}$）を満たす正則行列を**ユニタリ行列**という。

ユニタリ行列の列ベクトルは $\mathbb{C}^n$ の正規直交基底をなす（逆も成立）。ユニタリ変換はノルムを保存する：$\|U\mathbf{v}\| = \|\mathbf{v}\|$。

> **実数の特別な場合：** 実行列では $A^* = A^T$ であるから、エルミート行列 $\supset$ 実対称行列（$A^T = A$）、ユニタリ行列 $\supset$ 直交行列（$Q^T Q = I$）となる。
>
### 定理2：エルミート行列の固有値は実数

$A \in \mathrm{M}_n(\mathbb{C})$ がエルミート行列（$A^* = A$）ならば、$A$ のすべての固有値は実数。

**証明.** $A\mathbf{v} = \lambda\mathbf{v}$（$\mathbf{v} \in \mathbb{C}^n$、$\mathbf{v} \neq \mathbf{0}$）とする。

第2引数の線形性から、

$$\langle \mathbf{v}, A\mathbf{v} \rangle = \langle \mathbf{v}, \lambda\mathbf{v} \rangle = \lambda \langle \mathbf{v}, \mathbf{v} \rangle = \lambda\|\mathbf{v}\|^2$$

一方、$$\langle \mathbf{u}, A\mathbf{v} \rangle = \langle A^*\mathbf{u}, \mathbf{v} \rangle$$（一般恒等式）と $A^* = A$、第1引数の共役線形性から、

$$\langle \mathbf{v}, A\mathbf{v} \rangle = \langle A^*\mathbf{v}, \mathbf{v} \rangle = \langle A\mathbf{v}, \mathbf{v} \rangle = \langle \lambda\mathbf{v}, \mathbf{v} \rangle = \bar{\lambda}\langle \mathbf{v}, \mathbf{v} \rangle = \bar{\lambda}\|\mathbf{v}\|^2$$

$\|\mathbf{v}\|^2 > 0$ だから $\lambda = \bar{\lambda}$、すなわち $\lambda \in \mathbb{R}$。$\square$

> **恒等式 $\langle \mathbf{u}, A\mathbf{v} \rangle = \langle A^*\mathbf{u}, \mathbf{v} \rangle$ の確認：** 
> 
> 内積 $\langle \mathbf{u}, \mathbf{v}\rangle = \mathbf{u}^*\mathbf{v}$ の下では $\langle A^*\mathbf{u}, \mathbf{v} \rangle = (A^*\mathbf{u})^*\mathbf{v} = \mathbf{u}^*(A^{**})\mathbf{v} = \mathbf{u}^*A\mathbf{v} = \langle \mathbf{u}, A\mathbf{v} \rangle$（$A^{**} = A$）。

### 定理3：エルミート行列の固有ベクトルの直交性

$A$ がエルミート行列で、$\lambda_1 \neq \lambda_2$ が異なる固有値、$\mathbf{v}_1, \mathbf{v}_2$ がそれぞれの固有ベクトルならば $\langle \mathbf{v}_1, \mathbf{v}_2 \rangle = 0$。

**証明.**

第2引数の線形性から：

$$\langle \mathbf{v}_1, A\mathbf{v}_2 \rangle = \langle \mathbf{v}_1, \lambda_2\mathbf{v}_2 \rangle = \lambda_2\langle \mathbf{v}_1, \mathbf{v}_2 \rangle$$

恒等式 $\langle \mathbf{u}, A\mathbf{v} \rangle = \langle A^*\mathbf{u}, \mathbf{v} \rangle$、$A^* = A$、第1引数の共役線形性から：

$$\langle \mathbf{v}_1, A\mathbf{v}_2 \rangle = \langle A^*\mathbf{v}_1, \mathbf{v}_2 \rangle = \langle A\mathbf{v}_1, \mathbf{v}_2 \rangle = \langle \lambda_1\mathbf{v}_1, \mathbf{v}_2 \rangle = \bar{\lambda}_1\langle \mathbf{v}_1, \mathbf{v}_2 \rangle$$

定理2より $\lambda_1 \in \mathbb{R}$ だから $\bar{\lambda}_1 = \lambda_1$。以上より

$$(\lambda_1 - \lambda_2)\langle \mathbf{v}_1, \mathbf{v}_2 \rangle = 0$$

$\lambda_1 \neq \lambda_2$ より $\langle \mathbf{v}_1, \mathbf{v}_2 \rangle = 0$。$\square$

### 定理4：スペクトル定理

$A \in \mathrm{M}_n(\mathbb{C})$ がエルミート行列ならば、$A$ はユニタリ行列によって対角化できる。すなわちユニタリ行列 $U$（$U^* = U^{-1}$）と実対角行列 $\Lambda$ が存在して

$$U^* A U = \Lambda$$

*証明の骨格.* 帰納法による（$n=1$ は自明）。

**存在：** 代数学の基本定理（$\mathbb{C}$ 上で特性多項式は必ず根を持つ）と定理2より、$A$ は実の固有値 $\lambda_1$ を持つ。対応する固有ベクトルを正規化して $\mathbf{e}_1$（$\|\mathbf{e}_1\|=1$）とする。

**帰納ステップ：** $\mathbf{e}_1$ を含む正規直交基底 $\\{\mathbf{e}_1, \mathbf{f}_2, \ldots, \mathbf{f}_n\\}$ をグラム＝シュミットで構成し、$U_1 = (\mathbf{e}_1 \mid \mathbf{f}_2 \mid \cdots \mid \mathbf{f}_n)$ とおく（$U_1$ はユニタリ）。$U_1^* A U_1$ を計算すると

$$U_1^* A U_1 = \begin{pmatrix} \lambda_1 & \mathbf{0}^* \\ \mathbf{0} & B \end{pmatrix}$$

上三角・下三角部分が消えることは $A$ のエルミート性から従う（$A\mathbf{e}_1 = \lambda_1\mathbf{e}_1$ かつ $\mathbf{f}_j \perp \mathbf{e}_1$より $$\langle \mathbf{e}_1, A\mathbf{f}_j\rangle = \langle A^*\mathbf{e}_1,\mathbf{f}_j\rangle = \lambda_1\langle\mathbf{e}_1,\mathbf{f}_j\rangle = 0$$右上も $A$ のエルミート性より同様）。$B$ もエルミート行列（$(U_1^* A U_1)^* = U_1^* A^* U_1 = U_1^* A U_1$ の右下ブロック）。帰納法の仮定を $B$ に適用して対角化し、再構成すれば $U^* A U = \Lambda$ を得る。$\square$

> **「スペクトル」という名称：** 行列の固有値の集合をスペクトルという（量子力学での演算子のスペクトルに由来）。

> **実対称行列との関係：** 実対称行列（$A^T = A$、$A \in \mathrm{M}_n(\mathbb{R})$）はエルミート行列の特別な場合。スペクトル定理を実数の文脈に制限すると、実対称行列は直交行列 $Q$（$Q^T = Q^{-1}$）で対角化できる（$Q^T A Q = \Lambda$）ということ。

**計算例（実対称行列）：**

$$A = \begin{pmatrix} 2 & 1 & 0 \\ 1 & 2 & 0 \\ 0 & 0 & 3 \end{pmatrix}$$

特性多項式：

$$p_A(\lambda) = \det\begin{pmatrix}2-\lambda&1&0\\1&2-\lambda&0\\0&0&3-\lambda\end{pmatrix} = (3-\lambda)\det\begin{pmatrix}2-\lambda&1\\1&2-\lambda\end{pmatrix}$$

$$= (3-\lambda)[(2-\lambda)^2 - 1] = (3-\lambda)(\lambda-1)(\lambda-3) = (\lambda-1)(\lambda-3)^2$$

固有値：$\lambda_1 = 1$（重複度1）、$\lambda_2 = 3$（重複度2）。

$\lambda = 1$：$(A-I)\mathbf{v} = \mathbf{0}$ を解くと $V_1 = \mathrm{span}\{ {}^t(1,-1,0)\}$。正規化：$\mathbf{q}_1 = \frac{1}{\sqrt{2}}{}^t(1,-1,0)$。

$\lambda = 3$：$(A-3I)\mathbf{v} = \mathbf{0}$ を解くと $V_3 = \mathrm{span}\{ {}^t(1,1,0),\, {}^t(0,0,1)\}$（2次元）。すでに直交しているので正規化のみ：$\mathbf{q}_2 = \frac{1}{\sqrt{2}}{}^t(1,1,0)$、$\mathbf{q}_3 = {}^t(0,0,1)$。

ユニタリ行列（この場合は実直交行列）と対角化


$$U = \begin{pmatrix} \frac{1}{\sqrt{2}} & \frac{1}{\sqrt{2}} & 0 \\ -\frac{1}{\sqrt{2}} & \frac{1}{\sqrt{2}} & 0 \\ 0 & 0 & 1 \end{pmatrix}, \qquad U^* A U = \begin{pmatrix} 1 & 0 & 0 \\ 0 & 3 & 0 \\ 0 & 0 & 3 \end{pmatrix}$$


---

## エルミート形式

### 定義：エルミート形式

エルミート行列 $A \in \mathrm{M}_n(\mathbb{C})$（$A^* = A$）に対し、写像 $q: \mathbb{C}^n \to \mathbb{R}$ を

$$q(\mathbf{x}) := \mathbf{x}^* A \mathbf{x} = \sum_{i,j} \bar{x}_i a_{ij} x_j$$

と定義し、$A$ による**エルミート形式**という。$A^* = A$ より、

$\overline{q(\mathbf{x})} = \overline{\mathbf{x}^* A \mathbf{x}} = \mathbf{x}^* A^* \mathbf{x} = \mathbf{x}^* A \mathbf{x} = q(\mathbf{x})$ となり、

$q(\mathbf{x}) \in \mathbb{R}$ が保証される。

> **実数の特別な場合：** $A \in \mathrm{M}_n(\mathbb{R})$、$\mathbf{x} \in \mathbb{R}^n$ では $\mathbf{x}^* = \mathbf{x}^T$ となり、エルミート形式は**二次形式**$q(\mathbf{x}) = \mathbf{x}^T A \mathbf{x}$ に一致する。

### 定理5：エルミート形式の標準化

スペクトル定理より 
$ A = U \Lambda U^* $
（$U$ ユニタリ、$\Lambda = \mathrm{diag}(\lambda_1,\ldots,\lambda_n)$、
$\lambda_i \in \mathbb{R}$）。
$$\mathbf{y} = U^*\mathbf{x}$$ と変数変換すると

$$q(\mathbf{x}) = \mathbf{x}^* A \mathbf{x} = \mathbf{y}^* \Lambda \mathbf{y} = \sum_{i=1}^n \lambda_i |y_i|^2$$

これをエルミート形式の**標準形**という。固有値の符号が形式の幾何的性質を決定する。

| 固有値の符号 | エルミート形式の性質 | $q(\mathbf{x}) = c$（$c>0$）の形状 |
|:------------|:-------------|:---------------------------------|
| すべて正 | 正定値（$q > 0$、$\mathbf{x}\neq\mathbf{0}$） | 楕円体 |
| すべて非負 | 半正定値 | 楕円柱・退化楕円体 |
| 正と負が混在 | 不定値 | 双曲面 |
| すべて負 | 負定値 | （楕円体・向き逆） |

**計算例：** $q(x,y) = 3x_1^2 + 2x_1 x_2 + 3x_2^2$（実数の二次形式）を標準化する。

$$A = \begin{pmatrix}3&1\\1&3\end{pmatrix}$$

これは前述の例と同じ行列。固有値 $\lambda_1 = 2$、$\lambda_2 = 4$。変数変換 $\mathbf{y} = U^*\mathbf{x}$（$U$ は固有ベクトルを列に並べたユニタリ行列）により

$$q = 2|y_1|^2 + 4|y_2|^2$$

すべての固有値が正だから正定値。$q = c$（$c > 0$）は $(y_1, y_2)$ 座標での楕円。

---

## 行列の定値性

### 定義：正定値・半正定値

エルミート行列 $A \in \mathrm{M}_n(\mathbb{C})$ が

- **正定値**：$\forall \mathbf{x} \neq \mathbf{0},\; \mathbf{x}^* A \mathbf{x} > 0$
- **半正定値**：$\forall \mathbf{x},\; \mathbf{x}^* A \mathbf{x} \geq 0$
- **負定値**（：$\forall \mathbf{x} \neq \mathbf{0},\; \mathbf{x}^* A \mathbf{x} < 0$
- **不定値**：正の値も負の値もとる

であるという。$A$ が正定値であることを $A \succ 0$、半正定値を $A \succeq 0$ と書くこともある。

### 定理6：定値性の固有値による特徴づけ

エルミート行列 $A$ に対して：

- $A$ が正定値 $\iff$ すべての固有値 $> 0$
- $A$ が半正定値 $\iff$ すべての固有値 $\geq 0$
- $A$ が負定値 $\iff$ すべての固有値 $< 0$
- $A$ が不定値 $\iff$ 正の固有値と負の固有値が両方存在する

**証明.** 

スペクトル定理より $A = U\Lambda U^*$（$U$ ユニタリ）。

$\mathbf{y} = U^* \mathbf{x}$ と置くと $\mathbf{x} \leftrightarrow \mathbf{y}$ は全単射（$U$ は正則）かつ $\mathbf{x} = \mathbf{0} \iff \mathbf{y} = \mathbf{0}$。よって、

$$\mathbf{x}^* A \mathbf{x} = \mathbf{y}^* \Lambda \mathbf{y} = \sum_{i=1}^n \lambda_i |y_i|^2$$

右辺がすべての $\mathbf{y} \neq \mathbf{0}$ で正 $\iff$ すべての $\lambda_i > 0$（$\mathbf{y} = \mathbf{e}_i$ を代入すれば必要性、一般の $\mathbf{y}$ で十分性）。他の場合も同様。$\square$

> **幾何的解釈：** 定理6は、2次形式（あるいはエルミート形式） $q(\mathbf{x}) = \mathbf{x}^* A \mathbf{x}$ を変数関数 $z = q(\mathbf{x})$ とみなしたときのグラフの形状分類である。

### 定理7：シルベスターの判定法

エルミート行列 $A$ の左上 $k \times k$ 小行列を $A_k$ とする（$k = 1, \ldots, n$）：

$$A_1 = (a_{11}), \quad A_2 = \begin{pmatrix}a_{11}&a_{12}\\a_{21}&a_{22}\end{pmatrix}, \quad \ldots, \quad A_n = A$$

このとき

$$A \text{ が正定値} \iff \det(A_k) > 0 \quad (k = 1, \ldots, n)$$

**証明.** $(\Rightarrow)$：$A$ が正定値ならば $A_k$ も正定値（$\mathbb{C}^k$ を $\mathbb{C}^n$ に零埋め込みして制限する）。正定値行列の固有値はすべて正だから、$\det(A_k) = \prod \lambda_i(A_k) > 0$。

$(\Leftarrow)$：$n$ に関する帰納法。$n=1$ は $a_{11} > 0$ から明らか。$n-1$ まで成立と仮定する。$\det(A_k) > 0$（$k < n$）の仮定より帰納法の仮定から $A_{n-1}$ は正定値。$A_{n-1}$ の固有値はすべて正なので、$A$ のコレスキー分解（後述）を用いて $A$ の正定値性が導かれる。$\square$

> **シルベスターの実用上の意義：** 固有値を求めるには特性多項式を解く必要があり、一般に $n \geq 5$ では代数的に解けない。シルベスターの判定法は**行列式（有限回の四則演算）だけで正定値性を判定できる**点が実用的。

**計算例：**

$$A = \begin{pmatrix}4&2&0\\2&3&1\\0&1&2\end{pmatrix}$$

$\det(A_1) = 4 > 0$、$\det(A_2) = 4\cdot3 - 2\cdot2 = 8 > 0$、$\det(A_3) = \det(A)$。

$$\det(A) = 4(3\cdot2 - 1\cdot1) - 2(2\cdot2 - 1\cdot0) + 0 = 4\cdot5 - 2\cdot4 = 12 > 0$$

すべての主小行列式が正なので $A$ は正定値。

### 命題3：コレスキー分解

$A$ が正定値エルミート行列 $\iff$ 下三角行列 $L$（対角成分はすべて正の実数）が存在して $A = LL^*$。

この分解を**コレスキー分解**という。

*証明の骨格.* 

$(\Leftarrow)$：
$\mathbf{x}^* A \mathbf{x} = \mathbf{x}^* LL^* \mathbf{x} = \|L^*\mathbf{x}\|^2 \geq 0$。
等号は $L^*\mathbf{x} = \mathbf{0}$、
$L$ は正則（対角成分 $> 0$）だから、 $\mathbf{x} = \mathbf{0}$ のみ。

$(\Rightarrow)$：
ガウス消去法により $A$ を上三角行列 $U$ に変形する。

この際の基本変形（第 $j$ 行の定数倍を第 $i$ 行から引く操作、$i > j$）を表す行列は単位下三角行列であり、その逆行列も単位下三角行列となる。

これらの積を $L_0$ とおけば、$A = L_0 U$（LU分解）が得られる。

$U$ の対角成分を抜き出して対角行列 $D$ とし、
$U = D U_0$（$U_0$ は対角成分が1の上三角行列）とすると、
$A = L_0 D U_0$ となる。
$A$ はエルミート行列（$A = A^*$）であるから、
$L_0 D U_0 = U_0^* D L_0^*$。

分解の一意性により
$U_0 = L_0^*$ とならざるを得ず、
$A = L_0 D L_0^*$ という対称な形に帰着する。

> **補足：LDU 分解の一意性**
>
> 正則行列の LDU 分解（単位下三角 $L$・対角 $D$・単位上三角 $U$ の積）はただ1通りに定まる。
>
> 2通りの分解 $A = L_1 D_1 U_1 = L_2 D_2 U_2$ があったとする（$A$ が正則なので $L, D, U$ はいずれも正則）。左から $L_2^{-1}$、右から $U_1^{-1}$ を掛けると
>
> $$L_2^{-1} L_1 D_1 = D_2 U_2 U_1^{-1}$$
>
> 左辺は、対角成分が1の下三角行列 $L_2^{-1}L_1$ に対角行列 $D_1$ を右から掛けたものなので**下三角行列**。
> 
> 右辺は対角行列 $D_2$ に対角成分が1の上三角行列 $U_2 U_1^{-1}$ を右から掛けたものなので**上三角行列**。
> 
> 「下三角 ＝ 上三角」が成り立つには両辺とも対角行列でなければならず、対角成分を比較すると $D_1 = D_2$。
>
> $D_1 = D_2 =: D$ が確定したら、元の等式 $L_2^{-1} L_1 D = D U_2 U_1^{-1}$ の両辺に右から $D^{-1}$ を掛けると
>
> $$L_2^{-1} L_1 = D U_2 U_1^{-1} D^{-1}$$
>
> 右辺をよく見ると、$D$ と $D^{-1}$ というふたつの対角行列で挟んでいる形だが、$U_2 U_1^{-1}$ は対角成分が1の上三角行列であり、対角行列との積（$D(\cdot)D^{-1}$）を施しても上三角行列のままである。一方、左辺 $L_2^{-1}L_1$ は対角成分が1の下三角行列。再び「下三角 ＝ 上三角」の状況に戻るため、両辺とも単位行列（対角成分が1の対角行列）でなければならない。
>
> したがって $L_2^{-1} L_1 = I$、すなわち $L_1 = L_2$。同様に元の等式から $U_1 = U_2$。$\square$

次に、$A$ が正定値である条件を使う。任意の $\mathbf{x} \neq \mathbf{0}$ に対し $\mathbf{x}^* A \mathbf{x} > 0$ である。$\mathbf{y} = L_0^* \mathbf{x}$ と変数変換すると

$$\mathbf{x}^* A \mathbf{x} = \mathbf{x}^* (L_0 D L_0^*) \mathbf{x} = (L_0^*\mathbf{x})^* D (L_0^*\mathbf{x}) = \mathbf{y}^* D \mathbf{y} = \sum_{k=1}^n d_k |y_k|^2 > 0$$

これが任意の $\mathbf{y} \neq \mathbf{0}$ で成り立つため、$D$ の対角成分 $d_k$ はすべて正の実数（$d_k > 0$）でなければならない。

すべての $d_k > 0$ が保証されたため、対角行列 $$\sqrt{D} = \mathrm{diag}(\sqrt{d_1}, \ldots, \sqrt{d_n})$$ を定義できる。$L := L_0 \sqrt{D}$ とおけば

$$A = L_0 \sqrt{D} \sqrt{D} L_0^* = L L^*$$

となり、対角成分がすべて正の実数である下三角行列 $L$ が構成できる。$\square$

**別証明：ピボット $d_k$ の主小行列式による表示**

$A = L_0 D U_0$ において、$D$ の第 $k$ 対角成分（ピボット）は主小行列式の比で表される。

$$d_k = \frac{\det(A_k)}{\det(A_{k-1})} \qquad (\det(A_0) := 1)$$

**証明.**

**1. ブロックへの制限。** $L_0$ は下三角、$U_0$ は上三角であるため、積 $L_0 D U_0$ の左上 $k \times k$ ブロックには $k$ より大きいインデックスの成分が混ざり込まない。したがって全体の等式は左上のブロックに制限してもそのまま成り立つ。

$$A_k = (L_0)_k \, D_k \, (U_0)_k$$

**2. 行列式をとる。** 両辺の行列式を計算する。$(L_0)_k$ は対角成分がすべて $1$ の下三角行列なので $\det((L_0)_k) = 1$。$(U_0)_k$ も同様に $\det((U_0)_k) = 1$。$D_k = \mathrm{diag}(d_1, \ldots, d_k)$ なので $\det(D_k) = d_1 d_2 \cdots d_k$。したがって、

$$\det(A_k) = 1 \cdot d_1 d_2 \cdots d_k \cdot 1 = d_1 d_2 \cdots d_k$$

**3. 比をとる。** $k-1$ の場合と比較して

$$d_k = \frac{d_1 \cdots d_{k-1} d_k}{d_1 \cdots d_{k-1}} = \frac{\det(A_k)}{\det(A_{k-1})} \qquad \square$$

$A$ が正定値ならすべての $\det(A_k) > 0$（シルベスターの判定法の $\Rightarrow$ 方向）、よって $d_k > 0$。逆にすべての $d_k > 0$ ならすべての $\det(A_k) = d_1 \cdots d_k > 0$（シルベスターの $\Leftarrow$ 方向）。この別証明は、なぜシルベスターの判定法が成立するかを説明する。

**計算例（シルベスターの例と同じ $A$）：**

$$A = \begin{pmatrix}4&2&0\\2&3&1\\0&1&2\end{pmatrix}$$

列ごとに対角成分 $l_{jj}$、その下の成分 $l_{ij}$（$i > j$）を順番に決める：

$$\text{列1：} \quad l_{11} = \sqrt{a_{11}} = \sqrt{4} = 2, \quad l_{21} = \frac{a_{21}}{l_{11}} = \frac{2}{2} = 1, \quad l_{31} = \frac{a_{31}}{l_{11}} = \frac{0}{2} = 0$$

$$\text{列2：} \quad l_{22} = \sqrt{a_{22} - l_{21}^2} = \sqrt{3 - 1} = \sqrt{2}, \quad l_{32} = \frac{a_{32} - l_{31}l_{21}}{l_{22}} = \frac{1 - 0}{\sqrt{2}} = \frac{1}{\sqrt{2}}$$

$$\text{列3：} \quad l_{33} = \sqrt{a_{33} - l_{31}^2 - l_{32}^2} = \sqrt{2 - 0 - \tfrac{1}{2}} = \sqrt{\tfrac{3}{2}} = \frac{\sqrt{6}}{2}$$

よって

$$L = \begin{pmatrix}2 & 0 & 0 \\ 1 & \sqrt{2} & 0 \\ 0 & \dfrac{1}{\sqrt{2}} & \dfrac{\sqrt{6}}{2}\end{pmatrix}, \qquad A = LL^T \quad \text{（確認：}LL^T\text{ を展開すると元の }A\text{ に一致）}$$

> **コレスキー分解の応用：** 数値計算では正定値エルミート行列の連立方程式 $A\mathbf{x} = \mathbf{b}$ をコレスキー分解で解くのが標準的。$LL^*\mathbf{x} = \mathbf{b}$ を前進代入・後退代入で解け、$LU$ 分解の約半分の計算量で済む。
