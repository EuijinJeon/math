# 2장 The model and the variational principle + 2.1 The hierarchical cavity functional — 문단별 해설

원문: `build/sections/model.tex`, PDF 3–5쪽. 번호는 PDF 기준 (식 (2.1)–(2.13), 정리 2.1).

이 장은 모형, 가정, 시험 범함수 $\mathcal B_r$, 주 정리를 정의합니다. 이후 모든 장이 이 정의를 씁니다.

---

## 문단 1. 모형 (2.1), (2.2)

> Fix an even integer $p\ge2$ and $\alpha>0$. Let $\theta$ be a random real function on $\{-1,1\}^p$ and let
> $h$ be a real random variable. Write $B(\theta)=\max_s|\theta(s)|$ and assume
> $$\mathbb EB(\theta)+\mathbb E|h|<\infty.\tag{2.1}$$
> For independent $M_N\sim\mathrm{Pois}(\alpha N)$, independent copies $\theta_k$ of $\theta$, independent copies
> $h_i$ of $h$, and independent uniform indices $i_{\ell,k}\in[N]=\{1,\ldots,N\}$, set
> $$-H_N(\sigma)=\sum_{k=1}^{M_N}\theta_k(\sigma_{i_{1,k}},\ldots,\sigma_{i_{p,k}})+\sum_{i=1}^Nh_i\sigma_i,\qquad Z_N=\sum_{\sigma\in\{-1,1\}^N}e^{-H_N(\sigma)},\qquad F_N=\frac1N\mathbb E\log Z_N.\tag{2.2}$$
> All families in this definition are mutually independent. In particular, indices are sampled with
> replacement. The model parameters and disorder laws are fixed as $N$ varies.

### 기호

| 기호 | 의미 |
|---|---|
| $p$ (짝수) | clause의 arity (몇 체 상호작용) |
| $\alpha$ | clause 밀도: 평균 $\alpha N$개, 스핀당 평균 차수 $\alpha p$ |
| $\theta$ | 무작위 clause 함수 (온도 $\beta$는 $\theta$ 안에 포함, 예: $\beta J s_1s_2$) |
| $h$ | 무작위 외부장 |
| $B(\theta)$ | clause의 최대 크기 |
| $F_N$ | pressure (자유에너지 밀도의 $-\beta$배) |

### 해석

- (2.1)은 **1차 모멘트만** 요구합니다. 결합 $J$가 Cauchy처럼 분산이 무한이어도, 평균이 유한하면 됩니다.
- Poisson 개수 + 복원 추출: 계산을 쉽게 하는 표준 선택입니다. Poisson의 add-one 성질 (4장 Poisson 미분, 5장 분할,
  6.4절 Mecke)이 계속 쓰입니다. 같은 자리가 한 clause에 두 번 나오는 일은 $O(1/N)$로 드뭅니다.

### 물리적 의미

$\alpha$는 그래프의 연결도를 정합니다. 평균 차수 $c=\alpha p$가 작으면 거대 연결 성분이 없고 (trivially 상자성),
크면 고리가 많은 희석 그래프가 됩니다. 이 논문의 결과는 **모든 $\alpha$**에서 성립합니다.

---

## 문단 2. 분해와 양성 가정 (2.3), (2.4)

> The interaction hypotheses are the existence of a representation
> $$e^{\theta(s_1,\ldots,s_p)}=a\Bigl(1+b\prod_{\ell=1}^pf_\ell(s_\ell)\Bigr),\qquad\Bigl|b\prod_{\ell=1}^pf_\ell(s_\ell)\Bigr|<1\quad\text{a.s.},\tag{2.3}$$
> for every spin tuple, where $a>0$ and $b$ are real random variables, the $f_\ell:\{-1,1\}\to\mathbb R$ are
> independent copies of one random function, $b$ is independent of them, and
> $$\mathbb E[(-b)^n]\ge0\qquad(n\ge1).\tag{2.4}$$
> The expectations in (2.4) are interpreted as finite real expectations. This is automatic in the
> nondegenerate case: independence and the strict product bound force $b$ and $\max_s|f_1(s)|$ to be
> essentially bounded, as shown in Proposition 4.1. If the product term vanishes identically, the
> interaction is spin independent and one may take $b=0$. The multiplier $a$ may depend on all the other
> variables in the representation; no separate integrability of $\log a$ is assumed.

