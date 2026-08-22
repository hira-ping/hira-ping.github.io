+++
title = "連続性"
weight = 20
date = 2026-08-17
+++

[ノート：実数（ℝ）](40_knowledge-base/10_mathematics/20_set-theory/80-reals/)と[ノート：数列と極限](40_knowledge-base/10_mathematics/40_analysis/10-sequences/)を踏まえ、関数の連続性を厳密に定義する。$\varepsilon$-$\delta$ 論法による定義を出発点に、連続関数の基本性質を整理し、完備性を用いて中間値定理・最大値定理を証明する。

$\mathbb{R}$ の元を**点**と呼び、数直線として視覚化する。これは、$\mathbb{R}$ が一次元の連続した線であるという直感に対応するが、その正当化（$\mathbb{R}$ が距離空間・位相空間として幾何学的な直線と同一視できること）は位相空間論のノートに委ねる。

注目すべきは、連続性の定義（$\varepsilon$-$\delta$ 論法）が数直線のイメージに依存していない点である。
定義に現れるのは、$|x - a|$ が小さければ、$|f(x) - f(a)|$ も小さいという関係だけであり、
直線や空間の概念は不要である。

この観察が抽象化の手がかりになる。$|x - a|$ を一般の二点間の「大きさ」を測る関数 $d(x, a)$ に置き換えれば距離空間上の連続性が得られ、
さらに、$d(x, a) < \delta$ を満たす点の集まりを開集合という概念で抽象化すれば位相空間上の連続性が得られる。
$\varepsilon$-$\delta$ 論法は、その出発点に位置する。

---

{{< toc >}}

---

## 連続性の定義

### 定義：点での連続性

関数 $f: A \to \mathbb{R}$（$A \subseteq \mathbb{R}$）が点 $a \in A$ で**連続**であるとは、

$$\forall \varepsilon \in \mathbb{R}_{>0}, \exists \delta \in \mathbb{R}_{>0}, \forall x \in A; |x - a| < \delta \Rightarrow |f(x) - f(a)| < \varepsilon$$

が成り立つことをいう。

> **論理式の読み方：** どんな正の実数 $\varepsilon$ をとっても、ある $\delta > 0$ が存在して、$a$ から距離 $\delta$ 未満の点 $x$ における $f(x)$ と $f(a)$ の距離が $\varepsilon$ 未満になる。$\varepsilon$ は出力側の要求精度、$\delta$ はそれを保証する入力側の許容幅である。

### 定義：区間上の連続性

$f: A \to \mathbb{R}$ が $A$ のすべての点で連続であるとき、$f$ は $A$ 上で連続であるという。

### 連続性と数列の収束の同値性

連続性は数列を用いて言い換えることができる。この性質により、関数の極限を数列の極限に帰着させることが可能になる。

**命題：** $f: A \to \mathbb{R}$ が $a \in A$ で連続であることは、以下と同値である：

$$A \text{ 内の任意の数列 } (x_n) \text{ について、} \lim_{n \to \infty} x_n = a \Rightarrow \lim_{n \to \infty} f(x_n) = f(a)$$

**証明（$\Rightarrow$）** 

$f$ が $a$ で連続であると仮定し、$x_n \to a$ を満たす任意の数列 $(x_n)$ をとる。
示すべきは $f(x_n) \to f(a)$ である。

まず、任意の $\varepsilon > 0$ をとる。
仮定より $f$ は $a$ で連続だから、
この $\varepsilon$ に対してある $\delta > 0$ が存在し、
$$|x - a| < \delta \Rightarrow |f(x) - f(a)| < \varepsilon$$
が成り立つ。

次に、$x_n \to a$ の定義における任意の正の数として、いま得られた $\delta > 0$ を選ぶ。
すると、ある $N \in \mathbb{N}$ が存在して、
$$n \geq N \Rightarrow |x_n - a| < \delta$$
が成り立つ。

したがって、$n \geq N$ なる任意の $n$ に対して
$$|f(x_n) - f(a)| < \varepsilon$$ が成り立つ。
これは $f(x_n) \to f(a)$ を意味している。$\square$

**証明（$\Leftarrow$）** 

対偶を示す。すなわち、$f$ が $a$ で連続でないと仮定し、
$x_n \to a$ を満たしつつ $f(x_n) \not\to f(a)$ となる数列 $(x_n)$ を構成する。

$f$ が $a$ で連続でないとは、論理式を否定して以下が成り立つことである。

$$\exists \varepsilon_0 > 0, \forall \delta > 0, \exists x \in A; |x - a| < \delta \land |f(x) - f(a)| \geq \varepsilon_0$$

