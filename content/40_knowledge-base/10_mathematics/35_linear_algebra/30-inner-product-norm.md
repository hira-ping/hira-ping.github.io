+++
title = "内積・ノルム・直交化"
weight = 30
date = 2026-08-27
+++

足し算とスカラー倍に加え、内積をベクトル空間に追加し、長さも角度といった幾何学的な構造を導入する。係数体を $\mathbb{K} \in \{\mathbb{R}, \mathbb{C}\}$ に一般化して最初から複素内積空間として定義することで、実内積空間は特別な場合として自然に含まれる。

---

{{< toc >}}

---

## 内積

### 定義：内積空間

$\mathbb{K} \in \{\mathbb{R}, \mathbb{C}\}$ 上のベクトル空間 $V$ 上の**内積**とは、写像 $\langle \cdot, \cdot \rangle: V \times V \to \mathbb{K}$ であって以下を満たすものをいう。

**(I1) 第2引数に関する $\mathbb{K}$-線形性:** $\langle \mathbf{u},\, a\mathbf{v} + b\mathbf{w} \rangle = a\langle \mathbf{u}, \mathbf{v} \rangle + b\langle \mathbf{u}, \mathbf{w} \rangle$

**(I2) エルミート対称性：** $\langle \mathbf{u}, \mathbf{v} \rangle = \overline{\langle \mathbf{v}, \mathbf{u} \rangle}$

**(I3) 正定値性：** $\langle \mathbf{v}, \mathbf{v} \rangle \geq 0, \qquad \langle \mathbf{v}, \mathbf{v} \rangle = 0 \iff \mathbf{v} = \mathbf{0}$

> **実数体の場合：** $\mathbb{K} = \mathbb{R}$ では複素共役が恒等写像なので、(I2) は通常の対称性 $\langle\mathbf{u},\mathbf{v}\rangle = \langle\mathbf{v},\mathbf{u}\rangle$ に一致し、(I1) と合わせて双線形となる。

> **(I2) から $\langle\mathbf{v},\mathbf{v}\rangle \in \mathbb{R}$：** $\langle\mathbf{v},\mathbf{v}\rangle = \overline{\langle\mathbf{v},\mathbf{v}\rangle}$ より自身の複素共役に等しいから実数となる。よって、次項の正定値性 (I3) の不等式 $\langle\mathbf{v},\mathbf{v}\rangle \geq 0$ は $\mathbb{K} = \mathbb{C}$ でも意味をなす。

内積を備えたベクトル空間 $(V, \langle\cdot,\cdot\rangle)$ を
**計量ベクトル空間（または内積空間）**
という。

> **(I1) と (I2) から第1引数の共役線形性が従う**
>
> $$\begin{aligned} \langle a\mathbf{u} + b\mathbf{v},\, \mathbf{w} \rangle &= \overline{\langle \mathbf{w},\, a\mathbf{u} + b\mathbf{v} \rangle} \\ &= \overline{a\langle \mathbf{w}, \mathbf{u} \rangle + b\langle \mathbf{w}, \mathbf{v} \rangle} \\ &= \bar{a}\overline{\langle \mathbf{w}, \mathbf{u} \rangle} + \bar{b}\overline{\langle \mathbf{w}, \mathbf{v} \rangle} \\ &= \bar{a}\langle \mathbf{u}, \mathbf{w} \rangle + \bar{b}\langle \mathbf{v}, \mathbf{w} \rangle \end{aligned}$$
>
> すなわち内積は**半双線形**（第2引数に線形、第1引数に共役線形）である。


>**ディラック記法（物理学の流儀）との対応**
> 
> 量子力学では内積をブラ・ケット記法 $\langle u | v \rangle$ と書く。ケット $|v\rangle$（状態ベクトル）が線形に、ブラ $\langle u|$（ケット $|u\rangle$ の共役双対）が共役線形に作用する。本ノートの $\langle \mathbf{u}, \mathbf{v} \rangle$ は、第1引数 $\mathbf{u}$ がブラ $\langle u|$、第2引数 $\mathbf{v}$ がケット $|v\rangle$ に対応する。操作を受ける主役（状態ベクトル）を第2引数に置き、そちらの線形性を素直に保つこの流儀が、物理学やテンソル代数における標準的な設計である。

