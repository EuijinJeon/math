# 3.2 The two expansion rules — 문단별 해설

원문: `build/sections/trees.tex` 3.2절, PDF 8–10쪽. 번호는 PDF 기준 (식 (3.7)–(3.11), Lemma 3.2, 3.3).
앞 절 참조: Lemma 3.1 (3.5), (3.6).

수치 확인은 3.1절과 같은 $L=2$ 장난감 계 (깊이 1 $z\in\{0,1,2\}$, 스핀 $N=2$, $m_1=0.4$)와, 확장 이력을 정확한 유리수로
열거하는 프로그램으로 했습니다.

---

## 문단 1. 보호된 잎과 미분 규칙

> Call a leaf *protected* if its factor $A^a$ in the tree density is canceled by a denominator $A^a$. For a
> set $C$ of protected leaves and a bounded parameter-independent function $G$, consider
> $E_{\mathcal T}^A[G\prod_{a\in C}(A^a)^{-1}]$. Differentiating (3.5) shows that
> $$\partial_{t_j}\log W_{\mathcal T}(A)=\sum_{a\in\mathrm{Leaves}(\mathcal T)}\frac{D_j^a}{A^a}+\sum_{\beta\in\mathrm{Int}(\mathcal T)}\gamma_\beta\,\partial_{t_j}\log Y_\beta.$$
> In the derivative of $E_{\mathcal T}^A[G\prod_{a\in C}(A^a)^{-1}]$, the leaf terms at $a\in C$ cancel exactly
> with differentiation of their denominators. Each remaining leaf term inserts $D_j^a/A^a$ and makes that
> leaf protected. By (3.6), an internal-vertex term is the same expectation after adjoining an independent
> updated path below $\beta$, with an additional factor $D_j/A$ at its terminal vertex. This is precisely a
> fresh path at $\beta$, with coefficient $\gamma_\beta$, and its new leaf is protected. Conditional
> independence of children and the projectivity of tree sampling justify this representation even when $G$
> uses the other children of $\beta$.

### 해석 — 규칙 표

$E^A_{\mathcal T}[\,\cdot\,]=E_{\mathcal T}[\,\cdot\,W]$이므로 미분은 $\log W$의 미분을 곱하는 것입니다.

| $\partial\log W$의 항 | 결과 |
|---|---|
| 보호된 잎 $a\in C$의 $D^a/A^a$ | 분모 $1/A^a$의 미분 $-D^a/A^a$와 정확히 상쇄 → **0** |
| 보호 안 된 잎 $a$의 $D^a/A^a$ | 그 잎에 $D/A$를 붙이고 보호 (계수 **+1**) |
| 내부 꼭짓점 $\beta$의 $\gamma_\beta\partial\log Y_\beta$ | (3.6)으로 $\beta$ 아래 새 경로 하나에 $D/A$ (계수 **$\gamma_\beta$**), 새 잎은 보호 |

### 검증

$\partial\log W=\sum_aD^a/A^a+\sum_\beta\gamma_\beta\partial\log Y_\beta$: (3.5)의 로그를 미분. ✓
$\partial[G\prod_{C}(A^a)^{-1}W]=G\prod_C(A^a)^{-1}W[\partial\log W-\sum_{C}D^a/A^a]$ ⇒ $C$의 잎 항 상쇄. ✓
$\partial\log Y_\beta=E^A[D/A\mid\mathscr F_{d_\beta}]$는 $\beta$의 접두부에서 독립인 새 경로 하나의 기대값 — 그 경로를 $\beta$의 새 자식으로
나무에 붙인 것과 같습니다 (자식들의 조건부 독립 + 사영 일관성). ✓

### 물리적 의미

$\gamma_\beta=m_d-n_\beta m_{d+1}$은 "replica를 하나 더 붙일 때 그 replica가 깊이 $d$ 상태 $\beta$ 안에서 **새 하위 상태**로 들어가는
가중치"입니다. 음수일 수 있다는 점 ($n_\beta m_{d+1}>m_d$)이 replica 계산의 "$n\to0$에서 음의 가중치"를 연상시킵니다.

---

## 문단 2. 텔레스코핑 (3.7)과 나무 법칙 $Q_k$ (3.8)

