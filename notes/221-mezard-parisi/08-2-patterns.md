# 8.2 From multioverlaps to spin patterns — 문단별 해설

원문: `build/sections/comparison.tex` 8.2절, PDF 29–30쪽. 번호는 PDF 기준 (Lemma 8.2, 식 (8.3)–(8.5)).
앞 절 참조: Lemma 8.1 (8.2), 정리 7.1 (7.4), Lemma 3.2 ($Q_k$), Lemma 3.6, (7.1).

8.1절의 부호화는 한 자리씩만 정확합니다. 삽입 $A_{\rm s}$, $A_{\rm b}$는 자리 여러 개 ($p-1$개 × clause 수)를 동시에
읽으므로, 그 자리들의 replica 패턴을 **독립 시험 라벨**로 바꿀 수 있어야 합니다. 그 비용이 multi-overlap 요동입니다.

---

## 문단 1. Lemma 8.2 (Empirical-pattern comparison)

> **Lemma 8.2.** Fix a prescribed tree with $k$ leaves. Suppose an observable of absolute value at most
> one uses the replica-spin patterns at $a$ independent uniform site labels. Replacing these patterns by
> $a$ independent trial-label patterns from Lemma 8.1 changes its expected value by at most
> $$a\sum_{\varnothing\ne S\subseteq[k]}\mathbb E|R_S-\mathbb ER_S|.\tag{8.3}$$
> The observable may also depend on new insertion disorder, independent of the reservoir.

### 기호

| 기호 | 의미 |
|---|---|
| 패턴 $\boldsymbol\sigma_i=(\sigma_i^1,\dots,\sigma_i^k)$ | 자리 $i$에서 $k$개 replica 스핀의 벡터 |
| $a$ | 관측량이 읽는 균등 자리 라벨 수 |
| $\pi$ | 표본으로 뽑힌 replica 배치들이 주어졌을 때 패턴의 경험 분포 (자리에 대한) |
| $\bar\pi=\mathbb E\pi$ | 시험 라벨의 패턴 분포 ((8.2)) |

### 해석

같은 replica 배치 아래 무작위 자리 $a$개의 패턴은 $\pi^{\otimes a}$ (복원 추출)를 따릅니다. 시험 라벨 $a$개는 서로 독립이고
각각 $\bar\pi$를 따르므로 $\bar\pi^{\otimes a}$. 둘의 차이는 $\pi$가 $\bar\pi$에서 얼마나 요동하는가 — 이것이
$R_S$의 요동입니다 (패턴 분포의 Walsh–Fourier 계수가 $R_S$).

---

## 문단 2. Lemma 8.2의 증명

> Conditional on the sampled reservoir configurations, the pattern $\boldsymbol\sigma_i$ at a uniform
> site has empirical distribution
> $$\pi(\boldsymbol e)=\frac1N\sum_i\prod_{b=1}^k\frac{1+e_b\sigma_i^b}{2}=2^{-k}\sum_{S\subseteq[k]}R_S\prod_{b\in S}e_b,\qquad\boldsymbol e\in\{-1,1\}^k.$$
> The trial-label distribution is $\bar\pi=\mathbb E\pi$ by (8.2). Independent uniform sampling with
> replacement gives $\pi^{\otimes a}$ conditionally in the reservoir; the trial distribution is
> $\bar\pi^{\otimes a}$. The elementary telescoping bound for product measures gives
> $$\|\pi^{\otimes a}-\bar\pi^{\otimes a}\|_{\rm TV}\le a\|\pi-\bar\pi\|_{\rm TV}\le\frac a2\sum_{\varnothing\ne S\subseteq[k]}|R_S-\mathbb ER_S|.$$
> Integrating a function bounded by one costs at most twice total variation. Conditioning on the
> independent insertion disorder proves the last assertion.

### 검증

