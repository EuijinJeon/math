# 221번 프리프린트 문단별 해설 — 4장 이후 작업 프롬프트

이 파일은 새 Claude Code 세션에 그대로 넘기는 작업 지시문이다.

---

## 작업 개요

저장소 `EuijinJeon/math`의
`preprints/The-Mezard-Parisi-formula-for-diluted-spin-glasses-September-23-2026/`
(221번, "The Mézard–Parisi formula for diluted spin glasses")를 **4장부터 끝(10장)까지
한 문단씩** 한국어로 해설한다. 1–3장은 이전 세션에서 이미 다뤘고, 그 요약은 아래
"지금까지의 맥락"에 있다.

사용자는 비행기에 타 있어서 **질문에 답할 수 없다.** 확인 질문을 하지 말고, 판단이 필요한
곳은 합리적으로 정해서 진행한 뒤 해설 안에 그 판단을 한 줄로 밝혀 둔다.
사용자는 착륙 후 GitHub에서 그때까지 푸시된 내용을 받아 본다. 그래서 **작업이 끝난 부분은
곧바로 커밋하고 푸시**하는 것이 가장 중요하다.

## 원문 위치

- 소스: `.../build/sections/*.tex`
  - 4장 `upper.tex` (The interpolation upper bound)
  - 5장 `cavity.tex` (A perturbed cavity reservoir)
  - 6장 `perturbations.tex` (6.1–6.5)
  - 7장 `decorrelation.tex` (7.1–7.4)
  - 8장 `comparison.tex` (8.1–8.3)
  - 9장 `reduction.tex` (Normalization, truncation, and completion of the proof)
  - 10장 `consequences.tex` (Named models and the zero-temperature limit)
- PDF: `.../paper.pdf`. **식·Lemma 번호는 PDF 기준**으로 쓴다. tex 라벨과 PDF 번호를 대조하려면
  `pdftotext -layout paper.pdf -`를 쓴다. 번호를 추측하지 말고 확인한다.

## 결과물과 저장 위치

- 디렉터리: `notes/221-mezard-parisi/`
- 절마다 Markdown 파일 하나. 예:
  `04-interpolation-upper-bound.md`, `05-cavity-reservoir.md`, `06-1-perturbation-family.md`,
  `06-2-...md`, …, `07-1-...md`, …, `08-3-...md`, `09-completion.md`, `10-named-models.md`.
  하위 절이 없는 장은 장 하나에 파일 하나로 한다.
- `notes/221-mezard-parisi/README.md`에 진행 상황 목차를 유지한다. 각 파일 링크와 상태
  (완료 / 작업 중 / 미착수)를 적고, 커밋할 때마다 갱신한다.
- 1–3장 해설은 이번 작업 범위가 아니다. README에 "1–3장은 이전 대화에서 다룸"이라고만 적는다.

## 커밋·푸시 규칙 (가장 중요)

- 브랜치: `ccr-26534b03-9eqyqi`. 다른 브랜치에 푸시하지 않는다. PR은 만들지 않는다.
- **순서대로** 진행한다: 4장 → 5장 → 6.1 → … → 10장.
- **절 하나를 끝낼 때마다** README를 갱신하고 커밋한 뒤 즉시 푸시한다. 절이 길면
  (문단 5–6개 이상) 중간에 몇 문단마다 한 번 더 커밋·푸시한다.
  미완성 파일에는 맨 끝에 `> (작업 중 — 다음 문단부터 이어짐)` 표시를 남긴다.
- 푸시 전에 `git pull --rebase origin ccr-26534b03-9eqyqi`를 한다.
  푸시는 `git push -u origin ccr-26534b03-9eqyqi`를 쓴다. 네트워크 오류가 나면
  2s, 4s, 8s, 16s 간격으로 최대 4번 재시도한다.
- 커밋 메시지 예: `notes(221): 4장 interpolation upper bound 해설`.
  세션 환경이 지시하는 커밋 attribution 줄을 따른다.
