# 🚀 hexa-space — Space Toolkit (HEXA family)

> **11-verb space substrate** organized in **4 groups** —
> **core** (cosmic, starship) · **engineering** (aerospace, aerospace_transport,
> engineering, systems) · **observation** (astrodynamics, astronomy,
> obs_astronomy) · **life** (astrobiology, medicine). All 11 verbs ship as
> spec-first design docs at v1.0.0; working `.hexa` CLI dispatcher is a
> placeholder.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Version](https://img.shields.io/badge/version-1.0.0-informational.svg)](CHANGELOG.md)
[![Verbs: 11/11 spec](https://img.shields.io/badge/verbs-11%2F11_spec_(0%2F11_wired)-orange.svg)](#verbs)
[![Groups: 4](https://img.shields.io/badge/groups-core_·_engineering_·_observation_·_life-purple.svg)](#verbs)
[![Provenance: n6@c0f1f570](https://img.shields.io/badge/provenance-n6--architecture@c0f1f570-blue.svg)](https://github.com/need-singularity/n6-architecture)

---

## Why

`hexa-space` is the **standalone Space Toolkit** in the HEXA family — a
spec-first, single-source-of-truth substrate that pulls together every space
domain currently registered under
`n6-architecture/domains/space/` into one organized 11-verb CLI surface.
It is the n=6 substrate's empirical companion for the **space axis** (sister
of `hexa-bio` for biology and `hexa-cosmos` for theoretical cosmology).

The 11 verbs are organized into **4 groups**:

```
                      ┌──────────────────────┐
                      │       hexa-space     │
                      │       (n=6 axis)     │
                      └──────────┬───────────┘
                                 │
        ┌─────────────┬──────────┼──────────────┬─────────────┐
        │             │          │              │             │
   ┌────▼────┐   ┌────▼────┐ ┌───▼─────────┐ ┌──▼──────┐
   │  core   │   │engineer-│ │ observation │ │  life   │
   │  (2)    │   │ ing (4) │ │     (3)     │ │   (2)   │
   └─────────┘   └─────────┘ └─────────────┘ └─────────┘
```

The lattice anchors every verb in a single algebraic identity:

```
σ(6) = 12        12 frequency channels / 12 vertices
τ(6) = 4         4 regimes / phase ladder
φ(6) = 2         binary observation dichotomy
J₂   = 24        octahedral rotation group order

master identity:   σ · φ = n · τ = 12 · 2 = 6 · 4 = 24
```

---

## Verbs

11 verbs / 4 groups. Every verb is a `.md` design doc cp -R'd from
`n6-architecture/domains/space/` (provenance sha `c0f1f570`).

### core (2)

| Verb       | Source dir (n6)         | Spec file              |
|------------|-------------------------|------------------------|
| `cosmic`   | `space/hexa-cosmic/`    | `cosmic/hexa-cosmic.md`     |
| `starship` | `space/hexa-starship/`  | `starship/hexa-starship.md` |

### engineering (4)

| Verb                  | Source dir (n6)                  | Spec file                                   |
|-----------------------|----------------------------------|---------------------------------------------|
| `aerospace`           | `space/aerospace/`               | `aerospace/aerospace.md`                    |
| `aerospace_transport` | `space/aerospace-transport/`     | `aerospace_transport/aerospace-transport.md`|
| `engineering`         | `space/space-engineering/`       | `engineering/space-engineering.md`          |
| `systems`             | `space/space-systems/`           | `systems/space-systems.md`                  |

### observation (3)

| Verb            | Source dir (n6)                     | Spec file                                       |
|-----------------|-------------------------------------|-------------------------------------------------|
| `astrodynamics` | `space/astrodynamics/`              | `astrodynamics/astrodynamics.md`                |
| `astronomy`     | `space/astronomy/`                  | `astronomy/astronomy.md`                        |
| `obs_astronomy` | `space/observational-astronomy/`    | `obs_astronomy/observational-astronomy.md`      |

### life (2)

| Verb           | Source dir (n6)         | Spec file                          |
|----------------|-------------------------|------------------------------------|
| `astrobiology` | `space/astrobiology/`   | `astrobiology/astrobiology.md`     |
| `medicine`     | `space/space-medicine/` | `medicine/space-medicine.md`       |

---

## Status

**11-verb 통합 substrate (4 그룹: core + engineering + observation + life).
spec-first (작동 .hexa CLI TBD).**

- All 11 verbs at v1.0.0 ship as **spec-only** (`.md` design docs); the
  CLI dispatcher in `cli/hexa-space.hexa` is a **placeholder** that
  enumerates verbs and group membership but does not run any per-verb
  numerical sandbox.
- The n=6 invariant lattice claim (σ=12, τ=4, φ=2, J₂=24) is hypothesized
  for all 11 verbs; **no in-repo empirical verification** lands at v1.0.0.
- Working `.hexa` CLI per verb (cage-assembly-style numerical sandbox) is
  TBD in post-v1 cycles.
- Verdict: **SPEC_ONLY** (11/11 spec; 0/11 wired).

---

## Install

### Via `hx` (recommended, after registry registration)

```bash
hx install hexa-space          # global, pulls latest from registry
hx install hexa-space@1.0.0    # pin specific version
hexa-space --version           # → 1.0.0
```

### Via git clone (works today)

```bash
git clone https://github.com/need-singularity/hexa-space.git ~/.hexa-space
export HEXA_SPACE_ROOT=~/.hexa-space
export PATH="$HEXA_SPACE_ROOT/cli:$PATH"

# Verify 11/11 verb specs present:
hexa run $HEXA_SPACE_ROOT/cli/hexa-space.hexa selftest

# Browse a group:
hexa run $HEXA_SPACE_ROOT/cli/hexa-space.hexa group observation
```

The repo is **dependency-free** (no Python, no native build). All 11 verb
spec files are pure markdown and are read-only at install time.

---

## Cross-link

- **Sister theory-side substrate**: [`need-singularity/hexa-cosmos`](https://github.com/need-singularity/hexa-cosmos) — cosmology + particle + cosmic-observatory (theory companion to this engineering / observation / life axis).
- **Sister starship axis**: [`need-singularity/hexa-ufo`](https://github.com/need-singularity/hexa-ufo) — extends the `starship` verb with anomaly-vehicle modeling.
- **Sister biology axis**: [`need-singularity/hexa-bio`](https://github.com/need-singularity/hexa-bio) — molecular toolkit (weave/nanobot/ribozyme/virocapsid).
- **Upstream SSOT (specs)**: `n6-architecture/domains/space/` (sha [`c0f1f570`](https://github.com/need-singularity/n6-architecture/commit/c0f1f570)).

---

## License

MIT. See [LICENSE](LICENSE).
