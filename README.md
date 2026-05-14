<p align="center">
  <img src="docs/logo.svg" width="140" alt="hexa-space">
</p>

<h1 align="center">🚀 hexa-space</h1>

<p align="center"><strong>HEXA-Space Family</strong> — aerospace · 150/150 EXACT · Egyptian 3+2+1=n</p>

<p align="center">
  <a href="LICENSE"><img alt="License" src="https://img.shields.io/badge/license-MIT-blue"></a>
  <a href="verify/run_all.hexa"><img alt="Verify" src="https://img.shields.io/badge/verify-16%2F16-brightgreen"></a>
  <img alt="Spec" src="https://img.shields.io/badge/version-v1.1.0--pre-success">
  <img alt="Verbs" src="https://img.shields.io/badge/verbs-27%20(11%20canon%20·%2016%20ops)-informational">
  <img alt="Falsifiers" src="https://img.shields.io/badge/F--SPACE--*-4%2F4%20%40%2067%25-informational">
  <img alt="EXACT" src="https://img.shields.io/badge/EXACT-150%2F150-informational">
  <img alt="Sibling" src="https://img.shields.io/badge/sibling-hexa--bio%20·%20hexa--matter%20·%20hexa--physics-blueviolet">
  <a href="https://doi.org/10.5281/zenodo.20102622"><img alt="DOI" src="https://zenodo.org/badge/DOI/10.5281/zenodo.20102622.svg"></a>
</p>

<p align="center">aerospace · n=6 · σ=12 · τ=4 · φ=2 · Egyptian 3+2+1=n · core · engineering · observation · life · operations · Starship · Falcon · Dragon · Starlink · astrodynamics · astrobiology</p>

---

