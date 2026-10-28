# 6.2 Concentration of each perturbation score — 문단별 해설

원문: `build/sections/perturbations.tex` 6.2절, PDF 16–17쪽. 번호는 PDF 기준
(식 (6.3)–(6.12), Lemma 6.1). 앞 절 참조: (6.1), (6.2), (5.3), Lemma 3.1, (3.2).

> **이 판의 읽는 법.** 원문 인용 바로 아래에 **문장별 풀이**를 두었습니다. 원문 문장(또는 한 덩어리)을 다시
> 짧게 인용하고, 그 문장이 무슨 뜻인지, 그리고 원문이 생략한 중간 식을 바로 이어서 적었습니다. 검증(✓)과
> 수치 확인은 그 뒤에 따로 둡니다.

---

## 0. 이 절의 큰 그림 (원문에는 없는 안내)

목표는 섭동 점수 $D_\nu$가 상수 $\mathbb E_{\mathbf u}\langle D_\nu\rangle$ 근처에 몰려 있다는 것입니다. 점수와 그 상수의
차이는 두 조각으로 나뉩니다.
$$D_\nu-\mathbb E\langle D_\nu\rangle=\underbrace{\bigl(D_\nu-\langle D_\nu\rangle\bigr)}_{\text{① 열적 요동: 뿌리를 고정하고 경로만 바꿀 때}}+\underbrace{\bigl(\langle D_\nu\rangle-\mathbb E\langle D_\nu\rangle\bigr)}_{\text{② 무질서 요동: 뿌리를 바꿀 때}}.$$

| 조각 | 무엇이 흔들리나 | 쓰는 도구 | 문단 |
|---|---|---|---|
| ① | 같은 무질서에서 상태·배치를 다시 뽑을 때 | 자유에너지의 2차 도함수 = 분산 | 4–6 |
| ② | 무질서 자체를 다시 뽑을 때 | 볼록 함수 + 값의 집중 ⇒ 도함수의 집중 | 7–8 |

두 조각 모두 같은 함수 $X_0(u)$ (섭동된 계의 뿌리 로그 분배함수)를 통해 다룹니다. $X_0'(u)=\langle D_\nu\rangle$이기 때문입니다 ((6.7)).

---

## 문단 1. 점수와 오차의 정의

> For one type $\nu$, define on a tilted path, including its terminal Gibbs configuration,
> $$D_\nu=\sum_{q=1}^{n_\nu}\frac{g_{0,q}S_{0,q}}{1+t_\nu g_q\sigma_{i_q}+u_\nu g_{0,q}S_{0,q}}.\tag{6.3}$$
> Let $\langle\cdot\rangle$ denote expectation along one tilted path conditional on the root, and
> let $\mathbb E_{\mathbf u}$ average the root at fixed $\mathbf u$. Define
> $$e_{\nu,N}(\mathbf u)=\frac{1}{c_\nu s_N}\mathbb E_{\mathbf u}\Big\langle\big|D_\nu-\mathbb E_{\mathbf u}\langle D_\nu\rangle\big|\Big\rangle.\tag{6.4}$$

### 문장별 풀이

1. **"For one type $\nu$, define … $D_\nu=\sum_q\dots$"**
   종류 $\nu$의 섭동 항은 $n_\nu\sim\mathrm{Pois}(c_\nu s_N)$개이고, $q$번째 항은 스핀 가중치에
   $\psi_{\nu,q}=1+t_\nu g_q\sigma_{i_q}+u_\nu g_{0,q}S_{0,q}$를 곱합니다 ((6.2)). 그러므로 로그 가중치에는
   $\sum_q\log\psi_{\nu,q}$가 더해지고, 이것을 $u_\nu$로 미분하면
   $$\frac{\partial}{\partial u_\nu}\sum_q\log\psi_{\nu,q}=\sum_q\frac{g_{0,q}S_{0,q}}{\psi_{\nu,q}}=D_\nu .$$
   즉 **$D_\nu$는 "로그 가중치의 $u_\nu$-도함수"**입니다. 원문에는 이 말이 없지만, 문단 4에서 정확히 이 사실을 씁니다.
2. **"on a tilted path, including its terminal Gibbs configuration"**
   $D_\nu$가 무엇에 의존하는지 말해 줍니다.
   - 뿌리 변수: 개수 $n_\nu$, 자리 $i_q$ (그리고 나머지 무질서)
   - 보조 변수: $g_q$, $g_{0,q}$는 깊이 $1..L-1$에 놓인 Rademacher 표시의 함수
   - 마지막 스핀 배치: $\sigma_{i_q}$, 그리고 $S_0=\sigma_i$이면 $S_{0,q}$

   따라서 $D_\nu$는 "기울인 경로 하나" (보조 변수들 + 마지막 스핀 배치)의 함수입니다.
3. **"Let $\langle\cdot\rangle$ denote expectation along one tilted path conditional on the root"**
   뿌리를 고정하고, 기울인 커널 $K_1,\dots,K_{L-1}$로 보조 변수를 깊이마다 뽑고, $K_L$ (Gibbs)로 스핀을 뽑는 평균입니다.
   $L=1$ (보조 변수 없음)이면 그냥 Gibbs 평균입니다.
4. **"let $\mathbb E_{\mathbf u}$ average the root at fixed $\mathbf u$"**
   무질서(뿌리)에 대한 평균입니다. $\mathbf u$는 고정된 매개변수이므로 평균하지 않습니다.
