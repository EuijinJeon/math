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

---

## 문단 7. 뿌리 평균의 요동: 볼록 함수 $G$와 (6.11)

> *Fluctuations of the root mean.* It remains to concentrate $X_0'$ over the root. By (6.8), the
> random function $G(u)=X_0(u)+2nu^2$ is convex on $J_\nu$. Uniformly for $u\in J_\nu$ and all the
> other parameters,
> $$\mathrm{Var}(G(u))\leq C_\nu N,\qquad|\mathbb E_{\mathbf u}G'(u)|\leq C_\nu\lambda_\nu.\tag{6.11}$$
> To prove the first estimate, condition on the physical and total perturbation counts.
> Conditional on the latter count, its types and sites are independent labels; changing a label
> replaces a single bounded factor. Apply the Efron–Stein variance inequality [EfronStein]
> $\mathrm{Var}Z\le\frac12\sum_j\mathbb E(Z-Z^{(j)})^2$, where $Z^{(j)}$ is obtained by independently
> resampling the $j$th input. For completeness, with independent inputs $X_1,\ldots,X_k$, let $E_j$
> integrate only $X_j$ and let $\mathscr G_j=\sigma(X_1,\ldots,X_j)$. The Doob differences are
> $D_j=\mathbb E[Z-E_jZ\mid\mathscr G_j]$. Orthogonality and Jensen give
> $$\mathrm{Var}Z=\sum_j\mathbb ED_j^2\le\sum_j\mathbb E(Z-E_jZ)^2=\frac12\sum_j\mathbb E(Z-Z^{(j)})^2.$$
> This independent-input decomposition requires neither identical laws nor a symmetric statistic;
> see Efron–Stein [Section 2]. Resampling one interaction, field, or perturbation term changes $X_0$
> by a bounded amount: this is immediate for the spin weights and is preserved by each power mean.
> When a term is removed, its unused independent mark variables can be integrated out, so the same
> assertion holds for addition or deletion of a term. Conditional variances are therefore bounded by
> a constant times the number of root variables. Conditional means are Lipschitz functions of the
> counts, with bounded Lipschitz constants. If $Q,Q'$ are independent copies of a Poisson variable
> and $b$ is $C$-Lipschitz, then
> $$\mathrm{Var}(b(Q))=\tfrac12\mathbb E(b(Q)-b(Q'))^2\leq C^2\mathrm{Var}(Q).$$
> Applying this to the independent counts completes the $O(N)$ estimate. The correction $2nu^2$
> obeys the same estimates. The derivative bound in (6.11) follows directly from (6.6).

### 해석과 검증

**볼록성.** $G''=X_0''+4n\ge m_1\mathrm{Var}\ge0$ ((6.8)). ✓ 무작위 함수 $G$가 매 실현에서 볼록이므로
"볼록 함수의 값이 집중하면 도함수도 (거의 모든 점에서) 집중"이라는 GG의 고전 논법을 쓸 수 있습니다.

**Efron–Stein 증명 확인.**
- $D_j=\mathbb E[Z\mid\mathscr G_j]-\mathbb E[Z\mid\mathscr G_{j-1}]$ (Doob 마팅게일 차분). 입력이 독립이므로
  $\mathbb E[E_jZ\mid\mathscr G_j]=\mathbb E[Z\mid\mathscr G_{j-1}]$이고, 따라서 $D_j=\mathbb E[Z-E_jZ\mid\mathscr G_j]$. ✓
- $\mathrm{Var}Z=\sum_j\mathbb ED_j^2$ (직교성) ✓, 조건부 Jensen $D_j^2\le\mathbb E[(Z-E_jZ)^2\mid\mathscr G_j]$ ✓.
- $\mathbb E(Z-E_jZ)^2=\mathbb E\,\mathrm{Var}_j(Z)=\frac12\mathbb E(Z-Z^{(j)})^2$ (같은 조건부 법칙의 두 독립 표본). ✓

**입력 하나를 바꾸면 유계 변화.** clause 하나: $\le2B$; 장 하나: $\le2H$; 섭동 항 하나: $\le2\log2$
(Lemma 3.1의 단조성으로 power mean을 지나도 보존). $2nu^2$ 항은 $n$을 1 바꾸면 $2u^2\le1/2$만큼. ✓

**전체 분산.** $\mathrm{Var}G=\mathbb E\mathrm{Var}(G\mid\text{counts})+\mathrm{Var}\,\mathbb E(G\mid\text{counts})$.
- 첫 항 $\le C\,\mathbb E[M+N+n_{\rm tot}]=O(N)$ (clause 수 $M$의 평균 $O(N)$, 장 $N$개, 섭동 $s_N$개). ✓
- 둘째 항: 조건부 평균은 각 개수에 대해 Lipschitz (하나 더하면 유계 변화). Poisson 개수들이 독립이므로
  Efron–Stein을 개수에 다시 적용하고, 각 개수에는 Lipschitz 보조정리
  $\mathrm{Var}b(Q)=\frac12\mathbb E(b(Q)-b(Q'))^2\le\frac{C^2}2\mathbb E(Q-Q')^2=C^2\mathrm{Var}Q$ ✓를 씁니다.
  $\mathrm{Var}M=O(N)$, $\mathrm{Var}n_{\rm tot}=s_N$. 합 $O(N)$. ✓

**도함수 한계.** $G'=X_0'+4nu$, $|X_0'|\le2n$, $|4nu|\le2n$ ⇒ $|\mathbb EG'|\le4\lambda_\nu$. ✓

**검토 메모.** 섭동 "label"(종류·자리)은 총 개수에 조건부로 i.i.d.이고, 각 종류별 개수가
$\mathrm{Pois}(c_\nu s_N)$로 독립인 것과 같은 법칙입니다 (Poisson 분할의 역). 논문이 "condition on the total
perturbation count"라고 쓴 것은 이 동치를 쓴 것입니다. ✓

### 물리적 의미

$\mathrm{Var}(\log Z)=O(N)$은 자유에너지의 **self-averaging**입니다 (상대 요동 $N^{-1/2}$). 희석 모형에서는
Gaussian 집중 대신 "clause 하나 = 유계 영향"이라는 국소성만으로 충분합니다.

---

## 문단 8. 볼록 함수에서 도함수로: (6.12)와 결론

> *Passing from a convex function to its derivative.* Put $\bar G=\mathbb E_{\mathbf u}G$ and
> $Z=G-\bar G$. If $u\pm\rho$ lie in $J_\nu$, forward and backward difference quotients imply
> $$|G'(u)-\bar G'(u)|\leq\frac{|Z(u-\rho)|+2|Z(u)|+|Z(u+\rho)|}{\rho}+\bar G'(u+\rho)-\bar G'(u-\rho).$$
> The monotonicity of $\bar G'$ gives
> $$\int_a^b[\bar G'(u+\rho)-\bar G'(u-\rho)]\,du\leq2\rho[\bar G'(b+\rho)-\bar G'(a-\rho)].$$
> Together with (6.11), this proves
> $$\frac1{|I_\nu|}\int_{I_\nu}\mathbb E_{\mathbf u}|G'(u)-\mathbb E_{\mathbf u}G'(u)|\,du\leq C_\nu\left(\frac{\sqrt N}{\rho}+\frac{\rho\lambda_\nu}{|I_\nu|}\right).\tag{6.12}$$
> For all sufficiently large $N$, take $\rho=N^{-1/8}$, which lies within the fixed neighborhood
> margin. After division by $\lambda_\nu=c_\nu N^{3/4}$, both terms tend to zero. Removing the
> correction to $G'$ costs at most $C_\nu\mathbb E|n-\lambda_\nu|/\lambda_\nu\leq C_\nu\lambda_\nu^{-1/2}$.
> Thus the root contribution to (6.4) tends to zero. Combining it with (6.10) proves the result
> after integration over $u_\nu$. All estimates are uniform in the other parameters, so their
> integration against the remaining product measure proves (6.5).

### 검증

**차분 몫 부등식.** $G$, $\bar G$ 모두 볼록 ($\bar G$는 볼록 함수의 평균). 볼록성:
$\frac{G(u)-G(u-\rho)}\rho\le G'(u)\le\frac{G(u+\rho)-G(u)}\rho$, $\bar G$도 같음.
- 위쪽: $G'(u)-\bar G'(u)\le\frac{Z(u+\rho)-Z(u)}\rho+\Bigl[\frac{\bar G(u+\rho)-\bar G(u)}\rho-\bar G'(u)\Bigr]
  \le\frac{|Z(u+\rho)|+|Z(u)|}\rho+\bar G'(u+\rho)-\bar G'(u)$.
- 아래쪽: $\bar G'(u)-G'(u)\le\frac{|Z(u)|+|Z(u-\rho)|}\rho+\bar G'(u)-\bar G'(u-\rho)$.
- 두 경우 모두 논문 우변 이하. ✓

**적분.** $\int_a^b\bar G'(u+\rho)du-\int_a^b\bar G'(u-\rho)du=\int_{b-\rho}^{b+\rho}\bar G'-\int_{a-\rho}^{a+\rho}\bar G'
\le2\rho\bar G'(b+\rho)-2\rho\bar G'(a-\rho)$ ($\bar G'$ 단조 증가). ✓

**(6.12).** $\mathbb E|Z(u)|\le\sqrt{\mathrm{Var}G}\le\sqrt{C_\nu N}$ ⇒ 첫 항 $\le4\sqrt{C_\nu N}/\rho$.
둘째 항 $\le2\rho\cdot2C_\nu\lambda_\nu/|I_\nu|$ ((6.11)의 도함수 한계). ✓

**$\rho=N^{-1/8}$.** $\lambda_\nu$로 나누면 $\frac{\sqrt N}{\rho\lambda_\nu}\propto N^{1/2+1/8-3/4}=N^{-1/8}\to0$,
$\frac\rho{|I_\nu|}=j^jN^{-1/8}\to0$. ✓ 큰 $N$에서 $I_\nu\pm\rho\subset J_\nu$. ✓

**보정 제거.** $G'-\mathbb EG'=(X_0'-\mathbb EX_0')+4u(n-\lambda_\nu)$, $\mathbb E|n-\lambda|\le\sqrt\lambda$ ⇒
비용 $\le2\lambda^{-1/2}$ (나눈 뒤). ✓

**합치기.** $\mathbb E\langle|D-\mathbb E\langle D\rangle|\rangle\le\mathbb E\langle|D-\langle D\rangle|\rangle+\mathbb E|\langle D\rangle-\mathbb E\langle D\rangle|$,
첫 항은 (6.10), 둘째 항은 $X_0'=\langle D\rangle$ (6.7)이므로 위 결과. $u_\nu$에 대해 구간 평균,
나머지 좌표는 균등 한계이므로 $\pi$로 적분. ✓

**지수 정리.** $s_N=N^{\gamma}$로 일반화하면 첫 항 $N^{1/2}/(\rho N^\gamma)$, 둘째 항 $\rho$이므로 최적
$\rho=N^{(1/2-\gamma)/2}$, 오차 $N^{(1/2-\gamma)/2}$. 따라서 **$\gamma>1/2$가 필요**합니다. 5장 문단 7에서
남겨 둔 질문의 답: $s_N=N^{3/4}$는 $1/2<\gamma<1$ 조건을 만족합니다.

### 수치 확인

무작위 볼록 함수 $G,\bar G$ (서로 다른 $\log\cosh$ 혼합 + 2차항) 2000쌍, 무작위 $u$, $\rho\in(0.01,0.3)$에서
차분 몫 부등식의 (좌변 − 우변) 최댓값 $=-0.82<0$. ✓

### 물리적 의미

GG 논법의 핵심 문장 "자유에너지가 self-averaging하고 볼록하면 내부 에너지도 거의 모든 온도에서
self-averaging"을 정확히 재현했습니다. 열적 부분 (6.10)은 **비열의 유한성**과 같은 논리 (곡률 적분 =
도함수의 유계 변화)이고, 무질서 부분 (6.12)는 볼록 함수의 도함수가 평균 주위의 작은 요동으로만
움직인다는 사실입니다. 결과적으로 $\langle|D_\nu-\mathbb E\langle D_\nu\rangle|\rangle=o(s_N)$: 섭동 점수는
replica에 무관한 상수입니다. 다음 절들은 이 집중을 "anchor replica의 점수는 다른 replica들과
상관이 없다"는 형태로 바꿉니다.

---

## 요약

- 점수 $D_\nu=\partial_u\log(\text{weight})$의 정규화 평균 절대 편차 $e_{\nu,N}$을 정의 (6.4).
- 열적 부분: $X_0''=\langle\partial D\rangle+\sum_dm_d\langle(M_d-M_{d-1})^2\rangle\ge m_1\mathrm{Var}-4n$ (6.8),
  적분하면 $O(\lambda^{-1/2})$ (6.10). 깊이별 분산이 $m_d$로 가중되는 것을 수치로 확인.
- 무질서 부분: $G=X_0+2nu^2$의 볼록성 + Efron–Stein $\mathrm{Var}G=O(N)$ + 차분 몫 (6.12), $\rho=N^{-1/8}$.
- 결과 Lemma 6.1: $\int e_{\nu,N}\,d\pi\to0$. 상수는 $L$, $\nu$에 의존. $s_N=N^\gamma$에서 $\gamma>1/2$가 필요.

**다음 절 예고**: 6.3절에서 낮은 cavity 증분과 모든 점수 집중, 모든 나무 모멘트의 수렴을 동시에
만족하는 하나의 수열 $(N_j,\mathbf u_j)$를 고릅니다 (Lemma 6.2).
