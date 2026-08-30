+++
title = "線形写像・行列・行列式"
weight = 20
date = 2026-08-26
+++

[ノート：加群・ベクトル空間](40_knowledge-base/10_mathematics/35_linear_algebra/10-modules-vectorspaces/)でベクトル空間と線形写像を定義し、シュタイニッツの交換補題・次元の well-defined 性・次元公式（rank-nullity 定理）を証明した。本ノートではその計算的な側面を展開する。有限次元ベクトル空間における線形写像は、基底を定めることで行列として表現でき、写像の合成は行列の積に対応する。この対応関係により、線形代数の計算手法は、抽象的な線形写像を具体的に扱うための手段として理解される。

*※ 未定義の用語（$\mathrm{span}$, 正則など）を前置きなく使っているが、もっぱら自分専用のアーカイブなのでこれでいいだろう。気が向いたら、ちゃんと整理する。*

---

{{< toc >}}

---

## 行列の定義と線形写像の対応

次元の well-defined 性と次元公式は、[ノート：加群・ベクトル空間](40_knowledge-base/10_mathematics/35_linear_algebra/10-modules-vectorspaces/)で証明されている。ここでは次元が確定していることを前提に、ベクトル空間の元を数の配列として一意に表現する枠組みを構築する。

### 座標ベクトル：ベクトルを数の配列で表す

$V$ を体 $F$ 上の $n$ 次元ベクトル空間、$\mathcal{B} = (v_1, \ldots, v_n)$ を $V$ の**順序付き基底**とする。基底の定義より、任意の $v \in V$ は

$$v = x_1 v_1 + x_2 v_2 + \cdots + x_n v_n, \qquad x_i \in F$$

と一意に表される。この $n$ 個のスカラー $(x_1, \ldots, x_n)$ を $v$ の $\mathcal{B}$ に関する**座標**といい、

$$[v]_\mathcal{B} := \begin{pmatrix} x_1 \\ \vdots \\ x_n \end{pmatrix} \in F^n$$

$\begin{pmatrix} x_1 \\ \vdots \\ x_n \end{pmatrix}$ を ${}^t(x_1, \ldots, x_n)$ とも書く。「${}^t$」は転置（行と列の入れ替え）を表す記号である。

を $v$ の**座標ベクトル**という。

写像 $\phi_\mathcal{B}: V \to F^n: v \mapsto [v]_\mathcal{B}$ は同型である：
- **線形性：** 展開の一意性から
    - $[u+v]_\mathcal{B} = [u]_\mathcal{B} + [v]_\mathcal{B}$
    - $[cv]_\mathcal{B} = c[v]_\mathcal{B}$
- **全単射：** 基底の線形独立性（単射）と生成性（全射）から従う。

> **基底の選び方に依存：** 全く同じベクトル $v$ でも、どの基底を選ぶかによってその座標は変わってくる。基底を一つ固定して初めて、ベクトルは具体的な数の配列として書き表せるようになり、抽象的な理論を実際の計算に落とし込めるようになる。そして、この座標との対応関係を利用して、線形写像を表現する道具が行列である（定理1）。

### 定義：行列

体 $F$ 上の **$m \times n$ 行列**とは、$F$ の元を $m$ 行 $n$ 列に並べた配列

$$A = \begin{pmatrix} a_{11} & a_{12} & \cdots & a_{1n} \\ a_{21} & a_{22} & \cdots & a_{2n} \\ \vdots & \vdots & \ddots & \vdots \\ a_{m1} & a_{m2} & \cdots & a_{mn} \end{pmatrix}$$

のことである。$(i,j)$ 成分 $a_{ij}$ を用いて $A = (a_{ij})$ と略記する。$m \times n$ 行列全体の集合を $\mathrm{M}_{m,n}(F)$ と書く。特に、$m = n$ のとき $\mathrm{M}_n(F)$ とも書く。

行列の和 $A + B := (a_{ij} + b_{ij})$ とスカラー倍 $cA := (ca_{ij})$ により、$\mathrm{M}_{m,n}(F)$ 自身も $F$ 上の次元 $mn$ のベクトル空間をなす。

