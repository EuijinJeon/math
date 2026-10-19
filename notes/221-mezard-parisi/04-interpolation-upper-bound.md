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

---

## 문단 5. 증명 ③ Poisson 미분

> Poisson differentiation gives $\varphi'(t)/\alpha$ as the expected insertion increment of one
> real interaction minus $p$ times the increment of one cavity interaction at a uniform site. Each
> increment has absolute value at most $B(\theta)$, since the recursion preserves multiplicative
> bounds. Conditioning on the counts justifies the derivative on $(0,1)$, and the same bound gives
> continuity at the endpoints.

### 해석과 검증

**Poisson 미분 공식.** $M\sim\mathrm{Pois}(\mu)$이고 $g$가 적당히 적분 가능하면
$$\frac{d}{d\mu}\mathbb E g(M)=\mathbb E[g(M+1)-g(M)].$$
(증명: $\frac{d}{d\mu}e^{-\mu}\mu^n/n!=\pi_{n-1}-\pi_n$, 합의 순서 교환.) ✓

- 실제 clause: $\mu=t\alpha N$, $d\mu/dt=\alpha N$. $N$으로 나누면 $\alpha\,\Delta_{\rm real}$,
  여기서 $\Delta_{\rm real}=\mathbb E[\log T_0Z^{+\text{clause}}-\log T_0Z]$.
- cavity 항: 자리마다 $\mu_i=(1-t)\alpha p$, $d\mu_i/dt=-\alpha p$. $N$개 자리를 합하고 $N$으로
  나누면 $-\alpha p\cdot\frac1N\sum_i\Delta_{{\rm cav},i}=-\alpha p\,\Delta_{\rm cav}$
  (균등 자리 $i$에서의 증분). 
- 합: $\varphi'(t)/\alpha=\Delta_{\rm real}-p\,\Delta_{\rm cav}$. ✓

**증분의 한계.** clause 하나를 넣는 것은 스핀 가중치에 $A=e^{\theta(\cdot)}$를 곱하는 것이고,
Lemma 3.1에 따라 뿌리 로그는 $\log Y_0$만큼 변합니다. $e^{-B}\le A\le e^{B}$이면 Lemma 3.1의
단조성으로 $e^{-B}\le Y_0\le e^{B}$. cavity 항도 $|U_\theta|\le B(\theta)$ (2.6 아래). ✓
따라서 $|\Delta|\le\mathbb EB(\theta)<\infty$ (2.1)이고, 이 균등 한계로 미분과 기대값의 교환
(counts에 조건부로 Poisson 확률의 미분), 그리고 $t=0,1$에서의 연속성이 정당화됩니다. ✓

### 물리적 의미

Franz–Leone 방법의 핵심입니다. Gaussian 모형에서는 $\partial_t$가 Wick 정리를 거쳐 overlap의
2차식을 내지만, 희석 모형에서는 $\partial_t$가 **"clause 하나 추가"의 유한 차분**을 냅니다.
"cavity 다리 $p$개를 없애고 실제 clause 하나를 넣는" 교환의 비용이 $\varphi'$입니다.

---

## 문단 6. 증명 ④ 주장 (4.1)과 세 가지 삽입

> We claim that
> $$\varphi'(t)+\alpha(p-1)\mathbb E\log T_0V_{\rm e}\le0.\tag{4.1}$$
> All three insertions have the form $a(1+D)$ under (2.3). For a real interaction,
> $D=b\prod_\ell f_\ell(\sigma_{i_\ell})$; for a cavity interaction, replace $p-1$ of the factors by
> $\bar f(x)=\sum_s f(s)q_x(s)$; for an edge insertion, replace all $p$. In the last case the
> independent message process is appended to the unperturbed tilted tree, so its increment is
> $\log T_0V_{\rm e}$.

### 기호

| 기호 | 의미 |
|---|---|
| $\bar f(x)=\sum_sf(s)q_x(s)$ | 메시지 $x$가 정한 한 스핀 분포 아래 $f$의 평균. VB에서는 $\bar f(x)=\tanh x$ |
| $D_{\rm real}=b\prod_{\ell=1}^pf_\ell(\sigma_{i_\ell})$ | 실제 clause |
| $D_{\rm cav}=b\,f_p(\sigma_i)\prod_{\ell<p}\bar f_\ell(x_\ell)$ | cavity 항: 다리 $p-1$개가 메시지 |
| $D_{\rm edge}=b\prod_{\ell=1}^p\bar f_\ell(x_\ell)$ | edge 항: 다리 $p$개 모두 메시지, 스핀 없음 |

