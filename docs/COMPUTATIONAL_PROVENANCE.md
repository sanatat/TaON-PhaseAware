# Computational evidence and reproducibility status

## Data-source distinction

The project archive `TaON-PhaseAware-v4(1).zip` uploaded on 2026-10-28 contains the literature-analysis source code and planning documentation, **not** the completed Quantum ESPRESSO 7.5 calculations. Original QE output text files and relaxed CIFs have now been supplied and published in this repository. The values in `results/summary.csv` were checked against the final `qe/VO/relax_restart_04.out` and `qe/VN/relax_restart_06.out`. The separate `results/terminal_reported_pilot.csv` remains a historical transcription.

## Reported electronic and ionic settings

- Structure: a 12-atom monoclinic candidate `mp-4165`, pristine cell initially relaxed at fixed lattice vectors.
- 2×1×1 supercell (24 atoms before vacancy, 23 after deletion).
- Defects: one oxygen vacancy and one nitrogen vacancy at separate selected anion sites (not all symmetry-inequivalent configurations).
- Software: Quantum ESPRESSO 7.5, a serial pw.x executable locally compiled on a low-memory Linux laptop.
- Pseudopotentials: Ta, O and N PBE-compatible SSSP 1.3.0 Efficiency selections, with exact file names/hashes still to be archived.
- Reported defect inputs: 78 Ry plane-wave cutoff, 624 Ry charge-density cutoff, true Γ-only k sampling, `nspin=2`, Gaussian smearing of 0.005 Ry, and fixed-cell BFGS relaxations.
- Time-limited BFGS runs were continued through QE checkpoints, VO through restart_04 and VN through restart_06. Both were reported `bfgs converged`.
- Final max Cartesian force components below the stated `forc_conv_thr=0.001 Ry/Bohr`, per terminal reports.

## Publication status and remaining scientific validation

1. **Complete:** the three final CIFs are now published under `structures/`.
2. **Complete:** spin-polarized SCF and sequential ionic relaxation inputs/outputs are published under `qe/VO/` and `qe/VN/`.
3. Do not publish API keys, personal access tokens or proprietary pseudopotential binaries. The QE logs may contain local file paths.
4. **Partially complete:** final energies, force norms, magnetization and BFGS convergence were checked against uploaded logs; minimum-image displacements were tabulated from the user's local ASE analysis. Independent reproduction remains to be done.
5. **Complete in part:** pseudopotential metadata, file names and MD5 hashes were recorded under `metadata/sssp_cutoffs.json`; binaries are intentionally excluded.
6. Compute matched pristine electronic reference and test vacancy formation-energy sensitivity to cell size, k sampling, occupation, ionic force threshold, charge/spin configurations and chemical potentials.

## Scientific interpretation

The mean atomic displacements reported for VO and VN are 0.073734 Å and 0.097689 Å, respectively. Both are fixed-cell results for a **single vacancy placement**. The apparent VN magnetic moment (~0.99 μB) should not be described as proof of a stable magnetic ground state.

The two total energies are from **different compositions** and cannot rank vacancy formation or stability. Photocatalytic activity and carrier recombination have not been calculated.

## Literature-analysis files

The source archive contains literature curation and plotting logic, tests, and preliminary DFT input-generation helpers. The archive's original README and runbooks explicitly say DFT was not executed *in that original archive*. The 2026-10-28 README in this repository distinguishes that archival status from later user-reported calculations on a separate workstation.