5. **"$e_{\nu,N}(\mathbf u)=\frac{1}{c_\nu s_N}\mathbb E\langle|D_\nu-\mathbb E\langle D_\nu\rangle|\rangle$"**
   - 분모 $c_\nu s_N=\mathbb En_\nu=:\lambda_\nu$: $D_\nu$는 항 $\approx\lambda_\nu$개의 합이라 크기가 $\lambda_\nu$ 정도이므로 그것으로 나눈 **상대 오차**입니다.
   - 절댓값 안에서 빼는 것은 $\langle D\rangle$가 아니라 **전체 평균** $\mathbb E\langle D\rangle$입니다. 그래서 위 0절의 ①과 ②가 둘 다 들어 있습니다.
   - $e_{\nu,N}\to0$이면: "점수 $D_\nu$는 $(1+o(1))\times$ 결정적 상수"라는 뜻입니다.

### 기호

| 기호 | 의미 |
|---|---|
| $\psi_{\nu,q}$ | $q$번째 섭동 인자 (6.2) |
| $D_\nu=\partial_{u_\nu}\log(\text{spin weight})$ | 점수 |
| $\lambda_\nu=c_\nu s_N$ | 종류 $\nu$의 평균 항 수 |
| $\langle\cdot\rangle$ | 뿌리 고정, 기울인 경로 하나에 대한 평균 |
| $\mathbb E_{\mathbf u}$ | $\mathbf u$ 고정, 뿌리에 대한 평균 |
| $e_{\nu,N}$ | 상대 평균 절대 편차 (열적 + 무질서) |

### 물리적 의미

SK에서 Ghirlanda–Guerra 항등식의 출발점은 $\mathbb E\langle|H_p-\mathbb E\langle H_p\rangle|\rangle=o(N)$입니다 ($H_p$는 $p$-spin 섭동
해밀토니안). $D_\nu$가 그 역할을 합니다. 차이는 $\langle\cdot\rangle$이 단순한 Gibbs 평균이 아니라 **Parisi 위계를 따라 상태를 고르고
그 안에서 배치를 고르는** 평균이라는 점입니다.

---

## 문단 2. Lemma 6.1

> **Lemma 6.1 (Averaged score concentration).** For each fixed $L$ and each fixed type $\nu$,
> $$\int e_{\nu,N}(\mathbf u)\,\pi(d\mathbf u)\longrightarrow0.\tag{6.5}$$
> The assertion holds for the reservoir as well as for the original system. Constants need not be
> uniform in $L$ or $\nu$.

### 문장별 풀이

1. **"$\int e_{\nu,N}(\mathbf u)\,\pi(d\mathbf u)\to0$"**
   $\pi$는 각 $u_\mu$를 구간 $I_\mu$에서 균등하게 뽑는 곱측도입니다 (6.1절). 그러니 이 식은 "**대부분의** 매개변수 $\mathbf u$에서 오차가
   작다"는 뜻이고, 특정한 $\mathbf u$ 하나에서 작다는 뜻은 아닙니다. 점별로 주장하지 않는 이유는 문단 8에서 나옵니다. 볼록 함수의
   도함수는 꺾이는 점에서 튈 수 있기 때문입니다. 1차 상전이 점에서 자화가 불연속인 것과 같은 현상입니다.
2. **"holds for the reservoir as well"**
   증명은 "독립 유계 입력 $O(N)$개"라는 구조만 쓰므로 clause 평균이 $\rho_N$인 저장소에도 그대로 적용됩니다 (5장 마지막 문단).
3. **"Constants need not be uniform in $L$ or $\nu$"**
   아래 상수들에 $1/m_1=L$과 $1/|I_\nu|=j^j$가 들어갑니다. $L$과 $\nu$를 고정한 뒤 $N\to\infty$로 보내므로 상관없습니다.

---

## 문단 3. 증명 시작: 점수의 한계 (6.6)

> Hold the other parameters fixed, write $u=u_\nu$, $n=n_\nu$, and put $\lambda_\nu=c_\nu s_N$.
> Choose an open interval $J_\nu$ containing $I_\nu$ such that $|t_\nu|+|u|<1/2$ throughout its
> closure. On this interval, pathwise,
> $$|D_\nu|\leq2n,\qquad -4n\leq\partial_uD_\nu=-\sum_{q=1}^{n}\frac{(g_{0,q}S_{0,q})^2}{\psi_{\nu,q}^{2}}\leq0.\tag{6.6}$$

### 문장별 풀이

1. **"Hold the other parameters fixed, write $u=u_\nu$, $n=n_\nu$"**
   다른 종류의 $u_\mu$ ($\mu\ne\nu$)는 상수로 두고, $u_\nu$ 하나만 변수로 봅니다. 이후 "$u$"는 $u_\nu$, "$n$"은 $n_\nu$입니다.
2. **"Choose an open interval $J_\nu$ containing $I_\nu$ such that $|t_\nu|+|u|<1/2$"**
   $I_\nu=[j^{-j},2j^{-j}]$보다 조금 넓은 열린 구간이 필요한 이유는 문단 8에서 $u\pm\rho$ (구간 밖으로 살짝 나간 점)를 쓰기 때문입니다.
   존재 확인: $t_\nu=1/j\le1/4$이고 $2j^{-j}\le2/256$이므로 합이 $1/2$보다 충분히 작아, 여유 있는 구간을 잡을 수 있습니다. ✓
3. **"$|D_\nu|\le2n$"**
   $|t g\sigma|+|u g_0S_0|\le|t|+|u|<1/2$ ($|g|,|g_0|,|\sigma|\le1$) ⇒ $\psi>1/2$ ⇒ 항 하나 $|g_0S_0/\psi|<1/(1/2)=2$ ⇒ $n$개 합 $\le2n$. ✓