> **集合論的には：** $m \times n$ 行列は写像 $\{1,\ldots,m\} \times \{1,\ldots,n\} \to F$、すなわち添字の順序対に成分を対応させる写像として定義できる。

### 行列による線形写像の定義

$A \in \mathrm{M}_{m,n}(F)$ に対し、写像 $L_A: F^n \to F^m$ を

$$L_A(\mathbf{x}) := A\mathbf{x} = \begin{pmatrix} \sum_{k=1}^n a_{1k} x_k \\ \vdots \\ \sum_{k=1}^n a_{mk} x_k \end{pmatrix}$$

と定義する（$\mathbf{x} = {}^t(x_1, \ldots, x_n) \in F^n$）。$L_A$ が線形写像であることは分配律と結合律から直接確認できる。

> **例：**
>
> $$A = \begin{pmatrix} 1 & 0 & -1 \\ 2 & 3 & 0 \end{pmatrix} \in \mathrm{M}_{2,3}(\mathbb{R})$$
>
> とすると $L_A: \mathbb{R}^3 \to \mathbb{R}^2$ は
>
> $$L_A\begin{pmatrix} x_1 \\ x_2 \\ x_3 \end{pmatrix} = \begin{pmatrix} x_1 - x_3 \\ 2x_1 + 3x_2 \end{pmatrix}$$
>
> $\ker L_A$ を求めるには $x_1 - x_3 = 0$、$2x_1 + 3x_2 = 0$ を解く。$x_3 = x_1$、$x_2 = -\frac{2}{3}x_1$ だから
>
> $$\ker L_A = \mathrm{span}\left\{ \begin{pmatrix} 1 \\ -\frac{2}{3} \\ 1 \end{pmatrix} \right\}$$
>
> 次元公式と一致：$\dim \ker = 1$、$\dim \mathrm{Im} = 2$、$3 = 1 + 2$。


### 定理1：線形写像の行列表示

$V$、$W$ を $F$ 上の有限次元ベクトル空間とし、$\dim V = n$、$\dim W = m$ とする。$V$ の基底 $\mathcal{B} = (v_1, \ldots, v_n)$、$W$ の基底 $\mathcal{C} = (w_1, \ldots, w_m)$ を固定する。このとき、線形写像 $\varphi: V \to W$ に対し、ある $A \in \mathrm{M}_{m,n}(F)$ が一意に存在して

$$[\varphi(v)]_\mathcal{C} = A [v]_\mathcal{B} \qquad (\forall v \in V)$$

を満たす。ここで $[v]_\mathcal{B}$は $v$ の $\mathcal{B}$ に関する座標ベクトル（$v = \sum x_i v_i$ なら $[v]_\mathcal{B} = {}^t(x_1, \ldots, x_n)$）。
この $A$ を $\varphi$ の $(\mathcal{B}, \mathcal{C})$ に関する**表現行列**といい、$[\varphi]_\mathcal{B}^\mathcal{C}$ と書く。

**証明.** 各 $j = 1, \ldots, n$ に対し $\varphi(v_j) \in W$ は $\mathcal{C}$ で一意に展開される。

$$\varphi(v_j) = \sum_{i=1}^m a_{ij} w_i$$

$A = (a_{ij})$ と定める。任意の $v = \sum_j x_j v_j \in V$ に対し、$\varphi$ の線形性より、

$$\varphi(v) = \sum_j x_j \varphi(v_j) = \sum_j x_j \sum_i a_{ij} w_i = \sum_i \left(\sum_j a_{ij} x_j\right) w_i$$

よって、$[\varphi(v)]_\mathcal{C}$ の第 $i$ 成分は  $\sum_j a_{ij} x_j$ 、すなわち $[\varphi(v)]_\mathcal{C} = A[v]_\mathcal{B}$。

一意性：$A' \neq A$ ならば $v = v_j$ を代入すると成分が異なるので矛盾。$\square$

