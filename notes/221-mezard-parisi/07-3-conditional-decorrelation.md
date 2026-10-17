# 7.3 Conditional decorrelation — 문단별 해설

원문: `build/sections/decorrelation.tex` 7.3절, PDF 24–27쪽. 번호는 PDF 기준
(명제 7.4, 식 (7.14)–(7.27), 그림 1). 앞 절 참조: Lemma 7.2 (7.6)(7.7), Lemma 7.3, (7.12)(7.13),
정리 6.5 (6.17), Lemma 3.4 ($\kappa$), Lemma 3.5 (charging), (7.1)–(7.3).

7장에서 가장 긴 증명입니다. 잎 수 $k$에 대한 귀납으로 **조건부 공분산 $v_N(S,d)$가 깊이 평균으로 사라짐**을
보입니다. 핵심 아이디어는 3.3절에서 예고한 "목표 갈라짐을 한 칸 늦추면 부호 있는 계수의 합과 절댓값 합이
같은 차수 $\delta$가 된다"입니다.

이 해설의 수치 확인은 모두 **확장 이력을 정확한 유리수로 전부 열거**한 것입니다 (Lemma 3.3의 규칙을 그대로
구현: 안 쓴 옛 잎 계수 1, 현재 나무의 내부 꼭짓점 $\beta$에서 새 경로 계수 $\gamma_\beta=m_{d_\beta}-n_\beta m_{d_\beta+1}$).

---

## 문단 1. 명제 7.4

> **Proposition 7.4.** For every fixed labeled topology $S$ and every $\eta>0$,
> $$\lim_{L\to\infty}\limsup_{N\to\infty}\mathcal A_{L,\eta}v_N(S,d)=0,\tag{7.14}$$
> where the average ranges over all branching depths of $S$ and an additional regular depth $d$
> strictly before its first split. For a singleton, the average ranges over $d$ alone.

### 해석

$d$는 $S$의 첫 갈라짐보다 앞의 평가 깊이, 즉 "모든 잎이 아직 같은 깊이-$d$ 상태에 있는" 접두부입니다.
$v_N(S,d)\to0$: 그 상태 안에서 스핀 곱 벡터 $A_S$의 자리 간 상관이 사라진다. 잎 하나면 순수 상태의
clustering, 잎이 여럿이면 "상태 안 replica 묶음"의 clustering입니다.

---

## 문단 2. 귀납 구조와 $V_{k,L}$ (7.15)

> We induct on the number $k$ of leaves. The induction replaces each proper child by its conditional
> mean. It then applies the prescribed-tree identity to two copies with delayed branching depths;
> after summing the signed coefficients, this becomes a nonnegative three-copy estimate. To keep track
> of the depth averages, let
> $$V_{k,L}(\eta)=\max_{1\le|S|\le k}\limsup_{N\to\infty}\mathcal A_{L,\eta}v_N(S,d).\tag{7.15}$$
> The maximum is over finitely many labeled topologies. Averages of any lower-order covariance used
> below, including averages with extra unused coordinates or shifted depths, are bounded by the
> appropriate $V_{k-1,L}(\eta/2)$, using (7.2) when fractional powers occur.

### 해석

증명의 세 동작: (1) 자식 모양을 조건부 평균으로 사영 ((7.13), 귀납 가정이 오차를 제어), (2) 두 복사본에 나무
항등식을 적용하되 목표 깊이를 한 칸 늦춤, (3) 부호 있는 계수 합을 정리하면 **음이 아닌 세 복사본 양**
(7.7)이 나옴. $V_{k,L}$은 잎 $\le k$개 위상에 대한 최댓값이고, 목표는 $\lim_LV_{k,L}(\eta)=0$.
"이동된 깊이·안 쓴 좌표"가 섞인 평균은 7.1절의 비교 (좌표 합은 $L$로 상쇄, 이동은 $\eta\to\eta/2$)로
$V_{k-1,L}(\eta/2)$에 귀착됩니다.

---

## 문단 3. 기저: 잎 하나 (7.16), (7.17)

