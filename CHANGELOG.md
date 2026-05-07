# Changelog

All notable changes to **hexa-space** are documented here. Format follows
[Keep a Changelog](https://keepachangelog.com/en/1.1.0/) and SemVer.

## [unreleased] - 2026-05-08

### Added (2026-05-08 — RSC iter 1) — top-level `verify/` cross-cutter

Initial application of the **Runnable Surface Construction** (RSC) recipe
from `bedrock/docs/runnable_surface_recipe.md` (hexa-cern v1.1.0-pre
provenance). Begins closure-depth accumulation against `.roadmap.hexa_space
§A.4` falsifier preregister (F-SPACE-1/2/3/4).

- `verify/lattice_check.hexa` — repo-overall n=6 invariant audit covering
  arithmetic closure (σ·φ = n·τ = J₂ = 24), σ²/payload-band/Super-Heavy
  Raptor identities, roadmap §A.1 lattice declarations, §A.4 falsifier
  preregister, canonical-pillar n=6 lattice tokens (cosmic / starship /
  astrodynamics / astronomy / obs_astronomy / astrobiology / medicine),
  J₂ cross-pillar token sweep (≥ 6 of 11 hits), 16/16 ops `verify_*.hexa`
  presence, and `hexa.toml [closure]` raw#10 C3 honesty.
  Sentinel `__HEXA_SPACE_LATTICE__ PASS` — **24/24 EXACT**.
- `cli/hexa-space.hexa` — `verify` subcmd extended with cross-cutter
  resolution (`TOP_VERIFY_ALIASES`); `verify lattice` proxies the new
  `verify/lattice_check.hexa`. Per-verb `verify <verb>` path unchanged.
- `tests/test_lattice.hexa` — regression guard: direct + cli-proxy both
  must emit `__HEXA_SPACE_LATTICE__ PASS`.
- `hexa.toml [test].files` — `tests/test_lattice.hexa` registered (4/4).

## [unreleased] - 2026-05-07

### Added — `operations` extension group (16 new verbs)

A new 5th group `operations` interpreting SpaceX-domain entities as
hexa-* verbs on the n=6 lattice. Each verb ships with a spec MD +
verify_*.hexa companion. **16/16 emit `__HEXA_<VERB>_VERIFY__ PASS`.**

| # | Verb | Domain anchor |
|---|------|--------------|
| 1 | `spaceship` | Starship vehicle (n=6 ship engines, σ·n/φ−3 = 33 booster Raptors) |
| 2 | `satellite` | Starlink V2/V3 + Dragon platform (sopfr⁴·J₂ = 15,000 DTC FCC) |
| 3 | `space_center` | Starbase + Cape + Vandenberg (sopfr=5 active pads, 146/yr cap) |
| 4 | `space_ai_center` | launch-AI + Optimus autonomy (n=6 control loops) |
| 5 | `space_datacenter` | orbital edge-compute fabric (σ=12 GPU-eq cores per V3 sat) |
| 6 | `falcon` | Falcon 9 + FH (σ−n+3 = 9 Merlins, J₂+σ+φ+2 = 40 reuse cert) |
| 7 | `dragon` | Crew/Cargo Dragon (n=6 seats max, σ+τ = 16 Dracos) |
| 8 | `recovery` | drone-ship + chopstick (n/φ = 3 ASDS, J₂−τ = 20 HDA) |
| 9 | `orbital_depot` | Starship prop transfer (σ=12 tanker ceiling, J₂=24h window) |
| 10 | `hls` | Artemis HLS Starship (n=6 landing engines, J₂=24 t to surface) |
| 11 | `starlink` | constellation service (sopfr⁴·J₂ = 15,000 DTC additional sats) |
| 12 | `rideshare` | Transporter+Bandwagon (sopfr=5/yr, σ²−n·τ−1=119 payloads) |
| 13 | `station` | Vast Haven-1 (τ=4 crew × τ=4 missions × n=6 days = J₂=24 days) |
| 14 | `mars_base` | Mars settlement (sopfr=5 ships in 2026/27, J₂−τ=20 in 2028/29) |
| 15 | `direct_to_cell` | DTC service (σ·sopfr²/φ = 150 Mbps target) |
| 16 | `mondaloy` | Ni-base superalloy (n=6 elements, σ=12 chamber zones, J₂=24h overhaul) |

### Added — unified CLI extensions

- `cli/hexa-space.hexa` extended:
  - new top-level `ops [list|verify-all]` — ops-group registry / 16-verb verify sweep
  - new `verify <verb>` — runs `verify_<verb>.hexa` for any registered verb
  - new `verify-all` — runs every available verify_*.hexa across all 5 groups
  - existing `spacex` subcommand (intel/list/active/upcoming/group/show/counts/verify/mk)
  - existing `selftest` preserved — 11/11 canonical (back-compat, unchanged)
- `tests/test_ops.hexa` — 16/16 ops verify sweep + cli proxy regression guard

### Added — `aerospace_transport` SpaceX track (data feed)

- `aerospace_transport/spacex_intel_2026.md` — doc-first SpaceX 2026
  active+upcoming program registry. **Source-of-truth** for the 16
  ops verbs above.
- `aerospace_transport/verify_spacex.hexa` — n=6 invariant calculator
  (10/10 EXACT). Sentinel `__HEXA_SPACEX_VERIFY__ PASS`.
- `aerospace_transport/verify_mk_ladder.hexa` — Mk-ladder future
  projection (24-rung J₂-anchored, future items r=8..24 through 2050
  colony goal). Sentinel `__HEXA_SPACEX_MK_LADDER__ PASS`.
- `aerospace_transport/analyze_spacex.hexa` — 23-program registry analyzer.
- `tests/test_spacex.hexa` — 5/5 smoke harness.

### Fixed

- `cli/hexa-space.hexa::_split_pipe` — replaced broken JS-style
  `s.substr(i, i+1)` byte-walker with `s.split("|")`. The old version
  silently aliased to `s.substring(i, 2*i+1)` (since `.substr` is
  JS-style: 2nd arg = *length*) and made `selftest`/`status`/`group`
  crash with `index 1 out of bounds`. Now all three pass.

### Closure update (raw#10 honest C3)

- 27 verbs total: 11 canonical (unchanged spec-only) + 16 operations
  (spec + verify_*.hexa lattice-closure). Verdict bumped to
  `SPEC_PLUS_OPS_LATTICE`.
- Operations verbs are **drafted locally**; not yet upstream in
  `n6-architecture/domains/space/`. Cross-link headers mark each as
  `pending-upstream`.

### Provenance

- Pattern reference (structure only — no code dependency):
  `hexa-sscb` doc-first 4-place layout (verify/build/tests/firmware).
  hexa-space adopts the *spirit* (verify_*.hexa per verb-dir + tests/
  harness + doc-first .md SoT) without restructuring its layout.
- SpaceX data feed: WebSearch sweep 2026-05-07 — 30+ sources cited in
  `aerospace_transport/spacex_intel_2026.md` §5.

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
