# 6.5 Prescribing the colored tree — 문단별 해설

원문: `build/sections/perturbations.tex` 6.5절, PDF 19–21쪽. 번호는 PDF 기준
(정리 6.5, 식 (6.17), (6.18), Remark 6.6). 앞 절 참조: Lemma 3.3 (3.11), Lemma 3.4, Lemma 6.2, 6.3, 6.4.

6장의 결론입니다. Lemma 6.4가 준 "Taylor 계수 → 0"을 **색칠한 나무 모양마다 분리**해서, Ghirlanda–Guerra
항등식의 유한 깊이 위계 버전 (6.17)을 얻습니다.

---

## 문단 1. anchor의 두 종류, 색, 제약, $R_E$

> The anchor is called a *spin anchor* when $S_0=\sigma_i$, and a *marker anchor* when $S_0=1$. Added
> colors are ordered $1,\ldots,k$; the anchor has color $0$. They occupy distinct replica positions,
> none equal to the anchor, according to the canceled-anchor extension rule of Lemma 3.3. A
> constraint $\mathcal C$ prescribes any consistent collection of their pairwise split depths,
> involving only the added colors and the anchor. It imposes no extra restrictions involving the
> other old replicas. Let $\mathfrak E(\mathcal T,a_*,\mathcal C)$ be the allowed extension histories,
> with coefficients $c_E$ from that lemma. For a history $E$, set
> $$R_E=\frac1N\sum_{i=1}^N\begin{cases}\sigma_i^{a_*}\prod_{j=1}^k\sigma_i^{a_j(E)},&\text{spin anchor},\\ \prod_{j=1}^k\sigma_i^{a_j(E)},&\text{marker anchor}.\end{cases}$$
> For $k=0$ these are respectively $R_{\{a_*\}}$ and $1$.

### 기호

| 기호 | 의미 |
|---|---|
| spin anchor ($S_0=\sigma_i$) | 점수가 새 자리 스핀을 읽음 → $R_E$에 $\sigma^{a_*}_i$ 포함 |
| marker anchor ($S_0=1$) | 점수가 표시 변수만 읽음 → $R_E$에 anchor 스핀 없음 |
| 색 $0$ | anchor $a_*$ |
| 색 $1..k$ | 삽입 $A$의 $t$-전개에서 생기는 $k$개의 $D=g\sigma_i$ 인자가 놓이는 잎 |
| $\mathcal C$ | anchor와 색들 사이의 갈라짐 깊이 지정 (일관된 것) |
| $\mathfrak E(\mathcal T,a_*,\mathcal C)$ | $\mathcal C$를 만족하는 확장 이력 (Lemma 3.3: 옛 잎 계수 1, 새 경로 계수 $\gamma_\beta$) |
| $R_E$ | 이력 $E$의 색칠된 잎들 위 multi-overlap (3.1) |

### 해석

$t^k$ 차 계수에서는 $D=g\sigma_i$가 $k$번 나옵니다. 각 $D$는 (i) 아직 안 쓴 옛 잎 또는 (ii) 새 경로에
붙고, 새 자리 $i$를 평균하면 그 잎들의 스핀 곱의 자리 평균, 즉 $R_E$가 됩니다. 점수의 $S_0$가 $\sigma_i$이면
anchor의 스핀도 곱해집니다. "제약은 다른 옛 replica를 언급하지 않는다"는 것은 3.3절에서 말한
"reference path"만 지정한다는 뜻입니다. 이 덕분에 Lemma 3.4의 총합 $\kappa(S)$가 옛 나무와 무관해집니다.

---

## 문단 2. 정리 6.5 (Identity on prescribed trees)

> **Theorem 6.5.** For the perturbation family defined above, along every sequence from Lemma 6.2,
> $$\sum_{E\in\mathfrak E(\mathcal T,a_*,\mathcal C)}c_E\,\mathbb E[fR_E]-\mathbb Ef\sum_{E\in\mathfrak E(\{a_*\},a_*,\mathcal C)}c_E\,\mathbb E[R_E]\longrightarrow0.\tag{6.17}$$
> This holds for every fixed old tree, either kind of anchor, every bounded polynomial $f$ in its
> multioverlaps, every finite number of ordered added colors, and every prescribed constraint
> $\mathcal C$. The empty addition is allowed. The error is taken to zero at fixed $L$, fixed tree,
> and fixed constraint, before any limit in $L$.

### 해석

좌변 첫 항: old tree $\mathcal T$ (잎 = $f$가 읽는 replica들 + anchor)에 색 $k$개를 붙이는 모든 허용 확장의
가중합. 둘째 항: 옛 replica 없이 anchor 하나만 있는 나무에 같은 제약으로 색을 붙인 값 × $\mathbb Ef$.
즉 **"옛 replica들의 정보 $f$는, 새로 붙인 색들의 (계수 가중) 통계에 영향을 주지 않는다"**.

### 물리적 의미 — Ghirlanda–Guerra와의 연결 (형식적 계산)

가장 단순한 경우를 손으로 풀어 봅니다. 위계가 없는 경우 ($L=1$, $m_0=0$, $m_1=1$; 논문은 $L\ge2$이지만
구조를 보기 위한 형식적 계산임을 밝혀 둡니다). old tree: 뿌리 아래 잎 $1..n$ ($a_*=1$), spin anchor,
$k=1$, 제약 없음.
- old tree 쪽 선택: 옛 잎 $l\in\{2..n\}$ (계수 1) 또는 뿌리에서 새 경로 (계수 $\gamma=m_0-nm_1=-n$):
  $\sum_{l=2}^n\mathbb E[fR_{1l}]-n\,\mathbb E[fR_{1,n+1}]$.
