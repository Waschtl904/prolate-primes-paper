# Series Context Summary — Papers I–XVI

> **Purpose:** Paste this at the top of any new AI chat before working on Paper XVII or later.
> Provides the full logical chain without needing Papers I–XV in full.
> **Current working file:** `paper_xvi_draft.tex` on GitHub (`Waschtl904/prolate-primes-paper`).
> **Last updated:** April 2026, after Paper XVI draft (Lagrangian Singularity Transport / Airy Normal Form).

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
→ completeness (planned, Paper XIII) → coefficient stability / HS-norm estimates (Papers XIII–XV)
→ **microlocal Lagrangian singularity transport / Airy normal form (Paper XVI)**.

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
- `Phi(u;c)` (Paper XVI): fold amplitude `e^{i alpha_* u} int |beta|^{-1/2} e^{i(Theta(beta;c)+beta u)} chi d beta`
- `c_3(c)` (Paper XVI): cubic WKB coefficient `(1/6) theta'''(alpha_*;c) != 0`
- `C ⊂ T*R_beta × T*R_u` (Paper XVI): canonical relation, locally `{(beta, Theta'(beta;c)+u; u, beta)}`
- `S^m_{1,0}(c)` (Paper XVI): parameter-dependent symbol class in u, uniform in c (external parameter, NOT phase-space variable; no polyhomogeneous expansion assumed)

### ⚠️ Critical distinction (established after Paper IX referee process, confirmed through Paper XII)

`H_SOT` and `H_spec` are **two separate objects**:
- `H_SOT` = SOT-limit, bounded, self-adjoint, `Dom = L^2` — **unconditional**
- `H_spec` = formal spectral series operator — **closable and symmetric, unconditional**
- The identification `H_SOT = closure(H_spec)` is **Paper IX Open Problem 7 / Paper X Bridge Theorem (conditional on Hyp.(IX.b))** — **not proved anywhere in the series**

### ⚠️ Riesz-basis status (updated after Paper XII)

`{Phi_n^(inf)}` is an orthonormal system (ONS) along `c_k`. It is trivially a Riesz basis **with bounds 1,1** due to orthonormality (Paper XII Cor. 7.1). This is **NOT a nontrivial result** — it does not imply completeness, does not resolve the Bridge theorem, and does not close any open problem.

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

- **Lem 3.1 (PSWF precompactness):** `{Phi_n^(c)}` precompact in L2.
- **Prop 2.2:** `||Phi_n^(inf)|| = 1`.
- **Thm 3.3 (Closability + symmetry of H_spec):** H_spec closable and symmetric.

### Open Problem 7 (THE central open problem of the series)

`closure(H_spec) = H_SOT` — not proved anywhere.

---

## Paper X — Mosco Form Convergence & Friedrichs Extension (DRAFT, v46)

### Unconditional Results

- **Thread A:** SOT-limit `H_str` exists uniquely in B(L2)
- **Thread B:** Mosco convergence `q_c ->^M q_lim`
- **Thm `thm:friedrichs`:** `T_{q_lim} = H_str`
- **Cor `cor:resolvent`:** Strong resolvent convergence `(H_c - z)^{-1} ->^s (H_lim - z)^{-1}`
- **Thm `thm:rate-ext`:** `0 <= q_lim - q_c <= C_kappa c^{-1/4} ||f||^2`

### Conditional Result

- **Thm `thm:bridge` [Hyp.(IX.b)]:** `H_str = closure(H_spec)` — CONDITIONAL.

---

## Paper XI — Spectral Structure and Density (FINAL)

### Unconditional Results (along c_k)

- **Lem `lem:diagonal`:** Fixed subsequence `c_k`; `{Phi_n^(inf)}` is ONS.
- **Lem `lem:eigenvalue-eq`:** `H_lim Phi_n^(inf) = lambda_n^(inf) Phi_n^(inf)`.
- **Thm `thm:spectral-inclusion`:** `closure({lambda_n^(inf)}) ⊂ sigma_p(H_lim) ⊂ sigma(H_lim) ⊂ [0,1]`.
- **Thm `thm:density-criterion`:** Density of `{lambda_n^(inf)}` in [0,1] implies `sigma(H_lim) = [0,1]`.

### Open Problems in Paper XI

1. Density of `{lambda_n^(inf)}` in [0,1]
2. Gap lower bound `|lambda_n^(c) - lambda_{n+1}^(c)| >= C_kappa c^{-3/4}`
3. Subsequence-independence — all XI statements hold only along c_k
4. Completeness of `{Phi_n^(inf)}`

