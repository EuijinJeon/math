# 3장 도입 + 3.1 Path kernels and insertions — 문단별 해설

원문: `build/sections/trees.tex` 앞부분, PDF 6–8쪽. 번호는 PDF 기준 (식 (3.1)–(3.6), Lemma 3.1).

3장은 논문 전체의 **계산 도구**입니다. power mean 재귀에 함수 하나를 "삽입"했을 때 생기는 변화를 유한 나무 위의 기대값으로
쓰는 미적분입니다. 4장 (보간), 6장 (Palm·Taylor 추출), 7장 (계수 합), 8장 (로그 비교)이 모두 여기 결과를 씁니다.

수치 확인은 $L=2$ 장난감 계 (깊이 1 보조 변수 $z\in\{0,1,2\}$, 무작위 사전확률 $P_1$, 스핀 $N=2$, 무작위 양의 가중치
$w(z,\sigma)$, $m_1=0.4$)에서 기울인 커널을 정확히 계산해 수행했습니다.

---

## 문단 1. 3장 도입

> A power-mean insertion admits two expansions. The logarithmic expansion will compare pressures; an
> expansion with one canceled replica factor will extract the perturbation identities. Both follow from
> one differentiation rule on trees. We also bound their coefficients and the probability of exceptional
> branching depths. Power-mean calculations for hierarchical trial laws appear in Mézard–Parisi [MP01,
> Appendix A] and Panchenko–Talagrand [PT04, Section 5]; the latter uses cascade weights introduced by
> Ruelle [Ruelle87]. Here we derive the needed identities directly for finite sequences of arbitrary
> probability kernels, without assuming an infinite hierarchy.

### 해석

| 도구 | 쓰는 곳 |
|---|---|
| 로그 전개 (Lemma 3.2) | pressure 비교: 4장 (4.3), 8장 명제 8.3 |
| canceled-anchor 전개 (Lemma 3.3) | 섭동 항등식: 6장 (6.14)–(6.17), 7장 |
| 계수 합 (Lemma 3.4, 3.5) | 7장의 부호 합·절댓값 합 제어 |
| 갈라짐 깊이 분포 (Lemma 3.6) | 8장 (8.5): 깊이 평균 → $Q_k$ 평균 |

물리 문헌은 Ruelle cascade (Poisson–Dirichlet 가중치의 위계)를 쓰지만, 여기서는 **임의의 유한 확률 커널 열**로
직접 계산합니다. Ruelle cascade가 필요 없다는 것이 이 접근의 장점입니다.

---

## 문단 2. 경로와 깊이

> Fix an integer $L\geq1$ and numbers $0=m_0<m_1<\cdots<m_{L-1}<m_L=1$. A path has depths $0,\ldots,L$. Its
> depth-zero variable is the root. For $1\leq d\leq L$, the probability kernel $K_d$ draws the next variable
> given the whole prefix through depth $d-1$; $\mathscr F_d$ is the prefix sigma-field. The root
> distribution is fixed throughout all insertions. In an $r$-level application, $L=r+1$: depths
> $1,\ldots,r$ carry auxiliary variables, and depth $L$ carries a Gibbs spin configuration. For the trial
> law (2.7) with $r\ge1$, $\eta_d$ is the depth-$d$ variable for $0\le d<r$, and $x$ is the depth-$r$
> variable.

### 해석

| 깊이 | 변수 (실제 계) | 변수 (시험 법칙 (2.7)) |
|---|---|---|
| 0 (뿌리) | 물리 무질서 (quenched) | $\eta_0$ |
| $1..r$ | 보조 변수 (5장 이후: 섭동 표시) | $\eta_1,\dots,\eta_{r-1},x$ |
| $L=r+1$ | 스핀 배치 $\sigma$ | 스핀 (잎마다 $q_x$) |

$m_0=0$, $m_L=1$로 고정: 뿌리는 quenched ($m=0$), 마지막 스핀 적분은 보통의 Gibbs 평균 ($m=1$).

---

## 문단 3. 유한 나무

> A finite tree $\mathcal T$ consists of a common root and finitely many labeled paths, each ending at depth
> $L$. Every internal vertex has at least one child; in particular, all unary portions of paths are
> retained. At each vertex, different children are drawn independently using the appropriate kernel. We
> write $E_{\mathcal T}$ for this sampling expectation conditional on the root. A split at depth $d$ means
> that the last common vertex is at depth $d$. Replica positions at depth $L$ are distinct vertices, but
> the values sampled there need not differ. Thus independent spin replicas may be the same spin
> configuration. Removing some leaves and the portions of their paths unused by the remaining leaves
> preserves the sampling law of the remaining tree.

### 해석

