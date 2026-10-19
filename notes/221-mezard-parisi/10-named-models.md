# 10장 Named models and the zero-temperature limit — 문단별 해설

원문: `build/sections/consequences.tex`, PDF 32–33쪽. 번호는 PDF 기준 (따름정리 10.1–10.3, 식 (10.1), Remark 10.4).
앞 장 참조: 정리 2.1, (2.1)–(2.4), 명제 4.1, (2.11).

마지막 장은 정리 2.1을 이름 있는 모형에 적용하고, $\beta\to\infty$ (바닥 상태 에너지) 공식을 얻습니다.

---

## 문단 1. 장 도입

> The standard examples of the factorization are the diluted spin models and random satisfiability models
> of Franz–Leone and Panchenko–Talagrand [FL03, PT04]. We retain the Poisson counts and sampling with
> replacement specified in (2.2).

### 해석

분해 (2.3)의 표준 예는 두 족입니다: (i) 결합이 대칭인 희석 $p$-spin (Viana–Bray 포함), (ii) 무작위 $K$-SAT의 "soft"
버전. clause 수는 Poisson, 자리는 복원 추출 — 이 모형 정의를 그대로 씁니다. (자리가 겹치는 clause나 고정된
clause 수 $\alpha N$ 같은 변형은 $O(1/N)$ 차이로 보통 같은 극한을 주지만, 이 논문은 주장하지 않습니다.)

---

## 문단 2. 따름정리 10.1 (Viana–Bray and diluted even-spin models)

> **Corollary 10.1.** Fix an even integer $p\ge2$, $\alpha>0$, and independent real random variables $J,H$
> such that $J$ has a symmetric distribution and $\mathbb E|J|+\mathbb E|H|<\infty$. For every $\beta>0$, the
> model with $\theta_\beta(s_1,\ldots,s_p)=\beta J\prod_{\ell=1}^ps_\ell$, $h_\beta=\beta H$ satisfies the
> variational formula (2.13), with the trial functional evaluated at these interaction and field laws. In
> particular, this holds for the Viana–Bray model [VB85], which is the case $p=2$.

> *Proof.* Use $a=\cosh(\beta J)$, $b=\tanh(\beta J)$, $f_\ell(s)=s$. The functions $f_\ell$ are
> deterministic independent copies, and $|b|<1$ almost surely. Symmetry makes every odd moment of $b$ zero;
> the even moments are nonnegative. Finally, $B(\theta_\beta)=\beta|J|$ and $|h_\beta|=\beta|H|$. Thus all
> hypotheses of Theorem 2.1 hold.

### 검증

- $s=\prod s_\ell\in\{\pm1\}$: $e^{\beta Js}=\cosh\beta J+s\sinh\beta J=\cosh\beta J(1+s\tanh\beta J)$. ✓
  (수치: $\beta J=0.3,-1.2,2.5$에서 오차 $\le4.4\times10^{-16}$.)
- $|b|=|\tanh\beta J|<1$, $|f|=1$ ⇒ $|b\prod f|<1$. ✓ 결정적 함수는 자명하게 "독립 복사본". ✓
- (2.4): $J$ 대칭 ⇒ $b$ 대칭 ⇒ 홀수 모멘트 0, 짝수 모멘트 $\ge0$, 따라서 $\mathbb E(-b)^n\ge0$. ✓
- (2.1): $\mathbb E\beta|J|+\mathbb E\beta|H|<\infty$. ✓ $J$에는 1차 모멘트만 요구 — 예를 들어 꼬리가 $|J|^{-2-\epsilon}$인 결합도 허용됩니다.

### 물리적 의미

Viana–Bray (1985)는 평균 차수 $c=2\alpha$의 희석 SK 모형입니다. $\pm J$ 결합에서 RS 상자성 해 ($x\equiv0$)의 범함수는
$$\mathcal B_0(\delta_0)=\log2+\alpha\,\mathbb E\log\cosh\beta J$$
(annealed pressure)이고, 스핀 글라스 전이는 $c\,\mathbb E\tanh^2\beta J=1$ (de Almeida–Thouless/Bethe 안정성 경계)에서 일어납니다.

### 수치 확인 ($\pm J$ VB, $p=2$, $\alpha=1.5$, 평균 차수 3)

RS cavity 고정점을 population dynamics (크기 $2\times10^5$, 60회 반복)로 구하고 $\mathcal B_0$을 계산, 작은 $N$의 정확한 $F_N$
(완전 열거, 무질서 표본 60–150개)과 비교했습니다. 명제 4.1은 **모든 $N$에서** $F_N\le\mathcal B_r$을 주므로 작은 $N$에서도 성립해야 합니다.

