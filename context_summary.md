# Series Context Summary — Papers I–XV

> **Purpose:** Paste this at the top of any new AI chat before working on Paper XV or later.
> Provides the full logical chain without needing Papers I–XIV in full.
> **Current working file:** `paper15_DRAFT.tex` on GitHub (`Waschtl904/prolate-primes-paper`).
> **Last updated:** April 2026, after Paper XV draft (Weyl equidistribution / mesoscopic kernel estimates).

---

## Overarching Goal

The series constructs a spectral operator whose eigenvalue distribution
mirrors the non-trivial zeros of the Riemann zeta function (Hilbert–Pólya conjecture).
The core object is the PSWF concentration operator and its Mellin/Fourier transform.
Series arc: coercivity → scaling limits → spectral phase →
bandwidth decay → rigorous peak-width upper bounds → crossover asymptotics
→ lower bounds + spectral-zeta connection → domain & self-adjointness (conditional framework)
→ Mosco form convergence & Friedrichs extension → spectral inclusion & density criterion
→ localization principle for spectral projection stability
→ completeness (planned, Paper XIII) → coefficient stability / HS-norm estimates (Papers XIII–XV).

---

## Central Notation

- `Phi_n^(c)`: rescaled PSWF, `Phi_n^(c)(u) = psi_n^(c)(e^u) e^{u/2}`, `u in (-inf,0)`
- `Phi_hat_n^(c)(t)`: Fourier–Mellin transform of `Phi_n^(c)`
- `t_*(c,n) ~ c^{1/2}`: Fourier peak location (saddle frequency)
- `Delta_eps(c,n)`: peak width — smallest Delta s.t. L2-mass outside `[t_*-Delta, t_*+Delta]` <= eps * total
- `lambda_n^(c)`: Slepian concentration eigenvalue, `lambda_n^(c) in (0,1)`
- `lambda_n^(inf)`: limit eigenvalue, `lambda_n^(inf) := lim_{c->inf} lambda_n^(c)` (Paper IX, inherited from VIII Cor 4.3)
- `Phi_n^(inf)`: strong limit of `Phi_n^(c_k)` along the fixed diagonal subsequence `c_k`; ONS property holds (Paper XI, Lem. diagonal)
- `Z_cross = {t : c^{-2/3} <= |t-t_*| <= c^{-1/3}}`: crossover zone
- `H_c` (`\Hc`): finite-c PSWF concentration operator, bounded self-adjoint, `||H_c|| <= 1`
- `H_SOT` / `H_lim` (`\Hlim`): SOT-limit of H_c along `c_k`; bounded self-adjoint, `||H_SOT|| <= 1`; exists unconditionally (Paper X Lem 2.2). ALL spectral statements hold **along the fixed diagonal subsequence c_k** (Paper XI); subsequence-independence is Open Problem (Paper XI Prob. 3).
- `H_spec`: spectral operator defined by series `sum_n lambda_n^(inf) <f, Phi_n^(inf)> Phi_n^(inf)`; closable, symmetric (Paper IX Thm 3.3)
- `q_c`, `q_lim`: associated quadratic forms (Paper X)
- `kappa_n^(c)`: Airy normalisation coefficient, proved `|kappa_n^(c)| >= c_kappa > 0` (Paper VIII)
- `Dom(H_spec)`: canonical domain via spectral series (Paper IX, Def 3.1)
- `A_N^(c)`, `A_N^(c,(M))`: PSWF compression (Gram) operator and its M-truncation (Papers XIII–XV)
- `D^(M)`: diagonal reference operator (Paper XIV)
- `Sigma_near`, `Sigma_int`, `Sigma_far`: HS-norm decomposition of `||A_N^(c,(M)) - D^(M)||_HS^2` (Paper XIV)
- `I_c(k)`: oscillatory model kernel coefficient `int e^{ik*theta(xi)/c} w(xi) dxi` (Paper XV)
- `Sigma_model(c)`: `sum_{k=1}^{K(c)} |I_c(k)|^2`, the key intermediate-regime sum (Paper XV)
- `theta(xi)`: WKB phase extracted from PSWF ODE; `theta'(xi) = p(xi/c; alpha) > 0`; `theta''(xi) != 0` for `xi != 0` (Paper XV Lem. 4.2)

