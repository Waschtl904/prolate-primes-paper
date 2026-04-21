# Series Context Summary — Papers I–XVII

> **Purpose:** Paste this at the top of any new AI chat before working on any paper.
> **Last updated:** April 2026, after Paper XII final + Paper XIII draft (completeness classification).
> **Repo:** `Waschtl904/prolate-primes-paper`

---

## ⚠️ How to read this summary

Labels used throughout:
- ✅ **UNCONDITIONAL** — would survive peer review as stated
- ⚠️ **CONDITIONAL** — proved, but under a named hypothesis
- 🔶 **DRAFT** — written, but not yet publication-ready
- ❌ **OPEN** — not proved anywhere in the series
- ~~FINAL~~ — this label is **retired**: it meant "we stopped working on it", not "peer-review ready"

---

## Overarching Goal

Construct a spectral operator whose eigenvalue distribution mirrors the
non-trivial zeros of the Riemann zeta function (Hilbert–Pólya conjecture).
Core object: PSWF concentration operator `H_c` and its Mellin/Fourier transform.
Reference: **CCM2025** = Connes–Consani–Moscovici, arXiv:2511.22755.

Series arc:
```
Coercivity → Scaling limits → Spectral phase → Bandwidth bounds
→ WKB/Airy → Lower bounds + zeta connection
→ Functional-analytic framework (Mosco, Friedrichs)
→ Spectral inclusion & density criterion
→ Localization principle (Paper XII)
→ [Paper 13b: Gap-S — CURRENT TARGET]
→ [Paper 13a: Completeness classification]
→ HS-norm estimates (Papers XIV–XV)
→ Microlocal Lagrangian / Airy normal form (Papers XVI–XVII)
```

---

## Central Notation

| Symbol | Meaning |
|---|---|
| `Phi_n^(c)(u)` | Rescaled PSWF: `psi_n^(c)(e^u) e^{u/2}`, `u ∈ (-∞,0)` |
| `Phi_hat_n^(c)(t)` | Fourier–Mellin transform of `Phi_n^(c)` |
| `t_*(c,n) ~ c^{1/2}` | Fourier peak location (saddle frequency) |
| `Delta_eps(c,n)` | Peak width: smallest Delta with L2-mass outside peak ≤ eps |
| `lambda_n^(c)` | Slepian concentration eigenvalue, `∈ (0,1)` |
| `lambda_n^(inf)` | Limit eigenvalue along fixed subsequence `c_k` (Paper VIII Cor 4.3) |
| `Phi_n^(inf)` | Strong limit of `Phi_n^(c_k)` along fixed diagonal subsequence `c_k` |
| `Z_cross` | Crossover zone: `{t : c^{-2/3} ≤ |t-t_*| ≤ c^{-1/3}}` |
| `H_c` | PSWF concentration operator, bounded self-adjoint, `‖H_c‖ ≤ 1` |
| `H_SOT` / `H_lim` | SOT-limit of `H_c` along `c_k`; bounded self-adjoint — ✅ UNCONDITIONAL |
| `H_spec` | Formal spectral series `Σ_n lambda_n^(inf) ⟨f,Phi_n^(inf)⟩ Phi_n^(inf)` |
| `q_c`, `q_lim` | Associated quadratic forms (Paper X) |
| `kappa_n^(c)` | Airy normalisation coefficient, `|kappa_n^(c)| ≥ c_kappa > 0` (Paper VIII) |
| `W_c` | Transition window: `{n : |n - 2c/π| ≤ C_0 log c}` |
| `K` | Closed span: `K := closure(span{Phi_n^(inf)})` |

### ⚠️ Critical distinction

| Object | Status |
|---|---|
| `H_SOT` = SOT-limit, bounded, self-adjoint, `Dom = L²` | ✅ UNCONDITIONAL |
| `H_spec` = formal spectral series, closable, symmetric | ✅ UNCONDITIONAL |
| `H_SOT = closure(H_spec)` = **Bridge Theorem** | ❌ OPEN — Paper IX OP.7, Paper X |

### ⚠️ Riesz-basis status

`{Phi_n^(inf)}` is an ONS (orthonormal system) along `c_k`.
It is trivially a Riesz basis **with bounds (1,1)** — this is NOT a result,
it is just a restatement of orthonormality (Paper XII Cor. 7.1).
It does **not** imply completeness, does not resolve the Bridge Theorem.

### ⚠️ ALL Paper XI results hold only along the fixed subsequence `c_k`

