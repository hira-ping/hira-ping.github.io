+++
title = "一階述語論理の記法と推論規則"
weight = 10
date = 2026-08-06
lastmod = 2026-08-23
+++

数学の各分野の証明を読む際に、「この推論ステップは本当に正当化されるのか」という疑問に立ち返るためのリファレンス。一階述語論理の記法と推論規則をダイジェストとしてまとめる。形式的な体系の詳細（モデル、健全性・完全性定理など）は続きのノートで扱う（予定）。

---

{{< toc >}}

---

## 命題論理

命題論理とは、命題記号を最小の単位とするシンプルな論理体系である。個々の命題記号が表す具体的な主張（例えば、「0<1」「5は偶数である」など）には立ち入らず、その命題記号が真であるか偽であるかの情報のみに注目する。

### 定義：命題論理の論理式
- **命題記号:** $p, q, r, \dots$
- **論理記号:** $\neg, \land, \lor, \rightarrow$（それぞれ「...でない」「かつ」「または」「ならば」と読む）

上記の記号と適宜カッコを用いて、以下の規則に従い再帰的に構成される記号列を**命題論理の論理式**という。

1. 命題記号一つからなる記号列は論理式である。
2. $\phi$ が論理式であるとき、$(\neg \phi)$ は論理式である（**否定**という）。
3. $\phi$ および $\psi$ が論理式であるとき、$(\phi \land \psi), (\phi \lor \psi), (\phi \rightarrow \psi)$は論理式である（それぞれ、**論理積**、**論理和**、**含意**という）。

### カッコの省略ルール
上の定義に従うとカッコが多くなり読みにくくなるため、解釈の一意性をそこなわない範囲で以下のルールに従いカッコを省略する。

1. もっとも外側のカッコは省略してよい。
2. $\neg$ の範囲は、カッコで明示されない限り、もっとも狭くとらえる。
3. 規則(2)を適用した上で、$\land, \lor$ の適用範囲は、カッコで明示されない限り、もっとも狭くとらえる。
4. $\phi \land \psi \land \rho$ は、$\phi \land (\psi \land \rho)$の略記とみなす。これは $(\phi \land \psi) \land \rho$ と等しいため、括弧を省略した表記が正当化される。
5. $\phi \lor \psi \lor \rho$ は、$\phi \lor (\psi \lor \rho)$の略記とみなす。これは $(\phi \lor \psi) \lor \rho$ と等しいため、括弧を省略した表記が正当化される。

---

ある命題記号の真偽をその命題記号の**真理値**といい、真をT、偽をFで表す。

### 定義：命題論理の論理式の真偽
論理式$\phi, \psi$の真理値の組み合わせに応じて、$\neg \phi, \phi \land \psi, \phi \lor \psi, \phi \rightarrow \psi$ の真理値を下表に従い再帰的に定める。

**否定 ($\neg$)**

| $\phi$ | $\neg \phi$ |
| :---: | :---: |
| T | F |
| F | T |

**論理積 ($\land$)、論理和 ($\lor$)、含意 ($\rightarrow$)**

| $\phi$ | $\psi$ | $\phi \land \psi$ | $\phi \lor \psi$ | $\phi \rightarrow \psi$ |
| :---: | :---: | :---: | :---: | :---: |
| T | T | T | T | T |
| T | F | F | T | F |
| F | T | F | T | T |
| F | F | F | F | T |

$(\phi \rightarrow \psi) \land (\psi \rightarrow \phi)$であることを、$\phi \leftrightarrow \psi$ とも表す。このとき、$\phi$と$\psi$は同値であるという。

**同値 ($\leftrightarrow$)**

| $\phi$ | $\psi$ | $\phi \leftrightarrow \psi$ |
| :---: | :---: | :---: |
| T | T | T |
| T | F | F |
| F | T | F |
| F | F | T |

### 定義：論理的含意、論理的同値
論理式$\phi, \psi$に含まれる命題記号の真理値のすべての組み合わせを考える。