### ⚠️ Critical distinction (established after Paper IX referee process, confirmed through Paper XII)

`H_SOT` and `H_spec` are **two separate objects**:
- `H_SOT` = SOT-limit, bounded, self-adjoint, `Dom = L^2` — **unconditional**
- `H_spec` = formal spectral series operator — **closable and symmetric, unconditional**
- The identification `H_SOT = closure(H_spec)` is **Paper IX Open Problem 7 / Paper X Bridge Theorem (conditional on Hyp.(IX.b))** — **not proved anywhere in the series**

### ⚠️ Riesz-basis status (updated after Paper XII)

`{Phi_n^(inf)}` is an orthonormal system (ONS) along `c_k`. It is trivially a Riesz basis **with bounds 1,1** due to orthonormality (Paper XII Cor. 7.1). This is **NOT a nontrivial result** — it does not imply completeness, does not resolve the Bridge theorem, and does not close any open problem. The Riesz-basis approach mentioned in older summaries as the "recommended path" is **no longer operative** as a standalone strategy.

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

- **(VI.1) Pointwise decay:** `|Phi_hat_n^(c)(t)| <= C_kappa c^{-1/4} t^{-1/4}` for `1 <= t <= c^{1/2}`
- **(VI.2) Log-free L2 tail:** `||Phi_hat||_{L2(|t|>R)}^2 <= C_kappa^2 c^{-1/2} R^{-1/2}` for `1 <= R <= c^{1/4}`
- **(VI.3) Airy profile near t_*:** `Phi_hat_n^(c)(t) = c^{-1/2} kappa_n^(c) Ai(c^{2/3}(t-t_*)) (1+O(c^{-1/3}))` for `|t-t_*| <= c^{-1/3}`
- **(VI.4) Peak-width upper bound:** `Delta_eps <= C(kappa,eps) c^{-2/3}` (later improved by Paper VII)
- **(VI.5) L2 normalisation:** `||Phi_hat_n^(c)||_{L2}^2 = 1/2`

---

## Paper VII — Composite Asymptotics in Z_cross (FINAL)

- **(VII.1) Thm B:** `Delta_eps(c,n) <= C(kappa,eps) c^{-1/2}` — sharp upper bound on peak width
- **(VII.2) Thm C:** `||(H_c - H_SOT)f|| <= C_kappa c^{-3/4} ||f||` for every **fixed unit f** (pointwise-in-f rate, NOT operator norm)
- **(VII.3) Lem 6.2:** `|lambda_n^(c) - lambda_n^(c+1)| <= C_kappa c^{-3/4}`
- **(VII.4) Cor 3.8:** `int_{Z_cross} |Phi_hat_n^(c)|^2 dt ~ c^{-17/12}`
- **(VII.5) Thm A:** Composite Airy–WKB expansion in Z_cross

Note: Paper VII does **not** prove operator-norm convergence `||H_c - H_SOT|| -> 0`.

---

## Paper VIII — Non-Cancellation and Sharp Lower Bound (FINAL)

- **Thm `thm:lower`:** `Delta_eps(c,n) >= c_1(kappa,eps) c^{-1/2}` — unconditional
- **Cor `cor:sharp`:** `Delta_eps(c,n) ~ c^{-1/2}` (sharp two-sided)
- **Lem `lem:kappa-lower`:** `|kappa_n^(c)| >= c_kappa > 0`
- **Thm `thm:nonvanish`:** `|Phi_hat_n^(c)(t)| >= c_1 c^{-1/2}` on set `E_c` with `|E_c| >= c_* c^{-1/2}`
- **Cor 4.3 (critical import):** `|lambda_n^(c) - lambda_n^(inf)| <= C_kappa c^{-1/4}` — used in Papers IX, X, XI, XII
- **Thm `thm:zeta` (conditional on Hyp CCM):** each zeta zero `rho` lies in `sigma_app(H_lim)` with precision `O(c^{-3/4})`

---

## Paper IX — Conditional Framework: Domain, Closability, Self-Adjointness (DRAFT)

**Architecture:** Conditional framework paper. All results labelled unconditional/conditional explicitly.

### Unconditional Results

