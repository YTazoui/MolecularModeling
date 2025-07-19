# Colloidal Interaction & DLVO Umbrella Sampling

## Overview

This repository contains two Jupyter notebooks that explore colloidal interactions via DLVO theory and then apply umbrella‑sampling Monte Carlo to extract a potential of mean force:

1. **DLVO‑Analysis.ipynb** – Analytical & numerical exploration of the DLVO potential and computation of second virial coefficients (B₂) under various conditions.  
2. **TermProject.ipynb** – Umbrella‑sampling Monte Carlo simulation to reconstruct the free‐energy profile (PMF) of two colloidal particles interacting via the DLVO potential.

---

## DLVO‑Analysis.ipynb

**Purpose:**  
Quantify how van der Waals attraction and electrostatic repulsion combine to yield the classic DLVO interaction, and compute the second virial coefficient (B₂) for different particle–solvent systems.

**Key Steps & Features:**
- **Imports & Parameters:**  
  – NumPy, SciPy’s `integrate`, Matplotlib.  
  – Physical constants (Boltzmann’s constant, temperature, Hamaker constant, particle radius, dielectric properties, ionic strengths).
- **Total Potential Function (`calc_totPotential`)**  
  Computes  
  \[ V(r) = V_\mathrm{vdW}(r) + V_\mathrm{el}(r) \]  
  for spherical colloids at center‑to‑center separation *r*.
- **Plotting DLVO Curves:**  
  – Vary ionic strength, particle size, Hamaker constant, or solvent dielectric.  
  – Overlay multiple curves for direct comparison.
- **Second Virial Coefficient (B₂):**  
  – Defines the integrand  
  \[ -2\pi \bigl(e^{-V(r)/(k_BT)} - 1\bigr)\,r^2 \]  
  – Numerically integrates from a small cutoff to ∞ to estimate B₂ under each condition.  
  – Prints and plots B₂ vs. ionic strength (or other parameters).

**Usage:**  
1. Open in Jupyter and run all cells.  
2. Inspect and modify parameter lists (`I_values`, `A_values`, `R_values`, etc.) to explore new regimes.  
3. Examine plotted DLVO curves and B₂ outputs.

---

## TermProject.ipynb

**Purpose:**  
Use umbrella‑sampling Monte Carlo to reconstruct the potential of mean force (PMF) between two DLVO‑interacting colloids across a range of separations.

**Key Steps & Features:**
- **Core Utilities (ported from earlier projects):**  
  – `wrap(r, L)`, `dist(r1, r2, L)`, `E_i(...)`, `E_system(...)`, and `.xyz` writer.  
- **DLVO Potential (`DLVO(D)`):**  
  Returns the sum of van der Waals and screened‐electrostatic terms for center‑to‑center distance D.
- **Window Definition (`define_windows`)**  
  Splits the separation range (e.g. 10 nm → 50 nm) into overlapping “windows” for biased sampling.
- **Monte Carlo Move Proposal (`proposed_move`)**  
  Generates trial separations within each window and accepts/rejects via Metropolis criterion.
- **Umbrella Sampling Loop:**  
  – Runs a short MC simulation in each window to build a histogram of sampled distances.  
  – Applies the WHAM (weighted histogram) approach—or histogram‐overlap stitching—to reconstruct the unbiased PMF.
- **Visualization:**  
  – Plots individual window histograms and the stitched PMF vs. separation.  
  – Exports final PMF data for further analysis.

**Usage:**  
1. Open in Jupyter (ensure previous “Project 2” utilities are available or imported).  
2. Adjust parameters: total distance range, window width/overlap, MC sweeps per window, temperature, box size *L*.  
3. Run all cells to generate and visualize the PMF curve.

---

## Requirements

- **Python 3.x**  
- **Jupyter Notebook**  
- **Libraries:** `numpy`, `scipy`, `matplotlib`, `pandas` (TermProject), `random`

---

## How to Navigate

