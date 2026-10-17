# 5장 A perturbed cavity reservoir — 문단별 해설

원문: `build/sections/cavity.tex`, PDF 13–14쪽. 식·Lemma 번호는 PDF 기준입니다
(식 (5.1)–(5.7), Lemma 5.1). 앞 장 참조: (2.1), (2.3), (2.4), Lemma 3.1, 명제 4.1.

이 장부터 **아래쪽 한계** $\liminf F_N\ge\inf_r\Phi_r$의 증명이 시작됩니다. 5장은 그 첫 단계로,
$N$ 스핀계와 $N+1$ 스핀계를 공통의 $N$ 스핀계("저장소", reservoir)를 통해 비교하는
Aizenman–Sims–Starr(ASS) 틀을 세웁니다.

---

## 문단 1. 장 도입

> We compare systems of sizes $N$ and $N+1$ through a common $N$-spin system, the *reservoir*.
> This cavity comparison follows the Aizenman–Sims–Starr variational scheme [ASS03] and its
> spin-distribution form in Panchenko [Pan13, Section 2.2]. We add a sublinear number of bounded
> perturbations to obtain identities for its spin trees. The comparison below shows that these
> perturbations change the pressure by $o(1)$ and preserve the site-minus-bond cavity increment.

### 해석

- **ASS 틀**: $F_N=\frac1N\mathbb E\log Z_N$이고
  $\mathbb E\log Z_N=\sum_{n<N}(\mathbb E\log Z_{n+1}-\mathbb E\log Z_n)+\mathbb E\log Z_0$이므로
  $\liminf_NF_N\ge\liminf_N\Delta_N$, $\Delta_N:=\mathbb E\log Z_{N+1}-\mathbb E\log Z_N$
  (Cesàro 평균은 $\liminf$를 낮추지 않음). 그래서 **증분 하나**를 아래에서 누르면 됩니다.
- **증분의 cavity 표현**: $Z_{N+1}$과 $Z_N$을 둘 다 "공통 저장소 + 작은 삽입"으로 쓰면
  $\Delta_N=\log2+\mathbb E\log\langle A_{\rm s}\rangle-\mathbb E\log\langle A_{\rm b}\rangle$이 됩니다.
  site 삽입 $A_{\rm s}$는 새 스핀과 그 clause들, bond 삽입 $A_{\rm b}$는 과다 계산된 clause들입니다.
  이것은 (2.11)의 Bethe 장부 $\log2+V_{\rm s}-\alpha(p-1)V_{\rm e}$와 **같은 모양**이며, 차이는 메시지가
  시험 법칙 대신 저장소의 실제 Gibbs 측도에서 온다는 점뿐입니다.
- **섭동**: 저장소에 $s_N=N^{3/4}$개 정도의 유계 한-자리 인자 $\psi_\nu$를 더합니다. pressure는
  $O(s_N)=o(N)$만 바뀌지만, 저장소의 Gibbs 측도에 "항등식"(6장)을 강제합니다.

### 물리적 의미

물리학의 cavity 방법은 "스핀 하나를 더하고 clause 몇 개를 빼면 자유에너지 밀도가 나온다"는
계산입니다 (Mézard–Parisi 2001). ASS는 이것을 엄밀한 부등식 틀로 만들었습니다. 남는 과제는
"저장소의 Gibbs 측도가 Parisi 위계(Ruelle cascade)처럼 생겼다"는 것을 보이는 일인데, 이것을
위해 Ghirlanda–Guerra 항등식을 유도하는 표준 수단이 **작은 섭동**입니다. SK에서는 $p$-spin
섭동 해밀토니안을 $N^{\gamma}$ 크기로 더하는 것과 같은 역할입니다.

---

## 문단 2. 아래쪽 한계를 위한 가정

> Until Section 9, assume that $B(\theta)\le B$ and $|h|\le H$ almost surely and that the law of
> $\theta$ is invariant under permutations of its $p$ coordinates. Neither the factorization nor
> the positivity assumption is used in the lower bound.

### 해석

