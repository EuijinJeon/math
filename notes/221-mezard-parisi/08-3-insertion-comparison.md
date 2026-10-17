# 8.3 Comparison of the insertion logarithms — 문단별 해설

원문: `build/sections/comparison.tex` 8.3절, PDF 30–31쪽. 번호는 PDF 기준 (명제 8.3, 식 (8.6), 따름정리 8.4).
앞 절 참조: Lemma 5.1 (5.5)–(5.7), Lemma 8.1, Lemma 8.2, (8.4), Lemma 3.2 (3.9)(3.10), (2.8)–(2.12).

아래쪽 한계의 마지막 조각입니다. 저장소 삽입 로그를 시험 삽입 로그로 바꾸고, 그 결과가 정확히 $\mathcal B_{L-1}$임을
확인합니다.

---

## 문단 1. 명제 8.3

> **Proposition 8.3.** For the trial laws of Lemma 8.1, with $\mathbf m^{(L)}=(1/L,\ldots,(L-1)/L)$,
> $$\lim_{L\to\infty}\limsup_{N\to\infty}\left|\Delta_N^{L,\mathbf u_{L,N}}-\mathcal B_{L-1}(\zeta_{L,N},\mathbf m^{(L)})\right|=0.\tag{8.6}$$

### 해석

$\mathbf m^{(L)}$은 (5.1)의 균등 격자 ($m_0=0$, $m_L=1$ 제외). $r=L-1$단 시험 법칙 $\zeta_{L,N}\in\mathcal M_L$과 함께
허용 시험 법칙입니다 ($0<m_1<\dots<m_r<1$ ✓). 명제는 "ASS 증분 = 부호화된 시험 법칙의 Bethe 범함수 + 작은 오차".

---

## 문단 2. 증명 ① 시험 삽입과 정확한 항등식

> For each insertion in Lemma 5.1, replace the reservoir spins at its site labels by independent spin
> processes from Lemma 8.1. Denote the resulting trial insertions by $\widetilde A_{\rm s}$ and
> $\widetilde A_{\rm b}$, and their recursions from (3.3) by $\widetilde Y_{0,\rm s}$ and
> $\widetilde Y_{0,\rm b}$. These recursions use the trial kernels.
>
> At the terminal spin transition, averaging $\widetilde A_{\rm s}$ over its independent trial spins gives
> exactly $V_{\rm s}$ in (2.8); hence $\widetilde Y_{0,\rm s}=T_0V_{\rm s}$. For $\widetilde A_{\rm b}$ the
> same transition gives a product of $K_{\rm b}$ edge factors with disjoint message labels. Given the
> physical disorder and all message prefixes at a depth, these label groups remain independent. Their
> product therefore factors through each conditional power mean, successively from the last level to
> the first. Consequently,
> $$\mathbb E\log\widetilde Y_{0,\rm b}=\alpha(p-1)\mathbb E\log T_0V_{\rm e},\qquad
> \log2+\mathbb E\log\widetilde Y_{0,\rm s}-\mathbb E\log\widetilde Y_{0,\rm b}=\mathcal B_{L-1}(\zeta_{L,N},\mathbf m^{(L)}).$$
> By (5.5), it remains to compare the reservoir and trial insertion logarithms in the stated limits.

### 검증

- **site**: 시험 스핀 $\tau_\ell\sim q_{x_\ell}$ 독립이면
  $\mathbb E_\tau e^{\theta(\tau_1,\dots,\tau_{p-1},\varepsilon)}=\sum_se^{\theta(s,\varepsilon)}\prod_\ell q_{x_\ell}(s_\ell)=e^{U_\theta(x;\varepsilon)}$ (2.6).
  clause마다 라벨이 다르므로 곱이 인수분해 ⇒ $\frac12\sum_\varepsilon e^{h\varepsilon+\sum_jU_{\theta_j}}=V_{\rm s}$ (2.8). ✓
  마지막 전이 ($m_L=1$)가 이 평균이고, 그 위의 재귀는 메시지 사슬에 대한 power mean (2.10) ⇒ $\widetilde Y_{0,\rm s}=T_0V_{\rm s}$. ✓
- **bond**: 같은 방식으로 $\prod_{j\le K_{\rm b}}C_{\theta_j}(x^j_1,\dots,x^j_p)$. 서로소인 라벨 묶음은 각 깊이에서 조건부 독립이므로
  $\mathbb E[(\prod_jV_j)^m\mid\cdot]=\prod_j\mathbb E[V_j^m\mid\cdot]$ ⇒ $T_0\prod_j=\prod_jT_0$. ✓
  $\mathbb E\log\widetilde Y_{0,\rm b}=\mathbb E\sum_{j\le K_{\rm b}}\log T_0V_{\rm e}^{(j)}=\mathbb EK_{\rm b}\cdot\mathbb E\log T_0V_{\rm e}=\alpha(p-1)\mathbb E\log T_0V_{\rm e}$ (Wald, (2.12)로 적분 가능). ✓
