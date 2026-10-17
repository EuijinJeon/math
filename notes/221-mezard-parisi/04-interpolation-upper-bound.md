# 4장 The interpolation upper bound — 문단별 해설

원문: `build/sections/upper.tex`, PDF 12–13쪽. 식·명제 번호는 PDF 기준입니다
(명제 4.1, 식 (4.1)–(4.3)). 앞 장 참조: 정리 2.1, 식 (2.1)–(2.11), Lemma 3.1, Lemma 3.2.

이 장은 정리 2.1의 **위쪽 절반** $F_N\le\inf_r\Phi_r$을 증명합니다. 모든 유한 $N$에서
성립하는 부등식이라서 극한도, 집중 부등식도 필요 없습니다. 증명은 한 문단짜리 명제 하나이지만,
안에 네 단계(퇴화 경우 → 보간 → 정규화 → 볼록성)가 있어 단계별로 나누어 읽습니다.

---

## 문단 1. 장 도입

> The interpolation method of Guerra [Guerra03], adapted to diluted systems by Franz and Leone
> [FL03] and to arbitrary finite levels by Panchenko and Talagrand [PT04], replaces each real
> interaction by $p$ independent cavity interactions. The difference is controlled by the
> convexity of $x\mapsto x^p$. We give the argument for the full trial class, including
> unbounded messages and integrable physical disorder.

### 해석

- **Guerra 보간**: SK 모형에서 Guerra는 실제 해밀토니안과 "Parisi 시험 상태로 만든 독립 장(field)
  해밀토니안"을 $t\in[0,1]$로 섞고, $t$에 대한 도함수가 $-(R_{12}-q)^2$ 꼴의 음이 아닌 양의
  음수배가 됨을 보였습니다. 그래서 시험 범함수는 언제나 실제 pressure의 위쪽 한계가 됩니다.
- **Franz–Leone**: 희석(diluted) 모형에서는 가우스 적분부분(Gaussian integration by parts)
  대신 **Poisson 미분**을 씁니다. 실제 $p$-체 clause 하나를 "각 끝점이 바깥에서 오는 cavity
  메시지를 보는" clause $p$개로 바꿉니다. Bethe 격자의 언어로 말하면, 그래프에서 clause를 하나
  잘라 내고 그 자리에 잘린 다리마다 cavity 장을 붙이는 것입니다.
- **Panchenko–Talagrand**: 이것을 유한 단계 RSB(Parisi 매개변수 $m_1<\dots<m_r$)로 확장했습니다.
  3장의 power mean 재귀가 바로 이 확장을 쓰는 언어입니다.
- **볼록성**: 남는 항(remainder)이 $P^p-pPB^{p-1}+(p-1)B^p$ 꼴이고, $p$가 짝수이면
  $x\mapsto x^p$의 볼록성으로 음이 아닙니다. $p=2$에서는 정확히 $(P-B)^2$이 되어 Guerra의
  $(R_{12}-q)^2$과 같은 모양입니다.
- **새로운 점**: 원래 논문들은 유계 메시지나 유계 상호작용을 가정했습니다. 여기서는 (2.1)의 1차
  모멘트 가정만으로, 메시지 법칙 $\zeta$에는 아무 적분 조건도 걸지 않고 증명합니다. 이것이
  가능한 이유는 (2.12)처럼 power mean이 곱셈 한계를 보존하기 때문입니다.

### 물리적 의미

보간은 "실제 그래프의 clause를 하나씩 끊어서 나무 같은 cavity 구조로 바꾸는" 과정입니다.
Bethe 근사가 정확하려면 잘린 다리의 메시지들이 서로 독립이어야 하는데, 실제로는 상관이 있습니다.
그 상관의 대가가 볼록성 항이고, 부호가 항상 같은 방향이라 시험 범함수는 **변분 위쪽 한계**가
됩니다. 물리 문헌에서 $F=\max$ 또는 $\min$이 섞여 혼란스러운 부분(replica 계산에서 $n\to0$일 때
극값의 방향이 뒤집힘)을 수학적으로는 이 한 줄의 볼록성이 정리해 줍니다. 여기서 $F_N$은
$\log Z$ (pressure)이므로 "자유에너지의 최소" 대신 "pressure의 inf"로 나타납니다.

