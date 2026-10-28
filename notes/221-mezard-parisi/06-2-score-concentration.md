# 6.2 Concentration of each perturbation score — 문단별 해설

원문: `build/sections/perturbations.tex` 6.2절, PDF 16–17쪽. 번호는 PDF 기준
(식 (6.3)–(6.12), Lemma 6.1). 앞 절 참조: (6.1), (6.2), (5.3), Lemma 3.1, (3.2).

> **이 판의 읽는 법.** 원문 인용 바로 아래에 **문장별 풀이**를 두었습니다. 원문 문장(또는 한 덩어리)을 다시
> 짧게 인용하고, 그 뜻과 원문이 생략한 중간 식을 바로 이어 적었습니다. 새 항이 나올 때마다 **🔭 물리** 줄에서
> 그 항이 스핀 글라스 전체 계에서 무엇인지 (어떤 물리량, 어떤 상황인지) 적었습니다. 검증(✓)과 수치 확인은
> 그 뒤에 따로 둡니다.

---

## 0. 이 절의 큰 그림 (원문에는 없는 안내)

### 무대: 지금 다루는 계

| 대상 | 스핀 글라스 언어 |
|---|---|
| 스핀 $\sigma\in\{\pm1\}^N$ | Ising 스핀 $N$개. 무작위 희석 그래프 위에서 $p$체 상호작용 |
| 뿌리 (root) | **quenched 무질서**: 결합 $\theta_k$, 그래프 (clause의 자리), 외부장 $h_i$, 그리고 섭동의 개수·자리. 시료(sample) 하나를 정함 |
| 보조 변수 (깊이 $1..L-1$) | 섭동이 가진 Rademacher "색". 기울인 커널로 뽑히면 **깊이별 상태 (cluster) 선택**에 해당 |
| 기울인 경로 하나 | 상태를 위계대로 하나 고르고, 그 상태 안에서 스핀 배치를 하나 뽑은 것 = **replica 하나** |
| $\langle\cdot\rangle$ | 그 시료에서의 열적 평균. RSB 언어로 $\sum_\alpha W_\alpha\langle\cdot\rangle_\alpha$ (상태 무게 × 상태 안 평균) |
| $\mathbb E_{\mathbf u}$ | 시료 평균 (sample-to-sample 평균) |

### 목표

섭동의 **응답 관측량** $D_\nu$가 시료·상태·replica에 무관한 상수로 몰려 있음을 보입니다. 차이를 두 조각으로 나눕니다.
$$D_\nu-\mathbb E\langle D_\nu\rangle=\underbrace{\bigl(D_\nu-\langle D_\nu\rangle\bigr)}_{\text{① 열적 요동}}+\underbrace{\bigl(\langle D_\nu\rangle-\mathbb E\langle D_\nu\rangle\bigr)}_{\text{② 시료 간 요동}}.$$

| 조각 | 무엇이 흔들리나 | 쓰는 도구 | 물리적 원리 | 문단 |
|---|---|---|---|---|
| ① | 같은 시료에서 상태·배치를 다시 뽑을 때 | 자유에너지의 2차 도함수 = 분산 | 요동-응답 정리, 감수율 유한 | 4–6 |
| ② | 시료 자체를 다시 뽑을 때 | 볼록 함수 + 값의 집중 ⇒ 도함수의 집중 | 자유에너지의 self-averaging | 7–8 |

두 조각 모두 같은 함수 $X_0(u)$ (섭동된 시료의 자유에너지)로 다룹니다. $X_0'(u)=\langle D_\nu\rangle$이기 때문입니다 ((6.7)).

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
   즉 **$D_\nu$는 "로그 가중치의 $u_\nu$-도함수"**입니다.

   🔭 **물리 — 섭동 인자 $\psi$의 각 항.** $\log\psi\approx t\,g\,\sigma_i+u\,g_0S_0$ (작은 세기에서)이므로 섭동은 해밀토니안에 한-체 항을 더한 것입니다.
   | 항 | 스핀 글라스에서의 뜻 |
   |---|---|
   | $\sigma_{i_q}$ | 무작위로 고른 스핀 하나 (탐침이 닿는 자리) |
   | $g_q=g(\epsilon)$ | 그 자리가 속한 **상태의 색** $\epsilon$에 따라 부호·크기가 정해지는 계수 |
   | $t\,g\,\sigma_i$ | **상태마다 방향이 다른 약한 국소장** (세기 $t=1/j$). 같은 깊이-$d$ 상태 안에서는 같은 장, 다른 상태에서는 독립인 장 |
   | $u\,g_0S_0$ | 응답을 재기 위한 아주 약한 시험 항 (세기 $u\sim j^{-j}$). $S_0=\sigma_i$이면 또 하나의 국소장, $S_0=1$이면 스핀과 무관한 **상태별 에너지 이동** (상태를 색에 따라 조금 더/덜 무겁게 함) |

   🔭 **물리 — $D_\nu$.** $u$에 **켤레(conjugate)인 관측량**입니다. 장 $h$에 켤레인 것이 자화 $\sum_i\sigma_i$, 역온도에 켤레인 것이 에너지이듯이,
   $D_\nu\approx\sum_qg_0(\epsilon_q)S_{0,q}$는 "탐침 자리들에서 **상태 색으로 가중한 자화**" (또는 $S_0=1$이면 상태 색의 합)입니다. 섭동 전체에
   대한 계의 응답이고, 크기는 탐침 수 $\sim N^{3/4}$에 비례합니다.

2. **"on a tilted path, including its terminal Gibbs configuration"**
   $D_\nu$가 의존하는 것: 뿌리 (개수 $n_\nu$, 자리 $i_q$), 보조 변수 ($g_q$, $g_{0,q}$를 정하는 색), 마지막 스핀 배치 ($\sigma_{i_q}$, $S_{0,q}$).

   🔭 **물리.** $D_\nu$는 **replica 하나에서 잰 값**입니다. 같은 시료라도 replica (상태 + 배치)마다 값이 다릅니다.

