# Changelog

All notable changes to **hexa-space** are documented here. Format follows
[Keep a Changelog](https://keepachangelog.com/en/1.1.0/) and SemVer.

## [1.0.0] - 2026-05-06

### Added
- Initial standalone extraction from `n6-architecture@c0f1f570`
  (`domains/space/`).
- 11-verb Space Toolkit (HEXA family), organized in **4 groups**:
  - **core (2)** — `cosmic`, `starship`
  - **engineering (4)** — `aerospace`, `aerospace_transport`,
    `engineering`, `systems`
  - **observation (3)** — `astrodynamics`, `astronomy`, `obs_astronomy`
  - **life (2)** — `astrobiology`, `medicine`
- Placeholder CLI router (`cli/hexa-space.hexa`) with subcmds: `status`,
  `group <core|engineering|observation|life>`, `selftest`, `help`,
  `--version`.
- `tests/test_selftest.hexa` smoke harness (11-verb count check).
- `install.hexa` hx hook (raw#9 STRICT — hexa-only orchestration; zero
  Python deps).
- MIT license, README, CHANGELOG, hexa.toml manifest.
- GitHub-only distribution (canonical at
  <https://github.com/need-singularity/hexa-space>).

### Honest scope (raw#10 C3)
- 11/11 verbs ship as **spec-only** (`.md` design docs).
- **0/11 verbs** have a working empirical sandbox in this repo at v1.0.0.
- The CLI dispatcher is a **placeholder** — it enumerates verbs / groups
  and verifies spec-file presence, but does not run any per-verb numerical
  simulation.
- The n=6 invariant lattice (σ(6)=12, τ(6)=4, φ(6)=2, J₂=24) is
  *hypothesized* across all 11 verbs; no independent in-repo verification.

### Provenance
- Extracted from `n6-architecture/domains/space/` at sha `c0f1f570`
  (2026-05-06).
- Sister extractions in the HEXA family: `hexa-bio` v1.1.0
  (4 verbs, biology); `hexa-cosmos` (theory side, cosmology + particle +
  cosmic-observatory); `hexa-ufo` (starship co-axis).

[1.0.0]: https://github.com/need-singularity/hexa-space/releases/tag/v1.0.0
