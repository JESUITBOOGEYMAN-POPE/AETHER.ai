# AETHER Change Manifest

This file is the single organizational index for the files written or
updated during the AETHER memory/neural hardening, 19-region brain
expansion, resident SCI/OIE capabilities, expanded candidate/search
discovery, Neural Self-Portrait refinement, and explicit activation-control
cycles. Its sections cascade in the same order as the existing repository
tree; no source files were moved or renamed.

## 2026-11-26 addendum: external ECUCA quadrature governor and full audit (v1.4.0)

Version 1.4.0 adds ECUCA v2.0.0 as an external, byte-pinned quadrature
governor beside the quantum-analog outer shell. ECUCA is not embedded in
`AETHER_SHELL.ps1`, does not modify the nineteen-region brain, does not replace
`umdk.py`, and does not install process-wide builtin hooks. The launcher order
is governor, then shell, then application; refusal at the governor aborts the
launch.

Formal composition: the shell owns the imaginary axis
`Omega_t = Im(conj(z_t) z_(t+1)) / dt`, while ECUCA observes the rotated real
axis `Q_t = Im(conj(z_t) i z_(t+1)) / dt = Re(conj(z_t) z_(t+1)) / dt`, so
`conj(z_t) z_(t+1) = dt (Q_t + i Omega_t)` and the real inner product of the
two axes is zero. The bridge checks this decomposition to tolerance `1e-10`.

Certification after all integration and portability corrections:

- `python -m unittest discover -s tests -v` — `Ran 474 tests in 621.400s`,
  `OK (skipped=2)`; **0 failures, 0 errors**. This is the fresh full-suite
  operational certification for the audited source tree.
- `aether_integrity.verify()` now reuses the `includes`/`excludes` patterns
  recorded in each sealed manifest, so a full-tree manifest verifies with the
  same scope it was sealed with. A dedicated regression covers this round trip.
- `python -m unittest tests.test_full_stack_orthogonal -v` — 11 tests OK.
- `python -m unittest discover -s tests -p "test_full_stack*.py" -v` — 141 tests OK.
- `python -m compileall -q aether tests umdk.py windows_usb` — OK.
- `python -m aether --ecuca-status` — `ECUCA_STATUS`, `ok: true`, pinned source
  hash matches, six self-checks true, mechanisms `UMLA, CMRC, AAGE, URDRE,
  APIE, PCFSE`, four immutable rules, placement outside the shell.
- `python -m aether --ecuca-orthogonal-check` — `ORTHOGONAL_CHECK_PASSED`,
  `q = 0.8550633810409801`, `omega = -0.21833352648075888`, all four
  residuals `0.0`, tolerance `1e-10`.
- `python -m aether --status` — version `1.4.0`, `outer_shell`,
  `external_governor`, and `region_count: 19`.
- PowerShell governor `-Status` — `ECUCA_STATUS`, `ok: true`; missing-source
  negative control — `ECUCA_GOVERNOR_FAILED`, `ok: false`, nonzero exit.
- PowerShell shell `-ShellStatus` — `SHELL_VERIFIED`, operator `phase_area`,
  law gate returns `INSUFFICIENT_NATURE_EVIDENCE` without nature records.
- Direct ECUCA CLI export — five workloads
  (`matrix_multiplication`, `matrix_multiplication`, `linear_system`,
  `fractal`, `data_analysis`), proposals `[12, 12, 13, 8, 12]`, executed
  `[5, 5, 5, 3, 5]`, passed `[5, 5, 5, 3, 5]`, failed `[0, 0, 0, 0, 0]`.
- CLI parser smoke check — `--mode offline --db PATH --app` parses to
  `app=True`, `mode=offline`; packaging includes both `aether.shell` and
  `aether.orthogonal`.

The certification is scoped to the automated audit surfaces and the stated
Windows/Python 3.13.17/NumPy 2.5.5 environment. A runtime GUI session was not
opened; the app control was verified by source inspection and regression.

Portability remediation completed before the final audit: private-file helpers
now apply real Windows DACL checks and a portable `O_NOFOLLOW` substitute, key
and manifest paths use those helpers, subprocess tests force UTF-8 on Windows,
and temporary SQLite fixtures use non-fatal cleanup. These fixes are included
in the 474-test result above.

### v1.4.0 integration and governance artifacts