- $\psi$が真であるような真理値の組み合わせすべてについて、$\phi$の真理値が真となる場合、$\psi$は$\phi$を**論理的に含意する**といい、$\psi \vDash \phi$ と表す。
- $\psi \vDash \phi$ かつ $\phi \vDash \psi$、すなわち$\phi$と$\psi$の真理値がすべて一致する場合、$\phi$と$\psi$は**論理的に同値**であるといい、$\phi \equiv \psi$ と表す。

> **記号の使い分け：$\vDash$ と $\vdash$**
>
> このノートでは、真理値の意味論的な関係を $\vDash$（二重の縦棒）で表し、形式証明による構文論的な導出を $\vdash$（一本の縦棒）で表す。前者は「すべての真理値の組み合わせを考えたとき常に成り立つ」という意味論的な主張であり、後者は「推論規則の適用によって実際に導けた」という構文論的な主張である。健全性定理と完全性定理により、一階述語論理ではこの二つは一致する（$\Gamma \vDash \phi \Leftrightarrow \Gamma \vdash \phi$）。

### 定義：トートロジー
論理式$\phi$に含まれる命題記号の真理値のすべての組み合わせについて$\phi$の真理値が真となる場合、$\phi$を**トートロジー**という。

トートロジーは、各命題記号の内容を考えるまでもなく、文の形式から正しいと判断できる。
$\psi \vDash \phi$ であることと、論理式 $\psi \rightarrow \phi$ がトートロジーであることは同値である。同様に、$\phi \equiv \psi$ であることと、論理式$\phi \leftrightarrow \psi$ がトートロジーであることも同値である。

---

## 一階述語論理の文法

命題変数の具体的な主張がどのように構成されるかを見ていく。

命題論理のみで表現される主張（たとえば「$p \rightarrow q$ かつ $q \rightarrow r$ ならば、$p \rightarrow r$ である」）も立派な数学的主張であるが、それだけでは現代の数学の議論を十分に記述することはできない。
命題論理だけでは表現しきれない数学的主張を記述するために、命題論理の体系に個々の対象（モノ）と対象が満たす性質や関係を記述するための語彙（量化記号など）を導入し、より表現豊かにした論理体系が一階述語論理である。

### 定義：一階述語論理の論理式
一階述語論理の論理式を、以下のステップに従い再帰的に定義する。

- **ステップ1：記号の定義**
  定数記号、変数記号、関数記号、述語記号を定める。
- **ステップ2：項の定義**
  変数記号や定数記号、それらに関数記号を適用して得られるものを項と定義する。項は何らかの対象を指し示す表現であり、論理式（真偽をもつ主張）とは異なる。
  > **例:** 整数の言語を考えるとき、定数記号 $0$、変数 $x, y$、関数記号 $+, \times$ を用いると、$0$、$x$、$x+y$、$x \times (y + 0)$ はいずれも項である。一方、「$x > 0$」は真偽をもつ論理式であり、項ではない。
- **ステップ3：原始論理式の定義**
  項$t_1, \dots, t_n$とn個の引数をとる述語記号$P_n$に対して、$P_n(t_1, \dots, t_n)$は論理式である。これを**原始論理式**という。
- **ステップ4：論理式の再帰的定義**
  - 論理式$\phi, \psi$に対して、否定($\neg \phi$)、論理積($\phi \land \psi$)、論理和($\phi \lor \psi$)、含意($\phi \rightarrow \psi$)は論理式である。
  - 論理式$\phi$および変数$v$に対して、全称量化($\forall v, \phi$)、存在量化($\exists v, \phi$)は論理式である。

命題論理では、命題論理の具体的な主張には立ち入らず、命題を、単に「真」「偽」のふたつの値のみ意味としてもつ変数として考えた。そして、その変数を、否定、論理積、論理和、含意を意味する記号で組み合わせたものを命題論理の論理式と定義したのである。

では、命題変数の具体的な中身となる一階述語論理の真偽は何によって定まるのだろうか。
一般に、数学の主張は、その主張の文言だけで決まるのではなく、解釈の土台となる数学的構造に依存する。

> **例:** 「$x^2 = 2$となる$x$が存在する」という主張は、解釈の土台となる数学的構造が実数であれば真であるが、有理数であれば偽になる。また、「すべての$A, B$について、$AB=BA$である」という主張は、一般の行列を考えれば偽であるが、考える範囲を対角行列に限れば真になる。

