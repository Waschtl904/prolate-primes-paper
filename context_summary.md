# Series Context Summary - Papers I-VIII

> **Purpose:** Paste this at the top of any new GPT/AI chat before showing Paper VII or later.
> Provides the full logical chain without needing Papers I-VI.

---

## Overarching Goal

The series constructs a spectral operator whose eigenvalue distribution
mirrors the non-trivial zeros of the Riemann zeta function
(Hilbert-Polya conjecture). The core object is the PSWF operator
and its Gram matrix sampled at prime arguments.
Series arc: coercivity -> scaling limits -> spectral phase ->
bandwidth decay -> rigorous peak-width bounds -> crossover asymptotics
-> lower bounds.

---

## Central Notation

- `psi_n^(c)`: PSWF on `(-1,1)`, bandwidth `c`, eigenvalue `chi_n^(c) ~ cn`
- `Phi_n^(c)(u) = psi_n^(c)(e^u) e^{u/2}`, `u in (-inf,0)` -- satisfies Schrodinger eq.
- `V_c(u) = 1/4 + e^{2u}(chi_n^(c)+3/4) - c^2 e^{4u}` -- Schrodinger potential
- `g_hat_n^(c)(t) = int_{-inf}^0 Phi_n^(c)(u) e^{itu} du` -- Mellin/Fourier transform
- `t_*(c,n) ~ c^{1/2}` -- Fourier peak location
- `Delta_eps(c,n)` -- peak width (smallest Delta s.t. L2-mass outside [t_*-Delta, t_*+Delta] <= eps)
- `Omega_eps^abs ~ c^{1/2}` -- absolute tail bandwidth (locates peak, not a decay rate)
- `F_c(t) = sum_n lambda_n^(c) g_hat_n^(c)(t)` -- multi-mode observable
- `delta = c^{-1/3}` -- natural Airy scale near turning point `u_*`
- `Z_cross = {t : c^{-2/3} <= |t-t_*| <= c^{-1/3}}` -- crossover zone

---

## Paper I -- Coercivity of the Prolate Gram Form

Gram matrix `G_{mn}^(c) = <psi_m^(c), psi_n^(c)>` sampled at primes
is uniformly coercive for large `c`.
Tools: PNT, prime spacing, WKB amplitudes.
Output: coercivity constant scales as `c^{-1/2}`.

## Paper II -- Scaling Limits and Trace Formula

Rescaled Gram form converges to a limit operator as `c -> inf`.
Trace formula links eigenvalue distribution to a sum over primes.
Tools: uniform WKB, Weyl law, Montgomery-Odlyzko heuristics.

## Paper III -- Spectral Phase Analysis

Numerical + analytic study of the Fourier phase of `g_hat_n^(c)(t)`.
Phase transition near `t = t_* ~ c^{1/2}`.
Output: evidence for `c^{-1/2}` peak-width scaling;
identification of three-zone frequency structure.

## Paper IV -- No-Go Theorem for Spectral Phase

No bandlimited operator family with zeta-compatible spectral limits
can have non-degenerate Mellin phase.
Tools: Paley-Wiener, spectral localization.
Output: rules out naive constructions; motivates PSWF approach.

## Paper V -- Mellin Bandwidth Decay: ODE + Numerics

Numerical evidence: effective Mellin bandwidth scales as `c^{-1/2}`.
Barrier estimate (Thm 3.1): `|g_hat_n^(c)(t)| lesssim e^{-gamma c^{1/2}}`
for `t >> t_*`.
Output used in Paper VI: barrier estimate + `c^{-1/2}` conjecture.

---

## Paper VI -- Rigorous Peak-Width Bounds (COMPLETE, referee-ready)

### Theorem 3.2 (Pointwise decay)
`|Phi_hat_n^(c)(t)| <= C_kappa c^{-1/4} t^{-1/4}` for `1 <= t <= c^{1/2-kappa}`

Proof structure (3 steps):
1. Fix `delta = c^{-1/3}` (natural Airy scale). Split `I_+ = I_+^loc + I_+^tail`.
2. Tail (|u-u*|>delta): IBP, no stationary point, gives `c^{-1/4} t^{-1}` uniformly in t.
3. Local (|u-u*|<=delta): Airy matching via Langer-Olver (Lemma 2.3).
   Phase degeneracy prevents standard stationary phase.
   Airy kernel gives decay of order `t^{-1/4}` via cubic-type stationary phase
   (Olver 1974, Ch. 11). Full argument in Paper VII, Theorem A.

