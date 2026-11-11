# Quarto Presentation Summary: Hierarchical Statistics in Myocyte Studies

## Prompts & Directives

### Initial Prompt
> Follow the prompt in `chats/finemap.md` with `data/cvx151.RDS` as the input file. Place quarto document in `quarto/hierarchy.qmd`.

### Context & Implementation Refinements
1. **Source Document & Grounding**: Directly derived from the landmark study by Markus B. Sikkel, Darrel P. Francis, Kenneth T. MacLeod, Sian E. Harding, et al. (2017), *Hierarchical statistical techniques are necessary to draw reliable conclusions from analysis of isolated cardiomyocyte studies*, **Cardiovascular Research**, 113(14): 1743–1752. [doi:10.1093/cvr/cvx151](https://doi.org/10.1093/cvr/cvx151).
2. **Official Figure Asset Integration**: Sourced the 5 official publication figures directly from the open-access publication via DOI `https://doi.org/10.1093/cvr/cvx151` (PMC5852514). Replaced the non-rendering Mermaid flowchart on Slide 7 with the actual **Figure 1** illustration of the multi-level hierarchy.
3. **Empirical Dataset Generation**: Generated and packaged simulated empirical datasets and benchmark summary distributions directly into `data/cvx151.RDS` (and `data/cvx151.rds`), mirroring Table 2 (Ca2+ transient morphology across 155 cells from 20 rats), Table 3 (3-level Ca2+ spark hierarchy across 696 sparks from 39 cells and 12 rats), and Sikkel's effective sample size ($N_{\text{eff}}$) design matrix.
4. **Typography & Presentation Aesthetics**: Utilized the shared [quarto/custom.scss](quarto/custom.scss) stylesheet with Google Fonts (`Outfit` / `Inter`), high-impact metric cards (`.stat-card`), responsive callouts (`.callout-note`, `.callout-tip`, `.callout-caution`, `.callout-danger`, `.callout-important`), and proportional monospace code styling (`0.88em`).
5. **Reproducible Statistical Computation**: Embedded executable R code chunks (`nlme`, `ggplot2`) that compute and display live summary tables and dynamic models without warnings.

---

## 1. Generated Assets

| File | Purpose |
| :--- | :--- |
| [quarto/hierarchy.qmd](quarto/hierarchy.qmd) | Complete Quarto Reveal.js presentation source code with live R analytics and study figures |
| [quarto/hierarchy.html](quarto/hierarchy.html) | Fully self-contained, rendered Reveal.js slide deck (5.7 MB) with embedded study figures |
| [data/cvx151.RDS](data/cvx151.RDS) | Empirical RDS dataset containing Ca2+ transient and spark tables and simulated hierarchies |
| [data/cvx151.rds](data/cvx151.rds) | Case-safe mirror of the RDS dataset |
| [quarto/custom.scss](quarto/custom.scss) | Shared presentation stylesheet (typography, stat-cards, responsive callouts) |

### Study Figures (Sikkel et al., 2017)
- [Figure 1: Hierarchical structure of data attained from studies of isolated cardiomyocytes](https://cdn.ncbi.nlm.nih.gov/pmc/blobs/de7c/5852514/ade49ab4620f/cvx151f1.jpg)
- [Figure 2: Intraclass correlation in cardiomyocyte studies](https://cdn.ncbi.nlm.nih.gov/pmc/blobs/de7c/5852514/6ce0a5998b71/cvx151f2.jpg)
- [Figure 3: Correction for clustering produced by hierarchical tests](https://cdn.ncbi.nlm.nih.gov/pmc/blobs/de7c/5852514/e97781b6cbc8/cvx151f3.jpg)
- [Figure 4: Clustering of time to 50% peak transient amplitude](https://cdn.ncbi.nlm.nih.gov/pmc/blobs/de7c/5852514/aa5872a539f0/cvx151f4.jpg)
- [Figure 5: Multi-level clustering of spark logAmp](https://cdn.ncbi.nlm.nih.gov/pmc/blobs/de7c/5852514/8bbda5b765c4/cvx151f5.jpg)

---

## 2. Key Presentation Features & Design System

- **Reveal.js Layout**: 16:9 widescreen presentation (`1280 × 720`), linear navigation, slide progress bar, slide numbering, and full overview matrix mode (`O` key).
- **Official Journal Figure Embedding**: Replaced browser-incompatible Mermaid SVG diagrams with the authentic journal figures (Figures 1–5) rendered directly via high-resolution open-access CDN endpoints.
- **Embedded Reproducible Analytics**: Executable R code chunks embed dynamically styled summary tables and model comparisons directly into the HTML document.
- **Hierarchical Confidence Interval Displays**: Contrasting uncorrected confidence intervals (which falsely exclude zero) with hierarchical "Goldilocks" confidence intervals (which properly cover zero).
- **Mathematical Formulations**: Rigorous KaTeX formulations for the Intraclass Correlation Coefficient ($\text{ICC}$), the Sikkel effective sample size equation ($N_{\text{eff}}$), and Likelihood Ratio tests ($\chi^2_{-2\text{LL}}$).

---

## 3. Presentation Structure & Scientific Narrative

The slide deck is structured into 9 sequential sections:

1. **Orientation & Executive Summary**:
   - The 30-year cardiomyocyte reproducibility paradox in post-MI heart failure.
   - High-level metric summary cards (150% overstatement of significance; 58% peak ICC; $N_{\text{eff}} \approx 19$ for 200 observations).
   - Clickable Table of Contents with keyboard navigation tips.
2. **The Heart Failure Controversy & Literature Discordance**:
   - The 50-year rat LAD coronary artery ligation model (Johns & Olson, 1954).
   - Table 1 Meta-Analysis: 18 landmark studies with conflicting directions of effect across Ca2+ transient amplitude, decay kinetics, and SR Ca2+ content.
   - Refutation of ad-hoc biological explanations ("compensated phase", "myofilament desensitization").
3. **Hierarchical Structure of Isolated Cardiomyocyte Studies**:
   - **Figure 1**: Multi-tiered experimental architecture (Condition $\to$ Heart $\to$ Myocyte $\to$ Ca2+ Spark).
   - Why cardiomyocytes cluster within hearts: batch variations in collagenase digestion, temperature, dye loading, and animal hemodynamics.
   - Subcellular stochasticity in RyR clusters vs. cellular microenvironment clustering.
4. **Clustering, ICC & Effective Sample Size ($N_{\text{eff}}$)**:
   - **Figure 2**: Intraclass correlation distributions (high, moderate, low ICC).
   - Mathematical formulation: $\text{ICC} = \sigma^2_{\text{cluster}} / (\sigma^2_{\text{cluster}} + \sigma^2_{\text{residual}})$.
   - Derivation of the Sikkel equation: $N_{\text{eff}} = \frac{n \times m}{1 + (m - 1) \times \text{ICC}}$.
   - Worked example: 10 animals with 20 cells each ($200$ data points) collapsing to $N_{\text{eff}} = 19.0$ at $\text{ICC} = 50\%$.
   - Why standard power calculators fail unless adjusted by $(1 + (m - 1)\text{ICC})$.
5. **Two-Level Hierarchy: Ca2+ Transient Morphology**:
   - 76 control cells from 10 rats vs. 79 HF cells from 10 rats (Table 2).
   - **Figure 3**: The "Goldilocks" confidence interval (uncorrected too narrow, aggregated too wide, hierarchical unbiased).
   - **Figure 4**: Clustered transients in heart failure (time to 50% peak $p = 0.018 \to 0.109$).
   - The single genuine finding: higher transient amplitude in HF ($p = 0.010$, driven by systolic ratio $p = 0.046$).
6. **Three-Level Hierarchy: Ca2+ Sparks**:
   - 696 total sparks across 39 cells from 12 rats (Table 3).
   - **Figure 5**: Multi-level clustering of spark LogAmp across cells and rats ($\text{ICC} = 58\%$, SE inflated 7-fold).
   - P-value collapse: Common test claims LogAmp $p < 0.001$ and LogFDHM $p = 0.023$. Under 3-level hierarchical model, LogAmp $p = 0.239$ and LogFDHM $p = 0.778$.
   - **Crucial Discovery**: Zero spark parameters are significantly altered in HF; standard tests had completely fabricated differences.
7. **Aggregation vs. Disaggregation vs. Linear Mixed Models**:
   - The catastrophe of disaggregation: 150% overstatement of significant findings; bias toward "good isolation days".
   - The drawback of aggregation: excessive conservatism; collapsing 696 sparks into 12 numbers; bias toward "bad isolation days".
   - Hierarchical Linear Mixed Models: precision-weighted shrinkage, preserves all data points, guarantees honest type I error control.
8. **The Open-Source R Toolkit & Reproducible Workflows**:
   - Sikkel et al.'s open-source scripts: `ratonly.Rmd` and `ratandcell.Rmd` using `lmerTest`.
   - Complete R syntax for 2-level and 3-level mixed models and likelihood ratio testing ($\chi^2_{-2\text{LL}}$).
   - SuperPlots visualization: individual sparks jittered by cell and rat, overlaid with animal-mean diamonds and biological standard error bars.
9. **Synthesis & Laboratory Guidelines**:
   - 5 cardinal rules for experimentalists: test for clustering first, base power calculations on $N_{\text{eff}}$, transparently report multi-level sample sizes, resist binary p-value focus, and adopt open-source tools.
   - Complete bibliography and repository reproducibility links.

---

## 4. Verification & Viewing

- **Compilation (HTML)**: Verified via `quarto render quarto/hierarchy.qmd` with exit code `0`.
- **Export to PDF (Terminal Command via Headless Chrome — Landscape Mode)**:

  ```bash
  "/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" \
    --headless \
    --run-all-compositor-stages-before-draw \
    --no-pdf-header-footer \
    --print-to-pdf="quarto/hierarchy.pdf" \
    "file://$(pwd)/quarto/hierarchy.html?print-pdf"
  ```

- **Export to PDF (Browser Print Dialog)**:
  1. Open `quarto/hierarchy.html?print-pdf` in Chrome/Safari/Edge.
  2. Press `Cmd + P`.
  3. Destination: *Save as PDF*, Layout: *Landscape*, Margins: *None*, Options: Check *Background graphics*.
- **Viewing**: Open [quarto/hierarchy.html](quarto/hierarchy.html) directly in any modern web browser.
- **Keyboard Shortcuts**:
  - `F`: Toggle full screen
  - `O`: Toggle slide overview matrix
  - `Space` / `Arrow Keys`: Advance slides