数学的構造は、多くの場合、集合の上に、何かしらの要素の指定（定数）や演算（関数）、関係（述語）を与えたものになる。この数学的構造をストラクチャーやモデルという概念で抽象化し、一階述語論理の主張に真か偽かの意味を与える。この詳細は、続きのノートで扱う（予定）。

数学の具体的な分野を理解していく上では、考えている数学の分野ごとに、その主張が成立するかどうかを以下のように素朴に判断すれば問題ない。

### 論理式の素朴な解釈
上記で定義された論理式は、以下のように解釈される。

- **原始論理式 ($P(t_1, \dots, t_n)$):** $P$が表す性質や関係について、対象$t_1, \dots, t_n$がその性質を満たす、またはその関係が成り立つという基本的な主張を表す。
  > **例:** 整数を考えている場合、「3は8より小さい」という主張は真であり、「5は偶数である」という主張は偽である。
- **否定 ($\neg \phi$):** 「$\phi$ではない」という主張が真であることを意味する。
- **論理積 ($\phi \land \psi$):** 「$\phi$と$\psi$の両方」が真であることを意味する。
- **論理和 ($\phi \lor \psi$):** 「$\phi$と$\psi$の少なくとも一方」が真であることを意味する。
- **含意 ($\phi \rightarrow \psi$):** 「$\phi$が真であるならば、$\psi$も真である」ことを意味する。（$\phi$が偽である場合は、この主張全体は真とみなされる。）
- **全称量化 ($\forall v, \phi$):** 考えている範囲のすべての対象$v$について、$\phi$が真であることを意味する。
- **存在量化 ($\exists v, \phi$):** 考えている範囲に、$\phi$を真にするような対象$v$が少なくとも一つ存在することを意味する。

一階述語論理で記述された数学的主張が真であることがどういうことかは、いったんこれで分かったことにする（実際には、集合論の言葉で厳密に記述される）。

---

## 推論規則のまとめ

形式証明を構成する際に使える規則と公理を体系的にまとめる。ここでは、どのような規則が使えるかを整理することに主眼を置く。これらの規則を用いた実際の証明の書き方は、次節「証明の形式」で扱う。

### 基本的な公理
- **モーダスポンネス (公理):** $\phi$ および $\phi \rightarrow \psi$ から、$\psi$ を結論する。
- **トートロジー (公理):** 命題論理のトートロジーの各命題記号を論理式に置き換えたものは、公理となる。

### 二重否定の除去
$\vdash \neg \neg \phi \leftrightarrow \phi$。

この規則は量化記号の中であっても適用できる（量化記号を越えて適用できる）。具体的には以下のような同値性が成り立つ。
- $\vdash \forall v, (\neg \neg \phi) \leftrightarrow \forall v, \phi$
- $\vdash \exists v, (\neg \neg \phi) \leftrightarrow \exists v, \phi$

### 等号に関する規則
等号 $=$ は特別な二項述語として扱われ、以下の公理と規則が成り立つ。

- **反射律 (公理):** $\vdash v=v$
- **対称律:** $\vdash \forall v, \forall w, (v=w \rightarrow w=v)$
- **推移律:** $\vdash \forall v, \forall w, \forall u, ((v=w \land w=u) \rightarrow v=u)$
- **代入原理 (公理):** $\vdash v=w \rightarrow(\alpha[v/u] \rightarrow \alpha[w/u])$ （$\alpha$は原始論理式）
- **代入原理 (一般形):** 項$t_1, t_2, u$と変数$v$、論理式$\phi$について以下が成り立つ。
  - $\vdash t_1=t_2 \rightarrow u[t_1/v] = u[t_2/v]$
  - $\vdash t_1=t_2 \rightarrow (\phi[t_1/v] \leftrightarrow \phi[t_2/v])$

### 量化記号に関するカッコの省略ルール（一階述語論理への拡張）

命題論理における省略ルールに加え、一階述語論理における量化記号（$\forall, \exists$）の適用範囲（スコープ）について、解釈の曖昧さを防ぐため以下の規約を追加する。