| $\beta$ | $c\tanh^2\beta$ | annealed $\mathcal B_0(\delta_0)$ | RS 고정점 $\mathcal B_0$ ($q=\mathbb E\tanh^2x$) | $F_{10}$ | $F_{14}$ | $F_{18}$ |
|---|---|---|---|---|---|---|
| 0.4 | 0.43 | 0.81008 | 0.81041 ($q=0$) | 0.804(5) | 0.806(4) | 0.803(4) |
| 1.0 | 1.74 | 1.34382 | 1.33687 ($q=0.33$) | 1.205(16) | 1.232(12) | 1.283(19) |
| 1.5 | 2.46 | 1.97631 | 1.89824 ($q=0.55$) | 1.649(27) | 1.707(20) | 1.763(25) |

- 상자성 영역 ($c\tanh^2\beta<1$)에서는 RS 고정점이 $q=0$이고 annealed와 같습니다 (차이 $3\times10^{-4}$는 population 표본 오차).
- 스핀 글라스 영역에서는 $q>0$인 RS 해가 annealed보다 **낮은** 위쪽 한계를 줍니다. 정리 2.1에 따르면 참값은 모든 $r$에 대한
  infimum이고, 1RSB 이상에서 더 내려갈 수 있습니다 (여기서는 계산하지 않음).
- 정확한 $F_N$은 모든 경우 $\mathcal B_0$ 아래에 있습니다 ✓. $N$이 커질수록 증가하는 것은 유한 크기 효과입니다.

---

## 문단 3. 따름정리 10.2 (Soft random even-$K$ SAT)

> **Corollary 10.2.** Fix an even integer $K\ge2$ and $\alpha>0$. Let $\varepsilon_1,\ldots,\varepsilon_K$ be
> independent fair signs and let $W\ge0$ be independent of the signs, with $\mathbb EW<\infty$. For every
> $\beta>0$, the interaction
> $$\theta_\beta(s_1,\ldots,s_K)=-\beta W\prod_{\ell=1}^K\frac{1+\varepsilon_\ell s_\ell}{2},\qquad h=0,$$
> satisfies (2.13). The choice $W=1$ is the soft random even-$K$ SAT model; $W$ gives an independent
> nonnegative clause weight.

> *Proof.* The product $I_\varepsilon(s)=\prod_\ell(1+\varepsilon_\ell s_\ell)/2$ takes values in $\{0,1\}$ and
> indicates a violated clause. Therefore $e^{\theta_\beta(s)}=1+(e^{-\beta W}-1)I_\varepsilon(s)$. Take $a=1$,
> $b=e^{-\beta W}-1$, and $f_\ell(s)=(1+\varepsilon_\ell s)/2$. The functions are independent copies and
> independent of $b$. Since $0\le-b<1$, the strict product condition and every positivity inequality hold.
> Moreover, $B(\theta_\beta)=\beta W$, so Theorem 2.1 applies.

### 검증

- $I_\varepsilon(s)=1$ ⇔ 모든 $\ell$에서 $s_\ell=\varepsilon_\ell$ (리터럴이 모두 거짓 — 부호 규약상 "위반"). $I\in\{0,1\}$ ⇒
  $e^{-\beta WI}=1+(e^{-\beta W}-1)I$. ✓ (수치: $\beta W=0.5,3$에서 오차 $\le7\times10^{-18}$.)
- $f_\ell=(1+\varepsilon_\ell s)/2\in\{0,1\}$, i.i.d. (부호 독립), $b$는 $W$의 함수라 $f$와 독립. ✓
- $-b=1-e^{-\beta W}\in[0,1)$ ⇒ $|b\prod f|<1$, $\mathbb E(-b)^n\ge0$. ✓ $B(\theta)=\beta W$ (2.1). ✓

### 물리적 의미

"soft" SAT: 위반된 clause마다 에너지 $W$ (기본 1)의 벌점, 온도 $1/\beta$. $\beta\to\infty$에서 위반 clause 수의 최소화
(MAX-SAT)가 됩니다. 1RSB cavity 방법 (Mézard–Parisi–Zecchina 2002)이 예측한 SAT/UNSAT 전이와 군집 상들의 엄밀한
변분 공식이 짝수 $K$에서 양의 온도마다 성립한다는 뜻입니다.

### 검토 메모 — 짝수 $K$ 가정은 어디에 쓰이는가