4. **"$\partial_uD_\nu=-\sum(g_0S_0)^2/\psi^2$"**
   항 하나를 미분하면 $\partial_u\frac{a}{1+\dots+ua}=-\frac{a\cdot a}{\psi^2}$ ($a=g_0S_0$). $a^2\le1$, $\psi^{-2}<4$ ⇒ 항 하나는 $[-4,0]$ ⇒ $-4n\le\partial_uD\le0$. ✓

"pathwise"는 이 부등식이 모든 뿌리·경로 값에서 (평균하지 않고) 성립한다는 뜻입니다.

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

### 문장별 풀이

1. **"Let $X_0(u)$ be the random root log partition function before taking the root expectation."**
   섭동된 계의 분배함수를 3.1절의 power-mean 재귀로 뿌리까지 올린 값의 로그, 즉 $X_0=\log T_0Z$입니다. 뿌리가 무작위이므로
   $X_0$도 무작위이고, $u$의 함수입니다. 그 기대값이 5장의 $P_N^{L,\mathbf u}$입니다.
2. **"regard the logarithm of the spin weight as $X_L$ and the spin partition function as the step with exponent $m_L=1$"**
   3.1절의 재귀는 $X_{L-1}=\log Z$에서 시작합니다. 여기서는 한 칸 더 내려가서
   $$X_L(\sigma)=\log(\text{스핀 가중치}),\qquad X_{L-1}=\log\sum_\sigma e^{X_L(\sigma)}=\frac1{m_L}\log\sum_\sigma e^{m_LX_L}\quad(m_L=1)$$
   로 둡니다. 그러면 **모든 단계가 같은 모양** $X_{d-1}=\frac1{m_d}\log P_de^{m_dX_d}$가 되고, 마지막 단계의 기울인 커널
   $K_L=e^{X_L-X_{L-1}}$이 바로 Gibbs 측도입니다. (마지막 단계의 $P_L$은 확률이 아니라 개수 측도지만, 미분 계산에는 상관없습니다.)
3. **"Differentiation of one backward step gives $\partial X_{d-1}=K_d(\partial X_d)$"** — 원문이 생략한 계산:
   $m=m_d$로 쓰면 $X_{d-1}=\frac1m\log\int e^{mX_d}\,dP_d$이므로
   $$\partial X_{d-1}=\frac1m\cdot\frac{\int e^{mX_d}\,m\,\partial X_d\,dP_d}{\int e^{mX_d}\,dP_d}=\int\partial X_d\;\underbrace{e^{m(X_d-X_{d-1})}dP_d}_{=K_d\ (3.2)}=K_d(\partial X_d).$$ ✓
4. **"$\partial^2X_{d-1}=K_d(\partial^2X_d)+m_d\mathrm{Var}_{K_d}(\partial X_d)$"** — 한 번 더 미분:
   $K_d(\partial X_d)=\int\partial X_d\,e^{m(X_d-X_{d-1})}dP_d$에서 곱의 미분을 하면
   $$\partial^2X_{d-1}=\int\partial^2X_d\,dK_d+\int\partial X_d\cdot m(\partial X_d-\partial X_{d-1})\,dK_d
   =K_d(\partial^2X_d)+m\bigl[K_d((\partial X_d)^2)-(K_d\partial X_d)^2\bigr].$$
   괄호가 $K_d$ 아래 분산입니다. ✓ ("로그 적률생성함수의 2차 도함수는 분산"의 한 단계 판.)
5. **"Thus, for $M_d=\langle D_\nu\mid\mathscr F_d\rangle$, $X_0'(u)=\langle D_\nu\rangle$"** — 맨 아래에서 위로 올라갑니다:
   - 맨 아래: $\partial X_L=\partial_u\log(\text{스핀 가중치})=D_\nu$ (문단 1의 풀이 1). 이것이 $M_L$입니다.
   - 한 단계 위: $\partial X_{L-1}=K_L(D_\nu)=\langle D_\nu\mid\mathscr F_{L-1}\rangle=M_{L-1}$.
   - 계속하면 $\partial X_d=M_d$ (기울인 법칙 아래 조건부 기대값의 탑 성질). 뿌리에서 $\partial X_0=M_0=\langle D_\nu\rangle$. 이것이 (6.7)입니다. ✓

   **뜻**: 자유에너지의 $u$-도함수 = 점수의 평균. 이 사실 덕분에 무질서 요동 ②를 "$X_0'$의 요동"으로 바꿀 수 있습니다.
6. **(6.8)의 등식** — 4의 식을 맨 위에서부터 펼칩니다:
   $$X_0''=K_1(\partial^2X_1)+m_1\mathrm{Var}_{K_1}(M_1)
   =K_1K_2(\partial^2X_2)+m_2K_1\mathrm{Var}_{K_2}(M_2)+m_1\mathrm{Var}_{K_1}(M_1)=\cdots$$
   $$=\langle\partial^2X_L\rangle+\sum_{d=1}^Lm_d\langle\mathrm{Var}_{K_d}(M_d)\rangle .$$
   여기서 $\partial^2X_L=\partial_uD_\nu$이고, 깊이 $d$ 커널 아래 $M_d$의 분산은 마팅게일 차분의 조건부 2차 모멘트
   $\mathrm{Var}_{K_d}(M_d)=\langle(M_d-M_{d-1})^2\mid\mathscr F_{d-1}\rangle$입니다 ($K_d(M_d)=M_{d-1}$이므로). ✓
   - **점검 ($L=1$)**: 보조 변수가 없으면 $X_0''=\langle\partial D\rangle+\mathrm{Var}_{\rm Gibbs}(D)$ — 익숙한 "$\partial^2\log Z$ = 평균 곡률 + 분산"입니다.
