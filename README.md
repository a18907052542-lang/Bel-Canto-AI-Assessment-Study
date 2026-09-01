# Bel Canto AI Assessment Study

**The Influence of Cultural Origins and Transparency of AI Evaluation Criteria in Bel Canto Education on Cross-Cultural Identity Construction among Chinese Learners: The Mediating Role of Algorithmic Authority Internalization**

This repository contains the complete research materials, dataset, and analysis pipeline for a longitudinal quasi-experimental study examining how the cultural framing and transparency of AI-supported vocal assessment shape the cross-cultural identity construction of bel canto learners in Chinese conservatories and schools of music.

---

## Study at a glance

- **Design.** Longitudinal quasi-experiment (four waves across one semester) combined with an explanatory sequential mixed-methods design (quan → QUAL).
- **Sample.** 358 undergraduate and amateur bel canto learners from five conservatories and schools of music at comprehensive universities in Eastern and Central China (Condition A: 176; Condition B: 182; overall attrition = 18.6%).
- **Manipulation.** Two parallel AI vocal assessment interfaces — Condition A (transparent standard source + multiple reference systems) versus Condition B (opaque standard source + standard attainment score only) — with identical underlying acoustic engine, repertoire, tasks, and scoring frequency.
- **Key construct.** Algorithmic Authority Internalization (AAI), a four-factor construct operationalized for the first time in this study, measured across four waves with strong reliability, validity, and longitudinal measurement invariance.
- **Central analysis.** A moderated longitudinal mediation model nested within a latent growth model, in which the AAI slope mediates the causal effect of assessment condition on the identity-strategy slope, moderated by prior cultural identification strength.

---

## Hypotheses and results

| # | Hypothesis | Result |
|---|-----------|--------|
| H1 | Opaque standard source produces a significantly steeper positive AAI slope than transparent standard source | Δβ = .252, p < .001, Cohen's *d* = 1.02 — **supported** |
| H2 | Transparency shifts identity strategies from assimilation toward integration; opacity produces the reverse | Integration in Condition A rose from 41.5% to 50.6%; assimilation in Condition B rose from 30.8% to 46.7% — **supported** |
| H3 | AAI slope longitudinally mediates the effect of assessment condition on the identity-strategy slope | IE = -.108, 95% CI [-.153, -.067] — **supported** |
| H4 | Prior cultural identification moderates the effect of assessment condition on the AAI slope | γ₃ = -.139, p = .002; ω = -.057, 95% CI [-.089, -.028] — **supported** |

A qualitative finding — the **paradox of standard attainment and integration** — emerged from the mixed-methods phase, showing that teacher authority and vocal-plurality imagination serve as compensatory authority pathways beyond the AI assessment itself.

---

## Repository contents

Three downloadable archives are provided as GitHub releases:

### 1. `data.zip`

Contains the study dataset as a single Excel workbook with 18 sheets covering
participant master, four waves of AAI item responses, cross-cultural identity
responses, manipulation-check responses, vocal-skill scores, interview and
journal metadata, and coded theme frequencies. A machine-readable codebook
sheet defines every variable.

Sample: N recruited = 440, N final = 358.

### 2. `materials.zip`

Contains the eight research instruments and qualitative documents used in the
study:

- Questionnaire Booklet (all scales in full)
- Vocal Skill Scoring Rubric (standardized 100-point instrument)
- Interview Protocol (semi-structured; 15 primary questions across 7 sections)
- Interview Transcripts (from four typological cases)
- Reflective Journals (from participants across the four typological cases)
- AI Interface Mockup (visual specification of Conditions A and B)
- Coding Manual (five hierarchical themes with inclusion/exclusion criteria)
- Thematic Analysis Joint Display (mixed-methods integration matrix)

### 3. `code.zip`

Contains the complete analysis pipeline:

- 14 Python analysis modules, each independently runnable
- One master orchestrator (`run_all.py`)
- Configuration file (`config/reference_values.py`) with benchmark values from prior instrument-development work
- The dataset (same file as `data.zip`) for direct execution
- Requirements file and MIT license

The pipeline produces all figures (CONSORT flow, trajectories, slope distributions, path diagram, simple slopes, joint-display heatmap) and all tables (baseline balance, scale reliability, measurement invariance, growth-model estimates, mediation path coefficients, sensitivity bounds) reported in the study.

---

## How to reproduce the analyses

```bash
# 1. Download and extract code.zip
unzip code.zip
cd code_pkg

# 2. Install dependencies
pip install -r requirements.txt

# 3. Run the full pipeline (approximately 45 seconds)
python run_all.py

# Or run individual modules
python analysis/09_moderated_mediation.py
```

Python 3.9 or later is required. The pipeline uses `pandas`, `numpy`, `scipy`,
`statsmodels`, `semopy`, `matplotlib`, and `seaborn`. See `code.zip/requirements.txt`
for exact versions.

---

## Analytical framework

The core structural model treats the linear AAI slope across four waves as
the mediator between assessment condition and the identity-strategy slope,
with prior cultural identification as the moderator:

**Level-1 measurement equation:**

$$ \text{AAI}_{it} = \alpha_i + \beta_i \cdot t + \varepsilon_{it} $$

**Level-2 structural equation for the slope:**

$$ \beta_i = \gamma_0 + \gamma_1 \cdot \text{Cond}_i + \gamma_2 \cdot \text{ID}_i + \gamma_3 \cdot \text{Cond}_i \cdot \text{ID}_i + \zeta_i $$

**Longitudinal indirect effect:**

$$ \text{IE} = \gamma_1 \cdot b_{\beta \to \text{Slope}_{\text{ID}}} $$

**Index of moderated mediation:**

$$ \omega = \gamma_3 \cdot b_{\beta \to \text{Slope}_{\text{ID}}} $$

Confidence intervals for IE and ω are obtained via bias-corrected bootstrap
resampling with B = 5000.

---

## Materials development

The Algorithmic Authority Internalization (AAI) scale was developed for this
study across a two-stage validation procedure:

- **Stage 1 (EFA).** Independently recruited scale-development sample (n = 350 vocal learners); four factors extracted with cumulative variance 68.4%.
- **Stage 2 (CFA).** T1 data from the main sample (n = 358); four-factor model fit χ²/df = 2.34, CFI = .943, TLI = .935, RMSEA = .058, SRMR = .049.

Cronbach's alpha ≥ .80 and AVE ≥ .55 for all four dimensions.
Longitudinal measurement invariance was established across all four waves
(|ΔCFI| < .01 between nested models).

---

## Ethical safeguards

- Approved by the Institutional Review Board.
- All participants provided written informed consent and could withdraw at any time without academic penalty.
- To control for the Hawthorne effect, participants were told the study examined the instructional effects of AI feedback in vocal learning; the between-condition differences were not disclosed in advance.
- The acoustic scoring engine remained fixed throughout the semester; both groups were taught by instructors who had received standardized training and were not exposed to the interface differences.

---

## Citation

If you use the materials, dataset, or code from this repository in your own
work, please cite the study:

> *The Influence of Cultural Origins and Transparency of AI Evaluation Criteria in Bel Canto Education on Cross-Cultural Identity Construction among Chinese Learners: The Mediating Role of Algorithmic Authority Internalization.*

---

## License

- **Code**: MIT License (see `LICENSE` in `code.zip`).
- **Data and materials**: Creative Commons Attribution 4.0 International (CC BY 4.0) — free to use, share, and adapt with attribution.

---

## Contact

Issues, questions, and pull requests are welcome through the GitHub issue tracker.
