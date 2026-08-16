+++
title = "数体系の構成（ℤ・ℚ）"
weight = 60
date = 2026-08-11
+++

$\omega$ を出発点に、整数 $\mathbb{Z}$ と有理数 $\mathbb{Q}$ を集合論的に構成する。いずれも不足している演算（減法・除法）を同値類で補うという共通のアイデアに基づく。各ステップで well-definedness を丁寧に確認する。

---

{{< toc >}}

---

## 構成のアイデア

$\omega$ には加法と乗法があるが、減法（$3 - 5$ のような）と除法（$1 \div 3$ のような）は定義できない。これらを拡張によって補う。

**整数 $\mathbb{Z}$：** $a - b$ という差をペア $(a, b) \in \omega \times \omega$ で表し、同じ差を持つペアを同一視する。

**有理数 $\mathbb{Q}$：** $a \div b$ という比をペア $(a, b) \in \mathbb{Z} \times (\mathbb{Z} \setminus \\{0\\})$ で表し、同じ比を持つペアを同一視する。

いずれも、同値関係による商集合の構成（[ノート：同値関係・同値類・商集合](10_mathematics/20_set-theory/30-equivalence/)）である。

---

## 整数 $\mathbb{Z}$ の構成

### 同値関係の定義

$\omega \times \omega$ 上の関係を次で定める。

$$(a, b) \sim (c, d) \iff a + d = b + c$$

これは $a - b = c - d$ の言い換えである（$\omega$ では減法が定義されていないため、この形で書く）。

**同値関係の確認：**

- **反射律:** $a + b = b + a$（加法の可換律）。$\checkmark$
- **対称律:** $a + d = b + c \Rightarrow c + b = d + a$。$\checkmark$
- **推移律:** $a + d = b + c$ かつ $c + f = d + e$ と仮定する。辺々加えると $a + d + c + f = b + c + d + e$。両辺から $c + d$ を消去して $a + f = b + e$。$\checkmark$

### 整数の定義

$$\mathbb{Z} := (\omega \times \omega) / {\sim}$$

ペア $(a, b)$ の同値類 $[(a,b)]$ を「$a - b$」と読む。具体例：

$$0_\mathbb{Z} = [(0,0)] = \{(0,0),(1,1),(2,2),\ldots\}$$

$$1_\mathbb{Z} = [(1,0)] = \{(1,0),(2,1),(3,2),\ldots\}$$

$$-1_\mathbb{Z} = [(0,1)] = \{(0,1),(1,2),(2,3),\ldots\}$$

$$2_\mathbb{Z} = [(2,0)] = \{(2,0),(3,1),(4,2),\ldots\}$$

> **直観的イメージ：** $\mathbb{Z}$ の各同値類は、格子平面 $\omega \times \omega$ において「傾き 1 の平行な半直線」の上に乗っている格子点の集まりとして視覚化できる。

### 加法・乗法の定義と well-definedness

**加法：**

$$[(a,b)] + [(c,d)] := [(a+c,\; b+d)]$$

**乗法：**

$$[(a,b)] \times [(c,d)] := [(ac+bd,\; ad+bc)]$$

乗法の式は $(a-b)(c-d) = (ac+bd)-(ad+bc)$ という分配則の言い換えである。

**加法の well-definedness：**

$(a,b) \sim (a',b')$ すなわち $a+b'=b+a'$、および $(c,d) \sim (c',d')$ すなわち $c+d'=d+c'$ を仮定する。

$$(a+c)+(b'+d') = (a+b')+(c+d') = (b+a')+(d+c') = (b+d)+(a'+c')$$

よって $(a+c,b+d) \sim (a'+c',b'+d')$。$\square$

**乗法の well-definedness：**

$a+b'=b+a'$ より $a-b=a'-b'$（差として等しい）、同様に $c-d=c'-d'$。$\omega$ 上の等式として展開する：

$$(ac+bd)+(a'd'+b'c') = ac+bd+a'd'+b'c'$$

$$(ad+bc)+(a'c'+b'd') = ad+bc+a'c'+b'd'$$

$a+b'=b+a'$ および $c+d'=d+c'$ を用いて両辺が等しいことを確認できる（計算は $\omega$ の加法・乗法の可換律・分配律を使う）。

よって $(ac+bd,ad+bc) \sim (a'c'+b'd',a'd'+b'c')$。$\square$

---

## 有理数 $\mathbb{Q}$ の構成

### 同値関係の定義

$\mathbb{Z} \times (\mathbb{Z} \setminus \\{0\\})$ 上の関係を次で定める：