7. **(6.8)의 부등식 "$\ge m_1\mathrm{Var}(D_\nu\mid\mathscr F_0)-4n$"**
   - $m_d\ge m_1$ (지수가 증가)이므로 $\sum_dm_d\langle(M_d-M_{d-1})^2\rangle\ge m_1\sum_d\langle(M_d-M_{d-1})^2\rangle$.
   - 마팅게일 차분은 서로 직교하므로 $\sum_d\langle(M_d-M_{d-1})^2\rangle=\langle(M_L-M_0)^2\rangle=\langle(D-\langle D\rangle)^2\rangle=\mathrm{Var}(D\mid\mathscr F_0)$.
   - (6.6)에서 $\langle\partial_uD\rangle\ge-4n$.
   - 합치면 (6.8). ✓

### 기호

| 기호 | 의미 |
|---|---|
| $X_L=\log(\text{spin weight})$ | 잎에서의 로그 가중치 (스핀 배치의 함수) |
| $X_{d-1}=m_d^{-1}\log P_de^{m_dX_d}$ | (3.2) 위의 Monasson 퍼텐셜, $X_{L-1}=\log Z$ |
| $X_0(u)$ | 뿌리의 로그 (무작위, $u$의 함수) |
| $M_d=\langle D_\nu\mid\mathscr F_d\rangle$ | 깊이 $d$까지의 접두부가 주어졌을 때 점수의 평균 (마팅게일) |
| $\mathrm{Var}(D\mid\mathscr F_0)$ | 뿌리 고정, 경로에 대한 점수의 분산 = 열적 분산 |

### 물리적 의미

$X_0''$의 분산 항이 **깊이별로 $m_d$로 가중**됩니다. "점수가 어느 깊이-$d$ 상태에 있느냐에 따라 달라지는 정도"는 $m_d$만큼만
자유에너지의 곡률에 기여합니다. $m$이 "상태 사이 요동의 무게"라는 Parisi 매개변수의 해석이 그대로 보입니다. 가장 얕은 깊이의 가중치
$m_1=1/L$이 가장 작으므로 하한이 $m_1$로 정해지고, 그래서 상수가 $L$에 의존합니다.

### 수치 확인

$L=3$, $m=(1/3,2/3,1)$, 스핀 $N=2$, 깊이 1·2에 Rademacher 부호 하나씩, 섭동 항 4개 (무작위 $g,g_0$, 깊이, 자리, $S_0$), $t=0.2$.
$X_0(u)$를 power mean으로 직접 계산해 유한 차분 ($h=10^{-4}$)과 비교:

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

### 문장별 풀이

1. **"use the tilted path law at the current $u$"** — $K_d$는 $u$에 의존합니다. 문단 4의 $\langle\cdot\rangle$, $\mathrm{Var}$는 모두 지금 보고 있는
   $u$ 값에서의 기울인 법칙입니다.
2. **"At fixed root all derivatives are justified …"** — 뿌리를 고정하면 섭동 항이 유한 개이고, 각 $\psi$는 $u$의 매끄러운 양함수이며,
   재귀도 유한 단계입니다. 그래서 미분과 유한 합·적분의 교환이 문제없습니다.
3. **"Their root expectations are justified by the finite moments of the Poisson counts."** — 다음 문단에서 $\mathbb E X_0'$, $\mathbb E X_0''$를 씁니다.
   $|X_0'|\le2n$, $|X_0''|\le4n+\sum_dm_d(2n)^2\lesssim n+n^2$이고 $\mathbb En^2<\infty$이므로 지배 수렴으로 기대값과 미분을 바꿀 수 있습니다. ✓

---

## 문단 6. 열적 분산의 적분: (6.9), (6.10)

> Integrating (6.8) over $I_\nu=[a,b]$ and using $|X_0'|\leq2n$ yields
> $$\int_a^b\mathbb E_{\mathbf u}\mathrm{Var}(D_\nu\mid\mathscr F_0)\,du\leq\frac{4\lambda_\nu(1+b-a)}{m_1}.\tag{6.9}$$
> Consequently the interval-averaged thermal mean absolute deviation, divided by $\lambda_\nu$, is
> at most
> $$\left(\frac{4(1+|I_\nu|)}{m_1|I_\nu|\lambda_\nu}\right)^{1/2}.\tag{6.10}$$

### 문장별 풀이

1. **"Integrating (6.8) over $I_\nu=[a,b]$"** — (6.8)을 $\mathrm{Var}$에 대해 정리하면 $m_1\mathrm{Var}(D\mid\mathscr F_0)\le X_0''(u)+4n$. 양변을 $u\in[a,b]$에서 적분:
   $$m_1\int_a^b\mathrm{Var}\,du\le\int_a^bX_0''\,du+4n(b-a)=X_0'(b)-X_0'(a)+4n(b-a).$$
2. **"using $|X_0'|\le2n$"** — $X_0'=\langle D\rangle$이고 (6.6)에서 $|D|\le2n$이므로 $|X_0'(b)-X_0'(a)|\le4n$. 따라서
   $$m_1\int_a^b\mathrm{Var}\,du\le4n+4n(b-a)=4n(1+b-a).$$
   **요점**: 곡률을 적분하면 도함수의 차이가 되고, 도함수(평균 점수)는 유계입니다. 그래서 곡률의 큰 값, 곧 큰 분산은 오래 지속될 수 없습니다.
