+++
title = "数列と極限"
weight = 10
date = 2026-08-11
+++

[ノート：実数](10_mathematics/20_set-theory/80-reals/)で得た $\mathbb{R}$ の上で、数列の収束を厳密に定義する。$\varepsilon$-$N$ 論法による収束の定義を出発点に、極限の基本性質を整理し、完備性（上限性質）と同値な諸命題を導く。

---

{{< toc >}}

---

## 数列の定義

**定義：** $\mathbb{R}$ の**数列**とは、写像 $a: \mathbb{N} \to \mathbb{R}$ のことである。$a(n)$ を $a_n$ と書き、数列を $(a_n)_{n \in \mathbb{N}}$ または単に $(a_n)$ と表す。

数列は写像として集合論的に定義される。無限に続く実数の列という直感的な概念は、$\mathbb{N}$ から $\mathbb{R}$ への写像として ZFC の枠組みに収まる。

> **例：**
> - $a_n = 1/n$：$1, 1/2, 1/3, 1/4, \ldots$
> - $a_n = (-1)^n$：$-1, 1, -1, 1, \ldots$
> - $a_n = (1 + 1/n)^n$：$2, 9/4, \ldots$（$e$ に収束する）

---

## 収束・発散の定義

### 定義：収束

数列 $(a_n)$ が $L \in \mathbb{R}$ に**収束する**とは、

$$\forall \varepsilon \in \mathbb{R}_{>0} , \exists N \in \mathbb{N} , \forall n \geq N ; |a_n - L| < \varepsilon$$

が成り立つことをいう。このとき $L$ を $(a_n)$ の**極限**といい、$\lim_{n \to \infty} a_n = L$ または $a_n \to L$ と書く。

$(a_n)$ が何らかの $L \in \mathbb{R}$ に収束するとき**収束列**といい、収束しないとき**発散列**という。

> **論理式の読み方：** 「どんな正の実数 $\varepsilon$ をとっても、ある番号 $N$ が存在して、$N$ 以降のすべての項が $L$ から距離 $\varepsilon$ 未満に収まる」。$\varepsilon$ は要求精度、$N$ はその精度が保証される番号である。
>
>厳密な意味は、[ノート：一階述語論理の記法と推論規則](10_mathematics/10_foundations-of-mathematics/10_logics/)参照

### 定義：正負の無限大への発散

$$a_n \to +\infty \iff \forall M \in \mathbb{R} , \exists N \in \mathbb{N} , \forall n \geq N ; a_n > M$$

$$a_n \to -\infty \iff \forall M \in \mathbb{R} , \exists N \in \mathbb{N} , \forall n \geq N ; a_n < M$$

$+\infty, -\infty$ は実数ではなく、あくまで「どこまでも大きく（小さく）なる」という挙動の記述である。

<hr style="border: none; height: 2px; background: linear-gradient(to right, transparent, #94a3b8, transparent); margin: 3rem 0;">

## 極限の基本性質

### 定理1：極限の一意性

数列 $(a_n)$ が $L$ にも $L'$ にも収束するならば $L = L'$。

**証明.** $\varepsilon > 0$ を任意にとる。
仮定より、ある $N_1, N_2 \in \mathbb{N}$ が存在して、
$n \geq N_1$ で $|a_n - L| < \varepsilon/2$、$n \geq N_2$ で $|a_n - L'| < \varepsilon/2$。
$N = \max(N_1, N_2)$ とおくと、$n \geq N$ で

$$|L - L'| \leq |L - a_n| + |a_n - L'| < \varepsilon/2 + \varepsilon/2 = \varepsilon$$

$\varepsilon > 0$ 
は任意だから 
$|L - L'| = 0$、
すなわち $L = L'$。$\square$

> **$\varepsilon$-論法における頻出テクニック：**
>
> 証明の最後で使われた「任意の $\varepsilon > 0$ に対して $0 \leq |L - L'| < \varepsilon$ が成り立つならば、 $|L - L'| = 0$ である」という推論は、解析学の証明で今後無数に登場する。
>
> 直感的には、どんなに小さな正の数よりも小さい非負の数は、$0$ しかありえないという理屈である。
>もし仮に $|L - L'| > 0$ だったとすると、例えば $\varepsilon = |L - L'| / 2$ という具体的な正の数をとったとき、$|L - L'| < |L - L'| / 2$ となってしまい、矛盾が生じる。

### 定理2：収束列は有界

$(a_n)$ が収束するならば、
$|a_n| \leq M$ をすべての $n$ について満たす
$M \in \mathbb{R}$ が存在する。