$$(a, b) \sim (c, d) \iff a \times d = b \times c$$

これは $\dfrac{a}{b} = \dfrac{c}{d}$ の言い換えである（$\mathbb{Z}$ では除法が定義されていないため、この形で書く）。ここで $\times$ は整数の乗法である。

**同値関係の確認：**

- **反射律:** $a \times b = b \times a$（乗法の可換律）。$\checkmark$
- **対称律:** $a \times d = b \times c \Rightarrow c \times b = d \times a$。$\checkmark$
- **推移律:** $ad = bc$ かつ $cf = de$ を仮定する（$b, d, f \neq 0$）。第1式に $f$、第2式に $b$ を掛けると $adf = bcf$ かつ $bcf = bde$。よって $adf = bde$。$d \neq 0$ だから両辺を $d$ で割って $af = be$、すなわち $(a,b) \sim (e,f)$。$\checkmark$

> **注意:** 推移律の証明で$d$ で割る操作を行っているが、これは $\mathbb{Z}$ 上では整数の乗法の消去則（$d \neq 0$ かつ $xd = yd \Rightarrow x = y$、整数環の整域性）として正当化される。

### 有理数の定義

$$\mathbb{Q} := (\mathbb{Z} \times (\mathbb{Z} \setminus \{0\})) / {\sim}$$

ペア $(a,b)$ の同値類 $[(a,b)]$ を $\dfrac{a}{b}$ と書く。具体例：

$$\frac{1}{2} = [(1,2)] = \{(1,2),(2,4),(3,6),(-1,-2),\ldots\}$$

$$\frac{0}{1} = [(0,1)] = \{(0,1),(0,2),(0,3),\ldots\}$$

$$\frac{-1}{3} = [(-1,3)] = \{(-1,3),(-2,6),(1,-3),\ldots\}$$

> **直観的イメージ：** $\mathbb{Q}$ の各同値類は、格子平面 $\mathbb{Z} \times \mathbb{Z}$ において「原点と $(b, a)$ を結ぶ直線（傾き $a/b$）」の上に乗っている格子点の集まりとして視覚化できる。（ただし $b=0$ の Y軸は除く）。

### 加法・乗法の定義と well-definedness

**加法：**

$$\frac{[(a,b)] + [(c,d)]}{[(ad+bc, bd)]} := \left[\left(ad+bc,\; bd\right)\right]$$

（通分 $\dfrac{a}{b} + \dfrac{c}{d} = \dfrac{ad+bc}{bd}$ の言い換え。$b, d \neq 0$ より $bd \neq 0$。）

**乗法：**

$$[(a,b)] \times [(c,d)] := [(ac,\; bd)]$$

（$\dfrac{a}{b} \times \dfrac{c}{d} = \dfrac{ac}{bd}$ の言い換え。）

**加法の well-definedness：** 

$(a,b) \sim (a',b')$ すなわち $ab'=ba'$、および $(c,d) \sim (c',d')$ すなわち $cd'=dc'$ を仮定する。

$(ad+bc, bd) \sim (a'd'+b'c', b'd')$ を示す。すなわち $(ad+bc) \cdot b'd' = bd \cdot (a'd'+b'c')$ を確認する。

$$(ad+bc)b'd' = adb'd' + bcb'd'$$

$$bd(a'd'+b'c') = bda'd' + bdb'c'$$

$ab' = ba'$ より $adb'd' = bda'd'$、$cd' = dc'$ より $bcb'd' = bdb'c'$。よって両辺は等しい。$\square$

**乗法の well-definedness：**

$(ac)(b'd') = ac \cdot b'd'$ と $(bd)(a'c') = bd \cdot a'c'$ を比較する。

$ab'=ba'$ および $cd'=dc'$ より $acb'd' = a'c'bd$。$\square$

---

## 数体系の構成の連鎖

```
空集合の公理・無限の公理・分出公理図式
        ↓
        ω（自然数）　加法・乗法：再帰的定義
        ↓ ω×ω の差による同値類
        ℤ（整数）　　加法・乗法：同値類上に定義、well-defined を確認
        ↓ ℤ×(ℤ\{0}) の比による同値類
        ℚ（有理数）　加法・乗法：同値類上に定義、well-defined を確認
```

$\omega \to \mathbb{Z} \to \mathbb{Q}$ はいずれも**代数的構成**であり、不足している演算を同値類で補うという同じ構造を持つ。この先 $\mathbb{Q} \to \mathbb{R}$ へ進むには、有理数直線の穴を埋めるための位相的概念（極限・完備性）が必要になる。