- 스크래치 스크립트는 세션 스크래치패드에 두고 커밋하지 않는다. 다만 해설에 쓴 수치 결과는
  본문에 표로 남긴다.

## 해설 형식 (이전 세션과 같은 스타일)

각 문단마다 다음 순서로 쓴다.

1. **원문 인용**: 문단 전체를 인용 블록(`>`)으로 넣는다. 수식은 `$...$` / `$$...$$` LaTeX로 옮긴다.
   PDF 식 번호를 `\tag{}`로 붙인다.
2. **해석**: 한국어로, 문장 또는 의미 단위별로 풀어 쓴다.
   - 새 기호는 표로 정리한다 (기호 | 의미).
   - **물리적 의미**를 반드시 붙인다. 독자는 통계물리 배경은 있지만 Bethe/cavity 방법에는
     익숙하지 않다. replica, 상태(cluster), Parisi 매개변수 $m$, overlap, Ghirlanda–Guerra
     항등식, Aizenman–Sims–Starr, Guerra 보간 같은 물리 개념과 연결한다.
   - 앞 장의 어떤 결과(Lemma 3.x, 식 번호)를 쓰는지 명시한다.
3. **검증**: 증명이나 계산 단계는 한 줄씩 따라가며 맞는지 확인하고, 맞으면 ✓를 붙인다.
   논문이 생략한 단계(예: "telescoping gives")가 있으면 직접 유도해서 채운다.
   틀리거나 빈틈으로 보이는 곳이 있으면 숨기지 말고 "검토 메모"로 분명히 적는다.
4. **작은 예 / 수치 확인**: 가능하면 python으로 작은 모델(예: $L=2,3$, 보조 동전 1–2개,
   스핀 상태 4개, 무작위 가중치)을 만들어 식을 수치로 확인하고, 결과를 표나 코드 블록으로
   남긴다. 이전 세션에서 이 방식으로 Lemma 3.1의 (3.5), 식 (3.6), 3.2절 확장 규칙,
   Lemma 3.2의 로그 전개, Lemma 3.4의 $\kappa(S)$, Lemma 3.5의 절댓값 합,
   Lemma 3.6의 확률 상한을 모두 확인했다. 수치로 확인할 수 없는 부분(극한, 집중 부등식 등)은
   억지로 하지 않는다.
5. 각 파일 끝에 **요약**(3–6줄)과 "다음 문단/절 예고" 한 줄을 둔다.

문체: 존댓말이 아닌 설명체(…입니다/…이다 중 하나로 통일, 이전 세션은 "…입니다"),
제목 계층은 `#`(파일 제목) / `##`(문단) / `###`(세부). 너무 길게 늘이지 말고, 문단 하나에
대략 화면 1–3개 분량.

## 지금까지의 맥락 (1–3장 요약)

**모델 (2장).** 짝수 $p$, 밀도 $\alpha$. $M_N\sim\mathrm{Pois}(\alpha N)$개의 $p$-체 clause,
각 clause는 무작위 자리 $p$개에 $\theta_k(\sigma_{i_1},\dots,\sigma_{i_p})$를 건다.
외부장 $h_i$. $F_N=\frac1N\mathbb E\log Z_N$은 "pressure". 가정은 다음과 같다.
- (2.1) 1차 모멘트: $\mathbb E\max|\theta|+\mathbb E|h|<\infty$
- (2.3) 분해: $e^{\theta(s)}=a(1+b\prod_\ell f_\ell(s_\ell))$, $|b\prod f|<1$
  (Viana–Bray: $a=\cosh\beta J$, $b=\tanh\beta J$, $f(s)=s$)
- (2.4) 양성: $\mathbb E[(-b)^n]\ge0$

**cavity 범함수 (2.1절).** $q_x(s)=e^{xs}/2\cosh x$.
- $C_\theta$ (2.5): clause 하나를 넣을 때의 $Z$ 비율(edge 항)
- $U_\theta$ (2.6): clause가 새 스핀에 보내는 메시지
- 메시지 사슬 (2.7): $\eta_0\sim\zeta$, $\eta_{d+1}\mid\eta_d\sim\eta_d$, $x\mid\eta_{r-1}\sim\eta_{r-1}$.
  $\eta_0$는 뿌리(quenched, 장소별 무작위성), 아래층은 상태별 무작위성