논문 전체에서 $p$의 짝수성은 4장의 볼록성 단계 (`upper.tex`, "Since $p$ is even")에서만 쓰입니다 (원문 검색으로 확인).
그 단계의 괄호 $P^p-pPB^{p-1}+(p-1)B^p$는 $P,B\ge0$이면 **모든** $p\ge1$에서 $x^p$의 $[0,\infty)$ 위 볼록성으로 음이 아닙니다.
SAT에서는 $f\ge0$이므로 $P_{\mathcal T}=\frac1N\sum_i\mathbb E_f\prod_af(\sigma_i^a)\ge0$, $\bar f(x)=(1+\varepsilon\tanh x)/2\ge0$ ⇒
$B_{\mathcal T}\ge0$입니다. 따라서 이 해설이 확인한 범위에서는 **홀수 $K$ SAT에서도 같은 증명이 그대로 성립하는 것으로
보입니다** (Panchenko–Talagrand 2004의 위쪽 한계가 모든 $K$에서 성립하는 것과 같은 이유). 논문은 이것을 주장하지 않고
Remark 10.4에서 3-SAT을 다른 논문으로 미루고 있으므로, 이 관찰은 저자 확인이 필요한 사항으로 남겨 둡니다.

---

## 문단 4. 비례하지 않는 에너지 점수

> For the spin model, define the unscaled energy score by
> $$\mathcal E_N(\sigma)=\sum_{k=1}^{M_N}J_k\prod_{\ell=1}^p\sigma_{i_{\ell,k}}+\sum_{i=1}^NH_i\sigma_i.$$
> For the satisfiability model, put
> $$\mathcal E_N(\sigma)=-\sum_{k=1}^{M_N}W_k\prod_{\ell=1}^K\frac{1+\varepsilon_{\ell,k}\sigma_{i_{\ell,k}}}{2}.$$
> These scores and their disorder laws do not depend on $\beta$; in both cases the partition function is
> $Z_N(\beta)=\sum_\sigma e^{\beta\mathcal E_N(\sigma)}$. Let $\mathcal B_{r,\beta}$ denote the functional (2.11)
> for the corresponding laws at inverse temperature $\beta$.

### 해석

$\mathcal E_N=-H_N/\beta$ (온도를 뺀 "점수" = 음의 에너지). 무질서가 $\beta$와 무관하므로 같은 표본에서 $\beta$만 바꿀 수 있습니다.
SAT에서 $-\mathcal E_N$은 (가중) 위반 clause 수.

---

## 문단 5. 따름정리 10.3 (Zero-temperature variational limit)

> **Corollary 10.3.** For each model in Corollaries 10.1 and 10.2, the limit
> $g=\lim_{N\to\infty}\frac1N\mathbb E\max_\sigma\mathcal E_N(\sigma)$ exists and satisfies
> $$g=\lim_{\beta\to\infty}\frac1\beta\inf_{r\ge0}\inf_{\zeta,\mathbf m}\mathcal B_{r,\beta}(\zeta,\mathbf m).\tag{10.1}$$
> More precisely, the expression inside the temperature limit lies in $[g,g+\log(2)/\beta]$. For unit-weight
> SAT, the limiting expected minimum number of violated clauses per variable is $-g$.

> *Proof.* Write $g_N=N^{-1}\mathbb E\max_\sigma\mathcal E_N(\sigma)$ and $P_N(\beta)=N^{-1}\mathbb E\log Z_N(\beta)$.
> The first-moment assumptions make $g_N$ finite and uniformly bounded. Since there are $2^N$ spin
> configurations, $g_N\le\frac{P_N(\beta)}\beta\le g_N+\frac{\log2}{\beta}$. For each fixed $\beta>0$, Theorem 2.1
> gives $P_N(\beta)\to I(\beta)$, where $I(\beta)=\inf_{r,\zeta,\mathbf m}\mathcal B_{r,\beta}(\zeta,\mathbf m)$. Hence
> $\limsup_Ng_N\le\frac{I(\beta)}\beta\le\liminf_Ng_N+\frac{\log2}{\beta}$. Letting $\beta\to\infty$ proves that $g_N$
> converges to a limit $g$. Taking $N\to\infty$ in the finite-volume bounds now gives
> $g\le I(\beta)/\beta\le g+\log(2)/\beta$, proving (10.1). In the satisfiability model, maximizing the negative
> violation count is the same as minimizing that count.

### 검증

- $|g_N|\le\frac1N\mathbb E[\sum_k|J_k|+\sum_i|H_i|]=\alpha\mathbb E|J|+\mathbb E|H|$ (SAT: $\alpha\mathbb EW$). ✓
- $e^{\beta\max\mathcal E}\le Z_N\le2^Ne^{\beta\max\mathcal E}$ ⇒ $\max\mathcal E\le\frac1\beta\log Z\le\max\mathcal E+\frac{N\log2}\beta$, $N$으로 나누고 기대값. ✓
- 극한: $\limsup g_N\le I/\beta$, $I/\beta\le\liminf g_N+\log2/\beta$ ⇒ $\limsup g_N-\liminf g_N\le\log2/\beta\to0$ ⇒ $g_N\to g$. ✓
  그 뒤 $g\le I(\beta)/\beta\le g+\log2/\beta$ ⇒ (10.1). ✓

