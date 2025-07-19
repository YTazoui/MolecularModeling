# MolecularModeling
Contains files related to my molecular simulations projects

## Overview

This series of projects builds a molecular simulation pipeline for an Argon fluid using the Lennard-Jones potential and periodic boundary conditions. Simulations span the NVT, NPT, and NVE ensembles and include both Monte Carlo and Molecular Dynamics implementations. All code is written in Python within Jupyter Notebooks and executed using the `moleng` virtual environment.

## Contents

- `Meng355Project2.ipynb`: Foundational functions (Project 2)
- `Meng355Project3A.ipynb`: NVT Monte Carlo simulation (Project 3A)
- `Project3B_Tazoui.ipynb`: Equation of state & NPT MC simulation (Project 3B)
- `Project4A.ipynb`: NVE Molecular Dynamics simulator (Project 4A)
- `Project4b.ipynb`: NVT/NPT Molecular Dynamics with thermostat/barostat and diffusivity analysis (Project 4B)
- `Project2.pdf`, `Project3A.pdf`, `Project3B.pdf`, `Project4A.pdf`, `Project4B.pdf`: Assignment specifications
- `.xyz` files: Simulation trajectories for visualization in VMD or OVITO

---

## Project 2 – Foundations of Molecular Simulation

Implements building blocks for a Lennard-Jones molecular simulation:

- Periodic boundary wrapping
- Minimum image distance calculation
- Lennard-Jones energy and force functions
- Initialization of random/crystalline structures
- Per-particle and system-wide energy computations
- 3D plotting and `.xyz` coordinate output

---

## Project 3A – Monte Carlo I (NVT Ensemble)

Constructs a Monte Carlo simulator using the Metropolis algorithm:

- Atom displacement trial moves
- Efficient energy difference evaluation
- Metropolis accept/reject criterion with logging
- Trajectory output and configuration visualization
- Production runs at 298 K and 50 K with analysis of energy trends

---

## Project 3B – Monte Carlo II (Equation of State & NPT Ensemble)

Extends MC simulations to compute fluid properties and implement pressure control:

- **Equation of State**:
  - Pressure calculation via the virial formula
  - Comparison to ideal gas and van der Waals equations
- **NPT Monte Carlo**:
  - Volume trial moves with target pressure
  - Energy, pressure, and box size tracking
- **Radial Distribution Function (g(r))**:
  - Histogram-based structure analysis at two thermodynamic conditions
  - Discussion of phase behavior and particle correlations

---

## Project 4A – Molecular Dynamics I (NVE Ensemble)

Implements a Molecular Dynamics simulator using the Velocity Verlet algorithm:

- Truncated and shifted Lennard-Jones potential
- Tail corrections for energy and pressure
- Random velocity initialization via Maxwell-Boltzmann distribution
- Instantaneous computation of energy, pressure, and temperature
- Main MD loop with output logging and trajectory writing
- Verification of energy conservation and system behavior at T = 298 K

---

## Project 4B – Molecular Dynamics II (NVT & NPT Ensembles)

Enhances the MD simulator with thermostat/barostat and computes transport properties:

- **Berendsen Thermostat & Barostat**:
  - Temperature and pressure coupling with tunable time constants
  - Flexible ensemble switching (NVE, NVT, NPT)
- **NPT Simulation**:
  - System equilibration at 298 K, 200 bar
  - Output of KE, PE, E, T, P, and box length over time
- **NVT Simulation**:
  - Continuation of NPT run at fixed volume
  - Trajectory output for diffusivity analysis
- **Mean Squared Displacement (MSD)**:
  - Unwrapping of periodic boundaries
  - Time-averaged displacement computation
  - Estimation of self-diffusivity from linear MSD scaling

---

## Requirements

- Python 3.x
- Jupyter Notebook
- `numpy`, `scipy`, `matplotlib`, `mpl_toolkits`
- `MDAnalysis` (for MSD analysis)
- moleng virtual environment (provided by course setup)

## License

These projects were completed for educational purposes under MENG 25500 / 35500 at the University of Chicago.