3. **"Let $\langle\cdot\rangle$ denote expectation along one tilted path conditional on the root"**
   뿌리를 고정하고, 기울인 커널 $K_1,\dots,K_{L-1}$로 깊이마다 보조 변수를, $K_L$ (Gibbs)로 스핀을 뽑는 평균.

   🔭 **물리.** 시료 하나의 **열평형 평균**. RSB 그림에서는 "깊이 1 상태를 Parisi 무게로 고르고, 그 안에서 깊이 2 상태를 고르고, …, 마지막
   순수 상태 안에서 Boltzmann 평균" — 즉 $\sum_\alpha W_\alpha\langle\cdot\rangle_\alpha$입니다. 보조 변수가 없으면 ($L=1$) 보통의 Gibbs 평균.

4. **"let $\mathbb E_{\mathbf u}$ average the root at fixed $\mathbf u$"** — 무질서(뿌리)에 대한 평균. $\mathbf u$는 고정된 매개변수.

   🔭 **물리.** **시료 평균** (실험으로 치면 같은 제조법으로 만든 여러 시료를 측정해 평균). $\mathbf u$는 "실험자가 정한 탐침 세기"라서 평균하지 않습니다.

5. **"$e_{\nu,N}(\mathbf u)=\frac{1}{c_\nu s_N}\mathbb E\langle|D_\nu-\mathbb E\langle D_\nu\rangle|\rangle$"**
   - 분모 $c_\nu s_N=\mathbb En_\nu=:\lambda_\nu$로 나눈 **상대 오차**.
   - 빼는 것이 **전체 평균** $\mathbb E\langle D\rangle$이므로 0절의 ①과 ②가 모두 들어 있습니다.

   🔭 **물리.** $e_{\nu,N}\to0$은 "**탐침 응답이 시료에도, 상태에도, replica에도 의존하지 않는다**" (self-averaging + 상태 간 무요동)입니다.
   이것이 Ghirlanda–Guerra 항등식과 확률적 안정성 (stochastic stability)의 출발점입니다. SK에서 $\mathbb E\langle|H_p-\mathbb E\langle H_p\rangle|\rangle=o(N)$에 해당합니다.

### 기호

| 기호 | 수학적 정의 | 스핀 글라스에서의 뜻 |
|---|---|---|
| $\psi_{\nu,q}$ | (6.2) 섭동 인자 | 상태 색에 따른 약한 국소장 + 시험 항 |
| $D_\nu$ | $\partial_{u_\nu}\log(\text{가중치})$ | 탐침 세기 $u$에 켤레인 응답 (색 가중 자화) |
| $\lambda_\nu=c_\nu s_N$ | 평균 항 수 | 탐침이 닿는 자리 수 $\sim N^{3/4}$ (전체 스핀의 비율 $N^{-1/4}\to0$) |
| $\langle\cdot\rangle$ | 기울인 경로 하나의 평균 | 시료 하나의 열평형 평균 (상태 무게 포함) |
| $\mathbb E_{\mathbf u}$ | 뿌리 평균 | 시료 평균 |
| $e_{\nu,N}$ | 상대 평균 절대 편차 | 응답의 상대 요동 (열적 + 시료 간) |

---

## 문단 2. Lemma 6.1

> **Lemma 6.1 (Averaged score concentration).** For each fixed $L$ and each fixed type $\nu$,
> $$\int e_{\nu,N}(\mathbf u)\,\pi(d\mathbf u)\longrightarrow0.\tag{6.5}$$
> The assertion holds for the reservoir as well as for the original system. Constants need not be
> uniform in $L$ or $\nu$.

### 문장별 풀이

1. **"$\int e_{\nu,N}(\mathbf u)\,\pi(d\mathbf u)\to0$"**
   $\pi$는 각 $u_\mu$를 $I_\mu$에서 균등하게 뽑는 곱측도. "**대부분의** $\mathbf u$에서 오차가 작다"는 뜻이고 점별 주장은 아닙니다.

   🔭 **물리.** "거의 모든 탐침 세기에서". GG 항등식이 "거의 모든 온도에서" 성립하는 것과 같습니다. 예외가 될 수 있는 것은 **상전이 점**
   (예: 1차 전이에서 두 상태가 공존해 응답이 상태마다 다르게 튀는 세기)인데, 그런 점은 측도가 0에 가깝게 드뭅니다 (문단 8의 풀이 3).

2. **"holds for the reservoir as well"** — 증명이 "독립 유계 입력 $O(N)$개"만 쓰므로 clause 평균이 $\rho_N$인 저장소에도 적용됩니다.

   🔭 **물리.** 저장소는 스핀 하나를 뺀 $N$ 스핀 시료 (cavity 계). 거기서도 탐침 응답이 자기평균한다는 뜻입니다.

3. **"Constants need not be uniform in $L$ or $\nu$"** — 상수에 $1/m_1=L$과 $1/|I_\nu|=j^j$가 들어갑니다.

   🔭 **물리.** 위계를 촘촘히 할수록 ($L$↑) 얕은 층의 무게 $m_1=1/L$이 작아져 그 층의 요동이 자유에너지 곡률에 덜 드러나고, 탐침이 약할수록
   ($j$↑) 세기 구간이 좁아져 평균 효과가 약해집니다. 그래서 수렴이 느려지지만, $L$, $\nu$를 고정한 뒤 $N\to\infty$로 보내므로 상관없습니다.

---

## 문단 3. 증명 시작: 점수의 한계 (6.6)

