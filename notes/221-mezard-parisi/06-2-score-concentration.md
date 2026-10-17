# 6.2 Concentration of each perturbation score — 문단별 해설

원문: `build/sections/perturbations.tex` 6.2절, PDF 16–17쪽. 번호는 PDF 기준
(식 (6.3)–(6.12), Lemma 6.1). 앞 절 참조: (6.1), (6.2), (5.3), Lemma 3.1, (3.2).

이 절은 Ghirlanda–Guerra 논증의 **유한 깊이 power-mean 버전**입니다. 점수 $D_\nu$가 (i) 한 기울인
경로 위의 열적 요동과 (ii) 뿌리(무질서)의 요동 모두에서 집중함을 보입니다.

---

## 문단 1. 점수와 오차의 정의

> For one type $\nu$, define on a tilted path, including its terminal Gibbs configuration,
> $$D_\nu=\sum_{q=1}^{n_\nu}\frac{g_{0,q}S_{0,q}}{1+t_\nu g_q\sigma_{i_q}+u_\nu g_{0,q}S_{0,q}}.\tag{6.3}$$
> Let $\langle\cdot\rangle$ denote expectation along one tilted path conditional on the root, and
> let $\mathbb E_{\mathbf u}$ average the root at fixed $\mathbf u$. Define
> $$e_{\nu,N}(\mathbf u)=\frac{1}{c_\nu s_N}\mathbb E_{\mathbf u}\Big\langle\big|D_\nu-\mathbb E_{\mathbf u}\langle D_\nu\rangle\big|\Big\rangle.\tag{6.4}$$

### 기호

| 기호 | 의미 |
|---|---|
| $q=1..n_\nu$ | 종류 $\nu$의 섭동 항 번호 |
| $D_\nu=\partial_{u_\nu}\log(\text{spin weight})$ | 점수: 로그 가중치의 $u_\nu$-도함수 |
| $\langle\cdot\rangle$ | 뿌리에 조건부로, 기울인 커널 $K_1,\dots,K_L$을 따라 경로 하나를 뽑는 기대값 |
| $e_{\nu,N}$ | 정규화한 평균 절대 편차 (열적 + 무질서) |

### 해석

$\log\psi_{\nu,q}$를 $u_\nu$로 미분하면 $g_{0,q}S_{0,q}/\psi_{\nu,q}$이므로, $D_\nu$는 **종류 $\nu$ 섭동
전체의 응답**입니다. 개수가 $\approx c_\nu s_N$이라 $D_\nu$의 크기도 그 정도이고, $e_{\nu,N}\to0$은
"점수가 상대 오차 $o(1)$로 결정적 상수 $\mathbb E_{\mathbf u}\langle D_\nu\rangle$에 집중"을 뜻합니다.
절댓값 안에서 빼는 것이 **전체 평균** $\mathbb E\langle D\rangle$이므로 열적 요동과 무질서 요동이 한꺼번에
들어 있습니다.

### 물리적 의미

SK에서 GG 항등식의 출발점은 $\mathbb E\langle|H_p-\mathbb E\langle H_p\rangle|\rangle=o(N)$ 입니다 ($H_p$는
$p$-spin 섭동 해밀토니안). 여기서 $D_\nu$가 그 $H_p/\text{(세기)}$ 역할을 합니다. "기울인 경로"는
보조 변수까지 포함하므로, $\langle\cdot\rangle$은 단순한 Gibbs 평균이 아니라 **Parisi 위계를 따라 상태를
고르고 그 안에서 배치를 고르는** 평균입니다.

---

## 문단 2. Lemma 6.1

> **Lemma 6.1 (Averaged score concentration).** For each fixed $L$ and each fixed type $\nu$,
> $$\int e_{\nu,N}(\mathbf u)\,\pi(d\mathbf u)\longrightarrow0.\tag{6.5}$$
> The assertion holds for the reservoir as well as for the original system. Constants need not be
> uniform in $L$ or $\nu$.

### 해석

"거의 모든 $\mathbf u$에서"의 정량적 형태입니다. 점별 $e_{\nu,N}(\mathbf u)\to0$은 주장하지 않고
$\pi$-평균만 주장합니다 — 볼록 함수의 도함수는 꺾이는 점에서 요동할 수 있기 때문입니다 (1차 상전이에서
자화가 불연속인 것과 같은 현상).

---

## 문단 3. 증명 시작: 점수의 한계 (6.6)

