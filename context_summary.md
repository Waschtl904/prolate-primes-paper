# Series Context Summary — Papers I–VIII

> **Purpose:** Paste this at the top of any new AI chat before working on Paper VIII or later.
> Provides the full logical chain without needing Papers I–VII in full.
> **Current working file:** `paper8.tex` on GitHub (`Waschtl904/prolate-primes-paper`).

---

## Overarching Goal

The series constructs a spectral operator whose eigenvalue distribution
mirrors the non-trivial zeros of the Riemann zeta function (Hilbert–Pólya conjecture).
The core object is the PSWF concentration operator and its Mellin/Fourier transform.
Series arc: coercivity → scaling limits → spectral phase →
bandwidth decay → rigorous peak-width upper bounds → crossover asymptotics
→ lower bounds + spectral-zeta connection.

---

## Central Notation

- `Phi_n^(c)`: rescaled PSWF, `Phi_n^(c)(u) = psi_n^(c)(e^u) e^{u/2}`, `u in (-inf,0)`
- `Phi_hat_n^(c)(t)`: Fourier–Mellin transform of `Phi_n^(c)`
- `t_*(c,n) ~ c^{1/2}`: Fourier peak location (saddle frequency)
- `Delta_eps(c,n)`: peak width — smallest Delta s.t. L2-mass outside `[t_*-Delta, t_*+Delta]` <= eps * total
- `lambda_n^(c)`: Slepian concentration eigenvalue, `lambda_n^(c) in (0,1)`
- `Z_cross = {t : c^{-2/3} <= |t-t_*| <= c^{-1/3}}`: crossover zone
- `H_c`, `H_lim`: concentration operators (c-dependent and limiting)
- `kappa_n^(c)`: Airy normalisation coefficient, proved `|kappa_n^(c)| >= c_kappa > 0` (Paper VIII)

---

## Papers I–V (background, complete)

- **Paper I:** Gram matrix coercivity, coercivity constant ~ `c^{-1/2}`
- **Paper II:** Scaling limits, trace formula linking eigenvalues to primes
- **Paper III:** Spectral phase analysis, evidence for `c^{-1/2}` peak-width scaling
- **Paper IV:** No-go theorem — rules out naive bandlimited constructions
- **Paper V:** Barrier estimate `|Phi_hat_n^(c)(t)| << e^{-gamma c^{1/2}}` for `t >> t_*`;
  numerical evidence for `Delta_eps ~ c^{-1/2}`

---

## Paper VI — Rigorous Upper Bounds (FINAL)

Key results, all used downstream:

- **(VI.1) Pointwise decay:** `|Phi_hat_n^(c)(t)| <= C_kappa c^{-1/4} t^{-1/4}` for `1 <= t <= c^{1/2}`
- **(VI.2) Log-free L2 tail:** `||Phi_hat||_{L2(|t|>R)}^2 <= C_kappa^2 c^{-1/2} R^{-1/2}` for `1 <= R <= c^{1/4}`
- **(VI.3) Airy profile near t_*:** `Phi_hat_n^(c)(t) = c^{-1/2} kappa_n^(c) Ai(c^{2/3}(t-t_*)) (1+O(c^{-1/3}))` for `|t-t_*| <= c^{-1/3}`
- **(VI.4) Peak-width upper bound:** `Delta_eps <= C(kappa,eps) c^{-2/3}` (later improved by Paper VII)
- **(VI.5) L2 normalisation:** `||Phi_hat_n^(c)||_{L2}^2 = 1/2`

---

## Paper VII — Composite Asymptotics in Z_cross (FINAL, `paper7_FINAL.tex`)

Goal achieved: `Delta_eps(c,n) <= C(kappa,eps) c^{-1/2}` (sharp upper bound).

Key results, all used in Paper VIII:

- **(VII.1) Thm B:** `Delta_eps(c,n) <= C(kappa,eps) c^{-1/2}` — sharp upper bound on peak width
- **(VII.2) Thm C:** `||(H_c - H_lim)f|| <= C_kappa c^{-3/4} ||f||` for every fixed unit f (strong rate, not operator norm)
- **(VII.3) Lem 6.2:** `|lambda_n^(c) - lambda_n^(c+1)| <= C_kappa c^{-3/4}` — eigenvalue sensitivity upper bound
- **(VII.4) Cor 3.8:** `int_{Z_cross} |Phi_hat_n^(c)|^2 dt ~ c^{-17/12}` — corrected crossover mass
- **(VII.5) Thm A:** Composite Airy–WKB expansion in Z_cross:
  `Phi_hat_n^(c)(t) = c^{-1/2} A_n^(c)(c^{1/2}(t-t_*)) (1+O(c^{-1/6}))`
  with `|A_n^(c)(x)| <= C_kappa (1+|x|)^{-1/4}` uniformly

Note: Paper VII does **not** prove the matching lower bound `Delta_eps >= c_1 c^{-1/2}`.
This was explicitly left as Problem 7.1 for Paper VIII.

---

## Paper VIII — Non-Cancellation and Sharp Lower Bound (CURRENT, `paper8.tex`)