> Hold the other parameters fixed, write $u=u_\nu$, $n=n_\nu$, and put $\lambda_\nu=c_\nu s_N$.
> Choose an open interval $J_\nu$ containing $I_\nu$ such that $|t_\nu|+|u|<1/2$ throughout its
> closure. On this interval, pathwise,
> $$|D_\nu|\leq2n,\qquad -4n\leq\partial_uD_\nu=-\sum_{q=1}^{n}\frac{(g_{0,q}S_{0,q})^2}{\psi_{\nu,q}^{2}}\leq0.\tag{6.6}$$

### 문장별 풀이

1. **"Hold the other parameters fixed, write $u=u_\nu$, $n=n_\nu$"** — 다른 종류의 $u_\mu$는 상수, $u_\nu$ 하나만 변수.

   🔭 **물리.** 여러 탐침 장 중 하나의 세기만 조절하며 그 응답을 봅니다 (다른 장은 켠 채로 고정).

2. **"Choose an open interval $J_\nu$ … $|t_\nu|+|u|<1/2$"** — 문단 8에서 $u\pm\rho$를 쓰려고 $I_\nu$보다 조금 넓게 잡습니다.
   $t_\nu\le1/4$, $2j^{-j}\le2/256$이므로 가능합니다. ✓

   🔭 **물리.** **약한 섭동 영역**: 탐침 하나가 그 자리의 Boltzmann 가중치를 최대 2배까지만 바꿉니다 ($\psi\in(\tfrac12,\tfrac32)$). 계의 성질을 탐침이 "부수지 않는" 범위입니다.

3. **"$|D_\nu|\le2n$"** — $\psi>1/2$ ⇒ 항 하나 $|g_0S_0/\psi|<2$ ⇒ $n$개 합 $\le2n$. ✓

   🔭 **물리.** 응답은 탐침 수에 비례하는 **크기 상한(extensive bound)**을 가집니다. 자화가 $|\sum\sigma_i|\le N$인 것과 같습니다.

4. **"$\partial_uD_\nu=-\sum(g_0S_0)^2/\psi^2\in[-4n,0]$"** — 항 하나 미분 $-a^2/\psi^2$, $a^2\le1$, $\psi^{-2}<4$. ✓

   🔭 **물리.** $\partial_uD$는 응답의 **명시적(배치 고정) 변화율**, 즉 열적 요동과 무관한 "고유 곡률"입니다. $\psi$가 $u$에 대해 지수가 아니라
   1차식이라서 생기는 음의 항이고, 탐침 수만큼만 클 수 있습니다. (만약 $\psi=e^{ug_0S_0}$였다면 이 항은 0입니다.)

"pathwise"는 모든 시료·replica에서 평균 없이 성립한다는 뜻입니다.

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
   섭동된 계의 분배함수를 power-mean 재귀로 뿌리까지 올린 값의 로그, $X_0=\log T_0Z$. 시료마다 다르고 $u$의 함수입니다.

   🔭 **물리.** **시료 하나의 자유에너지** ($-\beta F$). 다만 RSB 위계를 Monasson 방식 ($Z^m$ 재가중)으로 포함한 "위계 자유에너지"입니다.
   그 시료 평균이 5장의 $P_N^{L,\mathbf u}$ (≈ $N\times$ pressure).

2. **"regard the logarithm of the spin weight as $X_L$ … exponent $m_L=1$"**
   $$X_L(\sigma)=\log(\text{스핀 가중치}),\qquad X_{L-1}=\log\sum_\sigma e^{X_L(\sigma)}\ (m_L=1),\qquad X_{d-1}=\frac1{m_d}\log P_de^{m_dX_d}.$$
   모든 단계가 같은 모양이 되고, 마지막 단계의 기울인 커널 $K_L=e^{X_L-X_{L-1}}$이 Gibbs 측도.

   🔭 **물리 — 재귀의 각 층.**
   | 항 | 뜻 |
   |---|---|
   | $X_L(\sigma)=-\beta H(\sigma)+\sum\log\psi$ | 배치 하나의 (음의) 에너지 × $\beta$ |
   | $X_{L-1}=\log\sum_\sigma e^{X_L}$ | 가장 깊은 상태 (순수 상태) 하나의 자유에너지 |
   | $X_{d-1}=\frac1{m_d}\log P_de^{m_dX_d}$ | 깊이 $d-1$ 상태의 자유에너지 = 그 안의 하위 상태들을 **$Z^{m_d}$로 합친** 것 (Monasson). $m_d\to1$: 하위 상태들을 그냥 더함, $m_d\to0$: 하위 상태들의 자유에너지를 단순 평균 |
   | $K_L$ | 상태 안의 Boltzmann 분포 |
   | $K_d=e^{m_d(X_d-X_{d-1})}P_d$ | 부모 상태 안에서 하위 상태를 고를 확률 $\propto Z_{\text{하위}}^{m_d}$ — **Parisi 상태 무게** |

3. **"$\partial X_{d-1}=K_d(\partial X_d)$"** — $X_{d-1}=\frac1m\log\int e^{mX_d}dP_d$를 미분하면
   $$\partial X_{d-1}=\frac{\int e^{mX_d}\partial X_d\,dP_d}{\int e^{mX_d}dP_d}=\int\partial X_d\,\underbrace{e^{m(X_d-X_{d-1})}dP_d}_{=K_d}=K_d(\partial X_d).$$ ✓

   🔭 **물리.** **Hellmann–Feynman / 켤레 관계**: 자유에너지의 장 도함수 = 켤레 관측량의 평균. 위계 버전에서는 "부모 상태의 응답 = 하위
   상태들의 응답을 Parisi 무게 $K_d$로 평균한 것".

