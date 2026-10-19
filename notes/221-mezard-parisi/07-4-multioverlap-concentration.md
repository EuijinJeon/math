# 7.4 Concentration of every multioverlap — 문단별 해설

원문: `build/sections/decorrelation.tex` 7.4절, PDF 27–28쪽. 번호는 PDF 기준
(식 (7.28)–(7.32), Remark 7.5, 정리 7.1의 증명). 앞 절 참조: 명제 7.4, (7.10), (7.13), (7.26), 정리 6.5.

명제 7.4는 "접두부 아래"의 요동을 제어했습니다. 남은 것은 접두부 자체의 무작위성, 즉 **상태 평균의 상태 간
요동**입니다. 이것을 marker anchor 항등식 한 번으로 처리하고 정리 7.1을 마무리합니다.

---

## 문단 1. 계획

> The covariance estimate controls fluctuations below a sampled prefix. We now use a marker anchor to
> concentrate the prefix projection, and combine this with the averaged continuity estimate.

### 해석

분산 분해 $\mathrm{Var}(R_S)=\mathbb E\,\mathrm{Var}(R_S\mid\mathscr F_{e-1})+\mathrm{Var}(M)$,
$M=\mathbb E[R_S\mid\mathscr F_{e-1}]$에서 첫 항은 명제 7.4 (자식 공분산)로, 둘째 항은 marker anchor 항등식으로
처리합니다. 평가 깊이를 $e$에서 $e-1$로 한 칸 당기는 비용은 마팅게일 연속성 (7.10).

---

## 문단 2. 단일 잎

> For a singleton, use the spin-anchor identity with no added colors and $f=R_S$. It gives
> $\mathbb ER_S^2=(\mathbb ER_S)^2+o_N(1)$.

### 검증

(6.17), $k=0$, spin anchor: $\mathbb E[fR_{a_*}]-\mathbb Ef\,\mathbb ER_{a_*}\to0$. $f=R_{a_*}$ (old tree = anchor 하나)이면
$\mathbb ER^2-(\mathbb ER)^2\to0$. ✓ 자화 $\frac1N\sum_i\sigma_i$의 self-averaging (열적 + 무질서 모두).

---

## 문단 3. marker anchor 구성과 계수 (7.28)

> Suppose $S$ first splits at $e$ and has proper child shapes $T_1,\ldots,T_s$. We will condition one
> step before $e$. Use $S$ as the old tree, designate one of its leaves as a marker anchor, and add a
> full copy of $S$ all of whose leaves split from the anchor at $e-1$. Its first path must be fresh at
> $e-1$, because the old tree has not yet branched there. All other target paths lie in the resulting
> fresh subtree. The extension coefficient on both sides of the prescribed-tree identity is the same
> nonzero number
> $$C(S,e)=-\delta\kappa(S).\tag{7.28}$$

### 해석과 검증

- 목표: anchor와 깊이 $e-1$에서 갈라지는 $S$의 새 복사본 (잎 $|S|$개 = 색 $k=|S|$개).
- 옛 나무 $S$는 깊이 $e$에서 처음 갈라지므로 깊이 $e-1$ 꼭짓점은 홑자식. 목표의 첫 경로는 거기서 새로 갈라져야
  하고 (계수 $m_{e-1}-m_e=-\delta$), 옛 잎은 모두 anchor와 깊이 $\ge e$에서 갈라지므로 재사용 불가. 나머지 목표
  경로는 새로 생긴 부분 나무 안에서 $S$ 모양을 이루며, Lemma 3.4로 그 합이 $\kappa(S)$. ✓
- anchor 혼자인 쪽도 같은 계산: $-\delta\kappa(S)$. ✓ $\kappa(S)\ne0$ (정칙 깊이, (7.19)와 같은 논리).

**수치 확인 (정확 열거).**

| $S$ | $L$ | 옛 나무 쪽 | anchor 혼자 | $-\delta\kappa(S)$ |
|---|---|---|---|---|
| 체리, $e=5$ | 8 | $1/64$ | $1/64$ | $-\tfrac18\cdot(-\tfrac18)=1/64$ ✓ |
| 잎 3개 사슬, $e=3$, 둘째 갈라짐 5 | 7 | $-1/343$ | $-1/343$ | $-\tfrac17\cdot\tfrac1{49}=-1/343$ ✓ |

---

## 문단 4. 접두부 사영의 집중 (7.29), (7.30)

