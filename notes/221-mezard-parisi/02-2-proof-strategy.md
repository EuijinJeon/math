# 2.2 Proof strategy — 문단별 해설

원문: `build/sections/overview.tex`, PDF 5–6쪽. 번호 붙은 식 없음. 각 단계가 몇 장에 해당하는지를 연결해 둡니다.

---

## 문단 1. 위쪽 한계와 아래쪽 한계의 구분

> The interpolation upper bound holds at every system size and every finite depth. We reproduce it in
> Section 4, including a normalization that avoids assuming integrability of the multiplier $\log a$. The
> lower bound has four steps.

### 해석

- 위쪽 한계: **모든 $N$**에서 $F_N\le\mathcal B_r$ (명제 4.1). 새로운 점은 $\log a$의 적분 가능성 없이 하는 정규화
  ($c=\theta(1,\dots,1)$을 빼는 것, 4장 문단 7).
- 아래쪽 한계: 아래 네 단계.

---

## 문단 2. 단계 1 — cavity 저장소 선택

> *Select a cavity reservoir.* A reservoir is a common Gibbs system on $N$ spins used to compare systems of
> sizes $N$ and $N+1$. For bounded interaction and field laws, add bounded Poisson perturbations whose number
> is sublinear in the system size. Their effect on the pressure vanishes. At each fixed hierarchy depth,
> select system sizes and deterministic perturbation parameters for which the difference between successive
> expected logarithms after the auxiliary power-mean recursion is at most an arbitrarily small error above
> the original pressure liminf. The same choices give concentration of every perturbation score
> (Section 5 and Lemma 6.2).

### 해석

| 요소 | 위치 |
|---|---|
| 저장소, ASS 증분 $\Delta_N=\log2+\mathbb E\log Y_{0,\rm s}-\mathbb E\log Y_{0,\rm b}+o(1)$ | 5장 Lemma 5.1 |
| 섭동 $s_N=N^{3/4}$개, pressure 변화 $o(N)$ | (5.3), 6.1절 |
| 낮은 증분 + 점수 집중을 동시에 만족하는 결정적 수열 | 6.3절 Lemma 6.2 |

**물리**: Aizenman–Sims–Starr의 cavity 비교 + Ghirlanda–Guerra의 섭동 기법.

---

## 문단 3. 단계 2 — 가지 패턴 지정

> *Prescribe branching patterns.* An elementary calculus for finite probability trees expands insertions
> into signed sums over added replica paths. Independent marks select any prescribed branching pattern.
> Score concentration then gives identities for these signed sums (Section 3 and Theorem 6.5).

### 해석

- 3장: 삽입을 나무 위의 부호 있는 합으로 전개 (Lemma 3.2, 3.3), 계수 합 (Lemma 3.4, 3.5).
- 6.5절: 깊이별 Rademacher 표시로 원하는 갈라짐 깊이를 고름 (6.18), 그리고 GG형 나무 항등식 (6.17).

---

## 문단 4. 단계 3 — 모든 multi-overlap 집중

> *Concentrate all multioverlaps.* Move each internal branching depth of a target tree one step later. The
> first fresh split at each new depth supplies the same small factor as the normalizing coefficient. A
> relative bound on the sum of absolute coefficients preserves control of errors after division.
> Conditional covariance then decays by induction on the number of replicas. A second identity
> concentrates the remaining conditional mean (Section 7).

### 해석

- "한 칸 늦추기": 목표 갈라짐 깊이를 옛 나무의 갈라짐 깊이와 겹치지 않게 해서, 새 갈라짐이 반드시 홑자식
  꼭짓점에서 생기도록 함 → 계수 $-\delta$ (3.3절 마지막 예, 7.3절 그림 1).
- "같은 작은 인자": 정규화 계수 $J=\kappa(S^+)^2$도 꼭짓점마다 $\delta$를 가지므로, 나눈 뒤 상대 비용이 유계 (7.20).
- 조건부 공분산의 귀납 (명제 7.4), marker anchor로 접두부 평균 집중 (7.4절).

---

## 문단 5. 단계 4 — 독립 cavity 메시지 복원

> *Recover independent cavity messages.* Encode a uniformly chosen reservoir site's entire finite hierarchy
> by successive conditional laws. Multioverlap concentration permits different site labels to be replaced
> by independent copies of this process in the cavity insertion. This yields an admissible trial value
> close to the selected increment (Section 8).

### 해석

Lemma 8.1 ($x=\operatorname{arctanh}\langle\sigma_i\rangle$, $\eta_d=\mathrm{Law}(\eta_{d+1}\mid\mathscr G_d)$) → Lemma 8.2 (패턴 교체 비용
= multi-overlap 요동) → 명제 8.3 ($\Delta_N\approx\mathcal B_{L-1}(\zeta_{L,N},\mathbf m^{(L)})$).

---

## 문단 6. 깊이 평균이 충분한 이유와 마무리

> The estimates in Step 3 are averages over separated interior branching depths. The insertion expansion
> assigns vanishing probability to the exceptional trees, so these averages are sufficient for Step 4. No
> uniform concentration in the depth is needed. The resulting lower bound holds for every bounded
> interaction law invariant under permutations of its inputs, without factorization or positivity.
> Finally, normalization and estimates uniform over all trial laws remove boundedness and give Theorem 2.1
> under the stated first moment assumption (Section 9).

### 해석

- 로그 전개의 나무 법칙 $Q_k$에서 "예외적 나무" (갈라짐이 경계 근처이거나 서로 가까움)의 확률은 $C_k(\eta+1/L)$
  (Lemma 3.6), 그리고 깊이 배정 확률이 $L^{-a}$로 균등 (3.17) ⇒ 깊이 평균 정보가 $Q_k$ 평균으로 그대로 전달 (8.2절 (8.5)).
- 아래쪽 한계는 분해·양성 없이 유계·순열 불변만으로 성립 (따름정리 8.4).
- 9장: 상수 이동으로 순열 불변성, 절단으로 유계성, 안정성 Lemma 9.1로 오차 제어.

### 물리적 의미 — 전체 그림 한 장

| 물리학의 cavity 논증 | 이 논문의 엄밀한 대응 |
|---|---|
| 스핀 하나 추가 − clause 보정 = 자유에너지 밀도 | ASS 증분 (5.5) |
| Parisi 위계를 ansatz로 가정 | 보조 변수 위계를 구성하고 섭동으로 맞춤 |
| GG 항등식 / 확률적 안정성 | 정리 6.5 |
| 상태 안의 clustering (순수 상태) | 정리 7.1 (multi-overlap 집중) |
| 이웃 cavity 장의 독립성 | Lemma 8.2 |
| 변분 원리의 방향 | 볼록성 + (2.4) (4장) |

---

## 요약

- 위쪽 한계: 모든 $N$에서 보간 (4장). 아래쪽 한계: 저장소·섭동 (5, 6.1–6.3) → 나무 항등식 (3, 6.4–6.5) → multi-overlap 집중
  (7) → 독립 메시지 복원 (8). 일반화: 9장.
- 깊이 평균 집중으로 충분한 이유는 $Q_k$에서 예외적 나무가 드물고 깊이 배정이 균등하기 때문입니다.

**다음 절 예고**: 3.1절에서 path kernel, 기울인 커널 (3.2), 삽입 재귀 (3.3)과 Lemma 3.1을 다룹니다.