- **Lem 3.1 (PSWF precompactness):** `{Phi_n^(c)}` precompact in L2; every subsequence has a further subsequence converging strongly to a unit vector.
- **Prop 2.2:** `||Phi_n^(inf)|| = 1` (used at exactly one point in Paper XI).
- **Thm 3.3 (Closability + symmetry of H_spec):** H_spec closable and symmetric.

### Hypotheses (none proved in Paper IX)

- **Hyp 1:** H_SOT has purely discrete spectrum with simple eigenvalues — central black box.
- **Hyp 2:** Norm-resolvent convergence.
- **Hyp 3:** Completeness of `{Phi_n^(inf)}`.
- **Hyp 4:** Uniform alignment `sup_{n<=kappa c} ||Phi_n^(c) - Phi_n^(inf)|| <= C_kappa c^{-1/4}`.

### Open Problem 7 (THE central open problem of the series)

`closure(H_spec) = H_SOT` — not proved anywhere.

---

## Paper X — Mosco Form Convergence & Friedrichs Extension (DRAFT, v46)

**Architecture:** Works entirely with H_SOT as **bounded**. All main results **unconditional** except the Bridge theorem.

### Unconditional Results

- **Lem `lem:ftb`:** `<H_c f, f> = ||B_c(P*Pf)||^2`
- **Thread A:** SOT-limit `H_str` exists uniquely in B(L2) — UNCONDITIONAL
- **Thread B:** Mosco convergence `q_c ->^M q_lim` — UNCONDITIONAL
- **Thm `thm:friedrichs`:** `T_{q_lim} = H_str` — UNCONDITIONAL
- **Cor `cor:resolvent`:** Strong resolvent convergence `(H_c - z)^{-1} ->^s (H_lim - z)^{-1}` — UNCONDITIONAL
- **Thm `thm:rate-ext`:** `0 <= q_lim - q_c <= C_kappa c^{-1/4} ||f||^2` (from Paper VIII Cor 4.3 only) — UNCONDITIONAL

### Conditional Result

- **Thm `thm:bridge` [Hyp.(IX.b)]:** `H_str = closure(H_spec)` — CONDITIONAL on Paper IX Open Problem 7.

---

## Paper XI — Spectral Structure and Density (FINAL)

**Architecture:** Establishes spectral geometry of `H_lim` along the fixed diagonal subsequence `c_k`.

### Unconditional Results (along c_k)

- **Lem `lem:diagonal` (Cantor diagonal):** Fixed subsequence `c_k` s.t. `Phi_n^(c_k) -> Phi_n^(inf)` strongly (uses `||Phi_n^(inf)||=1` from Paper IX Prop 2.2), `lambda_n^(c_k) -> lambda_n^(inf)`, `H_{c_k} ->^SOT H_lim`. `{Phi_n^(inf)}` is ONS.
- **Lem `lem:eigenvalue-eq`:** `H_lim Phi_n^(inf) = lambda_n^(inf) Phi_n^(inf)` — **H_lim has a genuine eigenstructure** (unconditional along c_k). Proof uses 3-term decomposition (A_k + B_k + C_k -> 0) bypassing non-commutation of limits.
- **Thm `thm:spectral-inclusion`:** `closure({lambda_n^(inf)}) ⊂ sigma_p(H_lim) ⊂ sigma(H_lim) ⊂ [0,1]` — UNCONDITIONAL.
- **Thm `thm:density-criterion`:** Density of `{lambda_n^(inf)}` in [0,1] implies `sigma(H_lim) = [0,1]`.

### Conditional Result

- **Thm `thm:weyl` (Semiclassical spectral transfer) [Hyp. NAcc]:** For each `lambda in (0,1)`, there exists `n(lambda)` s.t. `lambda_{n(lambda)}^(inf) = lambda + O(c(lambda)^{-1/4})` and `n(lambda) = floor(2c(lambda)/pi) + O(log c(lambda))`. This is an **inverse spectral localization result, NOT a Weyl counting law**.

### Key new feature vs. older summaries