4. **"$\partial^2X_{d-1}=K_d(\partial^2X_d)+m_d\mathrm{Var}_{K_d}(\partial X_d)$"** — 곱의 미분:
   $$\partial^2X_{d-1}=K_d(\partial^2X_d)+m\bigl[K_d((\partial X_d)^2)-(K_d\partial X_d)^2\bigr].$$ ✓

   🔭 **물리 — 요동-응답 정리의 한 층.** 감수율 (자유에너지의 2차 도함수) = (하위 상태들의 감수율 평균) + $m_d\times$(**형제 상태들 사이의 응답
   분산**). 상태마다 응답이 다르면 그만큼 감수율이 커지는데, 그 기여가 $m_d$로 깎입니다. $m_d\to0$이면 상태 간 요동은 감수율에 안 보이고
   (quenched), $m_d=1$이면 보통의 요동-응답 정리 $\chi=\langle\delta D^2\rangle$입니다.

5. **"Thus, for $M_d=\langle D_\nu\mid\mathscr F_d\rangle$, $X_0'(u)=\langle D_\nu\rangle$"** — 맨 아래 $\partial X_L=D_\nu=M_L$에서 시작해 3을 반복하면
   $\partial X_d=M_d$, 뿌리에서 $X_0'=M_0=\langle D_\nu\rangle$. ✓

   🔭 **물리.**
   - $M_d$ = **깊이 $d$ 상태 안에서의 평균 응답** (그 상태의 "색 가중 자화"). $M_L=D_\nu$는 배치 하나의 값, $M_0=\langle D\rangle$은 시료 전체 평균.
   - (6.7) = "시료의 자유에너지를 탐침 세기로 미분하면 평균 응답". 그래서 ② (시료 간 요동)는 **자유에너지 기울기의 시료 간 요동**으로 바뀝니다.

6. **(6.8)의 등식** — 4를 위에서부터 펼치면
   $$X_0''=\langle\partial^2X_L\rangle+\sum_{d=1}^Lm_d\langle\mathrm{Var}_{K_d}(M_d)\rangle,\qquad\partial^2X_L=\partial_uD,\quad\mathrm{Var}_{K_d}(M_d)=\langle(M_d-M_{d-1})^2\mid\mathscr F_{d-1}\rangle.$$ ✓
   점검 ($L=1$): $X_0''=\langle\partial D\rangle+\mathrm{Var}_{\rm Gibbs}(D)$.

   🔭 **물리 — 위계적 요동-응답 정리.**
   | 항 | 뜻 |
   |---|---|
   | $X_0''$ | 탐침 세기에 대한 **감수율** $\chi_u=\partial_u\langle D\rangle$ |
   | $\langle\partial_uD\rangle$ | 고유 (비열적) 기여 — 문단 3의 4 |
   | $M_d-M_{d-1}$ | 깊이 $d$에서 상태를 한 단계 더 구체적으로 정했을 때 응답이 바뀌는 양 = **깊이 $d$ 상태 간 응답 차이** ($d=L$이면 순수 상태 안의 열적 요동) |
   | $m_d\langle(M_d-M_{d-1})^2\rangle$ | 깊이 $d$의 요동이 감수율에 주는 기여, Parisi 무게 $m_d$로 가중 |

   Parisi 해에서 감수율이 $\chi=\beta\int(1-q(x))dx$처럼 층별 overlap을 $x$로 가중해 합한 꼴이 되는 것과 같은 구조입니다.

7. **(6.8)의 부등식** — $m_d\ge m_1$, 마팅게일 차분 직교성 $\sum_d\langle(M_d-M_{d-1})^2\rangle=\mathrm{Var}(D\mid\mathscr F_0)$, $\langle\partial D\rangle\ge-4n$. ✓

   🔭 **물리.** $\mathrm{Var}(D\mid\mathscr F_0)$는 **시료 하나 안에서 replica마다 응답이 다른 정도 전부** (상태 간 + 상태 안). 부등식은
   "감수율이 작으면 그 시료 안의 응답 요동도 작다" — 요동-응답 정리의 방향을 거꾸로 쓴 것입니다. 가장 얕은 층의 무게 $m_1$이 가장 작으므로
   그 층 요동이 가장 "숨기 쉽고", 하한은 $m_1$로 정해집니다.

### 기호

| 기호 | 수학적 정의 | 스핀 글라스에서의 뜻 |
|---|---|---|
| $X_L$ | 로그 스핀 가중치 | 배치 하나의 $-\beta\times$에너지 |
| $X_d$ | 재귀의 깊이 $d$ 값 | 깊이 $d$ 상태의 (Monasson) 자유에너지 |
| $X_0(u)$ | 뿌리 로그 | 시료의 위계 자유에너지 |
| $K_d$ | 기울인 커널 (3.2) | Parisi 상태 무게 $\propto Z^{m_d}$ |
| $M_d$ | $\langle D\mid\mathscr F_d\rangle$ | 깊이 $d$ 상태 안의 평균 응답 |
| $X_0''$ | 2차 도함수 | 탐침 감수율 |
| $\mathrm{Var}(D\mid\mathscr F_0)$ | 경로에 대한 분산 | 시료 안에서 replica 간 응답 요동 |

### 수치 확인

$L=3$, $m=(1/3,2/3,1)$, 스핀 $N=2$, 깊이 1·2에 Rademacher 부호 하나씩, 섭동 항 4개 (무작위 $g,g_0$, 깊이, 자리, $S_0$), $t=0.2$.
$X_0(u)$를 power mean으로 직접 계산해 유한 차분 ($h=10^{-4}$)과 비교:

| $u$ | $X_0'$ 유한차분 | $\langle D\rangle$ (6.7) | $X_0''$ 유한차분 | (6.8) 등식 우변 | $m_1\mathrm{Var}+\langle\partial_uD\rangle$ | $m_1\mathrm{Var}-4n$ |
|---|---|---|---|---|---|---|
| 0 | 0.38022862 | 0.38022862 | −0.393064 | −0.393064 | −0.6982 | −15.72 |
| 0.05 | 0.36049007 | 0.36049007 | −0.396741 | −0.396741 | −0.6934 | −15.72 |
| 0.1 | 0.34052713 | 0.34052713 | −0.402063 | −0.402063 | −0.6913 | −15.72 |

(6.7)과 (6.8)의 등식이 일치하고, 부등식의 두 하한도 성립합니다. ✓ (이 장난감에서는 고유 곡률 $\langle\partial D\rangle$가 커서 $X_0''<0$입니다.
그래서 문단 7에서 $2nu^2$를 더해 볼록하게 만들어야 합니다.)

---

## 문단 5. 미분의 정당화

> Here the conditional expectations and variances use the tilted path law at the current $u$. At
> fixed root all derivatives are justified by the bounded score and its derivatives; the finite
> recursion then justifies the displayed differentiation formulas. Their root expectations are
> justified by the finite moments of the Poisson counts.

### 문장별 풀이

1. **"use the tilted path law at the current $u$"** — $K_d$가 $u$에 의존하므로, 평균·분산은 지금 $u$ 값에서의 기울인 법칙입니다.

   🔭 **물리.** 감수율은 **탐침을 켠 상태의 평형**에서 잽니다. 탐침을 바꾸면 상태 무게도 따라 바뀝니다.

2. **"At fixed root all derivatives are justified …"** — 시료 하나에서는 탐침 수가 유한하고 $\psi$가 매끄러우므로 미분이 문제없습니다.

3. **"Their root expectations are justified by the finite moments of the Poisson counts."** — $|X_0'|\le2n$, $|X_0''|\lesssim n+n^2$, $\mathbb En^2<\infty$ ⇒ 지배 수렴. ✓

   🔭 **물리.** 탐침 수가 시료마다 Poisson으로 흔들리지만 분산이 유한하므로, 시료 평균한 자유에너지를 미분해도 됩니다.

---

## 문단 6. 열적 분산의 적분: (6.9), (6.10)

> Integrating (6.8) over $I_\nu=[a,b]$ and using $|X_0'|\leq2n$ yields
> $$\int_a^b\mathbb E_{\mathbf u}\mathrm{Var}(D_\nu\mid\mathscr F_0)\,du\leq\frac{4\lambda_\nu(1+b-a)}{m_1}.\tag{6.9}$$
> Consequently the interval-averaged thermal mean absolute deviation, divided by $\lambda_\nu$, is
> at most
> $$\left(\frac{4(1+|I_\nu|)}{m_1|I_\nu|\lambda_\nu}\right)^{1/2}.\tag{6.10}$$

### 문장별 풀이

1. **"Integrating (6.8) over $I_\nu=[a,b]$"** —
   $$m_1\int_a^b\mathrm{Var}\,du\le\int_a^bX_0''\,du+4n(b-a)=X_0'(b)-X_0'(a)+4n(b-a).$$

   🔭 **물리.** 감수율을 장 세기에 대해 적분하면 **응답의 총 변화량**이 됩니다 ($\int\chi\,du=\Delta\langle D\rangle$). 비열을 온도에 대해 적분하면
   에너지 변화가 되는 것과 같습니다.

2. **"using $|X_0'|\le2n$"** — $|X_0'(b)-X_0'(a)|\le4n$ ⇒ $m_1\int\mathrm{Var}\le4n(1+b-a)$.

   🔭 **물리.** 응답 $\langle D\rangle$은 크기 상한이 있으므로 총 변화량도 유계입니다. 따라서 **감수율이 큰 구간 (= 응답 요동이 큰 구간)은
   오래 지속될 수 없습니다**. 상전이 점에서 감수율이 발산해도 그 폭은 좁습니다.

3. **(6.9)** — 시료 평균, $\mathbb En=\lambda_\nu$. ✓

4. **"interval-averaged thermal mean absolute deviation … (6.10)"** — Jensen 두 번:
   $$\frac1{|I|}\int_I\mathbb E\langle|D-\langle D\rangle|\rangle du\le\frac1{|I|}\int_I\sqrt{\mathbb E\mathrm{Var}}\,du\le\Bigl(\frac1{|I|}\int_I\mathbb E\mathrm{Var}\Bigr)^{1/2}\le\Bigl(\frac{4\lambda(1+|I|)}{m_1|I|}\Bigr)^{1/2}.$$
   $\lambda$로 나누면 (6.10). ✓

   🔭 **물리.** 응답의 열적 요동은 표준편차 $\sim\sqrt{\lambda}$, 응답 자체는 $\sim\lambda$이므로 **상대 요동 $\lambda^{-1/2}\sim N^{-3/8}$**. 탐침 $N^{3/4}$개에 대한
   큰수의 법칙 — 정상적인 열역학계에서 상전이점을 피하면 에너지의 상대 요동이 $N^{-1/2}$인 것과 같습니다. 핵심은 이것이 **상태 간 요동까지
   포함**한다는 점입니다: 서로 다른 상태 (cluster)에서 잰 응답도 같은 값으로 몰립니다.

**판단 메모.** 상수가 $1/|I_\nu|=j^j$와 $1/m_1=L$에 의존하므로 $\nu$와 $L$에 대해 균등하지 않습니다. 극한은 항상 "$L$, $\nu$ 고정 후 $N\to\infty$" 순서입니다.

---

## 문단 7. 뿌리 평균의 요동: 볼록 함수 $G$와 (6.11)

원문이 길어서 다섯 덩어리로 나눠 인용합니다.

### (7a) 목표와 볼록 함수 $G$