> *One leaf.* Take two old paths splitting at $d$, with path $1$ a spin anchor, and add one color
> required to split from the anchor exactly at $d$. The available old path $2$ has coefficient $1$. A
> fresh path can split from both old paths at $d$, with coefficient $-c_d$, or follow path $2$ and
> leave it at $\ell>d$, with coefficient $-c_\ell$, where
> $$c_d=2m_{d+1}-m_d=(d+2)\delta,\qquad c_\ell=\delta\quad(d<\ell\le L-1).\tag{7.16}$$
> From the anchor alone the total coefficient is $-\delta$. Write $X=R_{12}$ and $X_\ell=R_{13}$ for
> the corresponding fresh extension. Each $X_\ell$ has the marginal law of $X$, and
> $\sum_{\ell=d}^{L-1}c_\ell=1+\delta$. The prescribed-tree identity with $f=X$ therefore gives
> $$\frac12\sum_{\ell=d}^{L-1}c_\ell\mathbb E(X-X_\ell)^2=\delta\mathrm{Var}(X)+o_N(1)\le\delta+o_N(1).\tag{7.17}$$
> For $\ell=d$, the three spin vectors are conditionally independent below $d$. Hence (7.7) and
> $c_d\ge\eta$ give $v_N(S,d)\le\delta/\eta+o_N(1)$ at each fixed $L,d$. This proves
> $V_{1,L}(\eta)\le\delta/\eta$.

### 검증

**계수.** 깊이 $d$ 꼭짓점은 자식 2개: $\gamma=m_d-2m_{d+1}=-(2(d+1)-d)\delta=-(d+2)\delta$. ✓ 경로 2 위 깊이
$\ell\in(d,L)$의 홑자식 꼭짓점: $\gamma=m_\ell-m_{\ell+1}=-\delta$. ✓ 경로 1 쪽이나 깊이 $<d$에서 갈라지면 제약
위반. 합: $1-(d+2)\delta-(L-1-d)\delta=1-(L+1)\delta=-\delta$, Lemma 3.4의 $m_d-1\cdot m_{d+1}=-\delta$와 일치. ✓
$\sum_\ell c_\ell=(d+2)\delta+(L-1-d)\delta=1+\delta$. ✓

**(7.17).** (6.17), $f=X$:
$\mathbb E[X\cdot X]-\sum_\ell c_\ell\mathbb E[XX_\ell]-\mathbb EX\cdot(-\delta)\mathbb EX\to0$
(anchor 혼자: 새 경로 $R_{13}$의 기대값 $=\mathbb EX$). 그러면
$\frac12\sum c_\ell\mathbb E(X-X_\ell)^2=(1+\delta)\mathbb EX^2-\sum c_\ell\mathbb E[XX_\ell]
=\delta\mathbb EX^2-\delta(\mathbb EX)^2+o(1)=\delta\mathrm{Var}X+o(1)$. ✓ ($\mathbb EX_\ell^2=\mathbb EX^2$ 사용.)

**$v_N$ 한계.** $\ell=d$ 항: $X=\sigma^1\cdot\sigma^2$, $X_d=\sigma^1\cdot\sigma^3$, 세 경로는 깊이 $d$ 아래 조건부 독립.
(7.7): $\mathbb E(X-X_d)^2\ge2v_N$. 그리고 모든 항이 음이 아니므로 $\frac12c_d\mathbb E(X-X_d)^2\le\delta+o(1)$,
즉 $v_N\le\delta/c_d+o(1)\le\delta/\eta+o(1)$ ($c_d=(d+2)/L\ge d/L>\eta$). ✓

### 수치 확인 (정확 열거, $L=8$)

| $d$ | 옛 나무 쪽 계수 합 | anchor 혼자 계수 합 | $-\delta$ |
|---|---|---|---|
| 2 | $-1/8$ | $-1/8$ | $-1/8$ |
| 4 | $-1/8$ | $-1/8$ | $-1/8$ |

### 물리적 의미

