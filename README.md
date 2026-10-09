# Critical bubble (bounce) by the shooting method

A Python notebook that computes the critical bubble of a first-order phase transition, extracts the nucleation action S₃/T, and derives the transition parameters that feed gravitational-wave predictions.

## Checklist

- [x] Derivation of the O(3)-symmetric bounce equation from the Euclidean action
- [x] Toy potential V(φ, T) and its minima / T_c
- [x] ODE integrator for the bounce equation
- [x] Shooting (bisection) on φ(0) with overshoot / undershoot detection
- [ ] Bubble profile φ(r) and action S₃
- [ ] Validation: thin-wall limit, convergence, cross-check
- [ ] S₃/T versus T, nucleation temperature T_n
- [ ] β/H at T_n (and α if included)

## Method

### The equation

#### Setup

At finite temperature the nucleation rate is controlled by a static, O(3)-symmetric critical bubble. Its action is

$$
S_3 = 4\pi \int_0^\infty r^2, dr \left[\frac{1}{2}\left(\frac{d\phi}{dr}\right)^2 + V(\phi, T) \right],
$$

and the critical bubble is the profile $\phi(r)$ that makes $S_3$ stationary. <!-- The nucleation rate then goes roughly as $\Gamma \propto e^{-S_3/T}$. -->

#### Equation of motion

Varying the action gives

$$
\boxed{\;\phi'' + \frac{2}{r}\phi' = \frac{dV}{d\phi}\;}
$$

The factor $2/r$ comes from the three-dimensional Laplacian acting on an O(3)-symmetric profile. In a four-dimensional Euclidean (zero-temperature) treatment it would be $3/r$.

#### Boundary conditions

$$
\phi'(0) = 0, \qquad \phi(r \to \infty) = \phi_\text{f}.
$$

- $\phi'(0)=0$ keeps the solution regular at the centre of the bubble. It also makes the boundary term $r^2\phi' \delta\phi$ vanish at $r=0$.
- $\phi \to \phi_\text{f}$ means that far from the bubble the field sits in the metastable (false) vacuum. This also makes the boundary term vanish at infinity.

### The Shooting Method

#### The damped-particle picture

Imagine $r$ as time. Then the equation describes a particle moving in the **inverted potential** $-V(\phi)$, with a friction term $\frac{2}{r}\phi'$ that is strong at small $r$ and weak at large $r$.

- The particle is released at rest at $\phi(0)=\phi_0$, between the true minimum and the barrier.
- It must come to rest exactly on the hilltop of $-V$ at $\phi_\text{f}$ as $r\to\infty$.
- If $\phi_0$ is too close to the true minimum, the particle loses too little energy to friction and **overshoots** $\phi_\text{f}$.
- If $\phi_0$ is too far from it, the particle loses too much energy and **undershoots**, turning back before it reaches $\phi_\text{f}$.
- The critical bubble corresponds to the $\phi_0$ between the two cases. This is the idea behind the shooting method.

#### Starting the integration

The friction term is singular at $r=0$, so the integration starts at a small $r_0$. Near the centre, $\phi \approx \phi_0 + a r^2$. Substituting into the equation gives $6a = V'(\phi_0)$, so

$$
\phi(r_0) \approx \phi_0 + \frac{V'(\phi_0)}{6} r_0^2, \qquad
\phi'(r_0) \approx \frac{V'(\phi_0)}{3} r_0 .
$$

These values are the initial conditions passed to the ODE solver.

### The Potential

We start by using the standard toy model for the potential :

$$
V(\phi,T)=D(T^2-T^2_0)\phi^2-ET\phi^3+(\frac{\lambda}{4})\phi^4
$$

- This potential has three extrema for positive constants $D,E and \lambda$ at $\phi=0$ and $\phi_-$ (the barrier top) and $\phi_+=\phi_\text{f}$ (the broken minimum) .
- **Critical temperature T_c** where $V(\phi_+)=V(0)$. This implies at this temperature $V$ has a double route at $0$ and $\phi_+$ thus suggesting the form for $V$ that is :
$$V(\phi)=(\frac{\lambda}{4})\phi^2(\phi-\phi_\text{f})^2$$.
- Expanding and matching the terms in the original form we get :
$$T_c^2=T_0^2(1-\frac{E^2}{\lambda D})^{-1}\quad,\quad\phi_c=\frac{2ET}{\lambda}$$

![V($\phi$) at various Temp (79)](figures/V_at_various_Temp.png)

## Results

## Limitations

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
## Repository layout

```
.
├── notebook.ipynb
├── requirements.txt
├── figures/
├── LICENSE
└── README.md
```

## References

1. M. Hindmarsh, M. Lüben, J. Lumma, M. Pauly, *Phase transitions in the early universe*, arXiv:2008.09136.
2. D. Croon, D. J. Weir, *Gravitational waves from cosmological phase transitions* (review), arXiv:2410.21509.

## Author

Priyanshu Sharma, priyanshuaryan2002@gmail.com, priyanshus21@iiserb.ac.in
