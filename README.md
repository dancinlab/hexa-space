# 🚀 hexa-space — Space Toolkit (HEXA family)

> **27-verb space substrate** organized in **5 groups** —
> 11 canonical (`n6-architecture`-extracted) +
> **16 operations extension** drafted from SpaceX intel 2026-05-07.
>
> - **core** (cosmic, starship)
> - **engineering** (aerospace, aerospace_transport, engineering, systems)
> - **observation** (astrodynamics, astronomy, obs_astronomy)
> - **life** (astrobiology, medicine)
> - **operations** (ext, 16 — see [§operations](#operations-ext-16--drafted-from-spacex-intel-2026-05-07))
>
> Canonical 11 ship as spec-first design docs (placeholder dispatcher);
> ops 16 ship as **spec + `verify_*.hexa` lattice-closure scripts**
> (16/16 emit `__HEXA_<VERB>_VERIFY__ PASS`). Three test harnesses
> verify regression: `test_selftest` 11/11 · `test_spacex` 5/5 ·
> `test_ops` 16/16.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Version](https://img.shields.io/badge/version-1.0.0-informational.svg)](CHANGELOG.md)
[![Manifest](https://img.shields.io/badge/manifest-hexa.toml-lightgrey.svg)](hexa.toml)
[![Verbs: 27](https://img.shields.io/badge/verbs-27_(11_canonical_+_16_ops)-blue.svg)](#verbs)
[![Wired: 16/27](https://img.shields.io/badge/wired-16%2F27_(16%2F16_ops_+_0%2F11_canonical)-green.svg)](#verbs)
[![Groups: 5](https://img.shields.io/badge/groups-core_·_engineering_·_observation_·_life_·_operations-purple.svg)](#verbs)
[![Provenance: n6@c0f1f570](https://img.shields.io/badge/provenance-n6--architecture@c0f1f570-blue.svg)](https://github.com/dancinlab/n6-architecture)
[![Tests: 32/32 PASS](https://img.shields.io/badge/tests-32%2F32_PASS_(11+5+16)-success.svg)](#verifying)

---

## Why

`hexa-space` is the **standalone Space Toolkit** in the HEXA family — a
spec-first single-source-of-truth substrate that:

1. pulls every space domain registered under
   `n6-architecture/domains/space/` (canonical 11 verbs) into one
   organized CLI surface, and
2. **extends** that core with a 16-verb `operations` group that
   *interprets* SpaceX-domain entities (Starship · Falcon · Dragon ·
   Starlink · DTC · Mars roadmap · MondAloy alloy · …) onto the n=6
   invariant lattice.

It is the n=6 substrate's empirical companion for the **space axis**
(sister of `hexa-bio` for biology and `hexa-cosmos` for theoretical
cosmology).

```
                            ┌──────────────────────┐
                            │       hexa-space     │
                            │       (n=6 axis)     │
                            └──────────┬───────────┘
                                       │
        ┌────────────┬─────────────┬───┴─────────┬───────────┬──────────────┐
        │            │             │             │           │              │
   ┌────▼────┐  ┌────▼────┐  ┌─────▼─────┐  ┌────▼────┐  ┌───▼──────────┐
   │  core   │  │engineer-│  │observation│  │  life   │  │  operations  │
   │  (2)    │  │ ing (4) │  │   (3)     │  │   (2)   │  │ (16, ext)    │
   └─────────┘  └─────────┘  └───────────┘  └─────────┘  └──────────────┘
                                                              ▲
                                                              │
                                                    drafted from SpaceX
                                                    intel 2026-05-07
                                                    (pending-upstream)
```

The lattice anchors every verb in a single algebraic identity:

```
σ(6) = 12        12 frequency channels / 12 vertices
τ(6) = 4         4 regimes / phase ladder
φ(6) = 2         binary observation dichotomy
J₂   = 24        octahedral rotation group order
sopfr(6) = 5     2 + 3 = 5 (sum of prime factors)

master identity:   σ · φ = n · τ = 12 · 2 = 6 · 4 = 24
```

For ops verbs the lattice closes empirically against the SpaceX 2026
snapshot — e.g. `sopfr⁴ · J₂ = 15,000` (DTC FCC filing exact),
`σ·sopfr²/φ = 150` (DTC throughput target Mbps),
`σ·n/φ − 3 = 33` (Super Heavy Raptor count).

---

## Directory layout

```
hexa-space/
├── cli/
│   └── hexa-space.hexa          ← unified dispatcher (status/group/ops/verify/spacex)
├── tests/
│   ├── test_selftest.hexa       ← 11/11 canonical
│   ├── test_spacex.hexa         ← 5/5 spacex-track
│   └── test_ops.hexa            ← 16/16 ops sweep
├── cosmic/  starship/                                   ← core (2)
├── aerospace/  aerospace_transport/  engineering/  systems/   ← engineering (4)
├── astrodynamics/  astronomy/  obs_astronomy/                 ← observation (3)
├── astrobiology/  medicine/                                   ← life (2)
├── spaceship/  satellite/  space_center/  space_ai_center/    ← operations (16, ext)
├── space_datacenter/  falcon/  dragon/  recovery/
├── orbital_depot/  hls/  starlink/  rideshare/
├── station/  mars_base/  direct_to_cell/  mondaloy/
├── aerospace_transport/spacex_intel_2026.md             ← ops data feed (web sweep 2026-05-07)
├── hexa.toml                    ← manifest (27 modules + tests)
├── install.hexa                 ← hx install hook
├── CHANGELOG.md  README.md  RELEASE_NOTES_v1.0.0.md  LICENSE
└── .roadmap.hexa_space          ← terminal goal + checkpoints + falsifiers
```

Quick links:
[`cli/`](cli/) ·
[`tests/`](tests/) ·
[`hexa.toml`](hexa.toml) ·
[`install.hexa`](install.hexa) ·
[`CHANGELOG.md`](CHANGELOG.md) ·
[`LICENSE`](LICENSE) ·
[`.roadmap.hexa_space`](.roadmap.hexa_space)

---

## Verbs

27 verbs / 5 groups. Canonical 11 are `.md` design docs cp -R'd from
`n6-architecture/domains/space/` (sha `c0f1f570`). Operations 16 are
locally drafted; spec MD + `verify_*.hexa` lattice script per verb.

### core (2)

| Verb       | Source dir (n6)         | Spec file              |
|------------|-------------------------|------------------------|
| `cosmic`   | `space/hexa-cosmic/`    | [`cosmic/hexa-cosmic.md`](cosmic/hexa-cosmic.md) |
| `starship` | `space/hexa-starship/`  | [`starship/hexa-starship.md`](starship/hexa-starship.md) |

### engineering (4)

| Verb                  | Source dir (n6)                  | Spec file                                   |
|-----------------------|----------------------------------|---------------------------------------------|
| `aerospace`           | `space/aerospace/`               | [`aerospace/aerospace.md`](aerospace/aerospace.md) |
| `aerospace_transport` | `space/aerospace-transport/`     | [`aerospace_transport/aerospace-transport.md`](aerospace_transport/aerospace-transport.md) |
| `engineering`         | `space/space-engineering/`       | [`engineering/space-engineering.md`](engineering/space-engineering.md) |
| `systems`             | `space/space-systems/`           | [`systems/space-systems.md`](systems/space-systems.md) |

> The `aerospace_transport` verb additionally hosts the SpaceX intel
> data feed: [`aerospace_transport/spacex_intel_2026.md`](aerospace_transport/spacex_intel_2026.md)
> (source of truth for the operations group below) + three companion
> `.hexa` scripts:
> [`verify_spacex.hexa`](aerospace_transport/verify_spacex.hexa)
> (n=6 calculator),
> [`verify_mk_ladder.hexa`](aerospace_transport/verify_mk_ladder.hexa)
> (24-rung future projection through 2050),
> [`analyze_spacex.hexa`](aerospace_transport/analyze_spacex.hexa)
> (23-program registry analyzer).

### observation (3)

| Verb            | Source dir (n6)                     | Spec file                                       |
|-----------------|-------------------------------------|-------------------------------------------------|
| `astrodynamics` | `space/astrodynamics/`              | [`astrodynamics/astrodynamics.md`](astrodynamics/astrodynamics.md) |
| `astronomy`     | `space/astronomy/`                  | [`astronomy/astronomy.md`](astronomy/astronomy.md) |
| `obs_astronomy` | `space/observational-astronomy/`    | [`obs_astronomy/observational-astronomy.md`](obs_astronomy/observational-astronomy.md) |

### life (2)

| Verb           | Source dir (n6)         | Spec file                          |
|----------------|-------------------------|------------------------------------|
| `astrobiology` | `space/astrobiology/`   | [`astrobiology/astrobiology.md`](astrobiology/astrobiology.md) |
| `medicine`     | `space/space-medicine/` | [`medicine/space-medicine.md`](medicine/space-medicine.md) |

### operations (ext, 16) — drafted from SpaceX intel 2026-05-07

Pending upstream landing in `n6-architecture/domains/space/`. Each verb
ships a spec MD + `verify_<verb>.hexa` lattice-closure script and is
runnable via `hexa run cli/hexa-space.hexa verify <verb>`.

| Verb               | Spec file                                                                                  | Verify script                                                                                          | Domain anchor / signature identity                       |
|--------------------|--------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------|----------------------------------------------------------|
| `spaceship`        | [`spaceship/spaceship.md`](spaceship/spaceship.md)                                         | [`verify_spaceship.hexa`](spaceship/verify_spaceship.hexa)                                             | Starship vehicle · `σ·n/φ − 3 = 33` Raptors              |
| `satellite`        | [`satellite/satellite.md`](satellite/satellite.md)                                         | [`verify_satellite.hexa`](satellite/verify_satellite.hexa)                                             | Starlink + Dragon · `sopfr⁴·J₂ = 15,000` (FCC)           |
| `space_center`     | [`space_center/space_center.md`](space_center/space_center.md)                             | [`verify_space_center.hexa`](space_center/verify_space_center.hexa)                                    | Starbase + Cape · `sopfr = 5` active pads                |
| `space_ai_center`  | [`space_ai_center/space_ai_center.md`](space_ai_center/space_ai_center.md)                 | [`verify_space_ai_center.hexa`](space_ai_center/verify_space_ai_center.hexa)                           | autonomy + Optimus · `n·σ·τ = J₂·σ = 288` ctrl-bits      |
| `space_datacenter` | [`space_datacenter/space_datacenter.md`](space_datacenter/space_datacenter.md)             | [`verify_space_datacenter.hexa`](space_datacenter/verify_space_datacenter.hexa)                        | orbital edge compute · `σ = 12` GPU-eq cores/sat         |
| `falcon`           | [`falcon/falcon.md`](falcon/falcon.md)                                                     | [`verify_falcon.hexa`](falcon/verify_falcon.hexa)                                                      | F9 + FH · `J₂ + σ + φ + 2 = 40` reuse cert               |
| `dragon`           | [`dragon/dragon.md`](dragon/dragon.md)                                                     | [`verify_dragon.hexa`](dragon/verify_dragon.hexa)                                                      | Crew + Cargo Dragon · `σ + τ = 16` Dracos                |
| `recovery`         | [`recovery/recovery.md`](recovery/recovery.md)                                             | [`verify_recovery.hexa`](recovery/verify_recovery.hexa)                                                | drone-ship + chopstick · `J₂ − τ = 20` HDA               |
| `orbital_depot`    | [`orbital_depot/orbital_depot.md`](orbital_depot/orbital_depot.md)                         | [`verify_orbital_depot.hexa`](orbital_depot/verify_orbital_depot.hexa)                                 | propellant transfer · `σ = 12` tanker ceiling            |
| `hls`              | [`hls/hls.md`](hls/hls.md)                                                                 | [`verify_hls.hexa`](hls/verify_hls.hexa)                                                               | Artemis HLS Starship · `J₂ = 24` t to surface            |
| `starlink`         | [`starlink/starlink.md`](starlink/starlink.md)                                             | [`verify_starlink.hexa`](starlink/verify_starlink.hexa)                                                | constellation · `sopfr⁴·J₂ = 15,000` DTC sats            |
| `rideshare`        | [`rideshare/rideshare.md`](rideshare/rideshare.md)                                         | [`verify_rideshare.hexa`](rideshare/verify_rideshare.hexa)                                             | Transporter + Bandwagon · `σ² − n·τ − 1 = 119` payloads  |
| `station`          | [`station/station.md`](station/station.md)                                                 | [`verify_station.hexa`](station/verify_station.hexa)                                                   | Vast Haven-1 + Axiom · `τ·τ·n = J₂` mission-days/life    |
| `mars_base`        | [`mars_base/mars_base.md`](mars_base/mars_base.md)                                         | [`verify_mars_base.hexa`](mars_base/verify_mars_base.hexa)                                             | Mars settlement · `sopfr = 5` ships (2026 wave)          |
| `direct_to_cell`   | [`direct_to_cell/direct_to_cell.md`](direct_to_cell/direct_to_cell.md)                     | [`verify_direct_to_cell.hexa`](direct_to_cell/verify_direct_to_cell.hexa)                              | DTC 5G NR · `σ·sopfr²/φ = 150` Mbps target               |
| `mondaloy`         | [`mondaloy/mondaloy.md`](mondaloy/mondaloy.md)                                             | [`verify_mondaloy.hexa`](mondaloy/verify_mondaloy.hexa)                                                | Ni-base superalloy (Raptor 3) · `n·τ·σ = 288` cycle      |

---

## Verifying

Three test harnesses live in [`tests/`](tests/) and are wired into
[`hexa.toml`](hexa.toml) `[test]`:

| Harness                                                      | Scope                                                                          | Result         |
|--------------------------------------------------------------|--------------------------------------------------------------------------------|----------------|
| [`tests/test_selftest.hexa`](tests/test_selftest.hexa)       | 11 canonical verb-spec presence sweep                                          | **11/11 PASS** |
| [`tests/test_spacex.hexa`](tests/test_spacex.hexa)           | spacex track: verify + mk_ladder + analyzer + cli proxy + selftest regression | **5/5 PASS**   |
| [`tests/test_ops.hexa`](tests/test_ops.hexa)                 | 16 ops verb sweep + cli `ops verify-all` proxy                                | **16/16 PASS** |

Run them all:

```bash
HEXA_SPACE_ROOT=$PWD hexa run tests/test_selftest.hexa
HEXA_SPACE_ROOT=$PWD hexa run tests/test_spacex.hexa
HEXA_SPACE_ROOT=$PWD hexa run tests/test_ops.hexa
```

---

## CLI (unified `hexa-space` dispatcher)

Entry: [`cli/hexa-space.hexa`](cli/hexa-space.hexa).

```bash
hexa run cli/hexa-space.hexa <subcmd> [args]
```

| Subcmd                  | Description |
|-------------------------|-------------|
| `status`                | 27-verb status table + caveats |
| `selftest`              | canonical-verb presence sweep (11/11 expected) |
| `group <name>`          | list verbs in `core` / `engineering` / `observation` / `life` / `operations` |
| `ops [list\|verify-all]` | operations registry / 16-verb verify sweep |
| `verify <verb>`         | run `verify_<verb>.hexa` for any registered verb |
| `verify-all`            | run every available `verify_*.hexa` across all 5 groups |
| `spacex <subcmd>`       | SpaceX 2026 program registry (intel/list/active/upcoming/group/show/counts/verify/mk) |
| `--version`             | print version |

Examples:

```bash
hexa run cli/hexa-space.hexa status
hexa run cli/hexa-space.hexa ops verify-all       # 16/16 PASS
hexa run cli/hexa-space.hexa verify mondaloy      # 9/9 EXACT
hexa run cli/hexa-space.hexa verify-all           # all 5 groups
hexa run cli/hexa-space.hexa spacex intel         # SpaceX 2026 snapshot path
hexa run cli/hexa-space.hexa spacex active        # active programs only
hexa run cli/hexa-space.hexa spacex group starship
```

---

## Status

**27-verb 통합 substrate (5 그룹: core + engineering + observation + life + operations).
Canonical 11 spec-only; operations 16 spec + verify_*.hexa lattice-closure (16/16 PASS).**

- 11 canonical verbs at v1.0.0 ship as **spec-only** (`.md` design docs);
  the CLI dispatcher in `cli/hexa-space.hexa` enumerates them but does
  not run any per-verb numerical sandbox.
- 16 operations verbs additionally ship `verify_<verb>.hexa` scripts
  that test n=6 **bookkeeping closure** against the SpaceX 2026
  snapshot — they verify that the count-lattice math is internally
  consistent, **NOT** that SpaceX physics obeys σ=12 / τ=4 / J₂=24.
- The n=6 invariant lattice (σ=12, τ=4, φ=2, J₂=24, sopfr(6)=5) is
  *hypothesized* for canonical verbs and *operationally fitted* for
  ops verbs against documented SpaceX numbers.
- Verdict: **`SPEC_PLUS_OPS_LATTICE`** (27/27 spec; 16/27 wired —
  16/16 ops + 0/11 canonical).

---

## Install

### Via `hx` (recommended, after registry registration)

```bash
hx install hexa-space          # global, pulls latest from registry
hx install hexa-space@1.0.0    # pin specific version
hexa-space --version           # → 1.0.0
```

`hx install hexa-space` pulls all 27 verbs (canonical 11 + operations
16) plus the SpaceX intel data feed (registered in
`hexa.toml [modules].hexa`).

### Via git clone (works today)

```bash
git clone https://github.com/dancinlab/hexa-space.git ~/.hexa-space
export HEXA_SPACE_ROOT=~/.hexa-space
export PATH="$HEXA_SPACE_ROOT/cli:$PATH"

# Verify canonical 11 verb-specs present:
hexa run $HEXA_SPACE_ROOT/cli/hexa-space.hexa selftest

# Verify all 16 operations verbs (lattice closure):
hexa run $HEXA_SPACE_ROOT/cli/hexa-space.hexa ops verify-all

# Browse a group:
hexa run $HEXA_SPACE_ROOT/cli/hexa-space.hexa group operations
```

The repo is **dependency-free** (no Python, no native build). All 27
verb spec files are pure markdown. The 16 ops `verify_*.hexa`
scripts are pure hexa-lang (raw#9 STRICT — no Python).

---

## Cross-link

- **Sister theory-side substrate**: [`dancinlab/hexa-cosmos`](https://github.com/dancinlab/hexa-cosmos) — cosmology + particle + cosmic-observatory (theory companion to this engineering / observation / life axis).
- **Sister starship axis**: [`dancinlab/hexa-ufo`](https://github.com/dancinlab/hexa-ufo) — extends the `starship` verb with anomaly-vehicle modeling.
- **Sister biology axis**: [`dancinlab/hexa-bio`](https://github.com/dancinlab/hexa-bio) — molecular toolkit (weave/nanobot/ribozyme/virocapsid).
- **Upstream SSOT (canonical specs)**: `n6-architecture/domains/space/` (sha [`c0f1f570`](https://github.com/dancinlab/n6-architecture/commit/c0f1f570)).
- **Operations data feed**: [`aerospace_transport/spacex_intel_2026.md`](aerospace_transport/spacex_intel_2026.md) — SpaceX 2026 active+upcoming program registry (web sweep 2026-05-07; 30+ sources cited in §5 of that file).

---

## License

MIT. See [LICENSE](LICENSE).