> The target and old copies are conditionally independent and identically distributed below
> $\mathscr F_{e-1}$. With $f=R_S$ and $M=\mathbb E[R_S\mid\mathscr F_{e-1}]$, their product has conditional
> expectation $M^2$. On the anchor-alone side, deleting the marker's continuation below $e-1$ integrates
> a probability kernel to one and leaves the ordinary target law $S$, with mean $\mathbb ER_S$. The
> identity therefore gives
> $$C(S,e)\bigl(\mathbb EM^2-(\mathbb ER_S)^2\bigr)=C(S,e)\mathrm{Var}(M)=o_N(1),\tag{7.29}$$
> and hence
> $$\mathrm{Var}(M)\longrightarrow0\quad\text{at each fixed }L,S,e.\tag{7.30}$$
> Division by $C(S,e)$ is made only at fixed $L$; no uniform lower bound as $L\to\infty$ is needed.

### 검증

- marker anchor이므로 $R_E$ = 색들만의 multi-overlap = 목표 복사본의 $R_S$. 옛 $S$와 목표 $S$는 깊이 $e-1$
  접두부를 공유하고 그 아래 조건부 독립·동분포 ⇒ $\mathbb E[f R_{\rm target}\mid\mathscr F_{e-1}]=M^2$. ✓
  모든 허용 이력이 같은 모양을 주므로 첫 항 $=C\,\mathbb EM^2$.
- anchor 혼자: marker 경로의 $e-1$ 아래 부분은 시험 함수가 읽지 않으므로 적분하면 1 → 목표는 보통의 $S$
  ⇒ $C\,\mathbb ER_S$, 곱하기 $\mathbb Ef=\mathbb ER_S$. ✓
- (6.17) ⇒ (7.29), $L$ 고정에서 $C\ne0$로 나눔 ⇒ (7.30). ✓

### 물리적 의미

$M$은 "깊이 $e-1$ 상태가 주어졌을 때의 multi-overlap 기대값"입니다. $\mathrm{Var}(M)\to0$은 **상태마다 이 값이
같다**, 즉 상태 사이에서 (그리고 무질서에 대해) 요동하지 않는다는 뜻입니다. RSB에서 "모든 상태는 통계적으로
동등하다" (상태의 자기 평균성)에 해당합니다. marker anchor는 스핀을 읽지 않고 상태 구조만 읽기 때문에
이 성질을 깔끔하게 끌어냅니다.

---

## 문단 5. 접두부 아래의 분산: $G$, $G_-$, (7.31)

> It remains to control the conditional variance below this prefix. The child covariances are evaluated
> at $e$, which is separated from all their branching depths; the move to $e-1$ will use martingale
> continuity instead. Set $G=\mathbf1\cdot\prod_j\mu_{e,T_j}$, $G_-=\mathbf1\cdot\prod_j\mu_{e-1,T_j}$. The
> latter is $\mathscr F_{e-1}$-measurable. By (7.13), $\mathbb E(R_S-G)^2\le p_N(S,e)^2$. Keeping all
> proper child depths fixed, the product difference inequality and (7.10) imply
> $$\mathcal A_{L,\eta}\mathbb E(G-G_-)^2\le C_k/L.\tag{7.31}$$
> Here $e$ is itself a ranged coordinate, so the one-step increments are summed before division by $L$.
> Since conditional expectation is the optimal $L^2$ projection,
> $$\mathbb E(R_S-M)^2\le\mathbb E(R_S-G_-)^2\le2p_N(S,e)^2+2\mathbb E(G-G_-)^2.$$

### 검증

- $G$: 자식 평균의 곱을 깊이 $e$에서 계산 (= $\mu_{e,S}$의 자리 평균). (7.13), $B=\mathbf1$ ⇒ $\|R_S-G\|_{L^2}\le p_N(S,e)$. ✓
- $G_-$: 같은 자식 모양을 깊이 $e-1$에서 평가 → $\mathscr F_{e-1}$-가측. ✓ 곱 차이 부등식:
  $|G-G_-|\le\|\prod\mu_e-\prod\mu_{e-1}\|_N\le\sqrt s(\sum_j\|\mu_{e,T_j}-\mu_{e-1,T_j}\|^2)^{1/2}$ ⇒
  $\mathbb E(G-G_-)^2\le s\sum_j\mathbb E\|\mu_{e,T_j}-\mu_{e-1,T_j}\|^2$. 다른 좌표 고정, $e$에 대해 합하면 (7.10)으로
  $\le s^2$, 정규화 $1/L$ ⇒ (7.31). ✓
- $M$은 $R_S$의 $\mathscr F_{e-1}$ 위 $L^2$ 최적 사영 ⇒ $\mathbb E(R_S-M)^2\le\mathbb E(R_S-G_-)^2$. ✓
  $(x+y)^2\le2x^2+2y^2$. ✓

### 수치 확인 (분산 분해, 이산 장난감)