### 해석과 검증

**(4.1)이 명제를 주는 이유.** (4.1)을 $[0,1]$에서 적분하면
$F_N-\varphi(0)=\int_0^1\varphi'\le-\alpha(p-1)\mathbb E\log T_0V_{\rm e}$, 즉
$F_N\le\log2+\mathbb E\log T_0V_{\rm s}-\alpha(p-1)\mathbb E\log T_0V_{\rm e}=\mathcal B_r$ (2.11). ✓
문단 5와 합치면 (4.1)은
$$\Delta_{\rm real}-p\,\Delta_{\rm cav}+(p-1)\,\Delta_{\rm edge}\le0,\qquad
\Delta_{\rm edge}:=\mathbb E\log T_0V_{\rm e}\tag{$*$}$$
과 같습니다. 이것이 증명할 대상입니다.

**세 삽입이 $a(1+D)$ 꼴인 이유.**
- 실제: (2.3) 그대로. ✓
- cavity: $e^{U_\theta(x;\varepsilon)}=\sum_{s'}a(1+b\prod_{\ell<p}f_\ell(s_\ell)f_p(\varepsilon))\prod_{\ell<p}q_{x_\ell}(s_\ell)
  =a(1+bf_p(\varepsilon)\prod_{\ell<p}\bar f_\ell(x_\ell))$ ($\sum_sq_x(s)=1$). ✓
  (논문 (2.6)은 새 스핀을 마지막 자리에 둡니다. $f_\ell$이 i.i.d.이므로 어느 자리든 법칙이 같습니다.)
- edge: $C_\theta=\sum_s a(1+b\prod f_\ell(s_\ell))\prod q_{x_\ell}(s_\ell)=a(1+b\prod_\ell\bar f_\ell(x_\ell))$. ✓

**edge 증분이 $\log T_0V_{\rm e}$인 이유.** edge 항은 스핀을 쓰지 않고 새 메시지 라벨만 씁니다.
3.1절 끝의 규칙대로 새 라벨을 각 깊이의 사전 커널과 함께 경로에 덧붙이면, 기존 기울기는 새 변수에
의존하지 않으므로 새 변수의 조건부 법칙은 사전 사슬 (2.7) 그대로입니다. $A$가 새 변수에만
의존하면 (3.3)의 재귀 $Y_{d-1}=(K_dY_d^{m_d})^{1/m_d}$에서 $K_d$의 새 변수 주변분포만 쓰이고,
$Y_{L-1}=K_LA=A$ ($m_L=1$, 스핀 무관)이므로 $Y_0$는 (2.10)의 $T_0V_{\rm e}$와 정확히 같습니다. ✓
따라서 이 항은 보간된 계와 무관한 **상수**이고, $(*)$의 셋째 항으로 들어갑니다.

### 물리적 의미

Bethe 장부(2.11)의 "$-\alpha(p-1)\times$edge"가 여기서 나옵니다. 실제 clause 하나를 cavity 항
$p$개로 바꾸면 clause의 기여를 $p$번 세게 되므로, 과다 계산한 $(p-1)$번을 edge 항으로 뺍니다.
$(*)$는 "실제 clause 하나 = cavity 다리 $p$개 − edge $(p-1)$개"라는 Bethe 근사가 **pressure를
과대평가하는 쪽으로만** 틀린다는 주장입니다.

---

## 문단 7. 증명 ⑤ 정규화와 $\lambda$-정칙화

> *Normalization.* We remove $a$ before taking expectations, so no integrability of $\log a$ is
> needed. Put $D_*=b\prod_\ell f_\ell(1)$ and $c=\theta(1,\ldots,1)$. Subtract $c$ from each
> insertion increment. These integrable subtractions cancel in the combination with coefficients
> $1,-p,p-1$. Keep the interpolated system fixed. For $0<\lambda<1$, replace each normalized
> increment by
> $$\log Y_0(1+\lambda D)-\log(1+\lambda D_*),\tag{4.2}$$
> where $Y_0$ is the insertion recursion of Lemma 3.2. For every spin input, the ratio
> $$\frac{1+\lambda D}{1+\lambda D_*}=(1-w)+w\frac{1+D}{1+D_*},\qquad
> w=\frac{\lambda(1+D_*)}{1+\lambda D_*}\in[0,1],$$
> lies between $e^{-2B(\theta)}$ and $e^{2B(\theta)}$. The same is true after averaging any subset
> of the spin inputs against the $q_x$'s. It follows that (4.2) is bounded in absolute value by
> $2B(\theta)$. For each fixed interaction, convergence as $\lambda\uparrow1$ is uniform in the spin
> inputs and messages and is preserved by the finite recursion. Dominated convergence therefore
> recovers the desired normalized increments.

### 기호

| 기호 | 의미 |
|---|---|
| $D_*=b\prod_\ell f_\ell(1)$ | 모든 스핀이 $+1$일 때의 $D$ (뿌리 가측, 스핀 무관) |
| $c=\theta(1,\dots,1)=\log a+\log(1+D_*)$ | 기준값 |
| $\lambda\in(0,1)$ | 정칙화 매개변수 |
| $w$ | 볼록 결합의 가중치 |

### 왜 정규화가 필요한가

증분 $\log Y_0(a(1+D))=\log a+\log Y_0(1+D)$ (Lemma 3.1의 동차성)입니다. $\log a$는 적분 가능하다는
보장이 없습니다 ($a$는 다른 변수에 마음대로 의존 가능). 그래서 $c$를 빼면
$$\log Y_0(a(1+D))-c=\log Y_0\Bigl(\frac{1+D}{1+D_*}\Bigr)$$
(동차성: $1+D_*$는 뿌리 가측 양수) 이 되어 $a$가 사라집니다. ✓
빼는 양 $c$는 $|c|\le B(\theta)$라 적분 가능하고, 세 삽입은 같은 법칙의 독립 $\theta$를 쓰므로
계수 합 $1-p+(p-1)=0$으로 $(*)$에서 정확히 상쇄됩니다. ✓

### 왜 $\lambda$가 필요한가

Lemma 3.2의 로그 전개는 $|t|\|D\|_\infty\le c<1$을 요구합니다. (2.3)은 $|D|<1$만 주고 1에서
떨어져 있다는 보장은 없습니다 (스핀 입력이 유한 개이므로 실현마다 $\max_s|D|<1$이지만, 실현에
대해 균등하지 않을 수 있음). $\lambda<1$을 곱하면 $\|\lambda D\|_\infty\le\lambda<1$로 균등해집니다.

### 검증

- 항등식: $(1-w)+w\frac{1+D}{1+D_*}=1+w\frac{D-D_*}{1+D_*}=1+\frac{\lambda(D-D_*)}{1+\lambda D_*}
  =\frac{1+\lambda D}{1+\lambda D_*}$. ✓
- $w\in[0,1]$: $1+D_*>0$, $1+\lambda D_*>0$이므로 $w\ge0$. $w\le1\iff\lambda+\lambda D_*\le1+\lambda D_*\iff\lambda\le1$. ✓
- $\frac{1+D}{1+D_*}=e^{\theta(s)-c}\in[e^{-2B},e^{2B}]$ ($|\theta(s)|,|c|\le B$). 1과 이 값의 볼록 결합도
  같은 구간에 있습니다 ($1\in[e^{-2B},e^{2B}]$). ✓
- "spin input 일부를 $q_x$로 평균": cavity/edge의 $D$는 $D_{\rm real}$의 일부 입력을 $q_{x}$로 평균한
  것이고, 비율의 분모 $1+\lambda D_*$는 평균과 무관하므로 비율도 같은 평균입니다. 구간 값의 확률
  평균은 구간 안에 있습니다. ✓
- Lemma 3.1의 단조성 ⇒ $|(4.2)|\le2B(\theta)$. ✓ $\lambda\uparrow1$에서 비율은 스핀·메시지에
  균등하게 수렴하고 ($w\to1$, 차이 $\le|1-w|\cdot e^{2B}$, $1-w=\frac{1-\lambda}{1+\lambda D_*}$ —
  고정된 상호작용에서 $1+\lambda D_*\ge\min(1,1+D_*)>0$이므로 균등), 유한 깊이 재귀가 균등 수렴을
  보존하므로, 지배 수렴 정리 (지배 함수 $2B(\theta)$, (2.1))로 정규화 증분이 회복됩니다. ✓

**검토 메모.** 정칙화된 baseline $-\log(1+\lambda D_*)$의 상쇄에도 적분 가능성이 필요합니다.
$|D_*|<1$이고 $\lambda<1$이므로 $|\log(1+\lambda D_*)|\le|\log(1-\lambda)|$로 유계입니다. ✓
논문은 이 점을 "The regularized baseline terms cancel"로만 적었지만 문제는 없습니다.

### 수치 확인 (a)

무작위 $D,D_*\in(-0.99,0.99)$, $\lambda\in(0,1)$ 2만 개에서 항등식 오차 최대 $1.4\times10^{-14}$,
$w\in[0,1]$과 "비율이 $1$과 $\frac{1+D}{1+D_*}$ 사이"를 모두 확인했습니다.

---

## 문단 8. 증명 ⑥ 볼록성과 계수 (4.3)

> *Convexity.* Apply Lemma 3.2 to the regularized increments. On a tree $\mathcal T$ with $n$
> replica leaves define
> $$P_{\mathcal T}=\frac1N\sum_{i=1}^N\mathbb E_f\prod_{a=1}^nf(\sigma_i^a),\qquad
> B_{\mathcal T}=\mathbb E_{f,x}\prod_{a=1}^n\bar f(x^a).$$
> Here $\mathbb E_f$ averages one fresh function $f$, shared by all $n$ replica factors in the
> product. The expectation $\mathbb E_{f,x}$ also averages an entire fresh message-label tree,
> including its root. This function and message tree are independent of one another and of the
> old tilted system. Thus $B_{\mathcal T}$ is deterministic for a fixed tree, while
> $P_{\mathcal T}$ still depends on the old spin replicas. At $r=0$, the message itself is a root
> variable shared by all replica leaves. Averaging the independent uniform indices and the
> independent copies of $f$ and of the new message label gives, respectively,
> $P_{\mathcal T}^p$, $P_{\mathcal T}B_{\mathcal T}^{p-1}$, and $B_{\mathcal T}^p$. The inserted
> $b$ is independent of these variables. Thus the order-$n$ coefficient of the combined
> regularized increment is
> $$-\frac{\lambda^n}{n}\mathbb E[(-b)^n]\,\mathbb E_{Q_n}\mathbb E\left[P_{\mathcal T}^p
> -pP_{\mathcal T}B_{\mathcal T}^{p-1}+(p-1)B_{\mathcal T}^p\right].\tag{4.3}$$
> The regularized baseline terms cancel. The tree law $Q_n$ is that of Lemma 3.2; it is common to
> the three insertions. The series is absolutely convergent for $\lambda<1$, with each insertion
> controlled by $\sum_{n\ge1}\lambda^n/n$. Since $p$ is even, convexity of $x\mapsto x^p$ makes the
> bracket nonnegative, and (2.4) makes (4.3) nonpositive. Taking $\lambda\uparrow1$ proves (4.1).
> Integration over $t\in[0,1]$ gives the proposition.

### 기호

| 기호 | 의미 |
|---|---|
| $\mathcal T$, $n$ | $Q_n$으로 뽑은 나무, 잎 = replica $n$개 |
| $\sigma^a$ | 잎 $a$의 스핀 배치 (기울인 커널로 뽑힘) |
| $P_{\mathcal T}$ | **일반화 multi-overlap**: $f$로 본 replica $n$개의 자리 평균 상관. VB($f(s)=s$)에서는 $R_{[n]}$ (3.1) |
| $x^a$ | 새 메시지 라벨 나무에서 잎 $a$가 보는 메시지 |
| $B_{\mathcal T}$ | cavity 쪽 대응물. VB에서는 $\mathbb E\prod_a\tanh x^a$ |
| $Q_n$ | (3.8)의 나무 법칙 ($m$에만 의존) |

### 해석: 계수 계산을 한 단계씩

Lemma 3.2: 뿌리(삽입된 $b,f,i$, 메시지 뿌리 측도까지 포함)에 조건부로
$$\log Y_0(1+\lambda D)=\sum_{n\ge1}\frac{(-1)^{n-1}\lambda^n}{n}\mathbb E_{Q_n}E_{\mathcal T}\prod_{a=1}^nD^a .$$
이제 삽입마다 $\prod_aD^a$를 계산합니다 ($b$는 모든 replica가 공유하는 뿌리 변수).

1. **실제**: $\prod_aD^a=b^n\prod_{\ell=1}^p\prod_af_\ell(\sigma^a_{i_\ell})$. 자리 $i_\ell$과 함수
   $f_\ell$은 $\ell$마다 독립이고 계·나무와도 독립이므로, Fubini로 $\ell$마다 평균하면
   $\mathbb E_{i,f}\prod_af(\sigma^a_i)=P_{\mathcal T}$, 따라서 $b^nE_{\mathcal T}P_{\mathcal T}^p$. ✓
2. **cavity**: $\prod_aD^a=b^n\prod_af_p(\sigma^a_i)\prod_{\ell<p}\prod_a\bar f_\ell(x^a_\ell)$.
   새 라벨은 사전 사슬로 경로에 붙어 있으므로 나무 모양이 주어지면 스핀과 독립인 나무 표본입니다.
   라벨 $\ell$마다 독립이고, 뿌리 $\eta_0^\ell\sim\zeta$까지 평균하면 각 인자가 $B_{\mathcal T}$.
   균등 자리 $i$와 $f_p$를 평균하면 $P_{\mathcal T}$. 합쳐서 $b^nE_{\mathcal T}[P_{\mathcal T}]B_{\mathcal T}^{p-1}$. ✓
3. **edge**: $b^nB_{\mathcal T}^p$. ✓

$(-1)^{n-1}\mathbb E[b^n]=-\mathbb E[(-b)^n]$이므로, 계수 $1,-p,p-1$로 묶으면 차수 $n$ 계수가
정확히 (4.3)입니다. ✓ 세 삽입 모두 **같은 보간된 계**에 넣으므로 $Q_n$과 기울인 커널이 공통입니다
(edge 삽입에서도 나무는 같은 $Q_n$; $A$가 스핀에 무관할 뿐).

**무조건 수렴.** 각 삽입의 $n$차 항은 $|\lambda D|^n/n\le\lambda^n/n$로 지배되고
$\sum\lambda^n/n=-\log(1-\lambda)<\infty$. 기대값과 합의 교환이 정당합니다. ✓

**부호.** $p$ 짝수이면 $g(x)=x^p$는 $\mathbb R$ 전체에서 볼록이므로 접선 부등식
$P^p\ge B^p+pB^{p-1}(P-B)$, 즉
$$P^p-pPB^{p-1}+(p-1)B^p\ge0\qquad(P,B\in\mathbb R).$$
나무를 고정하면 $B_{\mathcal T}$는 결정적이고 $P_{\mathcal T}$는 실수 확률변수이므로 기대값도 $\ge0$.
(2.4) $\mathbb E[(-b)^n]\ge0$와 앞의 $-\lambda^n/n$으로 (4.3) $\le0$. ✓
따라서 정칙화된 $(*)$의 좌변 $\le0$; 문단 7의 지배 수렴으로 $\lambda\uparrow1$에서 $(*)$, 곧 (4.1). ✓

$p=2$에서 괄호는 $(P_{\mathcal T}-B_{\mathcal T})^2$로, Guerra의 remainder
$\mathbb E\langle(R_{12}-q)^2\rangle$와 같은 꼴입니다. 다만 여기에는 **모든 차수 $n$의**
multi-overlap이 등장합니다. 희석 모형의 Gibbs 측도는 2-replica overlap만으로 결정되지 않고 모든
multi-overlap $R_{[n]}$이 필요하다는 사실 (Mézard–Parisi의 "함수형 order parameter")의 반영입니다.

**검토 메모 (홀수 $p$).** 홀수 $p$에서는 $x^p$가 음의 영역에서 오목이므로 괄호가 음수가 될 수 있습니다.
그래서 이 증명은 짝수 $p$에 한정됩니다. ($P_{\mathcal T},B_{\mathcal T}\ge0$을 따로 보장하는 모형,
예컨대 일부 $K$-SAT 류에서는 홀수 $p$도 되지만 이 논문 범위 밖입니다.)

### 수치 확인

**(b) 괄호의 최솟값.** $P,B\sim U(-1,1)$ 20만 쌍:

| $p$ | $\min[P^p-pPB^{p-1}+(p-1)B^p]$ |
|---|---|
| 2 | $0.0000$ |
| 3 | $-3.9981$ (음수 → 홀수 $p$ 불가) |
| 4 | $0.0000$ |
| 6 | $0.0000$ |

**(c) $r=1$ ($L=2$) 장난감 계에서 $(*)$와 급수 (4.3)를 정확 계산.**
설정: 스핀 $N=2$, 깊이-1 보조 상태 $z\in\{1,2,3\}$ (무작위 사전확률 $P_1$, 무작위 양의 가중치
$w(z,\sigma)$), $m_1=0.4$. 기울인 커널 $K_1(z)\propto P_1(z)Z(z)^{m}$, $K_2(\sigma\mid z)=w/Z(z)$.
$f\in\{f(s)=s,\ (f(-1),f(1))=(0.2,0.7)\}$ 각 확률 ½. 메시지 $x\in\{-1.2,0.3,1.5\}$,
$\zeta$ = 두 측도 $(0.6,0.3,0.1)$, $(0.1,0.2,0.7)$의 ½–½ 혼합.
좌변 $(*)$은 power mean 재귀로 직접, 우변은 $Q_n$ (깊이 2에서는 블록 크기 $s_j$로 들어갈 확률
$(s_j-m)/n$, 새 블록 $cm/n$인 CRP$(m,0)$)을 정확히 열거해 $n\le14$까지 합했습니다.
이 계는 보간된 계가 아닌 **임의의 기울인 나무**이지만, 증명은 기존 계의 구조를 쓰지 않으므로
$(*)$는 여기서도 성립해야 합니다.

| $p$ | $b$의 법칙 | $\lambda$ | $(*)$ 직접 계산 | 급수 (4.3), $n\le14$ |
|---|---|---|---|---|
| 2 | $\pm0.6$ 대칭 (VB형) | 0.5 | $-1.03366429\times10^{-2}$ | $-1.03366429\times10^{-2}$ |
| 2 | $\pm0.6$ 대칭 | 0.999 | $-4.660\times10^{-2}$ | — |
| 2 | $-0.8$ (0.6), $+0.5$ (0.4) | 0.5 | $-5.17229754\times10^{-2}$ | $-5.17229668\times10^{-2}$ |
| 2 | 같음 | 0.999 | $-1.650\times10^{-1}$ | — |
| 2 | $+0.8$ 고정 ((2.4) 위반) | 0.5 | $+8.685\times10^{-2}$ | $+8.685\times10^{-2}$ |
| 4 | $\pm0.6$ 대칭 | 0.5 | $-4.47232462\times10^{-3}$ | $-4.47232461\times10^{-3}$ |
| 4 | $-0.8$/$+0.5$ 혼합 | 0.5 | $-2.76714674\times10^{-2}$ | $-2.76714653\times10^{-2}$ |
| 4 | $+0.8$ 고정 ((2.4) 위반) | 0.999 | $+9.297\times10^{-2}$ | — |

- 급수와 직접 계산이 절단 오차 ($\le\sum_{n>14}0.4^n/n\approx7\times10^{-8}$) 안에서 일치합니다. ✓
- (2.4)를 만족하면 언제나 음수 ✓, $b=+0.8$ (강자성형, $\mathbb E(-b)^n$의 부호가 번갈아 바뀜)이면
  **양수**가 되어 한 단계 부등식이 깨집니다. (2.4)가 실제로 필요한 가정임을 보여 줍니다.
  (물리적으로: 강자성 상호작용 $J>0$, $f(s)=s$에서는 홀수 차 항 $\mathbb E[b^n]>0$이 반대 부호를
  주어, 이 보간으로는 위쪽 한계를 얻을 수 없습니다. VB처럼 $J$가 대칭이면 홀수 모멘트가 0이라
  문제가 없습니다.)

---

## 요약

- 명제 4.1: 모든 $N$과 모든 유한 단계 시험 법칙에서 $F_N\le\mathcal B_r(\zeta,\mathbf m)$.
- 퇴화 분해를 먼저 처리하고, 비퇴화 경우 $b$와 $f$가 자동으로 유계임을 보입니다.
- Franz–Leone 보간: 실제 clause를 cavity 항 $p$개로 바꾸고, Poisson 미분으로
  $\varphi'/\alpha=\Delta_{\rm real}-p\Delta_{\rm cav}$, edge 항은 상수 $\log T_0V_{\rm e}$.
- $c=\theta(1,\dots,1)$을 빼서 무거운 꼬리의 $a$를 없애고, $\lambda<1$로 정칙화해 Lemma 3.2를 적용.
- 차수 $n$ 계수 (4.3)은 $-\frac{\lambda^n}{n}\mathbb E(-b)^n\,\mathbb E[P^p-pPB^{p-1}+(p-1)B^p]$;
  짝수 $p$의 볼록성과 (2.4)로 $\le0$. 수치로 급수와 부호, 그리고 (2.4)의 필요성까지 확인했습니다.

**다음 절 예고**: 5장에서는 아래쪽 한계를 위해, Aizenman–Sims–Starr 식 cavity 비교에 쓸
"섭동을 넣은 cavity 저장소"(perturbed cavity reservoir)를 만듭니다.
