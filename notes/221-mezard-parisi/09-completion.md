# 9장 Normalization, truncation, and completion of the proof — 문단별 해설

원문: `build/sections/reduction.tex`, PDF 31–32쪽. 번호는 PDF 기준 (Lemma 9.1, 식 (9.1)–(9.3), 정리 2.1의 증명).
앞 장 참조: (2.1)–(2.4), (2.11), (2.12), 명제 4.1, 따름정리 8.4.

정리 2.1의 두 절반은 가정이 다릅니다. 위쪽 한계 (명제 4.1)는 분해 (2.3)·양성 (2.4)와 1차 모멘트를, 아래쪽 한계
(따름정리 8.4)는 유계·순열 불변을 씁니다. 9장은 **상수 이동**과 **절단 근사**로 둘을 잇습니다.

---

## 문단 1. 장 도입

> The lower bound proved in Corollary 8.4 requires bounded permutation-invariant interactions, whereas
> the upper bound uses the factorization and positivity hypotheses. An integrable constant shift and
> uniform approximation connect the two statements.

### 해석

| 반쪽 | 필요한 가정 | 9장의 다리 |
|---|---|---|
| 위 ($\limsup\le$) | (2.1), (2.3), (2.4) | 이미 일반 경우에 증명됨 (4장) |
| 아래 ($\liminf\ge$) | 유계, 순열 불변 | 상수 이동 → 순열 불변; 절단 → 유계; 안정성 Lemma 9.1로 오차 제어 |

---

## 문단 2. Lemma 9.1 (Stability)

> **Lemma 9.1.** Couple two interaction laws $\theta,\theta'$ and two field laws $h,h'$, each satisfying
> (2.1) for the fixed $p$ and $\alpha$, and put $D=\mathbb E\max_s|\theta(s)-\theta'(s)|$ and
> $d=\mathbb E|h-h'|$. Then
> $$|F_N-F_N'|\le\alpha D+d,\tag{9.1}$$
> $$|\mathcal B_r(\zeta,\mathbf m)-\mathcal B_r'(\zeta,\mathbf m)|\le\alpha(2p-1)D+d\tag{9.2}$$
> uniformly in $N,r$ and all trial laws, including $r=0$. If $c$ is an integrable random constant
> associated with an interaction and $\widehat\theta=\theta-c$, then
> $$\widehat F_N=F_N-\alpha\mathbb Ec,\qquad\widehat{\mathcal B}_r=\mathcal B_r-\alpha\mathbb Ec.\tag{9.3}$$

> *Proof.* Use the same counts and indices in the two Hamiltonians. Their pointwise log-weight difference
> is bounded by the sum of the interaction sup-norm differences and field differences. The logarithm of
> the partition function preserves this bound, which gives (9.1). Each cavity interaction changes by at
> most the corresponding sup-norm interaction difference, and so does each edge logarithm. The power means
> preserve these root-measurable bounds. The site term has mean $\alpha p$ interactions and the edge term
> has coefficient $\alpha(p-1)$, giving (9.2).
>
> For (9.3), the physical constants factor out of the spin partition function and of every power mean.
> In the functional, the site term shifts by $-\alpha p\mathbb Ec$ and the edge term contributes
> $+\alpha(p-1)\mathbb Ec$, for a net shift $-\alpha\mathbb Ec$.

### 검증