1. **量化記号の結合優先度:** 量化記号 $\forall x, \exists x$ は、否定 $\neg$ と同程度に強く結合し、$\land, \lor, \rightarrow$ などの二項論理結合子よりも優先される。
   - 例：$\forall x, P(x) \land Q$ は、$(\forall x, P(x)) \land Q$ の略記とみなす。全体に量化を及ぼしたい場合は、$\forall x, (P(x) \land Q)$ とカッコを明示する。
2. **量化記号の連続:** 量化記号が連続する場合、中間のカッコは省略してよい。
   - 例：$\forall x, (\forall y, P(x, y))$ は、$\forall x, \forall y, P(x, y)$ と略記する。

> **注:** この規約により、例えば $\exists e,(\forall z, z \notin e \land e \in x)$ と記述した場合でも、$\forall z$ のスコープは $z \notin e$ までで切れることが構文的に確定する。ただし、視認性を高めるために $\exists e,(\forall z, (z \notin e) \land e \in x)$ とあえてカッコを補うことは許容される。

### 量化記号に関する規則
量化記号の導入・除去に関わる中心的な規則をまとめる。$\phi[t/v]$ は論理式 $\phi$ 中の変数 $v$ を項 $t$ で置き換えた論理式を表す。

- **全称例化 (公理):** $\vdash \forall v, \phi \rightarrow \phi[t/v]$ （ただし、項$t$は$\phi$中の$v$に代入可能）
  - 特別な場合として $\vdash \forall v, \phi \rightarrow \phi$ が成り立つ（全称量化記号の単純な除去）。
- **全称汎化 (公理):** $\vdash \phi \rightarrow \forall v, \phi$ （ただし、$v$は$\phi$に自由出現しない）
- **存在例化:** 定数記号$c$が$\Gamma, \phi, \psi$のいずれにも出現しないとき、「$\Gamma \cup \\{\phi[c/v]\\} \vdash \psi$」ならば「$\Gamma \cup \\{\exists v, \phi\\} \vdash \psi$」が言える。
- **存在汎化:** $\vdash \phi[t/v] \rightarrow \exists v, \phi$
- **定数の一般化:** 定数記号$c$が$\Gamma$のどの論理式にも出現しないとき、「$\Gamma \vdash \phi[c/v]$」ならば「$\Gamma \vdash \forall v, \phi$」が言える。
- **束縛変数の取り替え:** 論理式$\phi$は、束縛変数の選び方だけが異なる同値な論理式$\phi'$に置き換え可能である。($\vdash \phi \leftrightarrow \phi'$)

### 量化記号に関する諸法則
量化記号の相互変換や分配に関する重要な法則をまとめる。

**ドモルガンの法則**

量化記号に関するドモルガンの法則は、全称と存在を否定によって相互に変換する。直感的には、「すべての $v$ について $\phi$ でない」ことと「$\phi$ を満たす $v$ が存在しない」ことは同じ意味であり、「ある $v$ について $\phi$ でない」ことと「$\phi$ がすべての $v$ について成り立つわけではない」ことも同値である。

- $\vdash \forall v, \neg \phi \leftrightarrow \neg(\exists v, \phi)$ (公理)
- $\vdash \forall v, \phi \leftrightarrow \neg(\exists v, \neg \phi)$
- $\vdash \exists v, \neg \phi \leftrightarrow \neg(\forall v, \phi)$
- $\vdash \exists v, \phi \leftrightarrow \neg(\forall v, \neg \phi)$

**量化記号の分配則**

量化記号と論理記号がどのように相互作用するかを表す法則である。全称量化記号は論理積と相性がよく（双方向に分配できる）、存在量化記号は論理和と相性がよい。一方、それ以外の組み合わせでは一方向の包含関係しか成り立たないことに注意する。

- $\vdash \forall v, (\phi \rightarrow \psi) \rightarrow (\forall v, \phi \rightarrow \forall v, \psi)$ (公理)
- $\vdash \forall v, (\phi \land \psi) \leftrightarrow (\forall v, \phi \land \forall v, \psi)$
- $\vdash (\forall v, \phi \lor \forall v, \psi) \rightarrow \forall v, (\phi \lor \psi)$
- $\vdash (\exists v, \phi \rightarrow \exists v, \psi) \rightarrow \exists v, (\phi \rightarrow \psi)$
- $\vdash \exists v, (\phi \lor \psi) \leftrightarrow (\exists v, \phi \lor \exists v, \psi)$
- $\vdash \exists v, (\phi \land \psi) \rightarrow (\exists v, \phi \land \exists v, \psi)$

