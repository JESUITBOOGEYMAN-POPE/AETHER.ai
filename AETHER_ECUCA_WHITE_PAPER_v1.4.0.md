# Orthogonal Energy Governance of an Epistemic Discovery Stack

## ECUCA v2.0.0 as a quadrature sibling governor of AETHER v1.4.0

**Prepared:** 2026-11-26  
**System under audit:** AETHER v1.4.0, Windows USB distribution, Python source tree  
**External layer:** ECUCA v2.0.0, byte-identical vendored script  
**Scope statement:** This paper reports implementation results, formal identities, and audited software behavior. It does not claim physical quantum hardware, universal optimization, or external empirical validation of scientific laws.

---

## Abstract

AETHER v1.3.0 enclosed its complete discovery architecture in a quantum-analog outer shell whose primitive is the Symplectic Phase-Curvature Operator

`Omega_t = Im(conj(z_t) z_(t+1)) / dt`.

Version 1.4.0 adds ECUCA v2.0.0 as an **external orthogonal governing layer** rather than as another brain region, shell primitive, or builtin hook. ECUCA is launched as a sibling gate before `AETHER_SHELL.ps1` and governs the real quadrature of the same channel phasor:

`Q_t = Im(conj(z_t) i z_(t+1)) / dt = Re(conj(z_t) z_(t+1)) / dt`.

The two layers therefore satisfy the exact decomposition

`conj(z_t) z_(t+1) = dt (Q_t + i Omega_t)`,

with `Q_t` and `Omega_t` orthogonal under the real Hilbert-Schmidt inner product. The integration is fail-closed: the launcher aborts if the ECUCA gate script is absent, if the vendored source hash is wrong, if ECUCA self-tests fail, or if the quadrature check fails. The nineteen-region brain, the authoritative `umdk.py`, and the opt-in global-hook policy are unchanged. Audited results report `ECUCA_STATUS`, six passing ECUCA self-checks, six ECUCA mechanisms, four immutable governance rules, exact zero residuals for quadrature decomposition and orthogonality, and a direct ECUCA demonstration that executes five benchmark workloads with zero failed verifications. The fresh full-suite audit completed with 474 tests, 2 skips, and zero failures or errors, certifying the audited source tree as fully operational within the stated Windows/Python environment.

---

## 1. Introduction

AETHER is an offline-first epistemic discovery architecture organized around a protected mathematical subkernel (`umdk.py`), a nineteen-region brain, a governed full stack, and a quantum-analog outer shell. The shell is explicitly an **analog** finite-dimensional complex Hilbert-space calculus, not a claim of physical quantum computation. It is observational: it does not patch builtins, add a twentieth brain region, or replace the protected kernel.

ECUCA v2.0.0 is an independent energy-constrained computational architecture that proposes strategies through six intelligence mechanisms, executes them through an energy-aware layer, verifies results independently, and applies recursive energy optimization under immutable constraints. Its own description frames it as “Universal Energy Intelligence”: discover how a problem should be solved before committing resources to solving it.

The design question addressed here is not “how to merge two systems,” but how to compose them **without violating either boundary**:

1. ECUCA must remain outside `AETHER_SHELL.ps1`.
2. It must be rotated into the quadrature orthogonal to the shell's curvature operator.
3. It must run as a sibling process before the shell.
4. It must not patch `open`, `compile`, `exec`, `eval`, or `__import__`.
5. It must fail closed if any provenance or self-check fails.
6. It must not change the brain region count, `umdk.py`, or the full-stack opt-in hook policy.

This paper defines the composition, describes the implementation, and reports only evidence produced by fresh execution and hash verification.

---

## 2. Formal background

### 2.1 Shell observable

Let `psi_t` be a normalized finite-dimensional state, `p_j,t = |psi_j,t|^2`, and let a diagonal unitary channel carry phases `omega_j`. Including state-relative phases `phi_j,t`, the shell observes

```text
z_t = <psi_t, U psi_t>
    = sum_j p_j,t exp(-i (omega_j + phi_j,t) dt),      |z_t| <= 1.   (1)
```

The shell's discovered primitive and its two-channel extension are

```text
Omega_t = Im(conj(z_t) z_(t+1)) / dt,                                (2)
Xi_t    = Im(conj(z^A_t) z^B_(t+1)) / dt
        - Im(conj(z^B_t) z^A_(t+1)) / dt.                            (3)
```

Equation (2) is the Symplectic Phase-Curvature Operator (SPCO); equation (3) is the Exchange Curvature Operator (ECO). In the shipped calibration the shell discovers `phase_area` from a declared contraction grammar rather than receiving the target expression.

### 2.2 ECUCA quadrature

