# Critical bubble (bounce) by the shooting method

<!-- One-sentence summary. Fill in once the notebook works. -->
A Python notebook that computes the critical bubble of a first-order phase transition, extracts the nucleation action S₃/T, and derives the transition parameters that feed gravitational-wave predictions.

<!-- Add after you push: -->
<!-- [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](LINK_TO_NOTEBOOK_ON_COLAB) -->

## Motivation

<!-- 3 to 4 sentences. Why bubble nucleation matters: -->
<!-- - first-order phase transitions proceed by nucleating bubbles of the new phase -->
<!-- - the nucleation rate depends on the action of the critical bubble -->
<!-- - the resulting transition parameters (T_n, alpha, beta/H) determine the gravitational-wave signal -->
<!-- - this is a learning project reproducing a standard calculation, based on arXiv:2008.09136 and arXiv:2410.21509 -->

## What is in this repo

<!-- Short list of what the notebook does, in order. Tick off as you finish. -->
- [ ] Derivation of the O(3)-symmetric bounce equation from the Euclidean action
- [ ] Toy potential V(φ, T) and its minima / T_c
- [ ] ODE integrator for the bounce equation
- [ ] Shooting (bisection) on φ(0) with overshoot / undershoot detection
- [ ] Bubble profile φ(r) and action S₃
- [ ] Validation: thin-wall limit, convergence, cross-check
- [ ] S₃/T versus T, nucleation temperature T_n
- [ ] β/H at T_n (and α if included)

## Method

### The equation

<!-- State the equation and boundary conditions: -->
<!-- φ'' + (2/r) φ' = dV/dφ, with φ'(0) = 0 and φ(∞) = φ_false -->
<!-- One sentence on why it is 2/r (3D, finite-temperature, O(3) symmetry). -->

### Shooting method

<!-- The damped-particle picture in the inverted potential -V. -->
<!-- Overshoot vs undershoot, and how bisection finds φ(0). -->
<!-- How you start at small r₀ to avoid the 1/r singularity. -->

### Potential used

<!-- Write the potential and the parameter values you chose. -->
<!-- Include a plot of V(φ) at a few temperatures. -->

## Results

<!-- Figures go in figures/. Embed with a one-line caption saying which cell produced each. -->

### Bubble profile

<!-- ![Critical bubble profile](figures/bubble_profile.png) -->
<!-- Caption: φ(r) at T = ..., with S₃ = ... -->

### Action and nucleation temperature

<!-- ![S3/T vs T](figures/action_vs_T.png) -->
<!-- Caption: S₃/T against T; T_n is where S₃/T ≈ [value you used]. -->

### Transition parameters

<!-- Small table: T_n, β/H, (α). State the potential and parameters they correspond to. -->

## Validation

<!-- Be specific and quantitative. -->
- **Thin-wall limit:** [how close your S₃ gets to 16πσ³/(3ε²) as T → T_c, and over what range]
- **Convergence:** [what you varied (tolerances, r₀) and how much S₃ changed]
- **Cross-check:** [comparison with CosmoTransitions, if done, with the numbers]

## Limitations

<!-- Be honest. Examples to keep or edit: -->
- Toy polynomial potential, not a full thermal effective potential
- No gauge dependence or higher-order thermal corrections
- Single scalar field only
- [Anything that didn't work or wasn't finished]

## How to run

```bash
git clone https://github.com/GriimHog/<repo-name>.git
cd <repo-name>
pip install -r requirements.txt
jupyter notebook notebook.ipynb
```

<!-- Or use the Colab badge above. State the Python version you tested with. -->

## Repository layout

```
.
├── notebook.ipynb
├── requirements.txt
├── figures/
├── docs/           # optional: scan of handwritten derivation
├── LICENSE
└── README.md
```

## References

1. M. Hindmarsh, M. Lüben, J. Lumma, M. Pauly, *Phase transitions in the early universe*, arXiv:2008.09136.
2. D. Croon, D. J. Weir, *Gravitational waves from cosmological phase transitions* (review), arXiv:2410.21509. <!-- check the exact title and author list on arXiv before publishing -->
<!-- Add the baryogenesis review and any other source you actually use. -->

## Author

Priyanshu Sharma, IISER Bhopal. priyanshus21@iiserb.ac.in
