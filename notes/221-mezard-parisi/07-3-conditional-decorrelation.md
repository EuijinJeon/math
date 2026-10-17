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

---

## 문단 7. 옛 줄기의 사영 벡터 $a$, $b$

> Let $a,b$ denote the vectors $a_{S,e}$ on the old stems I and II. The target stem in I shares the old
> prefix through $e$ because it contains the anchor, so its final projected vector is $a$.

### 해석

$a=\prod_j\mu_{e,T_j}$를 옛 I 줄기의 깊이-$e$ 접두부에서, $b$를 옛 II 줄기에서 계산한 것. 목표 I은 anchor를 포함하고
그 첫 갈라짐이 $e+1>e$이므로 깊이 $e$까지 anchor의 (= 옛 I의) 접두부를 따릅니다 → 사영 벡터가 정확히 $a$. ✓

---

## 문단 8. 부호 있는 확장 합: 목표 II 첫 경로의 분류

> *The signed extension sum.* Set $f$ to be the overlap of all $2k$ old leaves, an allowed fixed overlap
> monomial. All target-I additions stay in the anchor's branch below $d$, so they leave the old-II stem
> and its child counts unchanged. Classify the first added path of target side II by its prefix through
> $e$. It may diverge freshly at $\ell=d$, with coefficient $-c_d$, or follow the old II stem and
> diverge at $d<\ell<e$, with coefficient $-c_\ell=-\delta$. In such a class let $b_\ell$ be $a_{S,e}$ on
> the new stem; it shares the old II prefix through $\ell$. At $\ell=d$ the stems carrying $a,b,b_d$ are
> conditionally independent below $d$. Every remaining possibility follows the old II prefix through $e$
> and has final projected vector $b$. All later target paths in side II follow its first path through
> $e$, since their earliest split is $e+1$.

### 해석

- 시험 함수 $f$ = 옛 잎 $2k$개 전체의 multi-overlap $=A_S^{\rm I}\cdot A_S^{\rm II}$. 사영하면 $\approx a\cdot b$.
- 목표 II의 첫 경로는 anchor와 깊이 $d$에서 갈라져야 하므로 깊이 $d$ 꼭짓점에서 I이 아닌 쪽으로 갑니다. 선택지:
  1. 깊이 $d$ 꼭짓점에서 새로 (계수 $m_d-2m_{d+1}=-c_d$): 새 줄기 → 사영 벡터 $b_d$, 줄기 $a,b,b_d$는 $d$ 아래 독립.
  2. 옛 II 줄기를 따라가다 $d<\ell<e$의 홑자식 꼭짓점에서 새로 (계수 $-\delta$) → $b_\ell$ (II와 $\ell$까지 접두부 공유).
  3. 옛 II의 깊이-$e$ 접두부까지 따라감 (옛 II 잎 재사용, 또는 $\ge e$에서 새 경로) → 사영 벡터 $b$.
- 목표 II의 나머지 경로는 첫 경로와 $e+1$에서야 갈라지므로 깊이 $e$까지 첫 경로를 따릅니다. ✓

---

## 문단 9. 분류 안에서 결합 법칙이 고정됨

> For a fixed extension history, retain every old path and the first target-II prefix through $e$, and
> delete all other new branches. The target-I projection $a$ already depends only on the retained old
> anchor prefix. Each deleted subtree integrates to one under its probability kernels; a reused old leaf
> introduces no new variable. The retained tree depends only on the class: it is the old tree with a
> fresh stem attached at $\ell<e$, or just the old tree in the remaining class. The history is a
> combinatorial choice, not a condition on sampled values. Thus the joint marginal of the old paths and
> projected prefixes is fixed within each class. In particular, the expectation of $f$ times the
> projected overlap is constant within a class and can be multiplied by its total signed coefficient.

### 해석

사영된 항 $\mathbb E[f\cdot(a\cdot b_\ell)]$는 옛 경로들과 목표 II 첫 경로의 깊이-$e$ 접두부만 씁니다. 나머지 새 가지는
확률 커널로 적분하면 1 (사영 일관성). 그러므로 같은 분류의 모든 이력은 **같은 기대값**을 주고, 분류별 계수 합만
알면 됩니다. "이력은 표본 값에 대한 조건이 아니라 조합적 선택"이라는 문장은, 이력별로 나무 모양만 다르고 그 위의
표본 법칙은 미리 정해진 나무 표본 규칙을 따른다는 뜻입니다. ✓

---

## 문단 10. 계수 표