Define the rotation operator `R` as multiplication by `i`, a counter-clockwise ninety-degree rotation in the complex plane. For the same phasor step define

```text
p_t   = conj(z_t) z_(t+1) / dt,                                      (4)
Q_t   = Im(i p_t) = Re(p_t),                                         (5)
Omega_t = Im(p_t).                                                   (6)
```

Equation (5) is the ECUCA-governed quadrature. Equivalently,

```text
Q_t = Im(conj(z_t) i z_(t+1)) / dt,                                  (5a)
```

because `Im(conj(z_t) i z_(t+1)) = Im(i conj(z_t) z_(t+1))`.

Combining (4)-(6) gives the central composition law:

```text
p_t = Q_t + i Omega_t,
conj(z_t) z_(t+1) = dt (Q_t + i Omega_t).                            (7)
```

---

## 3. Formal results

### Theorem 1 — Exact quadrature decomposition

For any `dt > 0` and any shell phasors `z_t`, `z_(t+1)` satisfying (1), the ECUCA quadrature (5) and shell curvature (2) are the real and imaginary parts of the normalized phasor product (4). Therefore equation (7) holds exactly.

**Proof.** Write `p_t = a + ib` with `a, b` real. By definition `b = Im(p_t) = Omega_t`. Since `i p_t = -b + ia`, its imaginary part is `a = Re(p_t)`. ECUCA's rotated definition gives `Q_t = Im(i p_t) = a`. Hence `p_t = a + ib = Q_t + i Omega_t`. Multiplying by `dt` yields (7). The bound `|p_t| <= 1/dt` follows from `|z_t| <= 1`. ∎

### Theorem 2 — Orthogonality of the two axes

Let the real inner product on complex numbers be `<u, v>_R = Re(u conj(v))`. Then

```text
<p_t, i p_t>_R = Re(p_t conj(i p_t)) = 0.                            (8)
```

Moreover `|i p_t| = |p_t|`; the rotation preserves magnitude while exchanging the governed quantities.

**Proof.** Let `p_t = Q_t + i Omega_t` and `i p_t = -Omega_t + i Q_t`. Then

```text
p_t conj(i p_t)
  = (Q_t + i Omega_t)(-Omega_t - i Q_t)
  = 0 - i (Q_t^2 + Omega_t^2).
```

Its real part is zero. Magnitude preservation follows from `|i| = 1`. ∎

### Corollary 1 — Independent axis readings

The shell can report `Omega_t` without evaluating ECUCA's energy accounting, and ECUCA can report `Q_t` without evaluating the shell's phase-curvature grammar, provided both observe the same `conj(z_t) z_(t+1)` step. The coupling is therefore a shared observation, not a shared implementation.

### Corollary 2 — Governance interpretation

The orthogonality result is representational and architectural. It does **not** assert that energy cost and phase curvature are physically independent resources, nor that optimizing one cannot affect the other through workload choices. It asserts that the two governed readings are exact complementary components of the same complex step and that the integration keeps their implementations and process boundaries separate.

### Theorem 3 — Fail-closed gate composition

Let the launch sequence be `G` (ECUCA governor), `S` (shell), and `A` (AETHER application), with `G` a sibling predecessor of `S`. If `G` exits nonzero, then `S` and `A` are not started. The shipped launcher implements this by checking for the governor script before shell setup and exiting with code `2` on any gate refusal.

**Proof.** By inspection of `AETHER_LAUNCH.bat` and both USB/root launcher templates: the governor command block precedes the shell command block; each failure branch executes `exit /b 2`. The PowerShell governor itself requests exit code `2` on missing source, nonzero bridge exit, invalid JSON, or `ok = false`; host shells report this as a nonzero refusal status. ∎

---

## 4. Architecture

### 4.1 Boundary placement

| Layer | Location | Responsibility | Boundary |
| --- | --- | --- | --- |
| AETHER core/brain/full stack | `src/aether/` | Epistemic discovery, nineteen regions, governed stack | Protected |
| Quantum-analog shell | `src/aether/shell/`, `AETHER_SHELL.ps1` | `Omega`, `Xi`, discovery, proofs, enclosure | Observational |
| ECUCA governor | `src/aether/orthogonal/ecuca.py` | `Q`, energy/cost strategy governance | External sibling |
| Gate script | `AETHER_ORTHOGONAL_GOVERNOR.ps1` | Fail-closed launch gate | Sibling of shell |
| Bridge | `src/aether/orthogonal/ecuca_bridge.py` | Status, hash, quadrature check, receipts | Adapter only |

`AETHER_SHELL.ps1` contains no ECUCA logic. `aether/shell/` contains no ECUCA imports. The governor's PowerShell script contains no shell implementation. These exclusions are regression-tested.

### 4.2 Launch order