---

## Paper XII — Localization Principle for Spectral Projection Stability (DRAFT)

### Fully Proved Abstract Results

- **Thm `thm:mechanism`:** Exact Mechanism Factorization.
- **Thm `thm:abstract`:** `R_k -> 0 => ||P_k - P^inf|| -> 0`.
- **Prop `prop:no-go`:** Bypassing gap condition is provably impossible.

### Two remaining open hypotheses for PSWF projection stability

- **Gap-S (Hyp. XII.1):** `|lambda_n^(c) - lambda_{n+1}^(c)| >= g(c)` with `c^{-1/4}/g(c) -> 0`. **OPEN.**
- **SOT-Faster (Hyp. XII.2):** `||(H_{c_k} - H_lim) Phi_n^(inf)|| = o(g(c_k))`. **OPEN.**

---

## Papers XIII–XIV — Coefficient Stability and HS-Norm Estimates (DRAFT)

- **HS decomposition:** `||A_N^(c,(M)) - D^(M)||_HS^2 = Sigma_near + Sigma_int + Sigma_far`
- `Sigma_near = O(1/c)` — proved (conditional on (C))
- `Sigma_far = o(1)` — accessible via stationary phase
- `Sigma_int = o(1)` — sole remaining obstruction (target of Paper XV)

---

## Paper XV — Intermediate-Regime Kernel Estimates (DRAFT)

**Main achievement:** `Sigma_model(c) = o(1)` proved (Cor. 5.3).

### Key Results

- **WKB phase extraction (Lem. 4.1):** `theta(xi)` identified from PSWF ODE.
- **Phase non-degeneracy (Lem. 4.2):** `theta''(0)=0`, `theta'''(0)!=0` (cubic non-degeneracy; Airy-type control needed).
- **UDPL (Lem. 5.1):** Uniform degenerate phase bound handling Airy + IBP regimes.
- **Cor. 5.3:** `Sigma_model(c) = o(1)` unconditionally (given theta non-degeneracy).

### Open problems (Paper XV)

- **Prob. 6.1:** Lipschitz regularity of PSWF amplitude. **OPEN (critical).**
- **Prob. 7.1:** Local Weyl law (C). **OPEN (critical).**

---

## Paper XVI — Lagrangian Singularity Transport under Fourier Duality (DRAFT, referee-ready)

**Full title:** *Lagrangian Singularity Transport under Fourier Duality: Cubic WKB Phases, A₂-Fold Singularities, and the Airy Normal Form*

**Setting:** One-dimensional throughout (`beta, u ∈ R`).

**Role in series:** Provides the rigorous microlocal foundation for the Airy normal form used in Papers VI–VII. Translates the conormal singularity + cubic WKB phase structure (already identified in Paper XV Lem. 4.2) into the language of FIO theory, A₂ stable Lagrange singularities, and Hörmander's conormal distributions.

### Architecture

Three results, each conditional on Assumption 4.1 (uniform A₂-stability, conditions (i)–(vi)).

**Assumption 4.1 (uniform A₂-stability) — conditions:**
- (i) `Theta(beta;c) = c_3(c) beta^3 + O(beta^4)` in c-independent neighbourhood
- (ii) `c_3(c) >= delta_0 > 0`
- (iii) Uniform van der Corput: `|Theta''(beta^*(u);c)| >= delta_1 |u|^{1/2}`
- (iv) Uniform Jacobian decay: `|d^k_u J| <= C_k (1+|u|)^{-1/2-k}`
- (v) No secondary stationary points uniformly in c
- (vi) **Critical:** uniform symbol-type bounds of order 0 on CFU map t(beta,u;c); `|det(dt/dbeta)| >= delta_5 > 0`; uniform non-stationary phase bound `delta_4 > 0` outside Airy critical region

**Condition (vi) is the key hypothesis** — upgrades all estimates from "fixed c" to "uniform in c ≥ c_0". Its verification for PSWF is **Open Problem (XVI, prob:PSWF-microlocal)**, the primary target of Paper XVII.

### Main Results

