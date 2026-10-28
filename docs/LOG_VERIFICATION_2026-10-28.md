# Verification of supplied original QE outputs (2026-10-28)

The user supplied `TaON-PhaseAware-GitHub.zip` containing 37 entries. The two final restart outputs were directly inspected against the corresponding summary CSVs.

| Field | Oxygen vacancy VO | Nitrogen vacancy VN |
| --- | --- | --- |
| Final output in uploaded archive | `qe/VO/relax_restart_04.out` | `qe/VN/relax_restart_06.out` |
| Last `! total energy` (Ry) | -1589.90854898 | -1611.49329867 |
| `bfgs converged` | yes; 16 BFGS steps | yes; 17 BFGS steps |
| `JOB DONE` | yes | yes |
| Last `Total force` (Ry/Bohr) | 0.001535 | 0.002024 |
| Last `total magnetization` (Bohr magneton/cell) | 0.00 | 0.99 |
| Max per-component final force (Ry/Bohr) | 0.00045211 | 0.00058233 |
| `Begin final coordinates` | present | present |

**SHA-256 of uploaded original text files**:

- `qe/VO/relax_restart_04.out`: `8dd98656aab157b53833afa54fb04bcc223ce829e1b4e5eab1be3245a2e2153f`
- `qe/VN/relax_restart_06.out`: `932da8307794869aec7e83524bea5881dbb20e9f7ec260f3190b9c2fe880afe4`

**SHA-256 of relaxed CIF files in the uploaded archive**:

- `structures/VO23_relaxed.cif`: `bc6c69594f80053930ad60876c90b79bf598dc98720781b21d62c5bb6848959a`
- `structures/VN23_relaxed.cif`: `d73b35c33d57e95f8369e98385ae0c538f4fcbb846a37b8a974dd2458ec9bdc3`
- `structures/beta_TaON_relaxed.cif`: `7b3bbd009b5491a980e85d8a84bb0e2378b7b8199d551e66bf921542817af17d`

**Scope of verification:** numeric final energies, BFGS messages, forces, moments and original file presence were checked directly. This is not a claim of independently reproducing QE runs. The 2×1×1 Gamma-only, single-site, neutral-defect model remains preliminary. The complete raw log series will be available in the local ZIP; until all raw records appear in this repository, verification should use the user-supplied archive.