> **純粋数学流儀との比較：第2引数に共役をとる**
>
> 数学（特に関数解析）の教科書では、内積を(I1) を**第1引数に関する線形性**とし、第2引数を共役線形とする流儀もある。二つの流儀の間には単なる引数の入れ替え $\langle\mathbf{u},\mathbf{v}\rangle_{\mathrm{phys}} = \langle\mathbf{v},\mathbf{u}\rangle_{\mathrm{math}}$ という対応があるに過ぎない。本ノートでは、行列計算やテンソル表記との親和性が高い物理流儀（第2引数線形）で統一する。

### 内積の例

**標準内積（$\mathbb{C}^n$）：** $\mathbf{u} = {}^t(u_1,\ldots,u_n)$、$\mathbf{v} = {}^t(v_1,\ldots,v_n)$ に対し

$$\langle \mathbf{u}, \mathbf{v} \rangle := \sum_{i=1}^n \overline{u_i} v_i = \mathbf{u}^* \mathbf{v}$$

ただし $\mathbf{u}^* := \bar{\mathbf{u}}^T$ は**共役転置**。

- **(I1)**：$\langle \mathbf{u}, c\mathbf{v}\rangle = \mathbf{u}^* (c\mathbf{v}) = c(\mathbf{u}^* \mathbf{v}) = c\langle\mathbf{u},\mathbf{v}\rangle$ ✓
- **(I2)**：$\overline{\langle\mathbf{v},\mathbf{u}\rangle} = \overline{\mathbf{v}^* \mathbf{u}} = (\mathbf{v}^* \mathbf{u})^* = \mathbf{u}^* \mathbf{v} = \langle\mathbf{u},\mathbf{v}\rangle$ ✓
- **(I3)**：$\langle\mathbf{v},\mathbf{v}\rangle = \mathbf{v}^*\mathbf{v} = \sum_i|v_i|^2 \geq 0$ かつ、等号成立 $\iff \mathbf{v} = \mathbf{0}$ ✓

$\mathbb{K} = \mathbb{R}$ の場合、共役が恒等なので $\langle\mathbf{u},\mathbf{v}\rangle = \mathbf{u}^T\mathbf{v} = \sum_i u_iv_i$ となり、$\mathbb{R}^n$ の標準内積に一致する。

**重み付き内積（$\mathbb{R}^n$）：** 正の実数 $w_1, \ldots, w_n > 0$ を固定し

$$\langle \mathbf{u}, \mathbf{v} \rangle_w := \sum_{i=1}^n w_i u_i v_i$$

統計や最小二乗法で自然に現れる。

**多項式空間上の内積（$\mathbb{R}[x]_{\leq n}$）：** 
$$V = \mathbb{R}[x]_{\leq n}$$（次数 $\leq n$ の多項式）に対し

$$\langle f, g \rangle := \int_0^1 f(x)g(x)\,dx$$

これは (I1)〜(I3) を満たす（正定値性は $\int_0^1 f^2 \geq 0$ と $f \not\equiv 0$ なら $\int_0^1 f^2 > 0$ より）。