- `H_lim` is **confirmed to have actual eigenvectors `{Phi_n^(inf)}`** with corresponding eigenvalues `{lambda_n^(inf)}` (unconditionally along c_k).
- The spectral inclusion `sigma_p(H_lim) != empty` is **proved**.
- Subsequence-independence (`Phi_n^(inf)` and `lambda_n^(inf)` independent of diagonal subsequence up to phase) remains **Open Problem (XI Prob. 3)**.

### Open Problems in Paper XI

1. Density of `{lambda_n^(inf)}` in [0,1] (Conj. XI density)
2. No Accumulation / gap lower bound `|lambda_n^(c) - lambda_{n+1}^(c)| >= C_kappa c^{-3/4}`
3. **Uniqueness** (subsequence-independence) — all XI statements currently hold only along c_k
4. Form rate sharpness
5. Completeness of `{Phi_n^(inf)}`

---

## Paper XII — Localization Principle for Spectral Projection Stability (DRAFT)

**Architecture:** Abstract operator-theoretic result + conditional PSWF application.

### Fully Proved Abstract Results

- **Thm `thm:mechanism` (Exact Mechanism Factorization):** Scalar invariant
  `R_k := ||(A_k - A)phi|| / gamma_k + |lambda_k - lambda| / gamma_k`
  controls spectral projection stability via 3 exact steps:
  - (M1) Rank-one scalar reduction: `||P_k - P^inf|| = ||(I - P_k)phi||`
  - (M2) Spectral gap resolvent bound: `||(I-P_k)phi|| <= ||(A_k - lambda_k)phi|| / gamma_k`
  - (M3) SOT residual triangle: `||(A_k - lambda_k)phi|| <= ||(A_k - A)phi|| + |lambda_k - lambda|`
- **Thm `thm:abstract`:** `R_k -> 0 => ||P_k - P^inf|| -> 0` (sufficient).
- **Thm `thm:necessary-bounded-gap`:** Necessary when `gamma_k >= c_0 > 0`.
- **Prop `prop:no-go`:** Bypassing a gap condition is provably impossible.
- **Prop `prop:separation`:** `||A_k - A|| ≡ 1` but full projection stability — Davis–Kahan is incompatible with this regime.
- **Cor `cor:riesz` (trivial):** `{Phi_n^(inf)}` is a Riesz basis with bounds 1,1. Follows trivially from orthonormality. **Not a nontrivial contribution.**

### Conditional PSWF Results (conditional on Gap-S and SOT-Faster)

- **Cor `cor:convergence`:** `||P_n^(c_k) - P_n^(inf)|| -> 0` (spectral projection convergence).
- **Cor `cor:rate`:** Rate `O(c_k^{-1/4} / g(c_k))`.

### Two sole remaining open hypotheses for PSWF projection stability

- **Gap-S (Hyp. XII.1):** `|lambda_n^(c) - lambda_{n+1}^(c)| >= g(c)` with `c^{-1/4}/g(c) -> 0`. Conjectured `g(c) ~ (log c)^{-1}` via sine-kernel repulsion. **OPEN.**
- **SOT-Faster (Hyp. XII.2):** `||(H_{c_k} - H_lim) Phi_n^(inf)|| = o(g(c_k))`. Strictly weaker than any uniform rate. **OPEN.**

---

## Papers XIII–XIV — Coefficient Stability and HS-Norm Estimates (DRAFT)

*(Full text not yet in summary — reconstructed from Paper XV references.)*

### Reduction Chain (Paper XIV)

```
(C) + (D-strong)  =>  S_N^{(M(c))}(c) ~ c_0*beta > 0  =>  H3 fails  =>  H1 fails
```

- **HS decomposition** (Paper XIV): `||A_N^(c,(M)) - D^(M)||_HS^2 = Sigma_near + Sigma_int + Sigma_far`
- `Sigma_near = O(1/c) = o(1)` — **proved** (conditional on (C))
- `Sigma_far = o(1)` — **accessible** via stationary phase
- `Sigma_int = o(1)` — **the sole remaining obstruction** (target of Paper XV)

### Condition (C) — Local Weyl Law

Uniformly in `n in T_{alpha,kappa}(c)`:
`mu_{n,c}([-c_0, c_0]) = c_0/c + o(1/c)`

Required for frozen weight approximation and near-diagonal control. **Remains open** (Paper XV Prob. 7.1).