---

## 문단 2. 명제 4.1

> **Proposition 4.1.** Under the hypotheses of Theorem 2.1, $F_N\le\mathcal B_r(\zeta,\mathbf m)$
> for every $N$ and every admissible finite-level trial law. Consequently
> $F_N\le\inf_{r\ge0}\Phi_r$.

### 해석

- "모든 $N$"에서 성립합니다. 극한을 취하지 않으므로 $\limsup_N F_N\le\inf_r\Phi_r$이 곧바로
  나옵니다.
- "admissible finite-level trial law": $r\ge0$, $\zeta\in\mathcal M_{r+1}$,
  $0<m_1<\dots<m_r<1$인 모든 시험 법칙 (2.7). $r=0$이면 RS(replica symmetric) 시험,
  $r=1$이면 1RSB입니다.
- 둘째 문장: $\Phi_r=\inf_{\zeta,\mathbf m}\mathcal B_r$ (2.11)이므로 첫 문장에서 $\inf$를 취하면
  됩니다. ✓

### 검증

$F_N\le\mathcal B_r(\zeta,\mathbf m)$이 모든 $(\zeta,\mathbf m)$에서 성립 ⇒ $F_N\le\Phi_r$
⇒ 모든 $r$에서 성립 ⇒ $F_N\le\inf_r\Phi_r$. ✓

---

## 문단 3. 증명 ① 퇴화 분해의 처리와 $b$, $f$의 유계성

> First dispose of the degenerate factorization. Put $M=\max_{s=\pm1}|f(s)|$. If $b=0$ almost
> surely or $M=0$ almost surely, the interaction is a spin-independent random constant $c$, and
> $$F_N=\mathcal B_r=\log2+\mathbb E\log\cosh h+\alpha\mathbb E c$$
> for every trial law. Otherwise choose $u,v>0$ with $\mathbb P(M\ge u)>0$ and
> $\mathbb P(|b|\ge v)>0$. Since $|b|\prod_{\ell=1}^pM_\ell<1$ almost surely, independence gives
> $$\|b\|_\infty\le u^{-p},\qquad \|M\|_\infty\le(vu^{p-1})^{-1}.$$
> Indeed, violating either bound on a set of positive probability and restricting the other
> independent factors to these lower bounds would violate the strict product condition. All
> moments used below are therefore finite.

### 기호

| 기호 | 의미 |
|---|---|
| $f$ | (2.3)의 무작위 함수 $\{\pm1\}\to\mathbb R$ 하나 (독립 복사본 $f_1,\dots,f_p$) |
| $M=\max_s\lvert f(s)\rvert$ | $f$의 크기; $M_\ell$은 $f_\ell$의 크기 |
| $c$ | 상호작용이 스핀과 무관할 때의 값. 뒤에서는 $c=\theta(1,\dots,1)$로 재정의 |
| $\lVert\cdot\rVert_\infty$ | 본질적 상한(essential sup) |

### 해석과 검증

**(i) 퇴화 경우.** $b=0$ 또는 $f\equiv0$이면 $e^{\theta(s)}=a$가 $s$에 무관하므로
$\theta\equiv c:=\log a$입니다.

- 실제 계: $Z_N=e^{\sum_k c_k}\prod_i 2\cosh h_i$이므로
  $F_N=\frac1N\mathbb E\sum_k c_k+\log2+\mathbb E\log\cosh h=\alpha\mathbb Ec+\log2+\mathbb E\log\cosh h$.
  ($\mathbb E M_N=\alpha N$, Wald 항등식.) ✓