The authoritative launcher executes:

```text
Gate 1: AETHER_ORTHOGONAL_GOVERNOR.ps1 -> python -m aether.orthogonal --status
Gate 2: AETHER_SHELL.ps1               -> -LaunchGui
Gate 3: AETHER desktop application
```

If PowerShell is unavailable, the launcher uses a direct Python governor invocation before falling back to the shell/application path. This preserves the same ordering in constrained environments.

### 4.3 Bridge behavior

`EcucaGovernor.status()` loads the vendored script through `importlib.util.spec_from_file_location`, computes its SHA-256, verifies the declared version, runs `ECUCASystem.self_test()`, and reports mechanisms, immutable rules, research interfaces, and hook policy. Any exception is converted into `ECUCA_UNAVAILABLE` with `ok = false`, so the gate fails closed.

`orthogonal_check()` constructs two-level shell states, evaluates the channel phasor, and verifies:

- `dt > 0`;
- ninety-degree rotation identity;
- shell `Omega` equals the imaginary axis;
- exact complex decomposition;
- zero real inner product between the axes.

Tolerance is `1e-10`; observed residuals are `0.0` in the shipped check.

### 4.4 ECUCA mechanisms under governance

ECUCA v2.0.0 coordinates six mechanisms:

| Mechanism | Role | Primary energy objective |
| --- | --- | --- |
| UMLA | Universal Mathematical Law Archaeologist | Remove unnecessary operations by discovering structure, symmetry, sparsity, separability, and redundancy |
| CMRC | Counterfactual Mathematical Reality Compiler | Reduce memory movement and expensive hardware use via equivalent representations |
| AAGE | Autonomous Algorithm Genesis & Evolution | Discover algorithms yielding more verified results per joule and dollar |
| URDRE | Universal Reality-to-Digital Reconstruction Engine | Identify actual hardware and energy sources, then select execution environment |
| APIE | Autonomous Possibility and Invention Engine | Propose unconventional algorithms, data structures, and mappings |
| PCFSE | Predictive Consequence & Future-State Engine | Forecast consequences and avoid strategies likely to exceed constraints |

These mechanisms feed the Universal Energy-Aware Execution Layer (UEAEL), which performs hardware discovery, workload analysis, execution selection, energy/financial accounting, and adaptive execution. Results are checked by an independent verification engine. Recursive Energy Optimization and Verification Engine (REOVE) operates under four immutable rules:

```text
verification_required
safety_checks_enabled
authorization_required_for_deploy
rollback_always_available
```

SOCFM and REIT are present as explicitly experimental research interfaces; they are not production capabilities and are not used by the AETHER gate.

---

## 5. Audit method

The audit uses only artifacts present in the Windows USB source tree and the user-supplied ECUCA snapshot.

### 5.1 Environment

```text
Python: 3.13.17
NumPy:  2.5.5
OS:     Windows
Source: C:\AETHER.ai\windows_usb\src
```

### 5.2 Provenance hashes

```text
ECUCA vendored source / supplied snapshot / supplied v2 snapshot:
FD864FAD7D62319CCA86C84DB39B0506647AC3E5871B9DBAB31B64EEE0FFAE42

AETHER authoritative umdk.py:
077566A41D316B8B9EEB5C72584B9644D11B467A19CEBA8A3F3AE102058DD69A
```

The ECUCA hash is identical across `C:\Users\jesui\Downloads\ecuca.py`, `ecuca_v2_snapshot.py`, and `src\aether\orthogonal\ecuca.py`. The `umdk.py` hash matches the value recorded in previous manifest addenda.

### 5.3 Commands

```powershell
python -m aether --ecuca-status
python -m aether --ecuca-orthogonal-check
python -m aether --shell-status
python -m aether --full-stack-status
python -m aether.orthogonal --status

powershell -NoProfile -ExecutionPolicy Bypass \
  -File AETHER_ORTHOGONAL_GOVERNOR.ps1 -Status

python ecuca.py --self-test --export ecuca_direct_report.json --quiet
python -m unittest discover -s tests -p "test_full_stack*.py" -v
python -m unittest discover -s tests -v
python -m compileall -q aether tests umdk.py windows_usb
```

The direct ECUCA command is run from `src\aether\orthogonal`, preserving the canonical entry point `python ecuca.py`.

### 5.4 No-hook verification

The CLI regression captures `builtins.open`, `compile`, `exec`, `eval`, and `__import__` before and after both new CLI flags and asserts object identity is unchanged. ECUCA source contains no builtin patching call; its `_register_builtins` name refers to its own algorithm registry, not Python builtins.

---

## 6. Results

### 6.1 External governor status

`python -m aether --ecuca-status` returns:

