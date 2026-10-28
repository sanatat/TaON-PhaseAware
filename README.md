# TaON-PhaseAware

**Literature-aware analysis and preliminary DFT of oxygen/nitrogen vacancies in monoclinic β-TaON**

This repository is a reproducible research-workflow demonstration combining published TaON synthesis/photoelectrochemical evidence with a *preliminary* low-memory Quantum ESPRESSO defect study. It is **not** a publication or a validated prediction of photocatalytic activity.

## Scope and provenance

The original `TaON-PhaseAware-v4` archive supplied on **28 October 2026** contains Python analysis, curated literature data, plotting scripts, DFT input-generation helpers and tests. Its **25 archived entries do not contain the actual 2026 QE output files, final CIF geometries or pseudopotentials**. Code checks passed locally (10 tests). The preliminary defect figures below were transcribed from the researcher's terminal reports in this project discussion; **they have not been independently re-parsed from raw QE outputs in this repository**. Please do not cite them as a validated open dataset.

## Preliminary local defect pilot — reported values

Model: a 2×1×1 expansion of a 12-atom monoclinic TaON candidate (24 atoms pristine; 23 after removing one anion), spin-polarized PBE with SSSP 1.3 Efficiency UPFs, Quantum ESPRESSO 7.5, fixed-cell BFGS ionic optimization, Γ-only sampling, `ecutwfc=78 Ry`, `ecutrho=624 Ry`. Both jobs reportedly reached `bfgs converged`; their final structural files remain on the local workstation.

| Observable | Oxygen vacancy V_O | Nitrogen vacancy V_N |
| --- | ---: | ---: |
| Formula | Ta8N8O7 | Ta8N7O8 |
| Initial SCF total energy (Ry) | -1589.86304583 | -1611.43001577 |
| Final relaxed total energy (Ry) | -1589.90854898 | -1611.49329867 |
| Mean atomic displacement (Å) | 0.073734 | 0.097689 |
| Maximum atomic displacement (Å) | 0.134466 | 0.262767 |
| Final total magnetization (μB/cell) | ~0 | 0.99 |
| Maximum reported Cartesian force component (Ry/Bohr) | 0.00045211 | 0.00058233 |
| BFGS ionic convergence | Reported yes | Reported yes |

The VN vacancy has larger mean atomic displacement in this **single limited cell/site comparison**, and displays ~1 μB total magnetization in this specific spin-polarized calculation. Neither observation proves a general structural preference or a stable magnetic ground state. The absolute energies of V_O and V_N **must not be compared directly**: their compositions differ.

A structured copy with precise evidence level is in `results/terminal_reported_pilot.csv`.

## Key limitations / unfinished validation

- **No defect formation energies.** A compatible pristine 24-atom electronic calculation, suitable O/N chemical potentials, and convergence of *energy differences* are still needed. The previously completed pristine fixed-occupation run is not a matched reference for both spin-polarized defect cells.
- The 2×1×1 Γ-only test uses one vacancy position per anion species and a high effective vacancy concentration (12.5% of that anion sublattice). Supercell sizes, inequivalent sites, occupation, magnetization seeds and k-point grids require testing.
- A Materials Project structural candidate (mp-4165) was used in the user's local study; experimental phase matching and structural provenance require full verification, not just a compatible space group.
- No density of states, charged-defect analysis, charge-transition levels, kinetic barriers, or photocatalytic performance improvements are established here.
- Exact QE input/output files, UPF checksums and optimized CIFs are **not present in the currently uploaded v4 ZIP** and must be added before considering the DFT values independently reproducible.

## Original project workflow

The source archive also includes scripts and tests for phase-aware literature comparisons. For the **complete local source**, use the accompanying release archive until it is uploaded into this repository.

Typical local requirements: Python 3, `numpy`, `matplotlib`, and `pytest`. For actual DFT work, also install `ase`, valid crystallographic structures, matching pseudopotentials and QE.

Useful literature anchors:
- β-TaON phase-control study: [DOI:10.1039/D5DT01193K](https://doi.org/10.1039/D5DT01193K)
- V-doped TaON: [DOI:10.1002/smll.202510276](https://doi.org/10.1002/smll.202510276)
- Earlier ammonolysis series: [DOI:10.1155/2013/507194](https://doi.org/10.1155/2013/507194)

## Intended next additions

The signed-off GitHub export from the *actual workstation* should contain: final `VO23_relaxed.cif` and `VN23_relaxed.cif`, QE inputs and readable text outputs, structural-source metadata, computed displacement tables, methods, and hashes. Large scratch directories, wavefunctions and pseudopotential binaries should not be committed.

**Project status:** transparent preliminary research demonstration; additional source artifacts pending.