| Path | SHA-256 | Role |
| --- | --- | --- |
| `pyproject.toml` | `78a7ac5940ce3bee5c2c558df136da6ef2de0414059bfaf983605a7bb29ce1a2` | v1.4.0 metadata; shell and orthogonal packages included. |
| `aether/version.py` | `a7d0a56cc0594611eddaa34375b98f8e43151feee84d75b17cad178724e4f8e6` | Version 1.4.0. |
| `aether/__init__.py` | `46713ff11adc38450238a27769ecfcfe117170d4407d2f4525293ba69001d64d` | Public shell and orthogonal exports. |
| `aether/cli.py` | `2280e820176b58403f654ab5e6df1c31d231eda69be6f9ec41b773192330e741` | ECUCA status/check flags and status field. |
| `aether/app.py` | `549cb2adf48ed681a352513ca927e3ed7aa7e912e1928fc264041d43fc0aac0d` | ECUCA orthogonal governor control. |
| `aether/shell/__init__.py` | `ce591b75bd71c674d37e3bb46fb1cd63770d440eeca668ad156f7bea330f0551` | Unchanged shell package boundary. |
| `aether/shell/quantum_analog.py` | `d604e9e00e24d7ebed3b29c57355cabbdca80e4bd69d62f0dfaee22d18391fed` | Unchanged SPCO/ECO algebra and evidence gate. |
| `aether/shell/handler.py` | `373d575960edf8d8e8979e4dc89cce36a77ec1c9d7cc234ac5d6faf18929481b` | Unchanged encasing handler. |
| `aether/orthogonal/__init__.py` | `e2367025f6e3deb340d5b108755639f16250f57b1facd19f9ca63246ce6a83da` | Orthogonal package exports including pinned hash. |
| `aether/orthogonal/ecuca.py` | `fd864fad7d62319cca86c84db39b0506647ac3e5871b9dbab31b64eee0ffae42` | Byte-identical vendored ECUCA v2.0.0. |
| `aether/orthogonal/ecuca_bridge.py` | `5dcd0a774c53e1889968f28e0dcca0c179001403b45ab675c9032c1ebfb913e4` | Hash-pinned bridge, quadrature algebra, fail-closed receipt. |
| `tests/test_full_stack_orthogonal.py` | `70f2e4d4d56c33a5c664d6597c250e4c4bf6c663124d261e00700a3691a45fad` | Eleven quadrature, outer-placement, hash, launcher, and no-hook regressions. |
| `AETHER_ECUCA_WHITE_PAPER.md` | `dba9741ecaab096816a17fd8b892fe2a844e392e1ae1529df75d95fca17e8fd5` | Final formal paper and discovery catalog. |
| `../README.txt` | `016181b396697e165a79c2e0941aa6ef288cabffc2028ce7a240aaa70bbd9656` | v1.4.0 user docs, required NumPy, real data path. |
| `../AETHER_LAUNCH.bat` | `7f3fa94b97a8e09e574e670a1d26acdc241facf2e581f2d907d5a903c3aa9769` | Governor then shell then app; valid `--app` fallback. |
| `../AETHER_SHELL.ps1` | `a507248b6604a937f1673bf9cd69940708df7e0526c2e77cc543570d425059d5` | Shell enclosure with valid `--db PATH --app` GUI verb. |
| `../AETHER_ORTHOGONAL_GOVERNOR.ps1` | `8588442876e8244630862d5e87ccd8861dde1d66d4ea0a8e5fcd6efa1301d592` | External sibling fail-closed gate. |
| `windows_usb/AETHER_LAUNCH.bat` | `475b26a5df9c525cd196d70c286f2e0e01111046922f281c48b49be7a83b3fc8` | USB launcher with NumPy bootstrap and sibling ordering. |
| `windows_usb/build_usb_package.py` | `b4aeaa144045f6db6102896a2b2a3c2290ec982b2a3f7ca20da0def3a867ff3d` | Copies both sibling gates; v1.4.0 docs and data path. |
| `umdk.py` | `077566a41d316b8b9eeb5c72584b9644d11b467a19ceba8a3f3ae102058dd69a` | Unchanged authoritative UMDK implementation. |

### v1.4.0 portability artifacts

| Path | SHA-256 | Role |
| --- | --- | --- |
| `aether_private_files.py` | `8ff85f2a114d97a98df412446f7ca6618d441dc7b7ebe856046d6325248b04f4` | Shared private-file helper with Windows DACL enforcement. |
| `aether_keygen.py` | `daab1139003d2c9340d7ab618871788a53fe0cf02569258501f00addeb4da9eb` | Portable private create/verify checks. |
| `aether_integrity.py` | `817522f830802cbf71e137cf7c595231c5312434caf539d0707779c29caf02b4` | Portable key load/create and manifest sealing. |
| `aether_longterm.py` | `cdac9ebad49f746293e11df09332d5521ed8719b66334f59aa6ac89cd8e867eb` | Portable long-term key handling. |
| `aether_ledger.py` | `d11a6690c1da5444fee9a1dcdc762c5f1da95832d1ee71019fd9425d2622b04c` | Portable key, ledger, seal, and standalone verification paths. |
| `aether/cloud_ledger.py` | `4ca7d59c418b6ed8bca0c56b7aaede13be675bf1151458596352c9b98a0d16a8` | Portable private cache creation. |
| `aether/core/kernel.py` | `cc9604a0c9518042374e64cd28237e6e8aacbdf4c4acb79b245a9b76b68e515b` | Portable salt ownership check. |
| `tests/private_file_helpers.py` | `966a11267f548b15607f329cf08cef1ec8d864509da7eaeecad7931f85c9f063` | Portable permission assertions and fixture helpers. |
| `tests/test_aether_keygen.py` | `a7a198c1fd138e9bcbe49f169c90231dc27ccc49e50a45ce2b5b1ec8c9ff3012` | Portable keygen regressions. |
| `tests/test_aether_integrity.py` | `4cea3b4162037195cef029a5174ba7947e56d8fed2353a9b0d219419b8c2dec` | Portable integrity regressions. |
| `tests/test_aether_ledger.py` | `dd87493f45656480c83bf68018eedbfdb942aad2bf191516686ee564bed2bbeb` | Portable ledger regressions. |
| `tests/test_aether_salt_wiring.py` | `85615d3de6c9e5314ddc5032b0c7eeb2ccbf9c761dfb831058c66f979b388d5e` | Portable salt regressions. |
| `tests/test_aether_longterm.py` | `0074ea8ec42b81c61adde740b5445f590048136c0a9c6f5e432812789cdf0b87` | Portable long-term regressions. |
| `tests/test_aether_neural.py` | `2f814388c8e3f40ae9ce738d3a62aeb3b86b30bd8f96a697710cf3faa29ad0b6` | Portable neural-store regressions. |
| `tests/test_aether.py` | `1ac484cc06423d192c31b8e6a6d05b3824bca7fe5cad1ded614494a371c39e15` | UTF-8 CLI subprocess fixtures. |
| `tests/test_aether_brain.py` | `0439da64196770de8b7430aad25d698b464c6232e429393fabb1b3b79c5366a1` | UTF-8 CLI subprocess fixtures. |
| `tests/test_aether_consciousness.py` | `07dcc456f55b5769c096e05918274e732ade3ccf84c23efcbbfb647771b3586a` | UTF-8 CLI subprocess fixtures. |
| `tests/test_aether_ledger_integration.py` | `3488cfe9fde16a9d74cca7da74b67e7111e24eba90c72f8d64850fbd566de6f6` | UTF-8 CLI subprocess fixtures. |
| `tests/test_aether_science.py` | `64a1c63db24c65d1107687b08396128b0f351fa0956a54eedb6e091dab49742b` | UTF-8 CLI subprocess fixtures. |
| `tests/test_aether_vault.py` | `02a606c05f6f1a986864107f88dd497174fa9e07bfad8d397eee4b0506aec6be` | UTF-8 CLI subprocess fixtures. |
| `tests/test_umdk_meta.py` | `8a365c02321fb8b249a4c1223df3980429b650f2f8bf77bddbec48f856130953` | Non-fatal SQLite fixture cleanup. |
| `tests/test_umdk_smoke.py` | `f28d664b4c9ec2d10b590673ba5d99f396653fa82604e2dcc9455652ddbf0885` | Non-fatal SQLite fixture cleanup. |
| `tests/test_aether_visuals.py` | `08bb4a6f47fa6088432abbc4f16bdc0b8db4474c0471f7f794e3981f995f5ccc` | Portable offline-status assertion. |

