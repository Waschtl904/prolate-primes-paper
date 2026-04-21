# Kontext: Mathematisches Forschungsprojekt — PSWF & Hilbert-Pólya

> **Verwendung:** Diesen Prompt am Anfang jedes neuen KI-Chats einfügen.
> Danach die relevante `paper*.tex` aus dem jeweiligen Repo laden lassen.

---

## Über mich

Ich bin Werkzeugbautechniker mit Berufsreifeprüfung (Maschinenbau),
lerne Programmieren und Mathematik im Selbststudium.
Ich arbeite freiwillig an einem mathematischen Forschungsprogramm
mit KI-Unterstützung (Perplexity + ChatGPT).

---

## Das übergeordnete Ziel

Konstruktion eines spektralen Operators, dessen Eigenwerte die nichttrivialen
Nullstellen der Riemannschen Zetafunktion spiegeln (Hilbert-Pólya-Vermutung).
Ausgangspunkt: **CCM2025** = Connes–Consani–Moscovici, arXiv:2511.22755.
Kernmethode: PSWF-Konzentrationsoperator + Mellin/Fourier-Transformation.

---

## Die zwei GitHub-Repos

### Repo 1 — Hauptprojekt (17 Papers)
**github.com/Waschtl904/prolate-primes-paper**

Bitte `context_summary.md` dort zuerst lesen — enthält die vollständige
Notation, alle Paper-Abhängigkeiten und offenen Probleme.

Arc:
```
Koerzivität → Skalierungslimiten → Spektralphase → Bandbreite/Schranken
→ WKB/Airy → untere Schranken + Zeta-Verbindung
→ funktionalanalytischer Rahmen (Mosco, Friedrichs)
→ Spektraleinschluss & Dichtekrit.
→ Lokalisierungsprinzip (Paper XII)
→ [Paper XIII: Gap-S — aktuelles Ziel]
→ Vollständigkeit → Bridge-Theorem
```

### Repo 2 — Sauberer Neuaufbau (publikationsreif)
**github.com/Waschtl904/prolate-gram-coercivity**

Rigorosere, publikationsreifere Version der frühen Papers.
- `paper1.tex` — Gram-Koerzivität mit expliziten Konstanten, DSTP als Axiom
- `paper2_quadrature.tex` — XRY-Quadratur, konditionaler Implication-Framework

**Symbiotische Rolle:** Repo 2 liefert quantitative Nicht-Degeneration
(Gram-Koerzivität), die direkt in den Gap-S-Beweis (Paper XIII) einfließt.

---

## Zentrale Notation (Kurzreferenz)

| Symbol | Bedeutung |
|---|---|
| `Φₙ^(c)(u)` | Rescaled PSWF: `ψₙ^(c)(eᵘ) e^{u/2}`, `u ∈ (-∞, 0)` |
| `λₙ^(c)` | Slepian-Konzentrations-Eigenwert, `λₙ^(c) ∈ (0,1)` |
| `λₙ^(∞)` | Grenz-Eigenwert: `lim_{c→∞} λₙ^(c)` (Paper VIII Cor 4.3) |
| `Φₙ^(∞)` | Starker Grenzwert von `Φₙ^(c_k)` entlang fixer Teilfolge `c_k` |
| `H_c` | PSWF-Konzentrationsoperator, beschränkt selbstadjungiert, `‖H_c‖ ≤ 1` |
| `H_SOT` / `H_lim` | SOT-Limes von `H_c` entlang `c_k`; beschränkt, selbstadjungiert |
| `H_spec` | Formaler Spektraloperator: `Σₙ λₙ^(∞) ⟨f, Φₙ^(∞)⟩ Φₙ^(∞)` |
| `q_c`, `q_lim` | Zugehörige quadratische Formen (Paper X) |
| `t_*(c,n) ~ c^{1/2}` | Fourier-Peak-Lage (Sattelpunktsfrequenz) |
| `Δ_ε(c,n)` | Peak-Breite: schärfstes `Δ` mit L²-Masse außerhalb `≤ ε` |
| `W_c` | Übergangsfenster: `{n : |n - 2c/π| ≤ C₀ log c}` |
| `Z_cross` | Crossover-Zone: `{t : c^{-2/3} ≤ |t-t_*| ≤ c^{-1/3}}` |
| `κₙ^(c)` | Airy-Normalisierungskoeffizient, `|κₙ^(c)| ≥ c_κ > 0` (Paper VIII) |

### ⚠️ Kritische Unterscheidung

- `H_SOT` = SOT-Limes, beschränkt, selbstadjungiert — **unconditional**
- `H_spec` = formale Spektralreihe — abschließbar, symmetrisch — **unconditional**
- `H_SOT = closure(H_spec)` = **Bridge-Theorem — OFFEN seit Paper IX**