> **27-verb space substrate** in **5 groups** + **runnable surface**
> (RSC saturated 2026-05-08) + **Stage-1 procurement-prep**:
>
> - **core** (cosmic, starship)
> - **engineering** (aerospace, aerospace_transport, engineering, systems)
> - **observation** (astrodynamics, astronomy, obs_astronomy)
> - **life** (astrobiology, medicine)
> - **operations** (ext, 16 — see [§operations](#operations-ext-16--drafted-from-spacex-intel-2026-05-07))
>
> Per `bedrock/docs/runnable_surface_recipe.md` (RSC) — all 4
> preregistered falsifiers `F-SPACE-{1,2,3,4}` reach **67 % closure**
> (T1 algebraic ✓ + T2 numerical ✓; T3 hardware-only awaits Phase F
> funding). `verify/` ships 12 cross-cutter scripts (`lattice_check`,
> `cross_doc_audit`, 6× `numerics_*`, `falsifier_check`, `lint_numerics`,
> `saturation_check`, `board_audit`) + 4 Stage-1 `firmware/sim/*.hexa`
> sim-firmware (Phase C) + 4 `firmware/hdl/*.v` Vivado-synth Verilog
> skeletons (Phase D) + 4 `firmware/board/*/` per-board procurement
> bundles (Phase E — schematic + BOM + PCB stack-up + commissioning
> checklist + KiCad-readable `.kicad_sch`).

---

## Why

`hexa-space` is the **standalone Space Toolkit** in the HEXA family — a
spec-first single-source-of-truth substrate that:

1. pulls every space domain registered under
   `canon/domains/space/` (canonical 11 verbs) into one
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

## Repo layout

```
hexa-space/
├── cli/
│   └── hexa-space.hexa          ← unified dispatcher (status/group/ops/verify/spacex)
├── verify/                       ← RSC §1 cross-cutter inventory (12 scripts + run_all)
│   ├── run_all.hexa              orchestrator: 16/16 (12 verify/* + 4 fw/sim) bookkeeping closure
│   ├── lattice_check.hexa        n=6 master closure across 27 verbs   24/24
│   ├── cross_doc_audit.hexa      anchor consistency across docs       18/18
│   ├── numerics_kepler.hexa      F-SPACE-1 T2 (Kepler 3rd, math_pure)  6/6
│   ├── numerics_falcon.hexa      F-SPACE-2 T2 (octaweb + Tsiolkovsky)  9/9
│   ├── numerics_starship.hexa    F-SPACE-4 T2 (33-Raptor + Δv)         9/9
│   ├── numerics_bone_loss.hexa   F-SPACE-3 T2 (exp-decay + half-life)  8/8
│   ├── numerics_lattice_arithmetic.hexa  math_pure float ↔ int      12/12
│   ├── numerics_cross_pillar.hexa        anchor agreement              8/8
│   ├── falsifier_check.hexa      F-SPACE-* closure-pct tracker         4/4
│   ├── lint_numerics.hexa        recipe §4 5-invariant lint           31/31
│   ├── saturation_check.hexa     RSC self-stop probe (STOP triggered)
│   └── board_audit.hexa          Phase E doc audit                   32/32
├── firmware/                     ← Stage-1+ T3 closure path (.roadmap §A.6)
│   ├── doc/README.md             Phase C/D/E scope + Phase F readiness
│   ├── sim/                      Phase C — sim-firmware (.hexa, runs under hexa)
│   │   ├── orbit_pipeline.hexa            HEXA-ORBIT-01  (F-SPACE-1)  13/13
│   │   ├── launch_telemetry.hexa          HEXA-LAUNCH-01 (F-SPACE-2)  11/11
│   │   ├── dxa_pipeline.hexa              HEXA-DXA-01    (F-SPACE-3)  11/11
│   │   └── raptor_cluster.hexa            HEXA-RAPTOR-01 (F-SPACE-4)  11/11
│   ├── hdl/                      Phase D — Vivado-synth Verilog skeletons
│   │   ├── orbit_pipeline.v               xc7z020 / STM32H7 HLS shim
│   │   ├── launch_telemetry.v             xczu7ev (Zynq US+ ZCU104)
│   │   ├── dxa_pipeline.v                 xc7z020 / STM32H7 HLS shim
│   │   └── raptor_cluster.v               xcku040 (Kintex US KCU105)
│   └── board/                    Phase E — per-board procurement prep
│       ├── README.md                       4-board catalog + KiCad workflow
│       ├── orbit_01/  launch_01/  dxa_01/  raptor_01/
│       │   ├── SCHEMATIC.md      block diagram + net list + power tree
│       │   ├── BOM.csv           line-item BOM with Digi-Key MPNs + prices
│       │   ├── PCB.md            stack-up + outline + routing rules + EMC
│       │   ├── COMMISSIONING.md  Phase F bring-up + closure-event gate
│       │   └── <slug>.kicad_sch  KiCad 7+ root sheet skeleton
│       └── orbit_01/orbit_01.kicad_pro  full KiCad project file
├── tests/                        ← regression harnesses (5 in hexa.toml [test])
│   ├── test_selftest.hexa        11/11 canonical verb-spec sweep
│   ├── test_spacex.hexa          5/5 spacex-track
│   ├── test_ops.hexa             16/16 ops verb sweep
│   ├── test_lattice.hexa         11/11 cross-cutter (verify/) sweep
│   └── test_firmware.hexa        4/4 Phase C sim-firmware sweep
├── cosmic/  starship/                                   ← core (2)
├── aerospace/  aerospace_transport/  engineering/  systems/   ← engineering (4)
├── astrodynamics/  astronomy/  obs_astronomy/                 ← observation (3)
├── astrobiology/  medicine/                                   ← life (2)
├── spaceship/  satellite/  space_center/  space_ai_center/    ← operations (16, ext)
├── space_datacenter/  falcon/  dragon/  recovery/
├── orbital_depot/  hls/  starlink/  rideshare/
├── station/  mars_base/  direct_to_cell/  mondaloy/
├── aerospace_transport/spacex_intel_2026.md             ← ops data feed (web sweep 2026-05-07)
├── hexa.toml                    ← manifest (27 modules + 5 tests)
├── install.hexa                 ← hx install hook
├── CHANGELOG.md  README.md  RELEASE_NOTES_v1.0.0.md  LICENSE
└── .roadmap.hexa_space          ← terminal goal + falsifiers + §A.6 Stage-1+ closure path
```

Quick links:
[`cli/`](cli/) ·
[`verify/`](verify/) ·
[`firmware/`](firmware/) ·
[`tests/`](tests/) ·
[`hexa.toml`](hexa.toml) ·
[`install.hexa`](install.hexa) ·
[`CHANGELOG.md`](CHANGELOG.md) ·
[`LICENSE`](LICENSE) ·
[`.roadmap.hexa_space`](.roadmap.hexa_space)

---

## Closure status (RSC §3 ladder)

Per [`bedrock/docs/runnable_surface_recipe.md`](https://github.com/dancinlab/bedrock) — closure ladder
`0 % → 33 % → 67 % → 100 %` per falsifier.

### Falsifier preregister + tier closure

| Falsifier | Domain anchor | T1 (algebraic) | T2 (numerical) | T3 (hardware) | % |
|:----------|:--------------|:--------------:|:--------------:|:--------------:|:-:|
| F-SPACE-1 | Kepler 3rd law n=6 corrections (Mercury 43″/century baseline) | [`astrodynamics/verify_*`](astrodynamics/verify_astrodynamics.hexa) ✓ | [`numerics_kepler`](verify/numerics_kepler.hexa) ✓ | Phase F+G+H | **67 %** |
| F-SPACE-2 | Falcon 9 9-engine octaweb (3·3 grid = σ−φ+1) | [`falcon/verify_*`](falcon/verify_falcon.hexa) ✓ | [`numerics_falcon`](verify/numerics_falcon.hexa) ✓ | Phase F+G+H | **67 %** |
| F-SPACE-3 | ISS bone-loss τ=4 phase recovery (NASA Twin Study) | [`medicine/verify_*`](medicine/verify_space-medicine.hexa) ✓ | [`numerics_bone_loss`](verify/numerics_bone_loss.hexa) ✓ | Phase F+G+H | **67 %** |
| F-SPACE-4 | Starship 33-Raptor cluster (σ·n/φ−3) | [`spaceship/verify_*`](spaceship/verify_spaceship.hexa) ✓ | [`numerics_starship`](verify/numerics_starship.hexa) ✓ | Phase F+G+H | **67 %** |

`hexa run verify/falsifier_check.hexa` → `__HEXA_SPACE_FALSIFIER_CHECK__ PASS  4/4 ≥ 67%`.
`hexa run verify/saturation_check.hexa` → `__HEXA_SPACE_RSC_SATURATED__ STOP`.

### Phase ladder (closure path)

| Phase | Layer | Status | Artefact |
|:------|:------|:------:|:---------|
| **A** | Recipe baseline (RSC §1 12-cross-cutter inventory) | ✅ | `verify/` |
| **B** | Per-falsifier T1 algebraic + T2 numerical | ✅ | pillar `verify_*` + `verify/numerics_*` |
| **C** | Sim-firmware (state-machine + DAC/ADC pipeline) | ✅ 46/46 PASS | `firmware/sim/*.hexa` |
| **D** | HDL skeleton (Vivado 2024.1+ synthesizable) | ✅ 4/4 boards | `firmware/hdl/*.v` |
| **E** | Procurement prep (schematic + BOM + PCB + commissioning + KiCad) | ✅ 32/32 audit PASS | `firmware/board/*/` |
| **F** | Physical board procurement | ❌ **funding gate ~$26 k** (Stage-1 program) | (external — JLCPCB / PCBWay) |
| **G** | Bench commissioning (per `COMMISSIONING.md` checklists) | ❌ requires F | (external bench) |
| **H** | F-SPACE-N T3 closure event (flips falsifier_check to 100 %) | ❌ requires G | updates `falsifier_check.hexa` F<N>_T3 anchor |

**Stage-1 program cost** (qty 5 each + Vivado license shared) ≈ **$26 k** within `.roadmap §A.6` ~$25 k envelope.

---

## Verifying

Five test harnesses live in [`tests/`](tests/) and are wired into
[`hexa.toml`](hexa.toml) `[test]`:

| Harness                                                | Scope                                                                          | Result          |
|--------------------------------------------------------|--------------------------------------------------------------------------------|-----------------|
| [`tests/test_selftest.hexa`](tests/test_selftest.hexa) | 11 canonical verb-spec presence sweep                                          | **11/11 PASS**  |
| [`tests/test_spacex.hexa`](tests/test_spacex.hexa)     | spacex track: verify + mk_ladder + analyzer + cli proxy + selftest regression | **5/5 PASS**    |
| [`tests/test_ops.hexa`](tests/test_ops.hexa)           | 16 ops verb sweep + cli `ops verify-all` proxy                                | **16/16 PASS**  |
| [`tests/test_lattice.hexa`](tests/test_lattice.hexa)   | 11 RSC cross-cutter (verify/) sweep — direct + cli-proxy each                 | **11/11 PASS**  |
| [`tests/test_firmware.hexa`](tests/test_firmware.hexa) | 4 Phase C sim-firmware sentinel sweep (HEXA-{ORBIT,LAUNCH,DXA,RAPTOR}-01)     | **4/4 PASS**    |

Run them all:

```bash
for t in tests/test_selftest.hexa tests/test_spacex.hexa tests/test_ops.hexa \
         tests/test_lattice.hexa tests/test_firmware.hexa; do
    HEXA_SPACE_ROOT=$PWD hexa run "$t" | tail -3
done
```

### Orchestrator (single .hexa entry-point — sister of `hexa-fusion`/`hexa-rtsc` `run_all`)

```bash
hexa run verify/run_all.hexa   # 16/16 bookkeeping closure across all verify/*.hexa + firmware/sim/*.hexa
# expected tail: __HEXA_SPACE_RUN_ALL__ PASS
```

Coverage table for the orchestrator sweep:

| Tier               | Count | Scripts                                                                          | Result |
|--------------------|:-----:|----------------------------------------------------------------------------------|--------|
| T2 numerical       | 6     | `numerics_{kepler,falcon,starship,bone_loss,lattice_arithmetic,cross_pillar}`    | 6/6    |
| meta cross-cutter  | 6     | `lattice_check`, `cross_doc_audit`, `falsifier_check`, `lint_numerics`, `saturation_check`, `board_audit` | 6/6    |
| Phase C sim-firmware | 4   | `firmware/sim/{orbit_pipeline,launch_telemetry,dxa_pipeline,raptor_cluster}.hexa` | 4/4    |
| **Total**          | **16** | bookkeeping closure across `verify/*.hexa` + `firmware/sim/*.hexa`             | **16/16** |

closure, **NOT** physics-settled. T3 = published-invariant agreement (ISS / SpaceX
FCC / JAXA Kibo / NASA-HRP Twin Study) NOT live raw telemetry or lattice fit.
Underlying space-program CLAIMS (Mars colony, Dyson swarm, interstellar probe,
Starship $200/kg, lunar Gateway, crewed-Mars architectures) remain **UNPROVEN**
until Stage-1+ hardware (Phase F → G → H). Saturated ≠ falsified ≠ confirmed.
See [`LATTICE_POLICY.md`](LATTICE_POLICY.md) §1.2 + [`LIMIT_BREAKTHROUGH.md`](LIMIT_BREAKTHROUGH.md) §5.

Or run any single cross-cutter / firmware sim via the CLI proxy:

```bash
hexa run cli/hexa-space.hexa verify lattice            # 24/24 EXACT
hexa run cli/hexa-space.hexa verify falsifier          # 4/4 ≥ 67%
hexa run cli/hexa-space.hexa verify saturation         # __HEXA_SPACE_RSC_SATURATED__ STOP
hexa run cli/hexa-space.hexa verify board-audit        # 32/32 Phase E doc audit
hexa run cli/hexa-space.hexa verify fw-orbit           # 13/13 sim-firmware
hexa run cli/hexa-space.hexa verify numerics-kepler    # 6/6 Kepler T2
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
| `verify <cross-cutter>` | run any RSC cross-cutter — see table below |
| `spacex <subcmd>`       | SpaceX 2026 program registry (intel/list/active/upcoming/group/show/counts/verify/mk) |
| `--version`             | print version |

### RSC cross-cutter aliases (`verify <name>`)

| Alias | Script | Sentinel | Use |
|:------|:-------|:---------|:----|
| `lattice`                       | `verify/lattice_check.hexa`                  | `__HEXA_SPACE_LATTICE__ PASS`                       | n=6 master closure across 27 verbs (24/24) |
| `cross-doc`                     | `verify/cross_doc_audit.hexa`                | `__HEXA_SPACE_CROSSDOC__ PASS`                      | anchor consistency across docs (18/18) |
| `numerics-kepler`               | `verify/numerics_kepler.hexa`                | `__HEXA_SPACE_NUMERICS_KEPLER__ PASS`               | F-SPACE-1 T2 |
| `numerics-falcon`               | `verify/numerics_falcon.hexa`                | `__HEXA_SPACE_NUMERICS_FALCON__ PASS`               | F-SPACE-2 T2 |
| `numerics-starship`             | `verify/numerics_starship.hexa`              | `__HEXA_SPACE_NUMERICS_STARSHIP__ PASS`             | F-SPACE-4 T2 |
| `numerics-bone-loss`            | `verify/numerics_bone_loss.hexa`             | `__HEXA_SPACE_NUMERICS_BONE_LOSS__ PASS`            | F-SPACE-3 T2 |
| `numerics-lattice-arithmetic`   | `verify/numerics_lattice_arithmetic.hexa`    | `__HEXA_SPACE_NUMERICS_LATTICE_ARITHMETIC__ PASS`   | math_pure float ↔ int floor |
| `numerics-cross-pillar`         | `verify/numerics_cross_pillar.hexa`          | `__HEXA_SPACE_NUMERICS_CROSS_PILLAR__ PASS`         | cross-pillar T2 anchor agreement |
| `falsifier`                     | `verify/falsifier_check.hexa`                | `__HEXA_SPACE_FALSIFIER_CHECK__ PASS`               | F-SPACE-* closure-pct tracker |
| `lint-numerics`                 | `verify/lint_numerics.hexa`                  | `__HEXA_SPACE_LINT_NUMERICS__ PASS`                 | recipe §4 5-invariant lint |
| `saturation`                    | `verify/saturation_check.hexa`               | `__HEXA_SPACE_SATURATION_CHECK__ PASS` + `STOP` signal | RSC self-stop probe |
| `board-audit`                   | `verify/board_audit.hexa`                    | `__HEXA_SPACE_BOARD_AUDIT__ PASS`                   | Phase E doc audit (32/32) |
| `fw-orbit`                      | `firmware/sim/orbit_pipeline.hexa`           | `__HEXA_SPACE_FW_ORBIT_01__ PASS`                   | Phase C sim — HEXA-ORBIT-01 |
| `fw-launch`                     | `firmware/sim/launch_telemetry.hexa`         | `__HEXA_SPACE_FW_LAUNCH_01__ PASS`                  | Phase C sim — HEXA-LAUNCH-01 |
| `fw-dxa`                        | `firmware/sim/dxa_pipeline.hexa`             | `__HEXA_SPACE_FW_DXA_01__ PASS`                     | Phase C sim — HEXA-DXA-01 |
| `fw-raptor`                     | `firmware/sim/raptor_cluster.hexa`           | `__HEXA_SPACE_FW_RAPTOR_01__ PASS`                  | Phase C sim — HEXA-RAPTOR-01 |

Examples:

```bash
hexa run cli/hexa-space.hexa status
hexa run cli/hexa-space.hexa ops verify-all       # 16/16 ops PASS
hexa run cli/hexa-space.hexa verify mondaloy      # 9/9 EXACT
hexa run cli/hexa-space.hexa verify lattice       # n=6 closure 24/24
hexa run cli/hexa-space.hexa verify falsifier     # 4/4 ≥ 67% closure
hexa run cli/hexa-space.hexa verify saturation    # __HEXA_SPACE_RSC_SATURATED__ STOP
hexa run cli/hexa-space.hexa verify fw-orbit      # 13/13 Phase C HEXA-ORBIT-01
hexa run cli/hexa-space.hexa verify board-audit   # 32/32 Phase E docs
hexa run cli/hexa-space.hexa verify-all           # all 5 groups (canonical pillars)
hexa run cli/hexa-space.hexa spacex intel         # SpaceX 2026 snapshot path
hexa run cli/hexa-space.hexa spacex active        # active programs only
hexa run cli/hexa-space.hexa spacex group starship
```

---

## Status

**27-verb 통합 substrate · RSC saturated (sat-1 ✓ + sat-2 ✓ at 2026-05-08) ·
4/4 falsifiers @ 67 % closure · Phase A-E ✓ · Phase F funding-gated.**


- 11 canonical verbs at v1.0.0 ship as **spec-only** (`.md` design docs).
- **20 pillar `verify_<verb>.hexa` scripts** test n=6 **bookkeeping closure**
  against domain anchors (16 ops verbs + aerospace + aerospace_transport
  + engineering + astrodynamics + medicine).  They verify that the
  count-lattice math is internally consistent, **NOT** that physics
  obeys σ=12 / τ=4 / J₂=24.
- **12 cross-cutter `verify/*.hexa` scripts** (RSC §1) close the recipe
  inventory: lattice + cross-doc + 6 numerics + 4 meta (falsifier,
  lint, saturation, board-audit).
- **4 Phase C sim-firmware** scripts model Stage-1 controllers with
  state machines + DAC/ADC pipelines + safety-interlock logic
  (`__HEXA_SPACE_FW_*__ PASS` × 4, 46/46 individual checks).
- **4 Phase D HDL skeletons** (.v Verilog) compile in Vivado 2024.1+
  but are **not flashable** until Phase F boards arrive.
- **4 Phase E procurement-prep bundles** (schematic + BOM + PCB +
  commissioning + KiCad-readable .kicad_sch) document the path to
  ~$26 k Stage-1 board procurement.
- The n=6 invariant lattice (σ=12, τ=4, φ=2, J₂=24, sopfr(6)=5) is
  *hypothesized* for canonical verbs and *operationally fitted* for
  ops verbs against documented SpaceX numbers.  T3 closure event
  (Phase F+G+H) will test whether real silicon agrees with the
  closed-form derivations within recipe-stated tolerances.
- **`verify/run_all.hexa` orchestrator** sweeps 16 scripts (6 T2 numerical +
  6 meta cross-cutter + 4 Phase C sim-firmware) and emits
  `__HEXA_SPACE_RUN_ALL__ PASS` at 16/16 bookkeeping closure — sister
  pattern of `hexa-fusion` / `hexa-rtsc` / `hexa-cern` `run_all`. This is
  **bookkeeping** closure only; ISS/SpaceX/JAXA/NASA flight-data anchors
  use published invariants (NASA-HRP, FCC filings, Kepler 3rd law) NOT
  lattice fit. Space-program CLAIMS (Mars base, Dyson swarm, interstellar,
  crewed-Mars) remain UNPROVEN until Stage-1+ hardware (Phase F-G-H).
- Verdict: **`SPEC_PLUS_OPS_LATTICE_RSC_SATURATED`** (27/27 spec;
  16/27 wired pillar; 12/12 RSC cross-cutter; 16/16 run_all bookkeeping;
  Phase A-E ✓; F-SPACE-1/2/3/4 all 67 %; T3 awaits Phase F).

---

## Install

```bash
# 1. Install hexa-lang (gives you `hexa` + `hx` package manager)
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/dancinlab/hexa-lang/main/install.sh)"

# 2. Install hexa-space
hx install hexa-space
```

## Run

```bash
hexa-space status              # 27-verb status table + caveats
hexa-space selftest            # canonical-verb presence sweep (11/11 expected)
hexa-space group <name>        # list verbs in core/engineering/observation/life/operations
hexa-space ops [verify-all]    # operations-group registry / 16-verb verify sweep
hexa-space verify <verb>       # run verify_<verb>.hexa for any registered verb
hexa-space verify lattice      # n=6 cross-pillar audit
hexa-space verify falsifier    # F-SPACE-* closure-pct tracker
hexa-space verify saturation   # RSC self-stop probe
hexa-space verify board-audit  # Phase E procurement-prep doc audit
hexa-space verify-all          # run every available verify_*.hexa across all 5 groups
hexa-space spacex <subcmd>     # SpaceX 2026 program registry (intel/list/active/upcoming/group/show/counts/verify/mk)

# Orchestrator (sister of hexa-fusion / hexa-rtsc verify/run_all.hexa)
hexa run verify/run_all.hexa   # aggregate sweep — 16/16 verify/*.hexa + firmware/sim/*.hexa (bookkeeping closure)
```

---
## License

MIT. See [LICENSE](LICENSE).
