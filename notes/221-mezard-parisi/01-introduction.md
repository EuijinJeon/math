# 1장 Introduction — 문단별 해설

원문: `build/sections/introduction.tex`, PDF 1–2쪽. 서론에는 번호 붙은 식이 없습니다. 뒤 장 번호는 PDF 기준입니다.

서론은 (i) 문제 설정, (ii) 선행 연구와 이 논문이 푼 추측, (iii) 다른 변분 공식들과의 관계, (iv) 증명의 핵심 난점을
소개합니다. 수학적 주장은 2장 이후에 정확히 진술되므로, 여기서는 물리적 그림과 용어를 정리하는 데 집중합니다.

---

## 문단 1. 희석 스핀 글라스와 pressure

> A diluted spin glass has a finite mean number of interactions per spin. Its local environment remains
> random as the system grows, and the cavity method describes that environment through a distribution of
> local fields. When many competing states contribute to the partition function, the proposed order
> parameter is a hierarchy of distributions of these fields. The thermodynamic question is whether this
> hierarchy determines the limiting expected log partition function per spin. We call this quantity
> *pressure*. At inverse temperature $\beta$, the usual physical free energy per spin is its negative
> divided by $\beta$.

### 해석

| 용어 | 의미 |
|---|---|
| diluted (희석) | 스핀당 상호작용 수가 $N$과 무관한 유한 평균 ($\alpha p$). 그래프가 국소적으로 나무 같음 |
| local environment | 한 스핀 주변의 유한 반경 이웃. $N\to\infty$에서도 무작위로 남음 (SK와 다른 점) |
| cavity method | 스핀 하나를 빼고 이웃이 보내는 "국소장(메시지)"의 분포로 계를 기술 |
| hierarchy of distributions | RSB: 상태(cluster)들 위의 장 분포, 그 분포들의 분포, … (2장 (2.7)의 $\mathcal M_{r+1}$) |
| pressure | $\lim\frac1N\mathbb E\log Z_N$. 자유에너지 밀도는 $f=-\text{pressure}/\beta$ |

### 물리적 의미

SK 모형 (완전 연결)에서는 국소장이 중심극한정리로 가우스가 되므로 order parameter가 overlap 분포 $q(x)$ 하나로
충분합니다. 희석 모형에서는 각 스핀이 유한 개 이웃만 보므로 국소장 분포가 가우스가 아니고, **분포 자체가 order
parameter**가 됩니다. RSB가 일어나면 이것이 "분포의 분포의 …"라는 위계로 커집니다 (Mézard–Parisi 2001의
함수형 order parameter). 이 논문의 질문은 "그 위계가 정말로 pressure를 결정하는가"입니다.

---

## 문단 2. 선행 연구

> The Viana–Bray model is a classical diluted two-spin model [VB85]. Mézard and Parisi [MP01] developed
> the hierarchical cavity picture for the fixed-connectivity Bethe-lattice spin glass, with an explicit
> one-step replica-symmetry-breaking functional. Franz and Leone [FL03] adapted Guerra's interpolation
> method [Guerra03] to diluted systems and obtained replica-symmetric and one-step pressure bounds for
> even-arity models. Panchenko and Talagrand [PT04] then proved the arbitrary finite-level hierarchical
> upper bounds considered here.

### 해석 — 역사 정리

| 연도·저자 | 기여 | 이 논문에서의 위치 |
|---|---|---|
| Viana–Bray 1985 | 희석 2-spin 모형 정의 | 따름정리 10.1의 대표 예 |
| Mézard–Parisi 2001 | Bethe 격자 스핀 글라스의 위계적 cavity 그림, 1RSB 범함수 | 공식의 이름 |
| Guerra 2003 | SK에서 보간으로 Parisi 공식의 위쪽 한계 | 4장 방법의 원형 |
| Franz–Leone 2003 | 희석 모형의 RS·1RSB 위쪽 한계 (짝수 arity) | 4장 |
| Panchenko–Talagrand 2004 | 임의 유한 단계 RSB 위쪽 한계 | 4장 명제 4.1이 재현·일반화 |

즉 **위쪽 한계는 이미 알려져 있었고**, 이 논문의 새 내용은 아래쪽 한계 (등호)입니다.

---

## 문단 3. 주 결과와 해결한 추측

> We prove that the infimum of these bounds is the limiting pressure. This resolves the equality
> conjecture stated immediately after Theorem 4 of Panchenko–Talagrand [PT04], for their Poisson,
> even-arity Ising model class with factorized interactions and the specified positivity condition. Only
> first moments of the interaction and external field are required. The result includes the Viana–Bray
> model, diluted even-spin models with symmetric couplings, and soft random even-$K$ SAT at every positive
> temperature. The exact model and trial functional are defined in Section 2; the named models and their
> expected ground-state limits are treated in Section 10.

### 해석