> By Lemma 3.4, summing later side-II colors backwards gives $\kappa(S^+)$ for each first-path choice.
> Summing the side-I choices gives the other factor $\kappa(S^+)$. The fresh class at $\ell$ therefore
> has total coefficient $-c_\ell J$. The total coefficient is $-\delta J$, both from the old tree and from
> the anchor alone. Since $\sum_{\ell=d}^{e-1}c_\ell=(e+1)\delta=m_e+\delta$, the remaining
> prefix-through-$e$ class has coefficient $m_eJ$. Thus the projected terms have the following
> coefficients:
>
> | side-II prefix | projected overlap | total coefficient |
> |---|---|---|
> | fresh divergence at $d\le\ell<e$ | $a\cdot b_\ell$ | $-c_\ell J$ |
> | old prefix through $e$ | $a\cdot b$ | $m_eJ$ |

### 검증

- Lemma 3.4: 기준 경로 집합이 정해지면 다음 색의 허용 선택 합 $=m_d-jm_{d+1}$, 옛 나무와 무관. 목표 I 색들의
  합 $\to\kappa(S^+)$, 목표 II 첫 경로 이후 색들의 합 $\to\kappa(S^+)$. ✓
- 전체: 기준 모양 = 깊이 $d$에서 자식 2 + 각 쪽 $S^+$ ⇒ $\kappa=(m_d-m_{d+1})\kappa(S^+)^2=-\delta J$. ✓
- $\sum_{\ell=d}^{e-1}c_\ell=(d+2)\delta+(e-1-d)\delta=(e+1)\delta$. ✓ 남은 분류: $-\delta J+(e+1)\delta J=e\delta J=m_eJ$. ✓

### 수치 확인 (정확 열거)

$L=8$, $S$ = 체리 (잎 2개, 갈라짐 $e=5$), 두 복사본의 줄기 갈라짐 $d=2$. 옛 잎 4개, anchor = I의 잎 하나,
색 3개 (목표 I 1개, 목표 II 2개), 제약: $\mathrm{split}(a_*,c_1)=\mathrm{split}(c_2,c_3)=e+1=6$, 양쪽 사이 $=d=2$.
$J=\kappa(S^+)^2=\delta^2=1/64$.

| 목표 II 첫 경로의 접두부 | 열거한 계수 합 | $J$ 단위 | 논문 예측 |
|---|---|---|---|
| 깊이 $\ell=2$에서 새로 | $-1/128$ | $-\tfrac12J$ | $-c_d=-(d+2)\delta=-\tfrac12$ ✓ |
| $\ell=3$에서 새로 | $-1/512$ | $-\tfrac18J$ | $-\delta$ ✓ |
| $\ell=4$에서 새로 | $-1/512$ | $-\tfrac18J$ | $-\delta$ ✓ |
| 옛 II 접두부를 $e$까지 | $5/512$ | $\tfrac58J$ | $m_e=5/8$ ✓ |
| 전체 | $-1/512$ | $-\tfrac18J$ | $-\delta J$ ✓ |
| anchor 혼자 (전체) | $-1/512$ | | $-\delta J$ ✓ |

---

## 문단 11. 사영된 항등식 (7.22), (7.23)

> Multiply the projected overlap in each row by $f$ and divide the prescribed-tree identity by $J$.
> Rearranging gives
> $$\sum_{\ell=d}^{e-1}c_\ell\mathbb E\bigl[f(a\cdot b-a\cdot b_\ell)\bigr]=\delta\bigl(\mathbb E[f(a\cdot b)]-\mathbb Ef\,\mathbb ER_{\mathrm{target}}\bigr)+\rho_N(S,d),\tag{7.22}$$
> where $R_{\mathrm{target}}$ on the right is the target overlap in the anchor-alone extension. Its
> absolute value is at most one. The error satisfies
> $$|\rho_N(S,d)|\le C_{k,\eta}\bigl(p_N(S^+,e+1)+h_N(S)\bigr)+C_{L,k,\eta}\varepsilon_{N,L,k}.\tag{7.23}$$
> Indeed, multiplying a projection error by $f$, even when correlated with it, costs at most its $L^2$
> norm since $|f|\le1$. Sum these errors with absolute coefficients and apply (7.20). The final term
> includes division of the original identity error by $J$ and tends to zero at fixed $L$.

### 검증

(6.17)을 $J$로 나누고 표를 대입:
$$-\sum_\ell c_\ell\mathbb E[f\,a\cdot b_\ell]+m_e\mathbb E[f\,a\cdot b]+\delta\,\mathbb Ef\,\mathbb ER_{\rm target}=\text{오차}.$$
$m_e=\sum_\ell c_\ell-\delta$를 쓰면 $\sum_\ell c_\ell\mathbb E[f(a\cdot b-a\cdot b_\ell)]-\delta\mathbb E[f\,a\cdot b]+\delta\mathbb Ef\,\mathbb ER_{\rm target}$
$=$ 오차 ⇒ (7.22). ✓ 오차: (i) 사영 오차 ($L^2$에서 $2p_N(S^+,e+1)+h_N$)에 $|f|\le1$을 곱하고 절댓값 계수로 합해
$J$로 나눔 → (7.20)로 $C_{k,\eta}$배; (ii) (6.17) 자체의 오차 $\varepsilon_{N,L,k}$를 $|J|\ge c\delta^{2b}$로 나눔 →
$L$-의존 상수. ✓

