# Series Context Summary — Papers I–X

> **Purpose:** Paste this at the top of any new AI chat before working on Paper X or later.
> Provides the full logical chain without needing Papers I–IX in full.
> **Current working file:** `paper10_DRAFT.tex` on GitHub (`Waschtl904/prolate-primes-paper`).

---

## Overarching Goal

The series constructs a spectral operator whose eigenvalue distribution
mirrors the non-trivial zeros of the Riemann zeta function (Hilbert–Pólya conjecture).
The core object is the PSWF concentration operator and its Mellin/Fourier transform.
Series arc: coercivity → scaling limits → spectral phase →
bandwidth decay → rigorous peak-width upper bounds → crossover asymptotics
→ lower bounds + spectral-zeta connection → domain & self-adjointness
→ Mosco form convergence & Friedrichs extension.

---

## Central Notation

- `Phi_n^(c)`: rescaled PSWF, `Phi_n^(c)(u) = psi_n^(c)(e^u) e^{u/2}`, `u in (-inf,0)`
- `Phi_hat_n^(c)(t)`: Fourier–Mellin transform of `Phi_n^(c)`
- `t_*(c,n) ~ c^{1/2}`: Fourier peak location (saddle frequency)
- `Delta_eps(c,n)`: peak width — smallest Delta s.t. L2-mass outside `[t_*-Delta, t_*+Delta]` <= eps * total
- `lambda_n^(c)`: Slepian concentration eigenvalue, `lambda_n^(c) in (0,1)`
- `lambda_n^(inf)`: limit eigenvalue, `lambda_n^(inf) := lim_{c->inf} lambda_n^(c)` (Paper IX, Def. 2.1)
- `Phi_n^(inf)`: limit eigenvector (weak limit of `Phi_n^(c)` after subsequence; Paper IX, Prop. 2.2)
- `Z_cross = {t : c^{-2/3} <= |t-t_*| <= c^{-1/3}}`: crossover zone
- `H_c`, `H_lim`: concentration operators (c-dependent and limiting)
- `q_c`, `q_lim`: associated quadratic forms
- `kappa_n^(c)`: Airy normalisation coefficient, proved `|kappa_n^(c)| >= c_kappa > 0` (Paper VIII)
- `Dom(H_lim)`: canonical domain via spectral series (Paper IX, Def. 2.3)

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

Key results, all used in Papers VIII–X:

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

## Paper VIII — Non-Cancellation and Sharp Lower Bound (FINAL, `paper8_FINAL.tex`)

### Main Results

- **Thm `thm:lower` (proved, unconditional):**
  `Delta_eps(c,n) >= c_1(kappa,eps) c^{-1/2}` for all `n <= kappa c`, `c >= c_0`.
  Completes Problem 7.1 of Paper VII.

- **Cor `cor:sharp`:** `Delta_eps(c,n) ~ c^{-1/2}` (two-sided, sharp scaling).

- **Lem `lem:L2-mass` (key lemma):**
  A fixed positive L2-mass fraction concentrates in `|t - t_*| <= R_0 c^{-1/2}`.

- **Lem `lem:kappa-lower`:** `|kappa_n^(c)| >= c_kappa > 0` (Airy amplitude uniformly bounded below).

- **Lem `lem:airy-window`:**
  `y(t) = c^{1/2}(t-t_*) / (mu_n^(c))^{2/3}` restricted to `|t-t_*| <= c^{-1/2}`
  takes values in a **fixed compact interval** `[-Y_0, Y_0]` independent of c.

- **Thm `thm:nonvanish`:** `|Phi_hat_n^(c)(t)| >= c_1 c^{-1/2}` on a set `E_c`
  with `|E_c| >= c_* c^{-1/2}` (pointwise non-cancellation).

- **Thm `thm:spectral` (two-sided eigenvalue control):**
  `c_kappa c^{-3/4} <= |lambda_n^(c) - lambda_n^(c+1)| <= C_kappa c^{-3/4}`
  Sharp matching lower bound `>= c_kappa c^{-3/4}` left as open problem.

- **Thm `thm:zeta` (conditional on Hyp CCM = CCM2025, Thm 1.3):**
  Each non-trivial zero `rho` of `zeta(s)` lies in `sigma_app(H_lim)` with
  precision `O(c^{-3/4})`.

