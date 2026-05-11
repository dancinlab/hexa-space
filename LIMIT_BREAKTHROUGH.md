<!-- @created: 2026-05-12 -->
<!-- @sister: LATTICE_POLICY.md §1.2 -->
---
project: hexa-space
domain: Space substrate — 27-verb (11 canonical + 16 ops) launch/orbit/observation/life/operations bundle
limits_audited: 8
breakthrough_candidates: 3
hard_walls: 4
soft_walls: 2
unclear: 2
---

# LIMIT_BREAKTHROUGH.md — hexa-space

## §1 Domain identification

`hexa-space` is the 27-verb space-systems substrate organised in 5
groups (core / engineering / observation / life / operations). It is
the most physics-bound member of the earth-space-time triad: every
launch, transfer, and interplanetary mission is governed by Tsiolkovsky,
Hohmann, light-time delay, radiation belts and re-entry heat flux. The
operations sub-axis (16 ops verbs, drafted from SpaceX intel 2026-05-07)
introduces resource ceilings (launch $/kg, launch cadence).

The *infrastructure* nature of hexa-space: a launch-and-mission-design
modelling surface whose ceilings are some of the hardest in physics
(rocket equation is exponentially punishing in Δv) plus engineering
ceilings (launch cadence, ISRU readiness) that move on industry-scale
timelines.

## §2 Real limits applicable to this project

| # | Limit | Class | Source / value | Applicability to hexa-space |
|---|-------|-------|----------------|-----------------------------|
| L1 | Tsiolkovsky rocket equation | physics | Δv = Isp · g · ln(m₀/m_f) | HARD WALL. Caps every aerospace / aerospace_transport / cosmic / starship verb. Δv to LEO ≈ 9.4 km/s; LEO→Mars ≈ 3.6 km/s (Hohmann). |
| L2 | Specific impulse ceilings by propulsion | physics | Chemical Isp ≤ ~470 s (H₂/O₂); NTR ≤ ~900 s; ion ≤ ~10⁴ s; fusion ~10⁵–10⁶ s; photon → c | Direct lever in Tsiolkovsky; this is THE breakthrough axis for hexa-space. |
| L3 | Launch cost $/kg to LEO | engineering | Saturn V ~$54,000/kg (FY2025); Falcon 9 ~$2,720/kg; Falcon Heavy ~$1,500/kg; Starship target ~$200/kg (SpaceX 2024) | Caps every operations verb at scale; sets economic feasibility for any non-defence mission. |
| L4 | Hohmann transfer Δv | physics | Earth→Mars Δv ≈ 5.6 km/s total (departure + insertion); 6–8 month transit | Combined with L1, sets minimum mass-to-Mars; ITS / Starship architecture must match. |
| L5 | Light-time delay (c) | physics | c = 2.998 × 10⁸ m/s; Earth-Mars one-way ≈ 3–22 min (depending on opposition); Earth-Pluto ≈ 4–6 hr | HARD WALL on real-time telerobotics, control loops; binds astrodynamics / observation / operations verbs. |
| L6 | Radiation environment | physics | Van Allen belts (proton flux > 10⁶ cm⁻²s⁻¹); GCR dose-equivalent ≈ 0.6 Sv/yr at Mars surface (NASA HRP) | Caps human-mission durations and electronics; binds space-medicine verb and electronics shielding. |
| L7 | Re-entry heat flux | physics | q ∝ ρ^(0.5) v^3; Mars EDL peak q ~ 1.2 MW/m² (MSL); Earth lunar-return ~7 MW/m² | Caps TPS mass for re-entry verbs and operations sub-axis. |
| L8 | Launch cadence | engineering | SpaceX 2024 ≈ 134 Falcon launches; Starship 5+ test flights; global all-providers ≈ 250/yr (FAA AST 2024 data) | Caps the operations-verb throughput; sets a floor on mass-to-orbit per calendar year. |

(Skipped: lattice / n=6, σ(6)=12 anchors per LATTICE_POLICY §1.3 — they
are organising vocabulary for the 27-verb / 5-group partition.)

## §3 Per-limit breakthrough assessment