| 가정 | 쓰이는 곳 |
|---|---|
| $B(\theta)\le B$, $\lvert h\rvert\le H$ a.s. | 모든 증분·삽입이 균등 유계 → 집중·급수 수렴 |
| $\theta$ 법칙의 좌표 순열 불변성 | 새 스핀이 clause의 어느 자리에 들어가도 법칙이 같음 (문단 6) |
| (2.3) 분해, (2.4) 양성 | **쓰지 않음** (위쪽 한계 전용) |

9장에서 유계 가정을 (2.1)의 1차 모멘트로 완화합니다. 순열 불변성은 원래 모형에서 대칭화
$\theta\mapsto\theta\circ\pi$ ($\pi$ 균등 무작위)를 해도 $H_N$의 법칙이 바뀌지 않으므로
(자리가 i.i.d. 균등) 일반성을 잃지 않는 가정으로 보입니다 — 이 해설의 판단이며, 9장에서 다시 확인합니다.

### 물리적 의미

아래쪽 한계는 "실제 Gibbs 측도가 가질 수밖에 없는 구조"에서 나오므로, 상호작용의 부호 구조
((2.4)는 본질적으로 "좌절(frustration)이 강자성 쪽으로 기울지 않음")와 무관합니다. 반면 위쪽 한계는
보간의 볼록성 항 부호가 필요했습니다 (4장 수치 확인 (c): $b=+0.8$에서 깨짐).

---

## 문단 3. 깊이 격자와 섭동 인자

> Fix $L\ge2$ and use $r=L-1$ auxiliary levels with
> $$m_d=d/L\quad(0\le d\le L),\qquad\delta=1/L.\tag{5.1}$$
> Let $(c_\nu)_{\nu\ge1}$ be positive with $\sum_\nu c_\nu=1$, and let $s_N=N^{3/4}$. To the spin
> weight add independent Poisson families of single-site factors $\psi_\nu$, with counts of means
> $c_\nu s_N$ and independent uniform sites in $[N]$. Each factor uses its own auxiliary variables,
> drawn along the hierarchy with product priors, and satisfies
> $$1/2\le\psi_\nu\le3/2.\tag{5.2}$$
> The total number of factors is $\mathrm{Pois}(s_N)$ and is finite almost surely. Counts, types,
> and sites are root variables. The parameters of the factors are denoted by $\mathbf u$ and are
> fixed, not quenched random variables, unless a parameter average is explicitly taken. The
> factors needed later are specified in Section 6.

### 기호

| 기호 | 의미 |
|---|---|
| $L$, $m_d=d/L$, $\delta=1/L$ | 균등 격자. 3.3절 Lemma 3.5, 3.6이 이 격자를 가정 |
| $\nu$, $c_\nu$ | 섭동의 종류(가산 개)와 그 비율, $\sum c_\nu=1$ |
| $s_N=N^{3/4}$ | 섭동 총 개수의 평균 |
| $\psi_\nu$ | 한 자리 스핀과 자기 보조 변수에 의존하는 양의 인자 |
| $\mathbf u$ | 섭동의 매개변수 (고정; 6장에서 평균) |

### 해석

- **격자를 $m_d=d/L$로 고정하는 이유**: 아래쪽 한계에서는 시험 매개변수 $\mathbf m$을 우리가
  고르는 것이 아니라 저장소가 "보여 주는" 구조를 읽어 내야 합니다. 깊이를 아주 촘촘히 ($L\to\infty$)
  두면 어떤 Parisi 측도도 근사할 수 있고, $L$개 깊이 위에서 평균을 내는 7장의 기법이 쓰입니다.
  (3.3절 끝: 갈라짐을 한 칸 늦추면 부호 합과 절댓값 합이 둘 다 $\delta$.)
- **보조 변수**: 원래 계에는 보조 변수가 없습니다. 섭동 인자 각각이 깊이 $1..r$에 자기 변수
  (3장 요약: "실제로는 섭동이 읽는 Rademacher 부호")를 가지고, 이것이 저장소에 **인공적인 위계**를
  만듭니다. 이 변수들이 power mean 재귀로 기울여지면서 스핀 Gibbs 측도가 깊이별로 "상태"로 쪼개집니다.
- "parameters fixed, not quenched": 6장에서 매개변수 $\mathbf u$에 대해 평균을 취해 항등식을
  얻을 때까지는 결정적 상수로 둡니다.