> Hold the other parameters fixed, write $u=u_\nu$, $n=n_\nu$, and put $\lambda_\nu=c_\nu s_N$.
> Choose an open interval $J_\nu$ containing $I_\nu$ such that $|t_\nu|+|u|<1/2$ throughout its
> closure. On this interval, pathwise,
> $$|D_\nu|\leq2n,\qquad -4n\leq\partial_uD_\nu=-\sum_{q=1}^{n}\frac{(g_{0,q}S_{0,q})^2}{\psi_{\nu,q}^{2}}\leq0.\tag{6.6}$$

### 검증

- $J_\nu$ 존재: $t_\nu\le1/4$, $\sup I_\nu=2j^{-j}\le2/256$이므로 $|t|+|u|<1/2$인 열린 구간이
  $I_\nu$를 포함합니다. ✓
- $|t g\sigma|+|ug_0S_0|\le|t|+|u|<1/2$ ⇒ $\psi>1/2$ ⇒ 각 항 $|g_0S_0/\psi|<2$ ⇒ $|D|\le2n$. ✓
- $\partial_u(a/(1+\dots+ua))=-a^2/\psi^2$, $a^2\le1$, $\psi^{-2}<4$ ⇒ $-4n\le\partial_uD\le0$. ✓

---

## 문단 4. 한 기울인 경로 위의 요동: (6.7), (6.8)

> *Fluctuations along a tilted path.* Let $X_0(u)$ be the random root log partition function before
> taking the root expectation. To include the last step in the differentiation, regard the
> logarithm of the spin weight as $X_L$ and the spin partition function as the step with exponent
> $m_L=1$. Differentiation of one backward step gives
> $$\partial_uX_{d-1}=K_d(\partial_uX_d),\qquad \partial_u^2X_{d-1}=K_d(\partial_u^2X_d)+m_d\mathrm{Var}_{K_d}(\partial_uX_d).$$
> Thus, for $M_d=\langle D_\nu\mid\mathscr F_d\rangle$,
> $$X_0'(u)=\langle D_\nu\rangle,\tag{6.7}$$
> $$X_0''(u)=\langle\partial_uD_\nu\rangle+\sum_{d=1}^{L}m_d\langle(M_d-M_{d-1})^2\rangle\ \geq\ m_1\mathrm{Var}(D_\nu\mid\mathscr F_0)-4n.\tag{6.8}$$

### 기호

| 기호 | 의미 |
|---|---|
| $X_L=\log(\text{spin weight})$ | 잎에서의 로그 가중치 (스핀 배치 함수) |
| $X_{d-1}=m_d^{-1}\log P_de^{m_dX_d}$ | (3.2) 위의 Monasson 퍼텐셜, $X_{L-1}=\log Z$ |
| $M_d$ | 점수의 깊이-$d$ 조건부 기대값 (기울인 법칙 아래 마팅게일) |

### 검증

한 단계: $X_{d-1}=\frac1{m}\log\int e^{mX_d}dP$ ($m=m_d$). 미분하면
$$\partial X_{d-1}=\frac{\int e^{mX_d}\partial X_d\,dP}{\int e^{mX_d}dP}=K_d(\partial X_d),$$
$K_d=e^{m(X_d-X_{d-1})}P_d$ (3.2)이므로. ✓ 한 번 더:
$$\partial^2X_{d-1}=K_d(\partial^2X_d)+m\bigl[K_d((\partial X_d)^2)-(K_d\partial X_d)^2\bigr].$$ ✓
(로그 적률생성함수의 2차 도함수 = 분산.) 마지막 단계 $m_L=1$: $X_{L-1}=\log\sum_\sigma e^{X_L}$이고
$K_L$이 Gibbs 측도.

귀납: $\partial X_L=D_\nu$이므로 $\partial X_d=M_d$. 따라서 $X_0'=M_0=\langle D_\nu\rangle$ (6.7) ✓, 그리고
$$X_0''=\langle\partial_uD\rangle+\sum_{d=1}^Lm_d\langle\mathrm{Var}_{K_d}(M_d)\rangle,\qquad
\mathrm{Var}_{K_d}(M_d)=\langle(M_d-M_{d-1})^2\mid\mathscr F_{d-1}\rangle.$$ ✓
$m_d\ge m_1$이고 마팅게일 차분의 직교성으로 $\sum_d\langle(M_d-M_{d-1})^2\rangle=\langle(M_L-M_0)^2\rangle
=\mathrm{Var}(D\mid\mathscr F_0)$. 여기에 (6.6)의 $\langle\partial_uD\rangle\ge-4n$을 합치면 (6.8). ✓

### 물리적 의미