## 2026-11-25 addendum: quantum-analog outer shell (v1.3.0)

Version 1.3.0 encloses the complete AETHER architecture in a novel outer shell
without changing the nineteen-region brain, the authoritative `umdk.py`, or the
opt-in builtin-hook policy.

Formal definition: for normalized Born weights `p_j`, channel phases `omega_j`,
and relative phases `phi_j,t`, the shell observes

`z_t = sum_j p_j,t exp(-i(omega_j + phi_j,t) dt)` with `|z_t| <= 1`, then
discovers and applies the Symplectic Phase-Curvature Operator
`Omega_t = Im(conj(z_t) z_(t+1)) / dt` and its exchange extension `Xi_t`.
For equal-population two-level drift with accumulated phases `Theta = theta dt`
and `Delta = delta dt`, the independently re-derived identity is
`Omega = -sin(Delta/2) cos(Theta/2) cos((Theta+Delta)/2) / dt`.

Capabilities demonstrated in v1.3.0:

* Operator discovery: the SPCO is selected from a declared contraction grammar
  by global-phase nullness, population nullness, time-reversal oddness, target
  response, and a complexity penalty; no target operator name is supplied.
* Measurable advantage: on energy-conserving latent phase drift, SPCO detects
  one sample after change while CUSUM on population energy remains blind;
  default verified advantage is 199 samples with zero false alarms.
* Formal verification: boundedness, global-phase invariance, time
  antisymmetry, population nullness, exchange antisymmetry, and the
  phase-contrast identity are checked numerically by an independent path.
* Architectural breakthrough: the discovered operator becomes the shell's
  tensor `T_ab = Re(chi_a conj(chi_b))`, vector `v = (Re z_t, Im z_t, Omega dt)`,
  scalar `s = |Omega| dt`, and temporal fiber `dt` without a twentieth region.
* Evidence-gated law proposal: the Admissible Phase-Budget Law is emitted only
  from externally supplied observable and latent nature records with
  independent provenance; absent evidence returns a refusal.

`AETHER_LAUNCH.bat` now routes the desktop app through `AETHER_SHELL.ps1`.
`python -m aether --shell-status`, `--shell-law-evidence PATH`, and the app's
Quantum shell status control expose the shell. `src/umdk.py` remains unchanged.

Verification after this addendum:

- `python -m unittest discover -s tests -p "test_full_stack*.py" -v` — 130 tests, OK.
- `python -m compileall -q aether tests umdk.py` — OK.
- `python -m aether --shell-status` and `--full-stack-status` — OK.
- `python -m aether --shell-law-evidence PATH` with external fixture — OK,
  `LAW_PROPOSAL`, confidence `1.0`.
- `powershell -File AETHER_SHELL.ps1 -ShellStatus` and CLI forwarding — OK,
  `SHELL_VERIFIED`, operator `phase_area`.
- Fresh-process standalone import — OK, 15 modules / 46 exports.

| Path | SHA-256 | Role |
| --- | --- | --- |
| `pyproject.toml` | `b4a8cb6a97fc168ebb7c006967f0ae5dba283b195024aa5cef4af9f99e1ea27b` | v1.3.0 metadata. |
| `aether/version.py` | `94cdcdeba2a2c4feb01a72063f21aecaef1f6613e1930825498764f0cad35ff8` | Version 1.3.0. |
| `aether/__init__.py` | `1ac6eb0055100c010cb299cf77ed3e42d6c6d435bec318a5412ee2ffdf4fca4e` | Public shell exports. |
| `aether/cli.py` | `560bb72b511b3a3c9d060116075445ccfad2febb18fce4ffd9c2ff9ba2b4e6bc` | Shell status/law commands and status field. |
| `aether/app.py` | `e44ee65b30cfc70eb2b4a254fdb7b6e80002d35c83a884df789ea213147d538f` | Quantum shell status control. |
| `aether/shell/__init__.py` | `ce591b75bd71c674d37e3bb46fb1cd63770d440eeca668ad156f7bea330f0551` | Shell package boundary. |
| `aether/shell/quantum_analog.py` | `d604e9e00e24d7ebed3b29c57355cabbdca80e4bd69d62f0dfaee22d18391fed` | SPCO/ECO algebra, discovery, proofs, benchmark, law gate. |
| `aether/shell/handler.py` | `373d575960edf8d8e8979e4dc89cce36a77ec1c9d7cc234ac5d6faf18929481b` | Encasing handler and provenance receipt. |
| `aether/full_stack/standalone/build_full_stack_original.py` | `87a62f34a58ce1c968840b938925c1ca7fb7c118cd8a78fa3b69948c0266f97b` | Standalone order now includes shell modules. |
| `aether/full_stack/standalone/build_full_stack.py` | `30d61fb28a3c4b5e225d22cb7af8c83766663455bdecd99f85bea7319b09b8c5` | Shell source paths and relative-import rewrite. |
| `aether/full_stack/standalone/aether_full_stack.py` | `fa6fe411eebfb45368f6b1d211c8b192953bfa62805b3018b4f04f53d42619c8` | Regenerated 15-module standalone bundle. |
| `tests/test_full_stack_shell.py` | `05813d81d920424b5229780c7fbe83de97ee1ee4079c7540c25be771bd50f734` | Discovery, proof, benchmark, receipt, and law-gate regressions. |
| `AETHER_SHELL_FORMALISM.md` | `6ea55060bd78ded06b726edd6ad377c54d4efdf44ea30b81d88bc862dfc07f3a` | Formal definitions, proofs, and shell structure. |
| `AETHER_FULL_STACK_INTEGRATION.md` | `256052d1957cb7af0b3e5981417659323e1d5bc8d8d86c19a678cccb8c23df45` | Full-stack note for the shell enclosure. |
| `../README.txt` | `f1d06e9f48996405464363dcd80e33d1e1fd58a7aed6d999c400e68566bb763c` | Portable-package version and shell commands. |
| `../AETHER_LAUNCH.bat` | `1e3b4873e869f07d5c5ec7314d42033a2d4bd243f9d7ea59df7d5f3d408be018` | Launcher routes through the outer shell. |
| `../AETHER_SHELL.ps1` | `4b3e04b0b830b5c692910cd5baae70a3f8ecf2e5e160e6d1ac605cca9b042fc2` | PowerShell quantum-analog enclosure. |
| `umdk.py` | `077566a41d316b8b9eeb5c72584b9644d11b467a19ceba8a3f3ae102058dd69a` | Unchanged authoritative UMDK implementation. |