> For a tree with $n$ leaves, telescoping gives the useful identity
> $$\sum_{\beta\in\mathrm{Int}(\mathcal T)}\bigl(n_\beta m_{d_\beta+1}-m_{d_\beta}\bigr)=n.\tag{3.7}$$
> All summands are positive. Define a probability law $Q_k$ on trees with leaves labeled $1,\ldots,k$ as
> follows. Start with a single path. When the current tree has $n$ leaves, choose an internal vertex $\beta$
> with probability
> $$\frac{n_\beta m_{d_\beta+1}-m_{d_\beta}}{n},\tag{3.8}$$
> create a fresh child there, and continue with a completely new path to depth $L$. Give its terminal vertex
> label $n+1$. Identity (3.7) verifies the normalization. The random tree is chosen independently of all
> variables subsequently sampled on it. For example, under $Q_2$ the two paths split at depth $d$ with
> probability $m_{d+1}-m_d$, for $0\le d<L$. This split is uniform on the depths when $m_d=d/L$.

### 검증

**(3.7)**: 깊이 $d$의 꼭짓점들에 대해 $\sum_{\beta:d_\beta=d}n_\beta=\#\{\text{깊이 }d+1\text{ 꼭짓점}\}=:v_{d+1}$. 따라서
$\sum_\beta(n_\beta m_{d+1}-m_d)=\sum_{d=0}^{L-1}(v_{d+1}m_{d+1}-v_dm_d)=v_Lm_L-v_0m_0=n\cdot1-1\cdot0=n$. ✓
양수성: $n_\beta\ge1$, $m_{d+1}>m_d$. ✓
**$Q_2$**: 한 경로에서 깊이 $d$ 꼭짓점 (홑자식)을 고를 확률 $(m_{d+1}-m_d)/1$. ✓

### 수치 확인

| 확인 | 결과 |
|---|---|
| (3.7), 무작위 나무 ($L=4,9$; 잎 2, 4, 6개) | 합이 각각 정확히 2, 4, 6 ✓ |
| $Q_2$의 갈라짐 깊이 ($L=6$) | 모든 깊이에서 $1/6$ (균등) ✓ |
| $Q_k$ 전체 확률 ($k=3,4$, 여러 $L$) | 정확히 1 (3.4절 참조) ✓ |

### 물리적 의미

보조 층이 하나 ($L=2$)이면 $Q_k$는 "새 replica가 크기 $s$인 기존 상태에 들어갈 확률 $(s-m)/n$, 새 상태를 만들 확률 $cm/n$"인
**Chinese restaurant process CRP$(m,0)$** — Ruelle cascade (Poisson–Dirichlet$(m)$)에서 replica들의 상태 공유 통계입니다.
$L$층이면 그 위계 버전이고, $m_d=d/L$, $L\to\infty$에서는 Bolthausen–Sznitman 합류과정의 계보가 됩니다.

---

## 문단 3. Lemma 3.2 (Logarithmic expansion)

> **Lemma 3.2.** For a bounded real path function $D$ and $A=1+tD$,
> $$\log Y_0=\sum_{k\geq1}\frac{(-1)^{k-1}t^k}{k}\mathbb E_{Q_k}E_{\mathcal T}\prod_{a=1}^kD^a,\qquad|t|\|D\|_\infty<1.\tag{3.9}$$
> This identity is conditional on the root. If $|t|\|D\|_\infty\leq c<1$, the absolute value of the remainder
> after order $K$ is at most
> $$\sum_{k>K}\frac{c^k}{k}.\tag{3.10}$$

> *Proof.* The first derivative is, by (3.6), the expectation of $D/A$ on one updated path. Protect that leaf.
> Every subsequent derivative can only add a fresh path, because all current leaves are protected. At order
> $k$, all $k-1$ fresh coefficients are negative. After normalization by (3.7), their absolute products are
> $(k-1)!$ times the probabilities in $Q_k$. Therefore
> $$\left.\frac{d^k}{dt^k}\log Y_0\right|_{t=0}=(-1)^{k-1}(k-1)!\,\mathbb E_{Q_k}E_{\mathcal T}\prod_{a=1}^kD^a.$$
> Analyticity proves (3.9); the coefficients have absolute value at most $\|D\|_\infty^k/k$, which proves the
> stated convergence domain and (3.10).

### 검증

