# 6장 도입 + 6.1 The perturbation family — 문단별 해설

원문: `build/sections/perturbations.tex` 앞부분, PDF 15–16쪽. 번호는 PDF 기준 (식 (6.1), (6.2)).
앞 장 참조: 5장 (5.1)–(5.3), Lemma 3.1, Lemma 3.3.

6장의 목표는 저장소의 나무에서 **"지정한 replica 가지 패턴마다 성립하는 항등식"**(정리 6.5)을
얻는 것입니다. 6.1절은 그 재료인 섭동 족을 정의합니다.

---

## 문단 1. 6장의 무대

> Throughout this section the interaction and field are bounded, and the depth $L\geq2$ is fixed.
> The arguments apply both to the $N$-spin system and to the reservoir in Lemma 5.1. Its physical
> disorder consists of independent bounded interactions with a Poisson count of mean $O(N)$,
> together with $N$ independent bounded fields. All expectations in a statement at a specified
> parameter vector are taken with that vector held fixed.

### 해석

- 5장 문단 2의 유계 가정 ($B(\theta)\le B$, $|h|\le H$)과 고정된 $L$ 아래에서 일합니다.
- 6장의 논증은 "독립 유계 입력 $O(N)$개의 함수"라는 구조만 쓰므로, 원래 계와 저장소
  (clause 평균 $\rho_N$)에 똑같이 적용됩니다.
- "parameter vector held fixed": 섭동 매개변수 $\mathbf u$는 quenched 무질서가 아닙니다. 기대값
  $\mathbb E_{\mathbf u}$는 $\mathbf u$를 고정하고 뿌리(무질서)만 평균합니다.

---

## 문단 2. 전략과 선행 연구

> We choose perturbations whose derivatives concentrate, while selecting cavity increments at most
> an arbitrarily small error above the unperturbed liminf. A Poisson insertion then turns
> concentration into Taylor-coefficient identities. Independent signs along the inserted paths
> select the prescribed splitting depths. The use of concentration to obtain overlap identities
> has antecedents in the self-averaging argument of Ghirlanda–Guerra [GG98]. Related antecedents
> are the stochastic-stability relations of Aizenman–Contucci [AC98] and their extensions to
> diluted multioverlaps by Barra and De Sanctis [BarraDeSanctis07]. Panchenko's spin-distribution
> identities [Pan13] provide the cavity context. The bounded perturbation family and the
> identities on colored finite trees needed here are constructed and proved below.

### 해석 — 세 단계 계획

1. **집중**(6.2): 섭동의 도함수("점수" $D_\nu$)가 열적·무질서 요동 모두에서 평균 주위로 집중합니다.
   이것은 Ghirlanda–Guerra의 고전 논증과 같습니다. 자유에너지는 매개변수에 대해 볼록하고
   self-averaging하므로, 거의 모든 매개변수에서 그 도함수도 self-averaging합니다.
2. **선택**(6.3): 집중이 성립하면서 동시에 ASS 증분이 $\liminf F_N+2\varepsilon$ 이하인 크기 $N_j$와
   매개변수 $\mathbf u_j$를 하나의 수열로 고릅니다.
3. **추출**(6.4–6.5): 섭동 항 하나를 Poisson 삽입처럼 보면 (Palm 항등식) "anchor replica에서 점수를
   잰 기대값 = 독립 경우의 기대값"이 되고, 이것을 $t$에 대한 Taylor 계수로 풀면 나무 위의 항등식이
   나옵니다. 보조 Rademacher 부호의 곱이 **갈라짐 깊이를 고르는 지시함수**가 됩니다.

### 물리적 의미

| 개념 | 여기서의 대응물 |
|---|---|
| Ghirlanda–Guerra 항등식 | 점수 집중 → overlap 분포의 "확률적 안정성" |
| Aizenman–Contucci 확률적 안정성 | 작은 섭동을 더해도 overlap 분포가 불변 |
| Barra–De Sanctis | 희석 모형의 multi-overlap 버전 |
| Panchenko의 spin-distribution 항등식 | cavity 맥락의 같은 항등식 (무한 위계 가정) |

