+++
title = "環・体"
weight = 20
date = 2026-08-23
+++

群は一つの演算を持つ構造だった。本ノートでは二つの演算（加法と乗法）を持つ構造を定義する。加法については群の公理を要求し、乗法については結合律と分配律を要求したものが**環**である。さらに乗法についても逆元を要求したものが**体**である。

[ノート：整数・有理数（ℤ・ℚ）](40_knowledge-base/10_mathematics/20_set-theory/60-numbers/)や[ノート：実数（ℝ）](40_knowledge-base/10_mathematics/20_set-theory/80-reals/)で構成したℤ・ℚ・ℝは、この抽象的な定義の具体例である。ℤからℚへの拡張は、乗法逆元を付け加える操作であったが、これは環から体への拡張として整理できる。

---

{{< toc >}}

---

## 環の定義

### 定義：環

集合 $R$ と二つの二項演算 $+$（加法）と $\cdot$（乗法）の組 $(R, +, \cdot)$ が**環**であるとは、以下の公理をすべて満たすことをいう。

- **(R1) $(R, +)$ は可換群：**
	- 結合律：$(a+b)+c = a+(b+c)$
	- 単位元（零元）：$\exists 0 \in R,\; a + 0 = 0 + a = a$
	- 逆元：$\exists {-a} \in R,\; a + (-a) = 0$
	- 交換律：$a + b = b + a$
- **(R2) 乗法の結合律：** $(a \cdot b) \cdot c = a \cdot (b \cdot c)$
- **(R3) 乗法の単位元：** $\exists 1 \in R,\; 1 \cdot a = a \cdot 1 = a$
- **(R4) 分配律：**
	- $a \cdot (b + c) = a \cdot b + a \cdot c$
	- $(a + b) \cdot c = a \cdot c + b \cdot c$

> **流儀について：** 乗法の単位元（R3）を要求しない定義を採用する流儀もある（その場合、単位的環または環と区別することがある）。本ノートでは単位元の存在を環の定義に含める。

### 定義：可換環

環 $(R, +, \cdot)$ において乗法が交換律 $a \cdot b = b \cdot a$ を満たすとき、$R$ を**可換環**という。

### 基本性質

**命題1：** 任意の環 $R$ において、$a \cdot 0 = 0 \cdot a = 0$

**証明.** $a \cdot 0 = a \cdot (0 + 0) = a \cdot 0 + a \cdot 0$。両辺から $a \cdot 0$ を引くと $0 = a \cdot 0$。$\square$

**命題2：** $(-1) \cdot a = -a$

**証明.** $a + (-1) \cdot a = 1 \cdot a + (-1) \cdot a = (1 + (-1)) \cdot a = 0 \cdot a = 0$。加法逆元の一意性より $(-1) \cdot a = -a$。$\square$

> **零元と単位元の違い：** $0$（零元）は加法の単位元、$1$（単位元）は乗法の単位元。$0 = 1$ となる環は $R = \{0\}$ （**零環**）のみ。零環以外では $0 \neq 1$。

---

## 環の例

### 例1：整数環 $(\mathbb{Z}, +, \times)$

$\mathbb{Z}$ は可換環である。(R1)〜(R4) は、すべて[ノート：整数・有理数（ℤ・ℚ）](40_knowledge-base/10_mathematics/20_set-theory/60-numbers/)で確認済みである。乗法の単位元は $1$。

### 例2：有理数・実数・複素数

$(\mathbb{Q}, +, \times)$、$(\mathbb{R}, +, \times)$、$(\mathbb{C}, +, \times)$ はいずれも可換環である。（さらに体でもある。ー後述）

### 例3：剰余環 $\mathbb{Z}/n\mathbb{Z}$