> **対応のまとめ：**
> - 線形写像 $\varphi: V \to W$ ↔ 行列 $A \in \mathrm{M}_{m,n}(F)$（基底の選び方に依存）
> - $\varphi$ の第 $j$ 列 = $\varphi(v_j)$ を $\mathcal{C}$ で展開した座標

### 定理2：線形写像の合成と行列の積

合成写像 $\psi \circ \varphi$（$\varphi: V \to W$、$\psi: W \to U$）の座標変換を計算することで、行列の積が自然に導出される。

$B = [\psi]_\mathcal{C}^\mathcal{D} \in \mathrm{M}_{l,m}(F)$、$A = [\varphi]_\mathcal{B}^\mathcal{C} \in \mathrm{M}_{m,n}(F)$ に対し、積 $BA \in \mathrm{M}_{l,n}(F)$ を

$$(BA)_{ik} := \sum_{j=1}^m b_{ij} a_{jk}$$

と定義する。任意の $v \in V$ に対し、
$$[\psi(\varphi(v))]_\mathcal{D} = B(A[v]_\mathcal{B}) = (BA)[v]_\mathcal{B}$$が成り立つ。

**線形写像の合成は表現行列の積に等しい**（$[\psi \circ \varphi]_\mathcal{B}^\mathcal{D} = BA$）。

> **行列の積の意味：** なぜ行列の積は行と列の内積のような計算をするのか？ それは、線形写像を連続して適用した結果を書き下したらそうなるからである。

### 基底の変換と相似行列

基底を変えると座標ベクトルが変わり、表現行列も変わる。変換の規則を考える。

**基底変換行列（遷移行列）**

$V$ の2つの順序付き基底 $\mathcal{B} = (v_1, \ldots, v_n)$、$\mathcal{B}' = (v'_1, \ldots, v'_n)$ に対し、新基底（$\mathcal{B}'$）を旧基底（$\mathcal{B}$）で展開する。

$$v'_j = \sum_{i=1}^n p_{ij}\, v_i$$

係数を並べた行列 $$P = (p_{ij}) \in \mathrm{M}_n(F)$$
（第 $j$ 列 $= [v'_j]_\mathcal{B}$）を
 **$\mathcal{B}$ から $\mathcal{B}'$ への基底変換行列**
 （遷移行列）という。$\mathcal{B}'$ も基底であるから $P$ は正則である。

**座標の変換則**

任意の $v \in V$ を $\mathcal{B}'$ で $v = \sum_j y_j v'_j$ と書くと、$v'_j$ の展開を代入して

$$v = \sum_j y_j \sum_i p_{ij}\, v_i = \sum_i \!\left(\sum_j p_{ij} y_j\right) v_i$$

$\mathcal{B}$ での展開一意性から $[v]_\mathcal{B} = P [v]_{\mathcal{B}'}$、すなわち$[v]_{\mathcal{B}'} = P^{-1}[v]_\mathcal{B}$

> **基底が $P$ で変わると座標は $P^{-1}$ で変わる。** テンソル記法では、座標ベクトルのこの性質を**反変**と呼ぶ。

**表現行列の変換則（相似変換）**

$\varphi: V \to V$ を線形写像、$A = [\varphi]_\mathcal{B}^\mathcal{B}$ とする。$\mathcal{B}'$ に関する表現行列 $A' = [\varphi]_{\mathcal{B}'}^{\mathcal{B}'}$ を求めると、

$$[\varphi(v)]_{\mathcal{B}'} = P^{-1}[\varphi(v)]_\mathcal{B} = P^{-1}A[v]_\mathcal{B} = P^{-1}A\, P[v]_{\mathcal{B}'}$$

よって

$$A' = P^{-1}AP$$

**$P^{-1}AP$ の読み方（右から左へ）：**

$$A' = \underbrace{P^{-1}}_{\substack{\text{③ }\mathcal{B}'\text{ 座標へ戻す} \\ [\ \cdot\ ]_\mathcal{B} \mapsto [\ \cdot\ ]_{\mathcal{B}'}}} \underbrace{A}_{\substack{\text{② }\mathcal{B}\text{ 座標で} \\ \varphi\text{ を適用}}} \underbrace{P}_{\substack{\text{① }\mathcal{B}'\text{ 座標を} \\ \mathcal{B}\text{ 座標に変換}}}$$

