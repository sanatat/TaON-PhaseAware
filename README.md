# TaON-PhaseAware

**Preliminary fixed-cell DFT relaxation of oxygen and nitrogen vacancies in monoclinic β-TaON**

This repository documents a low-memory Quantum ESPRESSO 7.5 study conducted in October 2026. The numerical results were **cross-checked on 28 October 2026 against the original final QE output files contained in a separately supplied local archive**. A log verification report and SHA-256 checksums are available in [docs/LOG_VERIFICATION_2026-10-28.md](docs/LOG_VERIFICATION_2026-10-28.md).

**Important status:** the GitHub repository currently contains the verified CSV summary, per-atom displacement table, pseudopotential metadata and verification documentation. The three optimized CIF structures **are now committed** to GitHub. The original QE SCF and sequential relaxation input/output text logs for both vacancies are now committed under `qe/VO/` and `qe/VN/`. The relaxed CIF files and tabulated displacement results are also public. Additional numerical convergence checks are still required for quantitative defect thermodynamics.

## Verified preliminary numerical results

| Quantity | Oxygen vacancy V_O | Nitrogen vacancy V_N |
|---|---:|---:|
| Formula | Ta8N8O7 | Ta8N7O8 |
| Initial SCF energy (Ry) | -1589.86304583 | -1611.43001577 |
| Final relaxed energy (Ry) | -1589.90854898 | -1611.49329867 |
| Relaxation energy decrease (eV) | 0.619102 | 0.861008 |
| Mean minimum-image displacement (Å) | 0.073734 | 0.097689 |
| Maximum minimum-image displacement (Å) | 0.134466 | 0.262767 |
| Final total magnetization (μB/cell) | 0.00 | 0.99 |
| Max Cartesian force component (Ry/Bohr) | 0.00045211 | 0.00058233 |
| BFGS convergence | Confirmed from local output | Confirmed from local output |

Values correspond to one selected neutral vacancy per 24-atom supercell (23 remaining atoms). The pilot used 2×1×1 cell expansion, Γ-only sampling, PBE-based SSSP pseudopotentials, 78 Ry wavefunction / 624 Ry density cutoffs, spin polarization, and fixed-cell BFGS geometry optimization. The final logs showed `bfgs converged` and `JOB DONE`. Original logs were provided and directly inspected, not computationally rerun here.

## Repository layout

- [results/summary.csv](results/summary.csv): scalar results.
- [results/per_atom_displacements.csv](results/per_atom_displacements.csv): minimum-image displacement table, 23 atoms for each vacancy.
- [metadata/sssp_cutoffs.json](metadata/sssp_cutoffs.json): pseudopotential metadata.
- [docs/LOG_VERIFICATION_2026-10-28.md](docs/LOG_VERIFICATION_2026-10-28.md): direct checks of original log outputs and cryptographic hashes.
- [docs/COMPUTATIONAL_PROVENANCE.md](docs/COMPUTATIONAL_PROVENANCE.md): methods, assumptions and planned validation.
- [structures/](structures/): pristine TaON, relaxed VO and VN CIFs.
- [qe/VO/](qe/VO/) and [qe/VN/](qe/VN/): original QE SCF and sequential BFGS restart input/output files.

## Scientific interpretation and limitations

The mean relaxation displacement is larger for this nitrogen-vacancy configuration than for this oxygen-vacancy configuration. In the chosen spin-polarized calculation, V_N retains ~0.99 μB/cell while V_O converges to approximately zero. These are **individual-model observations** only.

Do **not** compare the absolute total energies of V_O and V_N to infer which vacancy is thermodynamically more favorable; the cell compositions differ. No defect formation energies, charge-transition levels, density-of-states conclusions or photocatalytic activity improvements are claimed. A matched 24-atom pristine electronic reference, O/N chemical potentials, larger supercells, inequivalent vacancy positions, and cutoff/k-point/spin sensitivity tests remain outstanding.

## Literature anchors

- [DOI:10.1039/D5DT01193K](https://doi.org/10.1039/D5DT01193K)
- [DOI:10.1002/smll.202510276](https://doi.org/10.1002/smll.202510276)
- [DOI:10.1155/2013/507194](https://doi.org/10.1155/2013/507194)

*Status: transparent exploratory research workflow, not a peer-reviewed publication.*