### 해석

| 성분 | 역할 | Viana–Bray ($\beta Js_1s_2$) | soft SAT |
|---|---|---|---|
| $a$ | 스핀 무관 상수 (무거운 꼬리를 흡수) | $\cosh\beta J$ | $1$ |
| $b$ | 결합 세기 | $\tanh\beta J$ | $e^{-\beta W}-1\le0$ |
| $f_\ell$ | 각 다리가 스핀을 읽는 방식 | $f(s)=s$ | $(1+\varepsilon_\ell s)/2$ |

- (2.3): clause가 **각 다리에 대해 곱으로 분해되는 한 개의 "모드"**만 가진다는 구조 가정. 4장에서 이 구조 덕분에
  보간 remainder가 $P^p-pPB^{p-1}+(p-1)B^p$ 꼴로 정리됩니다.
- (2.4): $b$의 분포가 "음수 쪽으로 기울거나 대칭". VB에서는 $J$ 대칭이면 홀수 모멘트 0. 4장 수치 확인에서 $b=+0.8$
  (강자성형)이면 보간 부등식이 실제로 깨지는 것을 보였습니다.
- 유계성 ($\|b\|_\infty$, $\|f\|_\infty<\infty$)은 가정이 아니라 귀결 (명제 4.1 증명 첫 단계).

### 물리적 의미

(2.3)–(2.4)는 Franz–Leone/Panchenko–Talagrand의 표준 조건입니다. 직관적으로 (2.4)는 "좌절(frustration)을 만드는 방향의
상호작용"을 허용하고 "강자성으로 정렬시키는 순수한 방향"은 배제합니다. 강자성 모형에서는 RS/RSB cavity 범함수가
위쪽 한계가 아닐 수 있기 때문입니다. 아래쪽 한계 (5–8장)는 이 가정을 쓰지 않습니다.

---

## 문단 3. 2.1절 도입과 $q_x$, $C_\theta$, $U_\theta$ (2.5), (2.6)

> We give the power-mean form of the Panchenko–Talagrand functional [PT04, Section 5]. A message $x$
> specifies a probability distribution on one spin. The site term inserts a new spin with its incident
> interactions; the edge term corrects for interactions counted in that insertion.
>
> For $x\in\mathbb R$ let $q_x(s)=e^{xs}/(2\cosh x)$. Define
> $$C_\theta(x_1,\ldots,x_p)=\sum_{s\in\{-1,1\}^p}e^{\theta(s)}\prod_{\ell=1}^pq_{x_\ell}(s_\ell),\tag{2.5}$$
> $$U_\theta(x_1,\ldots,x_{p-1};\varepsilon)=\log\sum_{s\in\{-1,1\}^{p-1}}e^{\theta(s_1,\ldots,s_{p-1},\varepsilon)}\prod_{\ell=1}^{p-1}q_{x_\ell}(s_\ell).\tag{2.6}$$
> Both $|\log C_\theta|$ and $|U_\theta|$ are bounded by $B(\theta)$, uniformly in the messages.

### 기호

| 기호 | 의미 |
|---|---|
| 메시지 $x$ | 한 스핀의 분포 $q_x$를 정하는 유효장. $\langle s\rangle=\tanh x$ |
| $C_\theta$ | 다리 $p$개가 모두 메시지인 clause의 분배함수 비 (edge 항) |
| $U_\theta(\cdot;\varepsilon)$ | 다리 $p-1$개가 메시지, 나머지 하나가 새 스핀 $\varepsilon$일 때 clause가 새 스핀에 주는 로그 가중치 |

### 검증