- 주 결과: $\lim F_N=\inf_r\Phi_r$ (정리 2.1, (2.13)). 극한의 **존재**도 결과의 일부입니다 (희석 모형에서는 sub-additivity로
  존재가 알려진 경우도 있지만, 여기서는 위·아래 한계가 일치해서 따라 나옴).
- 범위: Poisson clause 수, 짝수 arity $p$, Ising 스핀, 분해형 상호작용 (2.3), 양성 (2.4). 상호작용과 장은 **1차 모멘트만**.
- 예: Viana–Bray, 대칭 결합 희석 $p$-spin, soft 짝수 $K$-SAT (모든 양의 온도). 10장에서 영온도 극한까지.

### 물리적 의미

물리학자의 "Mézard–Parisi 공식"이 희석 모형에서 엄밀하게 성립한다는 첫 일반적 증명입니다. 다만 공식은 **유한 단계
RSB들의 infimum** 형태이고, full-RSB 극한 대상이나 최적 시험 법칙의 존재는 주장하지 않습니다.

---

## 문단 4. 다른 변분 공식들과의 관계

> An exact variational description and reduction to a prescribed trial class are distinct problems. The
> cavity variational principle of Aizenman, Sims and Starr [ASS03] for the Sherrington–Kirkpatrick model
> has a Viana–Bray counterpart in De Sanctis's formulation over random multioverlap structures
> [DeSanctis04]. Panchenko's spin-distribution approach [Pan13, Theorems 1–2] gives an exact variational
> formula over invariant exchangeable spin distributions. Under their positivity condition,
> Coja-Oghlan and Perkins [COP19] obtain an invariant-kernel variational formula for random regular
> factor graphs. These results use different descriptions of the state from the finite hierarchy of
> message laws optimized here. The additional task is to recover the specific hierarchical cavity
> functional without losing the pressure.

### 해석

두 종류의 문제를 구분합니다.
1. **어떤** 정확한 변분 공식이 존재하는가 — ASS, De Sanctis, Panchenko 2013, Coja-Oghlan–Perkins가 이미 답함.
   다만 그 공식들의 변수는 "무작위 multi-overlap 구조", "교환 가능한 스핀 분포", "불변 커널" 같은 일반적 대상입니다.
2. 그 infimum을 **특정한 시험 족** (유한 위계 메시지 법칙, Mézard–Parisi/Panchenko–Talagrand 범함수)으로 줄여도
   값을 잃지 않는가 — 이 논문의 과제.

### 물리적 의미

물리적으로는 "정확한 자유에너지는 어떤 상태 기술의 최적화로 주어진다"는 것과 "Parisi형 위계 ansatz면 충분하다"는 것이
다른 주장이라는 뜻입니다. SK에서 Parisi 공식의 증명 (Talagrand 2006, Panchenko의 ultrametricity)이 바로 둘째 종류였습니다.

---

## 문단 5. 더 가까운 결과들

> Panchenko [Pan16, Theorem 2] established a hierarchical single-site representation for finite-RSB
> asymptotic Gibbs measures of suitably modified models; approximation of general states by that class
> remains a separate step. Biswas, Chen and Sen [BCS25, Theorem 1.1 and Proposition 1.4] obtain exact
> replica-symmetric pressure formulas in high-temperature and critical or subcritical regimes for compact
> real spin spaces under moment and regularity assumptions. For the zero-field Ising spin glass with
> Rademacher couplings on random regular graphs, Concetti [Concetti25, Theorem 1.3] gives a
> full-replica-symmetry-breaking pressure bound no larger than each optimized finite-level bound;
> equality with that functional is conjectural in that work. The result here identifies the finite-depth
> Panchenko–Talagrand infimum at arbitrary density in its stated interaction class.

### 해석

| 결과 | 한계 |
|---|---|
| Panchenko 2016 | Gibbs 측도가 이미 유한 RSB이면 위계적 한-자리 표현이 있음. 일반 상태의 근사는 별개 |
| Biswas–Chen–Sen 2025 | RS 공식, 고온·임계 이하 영역에서만 |
| Concetti 2025 | 무작위 정규 그래프, full-RSB 위쪽 한계 (유한 단계보다 작거나 같음). 등호는 추측 |

이 논문: 밀도 $\alpha$ 제한 없이 (임의 밀도), 해당 상호작용 족 전체에서 유한 깊이 infimum이 정답.
8장의 부호화 (Lemma 8.1)는 Panchenko 2016의 "한-자리 위계 표현"을 **유한 $N$, 유한 깊이에서 직접** 만드는 것으로
볼 수 있습니다.

---

## 문단 6. 핵심 난점: multi-overlap