## 2026-11-25 addendum: protocol consequence layer (v1.2.0)

Version 1.2.0 wires the transferred full stack into the live AETER brain,
memory, and governance cycle without adding a twentieth brain region or
installing process-wide builtin hooks.

* `novel_math.py` introduces Protocol Lyapunov Algebra and Strict Negative
  Reward Reinforcement: bounded violation norms, `R <= 0`, evidence-gated debt
  decay, normalized region credit, and the absorbing `FREEZE` state.
* `negative_reward.py` binds those operators to brain signals, memory scores,
  the 729-cell synaptic matrix, neural reward, and long-term artifacts.
* `protocol_map.py` declares where each transferred module belongs across the
  existing 19 brain regions, the memory layers, and the twelve EMSG laws.
* `AetherKernel` supplies one shared consequence kernel and a hook-free
  full-stack status source to `BrainCortex`. `AetherKernel.status()` and
  `python -m aether --status` expose the compact `full_stack` state.
* CLI and app status now also report `consequence` and
  `consequence_last_step`; execution remains fail-closed with no global hooks
  and no sealed program files by default.
* `src/umdk.py` remains authoritative and unchanged by this addendum.

Verification after this addendum:

- `python -m unittest discover -s tests -p "test_full_stack*.py" -v` — 119 tests, OK.
- `python -m unittest tests.test_full_stack_protocol_map -v` — 7 tests, OK.
- `python -m compileall -q aether tests umdk.py` — OK.
- `python -m aether --full-stack-status` and `--full-stack-step` — OK,
  `global_hooks_installed: false`.
- `python -m aether.full_stack --help` and fresh-process standalone import — OK.
- The broader Windows/Python-3.13 suite retains only its pre-existing POSIX
  permission and SQLite-cleanup failures in unrelated ledger, long-term-memory,
  and CLI tests.

| Path | SHA-256 | Role |
| --- | --- | --- |
| `pyproject.toml` | `5c4fded9948f77fd6ae30d1399415b4094ca3308bccd4ec9e95bd55d9bce2d0c` | v1.2.0 metadata. |
| `aether/version.py` | `eed104785bf265c4470ea5880f8f0206e1bde037aa53f7e37208cedb8a9548aa` | Version 1.2.0. |
| `aether/__init__.py` | `d1e5e4fa5ed1c1a3fbce3ba910f76e039b42dc5df8804fec1ba19bf2ba9b90b2` | Public consequence/kernel exports. |
| `aether/core/kernel.py` | `913a28d3e18a5cb07e7f194bacce0c5b794a5f91f5230e8aac6928024eac6f0f` | Shared kernel binding, status, and long-term/neural consequence path. |
| `aether/brain/cortex.py` | `2f6da5dcc131061eea5ea13802dce8faee51cbf2086be2d454f0b9ebd7c18834` | Optional full-stack assessment and negative-only consequence routing. |
| `aether/full_stack/__init__.py` | `337e188feca0f61874cadea0b834465bb7e572fab48699bdfa3f24c3bf2f83d8` | New formal/protocol exports. |
| `aether/full_stack/integration.py` | `0e6901ec81a613990186931e91586568adc38741a33e0ab383663031d2fd7a45` | Shared consequence kernel and status fields. |
| `aether/full_stack/novel_math.py` | `be530adcc82f3f6b925f24e6fc82c5c9560e2279602787d7886b5a51d9866709` | PLA/SNRR formal operators. |
| `aether/full_stack/negative_reward.py` | `546f0c3470a6d8a75ca3b2a5ced2e095dedeadc9a935a4c172c8f708d726c7f9` | Strict negative-reward consequence kernel. |
| `aether/full_stack/protocol_map.py` | `f88afa6e43b2e0883c257149e287d826b3dc80950abe6b7a3d57a2cb488c83bf` | 19-region brain/memory/law placement. |
| `aether/full_stack/standalone/build_full_stack_original.py` | `65caff955614ad290c6a3fb297c69e2d2b9defb26fdbd99920ee7b934505283a` | Bundle order now includes PLA/SNRR and protocol map. |
| `aether/full_stack/standalone/aether_full_stack.py` | `9ed6a10c08cf91858d11a651b7339d8a21ca48ce0ab94a229fb24a9489ea29c3` | Regenerated 13-module standalone bundle. |
| `tests/test_full_stack_novel_math.py` | `4938ddcd2a6cbada883f820ebc398c2b1d0a082cf457ddbef212a3c64d5c97ba` | Formal operator invariants. |
| `tests/test_full_stack_negative_reward.py` | `bb02dabcb60089090a89177442310b29b6046e3fb846597912b46a9722e2dbb1` | Strict reward and escalation invariants. |
| `tests/test_full_stack_protocol_map.py` | `af6422ef1571acb1240ee364df4d2835cd6fd6f9685cfc9d9e16c2d47b2d73a0` | Placement, attenuation, and live kernel binding. |
| `AETHER_FULL_STACK_INTEGRATION.md` | `aaea3f09962d870c60c430e73d1134b6c3a818400c57c989c5cd30a1ac138aa1` | Operator documentation for v1.2.0. |
| `../README.txt` | `99459176cd1c4d6f1fcb8ee3dc9b293792b099fa5c42086a5e72705d88f4c41e` | Portable-package version and capability notes. |
| `../AETHER_LAUNCH.bat` | `3c98c326d95df588ffd04617f5ff4184ec9715d3fbf9afd18cfeab10e7b2e3bc` | Launcher version banner. |
| `umdk.py` | `077566a41d316b8b9eeb5c72584b9644d11b467a19ceba8a3f3ae102058dd69a` | Unchanged authoritative UMDK implementation. |