> **覚え方**
>
> $\exists x,(P(x) \land Q(x)) \rightarrow \left( \exists x,P(x) \land \exists x,Q(x) \right)$。
> だけ記憶しておけば、あとは対称的に考えていけば導ける。

**全称と存在の順序関係**

- $\vdash \forall v, \phi \rightarrow \exists v, \phi$
- $\vdash \exists v, \forall w, \phi \rightarrow \forall w, \exists v, \phi$

> **注:** 逆向き $\vdash \forall w, \exists v, \phi \rightarrow \exists v, \forall w, \phi$ は一般には成立しない。たとえば実数上で「任意の $x$ に対してある $y$ が存在して $y > x$」は真だが、「すべての $x$ より大きい $y$ が一つ存在する」は偽である。量化記号の順序には常に注意が必要である。

---

## 証明の形式

推論規則を踏まえた上で、実際に証明がどのような形式で構成されるかを定義し、具体例を示す。

### 定義：形式証明

論理式の有限列 $\phi_1, \phi_2, \dots, \phi_n$ であって、各 $\phi_i$ が以下のいずれかを満たすものを、前提集合 $\Gamma$ からの**形式証明**という。

1. $\phi_i$ は公理（命題論理のトートロジー、等号の公理、量化記号の公理）である。
2. $\phi_i \in \Gamma$ である（前提の一つ）。
3. ある $j, k < i$ が存在して $\phi_k = (\phi_j \rightarrow \phi_i)$ であり、モーダスポネンスにより導かれる。

$\phi_n$ を証明の**結論**という。前提集合 $\Gamma$ からの $\phi_n$ の形式証明が存在するとき $\Gamma \vdash \phi_n$ と表し、「$\Gamma$ は $\phi_n$ を**導出する**」という。$\Gamma = \emptyset$ のとき $\vdash \phi_n$ と書く。

### 実際の証明の書き方

実際の数学ではすべてのステップを列記する形式証明は煩雑であるため、以下の証明戦略を組み合わせた**半形式的な証明**が用いられる。

- **含意の証明（演繹定理の利用）:** $\phi \rightarrow \psi$ を示すには、$\phi$ を仮定し $\psi$ を導けばよい。
- **全称命題の証明（一般化定理の利用）:** $\forall v, \phi$ を示すには、$\Gamma$ に現れない新しい定数 $c$ を取り $\phi[c/v]$ を示せばよい。
- **存在命題の証明（存在汎化の利用）:** $\exists v, \phi$ を示すには、具体的な項 $t$ を与えて $\phi[t/v]$ を示せばよい。
- **存在前提の利用（存在例化の利用）:** 前提 $\exists v, \phi$ を使うには、以前に出現しない新しい定数 $c$ を取り、$\phi[c/v]$ を仮定して推論を進めてよい。
- **場合分け（論理和の利用）:** $\phi \lor \psi$ を仮定して $\chi$ を示すには、$\phi$ を仮定した場合と $\psi$ を仮定した場合に分け、それぞれ $\chi$ を示せばよい。

---

## 主要な証明法と定理
- **演繹定理:** $\Gamma \cup \\{\gamma\\} \vdash \phi$ ならば、 $\Gamma \vdash \gamma \rightarrow \phi$ である。
- **一般化定理:** $\Gamma \vdash \phi$ であり、かつ$\Gamma$のどの論理式にも変数$v$が自由出現しないならば、$\Gamma \vdash \forall v, \phi$ である。
- **対偶法:** $\Gamma \cup \\{\phi\\} \vdash \neg \psi$ と $\Gamma \cup \\{\psi\\} \vdash \neg \phi$ は同値である。
- **背理法:** $\Gamma \cup \\{\neg \phi\\}$ が矛盾（ある論理式$\alpha$について $\Gamma \vdash \alpha \land \neg \alpha$ であること）するならば、$\Gamma \vdash \phi$ である。
- **トートロジーに関する規則:** $\\{\psi_1, \dots, \psi_n\\}$ がトートロジー的に $\phi$ を含意し、かつ各 $\Gamma \vdash \psi_i$ であるなら、$\Gamma \vdash \phi$ である。