Subsequence-independence is ❌ OPEN (Paper XI, Open Problem 3).

---

## Papers I–VIII — Asymptotic Layer

### Paper I — Gram Coercivity
- ✅ Gram matrix `G^(N)_{p,c}` coercive with constant `~ c^{-1/2}`
- 🔶 Being rewritten more rigorously in **Repo 2** (`prolate-gram-coercivity`, paper1.tex)

### Paper II — Scaling Limits
- ✅ Trace formula linking eigenvalues to primes (conditional on Hyp. CCM)
- 🔶 Sauberer Neuaufbau teilweise in Repo 2

### Papers III–V — Spectral Phase, No-Go, Barrier
- ✅ No-go for naive bandlimited constructions
- ✅ `|Phi_hat_n^(c)(t)| ≪ e^{-γ c^{1/2}}` for `t ≫ t_*`
- 🔶 These papers have not been independently verified

### Paper VI — Rigorous Upper Bounds
- ✅ Pointwise decay: `|Phi_hat_n^(c)(t)| ≤ C_κ c^{-1/4} t^{-1/4}`
- ✅ Peak-width upper bound: `Delta_eps ≤ C(κ,eps) c^{-1/2}` (improved by Paper VII)
- ✅ Airy profile near `t_*`
- ✅ L2 normalisation: `‖Phi_hat_n^(c)‖² = 1/2`

### Paper VII — Composite Asymptotics in Z_cross
- ✅ **(Thm B)** `Delta_eps(c,n) ≤ C(κ,eps) c^{-1/2}` — sharp upper bound
- ✅ **(Lem 6.2)** `|lambda_n^(c) - lambda_n^(c+1)| ≤ C_κ c^{-3/4}`
- ⚠️ **(Thm C)** `‖(H_c - H_SOT)f‖ ≤ C_κ c^{-3/4} ‖f‖` for fixed unit f
  — **pointwise in f only, NOT operator norm** — this distinction is critical
- ✅ Composite Airy–WKB expansion in Z_cross

### Paper VIII — Non-Cancellation and Sharp Lower Bound
- ✅ `Delta_eps(c,n) ≥ c_1(κ,eps) c^{-1/2}` — unconditional lower bound
- ✅ `Delta_eps ~ c^{-1/2}` sharp two-sided
- ✅ `|kappa_n^(c)| ≥ c_kappa > 0`
- ✅ **(Cor 4.3 — critical import used everywhere):** `|lambda_n^(c) - lambda_n^(inf)| ≤ C_κ c^{-1/4}`
- ⚠️ **(Thm zeta)** each zeta zero `ρ` lies in `sigma_app(H_lim)` — **conditional on Hyp. CCM**

---

## Papers IX–XII — Functional-Analytic Layer

### Paper IX — Conditional Framework (🔶 DRAFT)
- ✅ `{Phi_n^(c)}` precompact in L² (Lem 3.1)
- ✅ `‖Phi_n^(inf)‖ = 1` (Prop 2.2)
- ✅ `H_spec` closable and symmetric (Thm 3.3)
- ❌ **Open Problem 7: `closure(H_spec) = H_SOT`** — THE central open problem

### Paper X — Mosco Form Convergence & Friedrichs Extension (🔶 DRAFT)
- ✅ SOT-limit `H_str` exists uniquely in B(L²)
- ✅ Mosco convergence `q_c →^M q_lim`
- ✅ `T_{q_lim} = H_str` (Friedrichs)
- ✅ Strong resolvent convergence `(H_c - z)^{-1} →^s (H_lim - z)^{-1}`
- ✅ `0 ≤ q_lim - q_c ≤ C_κ c^{-1/4} ‖f‖²`
- ⚠️ **Bridge Thm: `H_str = closure(H_spec)`** — conditional on Hyp.(IX.b) — ❌ Hyp.(IX.b) unproved

### Paper XI — Spectral Structure and Density (🔶 DRAFT, not FINAL)
All results hold **only along fixed diagonal subsequence c_k**.
- ✅ `{Phi_n^(inf)}` is ONS (Lem diagonal)
- ✅ `H_lim Phi_n^(inf) = lambda_n^(inf) Phi_n^(inf)` (Lem eigenvalue-eq)
- ✅ `closure({lambda_n^(inf)}) ⊂ sigma_p(H_lim) ⊂ sigma(H_lim) ⊂ [0,1]`
- ✅ Density criterion: density of `{lambda_n^(inf)}` in [0,1] ⟹ `sigma(H_lim) = [0,1]`
- ❌ Density of `{lambda_n^(inf)}` — OPEN
- ❌ Subsequence-independence — OPEN
- ❌ Completeness of `{Phi_n^(inf)}` — OPEN

