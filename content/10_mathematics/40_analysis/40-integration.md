+++
title = "積分"
weight = 40
date = 2026-08-19
+++

[ノート：微分](10_mathematics/40_analysis/30-differentiation/)を踏まえ、リーマン積分を定義する。面積という直感的な積分のイメージを分割・リーマン和・上下積分という厳密な枠組みに乗せ、ダルブーの可積分条件によって可積分性を特徴づける。微積分学の基本定理によって微分と積分が逆演算の関係にあることを示す。


---

{{< toc >}}

---

## リーマン積分の定義

### 分割とリーマン和

$[a, b]$ の**分割**とは、有限個の点の列

$$P = \{a = x_0 < x_1 < \cdots < x_n = b\}$$

のことをいう。各小区間 $[x_{i-1}, x_i]$ の幅を $\Delta x_i := x_i - x_{i-1}$ と書く。分割 $P$ の**幅**を $\|P\| := \max_i \Delta x_i$ で定める。

有界関数 $f: [a,b] \to \mathbb{R}$ と分割 $P$ に対して、各小区間上の上限・下限を

$$M_i := \sup_{x \in [x_{i-1}, x_i]} f(x), \qquad m_i := \inf_{x \in [x_{i-1}, x_i]} f(x)$$

と定め、**上和**・**下和**を

$$U(f, P) := \sum_{i=1}^{n} M_i \Delta x_i, \qquad L(f, P) := \sum_{i=1}^{n} m_i \Delta x_i$$

で定める。$m_i \leq M_i$ だから $L(f, P) \leq U(f, P)$ が常に成り立つ。

### 上積分・下積分

分割を細かくするほど上和は減少し、下和は増加する。より正確には、

**補題：** $P' \supseteq P$（$P'$ が $P$ の細分）ならば、 $L(f,P) \leq L(f,P') \leq U(f,P') \leq U(f,P)$。

**証明.** 点を一つ付け加えた場合に上和が減少しないことを示せば十分。小区間 $[x_{i-1}, x_i]$ に点 $x^*$ を加えると、

$$M_i \Delta x_i = M_i(x^* - x_{i-1}) + M_i(x_i - x^*) \geq \sup_{[x_{i-1},x^*]} f \cdot (x^* - x_{i-1}) + \sup_{[x^*,x_i]} f \cdot (x_i - x^*)$$

下和も同様。$\square$

**補題：** 任意の分割 $P, P'$ に対して $L(f, P) \leq U(f, P')$。