### 물리적 의미

$\psi_\nu$는 **약한 외부장 섭동**입니다. 보조 변수가 깊이 $d$에 붙어 있다는 것은 "깊이 $d$ 상태
(cluster) 안에서 공유되는 무작위 장"이라는 뜻입니다. 물리적으로는 Parisi의 "real replica"나
Franz–Parisi 결합장처럼 상태의 위계를 드러내 주는 탐침(probe)으로 보면 됩니다.

### 검증

$\mathrm{Pois}(c_\nu s_N)$이 독립이면 합은 $\mathrm{Pois}(\sum_\nu c_\nu s_N)=\mathrm{Pois}(s_N)$
(가산 합도 Poisson 중첩 성질로 성립, 평균이 유한하므로 a.s. 유한). ✓

---

## 문단 4. 섭동된 pressure와 (5.3)

> Apply the power-mean recursion to the resulting leaf partition function. Write
> $P_N^{L,\mathbf u}$ for its expected root logarithm. Comparing pointwise with the unperturbed spin
> weight and then applying the recursion gives
> $$|P_N^{L,\mathbf u}-NF_N|\le(\log2)s_N,\tag{5.3}$$
> uniformly in the hierarchy, its parameters, and $N$.

### 해석과 검증

$P_N^{L,\mathbf u}=\mathbb E\log T_0\bigl(\sum_\sigma e^{-H_N(\sigma)}\prod_{\text{섭동}}\psi\bigr)$.
(5.2)에서 인자마다 $|\log\psi|\le\log2$ ($\log(3/2)<\log2$). 인자가 $n$개이면 점별로
$2^{-n}Z_N\le Z^{\rm pert}\le2^nZ_N$, 이것이 Lemma 3.1의 단조성으로 재귀 후에도 유지됩니다
($Z_N$은 보조 변수와 무관하므로 power mean이 그대로 둡니다). 따라서
$|\log T_0Z^{\rm pert}-\log Z_N|\le n\log2$, 기대값을 취하면 $\mathbb En=s_N$. ✓

**의미**: $s_N/N=N^{-1/4}\to0$이므로 섭동은 pressure 밀도를 바꾸지 않습니다. 그래서
$\liminf F_N=\liminf\frac1NP_N^{L,\mathbf u}$이고, 섭동된 계로 ASS를 해도 됩니다.

---

## 문단 5. Lemma 5.1 (Cavity increments)

> **Lemma 5.1 (Cavity increments).** The increments
> $\Delta_N^{L,\mathbf u}=P_{N+1}^{L,\mathbf u}-P_N^{L,\mathbf u}$ are uniformly bounded in
> $N,L,\mathbf u$. There is a reservoir on $N$ spins with physical interaction count of mean
> $$\rho_N=\alpha(N+1)\left(\frac{N}{N+1}\right)^p,\tag{5.4}$$
> the usual fields, and the perturbation counts of means $c_\nu s_N$, such that
> $$\Delta_N^{L,\mathbf u}=\log2+\mathbb E\log Y_{0,\rm s}-\mathbb E\log Y_{0,\rm b}+o_N(1).\tag{5.5}$$
> The error is uniform in $L,\mathbf u$. The insertion recursion uses the tilted reservoir kernels
> and independent new root disorder, with terminal insertions
> $$A_{\rm s}(\sigma)=\frac12\sum_{\varepsilon=\pm1}\exp\left(h\varepsilon+\sum_{j=1}^{K_{\rm s}}
> \theta_j(\sigma_{i_{1,j}},\ldots,\sigma_{i_{p-1,j}},\varepsilon)\right),\tag{5.6}$$
> $$A_{\rm b}(\sigma)=\exp\left(\sum_{j=1}^{K_{\rm b}}\theta_j(\sigma_{i_{1,j}},\ldots,\sigma_{i_{p,j}})\right),\tag{5.7}$$
> where $K_{\rm s}\sim\mathrm{Pois}(\alpha p)$, $K_{\rm b}\sim\mathrm{Pois}(\alpha(p-1))$, and all
> displayed indices are independent uniform indices in $[N]$.

### 기호

