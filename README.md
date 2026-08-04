# Immune microenvironment of gastric adenocarcinoma vs. peritumoral tissue

Deconvolution of the tumour immune microenvironment in **gastric
adenocarcinoma (GAC)** compared with **peritumoral tissue (PTT)**, integrated
with network-based analyses of immune-cell fractions and microbial abundance.

Companion code for: *"Immune Remodeling and Dysbiosis May Distinguish the
Microenvironments of Gastric Adenocarcinoma and Peritumoral Tissue"*.

## What the analysis covers

* **Immune deconvolution with three methods** on the same TPM matrix:
  * **CIBERSORT** (LM22 signature, `code/CIBERSORT.R`)
  * **quanTIseq** (`quantiseqr`)
  * **EPIC**
* **Bacterial abundance** from metatranscriptomics (genus-level), joined to
  the clinical/deconvolution tables.
* **Correlation networks** — Spearman correlations between immune-cell
  fractions and network hubs, computed separately for **GAC and PTT**;
  significance matrices exported to Excel.
* **Statistical comparisons** — Wilcoxon tests of cell fractions and hub
  expression between GAC and PTT.
* **Figures** — layout figures of cell fractions, heatmaps, topology and
  hub/cell analyses.

## Reproducibility

```r
rmarkdown::render("code/XMEETING.Rmd")
```

* The project root is detected automatically — no hardcoded machine paths.
* Set `set.seed(123)` for the permutation components.
* Paths can be overridden with env vars `MI_DATA_DIR` and `MI_QV25_DIR`.

### Input data (not committed — private cohort)
Place the cohort files (Salmon quantifications, sample tables, clinical
data, `tpm_matrix.txt`, `bactab_all_genus.tsv`, `vsdcodingcompleto.RData`,
`dados_gerais2.RData`) in `data/qv25/` — the script resolves them relative
to the project root. `data/LM22.txt` (public CIBERSORT reference signature)
is included in the repo.

## Files
* `code/XMEETING.Rmd` — full analysis (deconvolution, microbiome,
  correlations, statistics, figures)
* `code/CIBERSORT.R` — reference implementation of CIBERSORT
  (Newman et al., *Nat. Methods* 2015; LM22)
* `data/LM22.txt` — LM22 immune-cell signature matrix (public reference)

## Stack
R/Bioconductor: CIBERSORT, quanTIseq (quantiseqr), EPIC, ComplexHeatmap,
Hmisc, writexl, ggplot2.