$C_\theta$와 $e^{U_\theta}$는 $e^{\theta(s)}$의 확률 평균이므로 $[e^{-B},e^B]$ 안. ✓
**수치**: 무작위 $\theta$ ($p=2,3,4$), 무작위 메시지 3000회에서 $\max(|\log C|/B,|U|/B)=0.99999999896\le1$. ✓

### 물리적 의미

Bethe 근사의 표준 재료입니다. 새 스핀 $\varepsilon$에 clause $a$가 보내는 cavity "u-메시지"는
$e^{U_\theta(x;\varepsilon)}\propto e^{u\varepsilon}$이고, VB에서는 $u=\operatorname{arctanh}(\tanh\beta J\tanh x)$입니다
(10장 수치 확인의 population dynamics가 이 식). $C_\theta$는 clause 하나의 "edge free energy"입니다.

---

## 문단 4. 위계 메시지 사슬 (2.7)

> Write $\mathcal P(E)$ for the Borel probability measures on $E$. Let $\mathcal M_1=\mathcal P(\mathbb R)$ and
> $\mathcal M_{j+1}=\mathcal P(\mathcal M_j)$, equipped with the topology of weak convergence and its Borel
> sigma-field. Fix $r\ge1$, $\zeta\in\mathcal M_{r+1}$, and $0<m_1<\cdots<m_r<1$. For each message label
> $\omega$ independently, draw
> $$\eta_0^\omega\sim\zeta,\qquad\eta_{d+1}^\omega\mid\eta_d^\omega\sim\eta_d^\omega\ (0\le d\le r-2),\qquad x^\omega\mid\eta_{r-1}^\omega\sim\eta_{r-1}^\omega.\tag{2.7}$$
> At $r=1$, this means that each label first draws a random probability measure $\eta_0$ with law $\zeta$,
> then draws $x$ with law $\eta_0$. Higher levels repeat this sampling of measures. All these variables are
> independent of the physical disorder. Use different labels for $x_1,\ldots,x_p$ and for $x_\ell^j$,
> $j\ge1$, $1\le\ell<p$.

### 해석

| 층 | 변수 | 공간 | 물리적 의미 (1RSB, $r=1$) |
|---|---|---|---|
| 뿌리 | $\eta_0\sim\zeta$ | $\mathcal M_r$ | 자리(무질서)마다 다른, 상태들 위의 장 분포 $P_i(h)$ |
| 깊이 $d$ | $\eta_d$ | $\mathcal M_{r-d}$ | 깊이 $d$ 상태 안의 하위 분포 |
| 깊이 $r$ | $x$ | $\mathbb R$ | 가장 깊은 상태에서의 장 |

라벨마다 독립: **서로 다른 이웃이 보내는 메시지는 독립** — Bethe 근사의 핵심 가정이 시험 법칙 안에 내장되어 있습니다.
3장 이후의 언어로는 $\eta_d$가 경로의 깊이-$d$ 변수, $x$가 깊이 $r$ 변수, 스핀이 깊이 $L=r+1$입니다.

---

## 문단 5. site 항과 edge 항 (2.8), (2.9)

> Take independent $k\sim\mathrm{Pois}(\alpha p)$, $\theta,\theta_1,\ldots$, and $h$, and put
> $$V_{\rm s}=\frac12\sum_{\varepsilon=\pm1}\exp\Bigl(h\varepsilon+\sum_{j=1}^kU_{\theta_j}(x_1^j,\ldots,x_{p-1}^j;\varepsilon)\Bigr),\tag{2.8}$$
> $$V_{\rm e}=C_\theta(x_1,\ldots,x_p).\tag{2.9}$$

### 해석

- $V_{\rm s}$: 새 스핀이 장 $h$와 clause $k\sim\mathrm{Pois}(\alpha p)$개 (Poisson 차수)를 통해 메시지를 받을 때의 국소 분배함수
  (½로 정규화). 5장 (5.6)의 $A_{\rm s}$에서 저장소 스핀을 메시지로 바꾼 것 (8.3절에서 정확히 이 대응을 씀).
- $V_{\rm e}$: clause 하나를 메시지 $p$개 사이에 넣는 비용.

---

## 문단 6. power mean과 $\mathscr F_d$ (2.10)

