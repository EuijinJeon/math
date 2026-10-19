# 6.3 One sequence for low increments and all identities — 문단별 해설

원문: `build/sections/perturbations.tex` 6.3절, PDF 17–18쪽. 번호는 PDF 기준 (Lemma 6.2).
앞 절 참조: (5.3), Lemma 5.1, Lemma 6.1, (3.1).

이 절은 짧지만 아래쪽 한계 증명의 **논리적 뼈대**입니다. 이후 모든 극한은 여기서 고른 하나의
수열 위에서 취합니다.

---

## 문단 1. 문제 설정

> The parameter choices must satisfy concentration and a low cavity increment simultaneously. Let
> $\underline F=\liminf_NF_N$ over all system sizes for the bounded model. Recall that
> $P_N^{L,\mathbf u}$ denotes the root-averaged perturbed log partition function, and put
> $\Delta_N(\mathbf u)=P_{N+1}^{L,\mathbf u}-P_N^{L,\mathbf u}$.

### 해석

목표는 $\underline F\ge\inf_r\Phi_r$입니다. ASS 논리 (5장 문단 1)로는 $\Delta_N$이 $\underline F$에 가까운
$N$들을 찾고, 거기서 $\Delta_N\gtrsim\mathcal B_r$을 보이면 됩니다. 그런데 $\Delta_N\gtrsim\mathcal B_r$을
보이려면 섭동 점수가 집중해야 하고 (6.2), 집중은 $\pi$-평균으로만 알려져 있습니다. 두 조건을 **같은
$(N,\mathbf u)$**에서 동시에 만족시켜야 합니다.

| 기호 | 의미 |
|---|---|
| $\underline F$ | 유계 모형의 $\liminf_NF_N$ |
| $\Delta_N(\mathbf u)$ | 매개변수 $\mathbf u$에서의 섭동된 ASS 증분 |

---

## 문단 2. Lemma 6.2 (Deterministic parameter selection)

> **Lemma 6.2.** For every fixed $L\geq2$ and $\varepsilon>0$, there are sizes $N_j\uparrow\infty$ and
> deterministic vectors $\mathbf u_j$ such that
> (i) $\Delta_{N_j}(\mathbf u_j)\leq\underline F+2\varepsilon$;
> (ii) for every fixed type $\nu$, $e_{\nu,N_j}(\mathbf u_j)\longrightarrow0$ in the reservoir;
> (iii) in the reservoir, the expectations of every finite product of multioverlaps on every fixed
> finite prescribed tree of depth $L$ converge along this sequence.

### 해석

- (i) 낮은 증분: 이 수열에서 $\Delta$가 $\underline F$보다 거의 크지 않습니다. 나중에
  $\Delta_{N_j}\ge\mathcal B_r-o(1)$을 보이면 $\underline F+2\varepsilon\ge\Phi_r-o(1)$.
- (ii) 모든 종류의 점수가 **점별로** (선택된 $\mathbf u_j$에서) 집중합니다.
- (iii) 저장소 나무 위 multi-overlap 모멘트가 모두 수렴합니다. 극한 "나무 법칙"이 존재한다는 뜻으로,
  물리에서 "overlap 분포 $P(q)$의 극한"을 부분수열로 잡는 것과 같습니다. 극한 객체가 무한 위계인지는
  묻지 않고, **유한 나무 모멘트**만 다룹니다.

---

## 문단 3. 증명 ① 평균 증분이 낮은 크기들

> *Find low averaged increments.* The uniform perturbation bound (5.3) gives
> $$\liminf_N\frac1N\int P_N^{L,\mathbf u}\,\pi(d\mathbf u)=\underline F.$$
> Hence infinitely many $N$ satisfy $\int\Delta_N\,d\pi\leq\underline F+\varepsilon$: otherwise
> telescoping the averaged increments would contradict this liminf. Lemma 5.1 supplies a constant
> $C$ such that $|\Delta_N(\mathbf u)|\leq C$ uniformly.

### 검증

- (5.3): $|\frac1NP_N^{L,\mathbf u}-F_N|\le\log2\cdot N^{-1/4}$가 $\mathbf u$에 균등 ⇒ $\pi$-적분 후
  $\liminf$이 $\underline F$. ✓
- 귀류: $N\ge N_0$에서 모두 $\int\Delta_N\,d\pi>\underline F+\varepsilon$이면
  $\frac1N\int P_N=\frac1N\bigl[\int P_{N_0}+\sum_{n=N_0}^{N-1}\int\Delta_n\bigr]>\frac{\int P_{N_0}}N+\frac{N-N_0}N(\underline F+\varepsilon)$
  ⇒ $\liminf\ge\underline F+\varepsilon$, 모순. ✓
- $|\Delta_N|\le C$: Lemma 5.1의 첫 문장 ($N,L,\mathbf u$에 균등). ✓

---

## 문단 4. 증명 ② 점수 오차가 작은 매개변수 고르기

> *Choose parameters with small score errors.* For a finite collection of types, Lemma 6.1 and
> Markov's inequality show that the set where all its errors are small has parameter measure
> tending to one. More explicitly, choose $N_j$ successively among the preceding infinite set so
> large that
> $$\sum_{\nu\leq j}\int e_{\nu,N_j}(\mathbf u)\,\pi(d\mathbf u)\leq j^{-3}.$$
> Then the set $G_j$ where $e_{\nu,N_j}\leq j^{-1}$ for all $\nu\leq j$ has complement of measure
> $q_j\leq j^{-2}$. Its conditional mean increment is at most
> $$\frac{\underline F+\varepsilon+Cq_j}{1-q_j}\leq\underline F+2\varepsilon$$
> for all sufficiently large $j$. A vector in $G_j$ with increment at most $\underline F+2\varepsilon$
> can therefore be chosen. Relabeling the tail proves (i) and (ii).