- **Thm `thm:endpoint` [Rig]:** `|Phi(u;c)| = O(|u|^{-1/2})` — endpoint decay, unconditional under Assumption `ass:fold-local`.
- **Thm `thm:airy-normalform` [Rig, conditional (i)–(vi)]:** Phi(u;c) is microlocally equivalent (in a conic neighbourhood of the fold point), modulo smoothing operators, to `e^{i(alpha_* u + R(u;c))} [a(u;c) Ai(c_3(c)^{-1/3} u) + r(u;c)]`, where `a ∈ S^{-1/2}_{1,0}(c)` and `|r| = O((1+|u|)^{-N})` uniformly in c.
- **Cor `cor:pointwise` [Cond, (i)–(vi)]:** `|Phi(u;c)| <= C(1+|u|)^{-3/4}` uniformly in c.
- **Cor `cor:global-bound` [Cond, (i)–(vi)]:** `|int_0^U Phi| = O(U^{1/4})` (Cesàro improvement over O(U^{1/2})).
- **Hypothesis `hyp:FIO-rigidity` [non-standard]:** Airy-class bound => A₂-fold in canonical relation. Correctly labelled as inverse reconstruction conjecture, not standard FIO.

### Key microlocal constructions

- **Conormal amplitude:** `|beta|^{-1/2} chi ∈ I^{-1/4}(R, {0})` — Hörmander Ch. 18.2 / Guillemin–Uhlmann framework
- **CFU as FIO:** Chester–Friedman–Ursell reduction treated as microlocal equivalence modulo `Psi^{-inf}`, NOT as a pointwise phase identity. Remainder `R_c ∈ Psi^{-inf}(R)` with `R_c: H^s -> H^{s+N}` uniformly in c (requires (vi)).
- **Canonical relation:** locally `C = {(beta, Theta'(beta;c)+u; u, beta)}` using standard sign convention `eta = d_u Psi`. Fourier transform = symplectic involution `(beta,xi;u,eta) -> (u,-eta;beta,-xi)`.
- **Joint scaling:** `-3/4` exponent arises from a single stationary-phase expansion in `t_tilde` (not product of two mechanisms). `a ∈ S^{-1/2}` = leading coefficient; `Ai(...)` = oscillatory envelope. Both bounds are a posteriori estimates only.
- **Symbol class `S^m_{1,0}(c)`:** parameter-dependent family in u, uniform in c. `c` is external parameter, NOT phase-space variable. No polyhomogeneous expansion assumed. Does NOT correspond to `S^m_{1,0}(R_{u,c})`.
- **Maslov phase:** absorbed into `R(u;c)` in the normal form; computed from Maslov index of C following Hörmander Ch. 25.1.

### Critical Assumption — Open Problem

**Open Problem (`prob:PSWF-microlocal`):** Does the PSWF amplitude `g(alpha;c) = |alpha - alpha_*|^{-1/2} e^{i theta(alpha;c)}` satisfy Assumptions `ass:fold-local` and `ass:microlocal` uniformly in c → ∞?
- Sub-question (a): `c_3(c) >= delta_0 > 0` (Olver WKB)?
- Sub-question (b): `theta''(alpha;c) != 0` for `alpha != alpha_*`, uniformly?
- Sub-question (c): Conditions (iv) and (vi) for the PSWF CFU Jacobian?

This is the **primary target of Paper XVII**.

### Key references added in Paper XVI

- **Arnold (1972):** Normal forms near degenerate critical points — A₂ classification
- **Golubitsky–Guillemin (1973):** Stable Mappings — coordinate-free stability conditions
- **Guillemin–Uhlmann (1981):** Oscillatory integrals with singular symbols — conormal distributions
- **Melrose–Uhlmann (1979):** Lagrangian intersection and Cauchy problem
- **Chester–Friedman–Ursell (1957):** CFU steepest descent extension
- Hörmander (1983) Ch. 18.1–18.2 (conormal), Ch. 7.7 (stationary phase), Ch. 25.1 (Maslov)
- Zworski (2012), Olver (1974) — already in series references

---

## The Central Open Problems of the Series (as of Paper XVI)

### Front A — Operator Identification (Papers IX–XII)

```
H_SOT  =?=  closure(H_spec)
```
Still the central structural problem.

### Front B — Spectral Completeness & Uniqueness (Papers XI–XII)

- Completeness of `{Phi_n^(inf)}` in L2
- Subsequence-independence of `Phi_n^(inf)`, `lambda_n^(inf)`
- Gap lower bound `|lambda_n^(c) - lambda_{n+1}^(c)| >= C_kappa c^{-3/4}`

### Front C — Coefficient Stability / HS Programme (Papers XIII–XV)