- 1차: $\partial\log Y_0=E^A[D/A]$ (경로 하나, 보호됨). ✓
- 이후: 보호 안 된 잎이 없으므로 새 경로만 붙고, 계수 $\gamma_\beta=-(n_\beta m_{d+1}-m_d)<0$. $n$개 잎일 때 선택의 절댓값
  합이 $n$ (3.7) ⇒ $k-1$번 붙인 후 절댓값 곱의 합 $=1\cdot2\cdots(k-1)=(k-1)!$, 각 이력의 몫은 정확히 $Q_k$ 확률. ✓
- $t=0$에서 $A=Y=1$ ⇒ $\frac{d^k}{dt^k}\log Y_0|_0=(-1)^{k-1}(k-1)!\mathbb E_{Q_k}E_{\mathcal T}\prod D^a$, Taylor 계수 $\frac{(-1)^{k-1}}k\cdots$. ✓
- 계수 크기 $\le\|D\|^k/k$ ⇒ (3.10). ✓

### 물리적 의미

$L=1$ (위계 없음)이면 모든 replica가 뿌리에서 갈라지므로 $\mathbb E_{Q_k}E_{\mathcal T}\prod D^a=\langle D\rangle^k$, (3.9)는
$\log(1+t\langle D\rangle)$의 보통 Taylor 전개입니다. 위계가 있으면 $\langle D\rangle^k$ 대신 **CRP로 뽑은 상태 공유 패턴 위의
$k$-replica 상관**이 들어갑니다. 4장 (4.3)과 8장 명제 8.3이 이 전개를 차수별로 비교합니다.

### 수치 확인 ($L=2$ 장난감, $Q_k$를 CRP로 정확 열거)

| $t$ | 부분합 $K=5$ | $K=10$ | $K=40$ | 직접 계산 $\log Y_0$ | 꼬리 한계 (3.10), $K=10$ |
|---|---|---|---|---|---|
| 0.3 | 0.019000188175 | 0.019000105043 | 0.019000105042 | 0.019000105042 | $2.2\times10^{-7}$ |
| 0.9 | 0.044667075931 | 0.044586370038 | 0.044585898739 | 0.044585898739 | $0.18$ |

급수가 직접 계산값으로 수렴하고, 실제 오차는 (3.10)의 한계 안에 있습니다. ✓

---

## 문단 4. 동반 규칙: 옛 replica가 있는 확장

> Here is the companion rule with old replicas. Fix a tree $\mathcal T$ with an anchor leaf $a_*$. Starting from
> all its old paths, assign colors $1,\ldots,k$ in that order. For the next color, one may either
> (i) choose an unused old leaf other than $a_*$, with coefficient $1$; or
> (ii) create a fresh path from any internal vertex $\beta$ of the current tree, with coefficient
> $\gamma_\beta=m_{d_\beta}-n_\beta m_{d_\beta+1}$.
> Each fresh path uses a new child at its divergence vertex and new vertices at every greater depth. Every
> chosen leaf receives its color and cannot be chosen again. The current tree includes all old paths,
> including unused ones, and every path already added. An extension history $E$ records these choices;
> write $a_j(E)$ for the leaf carrying color $j$, $\mathcal T_E$ for its final tree, and $c_E$ for the product of
> its coefficients.

### 해석

문단 1의 규칙을 그대로 쓰되, 처음에는 anchor 하나만 보호된 상태에서 시작합니다. 그러면 보호 안 된 옛 잎이 있으므로
(i)이 가능합니다. "현재 나무"는 쓰지 않은 옛 경로도 포함 — $n_\beta$를 셀 때 그 경로들도 자식으로 셉니다.

| 기호 | 의미 |
|---|---|
| anchor $a_*$ | 분모 $A^{a_*}$로 보호된 잎 (6장에서 섭동 점수를 재는 replica) |
| 색 $j$ | $j$번째 미분 $\partial_{t_j}$가 놓이는 잎 |
| 이력 $E$ | 색마다 고른 선택의 열 |
| $c_E$ | 계수의 곱 |

---

## 문단 5. Lemma 3.3 (Canceled-anchor expansion)