> The main obstacle is the distribution of spins seen across several replicas, that is, several samples
> from the same Gibbs system. The probability of each replica-spin pattern depends on products of every
> subset of those spins. The spatial average of such a product is a *multioverlap*; pair overlaps alone
> do not determine all these patterns. This is the information isolated by the spin-distribution approach
> [Pan13]. To compare a cavity insertion with independent hierarchical messages, we must control all
> finite multioverlaps before redrawing the message roots independently.

### 해석

replica $k$개를 한 자리에서 보면 패턴 $(\sigma_i^1,\dots,\sigma_i^k)\in\{\pm1\}^k$가 나오고, 그 경험 분포는 Walsh 전개로
$$\pi(\boldsymbol e)=2^{-k}\sum_{S\subseteq[k]}R_S\prod_{b\in S}e_b,\qquad R_S=\frac1N\sum_i\prod_{a\in S}\sigma_i^a$$
입니다 (8.2절 Lemma 8.2에서 그대로 씀). pair overlap $R_{\{a,b\}}$만으로는 $|S|\ge3$ 계수가 정해지지 않습니다.

### 작은 예

$k=3$이고 자리마다 패턴이 $\{(+,+,+),(+,-,-),(-,+,-),(-,-,+)\}$에서 균등하게 나오는 경우와, 8개 패턴 전체에서 균등하게
나오는 경우를 비교해 보면, 둘 다 모든 $R_{\{a\}}=0$, $R_{\{a,b\}}=0$이지만 앞의 경우 $R_{\{1,2,3\}}=1$, 뒤의 경우 $0$입니다.
pair overlap이 같아도 패턴 분포가 다를 수 있다는 가장 단순한 예입니다. (Walsh 전개에 대입하면 바로 확인됩니다.)

### 물리적 의미

SK에서는 가우스성 덕분에 pair overlap이 모든 것을 결정하지만, 희석 모형에서 cavity 장의 분포는 이웃 스핀들의 **모든
고차 상관**에 의존합니다. 그래서 7장 정리 7.1이 pair overlap이 아니라 **모든 유한 multi-overlap**의 집중을 증명해야 합니다.

---

## 문단 7. 방법의 개요

> We work with finite auxiliary hierarchies before taking the thermodynamic limit. Their branching is part
> of the construction; no ultrametric organization of the physical Gibbs states is assumed. Bounded
> perturbations yield identities for prescribed replica branching patterns. Delaying each branching depth
> by one level permits an induction that concentrates multioverlaps *on average over branching depths*.
> The cavity insertion itself has an expansion averaging over finite trees, so this averaged control is
> sufficient. The system size tends to infinity at each fixed depth; only then does the depth increase.
> The proof strategy following Theorem 2.1 explains how the finite-tree calculus, concentration and
> independent-message comparison fit together.

### 해석

| 서론의 문장 | 해당 장 |
|---|---|
| 유한 보조 위계를 먼저 도입, 위계의 갈라짐은 구성의 일부 | 3장 (path kernel), 5장 (섭동이 보조 변수를 가짐) |
| 물리적 Gibbs 상태의 초계량성은 가정하지 않음 | 전체 — Panchenko식 "GG ⇒ ultrametricity" 경로를 쓰지 않음 |
| 유계 섭동 → 지정한 가지 패턴의 항등식 | 6장 정리 6.5 |
| 갈라짐 깊이를 한 칸 늦춰 귀납, 깊이 평균으로 집중 | 7장 |
| 삽입 전개가 유한 나무 평균이므로 평균 제어로 충분 | 3장 Lemma 3.2, 8.2절 (8.4) |
| $N\to\infty$ 먼저, 그다음 깊이 $L\to\infty$ | 6.3절 이후의 극한 순서 |

### 물리적 의미

물리의 replica 계산에서 Parisi 위계는 ansatz로 **가정**되지만, 여기서는 보조 변수로 위계를 **인공적으로 만들고**,
섭동이 실제 Gibbs 측도를 그 위계에 맞추도록 강제합니다. 초계량성은 결과로도 증명하지 않으며, 필요한 것은 깊이 평균한
multi-overlap 집중뿐입니다.

---

## 요약

- 희석 스핀 글라스의 order parameter는 국소장 분포의 위계이고, 질문은 그 위계의 Mézard–Parisi/Panchenko–Talagrand
  범함수가 pressure를 정확히 주는가입니다.
- 위쪽 한계는 Franz–Leone, Panchenko–Talagrand가 이미 증명했고, 이 논문은 등호 (PT04의 추측)를 1차 모멘트 가정만으로 증명합니다.
- 다른 정확한 변분 공식들과 달리 특정 유한 위계 시험 족으로의 환원이 핵심입니다.
- 난점은 pair overlap이 아닌 모든 multi-overlap의 제어이며, 깊이를 한 칸 늦추는 귀납과 깊이 평균으로 해결합니다.

**다음 절 예고**: 2장에서 모형, 가정 (2.1)–(2.4), cavity 범함수 $\mathcal B_r$과 정리 2.1을 정확히 정의합니다.