> **計量テンソルとしての内積**
>
> 内積の公理 (I1)〜(I3) は抽象的だが、基底を一つ固定するだけで内積の全情報が行列として具体化する。
>
> **半双線形性から行列が得られる**
> 基底 $\mathcal{B} = \{\mathbf{e}_1, \ldots, \mathbf{e}_n\}$ を固定し、$\mathbf{u} = \sum_i u^i \mathbf{e}_i$、$\mathbf{v} = \sum_j v^j \mathbf{e}_j$ と展開する。半双線形性（第1引数に共役線形、第2引数に線形）より
> $$\langle \mathbf{u}, \mathbf{v} \rangle = \sum_{i,j} \overline{u^i} v^j \langle \mathbf{e}_i, \mathbf{e}_j \rangle$$
> そこで**計量テンソル**の成分を
> $$g_{ij} := \langle \mathbf{e}_i, \mathbf{e}_j \rangle$$
> と定義する。内積は $g_{ij}$ だけで記述される：
> $$\langle \mathbf{u}, \mathbf{v} \rangle = \sum_{i,j} \overline{u^i} g_{ij}\, v^j = \mathbf{u}^* G \mathbf{v}$$
> ただし $G = (g_{ij})$ は $n \times n$ の**グラム行列**である。
>
> **内積の公理 ↔ 計量テンソルの性質：**
>
> | 内積の公理 | 計量テンソルの性質 |
> | :--- | :--- |
> | (I1) 第2引数に線形（第1引数に共役線形） | $g_{ij}$ が定義される（$(0,2)$ 型テンソルとしての構造） |
> | (I2) エルミート対称性 $\langle \mathbf{u}, \mathbf{v} \rangle = \overline{\langle \mathbf{v}, \mathbf{u} \rangle}$ | $g_{ij} = \overline{g_{ji}}$（$G$ はエルミート行列 $G = G^*$） |
> | (I3) 正定値性 $\langle \mathbf{v}, \mathbf{v} \rangle > 0$（$\mathbf{v} \neq \mathbf{0}$） | $G$ は正定値エルミート行列 （全固有値 $> 0$，固有値は実数） |
>
> 内積とは正定値エルミートグラム行列 $G$ を係数に持つ半双線形形式のことである。$\mathbb{K} = \mathbb{R}$ では $G$ がエルミート行列 $=$ 実対称行列に帰着する。
>
> **標準内積：** $\mathbb{C}^n$ の標準基底のもとでは
> $$g_{ij} = \langle \mathbf{e}_i, \mathbf{e}_j \rangle = \delta_{ij} \quad \Longrightarrow \quad G = I_n$$
> 標準内積は $G = I_n$ という特殊ケースである。正規直交基底とは $g_{ij} = \delta_{ij}$ が成立する基底のことであり、グラム＝シュミット直交化は、任意の基底を $G \to I_n$ にする基底変換を見つける手続きである。
>
> **座標変換との対応：** [ノート：線形写像・行列・行列式](40_knowledge-base/10_mathematics/35_linear_algebra/20-linear-maps/)で見たように、基底を $P$ で変換すると座標は $P^{-1}$ で変換される。一方 $g_{ij}$ は基底ベクトルの内積なので $G \mapsto P^* G P$ と変換される（$\mathbb{R}$ の場合は $P^T G P$）。

---

## ノルム

### 定義：ノルム

内積空間 $(V, \langle\cdot,\cdot\rangle)$ において、各 $\mathbf{v} \in V$ の**ノルム**を

$$\|\mathbf{v}\| := \sqrt{\langle \mathbf{v}, \mathbf{v} \rangle}$$

と定義する。(I2) より $\langle\mathbf{v},\mathbf{v}\rangle \in \mathbb{R}_{\geq 0}$ だから平方根は定義される。$\|\mathbf{v}\|$ は $\mathbf{v}$ の長さに対応する。

**基本性質：**

- $\|\mathbf{v}\| \geq 0$、等号は $\mathbf{v} = \mathbf{0}$ のとき（正定値性 (I3) より）
- $\|c\mathbf{v}\| = |c|\|\mathbf{v}\|$
（半双線形性より：
$\langle c\mathbf{v}, c\mathbf{v}\rangle = \bar{c}\langle\mathbf{v}, c\mathbf{v}\rangle = \bar{c}\cdot c\langle\mathbf{v},\mathbf{v}\rangle = |c|^2\|\mathbf{v}\|^2$ ——第1引数の共役線形性、次いで第2引数の線形性を使う）

**$\mathbb{C}^n$ での例：** 標準内積のノルムは

$$\|\mathbf{v}\| = \sqrt{\sum_{i=1}^n |v_i|^2}$$

これは $\mathbb{R}^n$ ではピタゴラスの定理による通常の長さに、$\mathbb{C}^n$ では各成分の複素絶対値の二乗和の平方根に一致する。

### 定理1：コーシー＝シュワルツの不等式

任意の $\mathbf{u}, \mathbf{v} \in V$ に対して

$$|\langle \mathbf{u}, \mathbf{v} \rangle| \leq \|\mathbf{u}\|\,\|\mathbf{v}\|$$

等号成立は $\mathbf{u}$ と $\mathbf{v}$ が線形従属（一方が他方のスカラー倍）のとき。

**証明.** 

$\mathbf{v} = \mathbf{0}$ のとき両辺 $0$ で成立。$\mathbf{v} \neq \mathbf{0}$ とする。任意の $t \in \mathbb{K}$ に対し

$$0 \leq \|\mathbf{u} - t\mathbf{v}\|^2 = \langle \mathbf{u} - t\mathbf{v},\, \mathbf{u} - t\mathbf{v} \rangle$$