**(9.1).** 같은 Poisson 개수·자리로 결합. $|{-H_N}(\sigma)-(-H_N'(\sigma))|\le\sum_k\max_s|\theta_k-\theta_k'|+\sum_i|h_i-h_i'|=:\Lambda$
(모든 $\sigma$에서) ⇒ $|\log Z_N-\log Z_N'|\le\Lambda$. $\frac1N\mathbb E\Lambda=\alpha D+d$ (Wald). ✓

**(9.2).** $|U_\theta-U_{\theta'}|\le\max_s|\theta-\theta'|$, $|\log C_\theta-\log C_{\theta'}|\le\max_s|\theta-\theta'|$ (log-sum-exp의 1-Lipschitz성). ✓
power mean은 뿌리 가측 곱셈 한계를 보존 (Lemma 3.1의 단조성·동차성) ⇒
$|\log T_0V_{\rm s}-\log T_0V_{\rm s}'|\le|h-h'|+\sum_{j\le k}\max|\theta_j-\theta_j'|$, 기대값 $d+\alpha pD$;
edge: $\le D$, 계수 $\alpha(p-1)$. 합 $d+\alpha pD+\alpha(p-1)D=\alpha(2p-1)D+d$. ✓ $r$, $\zeta$, $\mathbf m$에 무관. ✓

**(9.3).** $Z_N(\widehat\theta)=e^{-\sum_kc_k}Z_N(\theta)$ ⇒ $\widehat F_N=F_N-\alpha\mathbb Ec$. ✓
$U_{\widehat\theta}=U_\theta-c$, $\widehat V_{\rm s}=e^{-\sum_jc_j}V_{\rm s}$ (상수는 power mean 밖으로) ⇒ $-\alpha p\mathbb Ec$;
$C_{\widehat\theta}=e^{-c}C_\theta$ ⇒ edge 항 $-\alpha(p-1)(-\mathbb Ec)=+\alpha(p-1)\mathbb Ec$. 합 $-\alpha\mathbb Ec$. ✓
($c$는 $\theta$와 상관이 있어도 됩니다 — clause마다 붙은 상수이기만 하면 됨.)

### 물리적 의미

(9.1)–(9.2)는 "상호작용을 조금 바꾸면 pressure도 시험 범함수도 조금만 바뀐다"는 연속성입니다. (9.3)은 각 clause의
**에너지 기준점**을 옮겨도 pressure 밀도가 $\alpha\mathbb Ec$ (clause 밀도 × 평균 이동)만큼 평행 이동한다는 자명한
사실이고, Bethe 장부 $\log2+V_{\rm s}-\alpha(p-1)V_{\rm e}$가 이 이동에 대해 **정확히 같은 양**만큼 움직인다는 점이
중요합니다 (site에서 $p$번, edge에서 $p-1$번 빼므로 순 1번 — 실제 clause 하나에 해당).

---

## 문단 3. 정리 2.1의 증명 ① 승수 $a$ 제거와 순열 불변성

> The multiplier $a$ may depend asymmetrically on the labeled input functions, so the original
> interaction law need not be permutation invariant. We first remove this multiplier by an integrable
> scalar shift. Set $c=\theta(1,\ldots,1)$ and $\widehat\theta=\theta-c$. The constant is integrable, since
> $|c|\le B(\theta)$. The factorization gives
> $$\widehat\theta(s)=\log\frac{1+b\prod_{\ell=1}^pf_\ell(s_\ell)}{1+b\prod_{\ell=1}^pf_\ell(1)}.$$
> The multiplier $a$ has disappeared. Independence and identical distribution of the $f_\ell$, and their
> independence of $b$, show that the law of $\widehat\theta$ is invariant under permutations of its inputs.
> Moreover $\mathbb EB(\widehat\theta)\le2\mathbb EB(\theta)<\infty$.

### 검증

- $\theta(s)-\theta(1..1)=\log a(1+b\prod f_\ell(s_\ell))-\log a(1+b\prod f_\ell(1))$. ✓ $a$ 소거.
- 순열 $\pi$: $\widehat\theta(s_{\pi(1)},\dots,s_{\pi(p)})$는 $(f_{\pi^{-1}(\ell)})$로 쓴 같은 식이고, $(f_1,\dots,f_p)$가 i.i.d.이고 $b$와 독립이므로
  $(b,f_{\pi^{-1}(1)},\dots)\overset{d}=(b,f_1,\dots)$ ⇒ 법칙 불변. ✓
- $B(\widehat\theta)\le B(\theta)+|c|\le2B(\theta)$. ✓

### 검토 메모 — 왜 "대칭화"가 아니라 "이동"인가 (5장 판단의 정정)

5장 문단 2에서 이 해설은 "$\theta$를 무작위 순열로 대칭화해도 일반성을 잃지 않는다"고 적었습니다. 이것은 **$F_N$에
대해서는 맞지만 $\mathcal B_r$에 대해서는 틀릴 수 있습니다.** $U_\theta$ (2.6)는 새 스핀을 마지막 자리에 고정하기 때문입니다.
그래서 논문은 대칭화 대신 상수 이동을 씁니다. 이동은 (9.3)에 따라 $F_N$과 $\mathcal B_r$을 **같은 양** $\alpha\mathbb Ec$만큼
옮기므로 공식의 양변이 함께 움직입니다. 그리고 분해 (2.3) 아래에서는 이동 결과가 자동으로 순열 불변입니다.

**수치 확인 (정확 계산, $r=0$).** $p=2$, $\alpha=0.8$, $h=0.3$, 메시지 점질량 $x_0=0.6$ ($\zeta=\delta_{x_0}$), $K_{\rm s}\le14$ 절단.

| 상호작용 | $\mathcal B_0(\theta)$ | 비교 |
|---|---|---|
| 분해형, 비대칭 승수 $a=e^{0.8f_1(1)}$, $b=\pm0.7$, $f\in\{s,(0.3,0.9)\}$ | 1.1462791053 | $\mathcal B_0(\widehat\theta)+\alpha\mathbb Ec=1.1462791066$ ✓ (차이 $10^{-9}$ = 절단 오차) |
| 같은 것, 입력 순서 교환 $\theta\circ\mathrm{swap}$ | 1.1462791053 | 원래와 같음 ✓ (분해형에서는 자리 무관) |
| 비분해·비대칭 $\theta=0.9s_1s_2+0.7s_1$ | 1.6713776616 | 교환: 1.7018862705, 대칭화 (½–½): 1.6858952678 — **다름** |

마지막 줄이 정정의 근거입니다: 비대칭 상호작용에서 $\mathcal B_0$은 새 스핀이 어느 자리에 들어가는지에 의존하고,
$F_N$은 그렇지 않습니다. 정리 2.1은 분해 가정 아래에서만 주장되므로 논문에는 문제가 없습니다.

---

## 문단 4. 증명 ② 절단과 극한

> For $K>0$, truncate each entry of $\widehat\theta$ to $[-K,K]$ and truncate $h$ to $[-K,K]$, obtaining
> $\widehat\theta^{(K)},h^{(K)}$. Permutation invariance is preserved. The bounded-law lower bound Corollary
> 8.4 applies whether or not truncation preserves the factorization. By dominated convergence,
> $$D_K=\mathbb E\max_s|\widehat\theta(s)-\widehat\theta^{(K)}(s)|\longrightarrow0,\qquad d_K=\mathbb E|h-h^{(K)}|\longrightarrow0.$$
> Write $\widehat I$ for the infimum of the normalized trial functional over all depths and trial laws,
> and $I_K$ for the same infimum with the truncated physical laws. The uniform trial estimate gives
> $|\widehat I-I_K|\le\alpha(2p-1)D_K+d_K$. The pressure estimate and Corollary 8.4 now imply
> $$\liminf_N\widehat F_N\ge I_K-\alpha D_K-d_K\ge\widehat I-2\alpha pD_K-2d_K.$$
> Letting $K\to\infty$ proves $\liminf_N\widehat F_N\ge\widehat I=\inf_r\widehat\Phi_r$. Undoing the constant
> shift gives $\liminf_NF_N\ge\inf_r\Phi_r$. Finally Proposition 4.1 gives $\limsup_NF_N\le\inf_r\Phi_r$.
> Both limits agree, proving existence and (2.13).

### 검증

- 좌표별 절단 $x\mapsto\max(-K,\min(K,x))$은 순열과 교환 ⇒ 순열 불변 유지. ✓ 유계 ⇒ 따름정리 8.4 적용 (분해 불필요). ✓
- $D_K\to0$: $\max_s|\widehat\theta-\widehat\theta^{(K)}|\le B(\widehat\theta)\mathbf1\{B(\widehat\theta)>K\}$, 적분 가능 지배. ✓ $d_K$ 동일. ✓
- (9.2)가 $r$, 시험 법칙에 균등 ⇒ infimum끼리도 $|\widehat I-I_K|\le\alpha(2p-1)D_K+d_K$. ✓
- (9.1): $\widehat F_N\ge F_N^{(K)}-\alpha D_K-d_K$, $\liminf F_N^{(K)}\ge I_K$ (따름정리 8.4). ✓
  합: $\ge\widehat I-\alpha(2p-1)D_K-d_K-\alpha D_K-d_K=\widehat I-2\alpha pD_K-2d_K$. ✓
- $K\to\infty$ ⇒ $\liminf\widehat F_N\ge\widehat I$. (9.3)로 되돌리면 양변에 $\alpha\mathbb Ec$를 더함:
  $\liminf F_N\ge\inf_r\Phi_r$. ✓ ($\widehat\Phi_r=\Phi_r-\alpha\mathbb Ec$, 모든 $r$에 같은 상수.)
- 명제 4.1 (원래 $\theta$, (2.1)(2.3)(2.4)) ⇒ $\limsup F_N\le\inf_r\Phi_r$. $\liminf=\limsup$ ⇒ 극한 존재, (2.13). ✓

**검토 메모.** 위쪽 한계는 이동하지 않은 원래 $\theta$에 대해 직접 적용합니다 (명제 4.1은 $a$의 적분 가능성을 요구하지
않도록 이미 정규화를 내장). 아래쪽 한계는 $\widehat\theta$에 대해 증명하고 (9.3)으로 되돌립니다. 두 결과 모두 같은 $\Phi_r$
(원래 $\theta$의 범함수)에 대한 것이므로 맞물립니다. ✓

### 물리적 의미

결론: 짝수 $p$, (2.1)(2.3)(2.4)를 만족하는 희석 스핀 글라스 (Viana–Bray, 희석 $p$-spin, 그 밖의 분해형 모형)에서
$$\lim_{N\to\infty}\frac1N\mathbb E\log Z_N=\inf_{r\ge0}\inf_{\zeta,\mathbf m}\Bigl[\log2+\mathbb E\log T_0V_{\rm s}-\alpha(p-1)\mathbb E\log T_0V_{\rm e}\Bigr].$$
Mézard–Parisi (2001)의 RSB cavity 공식이 **모든 유한 단계 RSB 시험의 infimum**으로서 엄밀하게 성립합니다. 무거운 꼬리
결합 (1차 모멘트만 유한)도 포함됩니다.

---

## 요약

- Lemma 9.1: 결합 상호작용의 sup-norm 차이 $D$, 장 차이 $d$에 대해 $|F_N-F_N'|\le\alpha D+d$, $|\mathcal B_r-\mathcal B_r'|\le\alpha(2p-1)D+d$;
  상수 이동은 양쪽을 $\alpha\mathbb Ec$만큼 같이 옮김 (9.3).
- $\widehat\theta=\theta-\theta(1..1)$은 $a$를 지우고 분해 덕분에 순열 불변. 절단 + 따름정리 8.4 + 안정성으로 아래쪽 한계, 명제 4.1로
  위쪽 한계, 따라서 정리 2.1.
- 수치로 (9.3)과 "분해형에서는 자리 순서 무관, 비분해 비대칭에서는 $\mathcal B_0$이 자리 순서에 의존"을 확인하고, 5장의 판단
  메모를 정정했습니다.

**다음 절 예고**: 10장에서 Viana–Bray, 희석 $p$-spin 등 이름 있는 모형에 정리를 적용하고 영온도 극한을 다룹니다.