### 수치 확인 (한 표본, $\pm J$ VB, $N=14$, $\alpha=1.5$)

| $\beta$ | $g_N$ | $P_N/\beta$ | $g_N+\log2/\beta$ |
|---|---|---|---|
| 0.5 | 1.0000 | 1.7792 | 2.3863 |
| 1 | 1.0000 | 1.2985 | 1.6931 |
| 2 | 1.0000 | 1.1337 | 1.3466 |
| 4 | 1.0000 | 1.0659 | 1.1733 |
| 8 | 1.0000 | 1.0329 | 1.0866 |

(한 표본에서는 기대값 없이 같은 부등식이 점별로 성립합니다.) ✓

### 물리적 의미

바닥 상태 에너지 밀도 (VB에서 $-g$, SAT에서 최소 위반 수 $-g$)가 "양의 온도 Parisi 공식의 $T\to0$ 극한"으로 주어집니다.
물리 문헌의 영온도 cavity (energetic 1RSB, "warning propagation"/survey 계산)는 $\beta\to\infty$와 $\inf$의 순서를 바꾸고
$m\to y/\beta$로 재척도화한 극한 범함수를 쓰는데, 이 따름정리는 그 교환을 정당화하지 **않으며** 양의 온도 공식의 극한만
주장합니다. 오차가 $\log2/\beta$로 균등하다는 점이 쓸모 있습니다.

---

## 문단 6. 시험 위계에 관한 주의

> The infimum in (10.1) is taken over all finite hierarchies separately at each positive temperature. The
> formula does not require attainment or a limiting hierarchy.

### 해석

$\beta$마다 최적 $r$, $\zeta$, $\mathbf m$이 다를 수 있고, 최적점이 존재할 필요도, $\beta\to\infty$에서 시험 법칙이 수렴할 필요도
없습니다. 위 문단의 "순서 교환은 별개 문제"와 같은 이야기입니다.

---

## 문단 7. Remark 10.4 (3-SAT)

> The even-arity hypothesis in Corollary 10.2 excludes random 3-SAT. For that model, the companion
> [OpenAIThreeSAT2026, Theorem 8.4] gives an exact soft-pressure formula over finite rational trials for a
> Poisson number of clauses whose variable positions are sampled independently with replacement. Its
> sign-indexed message pairs need not form a probability distribution, and its trial functional differs
> from (2.11).

### 해석

홀수 $K$ (특히 3-SAT)는 동반 논문이 다루며, 거기서는 메시지가 부호별 쌍이고 확률분포일 필요가 없으며 범함수도 다르다고
합니다. 문단 3의 검토 메모와 관련해: 이 Remark는 "이 논문의 증명이 홀수 $K$에서 깨진다"고 말하지는 않습니다. 짝수성이
쓰이는 유일한 곳 (4장 볼록성)이 SAT에서는 $P,B\ge0$으로 대체될 수 있어 보이므로, 같은 범함수 (2.11)로 3-SAT의 soft
pressure 공식도 성립할 가능성이 있습니다. 두 공식 (이 논문의 (2.11)과 동반 논문의 것)이 같은 값을 주는지는 이 해설의
범위 밖이며, 독자가 확인할 과제로 남깁니다.

---

## 요약

- 따름정리 10.1: 대칭 결합 $J$ (1차 모멘트만)의 희석 짝수 $p$-spin, 특히 Viana–Bray에서 정리 2.1 성립
  ($a=\cosh\beta J$, $b=\tanh\beta J$, $f(s)=s$). 수치: RS 고정점이 상자성 영역에서는 annealed와 같고 스핀 글라스 영역에서는 더
  낮은 위쪽 한계를 주며, 작은 $N$의 정확한 $F_N$이 언제나 그 아래에 있음.
- 따름정리 10.2: soft 짝수 $K$-SAT ($a=1$, $b=e^{-\beta W}-1\in(-1,0]$, $f=(1+\varepsilon s)/2$).
- 따름정리 10.3: 바닥 상태 점수 밀도 $g$ 존재, $I(\beta)/\beta\in[g,g+\log2/\beta]$.
- 검토 메모: 짝수성은 4장에서만 쓰이고 SAT에서는 $P,B\ge0$이라 홀수 $K$에서도 같은 증명이 될 것으로 보임 (논문은 주장하지 않음).

**마무리**: 이것으로 4–10장의 문단별 해설을 마칩니다. 전체 진행 상황과 파일 목록은 [README](README.md)에 있습니다.