- 잎 = replica. 두 replica가 깊이 $d$에서 갈라진다 = 깊이 $d$ 상태까지 같고 그 아래는 독립.
- 홑자식 부분을 남겨 두는 이유: 나중에 새 경로가 **홑자식 꼭짓점에서 갈라지는** 것을 셀 때 그 꼭짓점이 필요합니다
  (계수 $m_d-m_{d+1}=-\delta$, 3.3절).
- 사영 일관성: 잎을 지워도 남은 잎들의 법칙이 같음 — 6–8장에서 "쓰지 않는 가지는 적분하면 1"로 계속 사용.

### 물리적 의미

나무는 replica들의 **상태 계보**입니다. 같은 깊이-$d$ 꼭짓점을 공유한 replica는 같은 깊이-$d$ 상태 (cluster)에 있습니다.
Parisi 위계에서 두 replica의 overlap이 $q_d$인 것이 "깊이 $d$에서 갈라짐"에 해당합니다.

---

## 문단 4. multi-overlap (3.1)

> When the terminal variables are spin configurations $\sigma^a\in\{-1,1\}^N$, the multioverlap on a subset
> $S$ of the replica leaves is
> $$R_S=\frac1N\sum_{i=1}^N\prod_{a\in S}\sigma_i^a,\qquad R_\varnothing=1.\tag{3.1}$$
> An unspecified expectation $\mathbb E$ below includes the root and the sampling of the indicated tree.

### 해석

$|S|=2$이면 보통의 overlap $R_{12}$. $|S|\ge3$은 고차 상관이고, 한 자리 replica 패턴 분포의 Walsh 계수입니다 (1장 문단 6).

---

## 문단 5. 기울인 커널 (3.2)

> Here is how the path kernels arise from a partition function. Let $P_d$, $1\le d<L$, be the auxiliary
> prior kernels, put $X_{L-1}=\log Z$, and recursively set $X_{d-1}=m_d^{-1}\log P_de^{m_dX_d}$ $(1\le d<L)$.
> The corresponding *tilted kernels* are
> $$K_d(dz\mid\mathscr F_{d-1})=e^{m_d(X_d(z)-X_{d-1})}P_d(dz\mid\mathscr F_{d-1}),\qquad1\le d<L.\tag{3.2}$$
> They are probability kernels by the recursion. The final kernel $K_L$ is the Gibbs distribution of the
> spin configuration conditional on its auxiliary prefix. When $L=1$, only this final kernel is present.

### 검증

$\int K_d=e^{-m_dX_{d-1}}P_de^{m_dX_d}=e^{-m_dX_{d-1}}e^{m_dX_{d-1}}=1$. ✓ $X_0$가 (2.10)의 $\log T_0Z$에 해당.

### 물리적 의미

$X_d$는 깊이 $d$ 상태의 (Monasson) 로그 분배함수, $K_d\propto P_d\,e^{m_dX_d}=P_d\,Z_d^{m_d}$는 **상태를 $Z^m$으로 재가중한
상태 선택 확률**입니다. 1RSB에서 상태 무게 $W_\alpha\propto Z_\alpha$를 Poisson–Dirichlet$(m)$로 고르는 것과 같은 통계를,
유한 사전 커널에서 $Z^m$ 기울기로 구현한 것입니다.

---

## 문단 6. 삽입 재귀 (3.3)과 갱신 커널 (3.4)

> For a positive path function $A$, define
> $$Y_L=A,\qquad Y_{d-1}=\bigl(K_dY_d^{m_d}\bigr)^{1/m_d},\qquad d=L,\ldots,1.\tag{3.3}$$
> We initially suppose that $A$ is bounded above and away from zero, conditionally on the root. Every
> expression below is then well defined. Denote the kernels after insertion by
> $$K_d^A(dz\mid\mathscr F_{d-1})=\left(\frac{Y_d(z)}{Y_{d-1}}\right)^{m_d}K_d(dz\mid\mathscr F_{d-1}).\tag{3.4}$$
> The recursion shows that these are probability kernels. Superscript $A$ on a tree expectation means that
> these kernels are used.

### 해석

$A$ = 스핀 가중치에 곱하는 인자 (clause 하나, 섭동 하나, 새 스핀 등). $Y_d$는 기울인 커널로 계산한 $A$의 위계 power mean,
$K^A$는 $A$를 넣은 뒤의 새 기울인 커널. $\int K_d^A=Y_{d-1}^{-m_d}K_dY_d^{m_d}=1$. ✓

---

## 문단 7. Lemma 3.1 (Insertion calculus)