**証明.**  収束の定義より、任意の $\varepsilon > 0$ に対して条件を満たす $N$ が存在する。ここでは特に$\varepsilon = 1$ に対して $N$ をとると、
$n \geq N$ で 
$|a_n| \leq |a_n - L| + |L| < 1 + |L|$。
有限個の項 $|a_1|, \ldots, |a_{N-1}|$ と 
$1 + |L|$ の最大値を $M$ とおけばよい。$\square$

### 定理3：極限の四則演算

$(a_n) \to L$、$(b_n) \to M$ とする。

- $a_n + b_n \to L + M$
- $a_n - b_n \to L - M$
- $a_n b_n \to LM$
- $M \neq 0$ のとき $a_n / b_n \to L/M$（ただし十分大きな $n$ で $b_n \neq 0$）

**証明（積）.**
$|a_n b_n - LM| \leq |a_n||b_n - M| + |M||a_n - L|$。
$(a_n)$ は有界（定理2）だから $|a_n| \leq K$ なる $K$ が存在する。
$\varepsilon > 0$ に対し、
$|b_n - M| < \varepsilon/(2K)$ かつ 
$|a_n - L| < \varepsilon/(2(|M|+1))$ となる 
$N$ をとれば $|a_n b_n - LM| < \varepsilon$。$\square$

### 定理4：はさみうちの原理

$a_n \leq b_n \leq c_n$ がすべての $n$ について成り立ち、$a_n \to L$ かつ $c_n \to L$ ならば $b_n \to L$。

**証明.**
$\varepsilon > 0$
に対し、$n \geq N$
で $|a_n - L| < \varepsilon$
かつ $|c_n - L| < \varepsilon$
となる $N$ をとる。$n \geq N$ で

$$L - \varepsilon < a_n \leq b_n \leq c_n < L + \varepsilon$$

よって、
$|b_n - L| < \varepsilon$。
$\square$

---

## 完備性の同値な言い換え

[ノート：実数](10_mathematics/20_set-theory/80-reals/)で定義した完備性（上限性質）が、数列の収束に関する以下の命題と同値であることを示す。

$$\text{上限性質} \iff \text{単調収束定理} \iff \text{区間縮小法} \iff \text{BW定理} \iff \text{コーシーの判定法}$$

### 定理5：単調収束定理

単調増加かつ上に有界な数列は収束する。

**証明（上限性質 $\Rightarrow$ 単調収束定理）.**

$(a_n)$ を単調増加かつ上に有界とする。
集合 $A = \{a_n \mid n \in \mathbb{N}\}$ は空でなく上に有界だから、
上限性質より $L := \sup A$ が存在する。

$\varepsilon > 0$ を任意にとる。
$L - \varepsilon$ は $A$ の上界でないから、ある $N$ に対し $a_N > L - \varepsilon$。
$(a_n)$ は単調増加だから $n \geq N$ で $a_n \geq a_N > L - \varepsilon$。
また $a_n \leq L$ だから

$L - \varepsilon < a_n \leq L < L + \varepsilon$。
よって、
$|a_n - L| < \varepsilon$。
$\square$

**証明（単調収束定理 $\Rightarrow$ 上限性質）.**

 $\emptyset \neq A \subseteq \mathbb{R}$ が上に有界とする。上界の全体を $B = \{b \in \mathbb{R} \mid \forall a \in A, a \leq b\}$ とおく。
 
 $A$ の上界ではない要素 $a_0 \in A$ と、上界 $b_0 \in B$ を固定し、以下の二分探索で数列を構成する。（※もし $A$ のすべての要素が上界であれば、$A$ は一点集合であり上限は自明に存在する。）

$c_n = (a_n + b_n)/2$ とおき、$c_n \in B$ ならば $a_{n+1} = a_n$、$b_{n+1} = c_n$、$c_n \notin B$ ならば $a_{n+1} = c_n$、$b_{n+1} = b_n$ と定める。この構成により、各 $n$ について $b_n$ はつねに $A$ の上界（$b_n \in B$）であり、$a_n$ は $A$ の上界ではない（$a_n \notin B$）。

$(a_n)$ は単調増加かつ上に有界（例えば $b_0$ で抑えられる）だから、単調収束定理より極限 $L = \lim a_n$ が存在する。構成方法より区間の幅は $b_n - a_n = (b_0 - a_0)/2^n \to 0$ となるため、$b_n = a_n + (b_n - a_n) \to L$ である（極限の四則演算）。

ここで、この極限 $L$ が $A$ の最小の上界（$\sup A$）であることを示す。

