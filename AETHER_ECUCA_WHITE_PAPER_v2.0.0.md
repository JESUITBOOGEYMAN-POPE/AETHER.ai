# AETHER v1.4.0: Formal Algorithms, Provenance Calculus, and Quadrature Energy Governance by ECUCA v2.0.0

**Author:** William Brian Pope  
**Role:** Sole Author; Program Inventor and Engineer  
**Correspondence:** aether.ai@yahoo.com  
**Public reference repository:** `JESUITBOOGEYMAN-POPE/AETHER.ai`  
**Version:** 2.0.0  
**Date:** 2026-11-26  
**Target arXiv categories:** `cs.AI`, `cs.LG`, `physics.gen-ph`  
**Status:** Peer-review submission draft

---

## Abstract

AETHER is an offline-first epistemic discovery architecture that couples a provenance calculus, a family of bounded signal-processing algorithms, and an externally positioned orthogonal governor. This paper gives the formal foundations of AETHER v1.4.0 and the ECUCA v2.0.0 quadrature governor. Six algorithms are specified and analyzed: the Millivoltage Synaptic Voltage Consumption Corollary (MSVSC), Coherent Recursive Fractal Entropy (CRFE), the Neural Provenance Drift Anticipator (NPDA), Discovery Intelligence Provenance (DIP), Emergent Novel Discovery Provenance (ENDP), and the ECUCA quadrature governor. We supply definitions, algebraic expressions, pseudocode, boundedness results, thermodynamic-style inequalities, decidability results, concentration bounds, and worked numerical demonstrations computed from the certified implementation. We formalize ECUCA as a 90-degree rotated quadrature sibling governor that measures the real component of the complex phasor lag-one product while the AETHER shell measures the imaginary component. Exact decomposition, orthogonality, and fail-closed launch properties are proved. The implementation passes a fresh full suite of 474 tests with 0 failures, 0 errors, and 2 skips; the desktop application launches with the expected window title; and the C: integrity manifest verifies as `INTEGRITY_OK` over 204 files. All novelty claims are explicitly scoped as **novel within this architecture**; no claim of global mathematical, biological, or physical priority is made.

**Keywords:** provenance calculus, epistemic governance, fractal entropy, drift anticipation, Landauer bound, quadrature governor, orthogonal control, offline discovery systems, auditable AI

---

## 1. Introduction

### 1.1 Scope and qualification

This paper is a formal description of a computational architecture. It is not a biological measurement, clinical instrument, or claim of new physical law. Every defined quantity is computable from finite, deterministic program state. Where thermodynamic language is used, it is used under explicit assumptions that map an abstract activation threshold to an information-theoretic erasure cost.

The term **novel** is used only in the restricted sense of *novel within this architecture*: the constructions are new relative to the prior components of AETHER and are introduced here with self-contained definitions. They are not asserted to be unprecedented in the literature.

This paper supersedes the v1.0 quick-reference draft `AETHER_White_Paper_v1.0.md`. Where that draft used compressed or aspirational notation, the present paper uses the exact deployed definitions. In particular:

- MSVSC IER is a logistic normalization, not a raw ratio.
- CRFE uses a clamped base and an `at_critical_edge` band narrower than the proximity support.
- NPDA has explicit Kalman, normalization, and alert rules.
- ENDP uses token-level 4-grams and the novelty predicate `nu > 0.35`.
- DIP chain links use truncated SHA-256 fingerprints, not a global chain hash.
- The v1.0 statement “140 AETHER tests pass” is updated to the certified fresh suite of 474 tests.

### 1.2 Contributions

This paper contributes:

1. A formal provenance score, DIP, with bounded components and a probabilistic chain-fingerprint result.
2. A deterministic novelty score, ENDP, with Jaccard identities and a finite-vocabulary concentration bound.
3. A Kalman-inspired drift anticipator, NPDA, with gain validity, bounded health signals, and decidable alerts.
4. A recursive fractal-entropy measure, CRFE, with boundedness and critical-region optimality results.
5. A threshold-activation energy model, MSVSC, with a conditional Landauer-style lower-bound corollary.
6. A rigorous quadrature-governor theorem showing that ECUCA and the AETHER shell measure orthogonal components of the same complex phasor product.
7. A fail-closed launch composition theorem for the integrity preflight, governor gate, and shell.
8. Formalizations and explicit qualifications of the five mechanisms and five observed patterns listed in the v1.0 draft.
9. Reproducibility evidence from the certified v1.4.0 program.

### 1.3 Paper organization

Section 2 fixes notation. Section 3 states architectural invariants. Sections 4–8 define MSVSC, CRFE, NPDA, DIP, and ENDP. Section 9 formalizes ECUCA. Section 10 expands the associated concepts from the v1.0 draft. Section 11 gives verification evidence; Section 12 states limitations; Section 13 concludes.

---

## 2. Notation and Preliminaries

Let `[n] = {1,2,...,n}`. Let

$$
\operatorname{clamp}_{[a,b]}(x)=\min(b,\max(a,x)),
\qquad
\operatorname{clamp01}(x)=\operatorname{clamp}_{[0,1]}(x).
$$

Let `|S|` denote the cardinality of a finite set `S`. For a complex number `w=a+ib`, write `Re(w)=a`, `Im(w)=b`, and `\bar w=a-ib`. For two complex phasors `z_t,z_{t+1}`, define the lag-one product

$$
w_t \equiv \bar z_t z_{t+1}.
$$

All logarithms are natural unless explicitly marked `log2`. All scores are finite-precision computable quantities.

**Definition 2.1 (Bounded score).** A map `s:X -> [0,1]` is a bounded score.

**Definition 2.2 (Token n-gram set).** Let `tok(A)` be the sequence obtained from text `A` by lowercasing and extracting regex tokens `[a-z0-9]+`. The token `n`-gram set is

$$
G_n(A)=
\begin{cases}
\varnothing, & tok(A)=\varnothing,\\
\{\,(tok_i,\dots,tok_{i+n-1}) : 1\le i\le |tok(A)|-n+1\,\}, & |tok(A)|\ge n,\\
\{\,(tok_1,\dots,tok_{|tok(A)|})\,\}, & 0<|tok(A)|<n.
\end{cases}
$$

For the deployed ENDP engine, `n=4`.

**Definition 2.3 (Jaccard similarity).** For finite sets `A,B`,

$$
J(A,B)=
\begin{cases}
0, & A=\varnothing \text{ or } B=\varnothing,\\
\dfrac{|A\cap B|}{|A\cup B|}, & \text{otherwise}.
\end{cases}
$$

**Definition 2.4 (Provenance link).** A provenance link is a tuple

$$
\ell_j=(\text{step}_j,\text{agent}_j,\text{op}_j,\phi^{in}_j,\phi^{out}_j,\tau_j,\gamma_j,R_j,a_j,s_j),
$$

