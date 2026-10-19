# 3.3 Sums of extension coefficients — 문단별 해설

원문: `build/sections/trees.tex` 3.3절, PDF 10–12쪽. 번호는 PDF 기준 (식 (3.12)–(3.15), Lemma 3.4, 3.5).
앞 절 참조: Lemma 3.3 (3.11), (3.7).

6–7장에서 나무 항등식을 쓰려면 확장 계수 $c_E$들의 (i) **부호 있는 합** (항등식의 정규화 상수)과 (ii) **절댓값 합** (오차의
크기)을 알아야 합니다. 이 절이 그 둘을 계산합니다. 수치 확인은 모두 확장 이력의 정확한 유리수 열거입니다.

---

## 문단 1. 도입과 reference path

> We now control the signed normalization and the accumulated error in the prescribed-tree identities used
> for the lower bound.
>
> In an extension history, the anchor and the already colored paths are called reference paths. Constraints
> on the new color will only specify its splitting depths with these paths. In particular, a constraint does
> not distinguish unused old paths with the same specified ancestry.

### 해석

reference path = anchor + 이미 색을 받은 잎. 제약은 "새 색이 reference path들과 어느 깊이에서 갈라지는가"만 지정하고,
아직 안 쓴 옛 잎들 사이를 구분하지 않습니다. 이 성질 때문에 계수 합이 **옛 나무와 무관**해집니다 (Lemma 3.4).

---

## 문단 2. 제어해야 할 상쇄 — 핵심 예

> To see the cancellation that must be controlled, start with two old paths splitting at depth $d$, and let
> the first be the anchor. Require one added color to split from the anchor exactly at $d$. It may use the
> second old leaf, create a fresh path at the depth-$d$ vertex, or follow the second old path and leave it at
> a depth $\ell>d$. The respective coefficients give the total
> $$1+(m_d-2m_{d+1})+\sum_{\ell=d+1}^{L-1}(m_\ell-m_{\ell+1})=m_d-m_{d+1}.$$
> On the uniform mesh $m_d=d/L$, with $\delta=L^{-1}$, this signed total is $-\delta$, but the sum of absolute
> coefficients is $2+\delta$. If instead the required split is delayed to $d+1<L$, the only allowed choice is
> a fresh split at the unary depth-$(d+1)$ vertex on the anchor path. Its coefficient is $-\delta$, so the
> absolute sum is now $\delta$. The next two lemmas extend these two calculations: the first computes signed
> totals, and the second controls absolute sums when specified splits occur away from old branching depths.

### 검증

합: $1+m_d-2m_{d+1}+(m_{d+1}-m_L)=1+m_d-m_{d+1}-1=m_d-m_{d+1}$. ✓ 균등 격자에서 $-\delta$.
절댓값: $1+(d+2)\delta+(L-1-d)\delta=1+(L+1)\delta=2+\delta$. ✓
늦춘 경우: anchor 경로의 깊이 $d+1$ 홑자식 꼭짓점에서 새로 갈라지는 것만 허용 (옛 잎 $b$는 anchor와 $d$에서 갈라지므로 불가). ✓

### 수치 확인 ($L=8$)

| $d$ | 목표 깊이 $d$: 부호 합 / 절댓값 합 | 목표 $d+1$: 부호 합 / 절댓값 합 |
|---|---|---|
| 2 | $-1/8$ / $17/8$ | $-1/8$ / $1/8$ |
| 5 | $-1/8$ / $17/8$ | $-1/8$ / $1/8$ |

$17/8=2+\delta$ ✓, $1/8=\delta$ ✓.

### 물리적 의미 — 왜 이것이 문제인가

항등식은 "부호 합으로 나눈" 형태로 쓰입니다. 부호 합이 $-\delta$인데 절댓값 합이 $2+\delta$이면, 나눈 뒤 오차가 $(2+\delta)/\delta\sim2L$배로
불어납니다 (요약의 "비율 $2L+1$"). 옛 replica와 **같은 깊이**에서 갈라지라고 요구하면 "옛 replica 재사용" (+1)과 "새 replica
생성" (−1 근처)이 거의 상쇄되기 때문입니다. 깊이를 한 칸 늦추면 상쇄가 사라지고 두 합이 같은 차수가 됩니다 — 7.3절 귀납의
열쇠 (그림 1).

---

## 문단 3. Lemma 3.4 (Reference-path totals)

> **Lemma 3.4.** Suppose the next color must follow a specified reference prefix to depth $d$ and then enter a
> child distinct from all $j\geq1$ children there that contain reference paths. Apart from these ancestry
> constraints its continuation is unrestricted. The sum of the coefficients of all allowed choices is
> $$m_d-jm_{d+1}.\tag{3.12}$$
> Consequently, if the anchor and the colors must have a prescribed tree $S$, the total coefficient over all
> compatible extensions of any old tree is
> $$\kappa(S)=\prod_{v\in\mathrm{Br}(S)}\prod_{j=1}^{a_v-1}(m_{d_v}-jm_{d_v+1}),\tag{3.13}$$
> where $a_v$ and $d_v$ are the child count and depth of each branching vertex in the prescribed reference
> tree. More generally, the same one-step rule can be iterated starting from any already constructed set of
> references.