$\mathcal{B}'$ 座標にいるベクトル $[v]_{\mathcal{B}'}$ を、
- ①: $P$ でいったん $\mathcal{B}$ 座標に戻し、
- ②: $A$ で線形写像を適用し、
- ③: $P^{-1}$ で $\mathcal{B}'$ 座標に変換すると、

$\mathcal{B}'$ 座標での像 $[\varphi(v)]_{\mathcal{B}'}$ が得られる。これが $A'$ である。

**定義：相似行列**

$A, A' \in \mathrm{M}_n(F)$ が**相似**であるとは、ある正則行列 $P$ が存在して $A' = P^{-1}AP$ となることをいう。相似は行列上の同値関係であり、同じ線形写像を異なる基底で表した行列はすべて相似である。

> **相似不変量：** $\det(A) = \det(A')$、$\mathrm{tr}(A) = \mathrm{tr}(A')$、固有多項式は相似変換で変わらない。これらは線形写像そのものの不変量である（固有値・固有ベクトルは以降で詳述）

---

## 行基本変形と階数（rank）

行列の計算技術である行基本変形を導入し、それを用いて行列の階数（rank）が well-defined であることを示す。

### 定義：行基本変形と基本行列

行列 $A \in \mathrm{M}_{m,n}(F)$ に対する以下の操作を**行基本変形**という。

- **(R1) 行の入れ替え：** 第 $i$ 行と第 $j$ 行を交換する。

- **(R2) スカラー倍：** 第 $i$ 行を $c \neq 0$ 倍する。

- **(R3) 行の加算：** 第 $i$ 行に第 $j$ 行の $c$ 倍を加える。

各行基本変形は、単位行列 $I_m$ に同じ変形を施した**基本行列** $E$ を左から掛ける操作に対応する。

| 変形 | 基本行列 $E$ | $\det E$ |
|:-----|:------------|:---------|
| (R1) 第 $i$・$j$ 行の交換 | $I_m$ の第 $i$・$j$ 行を入れ替えた行列 | $-1$ |
| (R2) 第 $i$ 行を $c$ 倍 | $I_m$ の $(i,i)$ 成分を $c$ にした行列 | $c$ |
| (R3) 第 $i$ 行に第 $j$ 行の $c$ 倍を加える | $I_m$ の $(i,j)$ 成分を $c$ にした行列 | $1$ |

>$\det E$の意味については後述

基本行列はすべて正則であるため、行基本変形は、行列が表す線形写像の核と像の次元を保存する。

**逆行列への応用：** $A$ が正則のとき、$A$ を $I$ に変換する行基本変形の列 $E_k \cdots E_1 A = I$ が存在し、$E_k \cdots E_1 = A^{-1}$。これは、$(A \mid I)$ を行変形して $(I \mid A^{-1})$ を得るという逆行列の計算法の根拠である。

### 定義：簡約行階段形

行基本変形によって、任意の行列は**行階段形**に変換できる。各行の先頭の非零成分（**ピボット**）を $1$ にし、ピボットのある列の他の成分をすべて $0$ にしたものを**簡約行階段形**という。

**定理（簡約行階段形の一意性）：** 任意の行列に対して、簡約行階段形は一意に定まる。

> 証明は省略する。簡約行階段形が一意であることは行列の階数の well-definedness に対応する。

### 階数（rank）の well-defined 性

線形代数における階数（rank）が well-defined であることは、以下の3つの観点から保証される。

**1. 線形写像の階数**

線形写像 $f: V \to W$ の階数は $\mathrm{rank}(f) := \dim(\mathrm{Im}(f))$ として定義される。$\mathrm{Im}(f)$ は部分空間であり、次元の well-defined 性より次元は基底によらず一意に定まる。

**2. 行列の階数（行階数と列階数の一致）**

$m \times n$ 行列 $A$ に対して、**列階数**（列ベクトルが張る空間の次元）と**行階数**（行ベクトルが張る空間の次元）の2通りが考えられるが、**任意の行列に対して列階数と行階数は一致する**。