$L$ が上界であること： 任意の $x \in A$ に対し、$b_n$ は上界だから常に $x \le b_n$ である。先ほど確認したように $\lim_{n \to \infty} b_n = L$ であるから、この不等式の両辺で $n \to \infty$ と極限をとれば $x \le L$ となり、$L$ は上界である。

$L$ が最小の上界であること： 任意の $\varepsilon > 0$ に対し、$a_n \to L$ であるから $L - \varepsilon < a_n$ となる $n$ が存在する。この $a_n$ は上界ではないので、ある $x \in A$ が存在して $a_n < x$ となる。したがって $L - \varepsilon < x$ となり、これは $L - \varepsilon$ が上界ではないことを示している。

以上より、$L$ は $A$ の最小の上界、すなわち $L = \sup A$ である。$\square$

### 定理6：区間縮小法

閉区間の列 $[a_1, b_1] \supseteq [a_2, b_2] \supseteq \cdots$ で $b_n - a_n \to 0$ を満たすものに対して、$\bigcap_{n=1}^{\infty} [a_n, b_n]$ はただ一点からなる。

**証明（上限性質 $\Rightarrow$ 区間縮小法）.** $(a_n)$ は単調増加かつ上に有界（各 $b_n$ が上界）だから、単調収束定理より $L = \lim a_n$ が存在する。同様に $(b_n)$ は単調減少かつ下に有界だから $L' = \lim b_n$ が存在する。$b_n - a_n \to 0$ より $L' - L = 0$、すなわち $L = L'$。各 $n$ について $a_n \leq L \leq b_n$ だから $L \in \bigcap_n [a_n, b_n]$ であり、共通部分は空ではない。

一意性を示す。任意の $x \in \bigcap_n [a_n, b_n]$ をとると、すべての $n$ に対して $a_n \leq x \leq b_n$ が成り立つ。はさみうちの原理より $x = L$ となるため、共通部分は $L$ ただ一点からなる。$\square$

> **注釈：開区間における証明の破綻と不等号の緩み**
>
> 開区間 $(a_n, b_n)$ の列を考えた場合、極限 $L$（および $L'$）が存在し、$L = L'$ となることまでは全く同じように成り立つ。しかし、その次の「ゆえに $L \in \bigcap_n (a_n, b_n)$ である」という結論が引き出せなくなる。その理由は、極限操作に伴う不等号の緩みにある。
>
> 開区間 $(a_n, b_n)$ に要素 $x$ が含まれるための条件は、強い不等号（等号を含まない）で表される。
>
> $$a_n < x < b_n$$
>
> 一方で、数列 $(a_n)$ が $L$ に、$(b_n)$ が $L$ に近づいていくとき、極限値 $L$ と各項の大小関係は、弱い不等号（等号を含む）でしか保証されない。極限の世界では限りなく近づく結果として、限界値において両者が一致する（等号が成立する）可能性があるからである。
>
> $$a_n \leq L \leq b_n$$
>
> もし $L$ がすべての開区間 $(a_n, b_n)$ に含まれる（すなわち $L \in \bigcap_n (a_n, b_n)$ である）とするならば、すべての $n$ に対して以下の条件が成り立たなければならない。
>
> $$a_n < L < b_n$$
>
> しかし、極限から得られるのは $a_n \leq L \leq b_n$ までであり、$a_n = L$ や $L = b_n$ となってしまう可能性を排除できない。もし等号が成立してしまえば、その時点で $L$ はその開区間の外側（境界線上）に落ちてしまい、共通部分には含まれない。

### 定理7：ボルツァーノ＝ワイエルシュトラスの定理

有界な実数列は収束する部分列をもつ。

**証明（区間縮小法を利用）.** $(a_n)$ を有界とし、$a_n \in [c, d]$ とする。$[c, d]$ を二等分し、無限個の項を含む半分を $[a_1, b_1]$ とする。これを繰り返すと閉区間の列 $[a_k, b_k]$ で $b_k - a_k = (d-c)/2^k \to 0$ が得られる。区間縮小法より $\bigcap_k [a_k, b_k] = \\{L\\}$。各 $[a_k, b_k]$ に含まれる項を選んで部分列をつくると、それは $L$ に収束する。$\square$

### 定理8：コーシーの収束判定法

実数列 $(a_n)$ が収束することと、$(a_n)$ がコーシー列であることは同値である。

ここで $(a_n)$ が**コーシー列**であるとは、

$$\forall \varepsilon \in \mathbb{R}_{>0}\, \exists N \in \mathbb{N}\, \forall m, n \geq N; |a_m - a_n| < \varepsilon$$

が成り立つことをいう。

**証明（収束 $\Rightarrow$ コーシー列）.** 