- 시험 범함수: $U_\theta(\cdot;\varepsilon)=\log\sum_s e^c\prod q=c$, 따라서
  $V_{\rm s}=e^{\sum_{j\le k}c_j}\cosh h$이고 메시지와 무관하므로 $T_0V_{\rm s}=V_{\rm s}$.
  $\mathbb E\log T_0V_{\rm s}=\mathbb E\log\cosh h+\alpha p\,\mathbb Ec$.
  $V_{\rm e}=e^c$이므로 $\mathbb E\log T_0V_{\rm e}=\mathbb Ec$.
  (2.11): $\log2+\mathbb E\log\cosh h+\alpha p\mathbb Ec-\alpha(p-1)\mathbb Ec
  =\log2+\mathbb E\log\cosh h+\alpha\mathbb Ec$. ✓

따라서 퇴화 경우에는 부등식이 등호로 성립합니다. $\mathbb E|c|\le\mathbb EB(\theta)<\infty$이므로
모든 항이 유한합니다.

**(ii) 비퇴화 경우의 유계성.** $\mathbb P(M\ge u)>0$, $\mathbb P(|b|\ge v)>0$인 $u,v>0$를 잡습니다.

- $\|b\|_\infty\le u^{-p}$: 사건 $G=\{M_1\ge u,\dots,M_p\ge u\}$는 독립성으로
  $\mathbb P(G)=\mathbb P(M\ge u)^p>0$. 만약 $\mathbb P(|b|>u^{-p})>0$이면, $b$가 $f$들과
  독립이므로 $\mathbb P(\{|b|>u^{-p}\}\cap G)>0$이고, 그 위에서
  $|b|\prod M_\ell>u^{-p}u^p=1$이 되어 (2.3)의 $|b\prod f_\ell(s_\ell)|<1$에 모순입니다.
  (최댓값 $M_\ell$은 어떤 $s_\ell$에서 달성되므로, 각 $\ell$마다 그 $s_\ell$을 고르면 됩니다.) ✓
- $\|M\|_\infty\le(vu^{p-1})^{-1}$: 같은 방식으로 $\{|b|\ge v, M_2\ge u,\dots,M_p\ge u\}$ 위에서
  $M_1>(vu^{p-1})^{-1}$이면 곱이 1을 넘습니다. ✓

**결론.** $b$와 $f$가 본질적으로 유계이므로 $\mathbb E[(-b)^n]$ 같은 모든 모멘트가 유한합니다.
2장 본문 (2.4) 아래의 "This is automatic in the nondegenerate case"가 바로 이 논증을 가리킵니다.

### 물리적 의미

Viana–Bray에서는 $b=\tanh\beta J$, $f(s)=s$이므로 $|b|<1$, $M=1$이 자명합니다. 그러나 이 논문은
$a$가 무한히 클 수 있는 (예: $J$가 Cauchy 분포처럼 꼬리가 무거운) 경우도 허용합니다. 그래도
$e^\theta$를 $a(1+bf\cdots f)$로 쓰는 순간 "스핀에 의존하는 부분"은 자동으로 유계라는 관찰입니다.
즉 무거운 꼬리는 모두 스핀에 무관한 상수 $a$로 몰리고, 이 상수는 뒤의 정규화 단계에서
기대값을 취하기 **전에** 지워집니다.

---

## 문단 4. 증명 ② 보간 경로와 양 끝점

> *Interpolation.* Fix a trial law and set $L=r+1$. Interpolate between real interactions of mean
> $t\alpha N$ and, at each site $i$, independent cavity interactions
> $U_\theta(x_1,\ldots,x_{p-1};\sigma_i)$ of mean $(1-t)\alpha p$. Different cavity terms have
> disjoint message labels. Counts, interactions, fields, and root message measures are quenched.
> Apply the backward power-mean recursion to the spin partition function and denote its expected
> root logarithm divided by $N$ by $\varphi(t)$. For $r=0$ all messages are quenched and there is
> no auxiliary recursion. Independence between different sites throughout the recursion gives
> $$\varphi(1)=F_N,\qquad \varphi(0)=\log2+\mathbb E\log T_0V_{\rm s}.$$

### 기호