where `\phi^{in}_j,\phi^{out}_j` are truncated SHA-256 fingerprints, `\tau_j` is a timestamp, `\gamma_j\in[0,1]` is confidence, `R_j` is a region list, `a_j` is an algorithm label, and `s_j` is a source tier.

**Definition 2.5 (Finding).** A finding `F` is a tuple `(x,S,T,N,P,\nu)` where `x` is content, `S` is source metadata, `T` is the transformation list, `N` is neural state, `P` is a provenance chain, and `\nu\in[0,1]` is the ENDP novelty score.

**Definition 2.6 (Deployed constants).** The relevant deployed constants are:

$$
\alpha=0.73,\quad
mVQ_{bio}=\frac{15}{130},\quad
\lambda_{CRFE}=0.30,\quad
f_\star=0.70,\quad
\rho=0.50,
$$

$$
\tau_{NPDA}=10,\quad
R_{NPDA}=0.010,\quad
Q_{NPDA}=0.001,\quad
N_{ENDP}=4,\quad
B_{ENDP}=500.
$$

---

## 3. Formal Architecture

### 3.1 Boundary invariants

AETHER v1.4.0 enforces four architectural invariants:

- **I1 (Outside-shell):** ECUCA is a sibling process outside `AETHER_SHELL.ps1`.
- **I2 (No-hook):** Application and CLI defaults do not patch `open`, `compile`, `exec`, `eval`, or `__import__`.
- **I3 (Pinned provenance):** The vendored ECUCA source hash is pinned to `fd864fad7d62319cca86c84db39b0506647ac3e5871b9dbab31b64eee0ffae42`.
- **I4 (Fail-closed launch):** If the integrity preflight or governor gate fails, AETHER does not launch.

### 3.2 Launch composition

Let `P` be the standalone integrity-preflight predicate, `G` the ECUCA governor predicate, and `S` the shell-readiness predicate. The launcher implements

$$
\text{Launch} \iff P \land G \land S.
$$

Because ECUCA is external by I1, no shell-local write can set `G`. The direct CLI status payload reports the inspection field `fail_closed:false`; this describes the status-inspection mode, not the launcher's conjunctive gate. The launcher itself remains fail-closed by I4.

### 3.3 Qualification pipeline

For each candidate finding, AETHER computes, in order:

1. ENDP novelty `\nu` and emergence metadata.
2. DIP provenance score `\delta` and chain links.
3. MSVSC energy-efficiency record from chain confidence activations.
4. NPDA drift record from `(delta,nu)`.
5. CRFE record from emergence-level activations.

This ordering means drift and energy metrics consume provenance outputs rather than replacing them.

### 3.4 Algorithm summary

| # | Algorithm | Symbol | Output | Domain |
|---|---|---|---|---|
| 1 | MSVSC | `FE, SE, IER, CEE` | efficiency metrics | threshold-activation energy |
| 2 | CRFE | `FEX, CI, CRFE, RBT, I-CRFE` | critical fractal entropy | recursive entropy |
| 3 | NPDA | `DV, DA, PSI, NPC, INS` | drift alerts | signal processing |
| 4 | DIP | `\delta` | provenance quality | knowledge tracing |
| 5 | ENDP | `\nu` | novelty score | novelty detection |
| 6 | ECUCA | `Q_t` | quadrature governance | orthogonal control |

---

## 4. MSVSC — Millivoltage Synaptic Voltage Consumption Corollary

### 4.1 Definitions

Let `\theta` be the activation threshold, `V_{sw}` the full activation swing, and `N_s` the number of inputs. For input `i`, let `w_i\in[0,1]` be a weight, `a_i\in\mathbb R` an activation, and `V_i=w_i a_i` the voltage contribution. The synaptic voltage load is

$$
SVL=\sum_{i=1}^{N_s} V_i.
$$

The activation quantum is

$$
mVQ=\operatorname{clamp}_{[0.001,1]}\!\left(\frac{\theta}{V_{sw}}\right).
$$

For the biological calibration, `\theta=15\ \mathrm{mV}`, `V_{sw}=130\ \mathrm{mV}`, hence

$$
mVQ_{bio}=\frac{15}{130}\approx0.1153846154.
$$

Let `t_r` be refractory time, `f_r` firing rate, `b` transmitted bits, and `\varepsilon\in[0,1]` entropy overhead. The deployed implementation uses floors `N_s\ge1`, `t_r\ge0.1`, `f_r\ge0.01`, and `FE\ge10^{-6}` where division occurs. Define

$$
D=N_s\,t_r\,f_r.
$$

Firing efficiency is

$$
FE=\operatorname{clamp01}\!\left(mVQ\left(\frac{\max(0,SVL)}{\theta}\right)^\alpha\right).
$$

Energy consumption ratio and synaptic economy are

$$
ECR=\frac{D}{\max(10^{-6},FE)},\qquad
SE=\operatorname{clamp01}\!\left(\frac{FE^2}{D}\right).
$$

Let `\sigma(x)=1/(1+e^{-x})`. The information-energy ratio is

$$
IER=\sigma\!\left(0.1\left(\frac{b\,SE}{mVQ}-10\right)\right).
$$

Computational energy efficiency and normalized energy burden are

$$
CEE=\operatorname{clamp01}\bigl(IER(1-\varepsilon)\bigr),
\qquad
L=\frac{1}{\max(10^{-9},FE\,SE)}.
$$

The record caps `ECR` and `L` at `10^6` for reporting.

### 4.2 Lemma 4.1 — Firing efficiency is bounded

**Lemma.** For `\theta>0`, `mVQ\in(0,1]`, and `\alpha>0`, `FE\in[0,1]`.

**Proof.** The ratio `\max(0,SVL)/\theta` is nonnegative. Raising it to positive `\alpha` preserves nonnegativity, multiplying by `mVQ\in(0,1]` keeps the value nonnegative, and `clamp01` enforces the upper bound. ∎

### 4.3 Lemma 4.2 — Synaptic economy is bounded

**Lemma.** `SE\in[0,1]`.

**Proof.** `FE^2\ge0` and `D>0` by the implemented floors. The ratio is nonnegative, and `clamp01` enforces the upper bound. ∎

### 4.4 Theorem 4.3 — Conditional Landauer–MSVSC bound

**Assumptions.** (A1) Erasing one bit dissipates at least `k_B T\ln2`. (A2) `FE\cdot SE>0` is the useful-bit efficiency of the activation channel. (A3) Physical energy per delivered bit equals erasure cost divided by useful-bit efficiency.

**Theorem.** Under A1–A3,

$$
E_{bit}\ge k_B T\ln2\;L
=\frac{k_B T\ln2}{FE\cdot SE}.
$$