*証明の概要：* 行列 $A$ に行基本変形を施して簡約行階段形に変換する。行基本変形は行空間を変えず、列ベクトル間の線形従属関係も保つ。簡約行階段形においては、ピボットの個数が非零行の数（行階数）かつ線形独立な列の最大数（列階数）に一致する。したがって変形前の $A$ でも両者は一致する。$\square$

**3. 基底変換に関する不変性**

線形写像の表現行列は基底を取り替えると $P^{-1}AQ$ に変わるが、正則行列を掛ける操作は部分空間の次元を変化させないため、$\mathrm{rank}(A) = \mathrm{rank}(P^{-1}AQ)$ が成り立つ。

### 定理3：連立一次方程式の解法（ガウス消去法）

$A \in \mathrm{M}_{m,n}(F)$、$\mathbf{b} \in F^m$ とする。連立一次方程式 $A\mathbf{x} = \mathbf{b}$ を解くには、拡大係数行列 $(A \mid \mathbf{b})$ を行基本変形によって行階段形に変換すればよい。

$r = \mathrm{rank}\, A$ とする：
- **解なし**（不能）：行階段形で $\mathbf{b}$ 側に矛盾行（$0 = c \neq 0$）が現れるとき。
- **一意解**：$r = n$（かつ解なしでないとき）。
- **無限に多くの解**：$r < n$（かつ解なしでないとき）。自由変数が $n - r$ 個現れる。

*証明の骨格.* 行基本変形は可逆だから $A\mathbf{x} = \mathbf{b}$ と変換後の方程式は同値。行階段形では後退代入により解を陽に求められる。解の構造は次元公式（A3 定理5）に帰着する：$\ker L_A \cong F^{n-r}$、$\mathrm{Im}\, L_A \cong F^r$。$\square$

**計算例（$F = \mathbb{R}$）：**

$$\begin{pmatrix} 1 & 2 & 3 \\ 2 & 5 & 4 \\ 1 & 3 & 1 \end{pmatrix} \begin{pmatrix} x \\ y \\ z \end{pmatrix} = \begin{pmatrix} 6 \\ 11 \\ 6 \end{pmatrix}$$

$$\left(\begin{array}{ccc|c} 1 & 2 & 3 & 6 \\ 2 & 5 & 4 & 11 \\ 1 & 3 & 1 & 6 \end{array}\right) \xrightarrow{R_2 - 2R_1,\; R_3 - R_1} \left(\begin{array}{ccc|c} 1 & 2 & 3 & 6 \\ 0 & 1 & -2 & -1 \\ 0 & 1 & -2 & 0 \end{array}\right) \xrightarrow{R_3 - R_2} \left(\begin{array}{ccc|c} 1 & 2 & 3 & 6 \\ 0 & 1 & -2 & -1 \\ 0 & 0 & 0 & 1 \end{array}\right)$$

第3行が $0 = 1$ の矛盾を与えるので**解なし**。

---

## 行列式

### 動機：面積・体積の符号付き測度

$\mathbb{R}^2$ では、二つのベクトル $\mathbf{a} = {}^t(a_1, a_2)$、$\mathbf{b} = {}^t(b_1, b_2)$ の張る平行四辺形の**符号付き面積**は $a_1 b_2 - a_2 b_1$ で与えられる。$\mathbb{R}^n$ でこの概念を代数的に一般化したものが行列式である。

> **注記：** 面積・体積のイメージは公理の動機付けであり、行列式の論理展開自体は、任意の体 $F$ 上で純粋に代数的に行われる。

### 定義：行列式（公理的定義）

$n$ 次正方行列 $A$ の列ベクトルを $\mathbf{a}_1, \ldots, \mathbf{a}_n \in F^n$ と書く。**行列式**（determinant） $\det: \mathrm{M}_n(F) \to F$ は次の三条件を満たす唯一の写像として定義される：

- **(D1) 多重線形性：** 各列について線形である。

