# Numerical Methods: Implementation and Convergence Analysis

A collection of Jupyter notebooks implementing fundamental numerical algorithms from scratch in Python, with rigorous mathematical derivations, convergence studies, and error analysis. This project demonstrates core computational mathematics concepts relevant to graduate-level numerical analysis coursework.

## Project Overview

This repository contains three self-contained notebooks, each addressing a classical problem in numerical computation:

### Notebook 1 — Root-Finding Methods
**File:** `notebooks/01_root_finding_methods.ipynb`

Implements and compares three iterative algorithms for solving nonlinear equations f(x) = 0:
- **Bisection Method** — guaranteed convergence via the intermediate value theorem; linear (first-order) convergence.
- **Newton–Raphson Method** — derived from Taylor expansion; quadratic convergence near simple roots. Includes a failure-mode analysis (cycling near inflection points).
- **Secant Method** — derivative-free variant with superlinear convergence of order φ ≈ 1.618.

Each method is tested on polynomial, trigonometric, and exponential test functions. The notebook includes empirical convergence-rate estimation, error-vs-iteration plots (log scale), and an efficiency comparison normalised by function-evaluation cost.

### Notebook 2 — Numerical Integration (Quadrature)
**File:** `notebooks/02_numerical_integration.ipynb`

Implements composite quadrature rules for approximating definite integrals:
- **Composite Trapezoidal Rule** — piecewise linear interpolation; O(h²) error.
- **Composite Simpson's Rule** — piecewise quadratic interpolation; O(h⁴) error.
- **Romberg Integration** — Richardson extrapolation applied to the trapezoidal rule, systematically eliminating error terms.

Tested on four integrals with known closed-form values (sin, exp, rational, and a singular integrand √x). Includes log-log convergence plots, observed-rate tables, geometric visualisation of the quadrature panels, and a discussion of how integrand regularity affects the convergence order.

### Notebook 3 — ODE Solvers
**File:** `notebooks/03_ode_solvers.ipynb`

Implements single-step methods for initial value problems dy/dt = f(t, y):
- **Euler's Method** — first-order explicit scheme.
- **Improved Euler (Heun's Method)** — second-order predictor–corrector.
- **Classical Runge–Kutta (RK4)** — fourth-order, four-stage scheme with Butcher tableau.

Includes a complete stability analysis: amplification factors, stability-region plots in the complex plane, and a demonstration of instability on a mildly stiff problem. Convergence verified on three test problems with known analytical solutions. Efficiency comparison normalised by function-evaluation count.

## Repository Structure

```
numerical-methods-analysis/
├── README.md
├── requirements.txt
├── .gitignore
├── notebooks/
│   ├── 01_root_finding_methods.ipynb
│   ├── 02_numerical_integration.ipynb
│   └── 03_ode_solvers.ipynb
├── figures/           # Generated plots (created when notebooks are run)
└── utils/
    └── __init__.py
```

## Getting Started

### Prerequisites

- Python 3.9 or later
- pip

### Installation

```bash
git clone https://github.com/<your-username>/numerical-methods-analysis.git
cd numerical-methods-analysis
pip install -r requirements.txt
```

### Running the Notebooks

```bash
jupyter notebook notebooks/
```

Open any notebook and run all cells sequentially. Figures are saved automatically to the `figures/` directory.

## Mathematical Concepts Covered

- Iterative convergence theory (linear, quadratic, superlinear)
- Order of convergence: definition, empirical estimation, and verification
- Taylor series derivations of numerical schemes
- Newton–Cotes quadrature and the Euler–Maclaurin expansion
- Richardson extrapolation (Romberg integration)
- Local and global truncation error analysis
- Stability theory for explicit ODE solvers (Dahlquist test equation, amplification factors, stability regions)
- Butcher tableaux for Runge–Kutta methods

## Tools and Libraries

All core algorithms are implemented from scratch using only:
- **NumPy** — array operations and basic linear algebra
- **Matplotlib** — plotting and visualisation
- **SciPy** — used solely for computing high-precision reference solutions (via `brentq`)

No black-box solvers are used for the numerical methods themselves.

## Author

**Taimoor Ali**  
B.Sc. Mathematics, University of Jhang, Pakistan (2020–2024)

## License

This project is released for academic and educational purposes.