**Proof.** Let `E_{phys}` be the physical energy expended per erased bit and `E_{del}` the delivered useful energy. By A2, `E_{del}=(FE\,SE)E_{phys}`. By A1, `E_{phys}\ge k_B T\ln2`. Since `FE\,SE>0`, solve for delivered-bit cost:

$$
E_{bit}=E_{phys}\frac{1}{FE\,SE}
\ge k_B T\ln2\frac{1}{FE\,SE}.
$$

The implementation computes the normalized multiplier `L=1/(FE SE)`, capped at `10^6` for reporting. ∎

At `T=310.15\ \mathrm K`,

$$
k_B T\ln2
=1.380649\times10^{-23}\cdot310.15\cdot\ln2
\approx2.98\times10^{-21}\ \mathrm J.
$$

This theorem is conditional on A1–A3. It is a computational bookkeeping result, not a measurement of biological synapses.

### 4.5 Algorithm 1 — `compute_msvsc`

```text
INPUT: Ns, weights w[1..Ns], activations a[1..Ns], theta, swing,
       t_r, f_r, bits b, entropy_overhead eps, alpha=0.73
mVQ <- clamp(theta / swing, 0.001, 1)
SVL <- sum_i w[i]*a[i]
FE  <- clamp01(mVQ * (max(0, SVL)/theta)^alpha)
D   <- max(1,Ns)*max(0.1,t_r)*max(0.01,f_r)
ECR <- D / max(1e-6, FE)
SE  <- clamp01(FE^2 / D)
raw <- b*SE / max(1e-9,mVQ)
IER <- sigma(0.1*(raw-10))
CEE <- clamp01(IER*(1-clamp01(eps)))
L   <- min(1e6, 1/max(1e-9,FE*SE))
RETURN (mVQ, SVL, FE, ECR, SE, IER, CEE, L)
```

### 4.6 Demonstration

Take `theta=15/130`, `swing=1.0`, `N_s=100`, all `w_i=0.5`, all `a_i=1.0`, `t_r=2`, `f_r=10`, `b=1`, `\varepsilon=0.10`. Then `SVL=50`, `mVQ=0.1153846154`. Since `SVL/theta\gg1`, `FE=1`. Therefore

$$
D=100\cdot2\cdot10=2000,
\qquad
SE=\frac{1}{2000}=5\times10^{-4},
$$

$$
raw=\frac{1\cdot0.0005}{0.1153846154}\approx0.004333,
\qquad
IER=\sigma(0.1(0.004333-10))\approx0.269027,
$$

$$
CEE=0.269027(0.9)\approx0.242124,
\qquad
L=\frac{1}{1\cdot0.0005}=2000.
$$

These values match the certified implementation output to the displayed precision.

---

## 5. CRFE — Coherent Recursive Fractal Entropy

### 5.1 Definitions

Let `H_1,\dots,H_n\ge0` be entropies at hierarchical levels. The implementation requires `n\ge2` by appending copies of the last value if fewer than two levels are supplied.

The inter-level ratios are

$$
R_k=\frac{\max(10^{-9},H_{k+1})}{\max(10^{-9},H_k)},\qquad k=1,\dots,n-1.
$$

The fractal entropy exponent is

$$
FEX=\operatorname{clamp}_{[0,2]}\!\left(
\frac{\log(\max(10^{-9},H_n)/\max(10^{-9},H_1))}{\log n}
\right).
$$

The coherence integral is

$$
CI=\operatorname{clamp}_{[-1,1]}\!\left(
\frac{1}{n}\sum_{k=1}^{n}\cos(2\pi k\,FEX)
\right).
$$

Define critical proximity and coherent base as

$$
p(FEX)=\max\!\left(0,1-\frac{|FEX-0.70|}{0.50}\right),
\qquad
q(FEX,CI)=\max(0,FEX\,CI+0.5).
$$

Then

$$
CRFE=\operatorname{clamp01}\bigl(q(FEX,CI)\,p(FEX)\bigr).
$$

Let `\lambda=0.30`. The recursive bounding term is the exponentially weighted mean

$$
RBT=\frac{\sum_{k=1}^{n} H_k e^{-\lambda k}}{\sum_{k=1}^{n} e^{-\lambda k}}.
$$

The integrated score is

$$
I\!-\!CRFE=\operatorname{clamp01}\bigl(CRFE(1-e^{-\max(0,RBT)})\bigr).
$$

The `at_critical_edge` flag is

$$
|FEX-0.70|\le 0.25,
$$

equivalently `FEX\in[0.45,0.95]`. This is narrower than the full proximity support `[0.20,1.20]`.

### 5.2 Lemma 5.1 — Coherence bound

**Lemma.** `CI\in[-1,1]`.

**Proof.** Each cosine lies in `[-1,1]`; the arithmetic mean lies in `[-1,1]`; explicit clamping preserves the interval. ∎

### 5.3 Lemma 5.2 — RBT is a convex combination

**Lemma.** If `n\ge1` and `\lambda>0`, then

$$
\min_k H_k\le RBT\le\max_k H_k.
$$

**Proof.** Let `\omega_k=e^{-\lambda k}/\sum_j e^{-\lambda j}`. Then `\omega_k>0` and `\sum_k\omega_k=1`. Hence `RBT=\sum_k\omega_k H_k`, a convex combination. ∎

### 5.4 Theorem 5.3 — Boundedness of CRFE measures

**Theorem.** `CRFE\in[0,1]` and `I-CRFE\in[0,1]`.

**Proof.** `q\ge0` by definition. Lemma 5.1 and `FEX\in[0,2]` do not force `q\le1`, but explicit `clamp01` enforces `CRFE\in[0,1]`. Since `H_k\ge0`, Lemma 5.2 gives `RBT\ge0`, hence `1-e^{-RBT}\in[0,1)`. The product of two values in `[0,1]` lies in `[0,1]`, and the final clamp preserves it. ∎

### 5.5 Theorem 5.4 — Critical-region optimality

**Theorem.** `p(FEX)` is maximized uniquely at `FEX=0.70`, where `p=1`, and decreases linearly on the support `[0.20,1.20]`.

**Proof.** On the support, `p(FEX)=1-|FEX-0.70|/0.50`. The absolute-value term is minimized uniquely at `FEX=0.70`, giving `p=1`, and grows linearly with distance from `0.70`. Outside the support, `p=0`. ∎

### 5.6 Algorithm 2 — `compute_crfe`