| 기호 | 의미 |
|---|---|
| $t\in[0,1]$ | 보간 매개변수 |
| $M\sim\mathrm{Pois}(t\alpha N)$ | 실제 $p$-체 clause 수 |
| $k_i\sim\mathrm{Pois}((1-t)\alpha p)$ | 자리 $i$에 붙는 cavity 항 수 |
| $U_\theta(x_1,\dots,x_{p-1};\sigma_i)$ | (2.6) cavity 항: $p-1$개 다리에 바깥 메시지 $x_\ell$ |
| $\varphi(t)$ | 보간된 계의 $\frac1N\mathbb E\log(\text{power-mean 재귀의 뿌리값})$ |
| $L=r+1$ | 경로 깊이. 깊이 $1..r$: 메시지 사슬 $\eta_1,\dots,\eta_{r-1},x$, 깊이 $L$: 스핀 |

### 해석

보간된 해밀토니안은
$$-H_t(\sigma)=\sum_{k\le \mathrm{Pois}(t\alpha N)}\theta_k(\sigma_{i_{1,k}},\dots,\sigma_{i_{p,k}})
+\sum_{i=1}^N\Bigl[h_i\sigma_i+\sum_{j\le k_i}U_{\theta_{ij}}(x^{ij}_1,\dots,x^{ij}_{p-1};\sigma_i)\Bigr]$$
입니다. 메시지 $x^{ij}_\ell$은 (2.7)의 위계 사슬에서 뽑히는 **보조 변수**이므로, 분배함수
$Z_t(\boldsymbol x)$는 메시지에 의존하고, 이를 (2.10)/(3.2)의 power mean으로 뿌리까지 올립니다.
$$\varphi(t)=\frac1N\mathbb E\log T_0Z_t .$$

- "quenched"인 것: clause 수, 상호작용 $\theta$, 장 $h$, 각 메시지 라벨의 뿌리 측도 $\eta_0^\omega$.
  이들은 $\mathbb E$로 **로그 바깥**에서 평균합니다.
- "annealed in power mean"인 것: $\eta_1,\dots,\eta_{r-1},x$. 이들은 $T_d$ 안에서
  $m_{d+1}$ 거듭제곱 평균으로 적분합니다.

### 검증

- $t=1$: cavity 항이 없으므로 메시지가 없고, power mean은 상수에 작용해 그대로입니다.
  $\varphi(1)=\frac1N\mathbb E\log Z_N=F_N$. ✓
- $t=0$: 실제 clause가 없으므로 $Z_0=\prod_i\bigl(\sum_{\sigma_i}e^{h_i\sigma_i+\sum_jU_{ij}}\bigr)
  =\prod_i 2V_{\rm s}^{(i)}$. 서로 다른 자리의 인자는 서로소인 메시지 라벨에 의존하므로
  조건부 독립이고, 독립 곱의 power mean은 곱으로 갈라집니다:
  $\mathbb E[(\prod_iV_i)^{m}\mid\cdot]=\prod_i\mathbb E[V_i^{m}\mid\cdot]$ ⇒
  $T_d\prod_iV_i=\prod_iT_dV_i$ (깊이마다 귀납). 따라서
  $\varphi(0)=\frac1N\sum_i\mathbb E\log(2T_0V_{\rm s}^{(i)})=\log2+\mathbb E\log T_0V_{\rm s}$.
  (자리마다 $k_i\sim\mathrm{Pois}(\alpha p)$로 (2.8)의 $k$와 같은 법칙.) ✓

### 물리적 의미

$t=0$의 계는 **Bethe 나무의 뿌리 $N$개를 따로 떼어 놓은 것**입니다. 각 스핀은 자기 이웃
clause $k\sim\mathrm{Pois}(\alpha p)$개를 통해 바깥 세계(메시지)만 봅니다. RSB 시험에서는 이
바깥 세계가 Parisi 위계로 조직된 상태(cluster)들의 혼합이고, power mean의 지수 $m_d$는
Monasson의 재가중 $Z^{m}$ — 즉 "상태 하나의 자유에너지에 대한 복잡도(complexity)" 가중 — 에
해당합니다. $t$를 늘리면 cavity 다리가 실제 clause로 하나씩 이어집니다.

> (작업 중 — 다음 문단부터 이어짐)
