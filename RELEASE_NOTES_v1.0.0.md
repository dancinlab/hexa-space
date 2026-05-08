# hexa-space v1.0.0 — Space Toolkit (HEXA family) 🚀

**Release date**: 2026-05-06
**Closure verdict**: **SPEC_ONLY** (11/11 verbs spec; 0/11 wired)
**Provenance**: extracted 2026-05-06 from `n6-architecture/domains/space/`
at sha `c0f1f570`. Sister extraction of `hexa-bio` v1.1.0
(biology axis, 4 verbs).

This is the **initial standalone release** of `hexa-space`, an 11-verb
space substrate organized in **4 groups**: **core** (cosmic, starship) ·
**engineering** (aerospace, aerospace_transport, engineering, systems) ·
**observation** (astrodynamics, astronomy, obs_astronomy) · **life**
(astrobiology, medicine). All 11 verbs ship as spec-first design docs;
the working `.hexa` CLI dispatcher is a placeholder.

## Highlights

- **11-verb / 4-group organization** of every space domain currently
  registered under `n6-architecture/domains/space/`.
- **Placeholder CLI dispatcher** (`cli/hexa-space.hexa`) with `status`,
  `group <…>`, `selftest`, `help`, `--version`.
- **n=6 invariant lattice** — `σ(6)=12, τ(6)=4, φ(6)=2, J₂=24`; master
  identity `σ·φ = n·τ = 24`. Hypothesized across all 11 verbs (no in-repo
  empirical verification at v1.0.0 — see Honest scope §3).
- **MIT** license; **zero** runtime deps (no Python, no native build).
- **GitHub-only distribution** — canonical at
  <https://github.com/dancinlab/hexa-space>.

## Installation

```bash
# Recommended (post-hx install registration):
hx install hexa-space@1.0.0
hexa-space --version           # → 1.0.0

# Or git clone (works today):
git clone https://github.com/dancinlab/hexa-space.git ~/.hexa-space
export HEXA_SPACE_ROOT=~/.hexa-space
export PATH="$HEXA_SPACE_ROOT/cli:$PATH"
hexa-space selftest
```

## Quickstart

```bash
hexa-space selftest                    # 11-verb spec presence sweep
hexa-space status                      # 4-group / 11-verb table + caveats
hexa-space group core                  # cosmic, starship
hexa-space group engineering           # aerospace + 3 more
hexa-space group observation           # astrodynamics + 2 more
hexa-space group life                  # astrobiology, medicine
```

## Honest C3 caveats (raw#10)

1. **SPEC_ONLY at v1.0.0** — all 11 verbs ship as `.md` design docs, not
   executable empirical sandboxes. The CLI dispatcher enumerates verbs and
   verifies spec-file presence, but does not run any per-verb simulation.
2. **n=6 lattice claim is hypothesized for all 11 verbs**. No independent
   in-repo verification is performed; the lattice mapping is inherited
   from `n6-architecture/domains/space/` design docs.
3. **Working `.hexa` CLI per verb is TBD.** Numerical sandboxes (analogous
   to `hexa-bio/weave/`'s cage-assembly ODE) are deferred to post-v1
   cycles.

## Provenance

- Extracted from `n6-architecture/domains/space/` at sha `c0f1f570`
  (2026-05-06).
- Sister theory-side substrate: `hexa-cosmos` (cosmology + particle +
  cosmic-observatory).
- Sister starship axis: `hexa-ufo`.
- Sister biology axis: `hexa-bio` v1.1.0.

## License

MIT — see [LICENSE](LICENSE).

Author: 박민우 <nerve011235@gmail.com>