---

## 문단 12. 귀납 닫기: (7.24), (7.25)

> *Closing the induction.* Equation (7.13) gives $\|f-a\cdot b\|_{L^2}\le2p_N(S,e)$. Moreover
> $\sum_{\ell=d}^{e-1}c_\ell=(e+1)\delta\le1$. Replacing $f$ by $a\cdot b$ on the left of (7.22) therefore
> costs at most $4p_N(S,e)$. Each $a\cdot b_\ell$ has the same marginal law as $a\cdot b$, so that left
> side becomes $\frac12\sum_{\ell=d}^{e-1}c_\ell\mathbb E(a\cdot b-a\cdot b_\ell)^2$. Its summands are
> nonnegative and $c_d\ge\eta$. The right side of (7.22) is bounded in absolute value by
> $2\delta+|\rho_N(S,d)|$. Hence
> $$\mathbb E(a\cdot b-a\cdot b_d)^2\le C_\eta\bigl(\delta+p_N(S,e)+|\rho_N(S,d)|\bigr).\tag{7.24}$$
> Sample three copies of $A_S$ conditionally independently below $d$. Projecting each of the two
> contractions involving the first copy changes it in $L^2$ by at most $2p_N(S,e)$. Using (7.7), (7.24),
> and $p_N(S,e)\le k$, we obtain
> $$v_N(S,d)\le C_{k,\eta}\bigl(\delta+p_N(S,e)+p_N(S^+,e+1)+h_N(S)\bigr)+C_{L,k,\eta}\varepsilon_{N,L,k}.\tag{7.25}$$

### 검증

- $f=A^{\rm I}_S\cdot A^{\rm II}_S$, 두 쪽을 사영 (7.13) ⇒ $\|f-a\cdot b\|_{L^2}\le2p_N(S,e)$. ✓
  $|a\cdot b-a\cdot b_\ell|\le2$, $\sum c_\ell\le1$ ⇒ 교체 비용 $\le2\cdot2p_N=4p_N$. ✓
- $a\cdot b$와 $a\cdot b_\ell$은 같은 주변 법칙 (b와 $b_\ell$은 $a$에 대해 대칭적 위치) ⇒
  $\mathbb E[(a\cdot b)(a\cdot b-a\cdot b_\ell)]=\frac12\mathbb E(a\cdot b-a\cdot b_\ell)^2$. ✓
- 우변 $|\delta(\cdots)|\le2\delta$. $c_d\ge\eta$로 $\ell=d$ 항만 남기면 (7.24). ✓
- 세 복사본: $X,Y,Z$ = 깊이 $d$ 아래 조건부 독립인 $A_S$ 세 개. $X\cdot Y-X\cdot Z$를 사영하면 $a\cdot b-a\cdot b_d$
  ($L^2$ 오차 $\le4p_N$). (7.7): $2v_N\le\mathbb E(X\cdot Y-X\cdot Z)^2\le2\mathbb E(a\cdot b-a\cdot b_d)^2+2(4p_N)^2$.
  $p_N^2\le kp_N$로 1차로 합침. ✓ (7.23)을 대입하면 (7.25). ✓

### 물리적 의미

$v_N(S,d)$ (깊이 $d$ 상태 안의 clustering 결여)가 (i) $\delta$ (격자 간격), (ii) 자식 모양들의 clustering 결여
$p_N$, (iii) 깊이 이동 비용 $h_N$, (iv) 항등식 오차로 제어됩니다. 물리적으로: **"하위 묶음이 순수하면 상위
묶음도 순수하다"**. 6장의 GG형 항등식이 이 상속을 가능하게 합니다.

---

## 문단 13. 깊이 평균과 점화식: (7.26), (7.27)

