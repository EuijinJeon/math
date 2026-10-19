# 7장 도입 + 7.1 Averages over depths — 문단별 해설

원문: `build/sections/decorrelation.tex` 앞부분, PDF 21–22쪽. 번호는 PDF 기준
(식 (7.1)–(7.4), 정리 7.1). 앞 장 참조: 정리 6.5 (6.17), Lemma 6.2, Lemma 3.6, Remark 3.7(3.4절 끝 remark).

7장은 6장의 항등식만을 써서 **모든 multi-overlap이 (갈라짐 깊이를 평균하면) 집중한다**는 정리 7.1을
증명합니다. 8장에서 저장소를 독립 위계 메시지로 바꾸는 데 필요한 핵심 입력입니다.

---

## 문단 1. 7장의 무대

> Throughout this section $m_d=d/L$ and $\delta=L^{-1}$. For each fixed $L$, all limits in $N$ are
> along the sizes and parameter choices supplied by Lemma 6.2; they satisfy the identities of
> Theorem 6.5. Different values of $L$ may use different sequences. The argument uses only these
> identities and the tree sampling rules; in particular, it does not use the interaction
> factorization.

### 해석

- 균등 격자 (5.1). Lemma 3.5, 3.6과 3.3절의 "$\delta$" 계산이 그대로 쓰입니다.
- 입력은 두 가지뿐입니다: (a) 정리 6.5의 나무 항등식, (b) 나무 표본 규칙 (조건부 독립, 사영 일관성).
  모형의 세부 (clause, $\theta$의 분해)는 쓰지 않습니다. 따라서 7장의 결과는 "GG형 항등식을 만족하는 임의의
  유한 깊이 나무 계"에 대한 정리로 읽을 수 있습니다.

---

## 문단 2. 목표

> Our goal is concentration of every finite multioverlap, averaged over separated interior branching
> depths. These are the averages needed for the comparison with independent messages in Section 8.

### 물리적 의미

RSB 그림에서 replica들이 **어느 깊이에서 갈라지는지 지정하면** (예: 두 replica가 같은 깊이-$d$ 상태 안에
있다), 그 replica들의 multi-overlap $R_S$는 무작위가 아닌 값을 가져야 합니다. 이것이 "상태 안에서는
replica-symmetric", 다시 말해 **순수 상태 안에서 서로 다른 자리의 스핀이 상관을 잃는다** (clustering
property)는 물리적 가정의 수학적 형태입니다. 그 결과 cavity 장 (메시지)이 상태 안에서 독립이 되어,
Mézard–Parisi의 "메시지 분포의 분포의 …" 위계 (2.7)가 정당화됩니다.

---

## 문단 3. 위상과 $\eta$-정칙 깊이 배정

> A topology is a finite rooted tree on labeled leaves, with unary vertices suppressed. Each branching
> vertex is assigned an integer depth in $\{0,\ldots,L-1\}$, increasing strictly along every branch.
> Write $b(S)$ for the number of branching vertices of a topology $S$. Fix $\eta>0$. A depth
> assignment is *$\eta$-regular* if every assigned depth divided by $L$ lies in $(\eta,1-\eta)$ and the
> normalized depths of distinct branching vertices differ by more than $\eta$. When an additional
> prefix depth $d$ is specified, it must satisfy the same restrictions relative to all branching
> depths. When two copies of one topology use aligned depths, corresponding vertices share one depth
> coordinate; regularity is imposed on these distinct coordinates.

### 기호

| 기호 | 의미 |
|---|---|
| 위상 $S$ | 홑자식 꼭짓점을 지운 라벨 나무 (모양) |
| $b(S)$ | 갈라짐 꼭짓점 수 = 깊이 좌표 수 |
| $\mathbf q=(q_v)$ | 갈라짐 꼭짓점의 깊이 배정, 가지를 따라 엄격히 증가 |
| $\eta$-regular | 정규화 깊이 $q_v/L\in(\eta,1-\eta)$, 서로 $\eta$보다 멀리 |
| prefix depth $d$ | 추가로 지정하는 깊이 (예: 조건부 기대값을 취하는 깊이) |

### 해석

