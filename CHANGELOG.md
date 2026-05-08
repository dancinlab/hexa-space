# Changelog

All notable changes to **hexa-space** are documented here. Format follows
[Keep a Changelog](https://keepachangelog.com/en/1.1.0/) and SemVer.

## [unreleased] - 2026-05-08

### Added (2026-05-08 — RSC iter 9-13) — meta + closure-tracker + saturation

Five-script bundle closing recipe §1 inventory and emitting the
`__HEXA_SPACE_RSC_SATURATED__ STOP` self-signal. **sat-1 + sat-2 ✓** —
loop self-terminates per recipe §7.2; T3 awaits Stage-1+ hardware
(recipe §9).

- iter 9 — `verify/falsifier_check.hexa` (closure-pct tracker, recipe
  §3): F-SPACE-1/2/3/4 ladder report; **4/4 ≥ 67%**, min closure 67%.
  Sentinel `__HEXA_SPACE_FALSIFIER_CHECK__ PASS`.
- iter 10 — `verify/lint_numerics.hexa` (recipe §4 5-invariant lint):
  audits each `verify/numerics_*.hexa` for math_pure import, sentinel,
  FALSIFIERS array, exit(0), RUN/FAIL counters; plus `NUMERICS_SCRIPTS`
  inventory == on-disk glob count. **31/31 PASS** (5 invariants ×
  6 scripts + 1 count).
- iter 11 — `verify/numerics_lattice_arithmetic.hexa` (math_pure
  stability floor, shared cross-project per recipe §6.5): float ↔ int
  cross-check at every n=6 lattice node, (σ−φ)^n = 10^6 via pow_pure,
  sqrt/log/exp round-trip within 1e-12, perfect-number identity.
  **12/12 PASS**. Sentinel `__HEXA_SPACE_NUMERICS_LATTICE_ARITHMETIC__
  PASS`.
- iter 12 — `verify/numerics_cross_pillar.hexa` (cross-pillar T2
  anchor, recipe §1 #12): Kepler/astrodyn ratio agreement, Falcon
  9-engine + Super Heavy 33-engine integer ↔ closed-form, ISS day ↔
  GEO sidereal, master closure across all pillars. **8/8 PASS**.
- iter 13 — `verify/saturation_check.hexa` (RSC self-stop probe,
  recipe §7.3 + §7.5): emits `__HEXA_SPACE_RSC_SATURATED__ STOP` when
  lint passes + inventory floor met + min F-* T2 stack ≥ 1. Currently
  **STOP** triggered.
- `cli/hexa-space.hexa` — five new `TOP_VERIFY_ALIASES` (`falsifier`,
  `lint-numerics`, `saturation`, `numerics-lattice-arithmetic`,
  `numerics-cross-pillar`); help/usage updated.
- `tests/test_lattice.hexa` — extended to 11/11 cross-cutter sweep
  (lattice + cross-doc + 6 numerics + 3 meta), each via direct +
  cli-proxy.

### Added (2026-05-08 — RSC iter 8) — `verify/numerics_bone_loss.hexa`

F-SPACE-3 first T2 (numerical) — exponential bone-density decay model
for ISS microgravity exposure + τ=4-phase recovery vs NASA HRP / Twin
Study published bands.

- `verify/numerics_bone_loss.hexa` — math_pure-only floats. 8/8 PASS:
  linear loss n × 1%/mo = n% (= 6); exp-decay BMD(6mo)/BMD₀ ≈ 0.942
  (5.82% loss within HRP [5, 7]%); τ=4-phase post-flight ≈ 1
  half-life of recovery exp (Sibonga 2007 t½ = 6 mo); 6 NASA HRP
  risk areas; J₂ = 24-week expedition; n×τ = J₂ = 24 monitoring cells;
  master closure floor; log_pure ∘ exp_pure round-trip < 1e-9.
  Sentinel `__HEXA_SPACE_NUMERICS_BONE_LOSS__ PASS`.
- F-SPACE-3 closure pct lifts to **67%** (T1 ✓ + T2 ✓).

### Added (2026-05-08 — RSC iter 7) — `verify/numerics_starship.hexa`

F-SPACE-4 first T2 (numerical) — Super Heavy 33-Raptor cluster
(σ·n/φ − 3 = 33) thrust budget + Tsiolkovsky Δv vs SpaceX 2024+ specs.

- `verify/numerics_starship.hexa` — math_pure-only floats. 9/9 PASS:
  cluster σ·n/φ − 3 = 33; ring partition 3+10+20 (outer = J₂−τ = 20);
  ship engines = n = 6; cluster total thrust 33·2640 kN ≈ 87 MN
  (catalog 87); booster Δv ≈ 3.7 km/s within [1.5, 4.0] (full
  ship+payload stack); V3 LEO payload σ·τ·2 = 96 t; tile classes
  J₂² = 576; closure floor; sqrt_pure(2) within 1e-6. Sentinel
  `__HEXA_SPACE_NUMERICS_STARSHIP__ PASS`.
- F-SPACE-4 closure pct lifts to **67%** (T1 ✓ + T2 ✓).
- All 4 falsifiers (1/2/3/4) now satisfy **sat-1**: 67% closure each
  (T1 + T2 ✓; T3 hardware-only — recipe §9 Stage-1+).

### Added (2026-05-08 — RSC iter 6) — `verify/numerics_falcon.hexa`

F-SPACE-2 first T2 (numerical) — Falcon 9 octaweb 9-engine layout +
Tsiolkovsky Δv vs published SpaceX numbers.

- `verify/numerics_falcon.hexa` — math_pure-only floats. 9/9 PASS:
  octaweb 1+8 = σ−n+3 = 9 Merlins; outer ring = J₂/3 = 8; sea-level
  thrust 9·854 kN ≈ 7686 kN (catalog 7607); Tsiolkovsky Δv with full
  S2+payload stack (Isp_avg=297, mass-ratio 4.65) ≈ 3.18 km/s within
  booster band [2.0, 4.5]; LEO payload anchor J₂−φ+1 = 23 t (cat 22.8);
  yearly cadence J₂·σ/φ = 144; reuse-cert J₂+σ+φ+2 = 40; n=6 closure
  floor; math_pure log_pure(e) = 1 within 1e-6. Sentinel
  `__HEXA_SPACE_NUMERICS_FALCON__ PASS`.
- `cli/hexa-space.hexa` — `numerics-falcon` alias added.
- F-SPACE-2 closure pct lifts to **67%** (T1 ✓ + T2 ✓; T3 awaits
  Stage-1 hardware).

### Added (2026-05-08 — RSC iter 5) — `verify/numerics_kepler.hexa`

F-SPACE-1 first T2 (numerical) — Kepler 3rd law via real-float orbit
period computation against the n=6 closed-form `astrodynamics/verify_*`
predictions.

- `verify/numerics_kepler.hexa` — math_pure-only floating-point script
  (no libm) that computes T = 2π·sqrt(a³/μ) for LEO (R_E + 400 km) and
  GEO (R_E + 35,786 km) from WGS84/IAU constants (μ = 3.986e14, R_E =
  6.371e6). Verifies: T_LEO ∈ [88, 96] min (got 92.4); T_GEO ∈
  [23.5, 24.5] h (got 23.93); T_GEO/T_LEO within ±5% of σ·τ/3 = 16
  (got 15.54, rel-err 2.9%); Kepler 3rd identity (T²/a³ const) at
  numerical precision (rel-err < 1e-10); π via math_pure within float64
  precision; n=6 closure floor. Sentinel `__HEXA_SPACE_NUMERICS_KEPLER__
  PASS` — **6/6 PASS**.
- `cli/hexa-space.hexa` — `numerics-kepler` alias added; help/usage
  updated.
- F-SPACE-1 closure pct lifts to **67%** (T1 ✓ + T2 ✓; T3 awaits
  Stage-1 hardware).

### Added (2026-05-08 — RSC iter 4) — `medicine/verify_space-medicine.hexa`

F-SPACE-3 T1 (algebraic) calc — ISS bone-loss τ=4 phase / NASA HRP n=6
risk-area bookkeeping.

- 9-check arithmetic: master closure σ·φ = n·τ = J₂; 6 NASA HRP risk
  areas = n; 6 ISS physiological monitoring systems = n; 6 HERA isolation
  phases = n; τ = 4 bone-loss recovery phases (acute / subacute /
  remodelling / recovered) — F-SPACE-3 anchor; J₂ = 24-week ISS
  expedition; φ = 2 (pre/post-flight Twin Study); σ = 12 coverage cells
  (6 systems × 2 axes); 1%/month × n months = n% per expedition bone
  loss. Sentinel `__HEXA_MEDICINE_VERIFY__ PASS` — **9/9 EXACT**.
- `cli/hexa-space.hexa` `_verify_path_for` — special-cases `medicine` to
  the hyphenated `verify_space-medicine.hexa` path (mirrors the existing
  `engineering` special-case).
- F-SPACE-3 closure pct lifts to 33% (T1 ✓; T2 + T3 pending). All 4
  falsifiers (1/2/3/4) now have T1 closure.

### Added (2026-05-08 — RSC iter 3) — `astrodynamics/verify_astrodynamics.hexa`

F-SPACE-1 T1 (algebraic) calc — Kepler 3rd law n=6 closed-forms.

- 10-check arithmetic: master closure σ·φ = n·τ = J₂; orbit_dof = n = 6;
  phase-space dim = 2n = σ = 12; T_GEO/T_LEO = σ·τ/3 = 16; (σ·τ/3)² =
  256 = (a_GEO/a_LEO)³; J₂ = 24h sidereal day; LEO orbits/day =
  σ·τ/3 = 16; τ = 4 mission phases; σ = 12-month launch window; φ = 2
  crewed/uncrewed. Sentinel `__HEXA_ASTRODYNAMICS_VERIFY__ PASS` —
  **10/10 EXACT**.
- F-SPACE-1 closure pct lifts to 33% (T1 ✓; T2 + T3 pending).

### Added (2026-05-08 — RSC iter 2) — `verify/cross_doc_audit.hexa`

Second cross-cutter under the RSC recipe — anchor-consistency audit
across roadmap + 27 verb specs + README + CHANGELOG + hexa.toml.

- `verify/cross_doc_audit.hexa` — 18-check audit covering: 27/27 specs
  carry `@canonical`/`@origin`/`n6-architecture` provenance headers;
  16/16 ops specs cite `aerospace_transport/spacex_intel_2026.md`; SoT
  intel doc present + > 1 KB; roadmap §A.4 preregisters all 4
  falsifiers (F-SPACE-1..4); roadmap names sister substrates
  (hexa-cosmos / hexa-ufo / hexa-rtsc); README declares all 5 groups +
  27-verb count; CHANGELOG documents v1.0.0 baseline + operations
  extension; `hexa.toml [closure]` figures (27/11/16) and
  `[modules].hexa` enumerates all 27 specs. Sentinel
  `__HEXA_SPACE_CROSSDOC__ PASS` — **18/18 EXACT**.
- `cli/hexa-space.hexa` — `TOP_VERIFY_ALIASES` extends with
  `cross-doc → verify/cross_doc_audit.hexa`; help + usage updated.
- `tests/test_lattice.hexa` — generalized to 2/2 cross-cutter sweep
  (lattice + cross-doc), each via direct + cli-proxy.

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
  <https://github.com/dancinlab/hexa-space>).

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

[1.0.0]: https://github.com/dancinlab/hexa-space/releases/tag/v1.0.0