> Each child in either $p_N$ has fewer than $k$ leaves. To make the averaging step explicit, the aligned
> construction has $D=b(S)+1$ distinct depth coordinates, including $d$ and $e$. A term belonging to
> $T_j$ uses only $D_j=b(T_j)+1$ coordinates. For the shifted term these are
> $\pi_j(\mathbf q)=(e+1,(q_v+1)_{v\in\mathrm{Br}(T_j)})$. Every retained assignment has at most
> $L^{D-D_j}$ preimages, and its coordinates are $\eta/2$-regular for large $L$. If $w_j$ is the child
> covariance as a function of these coordinates, then, for $0<\gamma\le1$,
> $$L^{-D}\sum_{\mathbf q\;\eta\text{-regular}}w_j(\pi_j(\mathbf q))^\gamma\le L^{-D_j}\sum_{\mathbf y\;\eta/2\text{-regular}}w_j(\mathbf y)^\gamma\le\left(L^{-D_j}\sum_{\mathbf y\;\eta/2\text{-regular}}w_j(\mathbf y)\right)^\gamma.\tag{7.26}$$
> The unshifted term has the same bound without translating the coordinates. Thus the two aligned
> copies use single-copy estimates; there is no restriction of an independently averaged pair of copies
> to a diagonal. Taking $\gamma=1/4$ and then $\limsup_N$, and using (7.21) and (7.3), gives, for
> sufficiently large $L$,
> $$V_{k,L}(\eta)\le C_{k,\eta}\left(L^{-1/2}+V_{k-1,L}(\eta/2)^{1/4}\right).\tag{7.27}$$
> The maximum over smaller topologies in (7.15) can be absorbed in the right side because these
> covariances are bounded by one. The base case and induction now imply $V_{k,L}(\eta)\to0$ for every
> fixed $k,\eta$, proving the proposition.

### 검증

- 좌표: $S$의 갈라짐 $b(S)$개 + $d$ = $D$. ($e$는 $S$의 첫 갈라짐이므로 $b(S)$에 포함.) ✓ 자식 $T_j$의 공분산 항
  $v_N(T_j,e)$는 $T_j$의 갈라짐과 평가 깊이 $e$만 씀: $D_j=b(T_j)+1$. ✓
- 섬유 (fiber) 크기 $\le L^{D-D_j}$ ⇒ 첫 부등식; 이동된 좌표는 $\eta/2$-정칙 (7.1절). ✓ 둘째 부등식은 (7.2). ✓
- (7.25)를 평균: $\mathcal A\delta=O(L^{-1})$; $p_N=\sum_jv_N^{1/4}$ → $\gamma=1/4$로 $V_{k-1}(\eta/2)^{1/4}$;
  $h_N\le$: $\mathcal Ah_N\le(\mathcal Ah_N^2)^{1/2}\le(C/L)^{1/2}$ (7.21) → $L^{-1/2}$; $\varepsilon\to0$ (7.3). ✓
- 귀납: $V_{1,L}(\eta)\le1/(\eta L)\to0$; $V_{k,L}(\eta)\le C(L^{-1/2}+V_{k-1,L}(\eta/2)^{1/4})\to0$. ✓

**판단 메모 — 수렴 속도.** 점화식이 매 단계 4제곱근을 취하므로 $V_k$는 대략 $L^{-4^{-(k-1)}}$ 속도로만 줄어듭니다.
$C=1$, $\eta=0.1$로 점화식을 (등호로) 돌리면:

| $L$ | $V_1$ | $V_2$ | $V_3$ | $V_4$ |
|---|---|---|---|---|
| $10^2$ | 0.1 | 0.66 | 1.0 | 1.1 |
| $10^4$ | $10^{-3}$ | 0.19 | 0.67 | 0.91 |
| $10^8$ | $10^{-7}$ | 0.018 | 0.37 | 0.78 |
| $10^{16}$ | $10^{-15}$ | $1.8\times10^{-4}$ | 0.12 | 0.58 |

정량적으로는 매우 느리지만, 정리는 정성적 극한 ($L\to\infty$)만 주장하므로 문제가 없습니다.

---

## 요약

- 명제 7.4: $\lim_L\limsup_N\mathcal A_{L,\eta}v_N(S,d)=0$, 잎 수 귀납.
- 기저 (7.17): 한 층 GG 항등식 $\frac12\sum c_\ell\mathbb E(X-X_\ell)^2=\delta\mathrm{Var}X+o(1)$ ⇒ $v_N\le\delta/\eta$.
- 귀납: 두 복사본에 목표 $S^+$ (깊이 $+1$)를 요구해 상대 절댓값 비용을 $J=\kappa(S^+)^2$로 제어 (7.20),
  목표 II 첫 경로로 분류한 계수 표 ($-c_\ell J$, $m_eJ$, 합 $-\delta J$), 사영된 항등식 (7.22), 세 복사본 부등식으로
  (7.25), 깊이 평균 (7.26)으로 점화식 (7.27).
- 한 잎 계수 합, 계수 표 전체, 합 $-\delta J$를 정확한 유리수 열거로 확인했습니다.

**다음 절 예고**: 7.4절에서 marker anchor로 접두부 사영을 집중시키고 (7.28)–(7.30), 명제 7.4와 합쳐 정리 7.1
(모든 multi-overlap의 집중)을 완성합니다.