### 해석

- 한 걸음: 새 색이 reference 접두부를 깊이 $d$까지 따라간 뒤, reference를 담은 $j$개 자식이 아닌 곳으로 들어가야 함 →
  허용 선택의 계수 합 $=m_d-jm_{d+1}$. **옛 나무의 모양과 무관.**
- 전체: 목표 모양 $S$의 갈라짐 꼭짓점 $v$ (자식 $a_v$개, 깊이 $d_v$)마다, 그 꼭짓점의 자식 묶음에 처음 들어가는 색들이 차례로
  $j=1,\dots,a_v-1$을 만남 ⇒ $\kappa(S)$.

### 증명과 검증

> *Proof.* At the specified divergence vertex, let $n$ be the child count in the entire current tree. The $j$
> excluded children contain all references passing through that vertex. Each of the other $n-j$ children
> roots a subtree containing no reference. Its terminal vertices are therefore unused old leaves. If such a
> subtree is rooted at depth $d+1$, its permitted choices are an old leaf, with coefficient $1$, or a fresh
> divergence at an internal vertex in the subtree. If it has $q$ leaves, telescoping within it gives
> $$q+\sum_{\beta\text{ internal in the subtree}}(m_{d_\beta}-n_\beta m_{d_\beta+1})=m_{d+1}.$$
> The formula includes the case of a terminal child, when both sides are $1$. Adding these contributions to
> the fresh choice at the specified vertex gives $m_d-nm_{d+1}+(n-j)m_{d+1}=m_d-jm_{d+1}$.
>
> For consistent prescribed splitting depths with all reference paths, the deepest required common prefix
> determines the divergence vertex and its excluded reference children. Thus the one-step sum depends only on
> the current reference tree, not on which old paths or fresh paths realized it. Sum backwards over
> successive choices. At a branching vertex of the final prescribed tree, the numbers of excluded reference
> children when new child groups are first entered are exactly $1,\ldots,a_v-1$. Their factors give (3.13),
> independently of the color order.

- 부분 나무 텔레스코핑: (3.7)을 깊이 $d+1$에서 시작하는 부분 나무에 적용하면 $\sum(n_\beta m_{d_\beta+1}-m_{d_\beta})=q-m_{d+1}$
  ⇒ $q+\sum\gamma_\beta=m_{d+1}$. ✓ (잎 하나뿐인 자식이면 $1=1$.)
- 합: 갈라짐 꼭짓점에서 새로 ($m_d-nm_{d+1}$) + reference 없는 자식 $n-j$개 각각 $m_{d+1}$ ⇒ $m_d-jm_{d+1}$. ✓
- 마지막 단락: 한 걸음 합이 reference 나무에만 의존하므로 뒤에서부터 합하면 곱이 됩니다 (분배 법칙). ✓

### 수치 확인

| 확인 | 결과 |
|---|---|
| 무작위 old tree 3개 ($L=7$, 잎 3), 목표: anchor + 색 2개가 깊이 3에서 3갈래 별 | 세 경우 모두 합 $5/49$ |
| $\kappa(S)=(m_3-m_4)(m_3-2m_4)=(-\tfrac17)(-\tfrac57)$ | $5/49$ ✓ |
| 6.5–7장에서 쓴 경우들 (한 잎 $-\delta$, 두 복사본 표, marker 계수) | 7.3절, 7.4절에서 모두 일치 확인 |

### 물리적 의미

$\kappa(S)$는 Ruelle cascade에서 "$|S|$개의 replica가 정확히 모양 $S$로 상태를 공유할 확률"과 부호·계승을 빼면 같은 양입니다
(요약의 관찰: $\kappa(S)=(-1)^kk!\,Q_{k+1}(S)$). $j=1$ 인자 $m_d-m_{d+1}$은 작고 ($-\delta$), $j\ge2$ 인자 $m_d-jm_{d+1}\approx-(j-1)m_d$는
1차 크기입니다. 즉 **새 갈라짐 꼭짓점을 만드는 것은 비싸고, 이미 있는 갈라짐에 가지를 더하는 것은 싸다** (3.4절 문단 3에서 다시 다룸).

---

## 문단 4. 절댓값 합이 필요한 이유

> To control errors after division by a small reference coefficient, we also need an absolute bound. Moving a
> target branching depth away from all old branching depths forces a fresh unary split. The next estimate
> charges one small factor to each such vertex.

---

## 문단 5. Lemma 3.5 (Charging fresh splits)