- 합치면 (2.11)의 $\mathcal B_{L-1}$. ✓ (5.5)와 빼면 남는 것은
  $|\mathbb E\log Y_{0,\rm s}-\mathbb E\log\widetilde Y_{0,\rm s}|+|\mathbb E\log Y_{0,\rm b}-\mathbb E\log\widetilde Y_{0,\rm b}|$.

### 수치 확인 (power mean의 인수분해)

$r=2$ ($m_1=0.3$, $m_2=0.7$), 라벨 3개 (각자 무작위 2단 사슬), 양의 함수 $f_1,f_2,f_3$:
$T_0(f_1f_2f_3)=0.79356490997383$, $\prod_kT_0f_k=0.79356490997383$. ✓

### 물리적 의미

시험 쪽에서는 Mézard–Parisi cavity 계산이 **정확히** 성립합니다: 새 스핀의 이웃들은 독립 메시지를 보내고, 자유에너지
증분이 Bethe 범함수가 됩니다. 남은 일은 "저장소의 실제 이웃 스핀들 ≈ 독립 메시지"라는 근사의 오차를 재는 것입니다.

---

## 문단 3. 증명 ② 개수 절단과 로그 전개

> Consider either insertion and first restrict its Poisson count $K$ to $K\le M$, where $M$ is fixed. Set
> $C=H+BM$, $z=\cosh C$, and $c=\tanh C<1$. On this event both the reservoir insertion and its trial
> version can be written as $A=z(1+D)$ with $|D|\le c$, uniformly in all disorder and path variables. The
> deterministic term $\log z$ cancels in the comparison.
>
> At each order $k$ of Lemma 3.2, the product of the $k$ copies of $D$ is a bounded function of
> replica-spin patterns at at most $pM$ labels and of independent insertion disorder. By Lemma 8.2, its
> evaluation error on a fixed tree is bounded by $pM\sum_{S\ne\varnothing}\mathbb E|R_S-\mathbb ER_S|$.
> Hence (8.4) makes its tree-averaged error tend to zero in the ordered limits. For every fixed $M$,
> truncating the expansion after $q$ terms leaves an error at most $\sum_{k>q}c^k/k$ on either side,
> uniformly in $N,L$.

### 검증

- $K\le M$이면 $|\log A|\le H+BK\le C$ ⇒ $A\in[e^{-C},e^C]$. $e^{\pm C}=\cosh C(1\pm\tanh C)$이므로
  $A=z(1+D)$, $|D|\le\tanh C=c<1$. ✓ (수치: $C=0.5,2,5$에서 항등식 오차 $\le2\times10^{-15}$, $c=0.462,0.964,0.9999$.)
- $\log Y_0(A)=\log z+\log Y_0(1+D)$ (동차성), $\log z$는 양쪽 같음. ✓
- Lemma 3.2: $\log Y_0(1+D)=\sum_k\frac{(-1)^{k-1}}k\mathbb E_{Q_k}E_{\mathcal T}\prod_{a\le k}D^a$, 꼬리 $\le\sum_{k>q}c^k/k$ (3.10),
  커널에 균등 ⇒ $N,L$에 균등. ✓
- $k$차 항의 $\prod_aD^a$: 삽입이 읽는 자리 $\le pM$개 (site: $(p-1)K_{\rm s}$, bond: $pK_{\rm b}$)의 $k$-replica 패턴과 새 무질서의
  유계 함수 ($|D|\le c<1$). 저장소 쪽은 균등 자리 패턴, 시험 쪽은 독립 시험 라벨 패턴 ⇒ Lemma 8.2로 오차
  $\le pM\sum_S\mathbb E|R_S-\mathbb ER_S|$ (나무 고정). $Q_k$로 평균 ⇒ (8.4)로 $\lim_L\limsup_N=0$. ✓

**검토 메모.** 저장소 쪽 항은 저장소 커널의 나무 $E_{\mathcal T}$, 시험 쪽 항은 **시험 커널**의 나무입니다. 두 나무 법칙이
"한 자리 패턴" 수준에서 같다는 것이 Lemma 8.1이고, 자리 여러 개에서의 차이가 Lemma 8.2입니다. 또 $Q_k$는 두 쪽에서
같습니다 (같은 $\mathbf m$). ✓ 한편 Lemma 8.2는 "자리 패턴들의 결합 법칙"만 비교하므로, 저장소 쪽에서 삽입 자리들이
**복원 추출**로 같은 자리를 반복할 수 있다는 점도 $\pi^{\otimes a}$에 포함되어 있습니다. ✓

---

## 문단 4. 증명 ③ 꼬리와 극한 순서