| 기호 | 의미 |
|---|---|
| $\Delta_N^{L,\mathbf u}$ | 섭동된 계의 ASS 증분 |
| $\rho_N$ | 저장소의 clause 수 평균 |
| $Y_{0,\rm s}$, $Y_{0,\rm b}$ | 저장소에 $A_{\rm s}$, $A_{\rm b}$를 삽입했을 때의 (3.3) 뿌리값 (Lemma 3.1) |
| $K_{\rm s}$ | 새 스핀에 붙는 clause 수 (Bethe의 차수 $\mathrm{Pois}(\alpha p)$) |
| $K_{\rm b}$ | 과다 계산을 보정하는 clause 수 ($\alpha(p-1)$) |

### 해석

- $A_{\rm s}$: 새 스핀 $\varepsilon$이 외부장 $h$와 clause $K_{\rm s}$개를 통해 저장소의 스핀
  $p-1$개씩과 이어집니다. (2.8)의 $V_{\rm s}$와 비교하면, $U_\theta(x;\varepsilon)$의 메시지 $x$ 대신
  저장소 스핀이 직접 들어가 있습니다. 저장소 Gibbs 측도로 평균하면 그 스핀들의 "메시지"가 생깁니다.
- $A_{\rm b}$: (2.9)의 $V_{\rm e}$와 비교하면 clause $K_{\rm b}\sim\mathrm{Pois}(\alpha(p-1))$개를
  한꺼번에 넣습니다. 평균 개수 $\alpha(p-1)$이 (2.11)의 계수 $\alpha(p-1)$와 맞습니다.
- "independent new root disorder": 새 $\theta_j$, $h$, 자리 $i_{\ell,j}$, $K$는 뿌리 변수
  (quenched)이고 저장소와 독립입니다.
- 8장에서 저장소의 기울인 나무를 위계 메시지로 바꾸면 (5.5)의 우변이 $\mathcal B_r$이 되어
  $\Delta_N\gtrsim\mathcal B_r\ge\Phi_r$을 얻는 것이 전체 그림입니다.

### 물리적 의미

(5.5)는 엄밀한 형태의 **Mézard–Parisi cavity 방정식의 자유에너지 장부**입니다.
"$N+1$번째 스핀을 넣는 비용 − 그 과정에서 과다하게 생긴 clause의 비용". RSB가 있으면
$\log Y_0$는 단순한 Gibbs 평균의 로그가 아니라 **power mean의 로그**, 즉 상태들에 대해
$Z_\alpha^{m}$으로 재가중한 평균입니다 (Lemma 3.1).

---

## 문단 6. 증명 ① 물리 상호작용의 분해

> *The physical interactions.* Split the Poisson interaction process of the $(N+1)$-spin system
> according to the number of indices equal to $N+1$. Terms with no new index have mean $\rho_N$.
> Terms with exactly one new index have mean $\alpha p(N/(N+1))^{p-1}=\alpha p+O(N^{-1})$; by
> permutation invariance we may place the new input last. Their other indices are independent
> uniform indices in $[N]$, and their interaction functions retain the prescribed law. Terms with
> at least two new indices have total mean $O(N^{-1})$. Meanwhile, the $N$-spin system can be
> obtained from the same reservoir by adding a Poisson number of old interactions of mean
> $$\alpha N-\rho_N=\alpha(p-1)+O(N^{-1}).$$
> These quantities are nonnegative for all sufficiently large $N$.

### 해석과 검증

$(N+1)$ 스핀계의 clause는 $\mathrm{Pois}(\alpha(N+1))$개이고 각 자리는 $[N+1]$에서 복원 추출이므로,
"새 자리 $N+1$이 몇 번 나오는가"는 $\mathrm{Bin}(p,\frac1{N+1})$입니다. Poisson 분할(thinning)로
개수별 과정이 독립 Poisson이 됩니다.

- 새 자리 0번: $\alpha(N+1)\bigl(\frac N{N+1}\bigr)^p=\rho_N$. ✓ 이 clause들의 자리는 $[N]$에서
  균등 (조건부) — 저장소의 clause.