```text
status: ECUCA_STATUS
ok: true
boundary: ecuca-orthogonal-governor/v1
version: 2.0.0
source_sha256: fd864fad7d62319cca86c84db39b0506647ac3e5871b9dbab31b64eee0ffae42
placement: outside quantum-analog-shell/v1
embedded_in_shell: false
entry_point: python ecuca.py
rotation_degrees: 90
hook_policy: opt-in; ECUCA installs no builtin hooks
```

Reported mechanisms:

```text
UMLA, CMRC, AAGE, URDRE, APIE, PCFSE
```

All six ECUCA self-checks pass:

```text
energy_model_positive          true
nested_sparsity                true
numeric_sequence_accuracy      true
optimization_score_callable    true
modification_ordering          true
algorithm_resolution           true
```

Immutable rules reported:

```text
verification_required
safety_checks_enabled
authorization_required_for_deploy
rollback_always_available
```

### 6.2 Quadrature check

`python -m aether --ecuca-orthogonal-check` returns `ORTHOGONAL_CHECK_PASSED` for `dt = 1`, `theta = 0.4`, `delta = 0.5`, channel phases `(0, 0)`:

```text
q                       = 0.8550633810409801
omega                   = -0.21833352648075888
omega_from_shell        = -0.21833352648075888
rotated_quadrature      = 0.8550633810409801
phasor_inner_product    = 0.0
residual.rotation       = 0.0
residual.shell_axis     = 0.0
residual.decomposition  = 0.0
residual.orthogonality  = 0.0
tolerance               = 1e-10
```

A regression additionally checks the identities across `dt ∈ {0.25, 1.0, 2.0}`, `theta ∈ {-0.8, 0.0, 0.4, 1.1}`, and `delta ∈ {-0.5, 0.2, 0.7}`; all residuals are at or below `1e-12`.

The invalid-step case `dt = 0` returns `ORTHOGONAL_CHECK_FAILED` with `ok = false`, demonstrating fail-closed behavior at the operator level.

### 6.3 Direct ECUCA demonstration

The unmodified ECUCA CLI ran with `--self-test --export --quiet` and exited cleanly. The exported report contains five workloads:

| # | Problem type | Proposals | Executed | Passed | Failed | Best verified algorithm |
| --- | --- | ---: | ---: | ---: | ---: | --- |
| 1 | `matrix_multiplication` | 12 | 5 | 5 | 0 | `numpy_matmul` |
| 2 | `matrix_multiplication` | 12 | 5 | 5 | 0 | `numpy_matmul` |
| 3 | `linear_system` | 13 | 5 | 5 | 0 | `numpy_solve` |
| 4 | `fractal` | 8 | 3 | 3 | 0 | `mandelbrot_optimized` |
| 5 | `data_analysis` | 12 | 5 | 5 | 0 | `data_stats_standard` |

On the first workload, engaged proposal counts are CMRC 6, AAGE 3, URDRE 1, APIE 2, UMLA 0, PCFSE 0. Engagement is workload-dependent; all six mechanisms are present in the system and reported by the adapter.

These results demonstrate that the vendored ECUCA layer is operational in isolation under its own CLI. They do not establish superior performance on workloads outside this finite demonstration set, and the energy values are model estimates rather than external power-meter measurements.

### 6.4 PowerShell gate

The sibling gate was invoked directly:

```powershell
powershell -NoProfile -ExecutionPolicy Bypass \
  -File AETHER_ORTHOGONAL_GOVERNOR.ps1 \
  -PythonExe python -Source C:\AETHER.ai\windows_usb\src -Status
```

It returned `ECUCA_STATUS`, `ok: true`, the same source hash, the full quadrature receipt, and no embedded shell implementation. A negative control with a missing source directory returned `ECUCA_GOVERNOR_FAILED`, `ok: false`, and a nonzero exit status before any shell action. The gate requests code `2` on missing source, invalid bridge JSON, or `ok = false`.

### 6.5 Full-stack and integration regressions

`python -m unittest discover -s tests -p "test_full_stack*.py" -v` reports **141 tests OK**. The new orthogonal regression module contributes eleven tests covering:

1. exact ninety-degree quadrature over a parameter grid;
2. zero-residual orthogonal check payload;
3. fail-closed invalid `dt`;
4. byte-identical ECUCA source and self-test status;
5. outside-shell placement;
6. missing-source fail-closed behavior;
7. modified-source hash-gate failure;
8. CLI flags emitting JSON without builtin patching;
9. absence of ECUCA logic inside the shell or brain-facing shell modules;
10. governor-before-shell launcher order;
11. app control presence.

`python -m compileall -q aether tests umdk.py windows_usb` completes with no output, indicating successful compilation.