---

## 日本語の数学的主張と論理式の対応

数学の文章に現れる日本語表現と、それに対応する論理式のパターンをまとめる。

### 基本的な対応

| 日本語表現 | 論理式 |
| :--- | :--- |
| $P$かつ$Q$ | $P \land Q$ |
| $P$または$Q$ | $P \lor Q$ |
| $P$ならば$Q$ | $P \rightarrow Q$ |
| $P$でない | $\neg P$ |
| $P$のとき、かつそのときに限り$Q$ | $P \leftrightarrow Q$ |
| すべての$x$について$P(x)$ | $\forall x, P(x)$ |
| ある$x$が存在して$P(x)$ | $\exists x, P(x)$ |
| $P(x)$を満たす$x$はただ一つ存在する | $\exists! x, P(x)$ |

### 複合的な表現

| 日本語表現 | 論理式 |
| :--- | :--- |
| $P$でないならば$Q$でない（$P \rightarrow Q$の対偶） | $\neg Q \rightarrow \neg P$ |
| すべての$x$について$P(x)$でない | $\forall x, \neg P(x)$ |
| $P(x)$を満たす$x$は存在しない | $\neg \exists x, P(x)$ |
| 任意の$x$に対して、ある$y$が存在して$P(x,y)$ | $\forall x, \exists y, P(x, y)$ |
| $P(x,y)$を満たす$x, y$の組が存在する | $\exists x, \exists y, P(x, y)$ |
| $P(x)$ならば$Q(x)$であるような$x$が存在する | $\exists x, (P(x) \rightarrow Q(x))$ |
| $P(x)$かつ$Q(x)$であるような$x$が存在する | $\exists x, (P(x) \land Q(x))$ |
| すべての$x$について、$P(x)$ならば$Q(x)$ | $\forall x, (P(x) \rightarrow Q(x))$ |

---

## 量化記号への条件付け

量化記号の直後に条件を付ける略記がよく使われる。展開すると以下のようになる。

| 略記 | 展開形 |
| :--- | :--- |
| $\forall x \in A, \phi(x)$ | $\forall x,(x \in A \rightarrow \phi(x))$ |
| $\exists x \in A, \phi(x)$ | $\exists x,(x \in A \land \phi(x))$ |

$\forall$ と $\exists$ で論理記号が異なることに注意：全称量化では条件が含意（$\rightarrow$）で結ばれ、存在量化では論理積（$\land$）で結ばれる。直感的には、$\forall x \in A$ は「$A$ の外の $x$ については何も主張しない」ので含意が自然であり、$\exists x \in A$ は「$A$ の中に条件を満たす $x$ が存在する」ので論理積が自然である。

> **例：$\varepsilon$-$\delta$ 論法による極限の定義**
>
> $\lim_{x \to a} f(x) = L$ の定義は以下のように書かれる。
>
> $$\forall \varepsilon > 0, \exists \delta > 0, \forall x,(0 < |x - a| < \delta \rightarrow |f(x) - L| < \varepsilon)$$
>
> これを略記なしに展開すると、
>
> $$\forall \varepsilon,(\varepsilon > 0 \rightarrow \exists \delta,(\delta > 0 \land \forall x,(0 < |x-a| < \delta \rightarrow |f(x) - L| < \varepsilon)))$$
>
> $\forall \varepsilon > 0$ は含意に、$\exists \delta > 0$ は論理積に展開されていることが確認できる。

---

## 冠頭標準形

一階述語論理の論理式において、すべての量化記号が論理式の先頭に集められた形を**冠頭標準形**という。

$Q_1 v_1, Q_2 v_2, \cdots, Q_n v_n, \phi$

ここで各 $Q_i$ は $\forall$ または $\exists$、$\phi$ は量化記号を含まない論理式（**行列部**という）である。