3. **(6.9)** — 뿌리에 대해 평균하고 $\mathbb En=\lambda_\nu$를 넣으면 됩니다. 뿌리의 법칙은 $u$와 무관하므로 적분 순서를 바꿔도 됩니다. ✓
4. **"Consequently the interval-averaged thermal mean absolute deviation, divided by $\lambda_\nu$, is at most (6.10)"**
   "열적 평균 절대 편차"는 $\mathbb E\langle|D-\langle D\rangle|\rangle$, 곧 0절의 조각 ①입니다. 분산에서 절대 편차로 넘어가는 데 Jensen을 두 번 씁니다.
   $$\frac1{|I|}\int_I\mathbb E\langle|D-\langle D\rangle|\rangle du
   \overset{(\mathrm a)}{\le}\frac1{|I|}\int_I\sqrt{\mathbb E\mathrm{Var}}\,du
   \overset{(\mathrm b)}{\le}\Bigl(\frac1{|I|}\int_I\mathbb E\mathrm{Var}\,du\Bigr)^{1/2}
   \overset{(6.9)}{\le}\Bigl(\frac{4\lambda(1+|I|)}{m_1|I|}\Bigr)^{1/2}.$$
   (a) $\mathbb E|Y|\le\sqrt{\mathbb EY^2}$ (뿌리와 경로를 함께 평균), (b) 구간 평균에 대한 $\sqrt{\cdot}$의 오목성. 마지막에 $\lambda$로 나누면 (6.10). ✓
5. **크기** — $\lambda_\nu=c_\nu N^{3/4}$이므로 (6.10)은 $\propto\lambda^{-1/2}\propto N^{-3/8}\to0$. 조각 ①이 끝났습니다.

**판단 메모.** 상수가 $1/|I_\nu|=j^j$와 $1/m_1=L$에 의존하므로 $\nu$와 $L$에 대해 균등하지 않습니다. Lemma 6.1이 명시한 대로이며,
이후 극한은 항상 "$L$, $\nu$ 고정 후 $N\to\infty$" 순서입니다.

---

## 문단 7. 뿌리 평균의 요동: 볼록 함수 $G$와 (6.11)

원문이 길어서 다섯 덩어리로 나눠 인용합니다.

### (7a) 목표와 볼록 함수 $G$

> *Fluctuations of the root mean.* It remains to concentrate $X_0'$ over the root. By (6.8), the
> random function $G(u)=X_0(u)+2nu^2$ is convex on $J_\nu$.

- **"It remains to concentrate $X_0'$ over the root."** — 남은 것은 0절의 조각 ② $\langle D\rangle-\mathbb E\langle D\rangle$인데, (6.7)로 이것은
  $X_0'(u)-\mathbb EX_0'(u)$, 곧 **무작위 함수 $X_0$의 도함수의 요동**입니다.
- **"$G(u)=X_0(u)+2nu^2$ is convex"** — 문단 8의 도구는 "볼록 함수의 값이 집중하면 도함수도 집중한다"입니다. 그런데 $X_0$ 자체는 볼록이라는
  보장이 없습니다. (6.8)이 주는 것은 $X_0''\ge-4n$뿐입니다. 그래서 $2nu^2$를 더해 곡률을 $4n$만큼 올립니다:
  $$G''=X_0''+4n\ \ge\ m_1\mathrm{Var}(D\mid\mathscr F_0)\ \ge0.$$ ✓
  $2nu^2$은 나중에 떼어 내야 하는 "보정"입니다 (문단 8의 풀이 6).

### (7b) 필요한 두 추정 (6.11)

> Uniformly for $u\in J_\nu$ and all the other parameters,
> $$\mathrm{Var}(G(u))\leq C_\nu N,\qquad|\mathbb E_{\mathbf u}G'(u)|\leq C_\nu\lambda_\nu.\tag{6.11}$$

- 첫째: 함수 **값** $G(u)$의 무질서 요동은 표준편차 $O(\sqrt N)$ (자유에너지의 self-averaging).
- 둘째: 도함수의 **평균**은 크기 $O(\lambda_\nu)$.
- 문단 8에서 이 둘의 크기 비교 $\sqrt N\ll\lambda_\nu=c_\nu N^{3/4}$가 결정적입니다.
- 둘째 추정은 바로 나옵니다: $G'=X_0'+4nu$, $|X_0'|\le2n$, $|4nu|\le4n\cdot\tfrac12=2n$ ⇒ $|\mathbb EG'|\le4\lambda_\nu$. ✓ (원문 마지막 문장 "follows directly from (6.6)")

### (7c) Efron–Stein 부등식

> To prove the first estimate, condition on the physical and total perturbation counts. Conditional on
> the latter count, its types and sites are independent labels; changing a label replaces a single
> bounded factor. Apply the Efron–Stein variance inequality [EfronStein]
> $\mathrm{Var}Z\le\frac12\sum_j\mathbb E(Z-Z^{(j)})^2$, where $Z^{(j)}$ is obtained by independently
> resampling the $j$th input. For completeness, with independent inputs $X_1,\ldots,X_k$, let $E_j$
> integrate only $X_j$ and let $\mathscr G_j=\sigma(X_1,\ldots,X_j)$. The Doob differences are
> $D_j=\mathbb E[Z-E_jZ\mid\mathscr G_j]$. Orthogonality and Jensen give
> $$\mathrm{Var}Z=\sum_j\mathbb ED_j^2\le\sum_j\mathbb E(Z-E_jZ)^2=\frac12\sum_j\mathbb E(Z-Z^{(j)})^2.$$
> This independent-input decomposition requires neither identical laws nor a symmetric statistic;
> see Efron–Stein [Section 2].

- **"condition on the physical and total perturbation counts"** — 분산을 두 단계로 나눕니다:
  $$\mathrm{Var}G=\underbrace{\mathbb E\,\mathrm{Var}(G\mid\text{개수들})}_{\text{(7d)에서}}+\underbrace{\mathrm{Var}\,\mathbb E(G\mid\text{개수들})}_{\text{(7e)에서}}.$$
  개수를 고정하면 나머지 무질서는 **독립인 입력들의 유한한 목록**이 됩니다: clause마다 ($\theta_k$, 자리 $p$개), 장 $h_i$ ($N$개),
  섭동 항마다 (종류, 자리).