> For $0\le d<r$, let $\mathscr F_d$ be generated by all the physical disorder in these expressions and all
> $\eta_j^\omega$, $0\le j\le d$. Set
> $$T_rV=V,\qquad T_dV=\left(\mathbb E[(T_{d+1}V)^{m_{d+1}}\mid\mathscr F_d]\right)^{1/m_{d+1}}\quad(d=r-1,\ldots,0).\tag{2.10}$$
> Only auxiliary messages are integrated in these conditional expectations. For example, at depth one,
> $T_0V=(\mathbb E_x[V^{m_1}\mid\boldsymbol\eta_0])^{1/m_1}$. At depth two, each label draws $\eta_0\sim\zeta$, then
> $\eta_1\mid\eta_0\sim\eta_0$, and then $x\mid\eta_1\sim\eta_1$, and
> $$T_0V=\left(\mathbb E_{\boldsymbol\eta_1}\left[\left(\mathbb E_{\boldsymbol x}[V^{m_2}\mid\boldsymbol\eta_1]\right)^{m_1/m_2}\,\middle|\,\boldsymbol\eta_0\right]\right)^{1/m_1}.$$
> Here bold symbols collect all message labels in $V$; physical disorder is held fixed throughout,
> including in the two abbreviated displays.

### 검증

$r=2$: $T_1V=(\mathbb E_x[V^{m_2}\mid\mathscr F_1])^{1/m_2}$, $T_0V=(\mathbb E[(T_1V)^{m_1}\mid\mathscr F_0])^{1/m_1}$ ⇒
$(T_1V)^{m_1}=(\mathbb E_x[V^{m_2}])^{m_1/m_2}$, 표시된 식과 같음. ✓ 지수는 $m_{d+1}$ (깊이 $d+1$ 변수를 적분할 때). 3장의
$K_d$가 깊이 $d$ 변수를 $m_d$로 기울이는 것과 일치합니다.

### 수치 확인 (power mean의 극한과 단조성)

$V\sim$ log-normal$(0,1)$, 표본 20만:

| $m$ | $10^{-4}$ | 0.25 | 0.5 | 0.75 | 1 |
|---|---|---|---|---|---|
| $(\mathbb EV^m)^{1/m}$ | 0.99873 | 1.13194 | 1.28328 | 1.45530 | 1.65102 |

$m\to0$: $\exp\mathbb E\log V=0.99868$ (quenched), $m=1$: $\mathbb EV=1.65102$ (annealed). ✓ $m$에 대해 증가 (Lyapunov 부등식). ✓

### 물리적 의미

power mean은 Monasson의 $Z^m$ 재가중입니다. 깊이 $d+1$의 상태 $\alpha$가 자유에너지 $f_\alpha$를 가질 때 상태들에 대한
평균을 $e^{-m\beta Nf_\alpha}$로 가중하는 것과 같고, $m$은 Parisi 매개변수 (상태 무게 분포 $\mathrm{PD}(m)$의 지수)입니다.
$m\to0$은 "모든 상태를 똑같이 quenched 평균", $m=1$은 "Gibbs 측도 그대로 annealed 평균"입니다.

---

## 문단 7. 범함수 $\mathcal B_r$과 $\Phi_r$ (2.11); $r=0$

> Define
> $$\mathcal B_r(\zeta,\mathbf m)=\log2+\mathbb E\log T_0V_{\rm s}-\alpha(p-1)\mathbb E\log T_0V_{\rm e},\qquad\Phi_r=\inf_{\zeta,\mathbf m}\mathcal B_r(\zeta,\mathbf m).\tag{2.11}$$
> At $r=0$, the messages are independent with common law $\zeta\in\mathcal P(\mathbb R)$ and the operators $T_d$
> are omitted; this defines $\mathcal B_0(\zeta)$ and $\Phi_0$.

### 해석