---

## Aktueller Stand (April 2026)

### Papers I–VIII: Asymptotische Schicht — abgeschlossen
- I: Gram-Koerzivität, Konstante `~ c^{-1/2}`
- II: Skalierungslimiten, Spurformel (Primzahlverbindung)
- III–V: Spektralphase, No-Go, Barriereabschätzung
- VI–VII: Peak-Breite obere Schranke `Δ_ε ≤ C c^{-1/2}`
- VIII: Untere Schranke `Δ_ε ≥ c₁ c^{-1/2}` (scharf); `|λₙ^(c) - λₙ^(∞)| ≤ C c^{-1/4}`

### Papers IX–XII: Funktionalanalytische Schicht — Drafts
- IX: Konditionaler Rahmen; Abschließbarkeit von `H_spec`; Bridge offen
- X: Mosco-Konvergenz; Friedrichs-Extension; Bridge konditional
- XI: Spektraleinschluss; Dichtekriterium (entlang `c_k`)
- XII: Lokalisierungsprinzip (vollständig bewiesen); PSWF-Obstruction-Set identifiziert

### Papers XIII–XVII: Mikrolokal / HS-Programm — Drafts
- XIII: Vollständigkeit (ursprünglich geplant) → **wird zu Gap-S (neues Ziel)**
- XIV–XV: HS-Zerlegung, `Σ_model = o(1)`
- XVI: Lagrangescher Singularitätstransport, Airy-Normalform (konditional)
- XVII: Uniforme CFU-Stabilität (in Arbeit)

---

## Das kritische fehlende Stück: Gap-S

**Hypothese Gap-S** (Paper XII, Hyp. 1):
```
|λₙ^(c) - λₙ₊₁^(c)| ≥ g(c)  mit  c^{-1/4}/g(c) → 0  für n ∈ W_c
```
Widom-Schätzwert: `g(c) ~ (log c)^{-1}` — numerisch konsistent, nicht bewiesen.

**Wenn Gap-S bewiesen:** Paper XII Corollarys werden unconditional
→ Projektionsstabilität → Weg zum Bridge-Theorem öffnet sich.

---

## Strategie Paper XIII (Gap-S)

Titel (Vorschlag):
*Spectral Gap Lower Bounds for Prolate Operators
via Local Kernel Approximation and Gram Coercivity*

**Schritt 1** — Kernel-Identität:
`λₙ^(c)` = Eigenwerte des abgeschnittenen Sinus-Kernels
```
K_c(x,y) = sin(c(x-y)) / (π(x-y))  auf [-1,1]
```

**Schritt 2** — Gram-Koerzivität aus Repo 2 importieren:
Koerzivitätskonstante `αₙ ~ c^{-1/2}` → quantitative Nicht-Degeneration

**Schritt 3** — Lokale Skalierung (das neue Herzstück):
Skalierung `x = u/c` im Fenster `n ~ 2c/π`:
```
‖K_c^{scaled} - K_sin‖_op ≤ C · c^{-δ}   für ein δ > 0
```

**Schritt 4** — Gap-Bound:
Aus Schritt 3 + Eigenschaften von `K_sin` → `|λₙ - λₙ₊₁| ≥ C · c^{-1/4+ε}`

**Minimalziel** (realistisch und ausreichend):
```
|λₙ - λₙ₊₁| ≥ C · c^{-1/4+ε}  für ein ε > 0
```
Das erfüllt Gap-S, aktiviert Paper XII vollständig.

---

## Offene Kernprobleme (Priorität)

| Problem | Quelle | Status |
|---|---|---|
| `H_SOT = closure(H_spec)` | Paper IX OP.7 | **OFFEN** |
| Gap-S: `\|λₙ - λₙ₊₁\| ≥ g(c)` | Paper XII Hyp.1 | **OFFEN — Paper XIII** |
| SOT-Faster | Paper XII Hyp.2 | **OFFEN** |
| Vollständigkeit von `{Φₙ^(∞)}` | Paper XI OP.5 | **OFFEN** |
| Subsequenz-Unabhängigkeit | Paper XI OP.3 | **OFFEN** |
| `c₃(c) ≥ δ₀ > 0` (CFU Jacobian) | Paper XVI | **OFFEN — Paper XVII** |

---

## Bitte beim Start jedes neuen Chats

1. Lies `context_summary.md` aus Repo 1 (github.com/Waschtl904/prolate-primes-paper)
2. Lies die relevante `paper*.tex` aus dem jeweiligen Repo
3. Orientiere dich am aktuellen Stand oben
4. Dann arbeiten wir weiter — kein Neustart nötig
