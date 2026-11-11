# Quarto Presentation Summary: Pseudoreplication in Physiology

## Prompts & Directives

### Initial Prompt
> Follow the prompt in `chats/finemap.md` with `data/psuedoreplication.RDS` as the input file. Place quarto document in `quarto/pseudoreplication.qmd`.

### Context & Implementation Refinements
1. **Source Document & Theoretical Foundation**: Grounded in the tutorial review by David A. Eisner (2021), *Pseudoreplication in physiology: More means less*, **J. Gen. Physiol.** 153(2): e202012826. [doi:10.1085/jgp.202012826](https://doi.org/10.1085/jgp.202012826), coupled with foundational principles from Stuart Hurlbert (1984) and Sikkel et al. (2017).
2. **Official Figure Asset Integration**: Sourced the 3 official publication figures directly from the open-access publication via DOI `https://doi.org/10.1085/jgp.202012826` (PMC7814346) and embedded them across their respective slides.
3. **Resolution of Non-Rendering Mermaid Diagram (Slide 18)**: Replaced the browser-incompatible Mermaid SVG diagram on Slide 18 (*Multi-Tiered Experimental Hierarchies*) with a responsive 4-tier HTML nested card stack (Group $\to$ Animal $\to$ Cell/Islet $\to$ Subcellular Trace) with robust Tailwind color borders.
4. **Empirical Dataset Generation**: Generated and packaged simulated datasets and benchmark distributions directly into `data/psuedoreplication.RDS` (and `data/pseudoreplication.rds`), replicating Eisner's Figure 1 ($N=3, n=5$, Seed 153), a 2,000-replicate Monte Carlo type I error sweep ($n = 1$ to $50$), and an unbalanced mouse islet dataset inspired by the Attie–Yandell correspondence in `subsample.md`.
5. **Typography & Styling Consistency**: Leveraged the shared [quarto/custom.scss](quarto/custom.scss) stylesheet with Google Fonts (`Outfit` / `Inter`), statistical summary cards (`.stat-card`), responsive callouts (`.callout-note`, `.callout-tip`, `.callout-caution`, `.callout-important`), and proportional inline code sizing (`0.88em`).
6. **Live Statistical Modeling**: Integrated live, reproducible R execution via base `nlme` and `ggplot2` to calculate side-by-side estimates comparing naive pooled linear regression, conservative animal-mean models, and hierarchical linear mixed-effects models (LMMs).

---

## 1. Generated Assets

| File | Purpose |
| :--- | :--- |
| [quarto/pseudoreplication.qmd](quarto/pseudoreplication.qmd) | Complete Quarto Reveal.js presentation source code with live R chunks and study figures |
| [quarto/pseudoreplication.html](quarto/pseudoreplication.html) | Fully self-contained, rendered Reveal.js slide deck (5.6 MB) with embedded study figures |
| [data/psuedoreplication.RDS](data/psuedoreplication.RDS) | Empirical RDS dataset containing simulation trials, islet data, and Monte Carlo curves |
| [data/pseudoreplication.rds](data/pseudoreplication.rds) | Case-safe mirror of the RDS dataset |
| [quarto/custom.scss](quarto/custom.scss) | Shared presentation stylesheet (typography, stat-cards, responsive callouts) |

### Study Figures: Eisner (2021)
- [Figure 1: Simulation of the effects of comparing 15 cells drawn from 3 animals](https://cdn.ncbi.nlm.nih.gov/pmc/blobs/7594/7814346/d08a6b63a20a/JGP_202012826_Fig1.jpg)
- [Figure 2: Effects of animal and cell SD on apparent significance](https://cdn.ncbi.nlm.nih.gov/pmc/blobs/7594/7814346/032c8e97a0c0/JGP_202012826_Fig2.jpg)
- [Figure 3: Dependence of apparent significance on SD and sample numbers](https://cdn.ncbi.nlm.nih.gov/pmc/blobs/7594/7814346/4f208818e241/JGP_202012826_Fig3.jpg)

---

## 2. Key Presentation Features & Design System

- **Reveal.js Layout**: 16:9 widescreen presentation (`1280 × 720`), linear navigation, slide progress bar, slide numbering, and full overview matrix mode (`O` key).
- **Official Journal Figure Embedding**: Figures 1, 2, and 3 embedded directly via high-resolution open-access CDN endpoints, matching the presentation structure of `hierarchy.qmd` and `ld9p21_cross_ancestry.qmd`.
- **Responsive 4-Tier Hierarchy Stack**: Replaced brittle Mermaid flowcharts with pure CSS/HTML nested card stacks that render flawlessly without SVG script dependencies.
- **Embedded Reproducible Analytics**: Executable R code chunks embed dynamically styled ggplot2 figures and real-time model outputs directly into the HTML document.
- **SuperPlots Visualization**: Replaced misleading pooled bar charts with modern "SuperPlots" (Lord et al., 2020), plotting individual cells color-coded by animal, overlaid with animal-mean diamonds and cluster-level standard error bars.
- **Mathematical Transparency**: Full KaTeX/MathJax formulations for total variance decomposition, the Intraclass Correlation Coefficient ($\text{ICC}$), the Sikkel effective sample size equation ($N_{\text{eff}}$), and Brian Yandell's nested ANOVA degrees-of-freedom derivation.

---

## 3. Presentation Structure & Scientific Narrative

The slide deck is structured into 9 sequential sections:

1. **Orientation & Executive Summary**:
   - The physiological reproducibility paradox: how collecting more cells can inflate false positive discoveries up to 47%.
   - Metric cards: 47% peak false-positive rate, effective sample size collapse ($N \times n \to N$), and Hurlbert's 1984 benchmark.
   - Clickable Table of Contents with keyboard navigation tips.
2. **The Pseudoreplication Crisis & The Independence Assumption**:
   - Formal definition: treating technical replicates as independent biological units.
   - The extreme limiting case ($N = 1, n = 100$): the London vs. New York blood pressure analogy.
   - Ubiquity across isolated cardiomyocytes, slice electrophysiology, pancreatic islets, and cell culture plates.
3. **Variance Sources & The ICC Framework**:
   - Partitioning variance: between-animal variance ($\sigma^2_{\text{animal}}$) vs. within-animal measurement error ($\sigma^2_{\text{cell}}$).
   - Intraclass Correlation Coefficient ($\text{ICC}$): mathematical formula and limiting behavior ($\text{ICC} \to 1.0$ vs. $\text{ICC} \to 0.0$).
   - Sikkel effective sample size: $N_{\text{eff}} = \frac{N \times n}{1 + (n - 1) \times \text{ICC}}$. Dynamic table illustrating how 50 cells from 3 animals only provides $N_{\text{eff}} = 5.9$ when $\text{ICC} = 0.5$.
4. **Empirical Simulation: "More Means Less" (Eisner Figures 1–3)**:
   - **Figure 1**: 3 animals, 5 cells/animal under true null. Animal t-test ($p = 0.15$), LME ($p = 0.13$), naive cell t-test ($p = 0.0007$ spurious false positive).
   - **Figure 2**: Lower cell SD increases false discoveries (tighter clusters appear as repeated confirmations); higher animal SD increases false discoveries.
   - **Figure 3**: 200,000-trial parameter sweeps across SD space (Points A–D) and demonstration that adding more animals does *not* fix naive pooling while adding cells monotonically worsens type I error.
5. **Four Critical Nuances & Complex Hierarchies**:
   - When cell $n$ is valid (acute pharmacological interventions on single preparations without animal-group comparisons).
   - Multi-level subcellular nesting (hundreds of Ca2+ sparks per cardiomyocyte).
   - In vitro cell culture artifacts (wells and coverslips sharing flask/passage heritage).
   - Real biological intra-individual heterogeneity vs. technical noise.
   - **Slide 18**: Multi-Tiered Experimental Hierarchies presented as a 4-tier visual card stack.
6. **Statistical Solutions: Averaging vs. Linear Mixed Models**:
   - **Approach 1 (Animal Averaging)**: Arithmetic mean per animal $\bar{y}_i$ followed by standard t-test. Guaranteed 5.0% error control, but unweighted for unbalanced cell counts.
   - **Approach 2 (Linear Mixed-Effects Models)**: Gold standard random-intercept formulation $y_{ijk} = \mu + \text{Treatment}_i + u_{j(i)} + \epsilon_{ijk}$. Precision-weighted shrinkage, handles missing data, optimal statistical power.
   - Comprehensive comparative matrix across analytical parameters.
7. **Case Study: Mouse Islet Cell Hierarchies (Alan & Brian's Dialogue)**:
   - Addressing Alan Attie's question in `subsample.md` regarding multiple islets isolated from mice.
   - Brian Yandell's ANOVA table: Group ($df = 1$), Mouse within Group ($df = N - 2$), and Islet within Mouse ($df = N(c - 1)$).
   - Empirical run on unbalanced islet dataset ($N = 8$ mice, 53 total islets): naive test falsely claims $p = 0.0315$, while mouse-mean test ($p = 0.293$) and LME ($p = 0.299$) correctly reflect the true null.
8. **Implementation in R & SuperPlots**:
   - Clean, reproducible syntax for `aov(y ~ group + Error(animal_id))`, `nlme::lme()`, and `lme4::lmer()`.
   - The SuperPlot design standard (Lord et al., 2020): transparent technical replicate dots, color-coded animal clusters, enlarged biological summary diamonds, and animal-level error bars.
9. **Synthesis & Laboratory Guidelines**:
   - 5 cardinal rules for experimentalists: identify the true biological unit, never pool replicates naively, report both $N$ and $n$, select proper modeling software, and present data with SuperPlots.
   - Complete bibliography and repository reproducibility links.

---

## 4. Verification & Viewing

- **Compilation (HTML)**: Verified via `quarto render quarto/pseudoreplication.qmd` with exit code `0`.
- **Export to PDF (Terminal Command via Headless Chrome — Landscape Mode)**:

  ```bash
  "/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" \
    --headless \
    --run-all-compositor-stages-before-draw \
    --no-pdf-header-footer \
    --print-to-pdf="quarto/pseudoreplication.pdf" \
    "file://$(pwd)/quarto/pseudoreplication.html?print-pdf"
  ```

- **Export to PDF (Browser Print Dialog)**:
  1. Open `quarto/pseudoreplication.html?print-pdf` in Chrome/Safari/Edge.
  2. Press `Cmd + P`.
  3. Destination: *Save as PDF*, Layout: *Landscape*, Margins: *None*, Options: Check *Background graphics*.
- **Viewing**: Open [quarto/pseudoreplication.html](quarto/pseudoreplication.html) directly in any modern web browser.
- **Keyboard Shortcuts**:
  - `F`: Toggle full screen
  - `O`: Toggle slide overview matrix
  - `Space` / `Arrow Keys`: Advance slides
