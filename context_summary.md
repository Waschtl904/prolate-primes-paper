# Series Context Summary — Papers I–XI

> **Purpose:** Paste this at the top of any new AI chat before working on Paper IX or later.
> Provides the full logical chain without needing Papers I–VIII in full.
> **Current working file:** `paper9_DRAFT.tex` on GitHub (`Waschtl904/prolate-primes-paper`).
> **Last updated:** after Paper IX + Paper X referee patches (April 2026).

---

## Overarching Goal

The series constructs a spectral operator whose eigenvalue distribution
mirrors the non-trivial zeros of the Riemann zeta function (Hilbert–Pólya conjecture).
The core object is the PSWF concentration operator and its Mellin/Fourier transform.
Series arc: coercivity → scaling limits → spectral phase →
bandwidth decay → rigorous peak-width upper bounds → crossover asymptotics
→ lower bounds + spectral-zeta connection → domain & self-adjointness (conditional framework)
→ Mosco form convergence & Friedrichs extension → spectral identification (open).

---

## Central Notation

- `Phi_n^(c)`: rescaled PSWF, `Phi_n^(c)(u) = psi_n^(c)(e^u) e^{u/2}`, `u in (-inf,0)`
- `Phi_hat_n^(c)(t)`: Fourier–Mellin transform of `Phi_n^(c)`
- `t_*(c,n) ~ c^{1/2}`: Fourier peak location (saddle frequency)
- `Delta_eps(c,n)`: peak width — smallest Delta s.t. L2-mass outside `[t_*-Delta, t_*+Delta]` <= eps * total
- `lambda_n^(c)`: Slepian concentration eigenvalue, `lambda_n^(c) in (0,1)`
- `lambda_n^(inf)`: limit eigenvalue, `lambda_n^(inf) := lim_{c->inf} lambda_n^(c)` (Paper IX, inherited from VIII Cor 4.3)
- `Phi_n^(inf)`: subsequential weak limit of `Phi_n^(c)` in L2; ONS property holds (Paper IX, Lem 3.1)
- `Z_cross = {t : c^{-2/3} <= |t-t_*| <= c^{-1/3}}`: crossover zone
- `H_c` (`\Hc`): finite-c PSWF concentration operator, bounded self-adjoint, `||H_c|| <= 1`
- `H_SOT` (`\HSOT`): SOT-limit of H_c; bounded self-adjoint, `||H_SOT|| <= 1`; exists unconditionally (Paper X Lem 2.2)
- `H_spec` (`\Hspec`): spectral operator defined by series `sum_n lambda_n^(inf) <f, Phi_n^(inf)> Phi_n^(inf)`; closable, symmetric; **NOT identified with H_SOT** (open problem)
- `q_c`, `q_lim`: associated quadratic forms (Paper X)
- `kappa_n^(c)`: Airy normalisation coefficient, proved `|kappa_n^(c)| >= c_kappa > 0` (Paper VIII)
- `Dom(H_spec)`: canonical domain via spectral series (Paper IX, Def 3.1)

### ⚠️ Critical distinction (established after Paper IX referee process)

`H_SOT` and `H_spec` are **two separate objects**:
- `H_SOT` = SOT-limit, bounded, self-adjoint, defined via Paper X Thread A — **unconditional**
- `H_spec` = formal spectral series operator — **closable and symmetric, unconditional**
- The identification `H_SOT = closure(H_spec)` is **Paper IX Open Problem 7 / Paper X Hyp.(IX.b)** — **not proved anywhere in the series**

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
- **Cor 4.3:** `|lambda_n^(c) - lambda_n^(inf)| <= C_kappa c^{-1/4}` — used in Paper IX
- **Thm `thm:zeta` (conditional on Hyp CCM):** each zeta zero `rho` lies in `sigma_app(H_lim)` with precision `O(c^{-3/4})`

---

## Paper IX — Conditional Framework: Domain, Closability, Self-Adjointness (DRAFT)

**Architecture:** This is a **conditional framework paper**, NOT a norm-convergence paper.
All strong results are labelled unconditional/conditional explicitly.

### Unconditional Results