(7.17)은 GG 항등식의 한 층 버전입니다: "같은 깊이-$d$ 상태에서 뽑은 세 replica의 overlap 차이"의 가중합이
$\delta\cdot\mathrm{Var}$ 이하. 계수 $c_d$가 $\eta$ 이상이므로 **깊이 $d$에서 순수 상태 조건이 $O(\delta)$ 정확도로**
성립합니다. 3.3절의 경고 ("기존 갈라짐 깊이에 목표를 두면 부호 합 $-\delta$, 절댓값 합 $2+\delta$")가 여기서는
문제가 되지 않습니다. 모든 항이 같은 부호의 제곱 ($\mathbb E(X-X_\ell)^2\ge0$)이기 때문입니다.

---

## 문단 4. 이동된 두 복사본 (그림 1)

> *Shifted copies and their coefficients.* Let $|S|=k\ge2$, its first split be $e>d$, and its proper
> child shapes be $T_1,\ldots,T_s$. Sample an old tree consisting of two copies of $S$, denoted I and II,
> whose stems split at $d$ and whose internal depth assignments are aligned. Fix an old leaf in I as
> the spin anchor. Let $S^+$ be the topology $S$ with every internal branching depth increased by one.
> In the prescribed-tree identity require the anchor and the added colors to form two copies of $S^+$,
> separated at $d$, with the anchor in its original labeled position in the first copy. These
> constraints involve only the anchor and the added colors. Add all other colors of side I first, then
> those of side II. Figure 1 illustrates one local shift.
>
> *Figure 1.* One local effect of delaying a target split. The old tree is solid; the dashed child
> creates a split at the previously unary depth-$e+1$ vertex, with coefficient $m_{e+1}-m_{e+2}=-\delta$.
> The proof shifts every internal target depth and charges distinct vertices separately, even when their
> depths coincide. Later target colors may reuse eligible old leaves.

### 해석

| 대상 | 구성 |
|---|---|
| old tree | $S$의 복사본 I, II; 줄기는 깊이 $d$에서 갈라지고 내부 깊이는 정렬 (같은 좌표) |
| anchor | I의 한 잎 (spin anchor) |
| 목표 (target) | anchor + 색 $2k-1$개가 $S^+$ 두 개를 이루고, 둘은 깊이 $d$에서 분리 |
| $S^+$ | $S$의 모든 갈라짐 깊이 $+1$ |
| 색 순서 | 목표 I 쪽 먼저, 그다음 목표 II 쪽 |

**왜 $+1$인가 (그림 1).** 목표 갈라짐이 옛 나무의 갈라짐 깊이 $e$와 같으면 옛 잎 재사용 (계수 1)과 새 경로 (계수
$\approx-1$)가 상쇄하며 절댓값 합이 $O(1)$이 됩니다. $e+1$로 늦추면 그 깊이의 꼭짓점은 옛 나무에서 홑자식이므로
**반드시 새 경로가 그 홑자식 꼭짓점에서 갈라져야** 하고 계수는 $-\delta$입니다. 그러면 절댓값 합과 부호 합이 같은
차수가 되어 (Lemma 3.5), 나중에 $J$로 나누어도 오차가 폭발하지 않습니다.

---

## 문단 5. 정규화 상수 $J$: (7.18)–(7.20)

> Let $\kappa(T)$ be the reference coefficient (3.13), and put
> $$J=\kappa(S^+)^2.\tag{7.18}$$
> At each vertex the $j=1$ factor is $-\delta$; for $j\ge2$ its absolute value is at least $\eta/2$ for
> all sufficiently large $L$. If $b=b(S)$, then
> $$|J|\ge c_{k,\eta}\delta^{2b}>0.\tag{7.19}$$
> For large $L$, regularity ensures that each shifted depth differs from every branching depth of the
> old tree, including $d$. Thus these $2b$ target branching vertices must be created by fresh unary
> splits. Lemma 3.5 gives
> $$\frac1{|J|}\sum_{\text{allowed extensions}}|c|\le C_{k,\eta}.\tag{7.20}$$
> The two copies have aligned depths but distinct branching vertices: each vertex supplies its own
> factor $\delta$. This is the reason for the shift. The full signed coefficient has an additional
> factor $-\delta$ from separation at $d$; we divide by $J$ and leave that factor in the identity.
> Equation (7.20) then controls every projection error after division.