半双線形性を展開すると（$\alpha := \langle\mathbf{u},\mathbf{v}\rangle$ とおく）

$$\langle \mathbf{u} - t\mathbf{v},\, \mathbf{u} - t\mathbf{v} \rangle = \|\mathbf{u}\|^2 - t\langle\mathbf{u},\mathbf{v}\rangle - \bar{t}\langle\mathbf{v},\mathbf{u}\rangle + |t|^2\|\mathbf{v}\|^2 = \|\mathbf{u}\|^2 - t\alpha - \bar{t}\bar{\alpha} + |t|^2\|\mathbf{v}\|^2$$

（第1引数の共役線形性：$\langle -t\mathbf{v},\mathbf{w}\rangle = -\bar{t}\langle\mathbf{v},\mathbf{w}\rangle$；第2引数の線形性：$\langle\mathbf{u},-t\mathbf{v}\rangle = -t\langle\mathbf{u},\mathbf{v}\rangle$）

$$t = \dfrac{\bar{\alpha}}{\|\mathbf{v}\|^2}$$ を代入する
（$\bar{t} = \alpha/\|\mathbf{v}\|^2$、
$t\alpha = \bar{t}\bar{\alpha} = |\alpha|^2/\|\mathbf{v}\|^2$）。

$$0 \leq \|\mathbf{u}\|^2 - \frac{|\alpha|^2}{\|\mathbf{v}\|^2} - \frac{|\alpha|^2}{\|\mathbf{v}\|^2} + \frac{|\alpha|^2}{\|\mathbf{v}\|^4}\|\mathbf{v}\|^2 = \|\mathbf{u}\|^2 - \frac{|\alpha|^2}{\|\mathbf{v}\|^2}$$

整理して
$|\langle \mathbf{u}, \mathbf{v} \rangle|^2 \leq \|\mathbf{u}\|^2\|\mathbf{v}\|^2$
、平方根をとって結論を得る。

等号成立は $\|\mathbf{u} - t\mathbf{v}\|^2 = 0$、すなわち $\mathbf{u} = t\mathbf{v}$ のとき。$\square$

> **$t$ の幾何学的意味：** 代入した $t = \bar{\alpha}/\|\mathbf{v}\|^2 = \langle\mathbf{v},\mathbf{u}\rangle/\|\mathbf{v}\|^2$ は $\mathbf{u}$ を $\mathbf{v}$ の方向へ正射影したときの係数である。この不等式の意味は、$\mathbf{u}$ から正射影を引いた残りのベクトルの長さの2乗が $0$ 以上であるという幾何学的な事実である。

### 定理2：三角不等式

$$\|\mathbf{u} + \mathbf{v}\| \leq \|\mathbf{u}\| + \|\mathbf{v}\|$$

**証明.**

$$\|\mathbf{u} + \mathbf{v}\|^2 = \|\mathbf{u}\|^2 + \langle\mathbf{u},\mathbf{v}\rangle + \langle\mathbf{v},\mathbf{u}\rangle + \|\mathbf{v}\|^2 = \|\mathbf{u}\|^2 + 2\,\mathrm{Re}\langle \mathbf{u}, \mathbf{v} \rangle + \|\mathbf{v}\|^2$$

$\mathrm{Re}\langle\mathbf{u},\mathbf{v}\rangle \leq |\langle\mathbf{u},\mathbf{v}\rangle|$
だから、コーシー＝シュワルツの不等式より

$$\|\mathbf{u} + \mathbf{v}\|^2 \leq \|\mathbf{u}\|^2 + 2|\langle \mathbf{u}, \mathbf{v} \rangle| + \|\mathbf{v}\|^2 \leq \|\mathbf{u}\|^2 + 2\|\mathbf{u}\|\|\mathbf{v}\| + \|\mathbf{v}\|^2 = (\|\mathbf{u}\| + \|\mathbf{v}\|)^2$$

平方根をとって結論を得る。$\square$

> **距離空間への接続：** $d(\mathbf{u}, \mathbf{v}) := \|\mathbf{u} - \mathbf{v}\|$ と定義すると、三角不等式より $(V, d)$ は距離空間をなす。内積空間は自然に距離空間の構造を持つ。

---

## 直交性

### 定義：直交・正規直交