**証明.** $P'' = P \cup P'$ とおくと $P'' \supseteq P$ かつ $P'' \supseteq P'$ だから、$L(f,P) \leq L(f,P'') \leq U(f,P'') \leq U(f,P')$。$\square$

よって、上和全体は下に有界、下和全体は上に有界であるから、完備性より以下が定義できる。

**定義：上積分・下積分**

$$\overline{\int_a^b} f(x)\,dx := \inf_P U(f, P) , \qquad　\underline{\int_a^b} f(x)\,dx := \sup_P L(f, P)$$

補題より常に $\underline{\int_a^b} f \leq \overline{\int_a^b} f$ が成り立つ。

### リーマン積分の定義

$$\overline{\int_a^b} f(x)\,dx = \underline{\int_a^b} f(x)\,dx$$

が成り立つとき、$f$ は $[a,b]$ 上で**リーマン積分可能**であるといい、この共通の値を

$$\int_a^b f(x)\,dx$$

と書く。

---

## ダルブーの可積分条件

上積分と下積分が一致するかどうかを、分割の言葉で直接判定できる。

### 定理1：ダルブーの可積分条件

有界関数 $f: [a,b] \to \mathbb{R}$ がリーマン積分可能であることは、以下と同値である：

$$\forall \varepsilon > 0, \exists \text{ 分割 } P; U(f, P) - L(f, P) < \varepsilon$$

**証明（$\Rightarrow$）** $\overline{\int} f = \underline{\int} f =: I$ とする。$\varepsilon > 0$ に対し、上積分・下積分の定義より

$$U(f, P_1) < I + \varepsilon/2 , \quad L(f, P_2) > I - \varepsilon/2 $$

となる分割 $P_1, P_2$ が存在する。$P = P_1 \cup P_2$ とおくと細分の補題より

$$U(f,P) - L(f,P) \leq U(f,P_1) - L(f,P_2) < \varepsilon.$$

**証明（$\Leftarrow$）** 任意の $\varepsilon > 0$ に対し $U(f,P) - L(f,P) < \varepsilon$ となる $P$ が存在するとする。

$$0 \leq \overline{\int} f - \underline{\int} f \leq U(f,P) - L(f,P) < \varepsilon$$

$\varepsilon > 0$ は任意だから $\overline{\int} f = \underline{\int} f$。$\square$

### 定理2：連続関数は可積分

$f: [a,b] \to \mathbb{R}$ が連続ならばリーマン積分可能である。

**証明.** $f$ は $[a,b]$ 上で連続だから、最大値定理より有界。また有界閉区間上の連続関数は一様連続である（ハイネ=カントールの定理）。すなわち、

$$\forall \varepsilon > 0, \exists \delta > 0, \forall x, y \in [a,b]; |x-y| < \delta \Rightarrow |f(x)-f(y)| < \frac{\varepsilon}{b-a}$$

$\|P\| < \delta$ となる分割 $P$ をとると、各小区間で $M_i - m_i < \varepsilon/(b-a)$ だから

$$U(f,P) - L(f,P) = \sum_{i=1}^n (M_i - m_i)\Delta x_i < \frac{\varepsilon}{b-a} \sum_{i=1}^n \Delta x_i = \varepsilon$$

ダルブーの可積分条件より $f$ は可積分。$\square$

---

## 積分の基本性質

### 定理3：線形性

$f, g$ が $[a,b]$ 上で可積分、$c \in \mathbb{R}$ とする。

$$\int_a^b (f+g)\,dx = \int_a^b f\,dx + \int_a^b g\,dx, \qquad \int_a^b cf\,dx = c\int_a^b f\,dx$$

**証明.** 上和・下和の線形性から従う。$\square$

### 定理4：単調性

$f \leq g$ が $[a,b]$ 上で成り立ち、$f, g$ が可積分ならば

$$\int_a^b f\,dx \leq \int_a^b g\,dx$$

**証明.** $m_i(f) \leq m_i(g)$ だから $L(f,P) \leq L(g,P)$。下積分をとれば結論を得る。$\square$

### 定理5：区間の分割

$f$ が $[a,b]$ 上で可積分、$c \in (a,b)$ とする。

$$\int_a^b f\,dx = \int_a^c f\,dx + \int_c^b f\,dx$$

**証明.** $c$ を含む分割を考えると、上和・下和が区間ごとに分解できることから従う。$\square$

### 積分の記法の拡張

$b < a$ のとき $\int_a^b f\,dx := -\int_b^a f\,dx$、$\int_a^a f\,dx := 0$ と定める。定理5は $a, b, c$ の大小関係によらず成立する。

---

## 微積分学の基本定理

### 定理6：微積分学の基本定理（第1形式）

$f: [a,b] \to \mathbb{R}$ が連続とする。$F(x) := \int_a^x f(t)\,dt$ と定めると、$F$ は $[a,b]$ 上で微分可能であり

$$F'(x) = f(x)$$

が成り立つ。

**証明.** $h > 0$ のとき（$h < 0$ も同様）、

$$\frac{F(x+h) - F(x)}{h} = \frac{1}{h}\int_x^{x+h} f(t)\,dt$$

$f$ は $[x, x+h]$ 上で連続だから最大値・最小値 $M(h), m(h)$ をもつ（最大値定理）。すなわち、区間 $[x, x+h]$ 上の任意の $t$ について $m(h) \leq f(t) \leq M(h)$ が成り立つ。
ここで積分の単調性（定理4）を適用すると、

$$\int_x^{x+h} m(h) \,dt \leq \int_x^{x+h} f(t)\,dt \leq \int_x^{x+h} M(h) \,dt$$

が得られる。定数の積分は上和・下和の定義から直ちに $\int_x^{x+h} c \,dt = ch$ と計算できるため、

$$m(h) \cdot h \leq \int_x^{x+h} f(t)\,dt \leq M(h) \cdot h$$

となる。辺々を $h > 0$ で割って、

$$m(h) \leq \frac{1}{h}\int_x^{x+h} f(t)\,dt \leq M(h)$$

$h \to 0$ のとき $f$ の連続性より $M(h), m(h) \to f(x)$。はさみうちの原理より

$$\lim_{h \to 0} \frac{F(x+h)-F(x)}{h} = f(x). \quad \square$$

### 定理7：微積分学の基本定理（第2形式）

$f: [a,b] \to \mathbb{R}$ が連続、$G$ が $[a,b]$ 上で $G' = f$ を満たすとする（$G$ を $f$ の**原始関数**という）。このとき

$$\int_a^b f(x)\,dx = G(b) - G(a)$$

**証明.** $F(x) = \int_a^x f(t)\,dt$ とおくと定理6より $F' = f$。$G' = f$ と合わせて $(G-F)' = 0$。定数関数の特徴より $G - F = C$（定数）。$F(a) = 0$ だから $C = G(a)$、よって

$$\int_a^b f(x)\,dx = F(b) = G(b) - C = G(b) - G(a). \quad \square$$

> **微積分学の基本定理の意義：** 第1形式は「積分を微分すると元の関数に戻る」、第2形式は「原始関数が分かれば積分が計算できる」という二つの事実を述べている。微分と積分が逆演算の関係にあることが、この定理によって示された。

---

## 定理の依存関係

```
完備性（上限性質）
        ↓
上積分・下積分の存在
        ↓
リーマン積分の定義
        ↓
ダルブーの可積分条件　　最大値定理・一様連続性
                            ↓
                       連続関数は可積分
                            ↓
                　微積分学の基本定理（第1形式）
                            ↓
            （微分の）平均値定理・定数関数の特徴づけ
                            ↓
              　  微積分学の基本定理（第2形式）
```