| Limit | Class | Current state | Breakthrough vector | Trigger metric |
|-------|-------|---------------|---------------------|----------------|
| L1 Tsiolkovsky | HARD_WALL | Exponential in Δv; chemical mass ratio LEO ~25:1 | None for the equation; only Isp (L2), staging, or in-situ refuel can move m₀/m_f | A verb output claiming sub-Tsiolkovsky Δv ⇒ falsified |
| L2 Isp ceiling | BREAKABLE_WITH_TECH | Chemical ~470 s realised; NTR demoed (NERVA); ion realised (Dawn 3,100 s) | NTR for cargo, fusion drive (long-term), light-sail (Breakthrough Starshot) | One operational ≥ 1,500 s Isp drive on a Mars-cargo class mission |
| L3 Launch $/kg | BREAKABLE_WITH_TECH | Falcon 9 ~$2,720/kg; Starship target ~$200/kg | Full rapid reuse (booster + ship), high cadence amortisation | $/kg-to-LEO ≤ $500 over 100+ flight rolling window |
| L4 Hohmann Δv | HARD_WALL | 5.6 km/s Earth-Mars; orbital mechanics fixed | None for two-impulse Hohmann; lower with continuous-thrust low-thrust transfer (but trip time ↑) | Continuous-thrust trajectory with Δv-equivalent ≤ 4 km/s and time ≤ 200 d |
| L5 c / light-time delay | HARD_WALL | c is a constant of nature | None; only autonomy on the spacecraft side compensates | n/a |
| L6 Space radiation | SOFT_WALL | GCR shielding by mass (>30 g/cm² for ~50 % reduction); hydrogen-rich | Better shielding materials (HDPE, water walls), magnetic deflection (research), faster transit (L2) | Crew GCR dose ≤ 0.3 Sv per Mars mission |
| L7 Re-entry heat flux | SOFT_WALL | PICA, AVCOAT, SpaceX heat-shield tiles ≤ ~3 MW/m² operational | Higher-temp ablatives, transpiration cooling, mid-L/D entry profiles | Mars-class EDL with TPS mass < 8 % of entry mass |
| L8 Launch cadence | UNCLEAR | ~250/yr globally 2024 | Reusable boosters at high frequency, mass-production fabrication | ≥ 1,000 launches/yr globally |

## §4 Top-3 breakthrough opportunities (this project)

1. **L2 — Higher Isp propulsion.** This is the single biggest lever in
   hexa-space because Tsiolkovsky is exponential in Δv/Isp. Chemical →
   NTR (DRACO, NASA/DARPA 2027 demo target) doubles Isp; chemical →
   ion already realised on Dawn / BepiColombo for low-thrust missions.
   A serious hexa-space architecture must split *cargo* (high-Isp,
   slow) from *crew* (chemical, fast) per NASA Mars Architecture 7.0.
   Concrete trigger: at least one in-flight Isp ≥ 1,500 s drive
   referenced in `aerospace/` or `cosmic/`. Risk: medium (NTR
   regulatory / fission-in-space).
2. **L3 — Launch $/kg below $500.** The Starship roadmap (~$200/kg
   target) lowers the *economic* ceiling under which every other space
   verb operates. Verifiable trigger: $/kg-to-LEO ≤ $500 over a
   100-flight rolling window (FAA AST + payload-mass-actual). Risk:
   low-medium (proven downward trend).
3. **L6 — Radiation dose for crewed Mars.** With faster transit (L2) +
   better shielding, the NASA-HRP 0.3 Sv-per-mission threshold is
   reachable. This is enabling for the SPACE-MEDICINE verb and entire
   life sub-axis. Risk: high (no full validation yet).

## §5 Honest caveats (raw#10 C3)

- Tsiolkovsky (L1) is the most important HARD WALL in this entire
  bundle. No clever architecture brute-forces it. The ONLY paths are
  (a) better Isp, (b) staging, (c) in-situ refuel (ISRU). Any verb
  claim that ignores Tsiolkovsky is falsified.
- The speed of light (L5) is a hard wall. Real-time tele-robotics
  beyond cislunar is impossible; autonomy is the *only* answer.
  Hexa-space operations verbs must report autonomy-mode design.
- Launch $/kg (L3) is *economic* not physical — Starship's target
  $200/kg is contingent on rapid reuse achieving aircraft-like turn
  times (target ~24 h). Real-world 2024 turn times are still measured
  in weeks. Honest framing.
- The 27-verb / 5-group structure is organisational vocabulary, not a
  space-physics invariant. Nothing in orbital mechanics requires n=27
  or 5 groups — these are project decisions.
- Hohmann Δv (L4) is exact for impulsive two-burn transfers; gravity
  assists (Voyager, JUICE) and low-thrust continuous burns provide
  legitimate alternatives but at the cost of trip time.
- GCR is the most uncertain crew limit; NASA HRP risk model has wide
  bounds (factor of ~3) on lifetime cancer risk per mission.

## §6 References

- `LATTICE_POLICY.md` §1.2 (universal real-limits standard, 2026-05-12)
- NASA Mars Architecture 7.0 (2024 release) — chemical vs NTR split
- NASA Human Research Program (HRP) — space-radiation risk model
- FAA AST 2024 — Commercial Space Transportation statistics
- NASA NTP DRACO program — NTR Isp ≈ 900 s target
- SpaceX 2024 IAC — Starship cost target ~$200/kg-to-LEO
- Tsiolkovsky (1903), Hohmann (1925), Oberth (1929)
- NREL / NASA-Glenn ion-drive program — Dawn / NEXT-C performance