- **Lem 3.1 (PSWF precompactness):** `{Phi_n^(c)}` precompact in L2 (Fréchet–Kolmogorov);
  every subsequence has a further subsequence converging strongly to a unit vector.
- **Lem 3.2 (Rank-1):** finite-c Slepian projection structure; no uniformity in c claimed.
- **Thm 3.3 (Closability + symmetry of H_spec):** H_spec is closable and symmetric.
  Proof uses unitary isometry `U: L2 -> ell^2`, `Uf = (<f, Phi_n^(inf)>)_n`,
  plus dominated convergence in ell^2 with Bessel majorant.
- **Rem 1.3 (H_SOT bounded self-adjoint):** SOT-limit of uniformly bounded self-adjoint operators
  is bounded self-adjoint (Reed–Simon II, Problem II.3); `Dom(H_SOT) = L2`, `||H_SOT|| <= 1`.

### Hypotheses (none proved in Paper IX)

- **Hyp 1 (Discrete spectrum of H_SOT):** H_SOT has purely discrete spectrum with simple
  eigenvalues `lambda_0^(inf) > lambda_1^(inf) > ... > 0` and eigenvectors `{Phi_n^(inf)}`.
  Called "spectral decomposition instability under SOT convergence" — the central black box.
- **Hyp 2 (Norm-resolvent convergence):** `||(H_c - z)^{-1} - (H_SOT - z)^{-1}|| -> 0`.
  SOT convergence does NOT imply this (Reed–Simon Ex. VIII.7.14).
- **Hyp 3 (Completeness):** `{Phi_n^(inf)}` complete in L2(R).
- **Hyp 4 (Uniform alignment):** `sup_{n <= kappa c} ||Phi_n^(c) - Phi_n^(inf)|| <= C_kappa c^{-1/4}`.

### Conditional Results

- **Thm 4.1 (Full norm convergence) [Hyp 1 + Hyp 2]:**
  `||Phi_n^(c) - Phi_n^(inf)|| -> 0` via Kato VIII.1.8 + projection-norm argument.
- **Lem 5.1 (H_SOT eigenrelation) [Thm 4.1]:**
  `H_SOT Phi_n^(inf) = lambda_n^(inf) Phi_n^(inf)`.
  Proof: decompose via (P1) with `||Phi_n^(c)|| = 1`; remainder `r_c -> 0` by VII Thm C.
- **Thm 6.1 (Completeness => ESSA) [Thm 4.1 + Hyp 3]:**
  If `{Phi_n^(inf)}` complete then H_spec essentially self-adjoint. ONE DIRECTION ONLY;
  converse (ESSA => completeness) is open (Open Problem 6).
- **Thm 7.1 (Partial spectral truncation estimate) [Hyp 4]:**
  `||H_c - H_spec|| <= C_kappa c^{-1/4}`.
  ⚠️ This is a PARTIAL estimate for `n <= kappa c` only.
  Does NOT imply `||H_c - H_SOT|| -> 0` in B(L2) (tail + Riesz-basis gap missing).
  **NOT imported by Paper X.** Paper X derives its rate externally from Paper VIII.

### Open Problems in Paper IX

1. Norm-resolvent convergence (Hyp 2)
2. Discrete spectrum of H_SOT (Hyp 1) — central black box
3. Completeness of `{Phi_n^(inf)}` (Hyp 3)
4. Uniform alignment (Hyp 4)
5. Riesz-basis property of `{Phi_n^(inf)}` — would close tail+frame gap
6. Converse ESSA (requires explicit `Dom(H_spec*)`)
7. **Operator identification: `closure(H_spec) = H_SOT`** — THE central open problem of the series

---

## Paper X — Mosco Form Convergence & Friedrichs Extension (DRAFT, v46)

**Architecture:** Works entirely with H_SOT as a **bounded** operator.
All main results are **unconditional** except the Bridge theorem.

### Unconditional Results