```text
INPUT: H[1..n], lambda=0.30
if n < 2: append copies of H[-1] until n=2
H[k] <- max(0,H[k])
R[k] <- max(1e-9,H[k+1]) / max(1e-9,H[k]) for k=1..n-1
FEX  <- clamp((log(max(1e-9,H[n])/max(1e-9,H[1])) / log(n)), 0, 2)
CI   <- clamp((1/n)*sum_{k=1..n} cos(2*pi*k*FEX), -1, 1)
q    <- max(0, FEX*CI + 0.5)
p    <- max(0, 1 - abs(FEX-0.70)/0.50)
CRFE <- clamp01(q*p)
RBT  <- sum_k H[k]*exp(-lambda*k) / sum_k exp(-lambda*k)
I_CRFE <- clamp01(CRFE*(1-exp(-max(0,RBT))))
at_critical <- abs(FEX-0.70) <= 0.25
RETURN (R, FEX, CI, CRFE, RBT, I_CRFE, at_critical)
```

### 5.7 Demonstration

Let `H=(1.0,1.5,2.2,3.0)`. The certified implementation returns:

$$
FEX\approx0.792481,\quad
CI\approx-0.208204,\quad
CRFE\approx0.273039,
$$

$$
RBT\approx1.683229,\quad
I\!-\!CRFE\approx0.222316.
$$

The score is penalized because `FEX` is above `0.70`, although it remains inside the `at_critical_edge` band.

---

## 6. NPDA — Neural Provenance Drift Anticipator

### 6.1 Observed quantities

Let `Q_t\in[0,1]` be the observed DIP quality and `N_t\in[0,1]` the observed ENDP novelty at cycle `t`. Define raw drift and acceleration:

$$
DV_t=Q_t-Q_{t-1},
\qquad
DA_t=DV_t-DV_{t-1}.
$$

For the first observation, `Q_{t-1}=Q_t` and `DV_{t-1}=0`.

### 6.2 Kalman-inspired filter

Let state be `s_t=(\hat q_t,\widehat{dv}_t)` and covariance `p_t`. With process noise `Q=0.001` and observation noise `R=0.010`,

$$
q^{pred}_t=\hat q_{t-1}+\widehat{dv}_{t-1},
\qquad
p^{pred}_t=p_{t-1}+Q,
$$

$$
K_t=\frac{p^{pred}_t}{p^{pred}_t+R},
$$

$$
\hat q_t=q^{pred}_t+K_t(Q_t-q^{pred}_t),
$$

$$
\widehat{dv}_t=\widehat{dv}_{t-1}+0.1K_t(Q_t-q^{pred}_t),
$$

$$
p_t=(1-K_t)p^{pred}_t+Q.
$$

Define normalized acceleration

$$
\bar a_t=\min\!\left(1,\frac{|DA_t|}{0.10}\right).
$$

The provenance stability index and integrated NPDA signal are

$$
PSI_t=\max\!\left(0,e^{-|\widehat{dv}_t|\,10}(1-\bar a_t)\right),
$$

$$
NPC_t=
\begin{cases}
0, & \min(|Q_{1:t}|,|N_{1:t}|)<2,\\
0.5, & t<4,\\
\operatorname{clamp}_{[-1,1]}\bigl(\operatorname{corr}(Q_{1:t},N_{1:t})\bigr), & t\ge4,
\end{cases}
$$

$$
INS_t=\operatorname{clamp01}\!\left(
PSI_t\frac{\max(0,NPC_t+1)}{2}e^{-\bar a_t}
\right).
$$

Horizon forecasts are

$$
H_T=\operatorname{clamp01}(\hat q_t+\widehat{dv}_t T),
\qquad T\in\{5,10\}.
$$

### 6.3 Alert predicates

The implementation emits:

- `NPDA_DRIFT_ALERT` iff at least 3 consecutive raw drifts satisfy `DV<-0.05` and `|\widehat{dv}|>0.05`.
- `NPDA_ACCELERATION_ALERT` iff `|DA|>0.10`.
- `NPDA_HORIZON_ALERT` iff `H_5<0.35`.
- `NPDA_DECOUPLING_ALERT` iff `|NPC|<0.20`.
- `NPDA_STABILITY_ALERT` iff `PSI<0.30`.

### 6.4 Theorem 6.1 — Gain validity

**Theorem.** If `p_{t-1}\ge0`, `Q>0`, and `R>0`, then `0\le K_t<1` and `p_t>0`.

**Proof.** `p^{pred}=p_{t-1}+Q>0`. With `R>0`, the denominator `p^{pred}+R` strictly exceeds the numerator `p^{pred}`, so `0<K_t<1`. Hence `(1-K_t)>0` and `p_t=(1-K_t)p^{pred}+Q>0`. ∎

### 6.5 Theorem 6.2 — Bounded health signals

**Theorem.** `PSI_t\in[0,1]` and `INS_t\in[0,1]`.

**Proof.** The exponential `e^{-|\widehat{dv}|10}\in(0,1]`, and `1-\bar a\in[0,1]`. Their product is in `[0,1]`, and the outer `max(0,.)` preserves the interval. For `INS`, `(NPC+1)/2\in[0,1]` because `NPC\in[-1,1]`, `e^{-\bar a}\in(0,1]`, and the final `clamp01` enforces `[0,1]`. ∎

### 6.6 Proposition 6.3 — Decidable alerts

Each alert is a finite comparison of computable quantities against fixed thresholds. On finite-precision hardware, alert evaluation terminates and returns a boolean. Hence the alert set is decidable.

### 6.7 Algorithm 3 — `update_npda`

```text
INPUT: Q_t, N_t, state(q_hat,dv_hat,p), histories
Q_t <- clamp01(Q_t); N_t <- clamp01(N_t)
q_pred <- q_hat + dv_hat
p_pred <- p + Q
K <- p_pred/(p_pred + R)
innovation <- Q_t - q_pred
q_hat <- q_pred + K*innovation
dv_hat <- dv_hat + 0.1*K*innovation
p <- (1-K)*p_pred + Q
DV <- Q_t - previous_Q
DA <- DV - previous_DV
a_norm <- min(1, abs(DA)/0.10)
PSI <- max(0, exp(-abs(dv_hat)*10)*(1-a_norm))
NPC <- corr(Q_history,N_history) if len>=4 else 0.5
INS <- clamp01(PSI*max(0,(NPC+1)/2)*exp(-a_norm))
H5  <- clamp01(q_hat + dv_hat*5)
H10 <- clamp01(q_hat + dv_hat*10)
EMIT alerts per Section 6.3
RETURN record
```

### 6.8 Demonstration

Feed the certified engine the sequence

$$
Q=(0.80,0.74,0.66,0.55,0.45,0.35,0.27,0.20,0.15),
$$

$$
N=(0.30,0.35,0.40,0.45,0.50,0.55,0.60,0.65,0.70).
$$

At step 6 the implementation reports:

$$
DV_6=-0.10,\quad \widehat{dv}_6\approx-0.0279,\quad
H_5\approx0.3355,
$$