Bethe 자유에너지 장부: **스핀 하나 추가 ($\log2+\log V_{\rm s}$) − 과다 계산된 clause ($\alpha(p-1)$개 × $\log V_{\rm e}$)**.
스핀 하나를 넣으면 clause $\alpha p$개가 따라오지만 스핀당 실제 clause는 $\alpha$개이므로 $\alpha(p-1)$개를 뺍니다.
$\mathbb E$는 뿌리 (물리 무질서 + $\eta_0$)에 대한 바깥 평균. $r=0$은 RS (Bethe) 범함수입니다.

### 작은 예 (RS 상자성 해)

VB ($p=2$), $\zeta=\delta_0$ ($x\equiv0$): $U=\log\cosh\beta J$, $V_{\rm s}=\prod_j\cosh\beta J_j$, $V_{\rm e}=\cosh\beta J$ ⇒
$\mathcal B_0=\log2+2\alpha\mathbb E\log\cosh\beta J-\alpha\mathbb E\log\cosh\beta J=\log2+\alpha\mathbb E\log\cosh\beta J$ (annealed pressure). ✓
10장 수치 확인에서 이 값과 population dynamics RS 해를 비교했습니다.

---

## 문단 8. 유한성 (2.12)

> The quantities in (2.11) are finite without any moment assumption on the trial messages. Indeed, the
> power-mean operators preserve pointwise multiplicative bounds, and
> $$|\log T_0V_{\rm s}|\le|h|+\sum_{j=1}^kB(\theta_j),\qquad|\log T_0V_{\rm e}|\le B(\theta).\tag{2.12}$$

### 검증

$e^{-c}\le V\le e^{c}$ ($c$는 뿌리 가측)이면 각 power mean도 같은 구간. $V_{\rm s}$는 문단 3의 한계로 $[e^{-|h|-\sum B_j},e^{|h|+\sum B_j}]$. ✓
기대값: $\mathbb E|h|+\alpha p\mathbb EB<\infty$ (2.1). ✓ **수치**: 무작위 500개 표본에서 점별로 성립. ✓
메시지 $x$에는 아무 조건도 필요 없습니다 ($|x|\to\infty$여도 $q_x$는 확률분포).

---

## 문단 9. 정리 2.1

> **Theorem 2.1.** Under (2.1)–(2.4), the thermodynamic limit exists and
> $$\lim_{N\to\infty}F_N=\inf_{r\ge0}\Phi_r.\tag{2.13}$$
>
> The right side is an infimum over finite hierarchies. The theorem does not assume that a trial law
> attains it or that a limiting infinite-depth Gibbs state has been constructed.

### 해석

- 극한 존재 + Mézard–Parisi (Panchenko–Talagrand) 공식.
- $\inf_r\Phi_r=\lim_r\Phi_r$ (깊이를 늘리면 시험 족이 커지므로 $\Phi_r$은 비증가 — $r$단 시험은 한 층을 자명하게 둔
  $r+1$단 시험으로 쓸 수 있음; 이 논문은 명시하지 않지만 표준적 관찰).
- 최적점 존재, full-RSB 극한 대상은 주장하지 않음.

### 증명 구조 (2.2절 예고)

$\le$: 4장 명제 4.1 (모든 $N$). $\ge$: 5–8장 (유계·순열 불변) + 9장 (일반화).

---

## 요약

- 모형: Poisson clause, 복원 추출, 1차 모멘트 (2.1). 구조 가정: 분해 (2.3)과 양성 (2.4).
- 메시지 $x$는 $q_x$로 한 스핀 분포를 정하고, 위계 사슬 (2.7)로 RSB 시험 법칙 $\zeta\in\mathcal M_{r+1}$을 만듭니다.
- $\mathcal B_r=\log2+\mathbb E\log T_0V_{\rm s}-\alpha(p-1)\mathbb E\log T_0V_{\rm e}$, power mean (2.10)은 Monasson 재가중.
- 정리 2.1: $\lim F_N=\inf_r\Phi_r$. $|U|,|\log C|\le B$, power mean의 극한·단조성, (2.12)를 수치로 확인.

**다음 절 예고**: 2.2절에서 증명 전략 (위쪽 한계 + 아래쪽 한계 4단계)을 정리합니다.