（ある誤差 $\varepsilon_0 > 0$ が存在し、どれほど $\delta > 0$ を小さくとっても、条件を満たさない点 $x$ が存在することを意味する。）

この $\varepsilon_0$ を固定し、
各 $n \in \mathbb{N}$ について、任意の $\delta$ として、 $\delta = 1/n$ をとる。すると上の命題から、

$$|x_n - a| < \frac{1}{n} \quad \text{かつ} \quad |f(x_n) - f(a)| \geq \varepsilon_0$$

を満たす点 $x_n \in A$ が各 $n$ に対して選べる。

この数列 $(x_n)$ を考えると、
不等式 $|x_n - a| < 1/n$ により $x_n \to a$ である。
しかし、すべての $n$ に対して $$|f(x_n) - f(a)| \geq \varepsilon_0 > 0$$ であるため、
$f(x_n)$ は $f(a)$ に収束しない。$\square$

> 連続でないことの証明には、反例を探す範囲 $\delta$ を $1/n$ として狭めながら点 $x_n$ を選び出し、数列を構成する論法がよく用いられる。

---

## 連続関数の基本性質

### 定理1：四則演算の連続性

$f, g: A \to \mathbb{R}$ がともに $a \in A$ で連続ならば、$f + g$、$f - g$、$fg$ も $a$ で連続である。また $g(a) \neq 0$ ならば $f/g$ も $a$ で連続である。