- $V_s$ (2.8) site 항: 새 스핀이 $k\sim\mathrm{Pois}(\alpha p)$개 clause와 함께 들어옴
- $V_e$ (2.9) edge 항
- power mean (2.10): $T_dV=(\mathbb E[(T_{d+1}V)^{m_{d+1}}\mid\mathscr F_d])^{1/m_{d+1}}$.
  $m\to0$이면 quenched, $m=1$이면 annealed. Parisi/Monasson 재가중 $Z_\alpha^m$
- (2.11): $\mathcal B_r=\log2+\mathbb E\log T_0V_s-\alpha(p-1)\mathbb E\log T_0V_e$
  (Bethe 장부: 스핀 추가 − 과다 계산된 clause $\alpha(p-1)$개). $\Phi_r=\inf\mathcal B_r$
- 정리 2.1 (2.13): $\lim F_N=\inf_r\Phi_r$

**증명 전략 (2.2절).** 위쪽 한계는 Guerra–Franz–Leone 보간(4장, (2.3)·(2.4) 사용).
아래쪽 한계는 4단계로 이루어진다.
1. 섭동을 넣은 cavity 저장소 선택(5장, 6.3)
2. 지정한 replica 가지 패턴마다 항등식(3장, 6장)
3. 갈라짐 깊이를 한 칸 늦추고 깊이 평균으로 모든 multi-overlap 집중(7장)
4. 독립 위계 메시지 복원과 비교(8장)

9장은 유계 가정을 1차 모멘트로 완화한다. 아래쪽 한계는 (2.3)·(2.4) 없이 유계·순열 대칭
상호작용이면 성립한다.

**3장 핵심 기호.**
- 경로 깊이 $0..L$, $0=m_0<m_1<\dots<m_L=1$. 뿌리 = quenched 무질서, 삽입해도 고정.
  $r$층 적용에서는 $L=r+1$, 깊이 $1..r$은 보조 변수(실제로는 섭동이 읽는 Rademacher 부호),
  깊이 $L$은 Gibbs 스핀 배치
- 유한 나무 $\mathcal T$: replica = 잎. 홑자식 꼭짓점도 유지. 깊이 $d$에서 갈라짐 = 마지막
  공통 꼭짓점의 깊이. 사영 일관성(잎을 지워도 나머지 법칙 불변)
- $E_{\mathcal T}$: 뿌리를 고정한 나무 표본 평균. $\mathbb E$: 뿌리까지 포함한 전체 평균
- (3.1) multi-overlap $R_S=\frac1N\sum_i\prod_{a\in S}\sigma_i^a$ (replica 패턴 분포의 Walsh 계수)
- $X_{L-1}=\log Z$, $X_{d-1}=m_d^{-1}\log P_de^{m_dX_d}$ (Monasson 퍼텐셜).
  (3.2) 기울인 커널 $K_d=e^{m_d(X_d-X_{d-1})}P_d$. $K_L$ = 보조 접두부가 주어졌을 때의 Gibbs 측도
- (3.3) $Y_L=A$, $Y_{d-1}=(K_dY_d^{m_d})^{1/m_d}$. (3.4) $K_d^A=(Y_d/Y_{d-1})^{m_d}K_d$
- Lemma 3.1: 삽입하면 뿌리 로그가 $\log Y_0$만큼 변한다.
  (3.5) $W_{\mathcal T}(A)=\prod_{\text{잎}}A^a\prod_\beta Y_\beta^{\gamma_\beta}$,
  $\gamma_\beta=m_{d_\beta}-n_\beta m_{d_\beta+1}$. 단조성, 동차성.
  새 변수는 사전분포와 함께 경로 공간에 미리 넣고, 뿌리 변수는 quenched로 남는다