- **Lem `lem:ftb` (Coordinatisation):** `<H_c f, f> = ||B_c(P*Pf)||^2`; all results follow from this + monotonicity.
- **Thread A:** SOT-limit `H_str` exists uniquely in B(L2), `||H_str|| <= 1` (3ε-Cauchy argument on dense domain).
- **Thread B:** Mosco convergence `q_c ->^M q_lim` (monotonicity + HS-compactness of H_{c_0}).
- **Thm `thm:friedrichs`:** `q_lim` closed; `T_{q_lim} = H_str` (Riesz–Kato identification).
- **Cor `cor:resolvent`:** Strong resolvent convergence `(H_c - z)^{-1} ->^s (H_lim - z)^{-1}` for `z not in [0,1]`.
- **Thm `thm:rate-ext` (rate, external):** `0 <= q_lim(f,f) - q_c(f,f) <= C_kappa c^{-1/4} ||f||^2` — imported from **Paper VIII Cor 4.3 only**; no Paper IX dependency.

### Conditional Result

- **Thm `thm:bridge` (Bridge theorem) [Hyp (IX.b)]:**
  `H_str = closure(H_spec)`.
  Proof: both are SOT-limits of the same net `(H_c)` in a Hausdorff space; hence equal by uniqueness.
  ⚠️ **Conditional on Hyp.(IX.b):** the identification `H_SOT = closure(H_spec)` is
  **Paper IX Open Problem 7** and is NOT proved in Paper IX.
  The existence of the SOT-limit is unconditional; the identification is the hypothesis.

### Logical Structure of Paper X

```
FTB (coordinatisation lemma)
 ├── Thread A: SOT-limit H_str  ─────────────────────── UNCONDITIONAL
 ├── Thread B: Mosco q_c ->^M q_lim ─────────────────── UNCONDITIONAL
 ├── Friedrichs: T_{q_lim} = H_str ──────────────────── UNCONDITIONAL
 ├── Resolvent convergence ───────────────────────────── UNCONDITIONAL
 ├── Rate O(c^{-1/4}) [Paper VIII external] ──────────── UNCONDITIONAL
 └── Bridge: H_str = closure(H_spec) [Hyp.(IX.b)] ───── CONDITIONAL
```

### Open Problems in Paper X

1. **Identification** `H_SOT = closure(H_spec)` [= Paper IX Open Problem 7] — central
2. Rate sharpness: is `c^{-1/4}` sharp?
3. Quantitative resolvent rate F(c,z)
4. Is `sigma(H_lim) = [0,1]`?
5. Completeness of `{Phi_n^(inf)}` (shared with Paper IX)

---

## The Central Open Problem of the Series

After Papers I–X, the entire programme reduces to **one structural identification**:

```
H_SOT  =?=  closure(H_spec)
```

All other results are either:
- **proved unconditionally** (Mosco, SOT-limit, Friedrichs, closability, symmetry, precompactness), or
- **correctly conditional** on this identification or on completeness/norm-resolvent.

The three best-known approaches to the identification problem:
- **(A) Compactness of H_SOT:** if H_SOT compact, spectral stability nearly free — but compactness not established.
- **(B) Riesz-basis approach (recommended):** prove `{Phi_n^(inf)}` is a Riesz basis in L2;
  this would simultaneously close: operator-norm control, resolvent, completeness, ESSA.
  Starting point: Paper VIII `thm:nonvanish` (pointwise non-cancellation lower bound).
- **(C) Semiclassical / microlocal:** asymptotic integral-operator theory in the Slepian regime;
  very powerful but technically at Paper VI–VII+ level.

---

## Correct Logical Dependencies Between Papers IX and X

| What Paper X uses | Source | Status |
|---|---|---|
| Rate `||q_lim - q_c|| <= C c^{-1/4}` | Paper VIII Cor 4.3 | Unconditional import |
| `H_spec` closable, symmetric, `||H_spec f|| <= ||f||` | Paper IX Thm 3.3 + Rem 1.3 | Unconditional |
| `H_SOT = closure(H_spec)` — Bridge hypothesis | Paper IX **Open Problem 7** | **Structural hypothesis, NOT proved** |

Paper X does **not** use: eigenvectors, Parseval on limit basis, completeness, deficiency indices,
or any operator-norm rate from Paper IX.
Paper IX does **not** use: Mosco convergence, Friedrichs extension, or form closedness.

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
- **Rudin (1991):** *Functional Analysis*, 2nd ed., McGraw-Hill
- **Conway (1990):** *A Course in Functional Analysis*, 2nd ed., Springer