$a_n \to L$ とする。$\varepsilon > 0$ 
に対し $n \geq N$ で $|a_n - L| < \varepsilon/2$ 
となる $N$ をとると、$m, n \geq N$ で

$$|a_m - a_n| \leq |a_m - L| + |L - a_n| < \varepsilon. \quad \square$$

**証明（コーシー列 $\Rightarrow$ 収束）.** 

コーシー列は有界である（ノート7のコーシー列の有界性と同様の議論）。
BW定理より収束する部分列 $(a_{n_k}) \to L$ が存在する。
$\varepsilon > 0$ に対し、$m, n \geq N$ で $|a_m - a_n| < \varepsilon/2$ となる $N$ をとる。
十分大きな $k$ に対し $n_k \geq N$ かつ $|a_{n_k} - L| < \varepsilon/2$ だから、$n \geq N$ で

$$|a_n - L| \leq |a_n - a_{n_k}| + |a_{n_k} - L| < \varepsilon. \quad \square$$

> **コーシーの収束判定法の意義：** 収束先 $L$ が何であるかを知らなくても、項同士の距離だけで収束を判定できる。これは極限値が事前に分からない状況（たとえば級数の収束判定）で特に有用である。また、この性質が距離空間の完備性の定義（すべてのコーシー列が収束する）の出発点となる。

## 完備性の同値性のまとめ

本ノートでは上限性質を公理（出発点）として数列に関する重要な定理を導いたが、これら5つの命題は $\mathbb{R}$ においてすべて互いに同値である。本ノートでは「上限性質 $\Rightarrow$ 単調収束定理 $\Rightarrow$ 上限性質」および下記で「BW定理 $\Rightarrow$ 単調収束定理」の方向を示した。どれを完備性の定義として採用しても、同じ解析学を展開することができる。

| 命題 | 内容 |
| :--- | :--- |
| **上限性質** | 空でない上に有界な集合は上限をもつ |
| **単調収束定理** | 単調増加・上に有界な数列は収束する |
| **区間縮小法** | 縮小する閉区間列の共通部分はただ一点 |
| **BW定理** | 有界な数列は収束する部分列をもつ |
| **コーシーの判定法** | コーシー列であることと収束することは同値 |

これらはいずれも $\mathbb{Q}$ では成立しない（$\sqrt{2}$ への近似列はコーシー列だが $\mathbb{Q}$ 内に収束先をもたない）。完備性とはこの「穴のなさ」を異なる角度から捉えた表現である。

### BW定理から単調収束定理を導く

BW定理を認めれば、単調収束定理を導くことができる。これにより、上限性質を用いなくても、有界性と部分列の収束性から直接的に単調増加数列の挙動を制御できることがわかる。

**定理（BW定理 $\Rightarrow$ 単調収束定理）.**

**証明.** $(a_n)$ を単調増加かつ上に有界な数列とする。$a_n \ge a_1$ であるから、$(a_n)$ は有界である。BW定理より、$(a_n)$ は収束する部分列 $(a_{n_k})$ をもつ。その極限を $L$ とおく。

任意の $\varepsilon > 0$ をとる。部分列の収束より、$L - \varepsilon < a_{n_K} \le L$ となる番号 $n_K$ が存在する。元の数列 $(a_n)$ の単調性より、$n \ge n_K$ ならば $a_{n_K} \le a_n$ である。また、任意の $n$ に対して $a_n \le L$ が成り立つ（※）。したがって、$n \ge n_K$ において

$$L - \varepsilon < a_{n_K} \le a_n \le L < L + \varepsilon$$

となり、数列 $(a_n)$ は $L$ に収束する。$\square$

> ※ もしある $M$ で $a_M > L$ となれば、単調性よりそれ以降の部分列の項もすべて $L$ より大きくなり、部分列が $L$ に収束することに矛盾する。

---

## 上極限と下極限（limsup, liminf）

有界な数列は常に収束するとは限らない（例：$a_n = (-1)^n$）が、BW定理（定理7）が示すように、収束する部分列は必ず存在する。数列が究極的にどの範囲に絞られていくのかを捉えるため、上極限と下極限という概念を導入する。

### 定義：上極限と下極限

$(a_n)$ を有界な実数列とする。各 $k \in \mathbb{N}$ に対して、第 $k$ 項以降からなる集合の上限と下限をそれぞれ次のように定める。

$$b_k = \sup \{ a_n \mid n \geq k \}$$

$$c_k = \inf \{ a_n \mid n \geq k \}$$

