# 221. The Mézard–Parisi formula for diluted spin glasses — 문단별 해설

원문: `preprints/The-Mezard-Parisi-formula-for-diluted-spin-glasses-September-23-2026/paper.pdf`

- 1–3장: 이 저장소에 해설 추가 (아래 목록). 요약은 `PROMPT.md`의 "지금까지의 맥락"에도 있음.
- 4–10장: **완료**. 작업 지시문은 `PROMPT.md`.

| 절 | 파일 | 상태 |
|---|---|---|
| 1 Introduction | [01-introduction.md](01-introduction.md) | 완료 |
| 2 The model + 2.1 The hierarchical cavity functional | [02-1-model-functional.md](02-1-model-functional.md) | 완료 |
| 2.2 Proof strategy | — | 미착수 |
| 3.1 Path kernels and insertions | — | 미착수 |
| 3.2 The two expansion rules | — | 미착수 |
| 3.3 Sums of extension coefficients | — | 미착수 |
| 3.4 The distribution of branching depths | — | 미착수 |
| 4 The interpolation upper bound | [04-interpolation-upper-bound.md](04-interpolation-upper-bound.md) | 완료 |
| 5 A perturbed cavity reservoir | [05-cavity-reservoir.md](05-cavity-reservoir.md) | 완료 |
| 6 도입 + 6.1 The perturbation family | [06-1-perturbation-family.md](06-1-perturbation-family.md) | 완료 |
| 6.2 Concentration of each perturbation score | [06-2-score-concentration.md](06-2-score-concentration.md) | 완료 |
| 6.3 One sequence for low increments | [06-3-parameter-selection.md](06-3-parameter-selection.md) | 완료 |
| 6.4 Poisson insertion and analytic extraction | [06-4-palm-analytic.md](06-4-palm-analytic.md) | 완료 |
| 6.5 Prescribing the colored tree | [06-5-prescribed-trees.md](06-5-prescribed-trees.md) | 완료 |
| 7 도입 + 7.1 Averages over depths | [07-1-depth-averages.md](07-1-depth-averages.md) | 완료 |
| 7.2 Conditional covariance and continuity in depth | [07-2-conditional-covariance.md](07-2-conditional-covariance.md) | 완료 |
| 7.3 Conditional decorrelation | [07-3-conditional-decorrelation.md](07-3-conditional-decorrelation.md) | 완료 |
| 7.4 Concentration of every multioverlap | [07-4-multioverlap-concentration.md](07-4-multioverlap-concentration.md) | 완료 |
| 8 도입 + 8.1 Encoding a single-site tree | [08-1-encoding.md](08-1-encoding.md) | 완료 |
| 8.2 From multioverlaps to spin patterns | [08-2-patterns.md](08-2-patterns.md) | 완료 |
| 8.3 Comparison of the insertion logarithms | [08-3-insertion-comparison.md](08-3-insertion-comparison.md) | 완료 |
| 9 Normalization, truncation, completion | [09-completion.md](09-completion.md) | 완료 (5장 판단 메모 정정 포함) |
| 10 Named models and zero temperature | [10-named-models.md](10-named-models.md) | 완료 |

## 주요 검토 메모 (본문의 "검토 메모"·"판단 메모" 모음)

- **5장 ↔ 9장 (정정)**: 5장에서 "순열 불변성은 대칭화로 일반성을 잃지 않는다"고 판단했으나, 대칭화는 $F_N$만 보존하고
  $\mathcal B_r$은 바꿀 수 있습니다 ($U_\theta$가 새 스핀 자리를 고정). 논문은 상수 이동 $\hat\theta=\theta-\theta(1,\dots,1)$으로
  처리하며, 분해 가정 아래에서는 문제가 없습니다. 9장에 정확 계산으로 확인.
- **5장**: $\alpha N-\rho_N\ge0$은 "충분히 큰 $N$"뿐 아니라 모든 $N\ge1$에서 성립.
- **6.2절**: $s_N=N^{\gamma}$일 때 볼록-도함수 단계는 $\gamma>1/2$를 요구 ($N^{3/4}$는 만족).
- **6.4절**: Lemma 6.4는 해석성에 본질적으로 의존 ($j^{-j}$는 어떤 거듭제곱보다 빨리 작아짐).
- **7.3절**: 점화식 (7.27)의 수렴은 정성적이며, 속도는 대략 $L^{-4^{-(k-1)}}$ 수준.
- **10장**: 짝수성은 4장 볼록성에서만 쓰이고, SAT에서는 $P_{\mathcal T},B_{\mathcal T}\ge0$이므로 홀수 $K$에서도 같은 증명이
  성립할 것으로 보입니다 (논문은 주장하지 않음; 확인 필요).

수치 확인 스크립트는 세션 스크래치패드에서 실행했고 커밋하지 않았습니다. 결과는 각 파일 본문의 표에 남겨 두었습니다.