The fresh complete-suite audit was then run after all integration and portability fixes: `python -m unittest discover -s tests -v` reports `Ran 474 tests in 621.400s` and `OK (skipped=2)`, with zero failures and zero errors. This is the operational certification recorded in the v1.4.0 change-manifest addendum. The claim is scoped to the audited source tree, launch gates, CLI/app control surfaces, and Windows/Python 3.13.17 environment; no runtime GUI session was opened during the audit.

For preservation deployments, `aether_integrity.verify()` reuses the `includes` and `excludes` patterns recorded inside each sealed manifest. Previously verification always used a smaller default pattern set, so a full-tree manifest could not be verified by the standalone Gate 0 preflight. A dedicated regression test now locks in that round trip, and the launch gates therefore validate the same full source scope that was sealed.

### 6.6 Whole-program architecture audit

A read-only map of the complete source tree was used to verify that the v1.4.0 additions did not damage existing boundaries.

| Subsystem | Verified boundary | Evidence source |
| --- | --- | --- |
| Authoritative kernel | `umdk.py` hash unchanged; no v1.4.0 edit | Hash table, manifest |
| Brain | `REGION_ORDER` has 14 domain + 4 integration + 1 synthesis = 19 regions; `protocol_layout_status` reports `region_count: 19`, `bypass: not_permitted` | `brain/regions.py`, `full_stack/protocol_map.py` |
| Full stack | `build_stack(install=False)` default wrapper; hooks opt-in | `full_stack/integration.py` |
| Shell | SPCO/ECO, discovery, proofs, benchmark, evidence gate | `shell/*`, `AETHER_SHELL.ps1` |
| ECUCA | External sibling; hash-pinned; six mechanisms; four immutables | `orthogonal/*`, gate script |
| CLI/app | Read-only status/step controls; no builtin patching | `cli.py`, `app.py` |
| Security stores | Ledger, integrity, longterm, neural chains remain separate gates | top-level security modules |
| Packaging | Governor and shell copied as siblings; valid `--app` launch verb | `build_usb_package.py`, launchers |

The audit found and corrected five integration gaps before certification:

1. `aether.shell` was missing from packaged `pyproject.toml` packages; added.
2. Launchers and `-LaunchGui` passed removed CLI flags and a positional `gui` verb; replaced with `--db PATH --app`.
3. The ECUCA digest was reported but not enforced; now pinned in `EXPECTED_ECUCA_SHA256` and checked before module execution.
4. The USB launcher did not bootstrap NumPy, although ECUCA imports it; added wheel-based bootstrap.
5. Documentation claimed `~/.umdk-local` while `AetherConfig` defaults to `~/.umdk`; launchers and README now use the actual path.

These corrections are part of the evidence workup: the final audit is performed after them, not before.

### 6.7 Evidence workup matrix

| Claim | Primary command or artifact | Required marker | Counter-control |
| --- | --- | --- | --- |
| ECUCA source is byte-identical | `Get-FileHash aether\orthogonal\ecuca.py` | pinned SHA-256 | modified-source test rejects |
| ECUCA self-tests pass | `--ecuca-status` | six `true` checks | missing source rejects |
| Quadrature is exact | `--ecuca-orthogonal-check` | four zero residuals | `dt=0` fails closed |
| Gate precedes shell | launcher source + regression test | governor line before shell line | missing gate aborts |
| Shell remains unchanged | shell hash + shell status | `SHELL_VERIFIED` | ECUCA strings absent from shell |
| Full stack remains hook-free | `--full-stack-status` | `global_hooks_installed: false` | explicit hooks only |
| ECUCA mechanisms execute | direct CLI export | five reports, zero failures | verification failures reported |
| App exposes read-only control | `app.py` + regression | button and callback present | no builtin identity change |
| Package is installable | `pyproject.toml` package list | shell and orthogonal included | import smoke check |

---

## 7. Discoveries and claims

This section names the mechanisms that were identified, formalized, or newly composed in the audited system. The word “novel” is used in the architectural sense: these are novel mechanisms **of this integration** unless a separate literature-priority claim is explicitly supported. Established mathematical ideas are acknowledged in section 7.4.

### 7.1 Mechanism catalog