**証明.** 数列の極限の四則演算（[ノート：数列と極限](40_knowledge-base/10_mathematics/40_analysis/10-sequences/#%E5%AE%9A%E7%90%863%E6%A5%B5%E9%99%90%E3%81%AE%E5%9B%9B%E5%89%87%E6%BC%94%E7%AE%97)）
と連続性の数列による特徴づけから直ちに従う。

$x_n \to a$ とすると $f(x_n) \to f(a)$、$g(x_n) \to g(a)$ だから、$(f+g)(x_n) = f(x_n) + g(x_n) \to f(a) + g(a) = (f+g)(a)$。他も同様。$\square$

### 定理2：合成関数の連続性

$f: A \to \mathbb{R}$ が $a$ で連続、$g: B \to \mathbb{R}$（$f(A) \subseteq B$）が $f(a)$ で連続ならば、$g \circ f: A \to \mathbb{R}$ は $a$ で連続である。

**証明.** $x_n \to a$ とする。$f$ の連続性より $f(x_n) \to f(a)$。$g$ の連続性より $g(f(x_n)) \to g(f(a))$。$\square$

### 定理3：多項式関数の連続性

多項式関数 $p(x) = a_n x^n + \cdots + a_1 x + a_0$ はすべての点で連続である。

**証明.** $f(x) = x$ が連続（$\delta = \varepsilon$ とすればよい）であり、定理1を繰り返し適用することで任意の多項式の連続性が従う。$\square$

---

## 中間値定理

### 定理4：中間値定理

$f: [a, b] \to \mathbb{R}$ が連続で $f(a) \neq f(b)$ とする。

$f(a)$ と $f(b)$ の間の任意の値 $\gamma$（すなわち $f(a) < \gamma < f(b)$ または $f(b) < \gamma < f(a)$）に対して、$f(c) = \gamma$ となる $c \in (a, b)$ が存在する。

**証明.** 

$f(a) < \gamma < f(b)$ の場合を示す（もう一方は $-f$ に適用すればよい）。

集合 $S = \{x \in [a, b] \mid f(x) \leq \gamma\}$ を考える。
$a \in S$ だから $S \neq \emptyset$、また $S \subseteq [a, b]$ だから上に有界。
完備性より $c := \sup S$ が存在する。

$c \in [a, b]$ であることを確認する。
$a \in S$ より $c \geq a$。各 $x \in S$ に対し $x \leq b$ だから $c \leq b$。

$f(c) = \gamma$ を示す。

まず、**$f(c) > \gamma$ と仮定して矛盾を導く。**

$f$ の連続性より、ある $\delta > 0$ が存在して 
$|x - c| < \delta \Rightarrow f(x) > \gamma$ 。

> $f$ の連続性より、$\forall \varepsilon > 0, \exists \delta > 0; |x - c| < \delta \Rightarrow |f(x) - f(c)| < \varepsilon$ 。
>
> 任意の $\varepsilon$ として $f(c) - \gamma > 0$ をとると、ある $\delta$ が存在して、$|x - c| < \delta \Rightarrow |f(x) - f(c)| < f(c) - \gamma $ 。
> よって、$|x - c| < \delta \Rightarrow  \gamma < f(x)$ 。

すなわち、 $(c - \delta, c + \delta) \cap [a, b]$ 上では $f(x) > \gamma$ だから、
この範囲に $S$ の点はない。よって $c - \delta$ が $S$ の上界となり、$c = \sup S$ に矛盾する。

次に、**$f(c) < \gamma$ と仮定して矛盾を導く。**

$f$ の連続性より、ある $\delta > 0$ が存在して $|x - c| < \delta \Rightarrow f(x) < \gamma$ 。

$c = \sup S \leq b$。また、$f(b) > \gamma$ より $b \notin S$、すなわち $c \neq b$ だから、$c < b$ 。

$c + \delta \in S$ となる $\delta \in (0, \delta)$ が存在する。これは $c = \sup S$ に矛盾する。

以上により、 $f(c) = \gamma$。$\square$

> **完備性の役割：** $\sup S$ の存在が完備性によって保証されている。$\mathbb{Q}$ 上では中間値定理は成立しない。たとえば $f(x) = x^2 - 2$ は $f(1) = -1 < 0$ かつ $f(2) = 2 > 0$ だが、$f(c) = 0$ となる $c \in \mathbb{Q}$ は存在しない（$\sqrt{2} \notin \mathbb{Q}$）。

---

## 最大値定理

### 有界性の定理

**定理5：** $f: [a, b] \to \mathbb{R}$ が連続ならば、$f$ は有界である。

すなわち、ある $M \in \mathbb{R}$ が存在して、すべての $x \in [a, b]$ に対し $|f(x)| \leq M$。

**証明.** 

背理法で示す。

$f$ が有界でないとすると、各 $n \in \mathbb{N}$ に対し $|f(x_n)| > n$ となる $x_n \in [a, b]$ が存在する。
$(x_n)$ は有界（$a \leq x_n \leq b$）だから、
BW定理（[ノート：数列と極限](40_knowledge-base/10_mathematics/40_analysis/10-sequences/#%E5%AE%9A%E7%90%867%E3%83%9C%E3%83%AB%E3%83%84%E3%82%A1%E3%83%BC%E3%83%8E%E3%83%AF%E3%82%A4%E3%82%A8%E3%83%AB%E3%82%B7%E3%83%A5%E3%83%88%E3%83%A9%E3%82%B9%E3%81%AE%E5%AE%9A%E7%90%86)）
より収束する部分列 $(x_{n_k})$ が存在する。その極限を $c$ とする。
$c \in [a, b]$ であり、$f$ の連続性より $f(x_{n_k}) \to f(c)$。
しかし、$|f(x_{n_k})| > n_k \to \infty$ だから、$f(x_{n_k})$ は発散し、矛盾する。$\square$

### 定理6：最大値定理

$f: [a, b] \to \mathbb{R}$ が連続ならば、$f$ は最大値と最小値をもつ。すなわち

$$\exists x_{\max} \in [a, b],\; f(x_{\max}) = \sup_{x \in [a,b]} f(x)$$

$$\exists x_{\min} \in [a, b],\; f(x_{\min}) = \inf_{x \in [a,b]} f(x)$$

**証明（最大値）.** 

定理5より $f([a,b])$ は上に有界。$f([a,b]) \neq \emptyset$ だから、完備性より $M := \sup f([a,b])$ が存在する。

$M$ の定義より、各 $n \in \mathbb{N}$ に対し $M - 1/n < f(x_n) \leq M$ となる $x_n \in [a, b]$ が存在する。$(x_n)$ は有界だから BW 定理より収束する部分列 $(x_{n_k}) \to x_{\max}$ が存在し、$x_{\max} \in [a,b]$。$f$ の連続性より、

$$f(x_{\max}) = \lim_{k \to \infty} f(x_{n_k}) = M. \quad \square$$

（空でない部分集合 $S \subset \mathbb{R}$ について、上限 $\sup S$ が存在し、かつ $\sup S \in S$ ならば、$\sup S = \max S$ である。）

最小値も $-f$ に適用すれば同様に得られる。

> **定理5・6における完備性の役割：** BW定理（ノート8）を経由して完備性が使われている。有界閉区間 $[a,b]$ という設定が本質的であり、開区間や非有界な区間では最大値定理は一般に成立しない。たとえば $f(x) = x$ は $(0, 1)$ 上で最大値をもたず、$f(x) = x$ は $\mathbb{R}$ 上で有界でない。

中間値定理と最大値定理はいずれも完備性に依存しており、$\mathbb{Q}$ 上では成立しない。$\mathbb{R}$ が穴のない直線であるという完備性の解析学的な現れである。