- **Walsh 전개**: $\prod_b\frac{1+e_b\sigma_i^b}2=2^{-k}\sum_S\prod_{b\in S}e_b\sigma_i^b$; 자리 평균하면 $R_S$. ✓
- **$\bar\pi=\mathbb E\pi$**: (8.2)로 시험 라벨의 Walsh 계수가 $\mathbb ER_S$. ✓
- **곱 측도 망원 합**: $\pi^{\otimes a}-\bar\pi^{\otimes a}=\sum_{j=1}^a\pi^{\otimes(j-1)}\otimes(\pi-\bar\pi)\otimes\bar\pi^{\otimes(a-j)}$ ⇒ TV $\le a\,$TV. ✓
- **TV 한계**: $\|\pi-\bar\pi\|_{\rm TV}=\frac12\sum_e|\pi(e)-\bar\pi(e)|\le\frac12\cdot2^{-k}\sum_e\sum_{S\ne\varnothing}|R_S-\mathbb ER_S|=\frac12\sum_{S\ne\varnothing}|R_S-\mathbb ER_S|$ ($S=\varnothing$ 항은 $R_\varnothing=1$로 상쇄). ✓
- $|g|\le1$이면 $|\int g\,d\mu-\int g\,d\nu|\le2\|\mu-\nu\|_{\rm TV}$ ⇒ (8.3) (기대값 취함). ✓
- 새 삽입 무질서는 저장소와 독립이므로 조건부로 같은 논증. ✓

### 수치 확인

$k=3$, $N=7$: Walsh 전개 오차 $2.8\times10^{-17}$ ✓. 무작위 배치 40개로 만든 "저장소"에서
$\|\pi-\bar\pi\|_{\rm TV}/(\frac12\sum|R_S-\mathbb ER_S|)$ 최댓값 0.479 ≤ 1 ✓, $a=2,3$에서
$\|\pi^{\otimes a}-\bar\pi^{\otimes a}\|_{\rm TV}/(a\|\pi-\bar\pi\|_{\rm TV})$ 최댓값 0.886 ≤ 1 ✓.

### 물리적 의미

"서로 다른 자리의 스핀 패턴이 독립"이라는 cavity 가정 = **경험 패턴 분포 $\pi$가 자기 평균**한다 = 모든
$R_S$가 집중한다. 이것이 정리 7.1이 필요한 정확한 이유입니다. RS 경우의 고전적 형태는 "overlap 집중
$R_{12}\approx q$ ⇒ 서로 다른 자리의 국소장이 독립"입니다.

---

## 문단 3. 정리 7.1의 귀결 (8.4)

> Let $Q_k$ be the tree law in Lemma 3.2. We need the following consequence of the decorrelation theorem:
> $$\lim_{L\to\infty}\limsup_{N\to\infty}\mathbb E_{Q_k}\sum_{\varnothing\ne S\subseteq[k]}\mathbb E|R_S-\mathbb ER_S|=0\qquad(k\text{ fixed}).\tag{8.4}$$
> Here and below the inner limit is along the selected fixed-$L$ sequence.

### 해석

로그 전개 (Lemma 3.2)의 $k$차 항은 $Q_k$로 뽑은 나무 위의 기대값입니다. 그 나무들에 대해 평균한 multi-overlap
요동이 사라지면, 전개의 각 항에서 저장소 → 시험 라벨 교체 비용이 사라집니다. 정리 7.1은 **깊이 평균**
$\mathcal A_{L,\eta}$에 대한 진술이고, (8.4)는 **$Q_k$ 평균**에 대한 진술이므로 둘을 잇는 것이 다음 문단입니다.

---

## 문단 4. (8.4)의 증명: (8.5)

