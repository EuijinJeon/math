# 3.4 The distribution of branching depths — 문단별 해설

원문: `build/sections/trees.tex` 3.4절, PDF 12–13쪽. 번호는 PDF 기준 (식 (3.16), (3.17), Lemma 3.6, Remark 3.7).
앞 절 참조: (3.8) $Q_k$, Lemma 3.5. 이 절의 결과는 7.1절 ($\eta$-정칙)과 8.2절 ((8.5))에서 쓰입니다.

수치 확인은 $Q_k$ 아래 모든 나무를 확률과 함께 정확히 열거해 계산했습니다.

---

## 문단 1. 모양, 좌표, 정칙성

> Still take $m_d=d/L$. Suppress unary stretches only for the purpose of describing a shape by a finite
> topology and its branching-depth coordinates. For $0<\eta<1/2$, call a shape *regular* if every branching
> depth divided by $L$ lies in $(\eta,1-\eta)$ and any two distinct branching vertices have normalized depths
> differing by more than $\eta$. A singleton is regular. This is the regularity used when sampling a single
> tree; later we also use two copies whose corresponding depth assignments are deliberately aligned.

### 해석

- 모양 = 위상 (홑자식 부분을 접은 나무) + 갈라짐 꼭짓점마다 깊이 좌표 하나.
- **정칙(regular)**의 두 조건:
  1. 모든 갈라짐 깊이 $d_v/L\in(\eta,1-\eta)$ — 뿌리 근처나 잎 근처가 아님.
  2. **서로 다른** 갈라짐 꼭짓점의 정규화 깊이 차이 $>\eta$ — 서로 다른 꼭짓점이 비슷한 깊이에 몰리지 않음.
- 꼭짓점 하나의 자식 수 $a_v$에는 **제한이 없습니다**. 3갈래, 4갈래 꼭짓점도 좌표가 하나인 갈라짐 꼭짓점 하나일 뿐입니다
  (아래 문단 3에서 자세히).

### 물리적 의미

정칙 = 위계의 각 갈라짐이 Parisi 변수 $x=d/L$의 "내부"에 있고, 서로 다른 층이 구별될 만큼 떨어져 있음. 7장의 증명은 갈라짐 깊이를
한 칸 옮기는 조작을 하므로, 옮긴 깊이가 다른 갈라짐과 부딪히지 않도록 여유 $\eta$가 필요합니다.

---

## 문단 2. Lemma 3.6 (Regular shapes)

> **Lemma 3.6.** For every fixed $k$ there is $C_k<\infty$, independent of $L$ and $\eta$, such that
> $$Q_k\{\mathcal T\text{ is not regular}\}\leq C_k(\eta+L^{-1}).\tag{3.16}$$
> For any particular labeled topology with $a$ branching vertices and any consistent assignment of their
> depths,
> $$Q_k\{\text{that topology and depth assignment}\}\leq C_kL^{-a}.\tag{3.17}$$
> Deleting leaves from a regular tree produces a regular tree, after discarding branching vertices that
> become unary.

> *Proof.* Suppose the current tree has $n$ leaves. A new branching vertex is created exactly when the next
> path diverges at a unary vertex. Each such choice has probability $\delta/n$ by (3.8). At any depth there
> are at most $n$ vertices; hence for a set $B$ of depths the probability that the next path creates a
> branching vertex at a depth in $B$ is at most $|B|\delta$. At each of the first $k-1$ steps, the boundary
> depths and the depths within normalized distance $\eta$ of any previous branching vertex form a set of
> cardinality at most $C_k(\eta L+1)$. If none of these forbidden creation events occurs, the final tree is
> regular. A union bound proves (3.16). Divergence at an already branching vertex does not create a new
> coordinate and requires no extra exclusion.
>
> For (3.17), restrict a specified final labeled tree to leaves $1,\ldots,n$, retaining every unary stretch.
> These restrictions determine its successive histories under (3.8). Each of its $a$ branching vertices is
> first created by a unary divergence, whose probability is at most $\delta$; every other transition
> probability is at most $1$. The probability of the specified history is therefore at most $\delta^a$. If a
> topology description identifies equivalent child orderings, their number is bounded in terms of $k$ alone,
> which gives the stated version with $C_k$. Finally, a retained branching vertex after deletion was already a
> branching vertex of the original tree, at the same depth. Its depth coordinates are a subset of the old
> ones, so regularity is preserved.

### 검증