이 논문은 **유한 깊이 $L$의 나무 위에서**, 무한 Ruelle cascade를 먼저 구성하지 않고 이 항등식들을
직접 얻는다는 점이 새롭습니다 (정리 2.1 아래 문장: "does not assume ... a limiting infinite-depth
Gibbs state has been constructed").

---

## 문단 3. 표시 명세(mark specification)

> A *mark specification* consists of a finite number $n\geq0$ of labeled Rademacher coordinates, a
> depth in $\{1,\ldots,L-1\}$ assigned to each coordinate, two functions
> $g,g_0:\{-1,1\}^n\to\mathbb Q\cap[-1,1]$, and a choice $S_0=1$ or $S_0=\sigma_i$. Each coordinate is
> sampled at its assigned depth along an auxiliary path. Distinct coordinates are independent; the
> value of a coordinate is shared at a shared vertex and is independent at different vertices. The
> case $n=0$ includes constant functions. We use all such specifications, a countable collection
> because each sign domain is finite. Products of signs and their rational averages belong to this
> collection; these will select branching patterns.

### 기호

| 기호 | 의미 |
|---|---|
| $\epsilon_1,\dots,\epsilon_n$ | Rademacher 좌표 (값 $\pm1$, 각 ½), 각자 깊이 $d_k\in\{1..L-1\}$에 배정 |
| $g,g_0$ | 부호 벡터의 유리수 값 함수, 절댓값 $\le1$ |
| $S_0\in\{1,\sigma_i\}$ | 둘째 항이 스핀을 읽는지 여부 |

### 해석

- **"공유 꼭짓점에서 값 공유"**: 깊이 $d$에 배정된 좌표는 나무의 깊이-$d$ 꼭짓점마다 하나씩 독립으로
  뽑힙니다. 두 replica $a,b$의 경로가 깊이 $d$ 꼭짓점을 공유하면 같은 값, 아니면 독립입니다.
  따라서 $\mathbb E[\epsilon^a\epsilon^b]=\mathbf 1\{a,b\text{가 깊이-}d\text{ 꼭짓점 공유}\}$ — 이것이 6.5절의
  식 (6.18)입니다.
- **가산성**: 유한 정의역 $\{-1,1\}^n$ 위의 유리수 값 함수는 가산 개, $n$과 깊이 배정도 가산 개. ✓
  가산이어야 $\sum_\nu c_\nu=1$인 양의 가중치를 줄 수 있습니다.
- **선택 기능**: 갈라짐 깊이 $\ge d$의 지시함수를 부호 곱의 평균으로 만들 수 있으므로, 이들의
  차이로 "정확히 깊이 $d$에서 갈라짐"을 고를 수 있습니다.

### 물리적 의미

Rademacher 좌표는 깊이 $d$ 상태(cluster)에 붙은 **무작위 "색"**입니다. 같은 깊이-$d$ 상태에 있는
replica들은 같은 색을 보고, 다른 상태에 있으면 독립인 색을 봅니다. 색에 대한 상관을 재면 "두
replica가 깊이 $d$에서 같은 상태에 있는가"를 알 수 있습니다. 물리의 overlap $q_{ab}$를 직접 재는
대신, 위계 구조의 **조합적 골격**(어느 깊이에서 갈라지는가)을 직접 읽는 장치입니다.

### 작은 예 (정확 열거)

$L=4$, 잎 3개: $a,b$는 깊이 2에서 갈라지고 $c$는 깊이 1에서 갈라짐. 깊이 $d$의 Rademacher 좌표에
대한 $\mathbb E[\epsilon^x\epsilon^y]$:

| 깊이 $d$ | $(a,b)$ | $(a,c)$ | $(b,c)$ |
|---|---|---|---|
| 1 | 1 | 1 | 1 |
| 2 | 1 | 0 | 0 |
| 3 | 0 | 0 | 0 |

$\mathbb E[\epsilon_d^x\epsilon_d^y]=\mathbf 1\{\text{split}(x,y)\ge d\}$ ✓, 그래서
$\mathbf 1\{\text{split}=d\}=H_d-H_{d+1}$로 정확한 갈라짐 깊이를 고릅니다.

---

## 문단 4. 매개변수 $t$, $u$와 종류 $\nu$

> The two parameters have different roles: differentiation in $u$ produces a concentrated score,
> while the values of $t$ probe an insertion's Taylor expansion. Taking $u$ smaller than every fixed
> power of $t$ will force each limiting Taylor coefficient to vanish. For each specification include
> types indexed by all integers $j\geq4$. The type $\nu$ corresponding to this specification and $j$
> has
> $$t_\nu=j^{-1},\qquad I_\nu=[j^{-j},2j^{-j}],\qquad u_\nu\in I_\nu.\tag{6.1}$$

### 해석

- $u$: 섭동 세기. $u$로 미분한 것이 점수 $D_\nu$ (6.3)이고, 이것이 6.2절에서 집중합니다.
- $t$: 삽입 항 $1+tg\sigma_i$의 세기. 6.4절에서 $t$에 대한 해석 함수의 Taylor 계수를 읽습니다.
- $j\ge4$를 모두 넣으므로 $t_\nu=1/j\to0$인 수열이 있습니다. 해석 함수 $H(t)$가 $t=1/j$에서
  $|H(1/j)|\lesssim u_\nu\le2j^{-j}$이면 $H$는 0 근처에서 어떤 거듭제곱보다도 빨리 작아지므로
  모든 Taylor 계수가 0이어야 합니다 (6.4절 Lemma 6.4의 논리).

### 검증

$u/t^q\le2j^{-j}/j^{-q}=2j^{q-j}\to0$ ($j\to\infty$), 모든 고정 $q$에서. ✓

| $q$ | $j=4$ | $j=8$ | $j=16$ | $j=32$ |
|---|---|---|---|---|
| 1 | $3.1\times10^{-2}$ | $9.5\times10^{-7}$ | $1.7\times10^{-18}$ | $4.4\times10^{-47}$ |
| 2 | $1.2\times10^{-1}$ | $7.6\times10^{-6}$ | $2.8\times10^{-17}$ | $1.4\times10^{-45}$ |
| 5 | $8.0$ | $3.9\times10^{-3}$ | $1.1\times10^{-13}$ | $4.6\times10^{-41}$ |

### 물리적 의미

물리적으로는 "아주 약한 탐침($u$)으로 응답을 재되, 그 응답이 탐침 없는 계의 성질을 반영하도록
$u\to0$을 다른 모든 척도보다 빨리 보낸다"는 표준적인 선형 응답 논리입니다. $t$는 "탐침이 무엇을
보는가"를 정하는 모양 매개변수입니다.

---

## 문단 5. 섭동 인자 (6.2)

> Enumerate these types by $\nu\in\mathbb N$ and choose constants $c_\nu>0$ with $\sum_\nu c_\nu=1$.
> Independently for each type, put $n_\nu\sim\mathrm{Poisson}(c_\nu s_N)$, where $s_N=N^{3/4}$. Each
> term has an independent uniform site $i\in[N]$ and an independent copy of its mark process. At a
> leaf it multiplies the spin weight by
> $$\psi_\nu=1+t_\nu g\sigma_i+u_\nu g_0S_0.\tag{6.2}$$
> In particular $1/2<\psi_\nu<3/2$. Counts, types, and sites belong to the root; the mark variables
> are sampled with their product priors at their assigned auxiliary depths. Since the total count
> is $\mathrm{Poisson}(s_N)$, this construction uses only finitely many terms almost surely. The
> factor bound permits termwise comparison through the power means, as in (5.3).

### 해석과 검증

- $|t_\nu g\sigma_i|\le1/4$ ($j\ge4$), $|u_\nu g_0S_0|\le2j^{-j}\le2/256$. 따라서
  $\psi_\nu\in[0.742,1.258]\subset(1/2,3/2)$. ✓ (수치: $j\ge4$ 전체에서 최소 $0.7421875$, 최대 $1.2578125$.)
- 이것이 5장 (5.2)의 조건이므로 (5.3)과 Lemma 5.1이 이 족에 적용됩니다. ✓
- 구조: $g$와 $g_0$는 보조 경로의 부호 $\epsilon$에 의존하므로 $\psi_\nu$는 "깊이별 상태의 색"과
  "자리 $i$의 스핀"의 결합입니다. $tg\sigma_i$는 **색에 따라 달라지는 외부장**, $ug_0S_0$는 점수를
  만드는 작은 항입니다.

### 물리적 의미

$\psi=1+tg(\epsilon)\sigma_i$는 $e^{h(\epsilon)\sigma_i}/\cosh$의 1차 근사와 같은, **상태 색에 의존하는
무작위 장**입니다. Poisson 개수 $\sim N^{3/4}$개만큼 무작위 자리에 뿌려지므로 자리당 밀도는
$N^{-1/4}\to0$이지만, 전체 점수는 $N^{3/4}\to\infty$개 항의 합이라 큰수의 법칙이 작동합니다.

---

## 문단 6. 매개변수 측도 $\pi$

> Write $\pi$ for the product of the uniform probability measures on the intervals $I_\nu$, and
> $\mathbf u=(u_\nu)_\nu$. We use $\pi$ to select deterministic parameter vectors, not as part of
> their quenched law. Each interval has fixed positive length for a fixed type; concentration
> estimates may therefore depend on its length.

### 해석

- $\pi=\bigotimes_\nu\mathrm{Unif}(I_\nu)$: 가산 곱 확률측도 (Kolmogorov 확장으로 존재).
- 쓰임: "$\pi$-평균으로 오차가 작다 ⇒ 오차가 작은 결정적 $\mathbf u$가 존재" (Markov 부등식,
  6.3절). $\mathbf u$를 무작위로 두고 무질서와 섞지 않는다는 점이 중요합니다. 그래야 선택된 계가
  "고정된 해밀토니안을 가진 하나의 계"가 됩니다.
- $|I_\nu|=j^{-j}$는 $\nu$마다 고정이므로, 6.2절 상수가 $1/|I_\nu|$에 의존해도 $N\to\infty$에서는
  문제가 없습니다 (Lemma 6.1이 "Constants need not be uniform in $\nu$"라고 명시).

### 물리적 의미

Ghirlanda–Guerra 논증에서 항등식은 "거의 모든 온도/장 매개변수에서" 성립합니다. 여기서도 $\pi$-거의
모든 섭동 세기에서 집중이 성립하고, 그 중 하나를 골라 고정합니다.

---

## 요약

- 6장은 유계 계·고정 $L$에서, 저장소 나무 위의 항등식을 섭동 → 집중 → 선택 → Taylor 추출로 얻습니다.
- 표시 명세: 깊이별 Rademacher 좌표와 유리수 함수 $g,g_0$, $S_0\in\{1,\sigma_i\}$. 가산 족.
  같은 깊이-$d$ 꼭짓점을 공유하는 replica만 같은 부호를 보므로, 부호 상관이 갈라짐 깊이를 고릅니다.
- 종류 $\nu$=(명세, $j\ge4$), $t_\nu=1/j$, $u_\nu\in[j^{-j},2j^{-j}]$: $u$가 $t$의 어떤 거듭제곱보다 작음.
- $\psi_\nu=1+t_\nu g\sigma_i+u_\nu g_0S_0\in(1/2,3/2)$, 개수 $\mathrm{Pois}(c_\nu N^{3/4})$.
- 수치로 $\psi$ 범위, $u/t^q\to0$, 부호 상관 = 갈라짐 지시함수를 확인했습니다.

**다음 절 예고**: 6.2절에서 점수 $D_\nu$ (6.3)가 열적·무질서 요동 모두에서 집중함 (Lemma 6.1)을 보입니다.