### 검증

- $N_j$ 존재: 종류 $j$개는 유한, 각 $\int e_{\nu,N}\,d\pi\to0$ (Lemma 6.1, 저장소에서) ⇒ 충분히 큰 $N$에서
  합 $\le j^{-3}$. 그 $N$을 문단 3의 무한 집합에서 고릅니다. ✓
- Markov + 합집합: $\pi(e_\nu>1/j)\le j\int e_\nu$ ⇒ $q_j\le j\sum_{\nu\le j}\int e_\nu\le j^{-2}$. ✓
- 조건부 평균: $\int_{G_j}\Delta\,d\pi=\int\Delta-\int_{G_j^c}\Delta\le\underline F+\varepsilon+Cq_j$,
  $\pi(G_j)=1-q_j$로 나눔. ✓ $q_j\to0$이면 좌변 $\to\underline F+\varepsilon<\underline F+2\varepsilon$. ✓
- 조건부 평균 이하인 점이 $G_j$ 안에 존재 (평균 이하인 점이 양의 측도로 존재). ✓
- (ii): 고정 $\nu$에 대해 $j\ge\nu$부터 $e_{\nu,N_j}(\mathbf u_j)\le1/j\to0$. ✓

### 작은 수치 예

$\underline F=0.5$, $\varepsilon=0.01$일 때 조건부 평균 한계 $\frac{\underline F+\varepsilon+Cj^{-2}}{1-j^{-2}}$와
목표 $\underline F+2\varepsilon=0.52$:

| $C$ | $j=10$ | $j=20$ | $j=40$ | $j=80$ |
|---|---|---|---|---|
| 5 | 0.5657 ✗ | 0.5238 ✗ | 0.5135 ✓ | 0.5109 ✓ |
| 20 | 0.7172 ✗ | 0.5614 ✗ | 0.5228 ✗ | 0.5132 ✓ |

"for all sufficiently large $j$"가 $C$에 의존하는 문턱임을 보여 줍니다. 수열 앞부분을 버리고
번호를 다시 매기면 됩니다 ("Relabeling the tail").

### 물리적 의미

GG 항등식의 "거의 모든 매개변수에서"를 **하나의 결정적 섭동 세기 수열**로 바꾸는 단계입니다. 물리 문헌은
보통 "작은 섭동을 더하고 $N\to\infty$ 다음 섭동 $\to0$"이라고만 말하는데, 그 사이에 자유에너지
($\Delta$)를 잃지 않는다는 점을 확인하는 것이 여기의 내용입니다.

---

## 문단 5. 증명 ③ 대각 부분수열

> *Make all finite-tree moments converge.* At fixed $L$ the finite labeled tree shapes and finite
> products of their multioverlaps form a countable collection. Each such product is bounded by one
> in absolute value. A diagonal subsequence gives (iii), without affecting (i) or (ii).

### 검증

- 깊이 $L$ 고정, 잎 수 유한인 라벨 나무는 가산 개, 각 나무의 multi-overlap 곱도 가산 개 ✓.
- $|R_S|\le1$ (3.1) ⇒ 곱의 기대값은 $[-1,1]$의 수열 ⇒ Bolzano–Weierstrass로 수렴 부분수열,
  가산 개에 대해 대각 논법. ✓
- (i), (ii)는 부분수열로 옮겨도 유지됩니다 ((i)은 각 항의 성질, (ii)는 극한). ✓

---

## 문단 6. 이후의 규약

> From now on $L$ is fixed and $N\to\infty$ means convergence along a sequence from Lemma 6.2.
> Expectations below are evaluated at the selected deterministic vector, whose dependence on $N$ is
> suppressed. No uniformity in $L$, in the number of paths, or in a perturbation type is asserted
> for these limits.

### 해석

- 7–8장의 "$N\to\infty$"는 모두 이 수열을 따라갑니다.
- 극한 순서: $L$ 고정 → $N\to\infty$ (이 수열) → 마지막에 $L\to\infty$, $\varepsilon\to0$. 균등성이 없으므로
  순서를 바꾸면 안 됩니다.

---

## 요약

- 낮은 ASS 증분, 모든 점수 집중, 모든 유한 나무 모멘트 수렴을 동시에 만족하는 결정적 수열
  $(N_j,\mathbf u_j)$를 고릅니다 (Lemma 6.2).
- 도구: (5.3)의 균등 근사 + 망원 합 → 평균 증분이 낮은 무한히 많은 $N$; Lemma 6.1 + Markov → 점수
  오차가 작은 큰 측도 집합; 조건부 평균 → (i)(ii); 대각 논법 → (iii).
- 이후 극한은 이 수열 위에서, $L$을 고정한 채 취합니다.

**다음 절 예고**: 6.4절에서 섭동 항 하나를 Poisson 삽입으로 보는 Palm 항등식 (Lemma 6.3)과,
그로부터 삽입의 모든 Taylor 계수가 사라짐 (Lemma 6.4)을 얻습니다.