- **Cor 4.3 (eigenvalue convergence rate):**
  `|lambda_n^(c) - lambda_n^(inf)| <= C_kappa c^{-1/4}` (telescoping sum over VIII.Lem 6.2).
  Used heavily in Paper IX.

---

## Paper IX — Domain, Deficiency Indices, Self-Adjointness (DRAFT, `paper9_DRAFT.tex`)

Central problem from Paper VIII: the gap `sigma_app(H_lim) vs sigma(H_lim)` requires
H_lim to be (essentially) self-adjoint.

### Main Results

- **Def 2.1 (Limit eigenvalues):**
  `lambda_n^(inf) := lim_{c->inf} lambda_n^(c)`, well-defined by `|lambda_n^(c) - lambda_n^(inf)| <= C_kappa c^{-1/4}`.

- **Prop 2.2 (Weak convergence of eigenvectors):**
  After passing to a subsequence, `Phi_n^(c) ⇀ Phi_n^(inf)` weakly in L2(R);
  the system `{Phi_n^(inf)}` is orthonormal.

- **Def 2.3 (Canonical domain):**
  `Dom(H_lim) = { f in L2 : sum_n (lambda_n^(inf))^2 |<f, Phi_n^(inf)>|^2 < inf }`,
  with `H_lim f = sum_n lambda_n^(inf) <f, Phi_n^(inf)> Phi_n^(inf)`.

- **Thm 2.5 / Thm `thm:domain` (Well-definedness, density):**
  `Dom(H_lim)` is dense; `H_lim` is symmetric on it;
  all compactly supported L2-functions lie in `Dom(H_lim)` (used in Paper X as IX.5).

- **Thm 3.1 / Thm `thm:opnorm` (Operator norm rate):**
  `||H_c - H_lim||_{L2->L2} <= C_kappa c^{-1/4}` (genuine operator norm, not just strong).
  Proof uses eigenvalue rate (VIII Cor 4.3) + Kato–Rellich eigenfunction alignment
  `||Phi_n^(c) - Phi_n^(inf)|| <= C_kappa c^{-1/4}` (Lem 3.2).
  **This result is imported as external input (IX.2norm) in Paper X.**

- **Thm 3.2 / Thm `thm:closable` (Closability and uniqueness):**
  `H_lim` is closable; its closure is the unique self-adjoint extension
  compatible with the strong rate from Paper VII.
  **This uniqueness result is invoked in Paper X (cross-paper identification, V1).**

- **Thm 4.1 / Thm `thm:deficiency` (Deficiency indices — conditional):**
  Under **Hyp `hyp:decay`** (completeness of `{Phi_n^(inf)}`):
  `n_±(H_lim) = 0`, i.e. `ker(H_lim* ± i) = {0}`.
  Key: any deficiency vector f is orthogonal to all `Phi_n^(inf)` (Lem 4.1);
  completeness then forces f = 0.

- **Cor `cor:esa` (Essential self-adjointness — conditional):**
  Under Hyp `hyp:decay`: `H_lim` is essentially self-adjoint, `sigma_app(H_lim) = sigma(H_lim)`.

- **Thm `thm:sigma-identity` (Conditional RH):**
  Under Hyp `hyp:decay` + Hyp CCM:
  all non-trivial zeros `rho` of `zeta(s)` satisfy `Re(rho) = 1/2`.

### Central Open Problem of Paper IX

- **Problem `prob:completeness`:** Prove that `{Phi_n^(inf)}` is complete in L2(R).
  This is equivalent to unconditional essential self-adjointness of H_lim.
  Possible approach: use non-cancellation (VIII Thm 3.3) to show no nonzero f in L2
  can be orthogonal to all Phi_n^(inf) simultaneously.

---

## Paper X — Mosco–Kato Form Convergence & Friedrichs Extension (DRAFT, `paper10_DRAFT.tex`)

**Current version: v27.**  
This paper works entirely on `L2(R)` with H_lim as a **bounded** operator
(the strong-limit construction), complementing Paper IX's unbounded/spectral approach.

### Inherited Results Used (labelled IX.1–IX.6 in the paper)