- **Prob. 6.1 (Paper XV):** Lipschitz regularity of PSWF amplitude. **OPEN.**
- **Prob. 7.1 (Paper XV):** Local Weyl law (C). **OPEN.**

### Front D — Microlocal PSWF Verification (Paper XVI → XVII) ⬅ NEW

- **Prob. `prob:PSWF-microlocal` (Paper XVI):** Verify A₂-stability Assumption 4.1 (especially (vi)) for PSWF uniformly in c → ∞.
  - (a) `c_3(c) >= delta_0`: probably accessible via Olver WKB
  - (b) `theta'' != 0` away from alpha_*: plausible from Paper XV Lem. 4.2
  - (c) Uniform CFU Jacobian bounds (vi): **hardest sub-problem**, requires explicit PSWF phase control

---

## Correct Logical Dependencies (Papers IX–XVI)

| What later papers use | Source | Status |
|---|---|---|
| Rate `|lambda_n^(c) - lambda_n^(inf)| <= C c^{-1/4}` | Paper VIII Cor 4.3 | Unconditional |
| `||Phi_n^(inf)|| = 1` | Paper IX Prop 2.2 | Unconditional |
| SOT-limit `H_lim` exists | Paper X Thread A | Unconditional |
| `H_lim Phi_n^(inf) = lambda_n^(inf) Phi_n^(inf)` | Paper XI Lem eigenvalue-eq | Unconditional (along c_k) |
| Spectral inclusion | Paper XI Thm spectral-inclusion | Unconditional (along c_k) |
| Localization principle (abstract) | Paper XII Thm mechanism | Fully proved |
| `theta''(0)=0`, `theta'''(0)!=0` (cubic non-deg.) | Paper XV Lem. 4.2 | Unconditional |
| Sigma_model = o(1) | Paper XV Cor. 5.3 | Unconditional (given theta non-deg.) |
| Airy normal form microlocally | Paper XVI Thm airy-normalform | Conditional on (i)–(vi) |
| `|Phi(u;c)| <= C(1+|u|)^{-3/4}` | Paper XVI Cor pointwise | Conditional on (i)–(vi) |
| Cesàro `O(U^{1/4})` | Paper XVI Cor global-bound | Conditional on (i)–(vi) |
| A₂-stability (vi) for PSWF | Paper XVI Open Problem | **OPEN — target of Paper XVII** |
| `H_SOT = closure(H_spec)` | Paper IX Open Problem 7 | **NOT proved** |
| Subsequence-independence | Paper XI Open Problem 3 | **OPEN** |
| Gap-S | Paper XII Hyp. 3.1 | **OPEN** |
| Lipschitz regularity (amplitude) | Paper XV Prob. 6.1 | **OPEN** |
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

- **Olver (1974):** *Asymptotics and Special Functions* — turning points, Airy, Ch. 11
- **Osipov–Rokhlin–Xiao (2013):** *Prolate Spheroidal Wave Functions of Order Zero*
- **Bonami–Karoui (2014):** Uniform bounds of PSWFs
- **Slepian–Pollak (1961):** Original PSWF paper
- **CCM2025:** Connes–Consani–Moscovici, arXiv:2511.22755
- **Kato (1966):** *Perturbation Theory for Linear Operators*
- **Reed–Simon (1975):** *Methods of Modern Mathematical Physics, Vol. II*
- **Mosco (1969):** Convergence of convex sets
- **Widom (1964):** Asymptotic behavior of eigenvalues II
- **Stein (1993):** *Harmonic Analysis* — van der Corput, Airy bounds
- **Titchmarsh (1986):** *Theory of the Riemann Zeta-Function* — Weyl differencing
- **Zworski (2012):** *Semiclassical Analysis*, AMS
- **Hörmander (1983):** *Analysis of Linear PDE I*, Springer — Ch. 7.7, 18.1–18.2, 25.1
- **Arnold (1972):** Normal forms near degenerate critical points — A₂ classification
- **Golubitsky–Guillemin (1973):** *Stable Mappings and Their Singularities*
- **Guillemin–Uhlmann (1981):** Oscillatory integrals with singular symbols, Duke Math. J. 48
- **Melrose–Uhlmann (1979):** Lagrangian intersection and Cauchy problem, CPAM 32
- **Chester–Friedman–Ursell (1957):** Extension of steepest descents, Proc. Cambridge Philos. Soc. 53
- **Böttcher–Silbermann (1990):** *Analysis of Toeplitz Operators*
- **Simon (2011):** *Szegő's Theorem and Its Descendants*
