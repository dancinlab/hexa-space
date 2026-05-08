<!-- @canonical: hexa-space@local-draft (Stage-1+ T3 closure path) -->
<!-- @origin:    .roadmap.hexa_space §A.6 (post-RSC saturation 2026-05-08) -->

# 🚀 hexa-space firmware — Stage-1+ T3 closure controllers

> Phase C (sim-firmware) + Phase D (HDL skeletons) for the four
> preregistered F-SPACE-* falsifiers per
> [`.roadmap.hexa_space §A.6.1`](../../.roadmap.hexa_space).
> **Phase E** (physical board) requires funding (~$25 k / board).

---

## §1 Closure tier map

| Falsifier | Stage-1 controller | Phase C sim | Phase D HDL | Phase E board |
|:----------|:-------------------|:-----------:|:-----------:|:-------------:|
| F-SPACE-1 | HEXA-ORBIT-01  (STM32H7)         | ✓ `sim/orbit_pipeline.hexa` (13/13)   | ✓ `hdl/orbit_pipeline.v`   | ✗ funding |
| F-SPACE-2 | HEXA-LAUNCH-01 (Zynq US+ XCZU7EV)| ✓ `sim/launch_telemetry.hexa` (11/11) | ✓ `hdl/launch_telemetry.v` | ✗ funding |
| F-SPACE-3 | HEXA-DXA-01    (STM32H7)         | ✓ `sim/dxa_pipeline.hexa` (11/11)     | ✓ `hdl/dxa_pipeline.v`     | ✗ funding |
| F-SPACE-4 | HEXA-RAPTOR-01 (Kintex US XCKU040)| ✓ `sim/raptor_cluster.hexa` (11/11)  | ✓ `hdl/raptor_cluster.v`   | ✗ funding |

All Phase C sims emit `__HEXA_SPACE_FW_<NAME>__ PASS` and follow recipe §4
5-invariant template (math_pure import / sentinel / FALSIFIERS array /
exit(0) / RUN-FAIL counters).

## §2 Phase scope

**Phase C — sim-firmware** (`firmware/sim/<name>.hexa`)
- Pure-software state-machine model + DAC/ADC pipeline budget +
  safety-interlock latency check.
- No real silicon; runs entirely under `hexa run` interpreter.
- n=6 lattice anchors verified at every check (master closure σ·φ = n·τ
  = J₂ + per-domain identities).

**Phase D — HDL skeleton** (`firmware/hdl/<name>.v`)
- Synthesizable Verilog top-level module, Vivado 2024.1+ (`xc7z020`,
  `xczu7ev`, `xcku040`) or Cube.ai HLS shim for STM32H7.
- **Compiles** but **not flashable** until Phase E boards arrive.
- Encodes the same n=6 lattice values as the sim (`HEXA_REG_ID =
  32'h060C_0402` packing n·σ·τ·φ).

**Phase E — physical board** (out-of-scope until funded)
- Procure: ZCU104 dev kit (~$5 k) · KCU105 (~$5 k) · 2× STM32H7 Nucleo
  (~$200) · DXA scanner USB tap (~$10 k) · HDMI capture card (~$2 k)
- Bench: solder / connector qualification / FCC pre-scan.
- Validate: each board's bitstream against its sim sentinel — if a
  Phase D bitstream's behavioural sim diverges from the corresponding
  `firmware/sim/*.hexa`, the falsifier T3 tier is failed.

## §3 Files

```
firmware/
├── doc/
│   └── README.md                       (this file)
├── sim/                                (Phase C — runs under hexa)
│   ├── orbit_pipeline.hexa             F-SPACE-1
│   ├── launch_telemetry.hexa           F-SPACE-2
│   ├── dxa_pipeline.hexa               F-SPACE-3
│   └── raptor_cluster.hexa             F-SPACE-4
└── hdl/                                (Phase D — Vivado-compileable Verilog)
    ├── orbit_pipeline.v                F-SPACE-1
    ├── launch_telemetry.v              F-SPACE-2
    ├── dxa_pipeline.v                  F-SPACE-3
    └── raptor_cluster.v                F-SPACE-4
```

## §4 Run all Phase C sims

```sh
for f in firmware/sim/*.hexa; do
    HEXA_SPACE_ROOT="$(pwd)" hexa run "$f" | tail -3
done
```

Expected: 4/4 emit `__HEXA_SPACE_FW_*__ PASS` (46/46 individual checks).

## §5 Phase E readiness path

The agent **does not** simulate Phase E (no model can substitute for real
silicon).  Phase E enters scope only when:

1. Funding is committed (`~$25 k` capex per .roadmap §A.6).
2. Board procurement order is placed.
3. A new `.roadmap.hexa_space §A.6.2` adds a Phase E commissioning checklist.
4. New `firmware/board/<name>.md` files document the as-built schematic +
   PCB stack-up + measured performance against the Phase C/D sentinel.

Until then this directory documents the **closure path** but not the
closure event.  T3 stays ✗ in `verify/falsifier_check.hexa`.

— provenance: Phase C+D drafted 2026-05-08, RSC iter 14–17; Stage-1 board
catalog inspired by `hexa-antimatter` Phase C/D template (HEXA-PET-01 etc).
