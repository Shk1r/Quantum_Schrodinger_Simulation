# Time-Dependent Schrodinger Equation (1D)

This project studies the **time-dependent Schrödinger equation** for a particle in a 1D infinite box with a localized attractive potential. The goal is to compare two standard numerical approaches and show that they give the same physical evolution.

The work is implemented in a single Jupyter notebook:
- `Time-Dependent Schrodinger Equation.ipynb`

An example animation is saved as:
- `TD.gif`

## Methods Used
1. **Finite Difference (time-stepping)**
   - Discretizes space and time and updates $\psi$ directly.
   - Renormalizes at each step to keep total probability equal to $1$.

2. **Eigenstate Expansion**
   - Solves the time-independent problem to get eigenstates and energies.
   - Expands the initial state in eigenstates and adds the time phase.

Both methods are run on the same grid and compared visually.

## Potential
The potential is an attractive Gaussian well centered in the box:

$$
V(x) = -10^4 \exp\left(-\frac{(x-1/2)^2}{2(1/20)^2}\right)
$$

## How to Run
Open the notebook and run all cells.

```bash
jupyter notebook
```

The notebook will generate plots and an animation (`TD.gif`).

## Requirements
Tested with common scientific Python packages:
- `numpy`
- `matplotlib`
- `scipy`
- `numba`
- `scienceplots`

You can install them with:

```bash
pip install numpy matplotlib scipy numba scienceplots
```

## Results
The probability density $|\psi(x,t)|^2$ from both methods matches over time, confirming the consistency of the two numerical approaches.

## Notes
This project focuses on clarity and comparison of numerical methods rather than optimization or performance tuning.