$$\det(\ldots, \mathbf{a}_j + \mathbf{b}, \ldots) = \det(\ldots, \mathbf{a}_j, \ldots) + \det(\ldots, \mathbf{b}, \ldots), \qquad \det(\ldots, c\mathbf{a}_j, \ldots) = c\det(\ldots, \mathbf{a}_j, \ldots)$$

- **(D2) 交代性：** 二列を交換すると符号が反転する。

- **(D3) 正規化：** $\det(I_n) = 1$。

> **存在と一意性：** (D1)〜(D3) を満たす写像が存在し、かつ一意であることが示される。存在は置換を用いた陽な公式（置換展開）で確認できる。一意性は (D1)〜(D3) だけから従う。

> **交代性 (D2) の定義について:**  (D2) で交代性を「二列を交換すると符号が反転する」と定義したが、代数学において一般の体（または可換環）を扱う場合、「隣り合う二列（または任意の二列）が等しいとき $0$ になる」を交代性の定義とすることが多い。実数などでは、交換して符号反転で定義しても、 「$x = -x \Rightarrow 2x = 0 \Rightarrow x = 0$」 から、同じ列があるなら $0$ が言えるが、標数が 2 の体（$1 + 1 = 0$ となる体、暗号理論などで重要）では $x = -x$ が常に成り立ってしまうため、「符号反転の定義→同じ列があるなら $0$」が導けない。(D2) を「二列が等しいとき $0$ となる」と定義しても、多重線形性を用いて列を交換すると符号が反転することが導かれる。（$D(\mathbf{x} + \mathbf{y}, \mathbf{x} + \mathbf{y}) = 0$ の左辺を多重線形性を用いて展開すると言える。）