### Condition (D-strong) — Off-diagonal HS decay

`Sigma_int = sum_{C < |n-m| <= c^{theta_0}} |(A_N^(c,(M)))_{nm}|^2 = o(1)` for `M(c) ~ beta*c`.

---

## Paper XV — Intermediate-Regime Kernel Estimates (DRAFT)

**Title:** *Intermediate-Regime Kernel Estimates for the PSWF Compression Operator: Mesoscopic Scaling, WKB Phase Extraction, and Weyl Equidistribution*

**Main achievement:** Resolves the sole remaining analytic obstruction from Paper XIV: `Sigma_model(c) = o(1)`.

### Key Results (proved in Paper XV)

- **WKB phase extraction (Lem. 4.1):** Phase `theta(xi) = c * int_0^{xi/c} p(zeta; alpha) dzeta` explicitly identified from PSWF ODE, where `p(zeta; alpha) = sqrt((lambda(alpha) - zeta^2)/(1 - zeta^2))`.
- **Phase non-degeneracy (Lem. 4.2):**
  - `theta'(xi) = p(xi/c; alpha) > 0` for all `|xi| < c*sqrt(lambda(alpha))`
  - `theta''(xi) != 0` for `xi != 0` (since `lambda(alpha) in (0,1)` for `alpha in (0,1)`)
  - `theta''(0) = 0` but `theta'''(0) != 0` (cubic non-degeneracy; handled by Airy-type control)
- **No-go for linear phase (Cor. 3.2):** Frozen-phase model gives `Sigma_strip = Theta(c^{2-theta_0}) -> inf`. Nonlinear phase (`theta'' != 0`) is essential.
- **Uniform Degenerate Phase Lemma (UDPL, Lem. 5.1):** Provides uniform oscillatory integral bound `C * mu_1^{-3/5} * mu_3^{-1/5}` handling both the away-from-zero (IBP) and near-zero (Airy) regimes simultaneously, uniformly in the parameter h.
- **Joint k/xi_0 Decoupling (Prop. 5.2):** `|T(c)| = O(c^{3*theta_0/4 + eps}) = o(c^{theta_0})` via Weyl-differencing (Stage 1) + UDPL (Stage 2) + optimisation H ~ c^{(1+theta_0)/2} (Stage 3).
- **Cor. 5.3:** `Sigma_model(c) = o(1)` unconditionally (given theta non-degeneracy).

### Status of Paper XV targets

| Target | Status |
|---|---|
| `Sigma_model(c) = o(1)` | **PROVED** (Cor. 5.3) |
| Lipschitz regularity of PSWF amplitude (Prob. 6.1) | **OPEN** (critical) |
| Local Weyl law (C) uniformly in n (Prob. 7.1) | **OPEN** (critical, inherited from Paper XIV) |
| `Sigma_int = o(1)` (full) | **Conditional** on Prob. 6.1 + Prob. 7.1 |
| (D-strong) | **Conditional** on Sigma_int |
| H3 fails, H1 fails | **Conditional** on (C) + (D-strong) |

### Logical status summary for Paper XV

```
theta identified + theta' != 0 + theta'' != 0 (xi != 0)     PROVED
Linear phase => Model-Sigma fails                             PROVED (no-go)
Naive van der Corput insufficient                             PROVED
Weyl for fixed beta: O(c^{theta_0/2})                        AVAILABLE (W1)
Joint k/xi_0 decoupling                                       PROVED (Prop. 5.2)
Sigma_model = o(1)                                            PROVED (Cor. 5.3)
Lipschitz regularity (amplitude)                              OPEN
Local Weyl law (C)                                            OPEN
Sigma_int = o(1)                                              CONDITIONAL
```

---

## The Central Open Problems of the Series (as of Paper XV)

After Papers I–XV, the programme reduces to the following distinct open fronts:

### Front A — Operator Identification (from Papers IX–XII)

```
H_SOT  =?=  closure(H_spec)
```
Still the central structural problem. Paper X Bridge Theorem is conditional on this.

### Front B — Spectral Completeness & Uniqueness (from Papers XI–XII)