> To see this, fix $0<\eta<1/2$, and let $\mathfrak S_k$ be the finite collection of labeled topologies on
> nonempty subsets of $[k]$. We claim the bound
> $$\mathbb E_{Q_k}\sum_{\varnothing\ne S\subseteq[k]}\mathbb E|R_S-\mathbb ER_S|\le C_k\left(\eta+L^{-1}+\sum_{U\in\mathfrak S_k}\bigl(\mathcal A_{L,\eta}\mathrm{Var}(R_U)\bigr)^{1/2}\right).\tag{8.5}$$
> The average for a singleton has no depth coordinates. By Lemma 3.6, nonregular trees have probability
> at most $C_k(\eta+L^{-1})$. On regular trees every induced subtree retains the interior and separation
> conditions on its branching depths. For a topology with $a$ branching vertices, each depth assignment
> has probability at most $C_kL^{-a}$. If an induced subtree retains $a'$ branching vertices, each
> assignment of its depths has at most $L^{a-a'}$ extensions to the full tree. Summing out these unused
> coordinates leaves exactly the normalization $L^{-a'}$ in $\mathcal A_{L,\eta}$. Cauchy–Schwarz bounds
> the resulting average of mean absolute deviations by $\bigl(\mathcal A_{L,\eta}\mathrm{Var}(R_U)\bigr)^{1/2}$.
> Summing over the finitely many topologies and subsets, and using the bound two for each deviation on
> nonregular trees, proves (8.5). Apply Theorem 7.1 first at fixed $\eta$, taking the fixed-$L$ limit in
> $N$ before $L\to\infty$, and then let $\eta\downarrow0$ to obtain (8.4).

### 검증 (단계별)

1. 비정칙 나무: $Q_k$ 확률 $\le C_k(\eta+1/L)$ (3.16), 각 편차 $\le2$, 부분집합 $2^k$개 ⇒ $C_k(\eta+L^{-1})$. ✓
2. 정칙 나무 $\mathcal T$, 부분집합 $S$: $R_S$는 유도 부분 나무 $U$ (잎 $S$, 홑자식 압축)에만 의존 — 사영 일관성. 정칙성은
   유도 부분 나무로 상속 (Lemma 3.6 마지막 문장). ✓
3. 위상 $\mathcal T$ (갈라짐 $a$개)의 깊이 배정 확률 $\le C_kL^{-a}$ (3.17). $U$가 $a'$개의 갈라짐을 가지면 $U$의 배정
   하나를 확장하는 $\mathcal T$ 배정은 $\le L^{a-a'}$개 ⇒ $\sum\le C_kL^{-a'}\sum_{U\text{-배정}}\mathbb E|R_U-\mathbb ER_U|$
   $=C_k\mathcal A_{L,\eta}\mathbb E|R_U-\mathbb ER_U|$. ✓ (Remark 3.7의 논리.)
4. Cauchy–Schwarz: $\mathcal A(\mathbb E|\cdot|)\le\mathcal A(\mathrm{Var}^{1/2})\le(\mathcal A\mathrm{Var})^{1/2}$ ((7.2), $\gamma=1/2$). ✓
5. 극한: $\eta$ 고정 → $\limsup_N$ → $L\to\infty$ (정리 7.1이 각 $U$에서 0) → 남는 $C_k\eta$ → $\eta\downarrow0$. ✓

**검토 메모.** (8.5)의 좌변은 $\eta$에 의존하지 않으므로 마지막 $\eta\downarrow0$은 정당합니다. 정리 7.1의 극한은
$\eta>0$ 고정에서만 주어지므로 이 순서가 필요합니다. ✓

### 물리적 의미

$Q_k$는 로그 전개에서 replica 나무가 나타나는 "자연스러운" 확률이고 (Parisi의 $x$-측도로 뽑은 Ruelle 나무),
대부분의 나무는 갈라짐 깊이가 고르게 퍼져 있어 정칙입니다. 정리 7.1의 깊이 평균 정보가 정확히 $Q_k$ 평균으로
전달되는 것은 $Q_k$의 깊이 배정 확률이 $L^{-a}$로 균등하기 때문입니다 (균등 격자 $m_d=d/L$에서 갈라짐 깊이가
균등 분포 — 3.2절 "$Q_2$에서 깊이 $d$ 갈라짐 확률 $m_{d+1}-m_d=\delta$").

---

## 요약

- Lemma 8.2: 자리 $a$개의 replica 패턴을 독립 시험 라벨로 바꾸는 비용 $\le a\sum_{S\ne\varnothing}\mathbb E|R_S-\mathbb ER_S|$.
  핵심은 패턴 경험 분포의 Walsh 전개 (계수 = multi-overlap)와 곱 측도 TV 망원 합. 수치로 확인.
- (8.4)–(8.5): 정리 7.1의 깊이 평균 집중을 $Q_k$ 나무 평균 집중으로 변환. 비정칙 나무는 $C_k(\eta+1/L)$, 정칙 나무는
  유도 부분 나무별 깊이 평균 + Cauchy–Schwarz.
- 물리적으로: 경험 패턴 분포의 자기 평균성 = 서로 다른 자리 cavity 장의 독립성.

**다음 절 예고**: 8.3절에서 삽입 로그를 비교해 $\Delta_N\approx\mathcal B_{L-1}(\zeta_{L,N},\mathbf m^{(L)})$ (명제 8.3)을 보이고,
유계 모형의 아래쪽 한계 (따름정리 8.4)를 완성합니다.
