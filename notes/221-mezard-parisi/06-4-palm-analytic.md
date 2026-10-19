# 6.4 Poisson insertion and analytic extraction — 문단별 해설

원문: `build/sections/perturbations.tex` 6.4절, PDF 18–19쪽. 번호는 PDF 기준
(식 (6.13)–(6.16), Lemma 6.3, 6.4). 앞 절 참조: (6.2)–(6.4), Lemma 6.2, Lemma 3.1의 (3.5), Lemma 3.3.

이 절은 집중 (Lemma 6.1–6.2)을 **항등식**으로 바꿉니다. 도구는 두 가지입니다. (i) Poisson 과정의
Palm(Mecke) 항등식으로 "점수 하나"를 "새 섭동 하나의 삽입"으로 바꾸고, (ii) $u\ll t^q$인 매개변수
선택과 해석성으로 삽입의 Taylor 계수가 모두 0임을 보입니다.

---

## 문단 1. 시험 함수와 점수 항등식 (6.13)

> Fix an old labeled tree $\mathcal T$, a distinguished leaf $a_*$, and a bounded polynomial $f$ in
> multioverlaps of its old replicas. The polynomial and its coefficients are fixed as $N$ and the
> insertion parameters vary. The root-averaged expectation on this tree is denoted simply by
> $\mathbb Ef$. The anchor marginal is always one tilted path. Therefore (6.4) implies, for each
> fixed type $\nu$,
> $$\left|\frac{\mathbb E[fD_\nu^{a_*}]-\mathbb Ef\,\mathbb E\langle D_\nu\rangle}{c_\nu s_N}\right|\leq\|f\|_\infty e_{\nu,N}\longrightarrow0.\tag{6.13}$$

### 기호

| 기호 | 의미 |
|---|---|
| $\mathcal T$ | 저장소에서 뽑는 고정된 라벨 나무 ("old tree") |
| $a_*$ | anchor 잎: 점수를 재는 replica |
| $f$ | old replica들의 multi-overlap 다항식 (유계) |
| $D_\nu^{a_*}$ | anchor 경로 위에서 계산한 점수 (6.3) |

### 검증

$\mathbb E[fD^{a_*}]-\mathbb Ef\,\mathbb E\langle D\rangle=\mathbb E[f(D^{a_*}-\mathbb E\langle D\rangle)]$이고,
$|f|\le\|f\|_\infty$이므로 절댓값 $\le\|f\|_\infty\mathbb E|D^{a_*}-\mathbb E\langle D\rangle|$. 나무에서 잎 하나만
남기면 (사영 일관성, 3.1절) anchor 경로의 법칙은 기울인 경로 하나, 즉 $\langle\cdot\rangle$입니다. 따라서
$\mathbb E|D^{a_*}-\mathbb E\langle D\rangle|=\mathbb E\langle|D-\mathbb E\langle D\rangle|\rangle=c_\nu s_Ne_{\nu,N}$ (6.4).
Lemma 6.2(ii)로 $\to0$. ✓

### 물리적 의미

"점수가 상수로 집중하면, 점수는 다른 replica들의 어떤 관측량과도 상관이 없다." GG 항등식 유도의
첫 줄 $\mathbb E\langle fH^{a_*}\rangle\approx\mathbb E\langle f\rangle\mathbb E\langle H\rangle$과 같습니다.

---

## 문단 2. 삽입 표현 $J$와 차이 $H$: (6.14), (6.15)

> For a fixed mark specification, introduce an independent new uniform site and an independent copy
> of its mark process, and set $A=1+tg\sigma_i+ug_0S_0$. Let $Y$ be its insertion recursion from
> Lemma 3.1, and let $W_{\mathcal T}(A)$ be the updated-tree density (3.5). The expectations in the
> following display use the unmodified reservoir, extended by the independent insertion variables
> with their prior kernels:
> $$J_{N,\mathcal T}(t,u)=\mathbb E\left[f\,\frac{g_0^{a_*}S_0^{a_*}}{A^{a_*}}W_{\mathcal T}(A)\right],\tag{6.14}$$
> $$H_N(t,u)=J_{N,\mathcal T}(t,u)-\mathbb Ef\,J_{N,\{a_*\}}(t,u).\tag{6.15}$$
> In the single-anchor expression $J_{N,\{a_*\}}$, the test is $1$.

### 해석