3.4절 Lemma 3.6의 regular 정의와 같습니다. 정칙 배정에서는 (i) 갈라짐이 뿌리 근처나 잎 근처에 있지 않고,
(ii) 서로 다른 갈라짐이 몰려 있지 않습니다. Lemma 3.6에 따라 $Q_k$ 아래 정칙이 아닐 확률은
$\le C_k(\eta+1/L)$이므로, 정칙 배정만 다뤄도 로그 전개 (8장)에서 잃는 것이 작습니다.
"두 복사본의 정렬된 깊이": 분산 $\mathrm{Var}(R_S)=\mathbb E[R_SR_{S'}]-\dots$를 계산할 때 $S$의 두 복사본이
**같은 깊이 좌표**를 씁니다. 3장 요약의 "대응 깊이를 일부러 맞춘다"가 이것입니다.

---

## 문단 4. 깊이 평균 $\mathcal A_{L,\eta}$와 기본 비교: (7.1), (7.2)

> For a nonnegative array $z(\mathbf q)$ on $a$ depth coordinates, put
> $$\mathcal A_{L,\eta}z=L^{-a}\sum_{\mathbf q\;\eta\text{-regular}}z(\mathbf q).\tag{7.1}$$
> Additional ordering restrictions, such as $d<\min_vq_v$, are included in the summation domain. These
> are unnormalized averages: their total mass is at most one. Consequently, for $0<\gamma\le1$,
> $$\mathcal A_{L,\eta}(z^\gamma)\le(\mathcal A_{L,\eta}z)^\gamma.\tag{7.2}$$
> Two elementary comparisons will recur. Summing over an unused coordinate costs at most $L$, canceled
> by its normalization. A fixed integer shift of any subset of the coordinates maps $\eta$-regular
> assignments injectively into $\eta/2$-regular assignments for all sufficiently large $L$.

### 검증

- **질량 $\le1$**: 정칙 배정 수 $\le L^a$. ✓
- **(7.2)**: $\mathcal A$는 질량 $M\le1$인 측도에 대한 적분. $z^\gamma$는 오목이므로 Jensen:
  $\mathcal A(z^\gamma)=M\cdot\overline{z^\gamma}\le M(\bar z)^\gamma=M^{1-\gamma}(\mathcal Az)^\gamma\le(\mathcal Az)^\gamma$. ✓
- **안 쓰는 좌표**: $z$가 좌표 하나에 의존하지 않으면 그 좌표의 합은 $\le L$개 항, 정규화 $L^{-1}$이 상쇄. ✓
- **이동**: 일부 좌표를 정수 $s$만큼 옮기면 정규화 깊이가 $s/L$만큼 바뀝니다. $s/L\le\eta/2$이면 경계 조건
  $(\eta,1-\eta)\to(\eta/2,1-\eta/2)$, 간격 $>\eta\to>\eta-s/L\ge\eta/2$. 단사 (평행 이동). ✓

### 수치 확인

| 확인 | 결과 |
|---|---|
| 3잎 사슬 위상 ($q_1<q_2$), $\eta=0.1$: $\mathcal A_{L,\eta}(1)$ | $L=20$: 0.2050, $L=100$: 0.2363, $L=400$: 0.2428 → 극한 $(1-3\eta)^2/2=0.245$ |
| (7.2), 무작위 $z\ge0$, $\gamma\in(0.05,1)$, 2000회 | $\max[\mathcal A(z^\gamma)-(\mathcal Az)^\gamma]=-2.7\times10^{-5}<0$ ✓ |
| $q_1\mapsto q_1+1$ 이동, $\eta$-정칙 → $\eta/2$-정칙 | $L=40$: 358쌍 모두 ✓, $L=100$: 2363쌍 모두 ✓ |

질량이 1보다 작게 수렴하는 것은 정칙성이 제외한 영역 때문입니다 (정규화하지 않은 평균).

### 물리적 의미

$\mathcal A_{L,\eta}$는 "Parisi 위계의 깊이 $x=q/L\in(0,1)$에 대해 균등하게 평균"하는 연산입니다. 균등 격자
$m_d=d/L$에서 깊이 $d$는 Parisi 매개변수 $m=d/L$에 대응하므로, **Parisi 측도의 누적분포 변수 $x$에 대한
평균**으로 읽을 수 있습니다. 특정 깊이에서는 집중이 실패할 수 있지만 (예: 실제 계에 "상전이 깊이"가 있는 경우)
깊이 평균에서는 그 기여가 $1/L$로 희석됩니다.

---

## 문단 5. 유한 모음과 항등식 오차 (7.3)

> There are only finitely many labeled topologies of any bounded size and, at fixed $L$, only finitely
> many assignments of their depths. Thus errors in Theorem 6.5 can be maximized over any of the finite
> collections used below before taking $N\to\infty$. We denote such a maximum by
> $\varepsilon_{N,L,k}$; for each fixed $L,k$,
> $$\varepsilon_{N,L,k}\longrightarrow0.\tag{7.3}$$
> Constants multiplying this error may depend arbitrarily on $L$.

### 해석

정리 6.5는 나무·제약마다 개별 수렴만 줍니다. 그러나 $L$과 크기 $k$를 고정하면 관련 나무·제약·$f$ (단항식)가
유한 개이므로 최대값도 $\to0$. ✓ 이 덕분에 "$L$에 의존하는 상수 × $\varepsilon_{N,L,k}$"는
$\limsup_N$에서 사라집니다. 반면 $L$에 균등한 것이 필요한 항 (예: $C/L$)은 따로 추적합니다.

---

## 문단 6. 정리 7.1

> **Theorem 7.1.** For every fixed labeled topology $S$,
> $$\lim_{L\to\infty}\limsup_{N\to\infty}\mathcal A_{L,\eta}\mathrm{Var}(R_S)=0\qquad(\eta>0),\tag{7.4}$$
> where only the $b(S)$ branching depths are averaged. For a singleton, whose average has no
> coordinates, $\mathrm{Var}(R_S)\to0$ as $N\to\infty$ at every fixed $L$.

### 해석

- $\mathrm{Var}(R_S)$: 깊이 배정 $\mathbf q$를 고정하고, 그 모양으로 나무를 뽑았을 때 (뿌리 포함) $R_S$의 분산.
  깊이 배정마다 하나의 수이므로 $\mathcal A$로 평균할 수 있습니다.
- 극한 순서: $N\to\infty$ (Lemma 6.2의 수열, $L$ 고정) 다음 $L\to\infty$.
- 단일 잎 $S=\{a\}$: $R_S=\frac1N\sum_i\sigma_i^a$ (자화). 깊이 좌표가 없고, 각 $L$에서 $\mathrm{Var}\to0$.
  정리 6.5의 spin anchor, $k=0$ 항등식 ($\mathbb E[fR_{a_*}]\approx\mathbb Ef\,\mathbb ER_{a_*}$)에서 $f=R_{a}$로
  두면 바로 나옵니다 (7.4절 증명 첫 줄).

### 물리적 의미

$\mathrm{Var}(R_S)\to0$은 multi-overlap의 **self-averaging**이자, 지정한 상태 구조 안에서 multi-overlap이
결정적이라는 뜻입니다. 2-replica의 경우 이것은 "같은 깊이-$d$ 상태 안의 두 replica의 overlap은 $q_d$로
고정된다" — Parisi 해의 $q(x)$ 계단 함수 그림 — 와 같습니다. 희석 모형에서는 모든 차수의 $R_S$가 필요하므로
($P(q)$ 하나로 부족) 위상 $S$ 전체에 대해 증명합니다.

---

## 문단 7. 증명 계획

> The proof has two parts. First we control the randomness below a sampled prefix through the
> squared conditional covariance of the spin-product vector. This is an induction on the number of
> leaves; delaying the target splits by one level will control its signed extension coefficients. We
> then use a marker anchor to concentrate the remaining conditional mean at each fixed depth.
> Averaging over depths is essential when combining the two estimates.

### 해석

| 단계 | 내용 | 절 |
|---|---|---|
| 1 | 접두부 아래의 무작위성: 조건부 공분산 제곱 $v_N(S,d)$ (7.5)을 잎 수에 대한 귀납으로 제어. 목표 갈라짐을 한 칸 늦춰 부호 있는 확장 계수 (3.3절의 $\delta$ 계산)를 제어 | 7.2–7.3 |
| 2 | 남은 조건부 평균 (접두부의 함수)을 marker anchor 항등식으로 깊이마다 집중 | 7.4 |
| 3 | 두 추정을 합칠 때 깊이 평균이 필수 (깊이에 대한 연속성 Lemma 7.3) | 7.2, 7.4 |

### 물리적 의미

분산을 "상태 내부 요동" (접두부가 주어졌을 때)과 "상태 간 요동" (접두부 자체의 무작위성)으로 나누는
것은 RSB의 표준 분해 $\langle\cdot\rangle=\sum_\alpha W_\alpha\langle\cdot\rangle_\alpha$와 같습니다. 단계 1은 순수 상태
안의 clustering, 단계 2는 상태 가중치·상태 평균의 self-averaging입니다.

---

## 요약

- 7장은 정리 6.5의 항등식과 나무 표본 규칙만으로 multi-overlap 집중을 증명합니다 (모형 세부 무관).
- 정칙 깊이 배정과 정규화하지 않은 깊이 평균 $\mathcal A_{L,\eta}$ (7.1), Jensen 부등식 (7.2), 좌표 합·이동 비교.
- 유한 모음에서 항등식 오차의 최대 $\varepsilon_{N,L,k}\to0$ (7.3).
- 정리 7.1: $\lim_L\limsup_N\mathcal A_{L,\eta}\mathrm{Var}(R_S)=0$; 단일 잎은 각 $L$에서.
- 수치로 $\mathcal A(1)$의 극한, (7.2), 이동 단사성을 확인했습니다.

**다음 절 예고**: 7.2절에서 조건부 공분산 $v_N(S,d)$, 축약 부등식과 세 복사본 부등식 (Lemma 7.2), 깊이에 대한
평균 연속성 (Lemma 7.3)을 다룹니다.