$\mathbf{u}, \mathbf{v} \in V$ が $\langle \mathbf{u}, \mathbf{v} \rangle = 0$ を満たすとき、$\mathbf{u}$ と $\mathbf{v}$ は**直交する**といい $\mathbf{u} \perp \mathbf{v}$ と書く。

ベクトルの集合 $\{\mathbf{v}_1, \ldots, \mathbf{v}_k\}$ が

- **直交系**：$i \neq j \Rightarrow \langle \mathbf{v}_i, \mathbf{v}_j \rangle = 0$
- **正規直交系**：直交系かつ $\|\mathbf{v}_i\| = 1$（$\forall i$）

であるという。正規直交系が $V$ の基底をなすとき**正規直交基底**という。

**命題1：$\mathbf{0}$ を含まない直交系は線形独立。**

**証明.** $\sum_i c_i \mathbf{v}_i = \mathbf{0}$ とする。$\mathbf{v}_j$ を第1引数に置いて内積をとると

$$0 = \left\langle \mathbf{v}_j,\, \sum_i c_i \mathbf{v}_i \right\rangle = \sum_i c_i \langle \mathbf{v}_j, \mathbf{v}_i \rangle = c_j \|\mathbf{v}_j\|^2$$

（第2引数の線形性を用いて $c_i$ を外に出した。）$\mathbf{v}_j \neq \mathbf{0}$ より $\|\mathbf{v}_j\| \neq 0$ だから $c_j = 0$。$j$ は任意だから線形独立。$\square$

### 正規直交基底の便利さ

正規直交基底 $\{\mathbf{e}_1, \ldots, \mathbf{e}_n\}$ のもとでは、任意の $\mathbf{v} \in V$ の座標が内積で直接求まる：

$$\mathbf{v} = \sum_{i=1}^n \langle \mathbf{e}_i, \mathbf{v} \rangle\, \mathbf{e}_i$$

**証明.** $\mathbf{v} = \sum_i c_i \mathbf{e}_i$ と展開する。$\mathbf{e}_j$ を第1引数に置いて内積をとると

$$\langle \mathbf{e}_j, \mathbf{v} \rangle = \sum_i c_i \langle \mathbf{e}_j, \mathbf{e}_i \rangle = c_j \|\mathbf{e}_j\|^2 = c_j$$

(I1) の線形性を第2引数に使い（$c_i$ を外に出す）。
ここで、
$\langle\mathbf{e}_j,\mathbf{e}_i\rangle = \delta_{ji}$
を用いた。$\square$

一般の基底では連立方程式を解く必要があるが、正規直交基底では各係数が内積一回で得られる。

**$\mathbb{C}^n$ での例：** 標準基底 $\mathbf{e}_1 = {}^t(1,0,\ldots,0), \ldots, \mathbf{e}_n = {}^t(0,\ldots,0,1)$ は標準内積のもとで正規直交基底。$\langle \mathbf{e}_i, \mathbf{v} \rangle = \mathbf{e}_i^*\mathbf{v} = v_i$ は $\mathbf{v}$ の第 $i$ 成分そのもの。

---

## グラム＝シュミット直交化

### 定理3：グラム＝シュミットの直交化法

$V$ を内積空間、$\{\mathbf{a}_1, \ldots, \mathbf{a}_n\}$ を $V$ の線形独立なベクトルの集合とする。このとき、同じ部分空間を張る正規直交系 $\{\mathbf{e}_1, \ldots, \mathbf{e}_n\}$ が構成できる。

**構成：**

$$\mathbf{u}_1 := \mathbf{a}_1, \qquad \mathbf{e}_1 := \frac{\mathbf{u}_1}{\|\mathbf{u}_1\|}$$

$k = 2, \ldots, n$ に対して再帰的に：

$$\mathbf{u}_k := \mathbf{a}_k - \sum_{j=1}^{k-1} \langle \mathbf{e}_j, \mathbf{a}_k \rangle\, \mathbf{e}_j, \qquad \mathbf{e}_k := \frac{\mathbf{u}_k}{\|\mathbf{u}_k\|}$$

**証明.**

帰納法で示す。各ステップで
$$\mathbf{u}_k \neq \mathbf{0}$$
であることをまず確認する。