## 2026-11-25 addendum: transferred full-stack integration (v1.1.0)

The `aether_transfer_bundle.zip` contents were integrated as
`aether/full_stack/` without replacing the protected top-level `umdk.py`.
The existing app and CLI were extended with fail-closed full-stack status and
supervised-step controls; process-wide builtin hooks remain opt-in.

Verification after the integration:

- `python -m unittest discover -s tests -p "test_full_stack*.py" -v` — 95 tests, OK.
- `python -m aether --full-stack-status` — `FULL_STACK_STATUS`, no global hooks.
- `python -m aether.full_stack --help` and `aether-full-stack --help` — OK.
- `python -m compileall -q aether tests umdk.py ...` — OK.
- The broader Windows/Python-3.13 suite retains its pre-existing POSIX-permission
  and SQLite-cleanup failures; no new full-stack failures were observed.

Selected post-integration digests (the historical hashes below predate this
addendum and are retained as the earlier lifecycle snapshot):

| Path | SHA-256 | Role |
| --- | --- | --- |
| `pyproject.toml` | `867c8aac91a39aee13988f15f98ebcafd256b9b4eab03ae7b3ab22841ddd3466` | v1.1.0 metadata, full-stack packages, console script. |
| `aether/__init__.py` | `3d971f4ae94a9e3c07c7f564b81c6e7cc32ba7d998c9d1667f9600f4ac9726a0` | Public `AetherFullStack` and `full_stack` exports. |
| `aether/app.py` | `15b48a46bcd4cc72d22b8d0f3a161d69ed2175c4d9891230fa770e69e9538607` | Work-panel full-stack status and governed-step controls. |
| `aether/cli.py` | `0ad3969d033f07a60e6f18a040ba1e3afdf045fe44e84eb35428e55dfa6e2362` | Full-stack status/step/persistence flags. |
| `aether/version.py` | `f5570958ab0ef1d1b48e2b7ff4b4e3efd8245aa28ad0bede9ee7e918c5068154` | Version 1.1.0. |
| `aether/full_stack/__init__.py` | `600b957736f9d54c6c1005a29e0486b6de1b41c877030109374e447ad86474f1` | Full-stack package API. |
| `aether/full_stack/__main__.py` | `c219fc716bb25007eede49fabae910aae815309b93466b2d6cf496056e03b6d2` | `python -m aether.full_stack` entry point. |
| `aether/full_stack/integration.py` | `0902aa2159b7cba94a03c2374139731c2731dcaab364efe52465ac801fa81970` | Safe bridge with no global hooks by default. |
| `AETHER_FULL_STACK_INTEGRATION.md` | `582e04c7eb771cc16087caca3f7aaa5ac337147ebf21fa7049d6b19c31b1769a` | Integration/operator documentation. |
| `tests/test_full_stack_integration.py` | `c3b695e03cc71fa0d5298715f508e53a8d6a250f5a054d090b71e64014ff35ed` | Bridge, CLI, app, and safe-default tests. |

## Reorganization decision

No file-cascade reorganization was performed. Moving modules would break
import paths, the standalone `umdk.py` compatibility boundary, and the
authenticated source manifest without improving runtime accuracy. The
manifest below provides the requested organization while leaving the
working tree stable.

## Verification snapshot

- Unit suite: `python3 -m unittest discover -s tests` — 328 tests, OK.
- Scientific benchmark: 25/25 checks, score 1.0.
- Operational CLI pass: 30 commands, all exit 0, zero stderr.
- Fail-closed startup integrity: `INTEGRITY_OK`, file manifest resealed after the final source and test edits.
- Activation controls: offline functions, knowledge bank, cloud server,
  autonomous recall, and hypothesis corollary are explicitly switchable in
  the kernel, CLI, and Tk app.
- Brain/domain sync: every `AetherDomain` maps to active brain regions;
  `domain_sync.coverage_complete` is `True` for the full 19-region set.
- Autonomous recall: bounded, explicit, audited in-process cycles from the
  knowledge bank, encrypted long-term memory, and the synaptic bridge.
- Autonomous hypothesis corollary: deterministic, provenance-bound,
  qualified, offline generator with no generated-code execution.
