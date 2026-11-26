# AETHER v1.4.0 with ECUCA v2.0.0 — Executive Summary

## About

AETHER is a research architecture for investigating physical, mathematical,
informational, and temporal structure. It synthesizes relational mechanisms,
generates candidates, challenges them, runs bounded experiments, searches for
structural analogies, compares competing explanations, designs discriminating
experiments, attacks its own assessments, and stores provenance.

Version 1.4.0 integrates ECUCA v2.0.0 as an external orthogonal governor.
ECUCA is rotated 90° right as a quadrature controller and remains outside the
AETHER shell. The shell owns the phase-dynamic quantity

\[
\Omega_t = \operatorname{Im}(\overline{z_t}\,z_{t+1}) / dt,
\]

while ECUCA measures quadrature curvature

\[
Q_t = \operatorname{Re}(\overline{z_t}\,z_{t+1}) / dt.
\]

This separation is architectural: the launcher performs a standalone integrity
preflight, then starts the ECUCA governor, then the shell, then AETHER. The
vendored ECUCA module is byte-identical and hash-pinned. Application and CLI
defaults do not patch `open`, `compile`, `exec`, `eval`, or `__import__`;
orthogonality, outside-shell, quadrature, and fail-closed behavior are covered
by dedicated regressions.

## Audit and assurance posture

A fresh full-suite certification passed with 474 tests run, 0 failures, 0
errors, and 2 skips. The integrity verifier was corrected to store and honor
manifest `includes`/`excludes`, with a round-trip regression added. The CLI
exposes `--ecuca-status` and `--ecuca-orthogonal-check`, and the application
surface exposes an “ECUCA orthogonal governor” control.

Claims of novelty are deliberately scoped to **novel within this
architecture**; no claim is made that the underlying mathematics or component
techniques are globally novel.

## Preservation and continuity

The authoritative program is preserved through an encrypted immutable git
repository, an encrypted primary manifest, a hardened runtime configuration,
RFC 3161 externally timestamped certificates, and two offline encrypted USB
copies. Each USB backup uses a distinct passphrase and is bound to its source
volume serial; restore helpers verify the serial before decrypting. No
plaintext passphrase is stored on any volume. Where filesystem-level
encryption was unavailable, access was restricted to SYSTEM and the owning
account.

## Publication scope

This repository is a sanitized public reference, not the authoritative sealed
program distribution. Documentation, including the white paper and change
manifest, is licensed under **CC BY 4.0**. Released source code is licensed
under **Apache 2.0**. Integrity manifests, certificates, timestamp tokens,
keys, salts, encrypted backups, restore helpers, and other sealed artifacts
remain **all rights reserved**. Certified program source files were not
modified to insert copyright headers, preserving their audited hashes.