> **Lemma 3.3.** Let $H$ be a bounded function of the variables on the old tree, fixed as the insertion
> parameters vary. For $A_{\boldsymbol t}=1+\sum_{j=1}^kt_jD_j$, with bounded real path functions $D_j$, one has
> $$\left.\partial_{t_1}\cdots\partial_{t_k}E_{\mathcal T}^{A_{\boldsymbol t}}\frac{H}{A_{\boldsymbol t}^{a_*}}\right|_{\boldsymbol t=0}=\sum_Ec_E\,E_{\mathcal T_E}\left[H\prod_{j=1}^kD_j^{a_j(E)}\right].\tag{3.11}$$
> The formula holds in any fixed order of the colors. For identical directions $D_j=D$, the coefficient of
> $t^k$ is the right-hand side divided by $k!$. The analytic bounds established above apply to its left-hand
> side, uniformly over the path kernels. The empty extension has weight $1$.

> *Proof.* Begin with $C=\{a_*\}$ and $G=H$. Apply the preceding rule successively, incorporating each new
> $D_j$ in $G$. Fresh leaves are protected immediately, so the only unprotected leaves are unused old
> leaves. At zero all factors $A$ and $Y$ are $1$, proving the claimed rule and its coefficients.

### 검증

규칙을 $k$번 적용 ($t_1$부터 순서대로). 매번 새로 붙은 $D_j/A$를 $G$에 넣고 그 잎을 보호. $\boldsymbol t=0$에서 $A=Y=1$이므로
남는 것은 $c_E\,E_{\mathcal T_E}[H\prod D_j]$. ✓ 같은 방향이면 $\partial_t^k=\sum$ (모든 색 순서가 같은 항) ⇒ $[t^k]=\frac1{k!}\partial_t^k$. ✓

### 수치 확인 (혼합 도함수 유한 차분 vs 확장 합)

old tree = anchor $a$ + 옛 잎 $b$, $H$ = 두 잎의 $(z,\sigma)$에 대한 무작위 함수, $D_1,D_2$ 무작위. 좌변은 갱신 커널 (3.4)로
정확히 계산한 함수의 중심 차분, 우변은 모든 확장 이력을 열거해 각 최종 나무에서 기대값을 계산:

| old tree | $k$ | 좌변 (유한 차분) | 우변 (확장 합) | 이력 수 |
|---|---|---|---|---|
| 깊이 1에서 갈라짐 | 1 | $-0.19799682$ | $-0.19799682$ | 3 |
| 깊이 1에서 갈라짐 | 2 | $-0.01869436$ | $-0.01869436$ | 9 |
| 깊이 0에서 갈라짐 | 1 | $-0.12388507$ | $-0.12388507$ | 4 |
| 깊이 0에서 갈라짐 | 2 | $-0.01197914$ | $-0.01197914$ | 16 |

✓ ($k=1$, 깊이 1 나무의 이력 3개 = 옛 잎 $b$ (계수 1), 뿌리에서 새 경로 ($0-1\cdot m$), 깊이 1 꼭짓점에서 새 경로 ($m-2$).)

### 물리적 의미

6장에서 $H$에는 옛 replica들의 관측량 $f$와 anchor의 섭동 점수가 들어갑니다. (3.11)은 "섭동을 하나 더 넣은 계에서 잰 상관"을
**원래 계에서 replica를 덧붙인 나무들의 부호 있는 합**으로 바꿉니다. GG 항등식이 바로 이런 형태의 식입니다 (6.5절 문단 2의
$L=1$ 계산).

---

## 요약

- 미분 규칙: 보호된 잎은 상쇄, 보호 안 된 잎은 계수 1, 내부 꼭짓점은 새 경로 계수 $\gamma_\beta=m_d-n_\beta m_{d+1}$.
- 텔레스코핑 (3.7)로 $Q_k$ (3.8)가 확률 법칙이 됨 — 한 층이면 CRP$(m,0)$.
- Lemma 3.2: $\log Y_0=\sum\frac{(-1)^{k-1}t^k}k\mathbb E_{Q_k}E_{\mathcal T}\prod D^a$, 꼬리 $\sum c^k/k$. 수치로 확인.
- Lemma 3.3: anchor를 보호한 상태의 혼합 도함수 = 확장 이력의 부호 있는 합. 수치로 확인.

**다음 절 예고**: 3.3절에서 확장 계수의 부호 있는 합 (Lemma 3.4, $\kappa(S)$)과 절댓값 합 (Lemma 3.5)을 계산합니다.