- Resident capabilities: SCI/OIE status, investigation, and evolution commands pass.
- Encrypted memory/circuit: `LONGTERM_INTEGRITY_OK`, `NEURAL_INTEGRITY_OK`.
- GUI smoke: `DISPLAY=:0 timeout 8s python3 -m aether --app` — timeout 124, zero stderr.
- Startup profile: app construction reduced from ~19 s to ~3 s by reusing the startup integrity report for dashboard status.
- Wheel build: successful (`aether_discovery-1.0.0-py3-none-any.whl`).
- Launcher: `TryExec=/usr/bin/python3`, `StartupWMClass=Aether`, hand/help feedback on actions.
- Launcher smoke: `gtk-launch aether` opens the window with no stderr.
- Desktop icon: single `Science` category, named icon lookup at 48/64/128 px,
  refreshed desktop database, and source-relative launcher command.
- Header mode switcher: `LOCAL | OFFLINE | ONLINE | CLOUD` always visible in
  the app header; the sidebar mode toggle mirrors the same authoritative
  `kernel.set_mode()` path.
- Neural Self-Portrait asset: parsed successfully with 169 `<animate>` elements.
- Dashboard motion: aurora drift, panel arrival/sheen, live ticker, scan sweep, spark flow, gauge shimmer; reduced-motion respected.

All hashes below are SHA-256 digests captured after the final source and
test edits. This manifest does not hash itself. The integrity manifest is
resealed after this file is written.

## Preserved boundaries

- `umdk.py` and the AETHER 1.0 kernel architecture were preserved.
- The knowledge vault remains separate from the credential vault.
- `local|offline|online|cloud` modes remain explicit; network/cloud remain opt-in.
- Cloud server activation remains gated by cloud mode and an enabled adapter.
- Numeric long-term and synapse storage remains encrypted, authenticated, and fail-closed.
- Autonomous recall and corollary generation are explicit, bounded, in-process, audited, and never execute generated code.
- The portrait is an unbound, emergence-capable self-model: recursive emergent meta-cognitive telemetry, governed and audited, not a face or a novelty proof.

## Root documents

| Path | SHA-256 | Role |
| --- | --- | --- |
| `AETHER.md` | `51c7aad3477778e5ae5b1ae2c780cb4148d0faa520b40208ac08ae535098cf1f` | Architecture and operator documentation; brain, memory, portrait, mode, and boundary specifications. |
| `README.md` | `ea3faeef5cde5d12ee6c2f3151d8411d87dec29ff2904ebc1b8e13bc245fe219` | Top-level usage guide; commands for portrait, HUD, HTML dashboard, key generation, memory, and circuit. |

## Root tooling

| Path | SHA-256 | Role |
| --- | --- | --- |
| `aether_integrity.py` | `817522f830802cbf71e137cf7c595231c5312434caf539d0707779c29caf02b4` | Standalone offline seal/verify CLI for the authenticated source manifest. |
| `aether_keygen.py` | `195b05875dca3d0f750cc8e12305be5544f2491e9af6b04a3549155d33cd9215` | Standalone 32-byte cipher key generator/verifier; default ledger key path. |
| `aether_ledger.py` | `f30346ef74295fe3092a4836ce12bff3f4c1149f1a5c27f9e469b8be09d4add8` | Confidential append-only output ledger with encrypted files, catalog, and verifier. |
| `aether_longterm.py` | `a144787860b951cd4f3e633b62cc5788f1525061627f4aefbbb2a612293252f9` | Standalone long-term memory CLI and offline verification tooling. |
| `pyproject.toml` | `d21f7a5e4e51be02abdcf05fabc4bcc11d91a61f2db01f0593c82a1c0243254c` | Package metadata and aether-keygen entry point. |

## aether/ package core

| Path | SHA-256 | Role |
| --- | --- | --- |
| `aether/__init__.py` | `0d7979b280d136257439a815d6646e2fb4ed944326a669d5196fb8ff25991b26` | Package metadata and public exports for the updated subsystems. |
| `aether/app.py` | `127fc17a7880bd007097d8c14e4ed8b783cc2cd659c9de64ff4f9552a9e336b4` | Desktop application wiring; mode/search/cloud controls, resident-kernel status, portrait, and live panels. |
| `aether/charter.py` | `8a4e5f2bfb59f1ae3549241435928190cf0abb716cc0af74b9f9d0912ab0e3ab` | Emergence-permitting charter; audited governance policy and capabilities 09/10. |
| `aether/cli.py` | `942e9efa1d79015a5cf6f4df8d37f7c531244d374cb664367dae543dcade0f4c` | CLI commands for portrait, HUD, HTML, discovery, intelligence, integrity, and key workflows. |
| `aether/events.py` | `33a2d7e48b55d9f9d9da0a19acdfb3e501a66dd75adb63c6eb2682ddeabbec4d` | Bounded event validation, payload normalization, and corrupt-row recovery. |
| `aether/cloud_ledger.py` | `dbc7f51a4ea647e23c8fb1c58fea63ece3c20f407737a2bc5c8605fe71c62d73` | Opt-in encrypted cloud ledger mirror and manifest handling. |
| `aether/config.py` | `cd6ef1297e9b6a13924426235cd6b18a91b68ec7732a0bb6db651075b59b9467` | Runtime envelope, integrity, long-term memory, and neural configuration. |
| `aether/desktop.py` | `7d1554834115fea6aefae5604ef08b190e2f4ec83b6ffba8001f46c13bb821d1` | Desktop launcher metadata; TryExec validation, Aether WM class, icon, and offline defaults. |
| `aether/integrity.py` | `0b4cc9ac3322bcf1a7781d114e9667ad22d1d6969447b1f7c07c5cf335f8c078` | Kernel-side integrity gate, external chain checks, and fail-closed startup behavior. |
| `aether/longterm.py` | `a6cc58aff61c20a3fe14fc0d2a55682b430b0c4f9408eb03f19c91a84ab5a17d` | Encrypted recursive nine-ary long-term memory and reward-linked routing. |
| `aether/neural.py` | `e352f12278898b10c4e61863a73fb6fe56547e47e4dcd5a774abbb59f34d805a` | Event-driven dendrites/soma/axon/synapse circuit over the protected 729-cell core. |