- 홑자식 꼭짓점 (깊이 $d$, $n_\beta=1$)에서 갈라질 확률: $(1\cdot m_{d+1}-m_d)/n=\delta/n$. ✓
- 깊이 집합 $B$에서 새 갈라짐 생성: 깊이마다 꼭짓점 $\le n$개 ⇒ $\le|B|\cdot n\cdot\delta/n=|B|\delta$. ✓
- 금지 깊이: 경계 $\lfloor\eta L\rfloor+1$개씩 양쪽 + 기존 갈라짐 (최대 $k-1$개) 주변 $2\eta L+1$개씩 ⇒ $C_k(\eta L+1)$. 확률
  $\le C_k(\eta L+1)\delta=C_k(\eta+1/L)$, $k-1$걸음 합집합. ✓
- 이미 갈라진 꼭짓점에 붙는 것은 새 좌표를 만들지 않으므로 금지할 필요가 없습니다. ✓
- (3.17): 지정된 나무의 생성 이력이 (잎 번호로) 정해지고, 갈라짐 꼭짓점 $a$개는 각자 확률 $\le\delta$인 걸음에서 생김. ✓
- 지우기: 남은 갈라짐 꼭짓점은 원래 갈라짐 꼭짓점이고 깊이도 같음 ⇒ 좌표가 부분집합 ⇒ 정칙 유지. ✓

### 수치 확인

**(3.16)**: $Q_k$ 아래 비정칙 확률 (정확 계산).

| $k$ | $L$ | $\eta=0.05$ | $\eta=0.1$ | $\eta=0.2$ |
|---|---|---|---|---|
| 3 | 8 | 0.180 | 0.180 | 0.625 |
| 3 | 16 | 0.092 | 0.359 | 0.736 |
| 3 | 32 | 0.191 | 0.442 | 0.719 |
| 4 | 8 | 0.234 | 0.234 | 0.768 |
| 4 | 12 | 0.162 | 0.618 | 0.839 |

$L=32$, $k=3$에서 $\eta$ 대비 비율 $0.191/0.05\approx3.8$, $0.442/0.1\approx4.4$로 $C_3\approx4$인 $C_k\eta$ 꼴입니다. 작은 $L$에서는
$\eta L<1$이라 금지 깊이가 격자에 걸리지 않아 비단조로 보입니다 ($1/L$ 항의 효과). ✓

**지우기**: $k=4$, $L=12$, $\eta=0.1$에서 정칙 나무와 지울 잎의 쌍 3676개 모두, 지운 뒤에도 정칙. ✓

---

## 문단 3. 질문에 대한 해설: 정칙 나무가 다중 분기를 허용하는 이유

정칙성의 둘째 조건은 "서로 **다른** 갈라짐 꼭짓점"의 깊이에 관한 것이고, 한 꼭짓점의 자식 수는 제한하지 않습니다. 이것은
의도된 것입니다. 다중 분기는 $Q_k$에서 **드물지 않고**, 증명에서 **비싸지도 않기** 때문입니다.

### (a) $Q_k$에서 확률이 $O(1)$

(3.8)의 두 종류 선택을 비교하면:

| 선택 | 확률 | 크기 |
|---|---|---|
| 홑자식 꼭짓점에서 갈라짐 (새 좌표 생성) | $\delta/n$ | $O(1/L)$ |
| 이미 갈라진 꼭짓점 (자식 $n_\beta$개)에 자식 추가 | $(n_\beta m_{d+1}-m_d)/n\approx(n_\beta-1)m_d/n$ | $O(1)$ |

예: $Q_3$에서 세 잎이 한 꼭짓점에서 동시에 갈라질 확률은
$$\sum_{d=0}^{L-1}\delta\cdot\frac{(d+2)\delta}{2}=\frac{\delta^2}2\Bigl(\frac{L(L-1)}2+2L\Bigr)\longrightarrow\frac14.$$

| $L$ | 8 | 16 | 32 | ∞ |
|---|---|---|---|---|
| 공식 | 0.34375 | 0.296875 | 0.2734 | 0.25 |
| 열거한 $Q_3\{\text{3갈래 꼭짓점}\}$ | 0.3438 | 0.2969 | 0.2734 | — |

$Q_4$에서는 3갈래 이상 꼭짓점이 있을 확률이 $L=8$에서 0.64, $L=12$에서 0.60입니다. 그리고 정칙 나무 안에서도 비율이 큽니다:

| $L$ | $\eta$ | $Q_3\{\text{정칙}\}$ | $Q_3\{\text{정칙이고 3갈래}\}$ | 정칙 중 3갈래 비율 |
|---|---|---|---|---|
| 32 | 0.05 | 0.809 | 0.255 | 0.315 |
| 32 | 0.1 | 0.558 | 0.220 | 0.394 |
| 64 | 0.05 | 0.761 | 0.237 | 0.311 |
| 64 | 0.1 | 0.574 | 0.212 | 0.369 |