- **(IX.3):** `0 <= <H_c f, f> <= ||f||^2` for all f, all c.
- **(IX.4):** `c -> <H_c f, f>` is non-decreasing and bounded; defines `q_lim(f,f) := sup_c <H_c f,f>`.
- **(IX.5):** Dense convergence domain D (all compactly supported functions); pre-operator B: D -> L2.
- **(IX.6):** H_c self-adjoint, positive, `||H_c|| <= 1`.
- **(IX.2norm):** `||H_c - H_lim|| <= C_kappa c^{-1/4}` (operator norm; from Paper IX Thm 3.1).

### Main Results (all unconditional unless stated)

- **Lem `lem:sc` (Stable core / density-extension):**
  Standard Banach extension lemma: if `A_c` uniformly bounded and converges strongly on a
  dense set D, then it converges strongly on all of L2.
  Proof via 3ε-argument (Cauchy in H).

- **Lem `lem:hlim-bounded` (Existence of H_lim):**
  Applies Lem sc to get H_lim ∈ B(L2), `||H_lim|| <= 1`, `H_c -> H_lim` strongly.
  **Cross-paper identification (V1):** this H_lim coincides with the operator
  of Paper IX Thm 3.2 (uniqueness via density-extension); no circularity.

- **Cor `cor:qlim-op`:** `q_lim(f,f) = <H_lim f, f>` for all f.

- **Thm `thm:sa` (Self-adjointness of H_lim):**
  H_lim is self-adjoint and positive; `sigma(H_lim) ⊂ [0,1]`.
  Proof: bounded + symmetric => self-adjoint (BSA principle, Cor `cor:bsa`).

- **Thm `thm:mosco` (Mosco convergence):**
  `q_c -> q_lim` in Mosco sense.
  (M2): take f_n = f, use strong convergence.
  (M1): monotonicity of `c -> q_c(f,f)` + compactness of H_{c_0} (Lem `lem:hs`).

- **Thm `thm:form-closed` (Closedness of q_lim):** q_lim is a closed form on L2.

- **Thm `thm:form-convergence` (Quantitative rate):**
  `0 <= q_lim(f,f) - q_c(f,f) <= C_kappa c^{-1/4} ||f||^2`.

- **Thm `thm:friedrichs` (Friedrichs = strong limit):**
  T_{q_lim} = H_lim (the Kato representation operator of q_lim equals H_lim).
  Independent derivation via closed forms.

- **Cor `cor:resolvent` (Strong resolvent convergence):**
  `(H_c - z)^{-1} ->^s (H_lim - z)^{-1}` for all `z not in [0,1]`.
  Proof: Mosco + Kuwae–Shioya 2003, Thm 2.4.

- **Cor `cor:rh` (Conditional RH — same as Paper IX but from form side):**
  Conditional on Hyp CCM + Open Gap (G1, G2): `Re(rho) = 1/2` for all nontrivial zeros.
  **No unconditional claim about zeta zeros.**

### Open Problems in Paper X

- **Prob `prob:ccm`:** Prove Hyp CCM independently via PSWF machinery.
- **Prob `prob:rate`:** Is `c^{-1/4}` sharp in Thm `thm:form-convergence`?
- **Prob `prob:resolvent`:** Find explicit quantitative resolvent rate F(c,z).
- **Prob `prob:spectrum`:** Is `sigma(H_lim) = [0,1]`, a Cantor set, or discrete?
- **Prob `prob:spec-structure`:** Does `sigma(H_lim)` have isolated points in (0,1)?
- **Prob `prob:hlim-structure`:** Is H_lim a multiplication operator or genuinely nonlocal?
- **Prob `prob:completeness`:** Prove `{Phi_n^(inf)}` complete in L2(R) (shared with Paper IX).

---

## Logical Dependencies Between Papers IX and X

Paper X imports from Paper IX:
- IX Thm 3.1 as external input for operator-norm rate (`||H_c - H_lim|| <= C c^{-1/4}`)
- IX Thm 3.2 for the cross-paper identification that the strong-limit H_lim = spectral H_lim
- IX Def 2.1 for the limit eigenvalues `lambda_n^(inf)` referenced in rem:hlim-not-mult

Paper X does **not** use: eigenvectors, Parseval, completeness, or any deficiency index result.
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