### 검증

- (3.13): $\kappa(S^+)=\prod_v\prod_{j=1}^{a_v-1}(m_{q_v+1}-jm_{q_v+2})$. $j=1$: $m_{q+1}-m_{q+2}=-\delta$.
  $j\ge2$: $|m_{q+1}-jm_{q+2}|=(j-1)m_{q+1}+j\delta\ge m_{q+1}>\eta$ (정칙). 논문의 $\eta/2$는 여유 있는 하한. ✓
  ⇒ $|\kappa(S^+)|\ge\delta^b\eta^{\sum(a_v-2)}$, $|J|\ge c\,\delta^{2b}$. ✓
- 이동된 깊이 $q_v+1$은 옛 갈라짐 깊이 $\{q_w\}\cup\{d\}$ 중 어느 것과도 다름: 정칙 배정에서 서로 다른 깊이는
  $\eta L>1$ 이상 떨어져 있으므로 $q_v+1\ne q_w$ (큰 $L$). ✓ 따라서 목표 갈라짐 $2b$개는 모두 "옛 나무에서 갈라짐이
  아닌 깊이" → Lemma 3.5 (3.15)가 적용되어 $\sum|c|/|J|\le C$. ✓
- 분리 깊이 $d$에서의 인자 $-\delta$: 목표 I과 II를 분리하는 깊이 $d$는 옛 갈라짐 깊이와 **같으므로** 상대 비용
  추정에 포함하지 않고, 항등식 안에 남겨 둡니다 (문단 10의 표에서 $c_\ell$로 나타남).

---

## 문단 6. 두 목표 쪽의 사영 (7.21)

> *Projecting the two target sides.* In every extension, the marginal target tree consists of two
> ordinary copies of $S^+$, independent below their separation at $d$. By (7.13) its multioverlap
> differs in $L^2$ from the contraction of its projected means at $e+1$ by at most $2p_N(S^+,e+1)$.
> Change the proper child depths back by one, then change their evaluation depth from $e+1$ to $e$. The
> product difference inequality and Lemma 7.3 show that this adds an error at most $h_N(S)$ in $L^2$,
> with
> $$\mathcal A_{L,\eta}h_N(S)^2\le C_k/L.\tag{7.21}$$
> One can take $h_N(S)$ to be the sum of the finitely many $L^2(\|\cdot\|_N)$ distances in these
> comparisons, multiplied by a size-dependent constant. This definition depends only on the single-copy
> marginal shapes, not on the particular extension. Thus (7.21) holds uniformly for the comparisons in
> the extension sum, even though the union of the old and target trees itself need not have regular
> depths.

### 해석과 검증

목표 multi-overlap $R_{\rm target}=A_{S^+}^{\rm I}\cdot A_{S^+}^{\rm II}$. 두 쪽을 (7.13)으로 각각 첫 갈라짐 $e+1$에서의
자식 평균의 곱으로 바꾸고 (오차 $2p_N(S^+,e+1)$), 그다음 (a) 자식 내부 깊이를 $-1$ 되돌리기 (7.8), (b) 평가 깊이
$e+1\to e$ (7.9)로 $a_{S,e}$ 꼴의 벡터로 바꿉니다. 각 단계는 곱 차이 부등식 (7.11)로 $L^2$ 오차가 합산되고,
깊이 평균하면 $C/L$. ✓ 중요한 점: 이 비교들은 **목표 쪽의 주변 법칙**(한 복사본의 모양)에만 의존하므로 확장
이력과 무관하고, old+target 합집합이 정칙이 아니어도 됩니다 (사영 일관성). ✓

> (작업 중 — 다음 문단부터 이어짐)