다중 분기를 버리면 로그 전개 (3.9)의 $k$차 항에서 $O(1)$의 질량을 잃습니다. 정칙성이 버리는 것은 확률 $O(\eta+1/L)$인 사건뿐이어야
하므로, 다중 분기는 정칙 쪽에 남아야 합니다.

### (b) 증명에서 비용은 $\eta$뿐

$\kappa(S)$ (3.13)에서 $a_v$갈래 꼭짓점의 인자는 $\prod_{j=1}^{a_v-1}(m_{d_v}-jm_{d_v+1})$이고, 작은 인자 $-\delta$는 $j=1$ 하나뿐,
$j\ge2$는 $|m_d-jm_{d+1}|\ge m_d>\eta$입니다. 그래서 Lemma 3.5의 $|J|\ge\delta^b\eta^{\sum(a_v-2)}$ — 자식 수는 $\eta$의 지수에만
들어가고 $\delta$의 지수 $b$ (꼭짓점 수)는 늘리지 않습니다. 7.3절에서 $J$로 나눌 때 상대 비용 (7.20)이 $C_{k,\eta}$로 유계인 이유입니다.

### (c) 물리적 그림

$m_d=d/L$, $L\to\infty$에서 $Q_k$는 Parisi 매개변수가 균등한 Ruelle cascade의 replica 계보, 곧 **Bolthausen–Sznitman 합류과정**이고,
이 과정은 다중 합류가 특징입니다. 상태 언어로는 세 replica가 같은 부모 상태 안의 서로 다른 세 하위 상태에 있어 세 쌍의 overlap이
모두 $q_d$인 경우 — 초계량 공간의 정삼각형 — 로, RSB에서 흔한 배치입니다.

**정리**: 정칙성은 서로 다른 깊이 좌표를 떼어 놓는 장치입니다. 한 깊이에서 여러 갈래로 나뉘는 것은 확률이 $O(1)$이라 버릴 수 없고,
비용도 $\eta$ 정도라 버릴 필요가 없습니다.

---

## 문단 4. Remark 3.7

> For fixed $k$ there are finitely many labeled topologies. Therefore (3.17) converts an unnormalized depth
> average $L^{-a}\sum$ for a topology with $a$ branching coordinates into a bound for its contribution under
> $Q_k$. The same is true for errors on subshapes: summing over coordinates discarded by the subshape costs
> at most the corresponding power of $L$. Together with (3.16), this allows averaged estimates on regular
> depth assignments to be used in the logarithmic expansion.

### 해석

$Q_k$ 아래 기대값 $=\sum_{\text{위상}}\sum_{\text{깊이 배정}}Q_k(\cdot)\,z(\cdot)\le C_k\sum_{\text{위상}}L^{-a}\sum_{\mathbf q}z(\mathbf q)$ — 7.1절의
정규화하지 않은 깊이 평균 $\mathcal A_{L,\eta}$입니다. 부분 모양 (예: 유도 부분 나무의 multi-overlap)에 대한 오차는 버린 좌표를 합하면
$L^{a-a'}$만 들므로 $L^{-a'}\sum$로 정리됩니다. 이것이 8.2절 (8.5)의 논증 그대로입니다.

### 물리적 의미

균등 격자에서 $Q_k$의 깊이 배정 확률이 $L^{-a}$로 **균등**하다는 것은, 로그 전개가 Parisi 변수 $x$의 모든 값을 고르게 본다는 뜻입니다.
그래서 7장이 증명한 "깊이 평균 집중"이 정확히 8장이 필요로 하는 양이 됩니다 (서론 문단 7: "this averaged control is sufficient").

---

## 요약

- 정칙 모양: 갈라짐 깊이가 경계에서 $\eta$ 이상, 서로 다른 갈라짐 꼭짓점끼리 $\eta$ 이상 떨어짐. 자식 수는 제한 없음.
- Lemma 3.6: 비정칙 확률 $\le C_k(\eta+1/L)$, 특정 깊이 배정 확률 $\le C_kL^{-a}$, 잎을 지워도 정칙 유지. 정확 열거로 확인.
- 다중 분기는 $Q_k$에서 확률 $O(1)$ ($Q_3$에서 $\to1/4$)이고 비용은 $\eta$뿐이라 정칙 쪽에 남깁니다 (Bolthausen–Sznitman의 다중 합류).
- Remark 3.7: $Q_k$ 평균 ↔ 깊이 평균 $\mathcal A_{L,\eta}$의 변환.

**다음 절 예고**: 4장에서 보간 위쪽 한계 (명제 4.1)를 증명합니다 — [04-interpolation-upper-bound.md](04-interpolation-upper-bound.md).