> *Fluctuations of the root mean.* It remains to concentrate $X_0'$ over the root. By (6.8), the
> random function $G(u)=X_0(u)+2nu^2$ is convex on $J_\nu$.

- **"It remains to concentrate $X_0'$ over the root."** — 남은 것은 ② $\langle D\rangle-\mathbb E\langle D\rangle=X_0'-\mathbb EX_0'$.

  🔭 **물리.** **시료마다 평균 응답이 다른가?** 같은 제조법의 시료들이 탐침에 같은 평균 응답을 보이는지의 문제입니다.

- **"$G(u)=X_0(u)+2nu^2$ is convex"** — (6.8)이 주는 것은 $X_0''\ge-4n$뿐이므로 $2nu^2$를 더해 $G''=X_0''+4n\ge m_1\mathrm{Var}\ge0$. ✓

  🔭 **물리.** 보통 자유에너지는 켤레 장에 대해 볼록합니다 (감수율 ≥ 0 = 열역학적 안정성). 여기서는 문단 3의 4에서 본 "고유 곡률"
  $\langle\partial D\rangle\le0$ 때문에 그 성질이 깨질 수 있어, 무해한 2차항 $2nu^2$ (물리적 의미 없는 보정, 나중에 제거)을 더해 볼록성을 되살립니다.

### (7b) 필요한 두 추정 (6.11)

> Uniformly for $u\in J_\nu$ and all the other parameters,
> $$\mathrm{Var}(G(u))\leq C_\nu N,\qquad|\mathbb E_{\mathbf u}G'(u)|\leq C_\nu\lambda_\nu.\tag{6.11}$$

- 첫째: 자유에너지 **값**의 시료 간 표준편차 $O(\sqrt N)$.
- 둘째: 도함수의 **평균**은 $O(\lambda_\nu)$: $G'=X_0'+4nu$, $|X_0'|\le2n$, $|4nu|\le2n$ ⇒ $|\mathbb EG'|\le4\lambda_\nu$. ✓

  🔭 **물리.** 첫째는 **자유에너지의 self-averaging** (총 자유에너지 $\sim N$, 시료 간 요동 $\sim\sqrt N$, 상대 요동 $N^{-1/2}$). 둘째는 평균 응답이
  탐침 수에 비례한다는 것. 문단 8의 핵심은 "자유에너지 잡음 $\sqrt N$ ≪ 응답 신호 $N^{3/4}$"입니다.

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

- **"condition on the physical and total perturbation counts"** —
  $\mathrm{Var}G=\mathbb E\,\mathrm{Var}(G\mid\text{개수들})+\mathrm{Var}\,\mathbb E(G\mid\text{개수들})$. 개수를 고정하면 무질서는 독립 입력들의 목록
  (clause마다 결합과 자리, 장 $h_i$, 섭동 항마다 종류와 자리).

  🔭 **물리.** 시료 간 차이의 원천을 둘로 나눕니다: (i) **결합·그래프·장의 구체적 값** (같은 결합 수에서도 다름), (ii) **결합 수 자체** (희석
  그래프에서 clause 수가 Poisson으로 흔들림).

- **"its types and sites are independent labels"** — 총 개수에 조건부로 각 섭동 항의 종류·자리는 i.i.d. (Poisson 분할의 역).

  🔭 **물리.** 탐침들을 "무작위 자리에 독립으로 꽂힌 것"으로 볼 수 있다는 뜻.

- **Efron–Stein 부등식과 그 증명** — $D_j$는 Doob 마팅게일 차분 ($\mathbb E[E_jZ\mid\mathscr G_j]=\mathbb E[Z\mid\mathscr G_{j-1}]$), 직교성
  $\mathrm{Var}Z=\sum\mathbb ED_j^2$, 조건부 Jensen $D_j^2\le\mathbb E[(Z-E_jZ)^2\mid\mathscr G_j]$, 그리고 $\mathbb E(Z-E_jZ)^2=\frac12\mathbb E(Z-Z^{(j)})^2$. ✓

  🔭 **물리.** "시료의 자유에너지 요동 ≤ **결합 하나를 바꿀 때 자유에너지가 바뀌는 양**들의 제곱합." 국소적인 무질서 하나하나의 영향을 더해
  전체 요동을 누르는 도구입니다. 같은 분포일 필요가 없어서, 결합·장·탐침처럼 종류가 다른 무질서를 한꺼번에 다룰 수 있습니다.

### (7d) 입력 하나의 영향은 유계

> Resampling one interaction, field, or perturbation term changes $X_0$ by a bounded amount: this is
> immediate for the spin weights and is preserved by each power mean. When a term is removed, its
> unused independent mark variables can be integrated out, so the same assertion holds for addition or
> deletion of a term. Conditional variances are therefore bounded by a constant times the number of
> root variables.

- **"immediate for the spin weights and is preserved by each power mean"** — 결합 하나: 가중치가 모든 배치에서 $e^{\pm2B}$배 이내, 장 하나
  $e^{\pm2H}$, 섭동 하나 $[1/3,3]$배. Lemma 3.1의 단조성으로 power mean을 지나도 같은 범위 ⇒ $|X_0-X_0^{(j)}|\le2B$, $2H$, $\log3$. ✓

  🔭 **물리.** **희석 모형의 국소성**: 결합 하나는 스핀 $p$개만 묶으므로 그것을 바꾸면 자유에너지가 $O(1)$만 바뀝니다 (결합 세기가 유계일 때).
  이 사실은 모든 상태, 모든 위계 층에 대해 성립합니다. 상태 무게가 재배치되어도 자유에너지 변화는 $O(1)$입니다.

- **"its unused independent mark variables can be integrated out"** — 지운 탐침의 색 변수는 아무도 읽지 않으므로 적분해 없앱니다.

  🔭 **물리.** 탐침을 뽑아도 그 탐침이 쓰던 "색"은 계에 영향이 없는 유령 변수가 되어 사라집니다.