### Paper XII — Localization Principle (🔶 DRAFT, fully proved abstract part)
- ✅ **Exact Mechanism Factorization (Thm mechanism)** — fully proved abstract result
- ✅ `R_k → 0 ⟹ ‖P_k - P^inf‖ → 0`
- ✅ No-Go: bypassing gap condition is provably impossible
- ✅ Separation example: `‖A_k - A‖ ≡ 1` but full projection stability
- ⚠️ **Cor (projection convergence)** — conditional on Gap-S + SOT-Faster
- ❌ **Gap-S (Hyp. XII.1):** `|lambda_n^(c) - lambda_{n+1}^(c)| ≥ g(c)` with `c^{-1/4}/g(c) → 0` — OPEN
- ❌ **SOT-Faster (Hyp. XII.2):** `‖(H_{c_k} - H_lim) Phi_n^(inf)‖ = o(g(c_k))` — OPEN

---

## Papers XIII — Completeness Layer

### Paper 13a — Completeness Classification (🔶 DRAFT)
*"Completeness of the Limiting Slepian Eigenbasis: A Classification of Stability Mechanisms"*

This is a **barrier and classification paper**, not a progress paper.
It does NOT prove completeness. It proves:
- ✅ Route A (Thm): Parseval identity ⟺ completeness — frames cannot prove completeness
- ✅ Route B (Thm): `K = L²` ⟺ `PW_{c_0}² ⊆ K` for all `c_0 > 0` (localisation equivalence)
- ⚠️ Route C (Prop): compact resolvent ⟹ completeness — conditional on Hyp. compact-resolvent
- ❌ Completeness itself — OPEN
- ❌ Local spanning `PW_{c_0}² ⊆ K` for any fixed `c_0` — OPEN
- ❌ Coefficient norm convergence H1 — OPEN (most accessible next step)

### Paper 13b — Gap-S via Kernel Approximation (❌ NOT YET WRITTEN)
*"Spectral Gap Lower Bounds for Prolate Operators via Local Kernel Approximation and Gram Coercivity"*

**This is the current active target.**

Goal: prove Gap-S with at minimum `g(c) ≫ c^{-1/4}`.
Strategy:
1. Kernel identity: `lambda_n^(c)` = eigenvalues of `K_c(x,y) = sin(c(x-y))/(π(x-y))` on `[-1,1]`
2. Import Gram coercivity `α_N ~ c^{-1/2}` from Repo 2 (paper1.tex)
3. Local rescaling `x = u/c` in window `n ~ 2c/π`: show `‖K_c^scaled - K_sin‖_op ≤ C·c^{-δ}`
4. Gap bound as consequence

Minimal target (sufficient for Gap-S): `|lambda_n - lambda_{n+1}| ≥ C·c^{-1/4+ε}` for some `ε > 0`

---

## Papers XIV–XV — HS-Norm Estimates (🔶 DRAFT)

### Paper XIV
- HS decomposition: `‖A_N^(c,(M)) - D^(M)‖_HS² = Σ_near + Σ_int + Σ_far`
- ✅ `Σ_near = O(1/c)` (conditional on (C))
- ✅ `Σ_far = o(1)` via stationary phase
- ❌ `Σ_int = o(1)` — OPEN (target of Paper XV)

### Paper XV — Intermediate-Regime Kernel Estimates
- ✅ WKB phase extraction (Lem 4.1)
- ✅ Phase non-degeneracy: `theta''(0)=0`, `theta'''(0)≠0` (cubic, Airy-type)
- ✅ **Cor 5.3: `Sigma_model(c) = o(1)`** — unconditional (given theta non-deg.)
- ❌ **Prob 6.1:** Lipschitz regularity of PSWF amplitude — OPEN (critical)
- ❌ **Prob 7.1:** Local Weyl law (C) — OPEN (critical)

---

## Papers XVI–XVII — Microlocal Layer (🔶 DRAFT)