| ID | Mechanism | Formal object or invariant | Enforcing artifact | Evidence |
| --- | --- | --- | --- | --- |
| M1 | Orthogonal Quadrature Composition (OQC) | `p_t = Q_t + i Omega_t`; `<p_t, i p_t>_R = 0` | `ecuca_bridge.orthogonal_check` | Theorems 1-2; zero residuals |
| M2 | Pinned-Hash Sibling Admission (PHSA) | Admit only `H(source) = h*` | `EXPECTED_ECUCA_SHA256` in `EcucaGovernor.status` | Modified-source negative control |
| M3 | Fail-Closed Pre-Shell Gate (FPSG) | `G -> S -> A`; `G != 0 => not S and not A` | `AETHER_ORTHOGONAL_GOVERNOR.ps1`, launchers | Launcher-order test; missing-source control |
| M4 | Non-Invasive Observational Enclosure (NIOE) | `implementation(shell) ∩ implementation(governor) = empty` | `aether/shell/`, governor script | Shell/governor exclusion regression |
| M5 | Declared-Grammar Operator Discovery (DGOD) | Admissible iff nuisance residuals `<= epsilon` over a finite grammar | `discover_operator` | `OPERATOR_DISCOVERED`, `phase_area` |
| M6 | Energy Quadrature Budget (EQB) | `Q_t = Re(p_t)` as the real-axis budget paired with `Omega_t` | `quadrature_curvature`, ECUCA status | Five verified workload reports |
| M7 | Verified Strategy Pluralism (VSP) | Proposal set from six mechanisms, filtered by independent verification | `ECUCASystem.solve`, `VerificationEngine` | 8-13 proposals/workload, zero failures |
| M8 | Immutable Recursive Optimization (IRO) | REOVE cannot rewrite safety, disable verification, bypass authorization, or lose rollback | `REOVE.IMMUTABLE_CONSTRAINTS` | Four rules in governor receipt |
| M9 | Evidence-Gated Law Refusal (EGLR) | Law proposal requires observable + latent records with independent provenance | `propose_natural_law` | `INSUFFICIENT_NATURE_EVIDENCE` with no evidence |
| M10 | Provenance-Limited Research Interface Quarantine (PLRIQ) | SOCFM/REIT are reported but excluded from the launch gate | `ecuca.py` interfaces, `EcucaGovernor.status` | Status labels interfaces experimental |
| M11 | Portable Sibling Packaging (PSBP) | Package copies governor and shell as siblings; launcher uses valid CLI verbs | `build_usb_package.py`, launchers | Build-path and launcher-argument audit |

### 7.2 Formal definitions

**Definition 1 (Orthogonal Quadrature Composition).** Let `R` denote the real-linear operator `Rz = iz`. A quadrature composition is a pair of observational maps `(q, omega)` satisfying `q(z_t,z_(t+1)) = Im(R p_t)` and `omega(z_t,z_(t+1)) = Im(p_t)`, where `p_t = conj(z_t)z_(t+1)/dt`. A composition is *orthogonal* when `<p_t, R p_t>_R = 0`. The AETHER-ECUCA pair is an orthogonal quadrature composition by Theorems 1-2.

**Definition 2 (Pinned-Hash Sibling Admission).** Let `h*` be a pinned digest and `H` a digest function. An admission gate is pinning when `Admit(s) => H(s) = h*`. The ECUCA gate is pinning: `EXPECTED_ECUCA_SHA256` is checked before module execution, so a modified but self-test-passing source is rejected. This closes the gap between merely *reporting* a hash and *enforcing* it.

**Definition 3 (Fail-Closed Pre-Shell Gate).** Let `G`, `S`, and `A` denote governor, shell, and application start events. The launcher implements the guarded sequence `G; (G_ok ? S;A : abort)`, with abort status `2`. This is a process-level safety property: no shell receipt is issued for a launch that failed the governor.

**Definition 4 (Non-Invasive Observational Enclosure).** An enclosure is non-invasive when it observes a state transition without altering the transition's governing weights, builtins, or protected kernel. The shell satisfies this for AETHER; ECUCA satisfies it as a sibling gate. Neither depends on the other's internal implementation.

**Definition 5 (Declared-Grammar Discovery).** Let `C` be a finite set of contraction expressions and `N` a set of nuisance ensembles. Candidate `c` is admissible when `max_{n in N} |c(n)| <= epsilon` and the time-reversal residual is `<= epsilon`. Ranking by target response with a complexity penalty yields a *discovery within C*, not unbounded synthesis. The shell's selected `phase_area` operator satisfies this definition.

**Definition 6 (Verified Strategy Pluralism).** Let mechanisms `m_1..m_6` emit proposal sets `P_i`. The executed set is `E ⊆ ⋃P_i`, diversity-filtered and verification-gated. ECUCA's reports show `|⋃P_i|` of 8-13, `|E|` of 3-5, and zero failed verifications across five workloads. The claim is pluralism with verification, not optimality.

**Definition 7 (Immutable Recursive Optimization).** Let `M` be a modification proposal and `K` the immutable constraint set. REOVE admits `M` only if all rules in `K` remain satisfied after promotion. The observed `K` contains verification, safety, authorization, and rollback rules. The audited gate reports them; it does not grant unrestricted self-modification.