$$
PSI_6\approx0.7564,\quad NPC_6\approx-0.9959,\quad
INS_6\approx0.0016,
$$

with alert `NPDA_HORIZON_ALERT`. The observed quality reaches `0.35` at step 6 and falls below it at step 7. Thus the horizon alert precedes the observed threshold crossing by one step in this sequence. The v1.0 draft's “3–5 steps” observation is parameter- and history-dependent and is not an unconditional invariant.

---

## 7. DIP — Discovery Intelligence Provenance

### 7.1 Component scores

Let `s` be source score, `\tau_c` transformation score, `\kappa` cross-validation score, `\chi` coherence coupling, and `\nu` ENDP novelty. The deployed weights are

$$
(w_s,w_{\tau_c},w_\kappa,w_\chi,w_\nu)=(0.22,0.18,0.20,0.20,0.20).
$$

The aggregate provenance score is

$$
\delta(F)=0.22s+0.18\tau_c+0.20\kappa+0.20\chi+0.20\nu.
$$

The components are computed as follows.

**Source.** With source-tier map `M`, evidence items `e_1,\dots,e_m`, and tier key `t_i`,

$$
s=\frac{1}{m}\sum_{i=1}^{m} M(t_i),\qquad
M(\text{peer\_reviewed})=1.00,\ M(\text{preprint})=0.80,\dots,M(\text{unknown})=0.10.
$$

If evidence is empty, `s=M(candidate)=0.35` by default.

**Transformation.** For a chain of `n` links with operation diversity `d=|\{op_j\}|/n` and mean confidence `\bar\gamma`,

$$
\tau_c=\operatorname{clamp01}\bigl(0.40(1-e^{-n/4})+0.30d+0.30\bar\gamma\bigr).
$$

**Cross-validation.** Let `r` be the number of distinct brain regions divided by 8 (capped at 1), `a` the number of distinct algorithms divided by 6 (capped at 1), `e` evidence count divided by 5 (capped at 1), and `c` candidate count divided by 4 (capped at 1). Then

$$
\kappa=0.30r+0.25a+0.30e+0.15c.
$$

**Coherence coupling.** With neural coherence `c`, Kalman coherence `k`, and attention drift `d_a`,

$$
\chi=\operatorname{clamp01}\bigl(0.45c+0.30k+0.25\max(0,1-10d_a)\bigr).
$$

### 7.2 Theorem 7.1 — DIP boundedness

**Theorem.** If `s,\tau_c,\kappa,\chi,\nu\in[0,1]`, then `\delta\in[0,1]`.

**Proof.** The weights are nonnegative and sum to `1.0`; therefore `\delta` is a convex combination of values in `[0,1]`. ∎

### 7.3 Theorem 7.2 — Chain fingerprint change detection

Each link computes a 48-bit fingerprint

$$
\phi_j=\operatorname{SHA256}\bigl(\operatorname{canonicalJSON}(\text{content}_j)\bigr)[0:12\text{ hex}].
$$

**Theorem.** If canonical link content changes, the recorded fingerprint changes except with collision probability at most about `2^{-48}` under the random-oracle model for the truncated digest.

**Proof.** A content change maps to a new 48-bit value. Collision with the old value occurs with probability approximately `2^{-48}`. The implementation stores per-link fingerprints; it does not maintain a separate global chain hash, so the correct claim is per-link change detection, not a cryptographic chain-authentication guarantee. ∎

### 7.4 Qualification rule

The qualification label is the first matching branch of:

1. `EVIDENCE` if evidence count `\ge2` and `s\ge0.65`.
2. `UNDISCOVERED` if `\nu\ge0.75`, evidence count `0`, and `\delta\ge0.50`.
3. `EMERGENT` if `\nu\ge0.60` and `\delta\ge0.45`.
4. `CROSS_DOMAIN` if candidate count `\ge2` and `\delta\ge0.50`.
5. `DEDUCTION` if evidence count `\ge1` and `\delta\ge0.45`.
6. `HYPOTHESIS` if candidate count `\ge1` and `\delta\ge0.35`.
7. `CANDIDATE` if `\delta\ge0.25`.
8. `SPECULATIVE` otherwise.

### 7.5 Algorithm 4 — `compute_dip`

```text
INPUT: finding text F, evidence E, candidates C, regions R,
       algorithms A, neural state N, novelty nu
chain <- build_chain(F,E,C,R,A)
s      <- source_score(E)
tau_c  <- transformation_score(chain)
kappa  <- cross_validation_score(chain,len(C),len(E))
chi    <- coherence_coupling_score(N)
nu     <- clamp01(nu)
delta  <- 0.22*s + 0.18*tau_c + 0.20*kappa + 0.20*chi + 0.20*nu
qual   <- qualify_finding(delta,nu,len(E),len(C),s)
RETURN (delta, qual, chain, components)
```

### 7.6 Demonstration

For `s=0.80`, `\tau_c=0.70`, `\kappa=0.90`, `\chi=0.60`, `\nu=0.50`,

$$
\delta=0.22(0.80)+0.18(0.70)+0.20(0.90)+0.20(0.60)+0.20(0.50),
$$

$$
\delta=0.176+0.126+0.180+0.120+0.100=0.702.
$$

This is a provenance-quality score, not a truth score.

---

## 8. ENDP — Emergent Novel Discovery Provenance

### 8.1 Definitions

Let `A` be a candidate finding and `P={P_1,\dots,P_m}` the rolling prior buffer, with `m\le500`. Similarity is

$$
s_i=J(G_4(A),G_4(P_i)),
\qquad
\bar s=\max_i s_i,
$$

with `\bar s=0` if `P=\varnothing`. Define semantic distance and corpus penalty:

$$
d=1-\bar s,
\qquad
q=\begin{cases}
\bar s, & \bar s>0.80,\\
0, & \text{otherwise}.
\end{cases}
$$

Let `\omega_m` be the maximum applicable emergence-mode weight and `\omega_\ell` the discovery-tier weight. The deployed weights are

$$
\omega_m\in\{0.55,0.60,0.65,0.70,0.75,0.80,1.00\},
$$

$$
\omega_\ell\in\{0.10,0.30,0.60,0.80,1.00\}.
$$

The ENDP novelty score is

$$
\nu(A,P)=\operatorname{clamp01}\bigl(0.40d+0.25\omega_m+0.25\omega_\ell-0.10q\bigr).
$$

The novelty predicate is

$$
isNovel(A)\iff \nu>1-0.65=0.35.
$$

After scoring, the finding is ingested into the prior buffer.

### 8.2 Theorem 8.1 — Jaccard identities

**Theorem.** For finite sets `A,B`, `J(A,B)\in[0,1]`, `J(A,A)=1` when `A\ne\varnothing`, and `J(A,B)=J(B,A)`.