- $A$는 **새 섭동 항 하나**입니다 (자리 $i$ 새로 균등, 표시 변수 새로 뽑음).
- $W_{\mathcal T}(A)=\prod_{\text{잎}}A^a\prod_\beta Y_\beta^{\gamma_\beta}$ (3.5): $A$를 넣은 뒤의 나무 법칙의
  밀도. 즉 $J$는 "섭동 하나를 더 넣은 계에서, anchor에서 그 섭동의 점수 $g_0S_0/A$를 잰 기대값"입니다.
- $\frac{1}{A^{a_*}}$이 $W$의 $A^{a_*}$를 지우므로 anchor는 **보호된 잎**이 됩니다 (3.2절의 canceled-anchor).
- $H_N$: 그 값이 "독립 경우" ($f$와 점수가 분리)와 얼마나 다른가.
- $J_{N,\{a_*\}}$: 잎이 anchor 하나인 나무, $f=1$.

---

## 문단 3. Lemma 6.3 (Palm identity)

> **Lemma 6.3.** If $\nu$ is a type with the specified marks, then
> $$|H_N(t_\nu,u_\nu)|\leq\|f\|_\infty e_{\nu,N}.\tag{6.16}$$
> For a fixed mark specification the function $H_N(t,u)$ is the same for all its types $j$: its base
> reservoir contains the full original Poisson families, including all types.

> *Proof.* Apply the Poisson add-one identity to the sum over type-$\nu$ terms in $D_\nu$. After
> division by its mean $c_\nu s_N$, the remaining count is again Poisson with mean $c_\nu s_N$, and
> all the other counts are unchanged. Thus the remaining model has exactly the original reservoir
> law. The distinguished term becomes an independent new insertion with parameters $t_\nu,u_\nu$. Its
> score is $g_0^{a_*}S_0^{a_*}/A^{a_*}$. The updated tree density is (3.5), so the anchor factor
> $A^{a_*}$ cancels. This proves
> $$\frac{\mathbb E[fD_\nu^{a_*}]}{c_\nu s_N}=J_{N,\mathcal T}(t_\nu,u_\nu),\qquad\frac{\mathbb E\langle D_\nu\rangle}{c_\nu s_N}=J_{N,\{a_*\}}(t_\nu,u_\nu).$$
> Equation (6.16) now follows from (6.13). In particular no type has been deleted from the law of the
> base reservoir. This proves the last assertion.

### 검증

**Mecke 공식.** 강도 $\lambda\mu$인 Poisson 점과정 $\Pi$에 대해
$\mathbb E\sum_{x\in\Pi}F(x,\Pi\setminus\{x\})=\lambda\int\mathbb E F(x,\Pi)\,\mu(dx)$.
여기서 $x$ = 종류 $\nu$ 항 하나 (자리 + 표시 변수), $F(x,\Pi\setminus x)$ = "나머지 계에 $x$를 넣은 상태에서
anchor 점수 중 $x$ 몫 × $f$". 오른쪽에서 나머지 계는 **원래 저장소와 같은 법칙** (Poisson의 add-one
불변성) — 그래서 종류 $j$마다 같은 기본 저장소가 쓰입니다. ✓

**삽입된 나무 법칙.** "저장소 + $x$"에서의 나무 기대값 = 저장소 나무 기대값에 $W_{\mathcal T}(A)$를 곱한 것
(Lemma 3.1, (3.5)). 새 표시 변수는 사전 커널로 경로에 덧붙입니다 (3.1절 끝). ✓ 점수 몫은
$g_0^{a_*}S_0^{a_*}/A^{a_*}$. ✓ 따라서 $\mathbb E[fD^{a_*}]=c_\nu s_N\,J_{N,\mathcal T}(t_\nu,u_\nu)$,
$\mathcal T=\{a_*\}$, $f=1$이면 둘째 식. ✓ 둘을 (6.13)에 넣으면 (6.16). ✓

### 수치 확인 (Mecke 항등식의 정확 계산)

장난감 저장소: 스핀 $N=2$ (고정 결합 $e^{0.4\sigma_1\sigma_2+0.3\sigma_1-0.2\sigma_2}$), $L=2$, $m_1=0.5$.
섭동 한 종류, 개수 $\mathrm{Pois}(0.6)$, 자리 균등, 각 항마다 깊이 1 Rademacher 부호 $\epsilon$,
$\psi=1+t g(\epsilon)\sigma_i+ug_0(\epsilon)\sigma_i$ (spin anchor), $t=0.25$, $u=0.05$,
$g(\pm1)=(-0.9,0.6)$, $g_0(\pm1)=(0.3,0.8)$. 나무: 잎 2개 $(a_*,b)$, 시험 $f=R_{a_*b}$.
좌변은 저장소 나무에서 $\mathbb E[fD^{a_*}]$를, 우변은 같은 저장소에 새 항을 $W_{\mathcal T}(A)$로 넣은
$\lambda J$를 개수 $\le7$까지 열거해 계산했습니다. 깊이 1 갈라짐 나무에서는
$W=A^{a_*}A^bY_0^{-m}Y_1^{m-2}$, 깊이 0 갈라짐에서는 $W=A^{a_*}A^bY_0^{-2m}Y_{1}^{m-1}Y_{1}'^{\,m-1}$입니다.

