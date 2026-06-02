# RoughMob Two-Bead Hydrocarbons

This repository contains the simulation data supporting the manuscript:

> **Extending the RoughMob Framework to Two-Bead Coarse-Grained Models of Branched Hydrocarbon Liquids**
> *Submitted to the Journal of Physical Chemistry B (under review)*

---

## Overview

This dataset accompanies a study that extends the volume-based RoughMob framework to two-bead coarse-grained models of branched hydrocarbon liquids. The work develops a predictor for the mobility acceleration factor --- the ratio of the coarse-grained to the atomistic self-diffusion coefficient --- based on geometric descriptors of the molecular volume partitioned into active and passive regions. Thirteen branched hydrocarbons spanning six to twelve carbon atoms are studied at 298.15 K and 1 atm.

---

## Molecular Systems

The thirteen hydrocarbon liquids included in this dataset are:

| Abbreviation | Full Name                        | Formula        |
|--------------|----------------------------------|----------------|
| 23DMBt       | 2,3-dimethylbutane               | C₆H₁₄         |
| 3MP          | 3-methylpentane                  | C₆H₁₄         |
| 25DMHx       | 2,5-dimethylhexane               | C₈H₁₈         |
| 234TMP       | 2,3,4-trimethylpentane           | C₈H₁₈         |
| 3EtHx        | 3-ethylhexane                    | C₈H₁₈         |
| 2345TMHx     | 2,3,4,5-tetramethylhexane        | C₁₀H₂₂        |
| 27DMO        | 2,7-dimethyloctane               | C₁₀H₂₂        |
| 45DMO        | 4,5-dimethyloctane               | C₁₀H₂₂        |
| 2367TMO      | 2,3,6,7-tetramethyloctane        | C₁₂H₂₆        |
| 2457TMO      | 2,4,5,7-tetramethyloctane        | C₁₂H₂₆        |
| 3456TMO      | 3,4,5,6-tetramethyloctane        | C₁₂H₂₆        |
| 36DEO        | 3,6-diethyloctane                | C₁₂H₂₆        |
| 45DEO        | 4,5-diethyloctane                | C₁₂H₂₆        |

Three molecules --- 3MP, 3EtHx, and 234TMP --- are asymmetric and use an A--B two-bead mapping. The remaining ten molecules are symmetric and use an A--A mapping.

---

## Repository Structure

Each molecule has its own folder containing three subfolders:

```
<molecule>/
├── distributions/        # Target RDF and bonded distributions from atomistic simulations
├── potentials/           # Coarse-grained non-bonded and bonded pair potentials (IBI)
└── msd/                  # Mean-square displacement data from atomistic and CG simulations
```

### File descriptions

**distributions/**
| File | Description |
|------|-------------|
| `nb.A-A.dist.tgt` | Non-bonded centre-of-mass RDF target (A--A pairs) |
| `nb.A-A.dist.new` | Non-bonded RDF from the final IBI iteration (A--A pairs) |
| `nb.A-B.dist.tgt` | Non-bonded RDF target (A--B pairs, asymmetric molecules only) |
| `nb.B-B.dist.tgt` | Non-bonded RDF target (B--B pairs, asymmetric molecules only) |
| `bond.A-A.dist.tgt` | Intramolecular bond-length distribution target (A--A) |
| `bond.A-B.dist.tgt` | Intramolecular bond-length distribution target (A--B, asymmetric molecules only) |

**potentials/**
| File | Description |
|------|-------------|
| `nb.A-A.pot.table` | IBI-derived non-bonded pair potential (A--A) |
| `nb.A-B.pot.table` | IBI-derived non-bonded pair potential (A--B, asymmetric molecules only) |
| `nb.B-B.pot.table` | IBI-derived non-bonded pair potential (B--B, asymmetric molecules only) |

**msd/**
| File | Description |
|------|-------------|
| `msd-AA.dat` | Centre-of-mass mean-square displacement from the atomistic simulation |
| `msd-CG.dat` | Centre-of-mass mean-square displacement from the coarse-grained simulation |

---

## Simulation Details

**Atomistic simulations**
- Software: LAMMPS
- Force field: OPLS
- Temperature: 298.15 K
- Pressure: 1 atm
- Ensemble: NPT (Nosé--Hoover thermostat and barostat)
- Production run: 10 ns

**Coarse-grained force-field derivation**
- Software: VOTCA
- Method: Iterative Boltzmann Inversion (IBI) with pressure correction
- Two beads per molecule; bead centre defined as the centre of mass of constituent atoms
- Non-bonded potentials converged when the integrated relative deviation between CG and AA RDF fell below 1%
- Bonded potentials derived by direct Boltzmann inversion of the atomistic bond-length distribution

**Coarse-grained simulations**
- Software: LAMMPS
- Temperature: 298.15 K
- Pressure: 1 atm
- Ensemble: NPT (Nosé--Hoover thermostat and barostat)
- Production run: 10 ns

---

## Citation

If you use this data in your work, please cite the associated manuscript once it is published. A full citation will be added here upon acceptance.

---

## License

This dataset is made available for academic and research use. Please cite the associated publication if you use any part of this data.