**Proof.** `0\le|A\cap B|\le|A\cup B|`, so the ratio lies in `[0,1]`. Identity and symmetry follow from set identity and commutativity of intersection and union. The empty-set convention fixes `J(\varnothing,\varnothing)=0` in the implementation. ∎

### 8.3 Theorem 8.2 — Finite-vocabulary concentration

Let `\mathcal V` be a finite vocabulary of size `M`, and for sets `A,B\subseteq\mathcal V` define

$$
\rho_A=\frac{|A|}{M},\quad
\rho_B=\frac{|B|}{M},\quad
\rho_{A\cap B}=\frac{|A\cap B|}{M},\quad
\rho_{A\cup B}=\frac{|A\cup B|}{M}.
$$

Assume `\rho_{A\cup B}\ge\rho_{min}>0`. Draw `m` vocabulary elements independently and uniformly, and estimate

$$
\hat\rho_C=\frac{1}{m}\sum_{i=1}^{m}\mathbf 1\{X_i\in C\},
\qquad
\hat J=\frac{\hat\rho_{A\cap B}}{\hat\rho_{A\cup B}}.
$$

**Theorem.** For any `\varepsilon>0`,

$$
\Pr\bigl(|\hat J-J|\ge\varepsilon\bigr)
\le
4\exp\!\left(
-\frac{2m\varepsilon^2\rho_{min}^2}{(2+\varepsilon)^2}
\right).
$$

**Proof.** By Hoeffding's inequality, each indicator mean satisfies

$$
\Pr(|\hat\rho_C-\rho_C|\ge t)\le2e^{-2mt^2}.
$$

Apply this to `A\cap B` and `A\cup B` and take a union bound, giving failure probability at most `4e^{-2mt^2}`. On the success event, `\hat\rho_{A\cup B}\ge\rho_{min}-t`. Choose

$$
t=\frac{\varepsilon\rho_{min}}{2+\varepsilon}.
$$

Then `2t/(\rho_{min}-t)=\varepsilon`, and the ratio-difference identity gives `|\hat J-J|\le\varepsilon`. Substitution yields the stated bound. ∎

The deployed ENDP engine computes exact set intersections over stored n-grams, so this concentration theorem is relevant only to sampled or sketched approximations, not to the default exact path.

### 8.4 Algorithm 5 — `compute_endp`

```text
INPUT: finding text A, prior buffer P, domain, evidence flags,
       neural state, consciousness flag, prior domains
tokens <- regex [a-z0-9]+ over lowercase(A)
G_A <- token_4grams(tokens)
s_bar <- max over P_i of J(G_A, G_i), or 0 if P empty
d <- 1 - s_bar
q <- s_bar if s_bar > 0.80 else 0
modes <- detect_emergence_modes(...)
omega_m <- max mode weight
tier <- classify_discovery_tier(A,d,modes)  # no tier V unless conditions hold
omega_l <- tier weight
nu <- clamp01(0.40*d + 0.25*omega_m + 0.25*omega_l - 0.10*q)
is_novel <- nu > 0.35
crfe <- compute_crfe([level1, level2, level3])
ingest A into P
RETURN (nu,is_novel,modes,tier,s_bar,crfe)
```

### 8.5 Demonstration

For prior text `"the quick brown fox jumps over the lazy dog"` and candidate `"the quick brown fox jumps over the very lazy dogs"`, the certified engine reports:

$$
\bar s\approx0.444444,\quad
\nu\approx0.384720,\quad
isNovel=\text{True},
$$

with mode `ABDUCTIVE`, tier `I`, and `crfe_score=0` for that short-text activation case. The computed novelty exceeds `0.35`, so the novelty predicate fires.

---

## 9. ECUCA v2.0.0 as an Orthogonal Quadrature Governor

### 9.1 Formal background

Let `z_t,z_{t+1}\in\mathbb C`, `dt>0`, and

$$
w_t=\bar z_t z_{t+1}=a_t+ib_t.
$$

The AETHER shell observable is

$$
\Omega_t=\frac{\operatorname{Im}(w_t)}{dt}=\frac{b_t}{dt}.
$$

ECUCA is rotated 90 degrees right, so it measures

$$
Q_t=\frac{\operatorname{Im}(i w_t)}{dt}.
$$

Since `i(a+ib)=-b+ia`,

$$
\operatorname{Im}(iw_t)=a,
$$

and therefore

$$
Q_t=\frac{\operatorname{Re}(w_t)}{dt}=\frac{a_t}{dt}.
$$

### 9.2 Theorem 9.1 — Exact quadrature decomposition

**Theorem.**

$$
w_t=dt\,(Q_t+i\Omega_t).
$$

**Proof.** From the definitions, `a_t=dt Q_t` and `b_t=dt\Omega_t`. Hence

$$
w_t=a_t+ib_t=dt(Q_t+i\Omega_t).
$$

∎

### 9.3 Theorem 9.2 — Orthogonality of the two axes

**Theorem.** Under the standard identification `\mathbb C\cong\mathbb R^2`, the shell axis `\Omega` and ECUCA axis `Q` are orthogonal.

**Proof.** `Q_t` is the real coordinate of `w_t/dt`, and `\Omega_t` is the imaginary coordinate. Real and imaginary axes are spanned by `(1,0)` and `(0,1)`, whose dot product is `0`. The live orthogonal check reports `phasor_inner_product=0.0` and all residuals zero within tolerance `10^{-10}`. ∎

### 9.4 Corollary 9.3 — Independent readings

The two observables can be reported independently. Governance applied to `Q_t` does not write into the shell's `\Omega_t` channel because ECUCA is external by I1.

### 9.5 Theorem 9.4 — Fail-closed launch composition

**Theorem.** Let `P` be integrity preflight, `G` the ECUCA hash-and-status gate, and `S` shell readiness. The launcher admits AETHER iff `P\land G\land S`. If any predicate is false, AETHER does not launch.

**Proof.** By I1 and I3, `G` is evaluated externally against a pinned hash. By I4, `P`, `G`, and `S` are conjunctive prerequisites. A conjunction is false when any operand is false; therefore the launch predicate is false and launch is withheld. ∎

### 9.6 Algorithm 6 — Governor launch

```text
1. verify standalone integrity manifest P
2. if not P: HALT with INTEGRITY_PREFLIGHT_FAILED
3. start ECUCA sibling: python ecuca.py
4. verify ECUCA source hash equals pinned hash; evaluate G
5. if not G: HALT with ECUCA_GATE_FAILED
6. start AETHER_SHELL.ps1
7. start AETHER
8. emit status with Q, Omega, residuals, and hook policy
```

### 9.7 Demonstration

Let `z_t=1+0.2i`, `z_{t+1}=1.1+0.5i`, `dt=1`. Then