$$\mathbf{u}_k = \mathbf{0}$$ とすると
$$\mathbf{a}_k = \sum_{j<k} \langle \mathbf{e}_j, \mathbf{a}_k \rangle \mathbf{e}_j \in \mathrm{span}\{\mathbf{e}_1,\ldots,\mathbf{e}_{k-1}\} = \mathrm{span}\{\mathbf{a}_1,\ldots,\mathbf{a}_{k-1}\}$$
となり、線形独立性に矛盾。

直交性：$l < k$ のとき、$\mathbf{e}_l$ を第1引数に置いて計算する

$$\langle \mathbf{e}_l, \mathbf{u}_k \rangle = \langle \mathbf{e}_l, \mathbf{a}_k \rangle - \sum_{j=1}^{k-1}\langle \mathbf{e}_j, \mathbf{a}_k \rangle \langle \mathbf{e}_l, \mathbf{e}_j \rangle = \langle \mathbf{e}_l, \mathbf{a}_k \rangle - \langle \mathbf{e}_l, \mathbf{a}_k \rangle \cdot 1 = 0$$

（第2引数の線形性で $\langle\mathbf{e}_j,\mathbf{a}_k\rangle$ を外に出し、$\langle \mathbf{e}_l, \mathbf{e}_j \rangle = \delta_{lj}$$を使用）。$$\mathbf{e}_k = \mathbf{u}_k / \|\mathbf{u}_k\|$ も $\mathbf{e}_l$ と直交し、$\|\mathbf{e}_k\| = 1$。

生成：構成より $$\mathrm{span}\{\mathbf{e}_1,\ldots,\mathbf{e}_k\} = \mathrm{span}\{\mathbf{a}_1,\ldots,\mathbf{a}_k\}$$
（各 $\mathbf{e}_k$ は $\mathbf{a}_1,\ldots,\mathbf{a}_k$ の線形結合、逆も同様）。$\square$

> **$\mathbf{u}_k$ の幾何的意味：**
>
>$\sum_{j<k}\langle \mathbf{e}_j, \mathbf{a}_k \rangle \mathbf{e}_j$ は、
>$\mathbf{a}_k$ の $\mathrm{span}\{\mathbf{e}_1,\ldots,\mathbf{e}_{k-1}\}$ への**正射影**である。
>$\mathbf{u}_k$ はそれを引いた残り——$\mathbf{a}_k$
>からすでに正規直交化した部分空間への成分を除いた、純粋に新しい方向の部分。

**計算例（$\mathbb{R}^3$）：** $\mathbf{a}_1 = {}^t(1,1,0)$、$\mathbf{a}_2 = {}^t(1,0,1)$、$\mathbf{a}_3 = {}^t(0,1,1)$ を直交化する。

**ステップ1：**

$$\mathbf{u}_1 = \begin{pmatrix}1\\1\\0\end{pmatrix}, \qquad \|\mathbf{u}_1\| = \sqrt{2}, \qquad \mathbf{e}_1 = \frac{1}{\sqrt{2}}\begin{pmatrix}1\\1\\0\end{pmatrix}$$

**ステップ2：**

$$\langle \mathbf{e}_1, \mathbf{a}_2 \rangle = \frac{1}{\sqrt{2}}(1\cdot1 + 1\cdot0 + 0\cdot1) = \frac{1}{\sqrt{2}}$$

$$\mathbf{u}_2 = \begin{pmatrix}1\\0\\1\end{pmatrix} - \frac{1}{\sqrt{2}} \cdot \frac{1}{\sqrt{2}}\begin{pmatrix}1\\1\\0\end{pmatrix} = \begin{pmatrix}1\\0\\1\end{pmatrix} - \begin{pmatrix}1/2\\1/2\\0\end{pmatrix} = \begin{pmatrix}1/2\\-1/2\\1\end{pmatrix}$$

$$\|\mathbf{u}_2\| = \sqrt{1/4+1/4+1} = \sqrt{3/2}, \qquad \mathbf{e}_2 = \sqrt{\frac{2}{3}}\begin{pmatrix}1/2\\-1/2\\1\end{pmatrix} = \frac{1}{\sqrt{6}}\begin{pmatrix}1\\-1\\2\end{pmatrix}$$

**ステップ3：**

$$\langle \mathbf{e}_1, \mathbf{a}_3 \rangle = \frac{1}{\sqrt{2}}(1\cdot0 + 1\cdot1 + 0\cdot1) = \frac{1}{\sqrt{2}}, \qquad \langle \mathbf{e}_2, \mathbf{a}_3 \rangle = \frac{1}{\sqrt{6}}(1\cdot0 + (-1)\cdot1 + 2\cdot1) = \frac{1}{\sqrt{6}}$$