- (3.6) $\partial_{t_j}\log Y_d=E^{A}[D_j/A\mid\mathscr F_d]$: 미분 한 번 = 새 replica 경로 하나
- 3.2절 확장 규칙: 보호된 잎은 미분해도 아무것도 내지 않는다. 보호 안 된 잎은 계수 +1,
  내부 꼭짓점 β의 새 경로는 계수 $\gamma_\beta$
- (3.7) $\sum_\beta(n_\beta m_{d_\beta+1}-m_{d_\beta})=n$ (텔레스코핑)
- (3.8) $Q_k$: 확률 $(n_\beta m_{d_\beta+1}-m_{d_\beta})/n$로 꼭짓점을 골라 새 경로를 붙인다.
  $Q_2$에서 깊이 $d$ 갈라짐 확률은 $m_{d+1}-m_d$. 보조 층 하나이면 CRP$(m,0)$ = Ruelle cascade 통계
- Lemma 3.2 (3.9): $\log Y_0=\sum_k\frac{(-1)^{k-1}t^k}{k}\mathbb E_{Q_k}E_{\mathcal T}\prod_aD^a$,
  나머지 항 (3.10) $\sum_{k>K}c^k/k$
- Lemma 3.3 canceled-anchor 전개: anchor $a_*$는 $A^{a_*}$가 상쇄된 잎(섭동 점수를 측정하는
  replica, Palm 항등식에서 나옴). 색 $j$마다 (i) 안 쓴 기존 잎(계수 1) 또는 (ii) 새 경로($\gamma_\beta$)
- 3.3절: 기존 갈라짐 깊이에 목표를 두면 부호 합 $-\delta$, 절댓값 합 $2+\delta$ → 비율 $2L+1$.
  한 칸 늦추면 둘 다 $\delta$
- Lemma 3.4 (3.12) 한 단계 합 $m_d-jm_{d+1}$, (3.13) $\kappa(S)$. 기존 나무와 무관하다.
  관찰: $\kappa(S)=(-1)^kk!\,Q_{k+1}(S)$
- Lemma 3.5 (3.14) 새 깊이 갈라짐 $b$개이면 $\sum|c_E|\le C_{q,k}\delta^b$.
  (3.15) $m_{d_v}\ge\eta$이면 $\sum|c_E|/|J|\le C_{q,k,\eta}$
- 3.4절 regular: 갈라짐 깊이/L ∈ $(\eta,1-\eta)$, 서로 $\eta$ 초과로 떨어짐.
  두 복사본에서는 대응 깊이를 일부러 맞추고, 서로 다른 좌표에만 조건을 건다
- Lemma 3.6 (3.16) $Q_k$(regular 아님) $\le C_k(\eta+1/L)$, (3.17) 특정 깊이 배치 $\le C_kL^{-a}$,
  잎을 지워도 regular 유지. 7장의 깊이 평균 집중을 8장 로그 전개에 연결한다
- 4장에서 미리 본 것: 보간 도함수 계수 (4.3)
  $-\frac{\lambda^n}{n}\mathbb E[(-b)^n]\mathbb E_{Q_n}\mathbb E[P_T^p-pP_TB_T^{p-1}+(p-1)B_T^p]$.
  짝수 $p$의 볼록성과 (2.4)로 부호가 정해진다

## 시작 방법

1. 저장소 루트에서 브랜치 `ccr-26534b03-9eqyqi`를 체크아웃하고 최신 상태로 pull한다.
2. `pdftotext`가 있는지 확인한다(없으면 `poppler-utils` 설치를 시도하고, 실패하면 tex만 쓴다).
3. `notes/221-mezard-parisi/README.md`를 만들거나 갱신한 뒤 첫 커밋·푸시를 한다.
4. 4장 첫 문단부터 시작한다.

전체를 끝내면 README에 "완료"라고 표시하고 마지막으로 푸시한다. 중간에 컨텍스트가 길어져도
멈추지 말고 계속 진행한다.