$X_0''$의 분산 항이 **깊이별로 $m_d$ 가중**된다는 점이 핵심입니다. 깊이 $d$에서의 요동, 즉 "점수가
어느 깊이-$d$ 상태에 있느냐에 따라 달라지는 정도"는 $m_d$만큼만 자유에너지의 곡률에 기여합니다.
RSB에서 $m$이 "상태 사이 요동의 무게"라는 물리적 해석 (Parisi 매개변수 = 상태 무게 분포의 지수)이
그대로 나타납니다. 가장 얕은 깊이의 가중치 $m_1=1/L$이 가장 작으므로 상수가 $L$에 의존합니다.

### 수치 확인

$L=3$, $m=(1/3,2/3,1)$, 스핀 $N=2$, 깊이 1·2에 Rademacher 부호 하나씩, 섭동 항 4개 (무작위 $g,g_0$,
깊이, 자리, $S_0$), $t=0.2$. $X_0(u)$를 power mean으로 직접 계산해 유한 차분 ($h=10^{-4}$)과 비교:

| $u$ | $X_0'$ 유한차분 | $\langle D\rangle$ (6.7) | $X_0''$ 유한차분 | (6.8) 등식 우변 | $m_1\mathrm{Var}+\langle\partial_uD\rangle$ | $m_1\mathrm{Var}-4n$ |
|---|---|---|---|---|---|---|
| 0 | 0.38022862 | 0.38022862 | −0.393064 | −0.393064 | −0.6982 | −15.72 |
| 0.05 | 0.36049007 | 0.36049007 | −0.396741 | −0.396741 | −0.6934 | −15.72 |
| 0.1 | 0.34052713 | 0.34052713 | −0.402063 | −0.402063 | −0.6913 | −15.72 |

(6.7)과 (6.8)의 등식이 일치하고, 부등식의 두 하한도 성립합니다. ✓

---

## 문단 5. 미분의 정당화

> Here the conditional expectations and variances use the tilted path law at the current $u$. At
> fixed root all derivatives are justified by the bounded score and its derivatives; the finite
> recursion then justifies the displayed differentiation formulas. Their root expectations are
> justified by the finite moments of the Poisson counts.

### 해석

뿌리를 고정하면 섭동 항은 유한 개이고 각 $\psi$는 $u$의 매끄러운 양함수이므로 유한 재귀의 미분은
문제없습니다. 뿌리 기대값과의 교환은 $|X_0'|\le2n$, $|X_0''|\lesssim n+n^2$ 같은 한계와
$\mathbb E n^2<\infty$ (Poisson)로 지배 수렴. ✓ ($X_0''$의 분산 항은 $\le m_d(2n)^2$.)

---

## 문단 6. 열적 분산의 적분: (6.9), (6.10)

> Integrating (6.8) over $I_\nu=[a,b]$ and using $|X_0'|\leq2n$ yields
> $$\int_a^b\mathbb E_{\mathbf u}\mathrm{Var}(D_\nu\mid\mathscr F_0)\,du\leq\frac{4\lambda_\nu(1+b-a)}{m_1}.\tag{6.9}$$
> Consequently the interval-averaged thermal mean absolute deviation, divided by $\lambda_\nu$, is
> at most
> $$\left(\frac{4(1+|I_\nu|)}{m_1|I_\nu|\lambda_\nu}\right)^{1/2}.\tag{6.10}$$

### 검증

(6.8)을 정리하면 $m_1\mathrm{Var}\le X_0''+4n$. $[a,b]$에서 적분:
$m_1\int\mathrm{Var}\le X_0'(b)-X_0'(a)+4n(b-a)\le4n+4n(b-a)$. 기대값 $\mathbb En=\lambda_\nu$:
(6.9). ✓ 다음으로 Cauchy–Schwarz와 Jensen을 쓰면
$$\frac1{|I|}\int_I\mathbb E\langle|D-\langle D\rangle|\rangle du\le\frac1{|I|}\int_I\sqrt{\mathbb E\mathrm{Var}}\,du
\le\Bigl(\frac1{|I|}\int_I\mathbb E\mathrm{Var}\Bigr)^{1/2}\le\Bigl(\frac{4\lambda(1+|I|)}{m_1|I|}\Bigr)^{1/2},$$
이것을 $\lambda$로 나누면 (6.10). ✓ $\lambda_\nu=c_\nu N^{3/4}\to\infty$이므로 $\to0$ (속도 $N^{-3/8}$).

**판단 메모.** 상수가 $1/|I_\nu|=j^j$와 $1/m_1=L$에 의존하므로 $\nu$와 $L$에 대해 균등하지 않습니다.
Lemma 6.1이 명시한 대로이며, 이후 극한은 항상 "$L$, $\nu$ 고정 후 $N\to\infty$" 순서입니다.

> (작업 중 — 다음 문단부터 이어짐)