**Definition 8 (Evidence-Gated Law Refusal).** Let `E` be a nature-record set. A law proposal is emitted only if `|E| >= 3`, at least two independent provenance marks, at least one observable and one latent record, and mean confidence `>= 0.85`. Otherwise the system returns `INSUFFICIENT_NATURE_EVIDENCE`. Refusal is a first-class output, not an error path.

**Definition 9 (ECUCA Verified Efficiency and Composite Score).** For an execution result `r`, let `E(r)` be total estimated joules, `C(r)` estimated dollars, and `T(r)` execution seconds. ECUCA defines verified efficiency and a minimization score as

```text
eta(r) = 1 / E(r)        if r is independently verified, else 0
S(r)   = E(r) + lambda C(r) + mu T(r)                    (9)
r*     = argmin { S(r) : r is verified }                 (10)
```

The shipped demonstration uses `lambda = 0.1` and `mu = 0.5`. Energy is composed as processor + memory + storage + network + cooling + control + conversion joules; cooling is `(processor + memory)(PUE - 1)`, and cost is `joules / 3,600,000 × electricity_price`. These are model estimates, not meter readings. Equation (9) is directly exercised by the `optimization_score_callable` self-check.

### 7.3 Discovery list

### Discovery 1 — Complementary quadrature governance

The shell's `Omega` and ECUCA's `Q` are not merely analogous quantities. They are the imaginary and real components of one normalized phasor product. This yields an exact, compact composition law (7) and a rigorous orthogonality identity (8). It also gives a principled reason to place ECUCA at ninety degrees: the shell already occupied the imaginary axis, so the remaining orthogonal observable is the real axis.

### Discovery 2 — Non-invasive sibling governance is sufficient

The full composition does not require embedding ECUCA in the shell, adding a twentieth brain region, replacing `umdk.py`, or installing builtin hooks. A sibling process with a fail-closed receipt is sufficient to govern entry while preserving all existing layers. This is an architectural result: separation of concerns is achievable without weakening either subsystem.

### Discovery 3 — Fail-closed provenance is mechanically checkable

Byte identity is not asserted from filenames. The bridge hashes the vendored source on every status call and compares against the expected digest. Missing source, wrong version, failed self-tests, invalid quadrature, or invalid JSON all produce `ok = false` and a nonzero gate exit. The launcher propagates that refusal before starting the shell.

### Discovery 4 — ECUCA's strategy pipeline is independently operational

The direct CLI demonstration executes five diverse workloads, selects diverse best algorithms, and reports zero verification failures. This supports the claim that ECUCA is functional as an external governor candidate, while leaving broader efficiency claims scoped to the reported workloads and model.

### Discovery 5 — Orthogonality is a governance invariant, not a physical claim

The result is mathematical and architectural. It is valid for the defined complex-observable calculus and the implemented process boundary. It is not evidence of a physical quantum computer, thermodynamic advantage, or universal optimality.

### 7.4 Related-work positioning

The following positioning is deliberately conservative because external literature lookup was unavailable during this audit.

1. **Geometric and Berry phases.** Discrete phase areas and symplectic curvature of complex expectation values are established ideas in quantum geometry and topological phases. The contribution here is not the invention of geometric phase; it is the explicit, audited composition of a shell curvature axis with an external energy-governance axis under a pinned, fail-closed sibling gate.
2. **Energy-aware scheduling and autotuning.** Energy-aware algorithm selection, DVFS scheduling, and empirical autotuning are established. ECUCA's specific contribution in this integration is a six-mechanism proposal ensemble with independent verification and immutable optimization rules, reported through a machine-readable gate receipt. No global optimality claim is made.
3. **Cryptographic provenance and fail-closed gates.** Hash pinning and fail-closed admission are standard security patterns. The novelty here is their placement: the ECUCA check is external to, and ordered before, the observational shell, rather than embedded in it.
4. **Grammar-based operator discovery.** Searching a declared operator grammar with nuisance nullness constraints resembles scoped program synthesis and invariant discovery. The shell explicitly qualifies its result as discovery *within a declared grammar*, avoiding a broader invention claim.
5. **Sandboxed research interfaces.** Quarantining experimental interfaces from production control paths is a known safety pattern. PLRIQ applies it to ECUCA's SOCFM/REIT interfaces by reporting them without granting them launch authority.

---

## 8. Limitations and threats to validity