### Paper XVI — Lagrangian Singularity Transport / Airy Normal Form
All main results conditional on **Assumption 4.1 (uniform A₂-stability)**, especially condition (vi).
- ✅ `|Phi(u;c)| = O(|u|^{-1/2})` — endpoint decay, unconditional
- ⚠️ Airy normal form microlocally — conditional on (i)–(vi)
- ⚠️ `|Phi(u;c)| ≤ C(1+|u|)^{-3/4}` — conditional
- ❌ **Open Problem (prob:PSWF-microlocal):** verify A₂-stability for PSWF uniformly in c
  — primary target of Paper XVII

### Paper XVII — Uniform CFU Stability (❌ IN PROGRESS)
Primary target: verify Assumption 4.1(vi) for PSWF — `|det(dt/dβ)| ≥ δ₅ > 0` uniformly in c.

---

## Central Open Problems (Priority Order)

| Problem | Source | Status |
|---|---|---|
| `H_SOT = closure(H_spec)` (Bridge) | Paper IX OP.7 | ❌ OPEN — central |
| **Gap-S:** `\|lambda_n - lambda_{n+1}\| ≥ g(c)` | Paper XII Hyp.1 | ❌ OPEN — **Paper 13b** |
| SOT-Faster | Paper XII Hyp.2 | ❌ OPEN |
| Completeness of `{Phi_n^(inf)}` | Paper XIII OP | ❌ OPEN |
| Coefficient norm convergence H1 | Paper XIII OP.1 | ❌ OPEN (most accessible) |
| Subsequence-independence | Paper XI OP.3 | ❌ OPEN |
| Lipschitz regularity (amplitude) | Paper XV Prob.6.1 | ❌ OPEN (critical) |
| Local Weyl law (C) | Paper XV Prob.7.1 | ❌ OPEN (critical) |
| A₂-stability (vi) for PSWF | Paper XVI OP | ❌ OPEN — Paper XVII |

---

## Logical Dependencies (what later papers actually use)

| Claim | Source | Status |
|---|---|---|
| `\|lambda_n^(c) - lambda_n^(inf)\| ≤ C c^{-1/4}` | Paper VIII Cor 4.3 | ✅ |
| `‖Phi_n^(inf)‖ = 1` | Paper IX Prop 2.2 | ✅ |
| SOT-limit `H_lim` exists | Paper X | ✅ |
| `H_lim Phi_n^(inf) = lambda_n^(inf) Phi_n^(inf)` | Paper XI | ✅ (along c_k) |
| Spectral inclusion | Paper XI | ✅ (along c_k) |
| Localization principle (abstract) | Paper XII Thm mechanism | ✅ |
| `theta'''(0) ≠ 0` (cubic non-deg.) | Paper XV Lem 4.2 | ✅ |
| `Sigma_model = o(1)` | Paper XV Cor 5.3 | ✅ |
| Airy normal form | Paper XVI | ⚠️ conditional (i)–(vi) |
| Bridge Theorem | Paper IX OP.7 | ❌ NOT PROVED |
| Gap-S | Paper XII Hyp.1 | ❌ NOT PROVED |
| Completeness | Paper XIII | ❌ NOT PROVED |

---

## Zone Structure (Paper VII, corrected)

| Zone | Range of `\|t-t_*\|` | `\|Phi_hat\|` | L2-mass |
|---|---|---|---|
| Airy peak | `≤ c^{-2/3}` | `~ c^{-1/2}` | `~ c^{-5/3}` |
| Crossover Z_cross | `c^{-2/3}` to `c^{-1/3}` | `~ c^{-1/2} |t-t_*|^{-1/4}` | `~ c^{-17/12}` |
| Algebraic | `≥ c^{-1/3}` | `≤ C_κ c^{-1/4} t^{-1/4}` | `~ 1/2` (bulk) |
| Above peak | `t ≫ t_*` | `≤ e^{-γ c^{1/2}}` | negligible |

---

## Key References

- Slepian–Pollak (1961), Osipov–Rokhlin–Xiao (2013) — PSWF foundations
- CCM2025: Connes–Consani–Moscovici, arXiv:2511.22755
- Kato (1966), Reed–Simon (1975) — operator theory
- Mosco (1969) — form convergence
- Widom (1964) — eigenvalue asymptotics
- Olver (1974) — Airy, turning points
- Hörmander (1983) Ch. 7.7, 18.1–18.2, 25.1 — microlocal
- Arnold (1972), Golubitsky–Guillemin (1973) — A₂ singularities
- Chester–Friedman–Ursell (1957) — CFU steepest descent
- Guillemin–Uhlmann (1981), Melrose–Uhlmann (1979) — FIO/conormal
- Zworski (2012) — semiclassical analysis