### Theorem 4.1 (L2-tail bound)
`||Phi_hat_n^(c)||_{L2(|t|>R)}^2 <= C_kappa^2 c^{-1/2} R^{-1/2}`
(log-free for `1 <= R <= c^{1/4}`)

### Theorem 5.2 (Peak-width bound)
`Delta_eps(c,n) <= C(kappa,eps) c^{-2/3}`
From Airy profile: `Phi_hat_n^(c)(t_* + c^{-2/3} x) approx c^{-1/2} kappa_n^(c) Ai(x)`

### Theorem 6.1 (Non-vanishing of F_c)
`F_c` does not vanish identically on any compact `K subset R`.
Proof:
- `Phi_n^(c) in L^1(e^{a|u|}du)` for some `a>0` (exponential decay from potential barrier)
- => `g_hat_n^(c)` is real-analytic on R
- Sturm-Liouville eigenbasis => {Phi_n^(c)} linearly independent in L2(-inf,0)
- => {g_hat_n^(c)} linearly independent on R
- Vanishing on compact K with accumulation point => F_c=0 on R (real-analyticity)
- Inverse Fourier: sum lambda_n Phi_n = 0 => contradiction (lin. indep. + lambda>0)

### Open Problem (input for Paper VII)
Control Z_cross to improve `c^{-2/3}` -> `c^{-1/2}` peak-width bound.

---

## Paper VII -- Composite Asymptotics in Z_cross (IN PROGRESS)

Goal: Prove `Delta_eps(c,n) <= C(kappa,eps) c^{-1/2}` (sharp upper bound).

Strategy:
- Build uniform composite Airy-WKB expansion throughout Z_cross
- Show: `Phi_hat_n^(c)(t) = c^{-1/2} A_n^(c)(c^{1/2}(t-t_*)) (1+O(c^{-1/6}))`
  with `|A_n^(c)(x)| <= C_kappa (1+|x|)^{-1/4}` uniformly for `n <= kappa*c`
- Compute L2-mass in Z_cross: ~`c^{-17/12}` (Prop 2.1)
- Derive c^{-1/2} bound from composite expansion (Theorem A)

What Paper VII MUST NOT re-prove (already in VI):
- c^{-1/4} t^{-1/4} pointwise bound
- L2-tail bound
- Non-vanishing of F_c

Key references: Olver (1974) Ch.11, Stein (1993), Paper VI Thm 3.2 + Lemma 2.3.

---

## Paper VIII -- Lower Bounds (DRAFT)

Goal: `Delta_eps(c,n) >= c_1 c^{-1/2}` (matching lower bound, sharpness of VII).
Status: open problem.

---

## Zone Structure

| Zone | Range of |t-t_*| | Bound | L2-mass |
|---|---|---|---|
| Algebraic | >= c^{-1/3} | c^{-1/4} t^{-1/4} | ~1/2 (bulk) |
| Crossover Z_cross | c^{-2/3} to c^{-1/3} | Paper VII | ~c^{-17/12} |
| Airy peak | <= c^{-2/3} | height ~c^{-1/2} | ~c^{-5/3} |
| Above peak | t >> t_* | e^{-gamma c^{1/2}} | exp. small |

## Scaling Table

| Quantity | Rigorous | Sharp/conjectural |
|---|---|---|
| Omega_eps^abs | ~c^{1/2} | ~c^{1/2} |
| Delta_eps upper | <= C c^{-2/3} (Paper VI) | <= C c^{-1/2} (Paper VII) |
| Delta_eps lower | open | >= c_1 c^{-1/2} (Paper VIII) |
| Crossover L2 | ~c^{-17/12} (Paper VII) | -- |

---

## Key References

- Olver (1974): *Asymptotics and Special Functions*, Academic Press -- turning points, Airy, Ch.11
- Stein (1993): *Harmonic Analysis*, Princeton UP -- van der Corput, oscillatory integrals
- Slepian & Pollak (1961): Bell Syst. Tech. J. 40 -- original PSWF paper
- Landau & Pollak (1962): Bell Syst. Tech. J. 41 -- PSWF uncertainty III
- Berry & Keating (1999): SIAM Rev. 41 -- Riemann zeros and eigenvalue asymptotics