## aether/brain/

| Path | SHA-256 | Role |
| --- | --- | --- |
| `aether/brain/__init__.py` | `d25d4a539b53a66271a0d23ad2589b4507e75ed214c09a9915ece25887ef587a` | Brain package exports for regions, models, and cortex. |
| `aether/brain/base.py` | `71bb758a8d096a485205869eccddf135b8706fad3400d40d1e22a907b74e72bc` | Region contracts and shared analyzer interfaces. |
| `aether/brain/cortex.py` | `22a9726399861b57de9582a9bd4b094559c90bbfd98ebfe45c0df3a1089910ee` | Three-pass region dispatch, routing, digests, and meta-report aggregation. |
| `aether/brain/models.py` | `d850100d40f41d73db13014de9b2495aa7a72a93114b4366fa2f200d5d05d537` | Brain cycle report and knowledge synthesis result models. |
| `aether/brain/regions.py` | `f2224883746c3c0f57547f85c37346a690dcad6eb0320e8cde41b0281a734ee1` | Nineteen domain, integration, and synthesis region implementations. |

## aether/core/

| Path | SHA-256 | Role |
| --- | --- | --- |
| `aether/core/kernel.py` | `1c6cf490340499eb6057dc9e6c196bbe4fca73500658fea40023530ba3be0f1e` | Kernel orchestration; resident SCI/OIE, expanded search, runtime controls, status caching, and integrity. |
| `aether/core/intelligence.py` | `25acb5b2ba02fffeee625cd759a09b032ae75a5ca752fcbf49b16392370a64c9` | Always-resident SCI/OIE kernel; correction, evolution, provenance, and audit lifecycle. |
| `aether/core/state.py` | `7f677c7fa4f304d092e69f15dc4e8d30497d13007f01b89eb91cf1e263578144` | Strict bounded persisted-state loading with fresh-state fallback. |

## aether/discovery/

| Path | SHA-256 | Role |
| --- | --- | --- |
| `aether/discovery/__init__.py` | `81d3caac9a396db9c25ea655794ef0502803fc74986b756f7da6e60ffc4d88d5` | Discovery package exports. |
| `aether/discovery/engine.py` | `e5e375daa760a3104401758b4ee8857a24c9f3c5a18627ec0fbfe21b47033ce1` | Expanded local/online search orchestration with bounded provenance. |
| `aether/discovery/generator.py` | `89444698f40a27f3f55b1ac5a0c17e55d1c0af0ff2fe48cb169ed11756403ac7` | Deterministic candidate strategies, fingerprints, and bounded ceilings. |
| `aether/discovery/novelty.py` | `2d077083a085f04b14e14dc3eb8cfcf04617d162c70a4ed637ccecc43506425b` | Bounded autonomous emergent novelty assessment over candidates, evidence, and graph neighbors. |
| `aether/discovery/search_providers.py` | `6a6be60d24663847d7dd3a48b00b44ca5cd82d5e8d97ba8ca676623b9145e766` | Explicit allowlisted HTTPS adapters, including bounded Atom normalization. |
| `aether/discovery/verification.py` | `2b365b4758cec19a27a213467bbe33725d095f425464078b44f6d4a364a47171` | Autonomous recursive emergent verification of expanded strategies without proof or novelty claims. |

## aether/science/

| Path | SHA-256 | Role |
| --- | --- | --- |
| `aether/science/__init__.py` | `a0b8375ebba6352e52fd4c8212c7962cff58788d0b14fc0753bdfd01f537f2f1` | Scientific package exports including autonomous corollary generation. |
| `aether/science/corollaries.py` | `fcf27ae2361ae816f4594ef988223000a0fd526dd68e64b8cadbe9c967d34c0a` | Deterministic, offline, provenance-bound hypothesis corollary engine. |
| `aether/science/models.py` | `081d12554c7c3e1c36321075b801014682e6653348d0abe355b1b038243d7af6` | Scientific artifact models plus the qualified corollary record. |

## aether/ui/

| Path | SHA-256 | Role |
| --- | --- | --- |
| `aether/ui/__init__.py` | `f8ce389eb5ffba76cd4a8ab5233fba48a83b796899ce8bf492ecefccf87a1661` | UI package exports for HUD, identity, HTML, and portrait components. |
| `aether/ui/aether_portrait.svg` | `b8599abe0953505ec771f8a051a987107b72b123c6e170b90716f44cf403d0a0` | Regenerated standalone animated Neural Self-Portrait SVG asset. |
| `aether/ui/html.py` | `5137cc6c119fd8fc68aaab90dfb376d92d75a116b621aaa8563e6c97fab5f9a7` | Offline HTML dashboard; portrait panel, signature gauges, and tier-flow telemetry. |
| `aether/ui/hud.py` | `ace47cb538b1db62dbdd552e3d50a4e188033af032e6aea17ef8d5c0edccce78` | Terminal HUD; signature panel, signal telemetry, and brain architecture strip. |
| `aether/ui/identity.py` | `ed676cfee6f0d7d03497f34f87dc46734e508dfae5378f4e359ea9bf941f39f5` | ASCII/SVG portrait renderer, five identity signatures, anatomy guides, bounded disclaimers. |
| `aether/ui/portrait_canvas.py` | `8414c6c2646cafc4bbf6906c6534fc615e172bcb234a16adca0817430fbf8072` | Tk living-brain canvas; continuous idle motion, focus, ripples, cascades, anatomy detail. |
| `aether/ui/voice.py` | `80d39e7fc1f4904daa9550e36d2db83a4aa0e7325d31db87ec16aad442785f21` | Optional local speech backend helpers. |

## aether/vault/

