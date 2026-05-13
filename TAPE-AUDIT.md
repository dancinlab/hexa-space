# TAPE-AUDIT — hexa-space

## A. Audit-class ledgers

- `state/markers/*.marker` — **543 markers** (`_hexa_args_*`, `_hexa_probe_*`, `_hexa_substr_*`, `_test_math_*`, `analyze_spacex_*`). Mixed — both repo-housekeeping probes and **payload-specific** runs (`analyze_spacex`). Splitting into `state/runs.tape` + `state/payload_analyses.tape` keeps signal-to-noise high.
- `state/hexa_space_cli.log` — CLI log.
- No JSONL.

## B. Identity surface

`AGENTS.md` + `LATTICE_POLICY.md` + `IMPORTED_FROM_CANON.md` + `LIMIT_BREAKTHROUGH.md`. Vehicle stack identity (falcon/dragon/hls — explicit dir names). Fit for `hexa-space/identity.tape` declaring vehicle-stack axes.

## C. Domain.md files

19 root MD files: AEROSPACE-TRANSPORT, AEROSPACE, ASTROBIOLOGY, ASTRODYNAMICS, ASTRONOMY, HEXA-COSMIC, HEXA-STARSHIP, ... `AEROSPACE-TRANSPORT` is already meta-domain-shaped (`AEROSPACE+TRANSPORT.md` candidate). Subdirs (`aerospace_transport/`, `astrobiology/`, `astrodynamics/`, `astronomy/`, `cosmic/`, `direct_to_cell/`, `dragon/`, `falcon/`, `hls/`, `engineering/`) match the root MDs roughly 1:1 — good hygiene.

## D. Per-run/per-event history

`analyze_spacex_*` markers (~5+ visible) are domain-specific per-vehicle analysis runs — exactly the per-event grain `.tape` is for. Each run = `@T analyze_spacex <- @S vehicle=falcon|dragon|hls => @R ok == @D <metrics>`.

## E. Promotion candidates

- **n6 atoms** — orbital-mechanics canon (vis-viva, Hohmann transfer Δv), specific-impulse scaling.
- **hxc binaries** — telemetry timeseries, trajectory tracks, telescope frames.
- **n12 cube cells** — orbit-tier × vehicle-class × mission-phase.

## Verdict

**MEDIUM** — 543 markers split across housekeeping + payload-analysis, clean subdir/MD parity, one `+`-meta candidate. Solid mid-tier tape adoption target.