[ノート：群](40_knowledge-base/10_mathematics/30_algebra/10-groups/#%E4%BE%8B4%E6%9C%89%E9%99%90%E7%BE%A4)で構成した商集合 $\mathbb{Z}/n\mathbb{Z} = \{[0], [1], \ldots, [n-1]\}$ に加法と乗法を定める。

$$[a] + [b] := [a + b], \qquad [a] \cdot [b] := [a \cdot b]$$

**Well-definedness：** $[a] = [a']$（すなわち $n \mid a-a'$）かつ $[b] = [b']$ のとき、$[ab] = [a'b']$ を確認する。$a = a' + kn$、$b = b' + ln$ とすると

$$ab = (a'+kn)(b'+ln) = a'b' + (a'l + b'k + kln)n$$

よって $n \mid ab - a'b'$、すなわち $[ab] = [a'b']$。$\square$

加法については A1 の例4で確認済み。乗法の単位元は $[1]$。分配律は $\mathbb{Z}$ の分配律から従う。よって $\mathbb{Z}/n\mathbb{Z}$ は可換環である。

> **モジュラー演算：** モジュラー演算（$n$ を法とする計算）は、$\mathbb{Z}/n\mathbb{Z}$ という環の演算にほかならない。「余りだけ見ればよい」という計算規則の理由は well-definedness による。

### 例4：多項式環 $R[x]$

環 $R$ に対し、$R$ 係数の多項式全体

$$R[x] = \left\{ a_n x^n + a_{n-1} x^{n-1} + \cdots + a_0 \;\middle|\; n \in \mathbb{N},\, a_i \in R \right\}$$

は通常の多項式の加法・乗法について環をなす。$R$ が可換環ならば $R[x]$ も可換環。

> **多項式環の重要性：** $\mathbb{Z}[x]$・$\mathbb{Q}[x]$・$\mathbb{R}[x]$・$\mathbb{C}[x]$ はいずれも代数学で中心的な役割を果たす。とくに $\mathbb{F}[x]$（$\mathbb{F}$ は体）は整数環 $\mathbb{Z}$ と類似した性質（割り算・互除法・素元分解）をもつ。

### 例5：正方行列環 $M_n(\mathbb{R})$

$n \times n$ 実正方行列全体 $M_n(\mathbb{R})$ は行列の加法・乗法について環をなす。乗法の単位元は単位行列 $I_n$。$n \geq 2$ では乗法は**非可換**である。

> $M_n(\mathbb{R})$ については線形代数で詳しく扱う。ここでは非可換環の例として挙げるにとどめる。

---

## 体の定義

### 定義：体

可換環 $(F, +, \cdot)$ が**体**であるとは、$0 \neq 1$ かつ次が成り立つことをいう：

**(F1) 乗法逆元の存在：** $\forall a \in F,\; a \neq 0 \Rightarrow \exists a^{-1} \in F,\; a \cdot a^{-1} = 1$

すなわち体とは、零元以外のすべての元が乗法逆元をもつ可換環である。

> **言い換え：** $(F \setminus \{0\}, \cdot)$ が可換群をなすとき、$(F, +, \cdot)$ は体である。加法群と乗法群の両方が揃った構造が体である。

### 体の例

- $(\mathbb{Q}, +, \times)$： $a/b \neq 0$ の逆元は $b/a$。✓
- $(\mathbb{R}, +, \times)$： ✓
- $(\mathbb{C}, +, \times)$： $a + bi \neq 0$ の逆元は $\dfrac{a - bi}{a^2 + b^2}$。✓
- $(\mathbb{Z}/p\mathbb{Z}, +, \cdot)$（$p$ 素数）：体になる。

>  $\mathbb{Z}/p\mathbb{Z}$ が体であることの証明は、ベズーの定理（初等整数論）に依存する。ここでは事実として述べるにとどめる。
>  
 > **参考：**
 > 
 > $(\mathbb{Z}/p\mathbb{Z}, +, \cdot)$ が体となる理由
 > 
> $[a] \neq [0]$（すなわち $p$ が $a$ を割り切らない）とする。
$p$ は素数なので、$a$ と $p$ は互いに素であり $\gcd(a, p) = 1$ となる。
ここでベズーの定理（初等整数論）を用いると、$ax + py = 1$ を満たす整数 $x, y$ が存在する。
この等式を $\mathbb{Z}/p\mathbb{Z}$ 上で考えると、$[ax + py] = [1]$ となるが、$py$ は $p$ の倍数なので $[py] = [0]$。
したがって $[a] \cdot [x] = [1]$ となり、この $[x]$ が $[a]$ の乗法逆元である。✓
>
> $(\mathbb{Z}/n\mathbb{Z})$（$n$ 合成数） が体とならない理由
>
> たとえば $n = 6$ のとき、$[2]\cdot[3] = [6] = [0]$ だから $[2]$ と $[3]$ は零因子（零でないのに積が零）であり、逆元を持てない。

> **零因子：** 環 $R$ において $a \neq 0$、$b \neq 0$ かつ $ab = 0$ となる元 $a, b$ を**零因子**という。体に零因子は存在しない（逆元をもつ元は零因子になれないから）。

---

## 部分環・部分体

### 定義：部分環

環 $(R, +, \cdot)$ の部分集合 $S \subseteq R$ が**部分環**であるとは、$S$ が $R$ と同じ演算について環をなすことをいう。

**判定条件：** $S \subseteq R$ が部分環であることは、次の三条件をすべて満たすことと同値である。
1. $1_R \in S$（元の環の単位元を含む）
2. $\forall a, b \in S,\; a - b \in S$（加法の部分群である）
3. $\forall a, b \in S,\; a \cdot b \in S$（乗法について閉じている）

*証明は A1・部分群の1ステップ判定法と同様である。*

**例：** $\mathbb{Z} \subseteq \mathbb{Q} \subseteq \mathbb{R} \subseteq \mathbb{C}$ はいずれも部分環の連鎖である。

### 定義：部分体

体 $F$ の部分集合 $K \subseteq F$ が**部分体**（または $F$ の**部分体**）であるとは、$K$ が $F$ と同じ演算について体をなすことをいう。

**例：** $\mathbb{Q} \subseteq \mathbb{R} \subseteq \mathbb{C}$。また $\mathbb{Q}(\sqrt{2}) = \{a + b\sqrt{2} \mid a, b \in \mathbb{Q}\}$ は $\mathbb{R}$ の部分体である。

---

## 環準同型・体準同型

### 定義：環準同型

環 $(R, +, \cdot)$ と $(S, +, \cdot)$ に対し、写像 $\varphi: R \to S$ が**環準同型**であるとは、

$$\varphi(a + b) = \varphi(a) + \varphi(b), \qquad \varphi(a \cdot b) = \varphi(a) \cdot \varphi(b), \qquad \varphi(1_R) = 1_S$$

が成り立つことをいう。全単射な環準同型を**環同型**といい $R \cong S$ と書く。

> **単位元の保存：** $\varphi(1_R) = 1_S$ を定義に含める流儀と含めない流儀がある。含めない場合でも乗法の条件から $\varphi(1_R)$ が $S$ の単位元になることが多いが、一般には保証されないため、本ノートでは明示的に要求する。

### 命題3：環準同型の基本性質

環準同型 $\varphi: R \to S$ に対して：

1. $\varphi(0_R) = 0_S$
2. $\varphi(-a) = -\varphi(a)$
3. $\ker \varphi := \{a \in R \mid \varphi(a) = 0_S\}$ は $R$ の部分環（さらに**イデアル**の構造をもつ—後述）
4. $\mathrm{Im}\, \varphi$ は $S$ の部分環

**証明.**

1・2は加法群の準同型としての性質（[ノート：群](40_knowledge-base/10_mathematics/30_algebra/10-groups/#%E5%91%BD%E9%A1%8C6%E6%BA%96%E5%90%8C%E5%9E%8B%E3%81%AE%E5%9F%BA%E6%9C%AC%E6%80%A7%E8%B3%AA)）から従う。3・4は部分環の判定条件を確認すればよい。$\square$

### 定義：体準同型

体 $F$、$K$ 間の環準同型を**体準同型**という。

**命題4：** 体準同型は必ず単射である。

**証明.**

体準同型 $\varphi: F \to K$ を考える。単射性を示すため $\ker \varphi = \{0_F\}$ を示す（[ノート：群](40_knowledge-base/10_mathematics/30_algebra/10-groups/#%E5%91%BD%E9%A1%8C7%E6%A0%B8%E3%81%A8%E5%8D%98%E5%B0%84%E6%80%A7)）。

$a \in \ker \varphi$ とし、$a \neq 0_F$ と仮定して矛盾を導く。
$a \neq 0_F$ だから体 $F$ には逆元 $a^{-1}$ が存在する。準同型の性質を用いて $\varphi(1_F)$ を計算すると、
$\varphi(1_F) = \varphi(a \cdot a^{-1}) = \varphi(a) \cdot \varphi(a^{-1})$ となる。

ここで仮定より $a \in \ker \varphi$ すなわち $\varphi(a) = 0_K$ だから、
$\varphi(1_F) = 0_K \cdot \varphi(a^{-1}) = 0_K$ となる。

しかし、体準同型の定義より $\varphi(1_F) = 1_K$ であり、体 $K$ においては $0_K \neq 1_K$ であるから、これは矛盾。

したがって $a = 0_F$ でなければならず、$\ker \varphi = \{0_F\}$ が示された。$\square$

> **体準同型は埋め込み：** 体の間の準同型は必ず単射になる。つまり、体から体への写像で演算を保つものは、必ず包含（埋め込み）の形をしているということである。この意味で、体は非常に剛性の高い構造であるといえる。

### 環準同型の例

**包含写像：** $\mathbb{Z} \hookrightarrow \mathbb{Q}$、$n \mapsto n/1$ は環準同型。

**射影：** $\pi: \mathbb{Z} \to \mathbb{Z}/n\mathbb{Z}$、$a \mapsto [a]$ は環準同型（全射）。

**評価写像：** $\mathrm{ev}_c: R[x] \to R$、$f \mapsto f(c)$（$c \in R$ 固定）は環準同型。

---

## 整域と体の関係

### 定義：整域

可換環 $R$ が**整域**であるとは、$R$ に零因子が存在しないことをいう。すなわち

$$a \cdot b = 0 \Rightarrow a = 0 \text{ または } b = 0$$

**例：** $\mathbb{Z}$、$\mathbb{Q}$、$\mathbb{R}$、$\mathbb{C}$、$\mathbb{Z}/p\mathbb{Z}$（$p$ 素数）は整域。$\mathbb{Z}/6\mathbb{Z}$ は整域でない（$[2]\cdot[3]=[0]$）。

### 命題5：体は整域

体は整域である。

**証明.**

体 $F$ で $ab = 0$、$a \neq 0$ とする。$a$ の逆元 $a^{-1}$ が存在するから $b = 1 \cdot b = (a^{-1}a)b = a^{-1}(ab) = a^{-1} \cdot 0 = 0$。$\square$

> **逆は有限の場合のみ成立：** 有限整域は必ず体である（証明は元の有限性を使う）。無限の場合は逆が成立しない—反例：$\mathbb{Z}$ は整域だが体でない。