| 나무 | $\mathbb E[fD^{a_*}]$ | $\lambda J_{N,\mathcal T}$ |
|---|---|---|
| 깊이 1에서 갈라짐 | 0.02722557 | 0.02722562 |
| 깊이 0에서 갈라짐 | 0.01146499 | 0.01146500 |

차이 $\sim5\times10^{-8}$은 개수 절단 오차 ($\mathbb P(n\ge8)$ 수준)입니다. ✓

### 물리적 의미

Palm 항등식은 "무작위로 고른 섭동 항 하나를 들여다보는 것 = 섭동을 하나 새로 더하는 것"이라는
cavity 사고방식입니다. 이로써 집중 (6.13)이 **삽입 함수 $H_N(t,u)$가 작다**는 명제가 되고,
$H_N$은 $t$에 대해 해석적이라 Taylor 계수를 하나씩 읽을 수 있습니다.

---

## 문단 4. Lemma 6.4 (Vanishing insertion coefficients)

> **Lemma 6.4.** For every mark specification included in the perturbation family, old tree,
> anchor, and bounded overlap-polynomial test $f$, every Taylor coefficient at $t=0$ of $H_N(t,0)$
> tends to zero along the selected sequence.

### 해석

$u=0$으로 둔 $H_N(t,0)$을 $t$의 거듭제곱으로 전개하면, 각 계수는 (Lemma 3.3에 따라) old tree에
새 경로/옛 잎을 붙인 나무들 위의 multi-overlap 모멘트의 선형결합입니다. 그 결합이 $\to0$이라는 것이
6.5절 정리 6.5의 항등식이 됩니다.

---

## 문단 5. 증명 ① 균등 해석적 한계와 극한 $H$

> Lemma 3.3 gives a complex neighborhood $|t|,|u|<\rho$ on which the functions in (6.15) are analytic
> and uniformly bounded in $N$ and in the selected parameter vector. Shrinking $\rho$ gives a uniform
> bound on their $u$-derivatives as well. These constants may depend on the fixed tree, $L$, and
> $\|f\|_\infty$, but not on the type index $j$ in the mark specification.
>
> Each Taylor coefficient of $H_N(t,0)$ is a finite linear combination of multioverlap moments and
> products of two such moments on prescribed trees. Their coefficients are determined by the fixed
> tree, exponents, mark law, and polynomial test, and are independent of $N$. Indeed the canceled
> anchor expansion supplies finitely many extensions at any fixed order; averaging the independent
> insertion site turns its spin product into a multioverlap. These coefficients converge by Lemma
> 6.2(iii). The uniform analytic bound then implies, by the geometric bound on the Taylor tails,
> that $H_N(t,0)$ converges uniformly on each smaller disk to an analytic function $H(t)$.

### 검증

- **해석성**: $A=1+tg\sigma+ug_0S_0$에서 $|g|,|g_0|\le1$이므로 $|t|+|u|<1$에서 3.1절 "Analytic bounds"가
  적용됩니다. 커널에 균등한 한계이므로 $N$과 $\mathbf u$에 균등. ✓ $j$는 $(t,u)$의 값으로만 들어가므로
  $H_N$이라는 **함수** 자체는 $j$와 무관합니다. ✓
- **계수의 구조**: Lemma 3.3 (3.11)에서 $k$차 계수 = $\frac1{k!}\sum_Ec_E\,E_{\mathcal T_E}[H\prod_jD_j^{a_j(E)}]$,
  $D=g\sigma_i$. 새 자리 $i$를 평균하면 $\frac1N\sum_i\prod_a\sigma^a_i$ = multi-overlap (3.1), 표시 변수
  평균은 결정적 계수. $f$가 multi-overlap 다항식이므로 곱도 multi-overlap 다항식. 둘째 항 $\mathbb Ef\cdot J_{\{a_*\}}$는
  모멘트 둘의 곱. ✓ 확장 이력 $E$는 유한 개. ✓
