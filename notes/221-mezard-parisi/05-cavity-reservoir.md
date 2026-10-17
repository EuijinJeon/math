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

> (작업 중 — 다음 문단부터 이어짐)