접두부 5값, 조건부로 7원자: $\mathrm{Var}(R)=0.705607=\mathbb E\mathrm{Var}(R\mid\mathscr F)+\mathrm{Var}(M)$ ✓;
$\mathbb E(R-M)^2=0.6956\le\mathbb E(R-G)^2=1.599$ (임의의 $\mathscr F$-가측 $G$) ✓.

---

## 문단 6. 최종 추정 (7.32)

> Variance decomposition and (7.30) now show
> $$\limsup_{N\to\infty}\mathcal A_{L,\eta}\mathrm{Var}(R_S)\le C_k\left(L^{-1}+V_{k-1,L}(\eta/2)^{1/2}\right)\quad\text{for all sufficiently large }L.\tag{7.32}$$
> In this estimate we used $p_N(S,e)^2\le s\sum_jv_N(T_j,e)^{1/2}$ and (7.26) with $\gamma=1/2$: here the
> full average has $D=b(S)$ coordinates because $d$ is absent, while still $D_j=b(T_j)+1$. Proposition
> 7.4 finishes the proof.

### 검증

$\mathrm{Var}(R_S)=\mathbb E(R_S-M)^2+\mathrm{Var}(M)\le2p_N^2+2\mathbb E(G-G_-)^2+\mathrm{Var}(M)$. ✓
- $\mathrm{Var}(M)\to0$ (각 고정 깊이, 유한 개) ⇒ $\limsup_N\mathcal A$에서 0.
- $p_N^2=(\sum_jv_N(T_j,e)^{1/4})^2\le s\sum_jv_N(T_j,e)^{1/2}$ (Cauchy–Schwarz). ✓ (7.26), $\gamma=1/2$: 좌표 $D=b(S)$
  (여기는 $d$가 없음), 자식 항은 $D_j=b(T_j)+1$ 좌표 ($T_j$의 갈라짐 + 평가 깊이 $e$). ⇒ $\le CV_{k-1,L}(\eta/2)^{1/2}$. ✓
- (7.31) ⇒ $C/L$. ✓
- 명제 7.4: $\lim_LV_{k-1,L}(\eta/2)=0$ ⇒ (7.4). ✓ 정리 7.1 증명 완료.

**검토 메모.** 깊이 $e-1$이 $\eta$-정칙 영역 밖이거나 (예: $e/L$이 $\eta$ 근처) 다른 갈라짐과 너무 가까울 수 있지만,
여기서 $e-1$은 평가 깊이일 뿐 목표 갈라짐이 아니므로 (7.28)의 계수는 정칙성과 무관하게 $-\delta\kappa(S)\ne0$입니다.
$\kappa(S)\neq0$에는 $S$ 자체의 정칙성만 필요합니다. 문제없습니다.

---

## 문단 7. Remark 7.5 (극한 순서)

> All uncancelled small denominators in this section occur only in prescribed-tree identity errors. At
> fixed $L$ there are finitely many relevant trees, so those errors disappear before any depth average
> or $L$ limit is taken. Errors that survive the $N$ limit are controlled by the uniform relative
> absolute-cost bound (7.20), the lower-order covariance averages, and the martingale estimate $C/L$. No
> rate of convergence in $N$ uniform in $L$ is used.

### 해석

7장에서 작은 수로 나누는 곳 ($J\sim\delta^{2b}$, $C(S,e)\sim\delta^{b+1}$)은 모두 **항등식 오차**에만 곱해지고, 그
오차는 $L$ 고정에서 $N\to\infty$로 먼저 0이 됩니다. $N$ 극한 뒤에 남는 오차는 $L$에 균등한 상수로 제어됩니다:
(7.20), 하위 공분산 평균, $C/L$. 그래서 $N$에 대한 수렴 속도가 $L$에 균등할 필요가 없습니다.

---

## 요약

- 정리 7.1 증명: $\mathrm{Var}(R_S)=\mathbb E\mathrm{Var}(R_S\mid\mathscr F_{e-1})+\mathrm{Var}(M)$.
- $\mathrm{Var}(M)\to0$: marker anchor, 목표 = anchor와 $e-1$에서 갈라지는 $S$ 복사본, 계수 $-\delta\kappa(S)$ (7.28)
  (정확 열거로 확인), 항등식 (7.29).
- 조건부 분산: 깊이 $e$에서 자식 사영 ($p_N$) + $e\to e-1$ 마팅게일 연속성 (7.31).
- (7.32)와 명제 7.4로 $\lim_L\limsup_N\mathcal A_{L,\eta}\mathrm{Var}(R_S)=0$.
- 물리적으로: 지정한 상태 구조 안의 모든 multi-overlap이 결정적 — 순수 상태 clustering과 상태의 자기 평균성.

**다음 절 예고**: 8장 8.1절에서 한 자리(single-site) 나무를 위계 메시지로 부호화하는 방법을 다룹니다.