1. **Declared grammar.** Shell operator discovery is performed within a finite declared contraction grammar. It is not unbounded invention.
2. **Finite benchmark set.** ECUCA's five workloads demonstrate operation but do not establish global dominance over all algorithms or hardware.
3. **Estimated energy.** ECUCA energy and cost figures are model estimates; no calibrated external power measurement was performed.
4. **Sample quadrature verification.** The printed numerical check uses one parameter set, but algebraic proof and grid regression cover the general identity. The grid is finite, not exhaustive over all real values.
5. **Research interfaces.** SOCFM and REIT are explicitly experimental and are not used by the launch gate.
6. **Process-level, not kernel-level, coupling.** ECUCA gates launch and reports status; it does not continuously rewrite AETHER execution state. Continuous co-governance would require a separate design and audit.
7. **Portability context.** The reported audit is for the stated Windows/Python environment. POSIX-only assumptions in unrelated legacy modules were addressed separately in the full-suite portability work recorded in the manifest.

---

## 9. Reproducibility checklist

To reproduce the central evidence:

```powershell
cd C:\AETHER.ai\windows_usb\src

# 1. Provenance and self-test
python -m aether --ecuca-status

# 2. Exact quadrature receipt
python -m aether --ecuca-orthogonal-check

# 3. Sibling PowerShell gate
powershell -NoProfile -ExecutionPolicy Bypass \
  -File ..\AETHER_ORTHOGONAL_GOVERNOR.ps1 -Status

# 4. Direct ECUCA entry point (canonical form)
cd aether\orthogonal
python ecuca.py --self-test --export ecuca_direct_report.json --quiet

# 5. Integration, full-suite, and compilation audits
cd ..\..
python -m unittest discover -s tests -p "test_full_stack*.py" -v
python -m unittest discover -s tests -v
python -m compileall -q aether tests umdk.py windows_usb

# 6. Protected hash
Get-FileHash umdk.py -Algorithm SHA256
Get-FileHash aether\orthogonal\ecuca.py -Algorithm SHA256
```

Expected markers: `ECUCA_STATUS`, `ORTHOGONAL_CHECK_PASSED`, `ECUCA_GOVERNOR_RECEIPT` or `-Status` JSON with `ok: true`, five ECUCA workload reports, `141 tests OK` for the full-stack subset, `474 tests` with `OK (skipped=2)` for the full suite, clean `compileall`, and the two SHA-256 values listed in section 5.2.

---

## 10. Conclusion

AETHER v1.4.0 demonstrates that an external energy-governance architecture can be composed with an observational epistemic shell through an exact quadrature relationship. The shell keeps its imaginary phase-curvature axis; ECUCA governs the rotated real energy/cost axis; the launcher keeps them as ordered siblings and fails closed on any integrity refusal. The result is a stronger architectural boundary, not a weaker one: no builtin hooks, no extra brain region, no protected-kernel replacement, and no shell embedding. The formal identity, hash provenance, status receipts, direct ECUCA execution, regression suite, and clean 474-test full-suite certification together provide a reproducible basis for the claim, while the limitations above constrain its interpretation.

---

## Appendix A — Artifact map

| Artifact | Role |
| --- | --- |
| `src/aether/orthogonal/ecuca.py` | Byte-identical vendored ECUCA v2.0.0 source |
| `src/aether/orthogonal/ecuca_bridge.py` | Fail-closed adapter, hash verification, quadrature algebra |
| `src/aether/orthogonal/__init__.py`, `__main__.py` | Package API and `python -m aether.orthogonal` entry point |
| `AETHER_ORTHOGONAL_GOVERNOR.ps1` | External sibling gate; no shell implementation |
| `AETHER_LAUNCH.bat` | Authoritative governor-before-shell launch order |
| `src/windows_usb/AETHER_LAUNCH.bat` | USB template with the same ordering |
| `src/windows_usb/build_usb_package.py` | Copies governor and shell scripts; version 1.4.0 |
| `src/aether/cli.py` | `--ecuca-status`, `--ecuca-orthogonal-check` |
| `src/aether/app.py` | “ECUCA orthogonal governor” Work-panel control |
| `src/tests/test_full_stack_orthogonal.py` | Ten quadrature, placement, provenance, and no-hook regressions |
| `src/AETHER_CHANGE_MANIFEST.md` | Final version-1.4.0 audit and SHA-256 index |
| `src/umdk.py` | Protected authoritative kernel, unchanged |

## Appendix B — Notation

```text
z_t             shell channel characteristic at step t
dt              positive temporal step
p_j,t           Born weight of basis channel j
omega_j         channel phase
phi_j,t         state-relative phase
Omega_t          shell SPCO = Im(conj(z_t) z_(t+1)) / dt
Xi_t             shell ECO, antisymmetric two-channel extension
Q_t              ECUCA quadrature = Im(conj(z_t) i z_(t+1)) / dt
R                +90-degree complex rotation, multiplication by i
p_t              normalized phasor product conj(z_t) z_(t+1) / dt
<u,v>_R          real inner product Re(u conj(v))
```