- **"Conditional variances … constant times the number of root variables"** — $\mathrm{Var}(X_0\mid\text{개수})\le C(M+N+n_{\rm tot})$, 평균 $O(N)$. ✓

  🔭 **물리.** 독립 무질서 $O(N)$개가 각각 $O(1)$씩 기여 ⇒ 자유에너지 분산 $O(N)$.

### (7e) 개수의 요동과 마무리

> Conditional means are Lipschitz functions of the counts, with bounded Lipschitz constants. If $Q,Q'$
> are independent copies of a Poisson variable and $b$ is $C$-Lipschitz, then
> $$\mathrm{Var}(b(Q))=\tfrac12\mathbb E(b(Q)-b(Q'))^2\leq C^2\mathrm{Var}(Q).$$
> Applying this to the independent counts completes the $O(N)$ estimate. The correction $2nu^2$ obeys
> the same estimates. The derivative bound in (6.11) follows directly from (6.6).

- **"Conditional means are Lipschitz functions of the counts"** — 개수 하나 늘림 = 항 하나 추가 ⇒ 유계 변화.
- **Lipschitz 보조정리** — $\mathrm{Var}\,b(Q)\le C^2\mathrm{Var}Q$. ✓ $\mathrm{Var}M=\alpha N$, $\mathrm{Var}\,n_{\rm tot}=s_N$ ⇒ $O(N)$. ✓

  🔭 **물리.** clause 수의 요동 $\sim\sqrt{\alpha N}$이 자유에너지에 주는 요동 $\sim\sqrt N$. 희석 그래프에서 "결합이 몇 개냐"도 시료마다 다르지만
  그 효과는 결합 하나당 $O(1)$이라 같은 크기입니다.

- **"The correction $2nu^2$ obeys the same estimates."** — $\mathrm{Var}(2nu^2)=4u^4\lambda_\nu\le\lambda_\nu$. ✓

**검토 메모.** "총 개수에 조건부로 i.i.d. 라벨"은 원래의 독립 종류별 Poisson 개수와 같은 법칙입니다 (Poisson 분할의 역). ✓

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

1. **"Put $\bar G=\mathbb E_{\mathbf u}G$ and $Z=G-\bar G$"** — $\bar G$ 평균 함수, $Z$ 요동, $\mathbb E|Z|\le\sqrt{C_\nu N}$. $\bar G$도 볼록, $\bar G'=\mathbb EG'$.

   🔭 **물리.** $\bar G(u)$ = **시료 평균 자유에너지** (열역학적 자유에너지, 탐침 세기의 함수). $Z(u)$ = 그 시료의 자유에너지가 평균에서 벗어난 양.

2. **할선 부등식** — 볼록성: $\frac{G(u)-G(u-\rho)}\rho\le G'(u)\le\frac{G(u+\rho)-G(u)}\rho$. $G=\bar G+Z$를 넣으면
   $$G'(u)-\bar G'(u)\le\frac{Z(u+\rho)-Z(u)}\rho+\bar G'(u+\rho)-\bar G'(u),\qquad\bar G'(u)-G'(u)\le\frac{|Z(u)|+|Z(u-\rho)|}\rho+\bar G'(u)-\bar G'(u-\rho).$$
   합치면 원문의 부등식. ✓

   🔭 **물리.** 시료의 평균 응답 $G'$이 열역학적 응답 $\bar G'$에서 벗어나려면 둘 중 하나가 필요합니다:
   (i) **시료의 자유에너지 자체가 크게 흔들림** ($|Z|/\rho$) — 그러나 (6.11)로 $|Z|\sim\sqrt N$뿐;
   (ii) **열역학적 응답 $\bar G'$이 $u$ 근처에서 급변** — 곧 **상전이 근처** (1차 전이에서는 $\bar G'$이 점프, 시료마다 어느 쪽 상에 있는지가 달라
   응답이 튐). 볼록 함수는 잡음이 작으면 기울기도 거의 정해진다는 직관입니다.

3. **"The monotonicity of $\bar G'$ gives …"** —
   $$\int_a^b\bar G'(u+\rho)du-\int_a^b\bar G'(u-\rho)du=\int_{b-\rho}^{b+\rho}\bar G'-\int_{a-\rho}^{a+\rho}\bar G'\le2\rho[\bar G'(b+\rho)-\bar G'(a-\rho)].$$ ✓

   🔭 **물리.** 열역학적 응답 $\bar G'$은 단조 (감수율 ≥ 0)이고 크기가 유계이므로 **총 점프량이 유계**입니다. 그러니 (ii)가 큰 "상전이 근처" 세기는
   $u$ 축의 작은 부분만 차지합니다. 이것이 Lemma 6.1이 **구간 평균**으로만 성립하는 이유이고, GG 항등식이 "거의 모든 온도에서"인 이유와 같습니다.

4. **"Together with (6.11), this proves (6.12)"** — 첫 항 $\le4\sqrt{C_\nu N}/\rho$, 둘째 항 $\le\frac{2\rho}{|I|}\cdot2C_\nu\lambda_\nu$. ✓

   🔭 **물리.** (시료 잡음 / 분해능) + (분해능 × 응답 크기 / 세기 범위).

5. **"take $\rho=N^{-1/8}$ … both terms tend to zero"** — $\lambda$로 나누면 $N^{-1/8}$과 $j^jN^{-1/8}$. ✓ 큰 $N$에서 $u\pm\rho\in J_\nu$.

   🔭 **물리.** $\rho$는 **탐침 세기의 분해능**입니다. 너무 촘촘히 ($\rho$ 작게) 보면 자유에너지 잡음 $\sqrt N$이 할선 기울기를 흔들고, 너무 성기게
   ($\rho$ 크게) 보면 그 사이의 상전이 구조가 섞입니다. 둘의 균형점이 $N^{-1/8}$입니다.

6. **"Removing the correction to $G'$ costs at most $C_\nu\lambda_\nu^{-1/2}$"** — $G'-\mathbb EG'=(X_0'-\mathbb EX_0')+4u(n-\lambda_\nu)$, 차이 $\le2|n-\lambda_\nu|$, 평균 $\le2\sqrt{\lambda_\nu}$. ✓

   🔭 **물리.** 보정항의 요동은 **탐침 개수의 시료 간 Poisson 요동** ($\sqrt{\lambda}$)일 뿐이고, 물리적 응답과 무관합니다.

7. **"Thus the root contribution to (6.4) tends to zero."** — ② $\mathbb E|X_0'-\mathbb EX_0'|/\lambda_\nu$의 구간 평균 $\to0$. ✓

   🔭 **물리.** **평균 응답은 시료에 무관** (sample-to-sample 요동이 상대적으로 사라짐).

8. **"Combining it with (6.10) proves the result after integration over $u_\nu$."** —
   $\mathbb E\langle|D-\mathbb E\langle D\rangle|\rangle\le\mathbb E\langle|D-\langle D\rangle|\rangle+\mathbb E|\langle D\rangle-\mathbb E\langle D\rangle|$, 둘 다 $o(\lambda)$. ✓

   🔭 **물리.** 응답은 **replica에도 (상태·배치), 시료에도** 무관한 상수.

9. **"All estimates are uniform in the other parameters, so … (6.5)."** — 다른 탐침 세기에 대해서도 평균. ✓

   🔭 **물리.** 다른 탐침들을 어떤 세기로 켜 두든 같은 결론 — 탐침을 여러 개 동시에 켜도 된다는 뜻.

### 지수 정리 (원문에 없는 보충)

$s_N=N^\gamma$면 두 항은 $N^{1/2-\gamma}/\rho$와 $\rho$, 최적 오차 $N^{(1/2-\gamma)/2}$ ⇒ **$\gamma>1/2$가 필요**합니다.

🔭 **물리.** 탐침 신호 ($N^\gamma$)가 **자유에너지의 시료 간 잡음** ($N^{1/2}$)보다 커야 탐침 응답을 읽을 수 있습니다. 동시에 $\gamma<1$이어야 탐침이
pressure 밀도를 바꾸지 않습니다 ((5.3)). $N^{3/4}$는 "잡음보다는 크고 계를 바꾸지는 않는" 탐침 수입니다.

**판단 메모 (수렴 속도).** 둘째 항 $j^jN^{-1/8}$은 매우 느리게 0으로 갑니다. $j=4$에서도 이 항이 1보다 작으려면 $N>256^8\approx1.8\times10^{19}$.
증명은 속도를 쓰지 않으므로 논리에는 문제가 없습니다.

### 수치 확인

무작위 볼록 함수 $G,\bar G$ (서로 다른 $\log\cosh$ 혼합 + 2차항) 2000쌍, 무작위 $u$, $\rho\in(0.01,0.3)$에서 풀이 2의 부등식의
(좌변 − 우변) 최댓값 $=-0.82<0$. ✓

### 물리적 의미 (절 전체)

GG 논법 "자유에너지가 self-averaging하고 볼록하면 내부 에너지도 거의 모든 온도에서 self-averaging"을 위계 판으로 재현했습니다.
- 열적 부분 (6.10): 감수율의 적분 = 응답의 유계 변화 ⇒ 시료 안에서 replica (상태 간 포함) 응답 요동이 작음. 비열이 유한하다는 논리.
- 시료 간 부분 (6.12): 자유에너지 잡음 $\sqrt N$ ≪ 응답 $N^{3/4}$ ⇒ 상전이 근처를 제외하면 시료 간 응답 요동이 작음.

결론 $\langle|D_\nu-\mathbb E\langle D_\nu\rangle|\rangle=o(s_N)$: **상태 색에 결합한 탐침의 응답이 어느 상태에서 재든 같다.** 6.4절은 이것을
"탐침을 하나 더 꽂아도 replica들의 통계가 바뀌지 않는다" (확률적 안정성)로 바꾸고, 6.5절은 그것을 Ghirlanda–Guerra형 나무 항등식으로 만듭니다.

---

## 요약

- 오차 (6.4)를 열적 요동 ①과 시료 간 요동 ②로 나누고, 둘 다 시료의 위계 자유에너지 $X_0(u)$로 다룹니다 ($X_0'=\langle D\rangle$, (6.7)).
- ①: 위계적 요동-응답 정리 $X_0''=\langle\partial D\rangle+\sum_dm_d\langle(M_d-M_{d-1})^2\rangle$ (6.8) — 깊이 $d$ 상태 간 응답 차이가 Parisi 무게 $m_d$로
  감수율에 들어감. 감수율 적분 = 유계 응답 변화 ⇒ (6.10), 상대 요동 $N^{-3/8}$.
- ②: 자유에너지의 self-averaging ($\mathrm{Var}=O(N)$, 희석 모형의 국소성 + Efron–Stein) + 볼록성 ⇒ 응답의 시료 간 요동 작음 (6.12), 상전이 근처는 구간 평균으로 처리.
- 결과 Lemma 6.1. 탐침 수 $N^\gamma$는 자유에너지 잡음보다 커야 하므로 $\gamma>1/2$.

**다음 절 예고**: 6.3절에서 낮은 cavity 증분, 모든 점수의 집중, 모든 나무 모멘트의 수렴을 동시에 만족하는 하나의 수열 $(N_j,\mathbf u_j)$를
고릅니다 (Lemma 6.2).