$$
\bar z_t z_{t+1}=(1-0.2i)(1.1+0.5i)=1.2+0.28i.
$$

Hence `Q_t=1.2`, `\Omega_t=0.28`, and the axis inner product is `0`.

### 9.8 Live status evidence

The certified CLI reports:

```json
{
  "ok": true,
  "placement": {
    "embedded_in_shell": false,
    "handler_script": "AETHER_SHELL.ps1",
    "sibling_process": "AETHER_ORTHOGONAL_GOVERNOR.ps1",
    "entry_point": "python ecuca.py"
  },
  "rotation_degrees": 90,
  "hash_matches_pinned": true,
  "hook_policy": "opt-in; ECUCA installs no builtin hooks",
  "orthogonal": {
    "status": "ORTHOGONAL_CHECK_PASSED",
    "q": 0.8550633810409801,
    "omega": -0.21833352648075888,
    "phasor_inner_product": 0.0
  }
}
```

### 9.9 Mechanism catalog

| Code | Full name | Role |
|---|---|---|
| `UMLA` | Universal Mathematical Law Archaeologist | detects structure, symmetry, sparsity, separability, redundancy |
| `CMRC` | Counterfactual Mathematical Reality Compiler | constructs equivalent representations to reduce memory and operation cost |
| `AAGE` | Autonomous Algorithm Genesis & Evolution | generates and evolves algorithms measured by verified results per cost |
| `URDRE` | Universal Reality-to-Digital Reconstruction Engine | discovers hardware and execution environment |
| `APIE` | Autonomous Possibility and Invention Engine | proposes algorithms, structures, and hardware mappings |
| `PCFSE` | Predictive Consequence & Future-State Engine | scores and filters proposals by predicted consequence |

Research interfaces, explicitly non-production, are:

- `SOCFM` — Self-Organizing Computational Field Mechanism.
- `REIT` — Recursive Energy-Information Transduction.

---

## 10. Associated Novel Concepts from the v1.0 Draft

This section expands the five mechanisms and five observed patterns from the v1.0 draft. Each item is either defined as an implemented construct or explicitly qualified as an architectural interpretation.

### 10.1 Thermodynamic Provenance Bound

Define the provenance energy factor

$$
L(F)=\frac{1}{FE(F)\,SE(F)}.
$$

Under the MSVSC assumptions A1–A3, the conditional bound is

$$
E_{prov}(F)\ge k_B T\ln2\;L(F).
$$

**Interpretation.** Higher provenance work — more chain depth, more independent validation, more coherence — can be modeled as requiring more activation events and therefore a different `FE,SE` pair. This is a bookkeeping coupling between DIP and MSVSC, not a measured physical law.

### 10.2 Epistemic Uncertainty Principle

The v1.0 draft stated

$$
\nu\cdot\delta\le\frac14.
$$

**Qualification.** This inequality is not enforced by the current DIP or ENDP implementation. Both `\nu` and `\delta` are bounded in `[0,1]`, so their product can exceed `1/4`. The correct formal statement is a **design constraint**: an operating point is said to satisfy the epistemic uncertainty regime if

$$
(\nu,\delta)\in
\left\{(x,y)\in[0,1]^2:xy\le\frac14\right\}.
$$

A sufficient enforcement rule would be to reject or re-qualify findings with `\nu>0` and `\delta>1/(4\nu)`. The present implementation records the concept but does not apply that gate.

### 10.3 CRFE Capacity Bound

Let `C_{max}` be nominal channel capacity and let `C(\mathcal H)` be an architecture-defined effective capacity for hierarchy `\mathcal H`. The draft bound is

$$
C(\mathcal H)\le C_{max}\,I\!-\!CRFE(\mathcal H).
$$

Since `I-CRFE\in[0,1]`, this is a bounded attenuation law. It is a modeling rule: the architecture attenuates nominal capacity by its measured integrated critical-fractal score. It is not a new Shannon capacity theorem.

### 10.4 Drift-Entropy Production

Define an NPDA potential

$$
\Phi_{drift}=-\ln PSI
=-\ln\!\left(e^{-|\widehat{dv}|\tau}(1-\bar a)\right)
=\tau|\widehat{dv}|-\ln(1-\bar a).
$$

On the region `\bar a<1`, `\Phi_{drift}` increases monotonically with `|\widehat{dv}|` and `\bar a`. Equivalently, `PSI=e^{-\Phi_{drift}}` decreases monotonically. Thus `PSI` is a Lyapunov-like stability score under the modeled drift dynamics. The term “free energy” is an analogy, not a thermodynamic claim.

### 10.5 N-Gram Epistemology Theorem

Theorem 8.2 formalizes the v1.0 shorthand `J_4(A,B)≈sim_true±O(1/\sqrt{|V|})` under an explicit iid vocabulary-sampling model. The exact deployed path computes deterministic n-gram Jaccard similarity, so sampling error is zero there; the theorem governs approximate sketches only.

### 10.6 Criticality–Novelty Correspondence

Define, over a batch of `m` findings,

$$
\rho_{CN}
=
\operatorname{corr}\bigl(
I\!-\!CRFE(F_1),\dots,I\!-\!CRFE(F_m),
\nu(F_1),\dots,\nu(F_m)
\bigr).
$$

The observed pattern is said to hold in a batch when `\rho_{CN}>0`. This is an empirical, parameter-dependent observation, not a theorem. It is enabled structurally because ENDP passes emergence-level activations into CRFE.

### 10.7 Provenance–Energy Duality

For a finding with provenance quality `\delta`, define proof-work factor

$$
W(\delta)=1+\beta(1-\delta),\qquad\beta\ge0.
$$

If activation efficiency scales as `FE\,SE \propto 1/W(\delta)`, then

$$
L(\delta)\propto W(\delta),
$$

so higher `\delta` lowers the normalized energy burden. This is an architectural interpretation of the DIP–MSVSC coupling.

### 10.8 Drift Precedes Degradation

Define lead time

$$
\Lambda_t=
\min\{k>0:Q_{t+k}<0.35\}
-
\min\{k\ge0:\text{NPDA alert at }t+k\}.
$$

The v1.0 draft reported `\Lambda\in\{3,4,5\}` in selected runs. The certified demonstration in Section 6.8 yields `\Lambda=1`. Therefore the robust claim is: NPDA can alert before an observed DIP threshold crossing; the exact lead depends on history and thresholds.

### 10.9 Emergence-Mode Ladder

The v1.0 shorthand “certainty + novelty = 1” is not an identity in the implementation. Let `c=\bar s` be lexical familiarity. The implemented novelty contribution is

$$
0.40(1-c)+0.25\omega_m+0.25\omega_\ell-0.10q.
$$