任意の一階述語論理の論理式は、同値な冠頭標準形に変換できる。変換には以下の同値変換を繰り返し適用する。

冠頭標準形は以下の場面で役立つ。

- **主張の論理構造を把握する:** 量化記号がすべて先頭に集まることで、何を全称的に主張し何を存在的に主張しているかの骨格が一目で見える。「任意の $x$ に対してある $y$ が存在して……さらに任意の $z$ について……」のように量化記号が入り組んだ主張も、冠頭標準形にすれば $\forall x,\exists y,\forall z,\cdots$ と整理される。
- **否定を取る:** 主張の否定を作るとき、冠頭標準形にしてからドモルガンの法則で各量化記号を反転させると機械的に処理できる（$\forall \leftrightarrow \exists$ を反転し、行列部を否定する）。


### 量化記号を外に出す変換規則

$v$ が $\psi$ に自由出現しないとき、以下が成り立つ。

- $\forall v, \phi \land \psi \equiv \forall v,(\phi \land \psi)$
- $\forall v, \phi \lor \psi \equiv \forall v,(\phi \lor \psi)$
- $\exists v, \phi \land \psi \equiv \exists v,(\phi \land \psi)$
- $\exists v, \phi \lor \psi \equiv \exists v,(\phi \lor \psi)$
- $(\forall v, \phi) \rightarrow \psi \equiv \exists v,(\phi \rightarrow \psi)$
- $(\exists v, \phi) \rightarrow \psi \equiv \forall v,(\phi \rightarrow \psi)$
- $\psi \rightarrow (\forall v, \phi) \equiv \forall v,(\psi \rightarrow \phi)$
- $\psi \rightarrow (\exists v, \phi) \equiv \exists v,(\psi \rightarrow \phi)$

> **含意と量化記号の変換に注意:** $(\forall v,\phi) \rightarrow \psi$ を冠頭標準形にすると $\exists v,(\phi \rightarrow \psi)$ となり、$\forall$ が $\exists$ に変わる。これはドモルガンの法則（$\forall v,\phi \equiv \neg\exists v,\neg\phi$）と含意の定義（$\phi \rightarrow \psi \equiv \neg\phi \lor \psi$）から導かれる。

---

## 一意存在量化記号

性質 $P(x)$ を満たす $x$ が「ただ一つ存在する」という命題は、記号 $\exists!$ を用いて $\exists! x, P(x)$ と書き、**一意存在量化記号**と呼ぶ。一階述語論理において、これは $\exists$ と $\forall$ を組み合わせた以下の論理式として定義される。

$$\exists x, (P(x) \land \forall y, (P(y) \to x=y))$$

この論理式には、証明の文脈に応じて使い分けられる同値な表現がいくつか存在する。

### 同値な論理式のバリエーション

**1. 存在と一意性を分離する表現**

$$\exists x, P(x) \land \forall y, \forall z, ((P(y) \land P(z)) \to y=z)$$

前半で「少なくとも1つ存在する」ことを示し、後半で「2つ存在すると仮定すれば、それらは等しい（ゆえに1つである）」ことを示す。実際の数学の証明において、最も標準的かつ直感的に使われるアプローチである。**存在と一意性を独立して確認したいとき**（例：まず構成により存在を示し、次に別議論で一意性を示すとき）に特に有用である。

**2. より簡潔な同値表現**

$$\exists x, \forall y, (P(y) \leftrightarrow x=y)$$

「ある $x$ が存在して、任意の $y$ が性質 $P$ を満たすことと、$y$ が $x$ に等しいことが同値になる」という表現である。存在と一意性が一つの量化記号の下にまとまっており、**論理式を簡潔に書きたいとき**や、その $x$ を明示的に参照しながら議論を進めたいときに使いやすい。

> これらの論理的同値性は、群論において「群の単位元がただ一つであること」や「ある元の逆元が一意であること」を証明する際などに必要な概念である（[ノート：群](40_knowledge-base/10_mathematics/30_algebra/10-groups/#%E5%91%BD%E9%A1%8C1%E5%8D%98%E4%BD%8D%E5%85%83%E3%81%AE%E4%B8%80%E6%84%8F%E6%80%A7)）。