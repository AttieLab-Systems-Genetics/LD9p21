# Quarto Presentation Summary: Cross-Ancestry Fine-Mapping of Locus 9p21.3

## Prompts & Directives

### Initial Prompt
>
> Using `https://byandell.github.io/DocumentTools/prompts/presentation_prompts.html` develop a comprehensive quarto slide deck for the PDF in folder `data/`. Start by developing a plan broken into stages based on the main sections of this PDF.

### Follow-up Refinements

1. **Article Source**: Switched focus to `data/mmc3.pdf` (*Alkhairo et al., 2026, AJHG 113(11), 1630–1645*).
2. **Figure Asset Sourcing**: Linked directly to official Cell Press / *AJHG* remote URLs from [README.md](README.md#figures) rather than downloading local PNGs; verified dynamic base64 compilation without local image assets.
3. **Typography Calibration**: Scaled inline backtick code elements (`0.88em` monospace) to match the visual height of adjacent text across all slide elements.
4. **Slide 7 Architecture**: Resolved Mermaid SVG layout collision by restructuring Slide 7 ("Central Hypotheses Addressed by Alkhairo et al.") into a 2×2 responsive callout grid.

---

## 1. Generated Assets

| File | Purpose |
| :--- | :--- |
| [quarto/ld9p21_cross_ancestry.qmd](quarto/ld9p21_cross_ancestry.qmd) | Complete Quarto Reveal.js presentation source code |
| [quarto/custom.scss](quarto/custom.scss) | Custom presentation styling (Google Fonts `Outfit`/`Inter`, statistical cards, badges, callouts) |
| [quarto/ld9p21_cross_ancestry.html](quarto/ld9p21_cross_ancestry.html) | Self-contained, rendered Reveal.js slide deck (5.7 MB) |
| [.gitignore](.gitignore) | Configured to track source files while ignoring `.quarto/` and `*_files/` |
| [Figures 1–5](README.md#figures) | Embedded dynamically via official *AJHG* / Cell Press URLs |

---

## 2. Key Presentation Features & Design System

- **Reveal.js Layout**: 16:9 widescreen presentation, linear navigation, slide progress bar, slide numbering, and full overview matrix mode (`O` key).
- **Typography & Aesthetics**: Google Fonts pairing — `Outfit` for presentation and slide headings; `Inter` for body text, tables, and statistics.
- **Proportional Code Sizing**: Inline monospace elements (`code:not(pre code)`) styled at `0.88em` with subtle borders (`#e2e8f0`) to match surrounding text height without distortion.
- **Dynamic CDN Embedding**: All 5 publication figures rendered directly from the official journal CDN, eliminating large local binary dependencies while producing a fully offline-capable self-contained HTML deck.
- **Slide 7 Responsive Card Grid**: Replaced SVG flowchart with a 2×2 callout grid to ensure text readability without browser-specific hidden slide rendering collisions.

---

## 3. Presentation Structure & Scientific Narrative

The slide deck is structured into 8 sequential stages directly mapping the paper and its supplemental analyses:

1. **Orientation & Executive Summary**:
   - The 19-year 9p21.3 reproducibility paradox (robust in non-Africans, absent in Africans).
   - High-level metric summary cards ($N > 650,000$ individuals, 111 fine-mapped variants, 5 local ancestry tiers).
   - Two-column clickable Table of Contents.
2. **The 9p21.3 Paradox**:
   - Discovery history (2007 landmark GWAS) and the *ANRIL* / *CDKN2A* / *CDKN2B* genomic architecture.
   - Four formal hypotheses tested (power/bias, allelic heterogeneity, LD decay, multi-variant haplotype requirement).
3. **Multi-Ancestry Cohorts & Statistical Methods**:
   - Representation across MVP ($N > 650,000$), UK Biobank, BioBank Japan, H3Africa WGS, and Saudi SHGP.
   - Global Ancestry Inference (GIA) vs. Local Ancestry Inference (LAI) via Gnomix across 5 contiguous intervals.
   - Hamming distance formulation against an all-protective non-risk baseline.
4. **Global vs. Local Ancestry Dissection (Figures 1 & 2)**:
   - Global LocusZoom plots: strong signals in EUR ($p = 2.4 \times 10^{-143}$), EAS ($p = 2.2 \times 10^{-23}$), AMR, MID; null in AFR.
   - Local ancestry uncoupling in MVP: African Americans carrying one European 9p21 chromosome (`AFR|EUR`) restore the full CAD association ($p = 5.1 \times 10^{-14}$), while homozygous African chromosomes (`AFR|AFR`) show zero risk.
   - Evolutionary LD decay and Hudson $F_{ST}$ differentiation ($F_{ST} = 0.278$).
5. **Allelic Heterogeneity & Stepwise Conditional Analysis (Figure 3)**:
   - Primary signals differ by population (EUR lead `rs1333049` vs. EAS lead `rs4977574`).
   - Stepwise forward conditioning reveals secondary independent signals across the locus.
6. **Haplotypes & Hamming Distance (Figure 4)**:
   - The 6-SNP core haplotypes: `AACATT` (protective) and `GGTTCA` (risk) are virtually absent in continental and diaspora Africans.
   - Monotonic dose-response: progressive risk allele accumulation linearly drives CAD odds in non-Africans, whereas African genomes carry fragmented, novel recombinant configurations.
7. **Phenome-Wide Pleiotropy & Decoupled Sub-Phenotypes (Figure 5)**:
   - Pleiotropic divergence: In `EUR|EUR` and `AFR|EUR`, 9p21.3 influences CAD, PVD, aortic aneurysm, and T2D/glucose traits.
   - In `AFR|AFR`, vascular/glycemic associations disappear, but monocyte and platelet count associations remain intact, establishing decoupled regulatory elements.
8. **Molecular Circuitry, Clinical PRS Transferability & Conclusions**:
   - *ANRIL* splice modulation: circular (`circANRIL`) vs. pathological linear isoforms.
   - Polygenic Risk Score (PRS) equity: why European PRSs miscalibrate African risk, and how local-ancestry-informed scoring (LAI-PRS) resolves the disparity.

---

## 4. Verification & Viewing

HTML rendering preserves all slide elements, while PDF export requires some additional steps to ensure proper formatting.

- **Compilation (HTML)**: Verified via `quarto render quarto/ld9p21_cross_ancestry.qmd` with exit code `0` and zero warnings.
- **Export to PDF (Terminal Command via Headless Chrome — Landscape Mode)**:

  ```bash
  "/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" \
    --headless \
    --run-all-compositor-stages-before-draw \
    --no-pdf-header-footer \
    --print-to-pdf="quarto/ld9p21_cross_ancestry.pdf" \
    "file://$(pwd)/quarto/ld9p21_cross_ancestry.html?print-pdf"
  ```

  *(Generates 11" × 8.5" widescreen landscape slides [792 × 612 pt] with zero margins and background graphics).*
- **Export to PDF (Browser Print Dialog)**:
  1. Open `quarto/ld9p21_cross_ancestry.html?print-pdf` in Chrome/Safari/Edge.
  2. Press `Cmd + P`.
  3. Destination: *Save as PDF*, Layout: *Landscape*, Margins: *None*, Options: Check *Background graphics*.
- **Viewing**: Open [quarto/ld9p21_cross_ancestry.html](quarto/ld9p21_cross_ancestry.html) directly in any modern web browser.
- **Keyboard Shortcuts**:
  - `F`: Toggle full screen
  - `O`: Toggle slide overview matrix
  - `Space` / `Arrow Keys`: Advance slides