- 새 자리 정확히 1번: $\alpha(N+1)\cdot p\cdot\frac1{N+1}\bigl(\frac N{N+1}\bigr)^{p-1}
  =\alpha p\bigl(\frac N{N+1}\bigr)^{p-1}=\alpha p+O(N^{-1})$. ✓ 순열 불변성으로 새 스핀을
  마지막 자리로 옮겨도 $\theta$의 법칙이 같습니다 — 이것이 (5.6)의 꼴입니다.
- 2번 이상: $\alpha(N+1)\bigl[1-(\tfrac N{N+1})^p-\tfrac p{N+1}(\tfrac N{N+1})^{p-1}\bigr]
  \approx\alpha\binom p2\frac1{N+1}=O(N^{-1})$. ✓
- $N$ 스핀계: $\mathrm{Pois}(\alpha N)=\mathrm{Pois}(\rho_N)+\mathrm{Pois}(\alpha N-\rho_N)$로
  쪼개면 저장소 + clause 추가.
  $\alpha N-\rho_N=\alpha N\bigl[1-(\tfrac N{N+1})^{p-1}\bigr]=\alpha(p-1)+O(N^{-1})$. ✓

**검토 메모.** $\rho_N=\alpha N(\frac N{N+1})^{p-1}$이므로 $\alpha N-\rho_N\ge0$은 **모든** $N\ge1$에서
성립합니다. 논문의 "for all sufficiently large $N$"는 조심스러운 표현일 뿐 틀린 것은 아닙니다.

### 수치 확인 ($\alpha=1.3$)

| $p$ | $N$ | $\rho_N$ | $\alpha N-\rho_N$ (→$\alpha(p-1)$) | 새 자리 1번 평균 (→$\alpha p$) | 2번 이상 평균 |
|---|---|---|---|---|---|
| 2 | 10 | 11.818 | 1.1818 (1.3) | 2.3636 (2.6) | $1.2\times10^{-1}$ |
| 2 | 1000 | 1298.70 | 1.2987 | 2.5974 | $1.3\times10^{-3}$ |
| 2 | 10000 | 12998.70 | 1.29987 | 2.59974 | $1.3\times10^{-4}$ |
| 4 | 10 | 9.767 | 3.2329 (3.9) | 3.9068 (5.2) | $6.3\times10^{-1}$ |
| 4 | 1000 | 1296.11 | 3.8922 | 5.1844 | $7.8\times10^{-3}$ |
| 4 | 10000 | 12996.10 | 3.89922 | 5.19844 | $7.8\times10^{-4}$ |

차이가 모두 $O(1/N)$로 줄어듭니다 (2번 이상 평균 $\approx\alpha\binom p2/N$). ✓

### 물리적 의미

희석 그래프에서 새 스핀의 차수는 $\mathrm{Pois}(\alpha p)$이고, 두 번 이상 같은 clause에 들어가는
"짧은 고리"는 $O(1/N)$로 드뭅니다. **국소적으로 나무 같다(locally tree-like)**는 Bethe 근사의
전제가 바로 이 계산입니다.

---

## 문단 7. 증명 ② 섭동의 결합(coupling)

> *The perturbations.* The old-site perturbation count in the $(N+1)$-spin system has total mean
> $s_{N+1}N/(N+1)$, and the new-site count has mean $s_{N+1}/(N+1)$. Couple these processes to the
> reservoir perturbations using common Poisson points. The expected number of unmatched factors is
> at most
> $$|s_{N+1}-s_N|+2s_{N+1}/(N+1)=O(N^{-1/4}).$$
> Deleting or adding a perturbation changes the root logarithm by at most $\log2$; an interaction
> changes it by at most $B$. An unused auxiliary variable can simply be integrated out with its
> prior, so these comparisons remain valid when the number of auxiliary variables changes.

### 해석과 검증

- $(N+1)$ 스핀계의 섭동은 $\mathrm{Pois}(s_{N+1})$개, 자리는 $[N+1]$ 균등. 옛 자리 $[N]$에 떨어지는 것은
  평균 $s_{N+1}\frac N{N+1}$, 새 자리는 $\frac{s_{N+1}}{N+1}$. ✓ (종류 $\nu$ 비율은 그대로 $c_\nu$.)