- **"Conditional on the latter count, its types and sites are independent labels"** — 종류별 Poisson 개수 $n_\mu$들 대신 총 개수
  $n_{\rm tot}\sim\mathrm{Pois}(s_N)$를 고정하면, 각 항의 종류는 확률 $c_\mu$로 i.i.d.이고 자리도 i.i.d.입니다 (Poisson 분할의 역방향). 그래서 각 항을
  하나의 독립 입력으로 볼 수 있습니다.
- **Efron–Stein 부등식** — "입력 하나를 바꿀 때의 변화"로 분산을 누르는 도구입니다. 원문의 짧은 증명을 풀면:
  - $D_j:=\mathbb E[Z\mid\mathscr G_j]-\mathbb E[Z\mid\mathscr G_{j-1}]$ (Doob 마팅게일 차분). 입력이 독립이므로
    $\mathbb E[E_jZ\mid\mathscr G_j]=\mathbb E[Z\mid\mathscr G_{j-1}]$이고, 따라서 원문 식 $D_j=\mathbb E[Z-E_jZ\mid\mathscr G_j]$와 같습니다. ✓
  - 직교성: $\mathrm{Var}Z=\sum_j\mathbb ED_j^2$. ✓
  - 조건부 Jensen: $D_j^2\le\mathbb E[(Z-E_jZ)^2\mid\mathscr G_j]$. ✓
  - $\mathbb E(Z-E_jZ)^2$는 "$j$번째 입력에 대한 조건부 분산"의 평균이고, 이것은 그 입력을 독립 복사본으로 바꾼 $Z^{(j)}$와의 차이로
    $\frac12\mathbb E(Z-Z^{(j)})^2$입니다 (같은 법칙의 독립 두 표본 $Y,Y'$에 대해 $\mathrm{Var}Y=\frac12\mathbb E(Y-Y')^2$). ✓
  - 입력들이 같은 분포일 필요가 없다는 마지막 문장은, clause·장·섭동처럼 종류가 다른 입력을 한 목록에 섞어도 된다는 뜻입니다.

### (7d) 입력 하나의 영향은 유계

> Resampling one interaction, field, or perturbation term changes $X_0$ by a bounded amount: this is
> immediate for the spin weights and is preserved by each power mean. When a term is removed, its
> unused independent mark variables can be integrated out, so the same assertion holds for addition or
> deletion of a term. Conditional variances are therefore bounded by a constant times the number of
> root variables.

- **"immediate for the spin weights"** — 입력 하나를 바꾸면 스핀 가중치가 모든 배치에서 같은 범위의 배수로 바뀝니다:
  clause 하나 $e^{\pm2B}$, 장 하나 $e^{\pm2H}$, 섭동 하나 $[1/3,3]$배 ($\psi\in[\tfrac12,\tfrac32]$).
- **"preserved by each power mean"** — Lemma 3.1의 단조성·동차성: 가중치가 점별로 $[c^{-1},c]$배 범위에서 바뀌면 power mean도 같은 범위에서
  바뀝니다. 따라서 $|X_0-X_0^{(j)}|\le2B$, $2H$, 또는 $\log3$. ✓
- **"its unused independent mark variables can be integrated out"** — 섭동 항을 지우면 그 항의 표시 변수가 남는데, 아무도 읽지 않으므로 사전분포로
  적분하면 power mean이 바뀌지 않습니다 (상수의 power mean은 그 상수). 그래서 항의 추가·삭제도 같은 방식으로 다룹니다.
- **"Conditional variances are therefore bounded by a constant times the number of root variables."** — Efron–Stein에 대입:
  $$\mathrm{Var}(X_0\mid\text{개수들})\le\tfrac12\sum_j(\text{변화 상한})^2\le C\cdot(M+N+n_{\rm tot}).$$
  평균하면 $C(\alpha N+N+s_N)=O(N)$. ✓

### (7e) 개수의 요동과 마무리