$k$ が大きくなるにつれて考える集合は縮小していくため、数列 $(b_k)$ は単調減少であり下に有界となる。一方、数列 $(c_k)$ は単調増加であり上に有界となる。したがって、単調収束定理（定理5）より、これらの極限は必ず存在する。これを上極限・下極限と呼ぶ。

**上極限:**

$$\limsup_{n \to \infty} a_n = \lim_{k \to \infty} b_k = \lim_{k \to \infty} \left( \sup_{n \geq k} a_n \right)$$

（$\varlimsup_{n \to \infty} a_n$ と表記されることもある）

**下極限:**

$$\liminf_{n \to \infty} a_n = \lim_{k \to \infty} c_k = \lim_{k \to \infty} \left( \inf_{n \geq k} a_n \right)$$

（$\varliminf_{n \to \infty} a_n$ と表記されることもある）

> ※ $(a_n)$ が上に有界でない場合は $\limsup a_n = \infty$、下に有界でない場合は $\liminf a_n = -\infty$ と定める。

### 定理9：上極限・下極限と収束の同値性

有界な数列 $(a_n)$ について、以下の二つは同値である。

1. $(a_n)$ が $L$ に収束する
2. $\limsup_{n \to \infty} a_n = \liminf_{n \to \infty} a_n = L$

**証明.** 任意の $k \in \mathbb{N}$ に対して $c_k \leq a_k \leq b_k$ が常に成り立つ。
$L = \limsup a_n = \liminf a_n$ のとき、$k \to \infty$ とすると $b_k \to L$ かつ $c_k \to L$ であるから、はさみうちの原理（定理4）より $a_k \to L$ となる。

逆に $a_n \to L$ とする。任意の $\varepsilon > 0$ に対し、ある $N \in \mathbb{N}$ が存在して、$n \geq N$ ならば $L-\varepsilon < a_n < L+\varepsilon$ となる。ゆえに、第 $N$ 項以降の上限 $b_n$ と下限 $c_n$ も $[L-\varepsilon, L+\varepsilon]$ に含まれる。極限をとれば $L-\varepsilon \leq \liminf a_n \leq \limsup a_n \leq L+\varepsilon$。$\varepsilon$ は任意なので、$\limsup a_n = \liminf a_n = L$ である。$\square$

> **上極限・下極限の意義：** どんな有界数列であっても、上極限と下極限は必ず存在する。極限 $\lim a_n$ が存在するか分からない（あるいは存在しない）状況において、数列の挙動を不等式で評価することができる。今後の解析学（例えば、べき級数の収束半径を与えるコーシー・アダマールの定理など）で必要となる。

---

## 付録：$\varepsilon$-$N$ 論法の具体例

収束の定義（$\forall \varepsilon > 0\, \exists N \in \mathbb{N}\, \forall n \geq N; |a_n - L| < \varepsilon$）
を実際に使う練習として、二つの例を示す。
証明の構造は共通しており、$\varepsilon$ が与えられたら $N$ を具体的に構成する。

### 例1：$1/n \to 0$

**主張：** $\lim_{n \to \infty} 1/n = 0$

**証明：** $\varepsilon > 0$ を任意にとる。アルキメデスの原理（ノート7）より、$1/N < \varepsilon$ となる $N \in \mathbb{N}$ が存在する。このとき $n \geq N$ ならば

$$\left|\frac{1}{n} - 0\right| = \frac{1}{n} \leq \frac{1}{N} < \varepsilon. \quad \square$$

> **構造の読み方：** $N$ の存在をアルキメデスの原理が保証している。$\varepsilon$ が小さいほど大きな $N$ が必要になるという直感が、$1/N < \varepsilon$ という式に現れている。

### 例2：$n^2/(n^2+1) \to 1$

**主張：** $\lim_{n \to \infty} \dfrac{n^2}{n^2+1} = 1$

**証明：** $\varepsilon > 0$ を任意にとる。まず誤差を評価する：

$$\left|\frac{n^2}{n^2+1} - 1\right| = \left|\frac{-1}{n^2+1}\right| = \frac{1}{n^2+1} < \frac{1}{n}$$

アルキメデスの原理より $1/N < \varepsilon$ となる $N \in \mathbb{N}$ をとると、$n \geq N$ ならば

$$\left|\frac{n^2}{n^2+1} - 1\right| < \frac{1}{n} \leq \frac{1}{N} < \varepsilon. \quad \square$$

> **式変形のポイント：** $1/(n^2+1)$ を直接 $\varepsilon$ と比較するより、$1/n$ で上から抑えてから例1の結果を使う方が見通しがよい。扱いにくい式を扱いやすい式で上から抑える方法は $\varepsilon$-$N$ 論法で繰り返し現れる。