- 단일 anchor 쪽: 뿌리에서 새 경로, 계수 $0-1\cdot1=-1$: $-\mathbb E[R_{12}]$.
- (6.17): $\sum_{l=2}^n\mathbb E[fR_{1l}]-n\mathbb E[fR_{1,n+1}]+\mathbb Ef\,\mathbb ER_{12}\to0$, 즉
$$\mathbb E[fR_{1,n+1}]\approx\frac1n\mathbb Ef\,\mathbb ER_{12}+\frac1n\sum_{l=2}^n\mathbb E[fR_{1l}],$$
**정확히 Ghirlanda–Guerra 항등식**입니다. ✓ $L\ge2$에서는 새 경로가 깊이 $d$의 꼭짓점에서 계수
$m_d-n_\beta m_{d+1}$로 갈라지고, 제약 $\mathcal C$로 "anchor와 깊이 $d$에서 갈라짐"을 고르면 GG 항등식이
**깊이별로 층을 이룬 형태**가 됩니다. 이것이 Parisi 위계 (ultrametricity + Ruelle cascade)를 강제하는 재료이며,
$k\ge2$와 multi-overlap $R_E$는 희석 모형에 필요한 고차 버전입니다.

---

## 문단 3. 증명 ① $k=0$과 편극(polarization)

> For $k=0$, the claim is the vanishing constant coefficient from Lemma 6.4, using constant marks. For
> $k\ge1$, we explain how to extract distinct colored marks. Fix rational-valued functions
> $g_0,g_1,\ldots,g_k$, all bounded by one and constructed jointly from the same finite collection of
> auxiliary marks. The mixed insertion uses $A=1+\sum_{j=1}^kz_jg_j\sigma_i$. Its mixed derivative in
> all $z_j$ is the symmetric multilinear form obtained by polarizing the degree-$k$ coefficient for a
> single $g$. More explicitly, if $Q_N(g)=k![t^k]H_N(t,0)$, then the mixed derivative is
> $$\frac{k^k}{2^kk!}\sum_{\epsilon\in\{-1,1\}^k}\Bigl(\prod_{j=1}^k\epsilon_j\Bigr)Q_N\Bigl(k^{-1}\sum_{j=1}^k\epsilon_jg_j\Bigr).$$
> Every argument of $Q_N$ is rational-valued and bounded by one, so each resulting pair $(g,g_0)$
> belongs to the fixed mark family. Lemma 6.4 makes the displayed mixed derivative tend to zero. The
> mixed derivative expansion is precisely the ordered extension rule: there is no additional
> factorial in its coefficients.

### 해석과 검증

- **$k=0$**: $H_N(0,0)$ (상수항) $\to0$이 곧 (6.17)의 $k=0$ 경우. marker anchor에서는 $R_E=1$이고 빈 확장의
  가중치 1이므로 (6.17)이 $\mathbb E[f]-\mathbb Ef=0$으로 자명하고, spin anchor에서는
  $\mathbb E[fR_{a_*}]-\mathbb Ef\,\mathbb ER_{a_*}\to0$ (자화와 $f$의 비상관). ✓
  (논문의 "constant marks": $g_0$를 상수로 둔 명세. $H_N(0,0)$은 $g$에 의존하지 않음.)
- **왜 편극이 필요한가**: 색마다 다른 표시 함수 $g_j$를 붙여야 색별 제약을 줄 수 있습니다. 그런데 섭동 족에는
  "하나의 $g$"만 있는 항 $1+tg\sigma_i$만 있습니다. $H_N$이 $tg$의 함수이므로 $Q_N(g)=k![t^k]H_N$은
  $g$에 대해 $k$차 동차 다항식이고, 대칭 $k$-선형형식 $\mathcal M$에 대해 $Q_N(g)=\mathcal M(g,\dots,g)$입니다.
  혼합 도함수 $\partial_{z_1}\cdots\partial_{z_k}H_N|_0=\mathcal M(g_1,\dots,g_k)$이고, 편극 공식
  $\mathcal M(g_1..g_k)=\frac1{2^kk!}\sum_\epsilon\prod\epsilon_j\,Q(\sum\epsilon_jg_j)$에 동차성
  $Q(k^{-1}x)=k^{-k}Q(x)$를 쓰면 논문의 식. ✓
- **$k^{-1}$ 배율**: $|k^{-1}\sum\epsilon_jg_j|\le1$이고 유리수 값 → 섭동 족 안. ✓ 각 $Q_N(\cdot)\to0$
  (Lemma 6.4) ⇒ 유한 합도 $\to0$. ✓
- **"no additional factorial"**: Lemma 3.3에서 혼합 도함수 $\partial_{t_1}\cdots\partial_{t_k}$의 전개는 순서 있는
  색 규칙 그대로 계수 $c_E$이고, 같은 방향일 때만 $1/k!$이 붙습니다. ✓

### 수치 확인 (편극 공식)

무작위 대칭 $k$-선형형식 ($\mathbb R^3$ 위), 무작위 $g_1..g_k\in[-1,1]^3$:

| $k$ | $\mathcal M(g_1,\dots,g_k)$ | 논문의 편극 식 |
|---|---|---|
| 2 | $-0.092212812025$ | $-0.092212812025$ |
| 3 | $-0.265937554414$ | $-0.265937554414$ |
| 4 | $+0.009619009299$ | $+0.009619009299$ |

✓

> (작업 중 — 다음 문단부터 이어짐)
