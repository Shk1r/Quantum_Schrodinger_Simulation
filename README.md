# Time-Dependent Schrodinger Equation (1D)

This project studies the **time-dependent Schrödinger equation** for a particle in a 1D infinite box with a localized attractive potential. The goal is to compare four standard numerical approaches and show that they give the same physical evolution under the same dimensionless scaling and boundary conditions $\psi(0)=\psi(L)=0$.

The work is implemented in a single Jupyter notebook:
- `Time-Dependent Schrodinger Equation.ipynb`

An example animation is saved as:
- `TD.gif`

## Methods Used
1. **Explicit Finite Difference (time-stepping)**
   - Discretizes space and time and updates $\psi$ directly.
   - Renormalizes at each step to keep total probability equal to $1$.
   - Accelerated with `numba` JIT.

2. **Eigenstate Expansion**
   - Solves the time-independent problem to get eigenstates and energies.
   - Expands the initial state in eigenstates and adds the time phase.

3. **Crank–Nicolson (implicit)**
   - Solves $(I + i\Delta t/2 \; H)\psi^{n+1} = (I - i\Delta t/2 \; H)\psi^n$ each step.
   - Uses a tridiagonal (Thomas) solver implemented with `numba`.

4. **Split-Operator (Strang splitting)**
   - Alternates half-steps of the potential with a kinetic step in the sine basis.
   - Enforces $\psi(0)=\psi(L)=0$ via the sine transform.

All methods are run on the same spatial grid and compared visually. For runtime, Crank–Nicolson and Split‑Operator use fewer time steps but the same total simulated time; you can increase `Nt_cn` and `Nt_so` in the notebook if you want finer time resolution.

## Potential
The potential is an attractive Gaussian well centered in the box:

$$
V(x) = -10^4 \exp\left(-\frac{(x-1/2)^2}{2(1/20)^2}\right)
$$

We work in dimensionless units with $L=1$ throughout the notebook.

## How to Run
Open the notebook and run all cells.

```bash
jupyter notebook
```

The notebook will generate plots and an animation (`TD.gif`) comparing all four methods.
Re-running the notebook will overwrite `TD.gif`.

## Requirements
Tested with common scientific Python packages:
- `numpy`
- `matplotlib`
- `scipy`
- `numba`
- `scienceplots`
- `pillow` (for GIF output)

You can install them with:

```bash
pip install numpy matplotlib scipy numba scienceplots pillow
```

## Results
The probability density $|\psi(x,t)|^2$ from all four methods matches over time, confirming the consistency of the numerical approaches.

## Notes
This project focuses on clarity and comparison of numerical methods rather than optimization or performance tuning.