> Conditional means are Lipschitz functions of the counts, with bounded Lipschitz constants. If $Q,Q'$
> are independent copies of a Poisson variable and $b$ is $C$-Lipschitz, then
> $$\mathrm{Var}(b(Q))=\tfrac12\mathbb E(b(Q)-b(Q'))^2\leq C^2\mathrm{Var}(Q).$$
> Applying this to the independent counts completes the $O(N)$ estimate. The correction $2nu^2$ obeys
> the same estimates. The derivative bound in (6.11) follows directly from (6.6).

- **"Conditional means are Lipschitz functions of the counts"** — $b(M,n_{\rm tot})=\mathbb E[X_0\mid M,n_{\rm tot}]$에서 개수를 1 늘리는 것은 항 하나를
  추가하는 것이므로 (7d)에 따라 $b$가 유계만큼 변합니다.
- **Lipschitz 보조정리** — $\mathrm{Var}\,b(Q)=\frac12\mathbb E(b(Q)-b(Q'))^2\le\frac{C^2}2\mathbb E(Q-Q')^2=C^2\mathrm{Var}Q$. ✓
  개수가 여러 개(clause 수, 섭동 수)면 그 독립 개수들에 Efron–Stein을 다시 적용합니다. Poisson이므로 $\mathrm{Var}M=\alpha N$, $\mathrm{Var}\,n_{\rm tot}=s_N$ ⇒ $O(N)$. ✓
- **"The correction $2nu^2$ obeys the same estimates."** — $\mathrm{Var}(2nu^2)=4u^4\lambda_\nu$이고 $u\le1/2$이므로 $\le\lambda_\nu=O(N)$. 공분산 항까지
  $\mathrm{Var}(X+Y)\le2\mathrm{Var}X+2\mathrm{Var}Y$로 처리하면 $\mathrm{Var}G\le C_\nu N$. ✓

**검토 메모.** "총 개수에 조건부로 종류·자리가 i.i.d. 라벨"은 종류별 개수가 독립 $\mathrm{Pois}(c_\mu s_N)$인 원래 모형과 같은 법칙입니다
(Poisson 분할의 역). 따라서 이렇게 바꿔 보는 것은 정당합니다. ✓

### 물리적 의미

$\mathrm{Var}(\log Z)=O(N)$은 자유에너지의 **self-averaging**입니다 (상대 요동 $N^{-1/2}$). SK에서는 가우스 집중으로 얻지만, 희석 모형에서는
"clause 하나 = 유계 영향"이라는 국소성만으로 충분합니다.

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

### 문장별 풀이

1. **"Put $\bar G=\mathbb E_{\mathbf u}G$ and $Z=G-\bar G$"** — $\bar G$는 평균 함수 (결정적), $Z$는 요동. (6.11)에서 $\mathbb E|Z(u)|\le\sqrt{\mathrm{Var}G}\le\sqrt{C_\nu N}$.
   $\bar G$도 볼록입니다 (볼록 함수들의 평균). 또 $\bar G'=\mathbb EG'$ (문단 5의 교환).

2. **"forward and backward difference quotients imply …"** — 볼록 함수의 기울기는 오른쪽 할선과 왼쪽 할선 사이에 있습니다:
   $$\frac{G(u)-G(u-\rho)}\rho\le G'(u)\le\frac{G(u+\rho)-G(u)}\rho,\qquad\bar G\text{도 같음}.$$
   - 위쪽 한계: $G'(u)$를 오른쪽 할선으로 누르고 $G=\bar G+Z$를 넣으면
     $$G'(u)-\bar G'(u)\le\frac{Z(u+\rho)-Z(u)}\rho+\underbrace{\frac{\bar G(u+\rho)-\bar G(u)}\rho-\bar G'(u)}_{\le\,\bar G'(u+\rho)-\bar G'(u)}.$$
     (밑줄: $\bar G$의 오른쪽 할선은 $\bar G'(u+\rho)$ 이하.)
   - 아래쪽 한계: 왼쪽 할선으로 같은 계산을 하면 $\bar G'(u)-G'(u)\le\frac{|Z(u)|+|Z(u-\rho)|}\rho+\bar G'(u)-\bar G'(u-\rho)$.
   - 두 쪽을 합쳐 크게 잡으면 원문의 부등식. ✓

   **뜻**: 도함수의 요동은 (i) 값의 요동 $|Z|$를 간격 $\rho$로 나눈 것과 (ii) 평균 기울기가 $[u-\rho,u+\rho]$에서 변하는 양으로 눌립니다.
   (ii)는 평균 함수가 그 근처에서 심하게 꺾일 때만 큽니다.

3. **"The monotonicity of $\bar G'$ gives $\int_a^b[\bar G'(u+\rho)-\bar G'(u-\rho)]du\le2\rho[\dots]$"** — (ii)는 점마다 클 수 있지만 $u$에 대해
   적분하면 작습니다. 두 적분의 차이를 정리하면 양 끝 길이 $2\rho$짜리 구간만 남습니다:
   $$\int_a^b\bar G'(u+\rho)du-\int_a^b\bar G'(u-\rho)du=\int_{b-\rho}^{b+\rho}\bar G'-\int_{a-\rho}^{a+\rho}\bar G'\le2\rho\,\bar G'(b+\rho)-2\rho\,\bar G'(a-\rho).$$
   ($\bar G'$가 증가하므로 각 구간에서 최댓값·최솟값으로 누름.) ✓
   이것이 Lemma 6.1이 **구간 평균**으로만 성립하는 이유입니다. 꺾이는 점 근처의 $u$에서는 (ii)가 크지만, 그런 $u$의 비율이 작습니다.

4. **"Together with (6.11), this proves (6.12)"** — 2의 부등식에 기대값을 취하고 $u$에 대해 구간 평균:
   - 첫 항: $\mathbb E|Z|\le\sqrt{C_\nu N}$이 네 번 나오므로 $\le4\sqrt{C_\nu N}/\rho$.
   - 둘째 항: $\frac1{|I|}\cdot2\rho[\bar G'(b+\rho)-\bar G'(a-\rho)]\le\frac{2\rho}{|I|}\cdot2C_\nu\lambda_\nu$ ((6.11) 둘째 식).
   - 합치면 (6.12). ✓ ($G'-\bar G'=G'-\mathbb EG'$.)

5. **"take $\rho=N^{-1/8}$ … After division by $\lambda_\nu=c_\nu N^{3/4}$, both terms tend to zero"** — $\rho$는 두 항을 맞바꾸는 손잡이입니다:
   $\rho$가 작으면 첫 항 $\sqrt N/\rho$가 커지고, 크면 둘째 항 $\rho\lambda/|I|$가 커집니다. $\lambda$로 나누면
   $$\frac{\sqrt N}{\rho\lambda_\nu}\propto N^{\frac12+\frac18-\frac34}=N^{-1/8}\to0,\qquad\frac{\rho}{|I_\nu|}=j^jN^{-1/8}\to0.$$ ✓
   "within the fixed neighborhood margin": $N$이 크면 $\rho$가 작아져서 $u\pm\rho\in J_\nu$ (문단 3에서 $J_\nu$를 넓게 잡은 이유). ✓

6. **"Removing the correction to $G'$ costs at most $C_\nu\lambda_\nu^{-1/2}$"** — 지금 제어한 것은 $G'$의 요동인데 필요한 것은 $X_0'$의 요동입니다.
   $$G'-\mathbb EG'=(X_0'-\mathbb EX_0')+4u(n-\lambda_\nu)$$
   이므로 둘의 차이는 $4u|n-\lambda_\nu|\le2|n-\lambda_\nu|$, 평균 $\le2\sqrt{\mathrm{Var}\,n}=2\sqrt{\lambda_\nu}$. $\lambda_\nu$로 나누면 $2\lambda_\nu^{-1/2}\to0$. ✓

7. **"Thus the root contribution to (6.4) tends to zero."** — 조각 ② $\mathbb E|\langle D\rangle-\mathbb E\langle D\rangle|/\lambda_\nu=\mathbb E|X_0'-\mathbb EX_0'|/\lambda_\nu$의
   구간 평균이 $\to0$. ✓

8. **"Combining it with (6.10) proves the result after integration over $u_\nu$."** — 0절의 분해와 삼각부등식:
   $$\mathbb E\langle|D-\mathbb E\langle D\rangle|\rangle\le\underbrace{\mathbb E\langle|D-\langle D\rangle|\rangle}_{①\ (6.10)}+\underbrace{\mathbb E|\langle D\rangle-\mathbb E\langle D\rangle|}_{②\ \text{풀이 7}}.$$
   $\lambda_\nu$로 나누고 $u_\nu\in I_\nu$에 대해 평균하면 $\to0$. ✓

9. **"All estimates are uniform in the other parameters, so … (6.5)."** — 위 상수들은 다른 $u_\mu$ 값에 의존하지 않습니다. 그래서 나머지 좌표에 대해
   $\pi$로 평균해도 같은 한계가 남고, (6.5)가 됩니다. ✓

### 지수 정리 (원문에 없는 보충)

$s_N=N^\gamma$로 일반화하면 $\lambda$로 나눈 두 항은 $N^{1/2-\gamma}/\rho$와 $\rho$입니다. 둘을 같게 하는 $\rho=N^{(1/2-\gamma)/2}$에서 오차는
$N^{(1/2-\gamma)/2}$이므로 **$\gamma>1/2$가 필요**합니다. 값의 요동 $\sqrt N$이 점수의 크기 $N^\gamma$보다 작아야 한다는 뜻입니다. 5장의 $s_N=N^{3/4}$는
$1/2<\gamma<1$을 만족합니다 ($\gamma<1$은 pressure를 바꾸지 않기 위한 조건, (5.3)).

**판단 메모 (수렴 속도).** 둘째 항 $j^jN^{-1/8}$은 정성적으로 0으로 가지만 매우 느립니다. 가장 작은 $j=4$에서도 $j^j=256$이므로,
이 항이 1보다 작아지려면 $N>256^8\approx1.8\times10^{19}$이 필요합니다. 증명은 속도를 쓰지 않으므로 문제는 없습니다.

### 수치 확인

무작위 볼록 함수 $G,\bar G$ (서로 다른 $\log\cosh$ 혼합 + 2차항) 2000쌍, 무작위 $u$, $\rho\in(0.01,0.3)$에서 풀이 2의 부등식의
(좌변 − 우변) 최댓값 $=-0.82<0$. ✓

### 물리적 의미

GG 논법의 핵심 문장, "자유에너지가 self-averaging하고 볼록하면 내부 에너지도 거의 모든 온도에서 self-averaging"을 정확히 재현했습니다.
열적 부분 (6.10)은 **비열이 유한하다**는 것과 같은 논리입니다 (곡률의 적분 = 도함수의 유계 변화). 무질서 부분 (6.12)는 볼록 함수의 도함수가
평균 주위의 작은 요동으로만 움직인다는 사실입니다. 결과적으로 $\langle|D_\nu-\mathbb E\langle D_\nu\rangle|\rangle=o(s_N)$, 곧 섭동 점수는
replica에 무관한 상수입니다. 6.4절은 이 집중을 "anchor replica의 점수는 다른 replica들과 상관이 없다"는 형태로 바꿉니다.

---

## 요약

- 오차 (6.4)를 열적 요동 ①과 무질서 요동 ②로 나누고, 둘 다 $X_0(u)$로 다룹니다 ($X_0'=\langle D\rangle$, (6.7)).
- ①: $X_0''=\langle\partial D\rangle+\sum_dm_d\langle(M_d-M_{d-1})^2\rangle\ge m_1\mathrm{Var}-4n$ (6.8). 곡률을 적분하면 도함수 차이로 유계 → (6.9) →
  Jensen으로 (6.10), 크기 $O(\lambda^{-1/2})$.
- ②: $G=X_0+2nu^2$를 볼록하게 만들고, Efron–Stein으로 $\mathrm{Var}G=O(N)$ (6.11). 할선 부등식과 $\bar G'$의 단조성으로 (6.12), $\rho=N^{-1/8}$,
  보정 $4u(n-\lambda)$ 제거.
- 결과 Lemma 6.1: $\int e_{\nu,N}\,d\pi\to0$. 상수는 $L$과 $\nu$에 의존하고, $s_N=N^\gamma$에서 $\gamma>1/2$가 필요합니다.

**다음 절 예고**: 6.3절에서 낮은 cavity 증분, 모든 점수의 집중, 모든 나무 모멘트의 수렴을 동시에 만족하는 하나의 수열 $(N_j,\mathbf u_j)$를
고릅니다 (Lemma 6.2).