- 저장소와 $N$ 스핀계는 평균 $s_N$으로 **같은** 섭동을 씁니다. 옛 자리 과정 (평균
  $s_{N+1}\frac N{N+1}$)과 저장소 과정 (평균 $s_N$)을 공통 Poisson 점으로 결합하면, 어긋난 점의 평균
  개수는 $|s_{N+1}\frac N{N+1}-s_N|\le|s_{N+1}-s_N|+\frac{s_{N+1}}{N+1}$. 새 자리 섭동은 모두
  어긋난 것으로 셉니다: $+\frac{s_{N+1}}{N+1}$. 합이 논문의 한계. ✓
- 크기: $s_{N+1}-s_N\approx\frac34N^{-1/4}$, $\frac{s_{N+1}}{N+1}\approx N^{-1/4}$. ✓
- 하나 지우거나 더하면 뿌리 로그는 $\le\log2$ (5.2)만큼, clause 하나는 $\le B$만큼 변합니다
  (Lemma 3.1 단조성). 보조 변수 개수가 달라져도, 쓰이지 않는 변수는 사전확률로 적분해 없애면
  power mean이 바뀌지 않습니다 (상수의 power mean = 상수). ✓

### 수치 확인

| $N$ | 실제 어긋남 평균 | 논문 한계 | $N^{-1/4}$ |
|---|---|---|---|
| 10 | 0.682 | 1.515 | 0.562 |
| 100 | 0.394 | 0.868 | 0.316 |
| 1000 | 0.222 | 0.489 | 0.178 |
| 10000 | 0.125 | 0.275 | 0.100 |

두 값 모두 $N^{-1/4}$에 비례해 줄어듭니다. ✓

### 물리적 의미 — 왜 $s_N=N^{3/4}$인가

섭동 개수는 두 요구 사이에서 정해집니다. (i) $s_N/N\to0$: pressure 밀도를 바꾸지 않음 (5.3).
(ii) $s_{N+1}-s_N\to0$이고 $s_N/N\to0$: 증분 $\Delta_N$을 바꾸지 않음 (여기). (iii) $s_N\to\infty$:
6.2절에서 섭동 "점수"가 집중하려면 섭동이 충분히 많아야 합니다. $N^{3/4}$는 이 셋을 모두
만족하는 편리한 선택입니다 ($N^{\gamma}$, $0<\gamma<1$이면 (i),(ii)는 성립; (iii)의 정량적 요구는
6.2절에서 확인합니다).

---

## 문단 8. 증명 ③ 증분 식

> *The increment.* We may consequently discard the repeated-new-index interactions, match the
> perturbations, and replace the two insertion count means by their limits at a total expected
> cost $O(N^{-1/4})$. Summing over the new spin gives $2A_{\rm s}$, while the old-system correction
> gives $A_{\rm b}$. The factor $2$ supplies the term $\log2$ in the increment. The insertion
> identity for the power means then proves (5.5). Finally,
> $$|\log Y_{0,\rm s}|\le H+BK_{\rm s},\qquad|\log Y_{0,\rm b}|\le BK_{\rm b}.$$
> Together with the coupling estimate this bounds the increments for large $N$; increasing the
> constant covers the remaining sizes. All estimates are uniform in $L$ and $\mathbf u$.

### 해석과 검증

1. **비용 정리**: (a) 2번 이상 새 자리 clause 버림: 평균 $O(N^{-1})$개 × $B$. (b) 섭동 결합:
   $O(N^{-1/4})$개 × $\log2$. (c) 삽입 개수 평균을 $\alpha p(\frac N{N+1})^{p-1}\to\alpha p$,
   $\alpha N-\rho_N\to\alpha(p-1)$으로 바꾸기: 두 Poisson의 결합으로 어긋남 $O(N^{-1})$개 × $B$.
   합 $O(N^{-1/4})$. ✓ 각 비용은 "개수 × 한 개당 한계"로, 개수에 대해 조건부로 Lemma 3.1의 단조성을
   쓰면 됩니다.
2. **$N+1$ 쪽**: 남은 $(N+1)$ 스핀계 = 저장소 × (새 스핀 $\varepsilon$과 그 clause들, 장 $h\varepsilon$).
   $\varepsilon$에 대해 합하면 스핀 가중치에
   $\sum_\varepsilon e^{h\varepsilon+\sum_j\theta_j(\cdot,\varepsilon)}=2A_{\rm s}(\sigma)$를 곱한 것.
   Lemma 3.1: 뿌리 로그 증분 $=\log Y_0(2A_{\rm s})=\log2+\log Y_{0,\rm s}$ (동차성). ✓