- **수렴**: Lemma 6.2(iii)로 각 모멘트 수렴 ⇒ 각 계수 수렴. Cauchy 부등식으로 $|[t^k]H_N|\le C\rho^{-k}$이므로
  반지름 $\rho'<\rho$ 원판에서 꼬리가 기하급수로 균등하게 작고, 따라서 $H_N(\cdot,0)\to H$ 균등, $H$ 해석적. ✓

---

## 문단 6. 증명 ② $u\ll t^q$로 모든 계수 소멸

> For every sufficiently large fixed $j$, the corresponding type and Lemma 6.3 give
> $$\limsup_{N\to\infty}|H_N(j^{-1},0)|\leq C\limsup_{N\to\infty}|u_{\nu,N}|\leq2Cj^{-j}.$$
> Here the score error tends to zero with $j$ fixed, and the same function $H_N$ is used for every
> $j$, by Lemma 6.3. Hence $|H(j^{-1})|\leq2Cj^{-j}$. If the first nonzero Taylor coefficient of $H$
> had degree $q$, then $|H(j^{-1})|\geq cj^{-q}$ for all sufficiently large $j$, a contradiction.
> Thus $H$ vanishes identically near zero, proving the claim coefficient by coefficient.

### 검증

- $j^{-1}<\rho$인 $j$에서: $|H_N(j^{-1},0)|\le|H_N(j^{-1},u_\nu)|+u_\nu\sup|\partial_uH_N|
  \le\|f\|_\infty e_{\nu,N}+C u_\nu$. $e_{\nu,N}\to0$ (Lemma 6.2(ii), $j$ 고정), $u_\nu\le2j^{-j}$ (6.1). ✓
- 극한: $|H(1/j)|\le2Cj^{-j}$. ✓
- $H(t)=a_qt^q(1+O(t))$, $a_q\ne0$이면 큰 $j$에서 $|H(1/j)|\ge\frac{|a_q|}2j^{-q}$. 그런데
  $2Cj^{-j}/j^{-q}=2Cj^{q-j}\to0$ (6.1절 표). 모순. ✓ 따라서 $H\equiv0$ 근방, 즉 모든 계수 0,
  $H_N$의 계수 $\to$ $H$의 계수 $=0$. ✓

**검토 메모 — 해석성이 필수인 이유.** $j^{-j}=\exp(-\frac1t\log\frac1t)$ ($t=1/j$)는 어떤 거듭제곱보다 빨리
작아집니다. 해석성이 없다면 $e^{-1/t}$처럼 모든 차수에서 0인데 0이 아닌 함수가 있을 수 있어 논리가
무너집니다. Lemma 3.3의 균등 해석적 한계가 이 단계를 지탱합니다.

**검토 메모 — 극한 순서.** $N\to\infty$를 $j$ 고정으로 먼저 하고, 그 다음 $j\to\infty$입니다 (이 절 끝의
Remark). 이 순서 덕분에 $\nu$에 대한 균등 집중은 필요 없습니다.

### 물리적 의미

이것은 **확률적 안정성(stochastic stability)**의 정밀한 형태입니다. 크기 $t$의 섭동을 하나 더해도 overlap
통계가 바뀌지 않는다 ("$H(t)\equiv0$")는 것을, 섭동 세기의 모든 차수에서 주장합니다. Aizenman–Contucci
항등식이 SK의 $t^2$ 차 항에서 나오듯, 여기서는 모든 차수 $t^k$가 각각 하나의 항등식이 됩니다.

---

## 요약

- 점수 집중 ⇒ anchor 점수와 다른 replica 관측량의 비상관 (6.13).
- Mecke/Palm: 점수의 기대값 = 새 섭동 삽입 $J_{N,\mathcal T}(t_\nu,u_\nu)$, 기본 저장소의 법칙은 그대로
  (Lemma 6.3). 장난감 저장소에서 정확 계산으로 확인 (차이 $5\times10^{-8}$, 절단 오차).
- $H_N(t,0)$의 계수는 나무 위 multi-overlap 모멘트의 결합, 균등 해석적 ⇒ $H_N\to H$.
  $|H(1/j)|\le2Cj^{-j}$ ⇒ $H\equiv0$ (Lemma 6.4).

**다음 절 예고**: 6.5절에서 다중 색 편극(polarization)과 Rademacher 선택자 (6.18)로 Taylor 계수를
"지정한 색칠 나무 모양"마다 분리해, 정리 6.5의 나무 항등식 (6.17)을 얻습니다.