$$\mathbf{u}_3 = \begin{pmatrix}0\\1\\1\end{pmatrix} - \frac{1}{\sqrt{2}}\cdot\frac{1}{\sqrt{2}}\begin{pmatrix}1\\1\\0\end{pmatrix} - \frac{1}{\sqrt{6}}\cdot\frac{1}{\sqrt{6}}\begin{pmatrix}1\\-1\\2\end{pmatrix} = \begin{pmatrix}0\\1\\1\end{pmatrix} - \begin{pmatrix}1/2\\1/2\\0\end{pmatrix} - \begin{pmatrix}1/6\\-1/6\\1/3\end{pmatrix} = \begin{pmatrix}-2/3\\2/3\\2/3\end{pmatrix}$$

$$\|\mathbf{u}_3\| = \frac{2\sqrt{3}}{3}, \qquad \mathbf{e}_3 = \frac{1}{\sqrt{3}}\begin{pmatrix}-1\\1\\1\end{pmatrix}$$

確認：$\langle \mathbf{e}_1, \mathbf{e}_2 \rangle = \frac{1}{\sqrt{12}}(1\cdot1 + 1\cdot(-1) + 0\cdot2) = 0$ ✓

---

## 正射影と最良近似

### 定義：正射影

$W$ を $V$ の部分空間、$\{\mathbf{e}_1,\ldots,\mathbf{e}_k\}$ を $W$ の正規直交基底とする。$\mathbf{v} \in V$ の $W$ への**正射影**を

$$\mathrm{proj}_W \mathbf{v} := \sum_{i=1}^k \langle \mathbf{e}_i, \mathbf{v} \rangle\, \mathbf{e}_i$$

と定義する。

### 定理4：最良近似定理

$\mathbf{v} - \mathrm{proj}_W \mathbf{v} \perp W$、すなわち $W$ 内で $\mathbf{v}$ に最も近いベクトルは $\mathrm{proj}_W \mathbf{v}$ である：

$$\|\mathbf{v} - \mathrm{proj}_W \mathbf{v}\| \leq \|\mathbf{v} - \mathbf{w}\| \qquad (\forall \mathbf{w} \in W)$$

**証明.**

$\mathbf{p} = \mathrm{proj}_W \mathbf{v}$ とおく。任意の $\mathbf{e}_j$ に対し

$$\langle \mathbf{e}_j,\, \mathbf{v} - \mathbf{p} \rangle = \langle \mathbf{e}_j, \mathbf{v} \rangle - \langle \mathbf{e}_j, \mathbf{p} \rangle = \langle \mathbf{e}_j, \mathbf{v} \rangle - \sum_i \langle \mathbf{e}_i, \mathbf{v} \rangle \langle \mathbf{e}_j, \mathbf{e}_i \rangle = \langle \mathbf{e}_j, \mathbf{v} \rangle - \langle \mathbf{e}_j, \mathbf{v} \rangle = 0$$

よって $\mathbf{v} - \mathbf{p} \perp W$。任意の $\mathbf{w} \in W$ に対し $\mathbf{p} - \mathbf{w} \in W$ だから

$$\|\mathbf{v} - \mathbf{w}\|^2 = \|(\mathbf{v}-\mathbf{p}) + (\mathbf{p}-\mathbf{w})\|^2 = \|\mathbf{v}-\mathbf{p}\|^2 + \|\mathbf{p}-\mathbf{w}\|^2 \geq \|\mathbf{v}-\mathbf{p}\|^2$$

（直交するベクトルにピタゴラスの定理を適用）。$\square$

> **最小二乗法への応用：** 連立方程式 $A\mathbf{x} = \mathbf{b}$ が解を持たないとき（過剰決定系）、$\|A\mathbf{x} - \mathbf{b}\|^2$ を最小にする $\mathbf{x}$ を求める問題が最小二乗法である。最良近似定理より、$A\mathbf{x}$ が $\mathbf{b}$ の $\mathrm{Im}\,A$ への正射影に等しくなるとき最小となる。正規方程式 $A^* A \mathbf{x} = A^* \mathbf{b}$（$\mathbb{K} = \mathbb{C}$ の場合）はこの条件の言い換えである。