| Path | SHA-256 | Role |
| --- | --- | --- |
| `aether/vault/__init__.py` | `111f0a62665a248d895005a458647cef64fe6d6b9c43ba9db76de2913f39003b` | Vault package exports. |
| `aether/vault/bridge.py` | `0b3cea1f82f23d6d73736e87d9d0b752c0215548d55603d652983a621bf7fa76` | Vault-to-synapse transfer bridge and counting/provenance checks. |
| `aether/vault/engine.py` | `00f3b218015b9f7becd0ca54de094086ca96d94058cb77fe07e668c5b94271d3` | Memory vault preservation and recall engine. |
| `aether/vault/evolution.py` | `cb0a756f2f23546a1dbd4f3d66b30e040da251a8160aa991987cea47f79ad8fd` | Vault evolution and abstract-structure growth. |
| `aether/vault/models.py` | `9bb09caf579055bc9a4012e98be29391126877557cd78d1cb7b5e6b0e39c5572` | Vault record and link models. |
| `aether/vault/recombination.py` | `1b6ce9481c9ec1bbd7d823e6309880c4a134b4a1e942469c62b8d55bbe3de138` | Knowledge recombination and invention handoff. |
| `aether/vault/store.py` | `bc458cbfb868c5877015974d91e7cd93f35e1da316a1e5cd4320ce9c8a311e76` | Encrypted/authenticated vault persistence. |
| `aether/vault/understand.py` | `239e9cd872d081f1855cd0758899b85afaf21c8cdf39d1a07ba6fc7c64ce598d` | Vault understanding layer and retrospective analysis. |

## tests/

| Path | SHA-256 | Role |
| --- | --- | --- |
| `tests/test_aether.py` | `4b45d36e1f243f8b449ccbb8e7777f6f63e057653f033eacb486f10a7049573c` | Core kernel, CLI, memory, and envelope behavior tests. |
| `tests/test_aether_activation.py` | `10ba1c60019670a48d16b78cc6d075d81ed3e5b50aa3085c4879e73b414f3fb7` | Activation switches, domain sync, autonomous recall, corollary, CLI, and visual tests. |
| `tests/test_aether_app.py` | `024164d2ef057d55ef1c240a6e4494befa82b3b3d5bfb9bed452a41786f11cc7` | Tk application and live portrait canvas behavior tests. |
| `tests/test_aether_brain.py` | `ca6a6129fa103c475f203b5f103d48e780c6a1b317be4fba6a44f9cb2568e1a5` | Nineteen-region, tier, synthesis, digest, and CLI brain contract tests. |
| `tests/test_aether_discovery_expansion.py` | `a49fea7c36e192a3174d990dfb2ad66b151e172a3414a7ba8557d2357e868f50` | Expanded strategies, bounded local search, and online allowlist tests. |
| `tests/test_aether_integrity.py` | `4cea3b4162037195cef029a5174ba7947e56d8fed2353a9b0d219419b8c2dec` | Integrity seal/verify and fail-closed behavior tests. |
| `tests/test_aether_intelligence.py` | `57de6146f1001bf0e944958fa106b0e87e3680fb0aaa6af31a9986a848ccd9ed` | Resident SCI/OIE, runtime controls, and dashboard telemetry tests. |
| `tests/test_aether_keygen.py` | `aaf1ece67f6655a532cb4ed2bae833ed32503489bfde7af02655ac794c99be96` | Standalone key generation, mode, and verification tests. |
| `tests/test_aether_ledger.py` | `818be2a5d201a74b16beeb04745e3d33e777c5fd34f106bb64783b35303ff954` | Ledger encryption, append-only, catalog, and verification tests. |
| `tests/test_aether_ledger_integration.py` | `e789b1de4fdf0a463b947696d52d265455386c48bfc91a8d836ee30450572562` | Ledger integration and external file coverage tests. |
| `tests/test_aether_longterm.py` | `cf9b7df4004a554df2118329abc093c200d8aa222ec7f21c9576cbef480635c6` | Long-term memory encryption, addressing, recall, and verification tests. |
| `tests/test_aether_neural.py` | `0d885246a5c4cd2796e4a8e227520418a1eba52ce9c6289ea7bdc04a250f993e` | Neural circuit, synapse routing, event flow, and integrity tests. |
| `tests/test_aether_salt_wiring.py` | `3b11761ae511e29bfd99a4f9a6ff48d692f8e4834770fb77aa445b2c34fc3aa6` | Owner-controlled PBKDF2 salt file validation and kernel wiring tests. |
| `tests/test_aether_search_providers.py` | `7ca89e86ef3a2c6c86947fea323994ddaa94c33ef2c98c0b717e8f771f36cc9d` | Atom normalization, provider registry, and offline request suppression tests. |
| `tests/test_aether_validation.py` | `fc87d588a0ec48552697423569a9909a58a41eb21ad8d7560d2a4ba32e4d70b3` | Bounded config, event, and persisted-state validation tests. |
| `tests/test_aether_vault.py` | `ee708ac5d6bc2d691de8ac8eaea8080fd8a86f80b9b3a72ff6555e31c858eaa8` | Vault preservation, recall, and integrity tests. |
| `tests/test_aether_vault_bridge.py` | `33a4533cc90d9a6039ef296923bcb31ca3e6b63489227c54b34b518d39c0e9f4` | Vault-to-synapse bridge tests. |
| `tests/test_aether_visuals.py` | `85fc66b04286393460863be9894e9c0a0dbdcc70d3e9086fdeace212f4cb7fc6` | Terminal/SVG/HTML portrait, signature, tier-strip, and animation tests. |

## Generated operational artifacts outside the repository

- `/tmp/opencode/aether_ops/dashboard.html` — live HTML dashboard preview.
- `/tmp/opencode/aether_ops/portrait.svg` — exported animated portrait.
- `/tmp/opencode/aether_ops/aether_ops.db` — isolated offline operational database.
- `/tmp/opencode/dist/aether_discovery-1.0.0-py3-none-any.whl` — built wheel.