Status: **complete and internally consistent on GitHub.**

### Main Results

- **Thm `thm:lower` (proved, unconditional):**
  `Delta_eps(c,n) >= c_1(kappa,eps) c^{-1/2}` for all `n <= kappa c`, `c >= c_0`.
  Completes Problem 7.1 of Paper VII.

- **Cor `cor:sharp`:** `Delta_eps(c,n) ~ c^{-1/2}` (two-sided, sharp scaling).

- **Lem `lem:L2-mass` (key lemma):**
  A fixed positive L2-mass fraction concentrates in `|t - t_*| <= R_0 c^{-1/2}`.
  Proof: 5 steps using composite Airy expansion + barrier estimate (right tail)
  + log-free L2 tail (VI.2, left tail) + full L2-norm `= 1/2` as reference.
  **Important correction:** earlier version incorrectly used Slepian eigenvalue
  identity `int_{|t|<=1} = lambda_n^(c)/2` as reference — invalid since
  `t_* ~ c^{1/2} -> inf`, so the window is entirely outside `[0,1]` for large c.

- **Lem `lem:kappa-lower`:** `|kappa_n^(c)| >= c_kappa > 0` (Airy amplitude uniformly bounded below).

- **Lem `lem:airy-window`:**
  `y(t) = c^{1/2}(t-t_*) / (mu_n^(c))^{2/3}` restricted to `|t-t_*| <= c^{-1/2}`
  takes values in a **fixed compact interval** `[-Y_0, Y_0]` independent of c.
  => Ai has finitely many zeros in this window; zero-free intervals have t-width `~ c^{-1/2}`.

- **Thm `thm:nonvanish`:** `|Phi_hat_n^(c)(t)| >= c_1 c^{-1/2}` on a set `E_c`
  with `|E_c| >= c_* c^{-1/2}` (pointwise non-cancellation).

- **Thm `thm:spectral` (two-sided eigenvalue control):**
  `c_kappa c^{-3/4} <= |lambda_n^(c) - lambda_n^(c+1)| <= C_kappa c^{-3/4}`
  - Upper bound: Paper VII Lem 6.2
  - Lower bound: Hellmann–Feynman identity gives `|d lambda/dc| >= 2 c_kappa' > 0`
    (unconditional, independent of c) => `|lambda_n^(c) - lambda_n^(c+1)| >= c_kappa > 0`
    This is **stronger** than `c^{-3/4}` for large c.
    The sharp matching lower bound `>= c_kappa c^{-3/4}` (same rate as upper bound)
    would require refined analysis of `int_0^1 t^2 |Phi_n^(c)(t)|^2 dt ~ c^{-3/4}`;
    this is left as an open problem.

- **Thm `thm:zeta` (conditional on Hyp `hyp:ccm` = CCM2025, Thm 1.3):**
  Each non-trivial zero `rho` of `zeta(s)` lies in `sigma_app(H_lim)` with
  precision `O(c^{-3/4})`.

### Proof Logic of `thm:lower` (contradiction argument)

1. Assume `Delta_eps(c,n) < eta c^{-1/2}` for some fixed `eta`.
2. **Upper bound on integral:** sup-norm `|Phi_hat| <= C_kappa c^{-1/2}` (VII.5)
   => `int_{|t-t_*| <= Delta} |Phi_hat|^2 dt <= C_kappa^2 c^{-1} * 2 eta c^{-1/2} = 2 C_kappa^2 eta c^{-3/2} -> 0`
3. **Lower bound on integral:** Lem `lem:L2-mass` gives `>= (1-eps^2)/2`
4. Contradiction for large c. Hence `Delta_eps >= c_1 c^{-1/2}`.

Note: proof does **not** use the upper bound `Delta_eps <= C c^{-1/2}` (VII.1) — fully independent.

---

## Zone Structure (corrected, Paper VII)

| Zone | Range of `|t-t_*|` | `|Phi_hat|` | L2-mass |
|---|---|---|---|
| Airy peak | `<= c^{-2/3}` | `~ c^{-1/2}` | `~ c^{-5/3}` |
| Crossover Z_cross | `c^{-2/3}` to `c^{-1/3}` | `~ c^{-1/2} |t-t_*|^{-1/4}` | `~ c^{-17/12}` |
| Algebraic | `>= c^{-1/3}` | `<= C_kappa c^{-1/4} t^{-1/4}` | `~ 1/2` (bulk) |
| Above peak | `t >> t_*` | `<= e^{-gamma c^{1/2}}` | negligible |

---

## Key References

- **Olver (1974):** *Asymptotics and Special Functions*, Academic Press — turning points, Airy asymptotics, Ch. 11
- **Osipov–Rokhlin–Xiao (2013):** *Prolate Spheroidal Wave Functions of Order Zero*, Springer
- **Bonami–Karoui (2014):** Uniform bounds of PSWFs and eigenvalue decay, C.R. Math. 352
- **Slepian–Pollak (1961):** Bell Syst. Tech. J. 40 — original PSWF paper
- **CCM2025:** Connes–Consani–Moscovici, *Zeta Spectral Triples*, arXiv:2511.22755