> **Lemma 3.1.** Suppose a leaf partition function is iterated by power means, with exponents
> $m_1,\ldots,m_{L-1}$, and $K_1,\ldots,K_{L-1}$ are its tilted kernels. Let $K_L$ be its terminal Gibbs
> kernel. Multiplying each spin weight by $A$ changes the iterated root logarithm by $\log Y_0$, where (3.3)
> uses the kernels before insertion. The new kernels are (3.4).
>
> For an internal vertex $\beta$ of a prescribed tree, let $d_\beta$ be its depth, let $n_\beta$ be its number
> of children, and put $\gamma_\beta=m_{d_\beta}-n_\beta m_{d_\beta+1}$. The conditional joint density of its
> updated tree law is
> $$W_{\mathcal T}(A):=\frac{dP_{\mathcal T}^A}{dP_{\mathcal T}}=\prod_{a\in\mathrm{Leaves}(\mathcal T)}A^a\prod_{\beta\in\mathrm{Int}(\mathcal T)}Y_\beta^{\gamma_\beta}.\tag{3.5}$$
> Here $Y_\beta$ is $Y_{d_\beta}$ evaluated on the prefix at $\beta$.
>
> The recursion is monotone and homogeneous: if $a\leq A\leq b$, for positive root-measurable $a,b$, then
> $a\leq Y_d\leq b$ at every depth; and multiplying $A$ by a positive root-measurable constant multiplies
> every $Y_d$ by that constant.

> *Proof.* At the terminal spin integration, the partition-function ratio is $K_LA=Y_{L-1}$, because
> $m_L=1$. If $X_d$ and $X_d^A$ are the old and new backward logarithms, substitution in the preceding
> power mean gives $\exp(m_d(X_{d-1}^A-X_{d-1}))=K_d\exp(m_d(X_d^A-X_d))$. Backward induction proves
> $X_d^A-X_d=\log Y_d$ and then gives (3.4); the same formula at $d=L$ is the usual Gibbs density ratio.
>
> Multiply the edge density ratios in (3.4) over the tree. An internal vertex at positive depth $d$ receives
> exponent $m_d$ from its incoming edge and exponent $-n_\beta m_{d+1}$ from its outgoing edges. At the root
> there is no incoming edge, which agrees with $m_0=0$. Each terminal vertex receives exponent $m_L=1$. This
> proves (3.5). Monotonicity and homogeneity follow at once by backward induction in (3.3).

### 검증

- $X_{L-1}^A-X_{L-1}=\log\frac{\sum_\sigma wA}{\sum_\sigma w}=\log K_LA=\log Y_{L-1}$. ✓
- $e^{m_dX_{d-1}^A}=P_de^{m_dX_d^A}=P_de^{m_dX_d}e^{m_d\log Y_d}=e^{m_dX_{d-1}}K_dY_d^{m_d}$ ⇒ $X_{d-1}^A-X_{d-1}=\log Y_{d-1}$. ✓
- 새 기울인 커널: $e^{m_d(X_d^A-X_{d-1}^A)}P_d=(Y_d/Y_{d-1})^{m_d}K_d$ = (3.4). ✓
- (3.5): 경로를 따라 간선 비 $(Y_d/Y_{d-1})^{m_d}$를 곱하면, 꼭짓점 $\beta$ (깊이 $d$)에서 $Y_d$의 지수는 들어오는 간선 $+m_d$,
  나가는 간선 $n_\beta$개에서 각 $-m_{d+1}$ ⇒ $\gamma_\beta$. 잎은 $Y_L^{m_L}=A$. ✓

### 수치 확인

| 확인 | 값 |
|---|---|
| $X_0^A-X_0$ (직접) vs $\log Y_0$ ($A=1+0.3D$, $D$ 무작위) | $0.019000105041551$ vs $0.019000105041551$ ✓ |
| (3.5), 깊이 1에서 갈라지는 잎 2개 나무: $E^A_{\mathcal T}[F]$ vs $E_{\mathcal T}[FW]$ | $0.288132548563$ vs $0.288132548563$ ✓ |
| (3.5), 깊이 0에서 갈라지는 나무 | $0.318295007422$ vs $0.318295007422$ ✓ |

($F$는 두 잎의 $(z,\sigma)$에 대한 무작위 함수. 깊이 1 나무: $W=A^aA^bY_0^{-m}Y_1^{m-2}$, 깊이 0 나무: $W=A^aA^bY_0^{-2m}Y_1^{m-1}Y_1'^{\,m-1}$.)

### 물리적 의미

clause 하나를 넣으면 (i) 자유에너지가 $\log Y_0$만큼 바뀌고 — cavity 증분 — (ii) **상태들의 무게도 다시 가중**됩니다
($K^A$). 단순한 Gibbs 평균에서는 $\log\langle A\rangle$이지만, RSB에서는 상태마다 $\langle A\rangle_\alpha$를 $m$제곱으로 재가중하는
$\log(\sum_\alpha W_\alpha\langle A\rangle_\alpha^m)^{1/m}$ 꼴이 됩니다. 이것이 Mézard–Parisi의 "reweighting" 항입니다.

> (작업 중 — 다음 문단부터 이어짐)