3. **$N$ 쪽**: 저장소 × $A_{\rm b}$ ⇒ 증분 $\log Y_{0,\rm b}$. ✓
4. 빼면 (5.5). ✓
5. **한계**: $e^{-H-BK_{\rm s}}\le A_{\rm s}\le e^{H+BK_{\rm s}}$, 단조성으로 $Y_{0,\rm s}$도 같은 구간. ✓
   $\mathbb E[H+BK_{\rm s}]=H+B\alpha p$이므로 $|\Delta_N|\le\log2+H+B\alpha(2p-1)+O(N^{-1/4})$.
   작은 $N$은 상수를 키워서 처리 ($|\Delta_N|\le|P_{N+1}|+|P_N|$이 각 $N$마다 유한). ✓
6. 어떤 단계도 $L$, $\mathbf u$에 의존하지 않습니다 ((5.2)의 한계와 Lemma 3.1만 사용). ✓

**검토 메모.** (5.5)의 $Y_{0,\rm s}$, $Y_{0,\rm b}$는 **같은 저장소의 기울인 커널**로 계산됩니다.
그래서 6–8장의 정보(저장소 나무의 구조)가 두 항에 동시에 적용됩니다. 이것이 ASS 비교의 요점이며,
두 계를 따로 다루면 생기지 않는 상쇄가 여기서 생깁니다.

---

## 문단 9. 이후의 약속

> In the rest of the lower-bound proof, all spin trees are sampled from this reservoir using its
> tilted auxiliary kernels and its terminal Gibbs kernel. The reservoir retains an independent
> Poisson interaction process of mean $O(N)$ and $N$ independent bounded fields. Thus the
> concentration argument applies to its slightly modified interaction mean as well.

### 해석

- 6–8장의 모든 "나무" $\mathcal T$는 **저장소**에서 뽑습니다: 깊이 $1..r$은 기울인 보조 커널
  (3.2), 깊이 $L$은 Gibbs 커널.
- 저장소는 clause 평균이 $\alpha N$ 대신 $\rho_N=\alpha N+O(1)$인 것만 다르므로, 6.2절의 집중
  논증 (clause 하나나 장 하나를 바꿀 때 유계 차분 → Efron–Stein/Poisson 집중)이 그대로 적용됩니다.

### 물리적 의미

ASS 증분에 쓰이는 "cavity 메시지"는 모두 저장소의 실제 Gibbs 측도에서 나옵니다. 남은 장들의 임무는
이 측도가 (i) Ghirlanda–Guerra 류 항등식을 만족하고 (6장), (ii) 서로 다른 자리의 스핀이 상태 안에서
상관이 사라지며 (7장), (iii) 따라서 독립 위계 메시지로 바꿀 수 있음 (8장)을 보이는 것입니다.

---

## 요약

- ASS 틀: $\liminf F_N\ge\liminf\Delta_N$, 증분을 공통 저장소로 표현.
- 저장소에 $s_N=N^{3/4}$개의 유계 한-자리 섭동 $\psi_\nu$를 넣고, 섭동별 보조 변수로 $L$단 위계를 만듦.
  pressure 변화 $\le s_N\log2=o(N)$ (5.3).
- Lemma 5.1: $\Delta_N=\log2+\mathbb E\log Y_{0,\rm s}-\mathbb E\log Y_{0,\rm b}+o(1)$, site 삽입은
  $\mathrm{Pois}(\alpha p)$개, bond 삽입은 $\mathrm{Pois}(\alpha(p-1))$개 clause. 오차는 $L,\mathbf u$에 균등.
- Poisson 분할의 평균, $\alpha N-\rho_N$, 섭동 어긋남 $O(N^{-1/4})$를 수치로 확인했습니다.
- 아래쪽 한계는 (2.3), (2.4)를 쓰지 않고, 유계·순열 불변만 씁니다.

**다음 절 예고**: 6.1절에서 섭동 인자 $\psi_\nu$의 구체적인 족(family)을 정의합니다.