- Completeness of `{Phi_n^(inf)}` in L2
- Subsequence-independence of `Phi_n^(inf)`, `lambda_n^(inf)` (up to phase)
- Gap lower bound `|lambda_n^(c) - lambda_{n+1}^(c)| >= C_kappa c^{-3/4}` (implies NAcc)

### Front C — Coefficient Stability / HS Programme (Papers XIII–XV)

Two critical open problems remain before `Sigma_int = o(1)` is fully established:
1. **Lipschitz regularity of PSWF amplitude (Paper XV Prob. 6.1):**
   `||Phi_hat_{n+k}^(c) - Phi_hat_n^(c)||_{L2([-c_0,c_0])} = O(k/c)` uniformly in `n in T_{alpha,kappa}(c)`, `|k| <= c^{theta_0}`.
   Plausible from WKB smooth `n/c`-dependence of amplitude; rigorous L2-control of semiclassical transport equation needed.
2. **Local Weyl Law (C) (Paper XV Prob. 7.1):**
   `mu_{n,c}([-c_0,c_0]) = c_0/c + o(1/c)` uniformly in `n in T_{alpha,kappa}(c)`.
   Main difficulty: uniformity near turning point as `n/c -> alpha`.

---

## Correct Logical Dependencies (Papers IX–XV)

| What later papers use | Source | Status |
|---|---|---|
| Rate `|lambda_n^(c) - lambda_n^(inf)| <= C c^{-1/4}` | Paper VIII Cor 4.3 | Unconditional |
| `||Phi_n^(inf)|| = 1` | Paper IX Prop 2.2 | Unconditional |
| `H_spec` closable, symmetric | Paper IX Thm 3.3 | Unconditional |
| SOT-limit `H_lim` exists, `Dom = L^2`, `||H_lim|| <= 1` | Paper X Thread A | Unconditional |
| Mosco convergence, Friedrichs, strong resolvent conv. | Paper X | Unconditional |
| `H_lim Phi_n^(inf) = lambda_n^(inf) Phi_n^(inf)` (along c_k) | Paper XI Lem eigenvalue-eq | Unconditional (along c_k) |
| Spectral inclusion `sigma_p(H_lim) != empty` | Paper XI Thm spectral-inclusion | Unconditional (along c_k) |
| Localization principle (abstract) | Paper XII Thm mechanism | Fully proved |
| `H_SOT = closure(H_spec)` — Bridge | Paper IX Open Problem 7 | **Structural hypothesis, NOT proved** |
| Subsequence-independence | Paper XI Open Problem 3 | **OPEN** |
| Gap-S | Paper XII Hyp. 3.1 | **OPEN** |
| SOT-Faster | Paper XII Hyp. 3.4 | **OPEN** |
| Lipschitz regularity of PSWF amplitude | Paper XV Prob. 6.1 | **OPEN** |
| Local Weyl law (C) | Paper XV Prob. 7.1 | **OPEN** |

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
- **Kato (1966):** *Perturbation Theory for Linear Operators*, Springer
- **Reed–Simon (1975):** *Methods of Modern Mathematical Physics, Vol. II*, Academic Press
- **Mosco (1969):** *Convergence of convex sets*, Adv. Math. 3, 510–585
- **Kuwae–Shioya (2003):** *Convergence of spectral structures*, Comm. Anal. Geom. 11, 599–673
- **Widom (1964):** *Asymptotic behavior of eigenvalues II*, Arch. Ration. Mech. Anal. 17 — average gap density `~ (log c)^{-1}`
- **Davis–Kahan (1970):** SIAM J. Numer. Anal. 7 — rotation of eigenvectors (incompatible with Paper XII regime)
- **Stein (1993):** *Harmonic Analysis*, Princeton — van der Corput, Airy bounds
- **Titchmarsh (1986):** *Theory of the Riemann Zeta-Function*, Oxford — Weyl differencing, exponent pairs
- **Weyl (1916):** Equidistribution mod 1, Math. Ann. 77
- **Rudin (1991):** *Functional Analysis*, 2nd ed., McGraw-Hill
- **Zworski (2012):** *Semiclassical Analysis*, AMS
- **Böttcher–Silbermann (1990):** *Analysis of Toeplitz Operators*, Springer
- **Simon (2011):** *Szegő's Theorem and Its Descendants*, Princeton