> **テンソル記法との対応：** レヴィ＝チヴィタ記号 $\epsilon_{i_1\cdots i_n}$ を使うと行列式は $$\det A = \epsilon_{i_1\cdots i_n} A^{i_1}{}_{1} \cdots A^{i_n}{}_{n}$$と書ける。置換展開との同値性・積公式・余因子行列の一貫した導出は[ノート：アインシュタイン記法による行列計算](#)を参照。

### 定理4：行列式の一意性と置換展開

公理 (D1)〜(D3) を満たす写像 $\det: \mathrm{M}_n(F) \to F$ はただ一つに定まり、その値は以下の陽な公式（置換展開）で与えられる。

$$\det A = \sum_{\sigma \in S_n} \mathrm{sgn}(\sigma) \prod_{j=1}^n a_{\sigma(j)j}$$

**証明.**

$D: \mathrm{M}_n(F) \to F$ を (D1)〜(D3) を満たす任意の写像とする。各列を標準基底で展開し多重線形性を適用すると

$$D(A) = \sum_{i_1=1}^n \cdots \sum_{i_n=1}^n a_{i_1 1} \cdots a_{i_n n} \, D(\mathbf{e}_{i_1}, \ldots, \mathbf{e}_{i_n})$$

交代性より添字に重複があれば $0$ になるため、残るのは置換 $\sigma \in S_n$（$i_j = \sigma(j)$）に対応する項のみ。さらに交代性より $D(\mathbf{e}_{\sigma(1)}, \ldots, \mathbf{e}_{\sigma(n)}) = \mathrm{sgn}(\sigma) D(I_n) = \mathrm{sgn}(\sigma)$。よって

$$D(A) = \sum_{\sigma \in S_n} \mathrm{sgn}(\sigma) \, a_{\sigma(1)1} \cdots a_{\sigma(n)n}$$

これは $D$ の値を行列の成分だけで一意に定まる。$\square$

**例：$2 \times 2$ の場合**

$$\det \begin{pmatrix} a & b \\ c & d \end{pmatrix} = ad - bc$$

**例：$3 \times 3$ の場合**（サラスの公式）

$$\det \begin{pmatrix} a_{11} & a_{12} & a_{13} \\ a_{21} & a_{22} & a_{23} \\ a_{31} & a_{32} & a_{33} \end{pmatrix} = a_{11}a_{22}a_{33} + a_{12}a_{23}a_{31} + a_{13}a_{21}a_{32} - a_{13}a_{22}a_{31} - a_{12}a_{21}a_{33} - a_{11}a_{23}a_{32}$$

### 命題：行列式の基本性質

(D1)〜(D3) から直ちに以下が従う。

- **二列が等しければ $\det A = 0$**
- **零列があれば $\det A = 0$**
- **行基本変形との対応：** (R1) → 符号反転、(R2) → $c$ 倍、(R3) → 不変
- **$A$ が正則 $\iff$ $\det A \neq 0$**

### 定理5：行列式の積公式

$$\det(AB) = \det(A)\det(B)$$

**証明.** $\det(A) \neq 0$ のとき $D(B) := \frac{\det(AB)}{\det(A)}$ が (D1)〜(D3) を満たすことを確認すると、一意性より $D(B) = \det(B)$。よって、$\det(AB) = \det(A)\det(B)$。$\square$

> **一意性の威力：** 行列成分のシグマ計算を使わず、公理を満たす関数は一つしかないという事実だけで証明を完了できる。

> **別証明（$\epsilon$ 記号）：** $\epsilon_{ijk}$ の縮約として $\det(AB)$ を展開し $A$ と $B$ の因子を分離するとより見通しの良い証明が得られる。

### 定理6：余因子展開

$$A = (a_{ij}) \in \mathrm{M}_n(F)$$に対し、
$(i,j)$ **余因子**を $C_{ij} := (-1)^{i+j} \det A_{ij}$（$A_{ij}$ は $A$ から第 $i$ 行・第 $j$ 列を除いた $(n-1)\times(n-1)$ 行列）と定義する。

**第 $i$ 行に関する余因子展開：**

$$\det A = \sum_{j=1}^n a_{ij} C_{ij}$$

**証明（第1列展開）.** 多重線形性で $\mathbf{a}_1 = \sum_i a_{i1} \mathbf{e}_i$ を展開し、
交代性で $\mathbf{e}_i$ を先頭に移動（$i-1$ 回の列交換）すると $(-1)^{i+1} \det A_{i1}$ が得られる。$\square$

**計算例：**

$$\det \begin{pmatrix} 2 & 1 & 0 \\ 3 & 4 & 1 \\ 0 & 2 & 5 \end{pmatrix} = 2(20-2) - 1(15-0) + 0 = 36 - 15 = 21$$

> **実用：** 零成分が多い行・列に沿って展開すると計算量が大幅に減る。

### 定理7：クラメルの公式

$A \in \mathrm{M}_n(F)$ が正則（$\det A \neq 0$）のとき、$A\mathbf{x} = \mathbf{b}$ の一意解は

$$x_j = \frac{\det A_j}{\det A} \qquad (j = 1, \ldots, n)$$

で与えられる。ここで $A_j$ は $A$ の第 $j$ 列を $\mathbf{b}$ で置き換えた行列。

**証明.** 余因子行列 $\mathrm{adj}(A)$ を用いて $A \cdot \mathrm{adj}(A) = \det(A) \cdot I_n$ が示され、$A^{-1} = \frac{1}{\det A}\mathrm{adj}(A)$。$\mathbf{x} = A^{-1}\mathbf{b}$ の第 $j$ 成分を余因子展開で整理すると $x_j = \frac{\det A_j}{\det A}$。$\square$

> **クラメルの公式は実用的でない：** 計算量は $O(n \cdot n!)$（ガウス消去法は $O(n^3)$）。価値は計算法ではなく、解の各成分が $\mathbf{b}$ の線形関数として明示的に表されるという理論的側面にある。

> **テンソル記法による余因子行列と逆行列の明示的表現：** $\epsilon$ 記号を使うと余因子行列を $$\tilde{A}^{j_1}{}_{i_1} = \frac{1}{(n-1)!}\,\epsilon_{i_1 i_2 \cdots i_n} \epsilon^{j_1 j_2 \cdots j_n} A^{i_2}{}_{j_2} \cdots A^{i_n}{}_{j_n}$$ と陽に書ける。$$\tilde{A}A = (\det A)I$$