Only the first term is complementary to `c`. The emergence-mode ladder is therefore an additive structure over familiarity, mode weight, tier weight, and penalty — not a conservation law.

### 10.10 Fractal Scaling of Provenance Chains

Given DIP chain-level entropies `H_1,\dots,H_n`, CRFE measures whether those entropies are scale-invariant via `FEX`, `CI`, and `I-CRFE`. A finding is said to exhibit fractal provenance scaling when `at_critical=True` and `I-CRFE` is high over successive chain depths. This is a structural diagnostic, not evidence of physical fractality.

---

## 11. Verification and Reproducibility

### 11.1 Certified test result

A fresh full-suite run produced:

```text
Ran 474 tests in 699.509s
OK (skipped=2)
```

with 0 failures and 0 errors. Failure/error line count in the log was 0.

### 11.2 Integrity and provenance hashes

- ECUCA pinned SHA-256: `fd864fad7d62319cca86c84db39b0506647ac3e5871b9dbab31b64eee0ffae42`
- Authoritative `umdk.py` SHA-256: `077566a41d316b8b9eeb5c72584b9644d11b467a19ceba8a3f3ae102058dd69a`
- C: integrity root: `C:\AETHER.ai\windows_usb`
- C: integrity manifest: `INTEGRITY_OK`, 204 files, 0 mismatched, 0 missing, 0 added.
- Previous v1.4.0 white paper SHA-256: `dba9741ecaab096816a17fd8b892fe2a844e392e1ae1529df75d95fca17e8fd5`

### 11.3 Desktop readiness

The production desktop process launched successfully:

```text
WINDOW_TITLE = AETHER // Autonomous Epistemic Theory and Experimental Research
RESPONDING   = True
```

and was closed after verification.

### 11.4 Reproduction commands

```powershell
cd C:\AETHER.ai\windows_usb\src
python -m unittest discover -s tests -v
python -m aether --config C:\AETHER.ai\SECURITY\AETHER_RUNTIME_CONFIG.json --ecuca-status
python -m aether --config C:\AETHER.ai\SECURITY\AETHER_RUNTIME_CONFIG.json --ecuca-orthogonal-check
python -m aether --config C:\AETHER.ai\SECURITY\AETHER_RUNTIME_CONFIG.json --app
```

No passphrases, tokens, certificates, salts, or private keys are included in this paper.

---

## 12. Limitations and Threats to Validity

1. MSVSC thermodynamic results are axiomatized computational bounds, not experimental biophysics.
2. `FEX=0.70`, the CRFE critical band, and all NPDA thresholds are architecture parameters, not universal constants.
3. NPDA uses a scalar Kalman-inspired approximation; nonlinear regime shifts are not modeled.
4. ENDP similarity is lexical/token-level and may miss semantic equivalence or detect superficial overlap.
5. DIP is a provenance-quality score, not a truth or correctness guarantee.
6. DIP chain fingerprints are 48-bit truncations; they provide change detection, not strong cryptographic authentication.
7. The epistemic uncertainty inequality is a design constraint, not an implemented invariant.
8. CRFE capacity attenuation and thermodynamic provenance bounds are modeling rules, not information-theoretic discoveries.
9. The fail-closed launch theorem depends on the integrity of the launcher, ACLs, and pinned hash source.
10. Novelty is scoped to this architecture; external priority is not claimed.

---

## 13. Conclusion

AETHER v1.4.0 has a self-contained formal basis. MSVSC, CRFE, NPDA, DIP, and ENDP are defined with bounded scores, algorithms, theorems, and demonstrations computed from the certified implementation. The five mechanisms and five observed patterns from the v1.0 draft are preserved but rigorously qualified. ECUCA v2.0.0 is formalized as a 90-degree quadrature sibling governor with exact decomposition, orthogonality, and fail-closed launch guarantees. The certified implementation passes 474 tests, verifies its integrity manifest, and launches in production desktop mode.

---

## Appendix A — Symbol Table

| Symbol | Meaning |
|---|---|
| `mVQ` | millivoltage activation quantum |
| `FE` | firing efficiency |
| `SE` | synaptic economy |
| `ECR` | energy consumption ratio |
| `IER` | information-energy ratio |
| `CEE` | computational energy efficiency |
| `L` | normalized energy burden |
| `FEX` | fractal entropy exponent |
| `CI` | coherence integral |
| `RBT` | recursive bounding term |
| `I-CRFE` | integrated CRFE |
| `DV` | drift vector |
| `DA` | drift acceleration |
| `PSI` | provenance stability index |
| `NPC` | novelty-provenance coupling |
| `INS` | integrated NPDA signal |
| `\delta` | DIP provenance score |
| `\nu` | ENDP novelty score |
| `J_4` | token-level 4-gram Jaccard similarity |
| `\bar s` | maximum similarity to a prior finding |
| `Q_t` | ECUCA quadrature observable |
| `\Omega_t` | shell phase observable |

## Appendix B — Algorithm Index

1. `compute_msvsc` — threshold activation energy model.
2. `compute_crfe` — recursive fractal entropy.
3. `update_npda` — drift anticipation.
4. `compute_dip` — provenance quality and qualification.
5. `compute_endp` — novelty scoring and emergence classification.
6. `governor_launch` — fail-closed quadrature governance.

## Appendix C — Data and Provenance Statement

All reported numerical demonstrations were computed against the certified source tree at `C:\AETHER.ai\windows_usb\src`. The implementation was not modified to produce this paper. The paper is a documentation artifact stored outside the sealed source tree unless explicitly copied to a public reference directory.

## Appendix D — References

1. Landauer, R. (1961). Irreversibility and heat generation in the computing process. *IBM Journal of Research and Development*, 5(3), 183–191.
2. Shannon, C. E. (1948). A mathematical theory of communication. *Bell System Technical Journal*, 27, 379–423, 623–656.
3. Jaccard, P. (1901). Étude comparative de la distribution florale dans une portion des Alpes et des Jura. *Bulletin de la Société Vaudoise des Sciences Naturelles*, 37, 547–579.
4. Kalman, R. E. (1960). A new approach to linear filtering and prediction problems. *Journal of Basic Engineering*, 82(1), 35–45.
5. Hurst, H. E. (1951). Long-term storage capacity of reservoirs. *Transactions of the American Society of Civil Engineers*, 116, 770–808.
6. Cover, T. M., & Thomas, J. A. (2006). *Elements of Information Theory* (2nd ed.). Wiley-Interscience.
7. Hoeffding, W. (1963). Probability inequalities for sums of bounded random variables. *Journal of the American Statistical Association*, 58(301), 13–30.

---

**Author statement:** William Brian Pope is the sole author of this manuscript and the inventor and engineer of the AETHER program and its ECUCA quadrature-governor integration.