> Outside the count cutoff the original insertion logarithms, on both sides, are bounded by $H+BK$.
> Their expected contribution is therefore at most $2\mathbb E[(H+BK)\mathbf 1_{\{K>M\}}]$, which tends to
> zero as $M\to\infty$. This proves convergence of the expected insertion logarithms: explicitly, first
> choose $M$ to control the Poisson tail, then $q$ to control the geometric tail, and then take the
> limits in $N$ and $L$ for the finitely many remaining expansion terms. Together with the trial
> identities above and (5.5), this proves (8.6).

### 검증

$|\log Y_0|\le H+BK$ (5장 문단 8). $\mathbb E[(H+BK)\mathbf1_{K>M}]\to0$ (Poisson의 1차 모멘트 유한). ✓ 순서:
$M$ (Poisson 꼬리) → $q$ (기하 꼬리, $c$가 $M$에 의존) → 유한 개 항에 대해 $N$, $L$ 극한. ✓

### 수치 예 (Poisson 꼬리)

$H=B=1$, $\mathbb EK=4$ (예: $\alpha p=4$)일 때 $2\mathbb E[(H+BK)\mathbf1_{K>M}]$:

| $M$ | 5 | 10 | 15 | 20 | 30 |
|---|---|---|---|---|---|
| 꼬리 비용 | 3.40 | $7.1\times10^{-2}$ | $1.7\times10^{-4}$ | $8.6\times10^{-8}$ | $7.5\times10^{-16}$ |

$M$을 키우면 $c=\tanh(H+BM)\to1$이 되어 필요한 $q$가 커지지만, $M$을 먼저 고정하므로 문제 없습니다.

---

## 문단 5. 따름정리 8.4 (유계 모형의 아래쪽 한계)

> **Corollary 8.4.** For every bounded permutation-invariant interaction law and bounded field law, with
> the functionals defined in Section 2, $\liminf_{N\to\infty}F_N\ge\inf_{r\ge0}\Phi_r$.

> *Proof.* Write $A=\inf_{r\ge0}\Phi_r$, which is finite by (2.12). Each encoded trial value is at least
> $A$, so (8.1) gives, at every fixed $L$,
> $$A\le\underline F+2\varepsilon+\limsup_{N\to\infty}\left|\Delta_N^{L,\mathbf u_{L,N}}-\mathcal B_{L-1}(\zeta_{L,N},\mathbf m^{(L)})\right|.$$
> The inner limit uses that depth's selected sequence. Letting $L\to\infty$ in Proposition 8.3 gives
> $A\le\underline F+2\varepsilon$, and then $\varepsilon\downarrow0$ proves the result.

### 검증

- $A$ 유한: (2.12)로 $|\mathcal B_r|\le\log2+H+\alpha pB+\alpha(p-1)B$, 모든 $r$에 균등. ✓
- $A\le\Phi_{L-1}\le\mathcal B_{L-1}(\zeta_{L,N},\mathbf m^{(L)})\le\Delta_N+|\Delta_N-\mathcal B_{L-1}|\le\underline F+2\varepsilon+|\cdots|$ (8.1). ✓
  $\limsup_N$ (그 $L$의 수열) → $L\to\infty$ (8.6) → $\varepsilon\downarrow0$. ✓
- 쓰인 가정: 유계 $\theta$, $h$; 순열 불변 (5장 문단 6). (2.3), (2.4)는 쓰지 않음 (5장 문단 2). ✓

### 물리적 의미

$\underline F\ge\inf_r\Phi_r$: 실제 pressure는 어떤 유한 RSB 시험 범함수의 infimum보다 작지 않습니다. 4장의 위쪽 한계와
합치면 (유계 경우) $\lim F_N=\inf_r\Phi_r$ — **Mézard–Parisi 공식**. 증명이 실제로 만든 시험 법칙은 저장소에서 읽어 낸
$\zeta_{L,N}$이며, 이것이 "물리적으로 올바른 order parameter"의 근사입니다. 최적 시험 법칙의 존재나 무한 깊이 극한은
필요하지 않습니다.

---

## 요약

- 시험 삽입에서는 cavity 계산이 정확: $\widetilde Y_{0,\rm s}=T_0V_{\rm s}$, $\mathbb E\log\widetilde Y_{0,\rm b}=\alpha(p-1)\mathbb E\log T_0V_{\rm e}$,
  따라서 $\log2+\dots=\mathcal B_{L-1}$. power mean 인수분해를 수치로 확인.
- 저장소 ↔ 시험 비교: 개수 절단 $K\le M$, $A=\cosh C(1+D)$, 로그 전개의 각 차수에 Lemma 8.2 + (8.4), 기하 꼬리.
- 명제 8.3: $\lim_L\limsup_N|\Delta_N-\mathcal B_{L-1}(\zeta_{L,N},\mathbf m^{(L)})|=0$.
- 따름정리 8.4: 유계·순열 불변 모형에서 $\liminf F_N\ge\inf_r\Phi_r$.

**다음 절 예고**: 9장에서 순열 불변 정규화, 상호작용 절단으로 유계 가정을 (2.1)의 1차 모멘트로 완화하고 정리 2.1의
증명을 완성합니다.