> **Lemma 3.5.** Assume $m_d=d/L$ and put $\delta=L^{-1}$. Start with an old tree having $q$ leaves and assign
> $k$ colors by the canceled-anchor extension rule. Prescribe the reference shape of the anchor and the
> colors, possibly with additional restrictions on allowed extensions. Suppose $b$ specified branching
> vertices of that shape have depths which are not branching depths anywhere in the old tree. Then
> $$\sum_{E\text{ allowed}}|c_E|\leq C_{q,k}\delta^b.\tag{3.14}$$
> The constant is independent of $L$, the prescribed depths, and their coincidences at different vertices.
> In particular, for these $b$ vertices let $J=\prod_v\prod_{j=1}^{a_v-1}(m_{d_v}-jm_{d_v+1})$. If
> $m_{d_v}\geq\eta>0$ at all of them, then $J\ne0$ and
> $$\frac{1}{|J|}\sum_{E\text{ allowed}}|c_E|\leq C_{q,k,\eta}.\tag{3.15}$$

### 증명 요지와 검증

> *Proof (요약 인용).* If the current tree has $s$ leaves, (3.7) says that the total absolute coefficient of
> all fresh choices is $s$. There are at most $s$ eligible old choices. Hence the total absolute coefficient
> at an unrestricted step is at most $2s\leq2(q+k)$. At any fixed depth there are at most $s$ vertices.
> Restricting a step to fresh divergences at unary vertices of a prescribed depth therefore gives total
> absolute coefficient at most $s\delta$ … Distinct target vertices become branching at distinct steps … There
> are at most $k!/(k-b)!$ possible assignments … Iterated summation over choices gives at most
> $\frac{k!}{(k-b)!}(q+k)^b(2(q+k))^{k-b}\delta^b$. … For the final assertion, the $j=1$ factor at each designated
> vertex has absolute value $\delta$, whereas for $j\geq2$, $|m_d-jm_{d+1}|=(j-1)m_d+j\delta\geq\eta$. … Thus
> $|J|\geq\delta^b\eta^{\sum_v(a_v-2)}$, and the result follows.

- 한 걸음의 절댓값 합: 새 경로 계수의 절댓값 합 $=s$ ((3.7)), 옛 잎 $\le s$개 ⇒ $\le2s$. ✓
- 목표 꼭짓점은 옛 나무에서 갈라짐이 아니므로, 그것이 갈라짐이 되는 순간은 **홑자식 꼭짓점에서 새 경로가 갈라질 때**뿐이고
  계수는 $-\delta$, 그 깊이의 꼭짓점은 $\le s$개 ⇒ 그 걸음의 절댓값 합 $\le s\delta$. ✓
- 서로 다른 목표 꼭짓점은 서로 다른 걸음에서 생김 (새 경로 하나는 갈라짐 꼭짓점 하나만 만듦) ⇒ 걸음 배정 $\le k!/(k-b)!$가지. ✓
- $J$의 하한: $j=1$ 인자 $\delta$, $j\ge2$ 인자 $\ge\eta$ ⇒ $|J|\ge\delta^b\eta^{\sum(a_v-2)}$ ⇒ (3.15). ✓

### 수치 확인 (늦춘 목표의 절댓값 합)

old tree = 깊이 $d=L/4$에서 갈라지는 잎 2개, 목표 = anchor와 색 하나가 깊이 $d+1$에서 갈라짐 ($b=1$):

| $L$ | 8 | 16 | 32 |
|---|---|---|---|
| $\sum\lvert c_E\rvert$ | 0.125 | 0.0625 | 0.03125 |
| $\sum\lvert c_E\rvert/\delta$ | 1.000 | 1.000 | 1.000 |

$\delta^b$ 스케일 ✓, 상대 비용 $\sum|c|/|J|=1$ ($J=-\delta$) ✓.

### 물리적 의미

"새 상태를 만드는 데는 $\delta$ (상태 하나의 무게 $\sim1/L$)가 든다." 목표 모양의 새 갈라짐마다 $\delta$를 하나씩 청구하면, 부호
합 $J$와 절댓값 합이 같은 $\delta^b$ 차수가 되어 나눗셈이 안전해집니다. 다중 분기 ($a_v\ge3$)는 추가로 $\eta$만 들 뿐 $\delta$는
더 들지 않습니다.

---

## 요약

- 같은 깊이에서 갈라지라는 목표는 부호 합 $-\delta$, 절댓값 합 $2+\delta$ — 나눗셈에 위험. 한 칸 늦추면 둘 다 $\delta$.
- Lemma 3.4: 한 걸음 합 $m_d-jm_{d+1}$, 모양 $S$ 전체 합 $\kappa(S)$, 옛 나무와 무관 (무작위 old tree로 확인).
- Lemma 3.5: 옛 갈라짐 깊이가 아닌 목표 꼭짓점 $b$개 ⇒ 절댓값 합 $\le C\delta^b$, $|J|$ 대비 상대 비용 유계 ($\delta^b$ 스케일 확인).

**다음 절 예고**: 3.4절에서 $Q_k$ 아래 갈라짐 깊이의 분포 — 정칙(regular) 모양과 Lemma 3.6 — 를 다룹니다.
