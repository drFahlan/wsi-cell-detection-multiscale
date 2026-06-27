# Multi-Scale WSI Cell Detection with Tissue-Guided Knowledge Injection

Cell detection and classification (tumor vs. healthy) on Whole Slide Images (WSI), comparing single-scale and multi-scale input pipelines with auxiliary tissue segmentation as a source of spatial context.

---

## Problem

Accurate detection and classification of cells in histopathology images is a critical step in computational pathology. Whole Slide Images (WSIs) are captured at multiple magnification levels, yet most detection pipelines use a single scale, discarding the spatial context available at coarser resolutions. This project investigates whether incorporating an additional WSI scale — and injecting tissue-level segmentation knowledge — improves cell detection performance.

The dataset supports **multitask learning**: it contains annotations for both cell detection/classification (primary task) and tissue segmentation (auxiliary task). The auxiliary task provides spatial priors that may inform cell-level predictions.

---

## Dataset

This project uses the **[OCELOT 2023](https://ocelot.grand-challenge.org/)** dataset, a publicly available benchmark for cell detection in histopathology.

| Property | Detail |
|---|---|
| Task | Cell detection + classification (tumor / background) |
| Modality | H&E stained WSI patches |
| Scales | Cell-level crop + tissue-level crop (two scales per sample) |
| Auxiliary labels | Tissue region segmentation (tumor / background tissue) |
| Split | Train / Val / Test |

EDA findings that motivated experimental design choices are documented in [`eda/README.md`](eda/README.md).

---

## Experimental Design

Four experimental conditions were compared:

| # | Condition | Description |
|---|---|---|
| 1 | **Baseline** | Single-scale input, cell detection only |
| 2 | **Multi-scale** | Cell-scale + tissue-scale input combined |
| 3 | **Knowledge injection** | Tissue segmentation prediction used as auxiliary input to cell detection |
| 4 | **Multi-scale + Knowledge injection** | Both extensions combined |

See [`notebooks/README.md`](notebooks/README.md) for the full notebook index and links to versions with outputs.

---

## Key Findings

> Results will be updated when paper is finalized.

| Condition | F1 | Precision | Recall |
|---|---|---|---|
| Baseline | — | — | — |
| Multi-scale | — | — | — |
| Knowledge injection | — | — | — |
| Multi-scale + KI | — | — | — |

Qualitative detection examples and scale comparison figures are in [`assets/`](assets/).

---

## Architecture

<!-- Replace with actual architecture diagram -->
![Architecture](assets/architecture.png)

---

## Repository Structure

```
├── notebooks/          ← stripped notebooks (no outputs); full versions linked from notebooks/README.md
├── eda/                ← EDA findings and their influence on design decisions
├── assets/             ← figures: architecture, results table, detection examples
└── requirements.txt    ← Python dependencies
```

---

## Reproducibility Note

Experiments were run on **Google Colab** with data loaded from Google Drive. Notebooks in this repository have outputs stripped to keep file sizes manageable. Full notebooks with outputs are available via Google Drive links in [`notebooks/README.md`](notebooks/README.md).

The OCELOT dataset can be downloaded from the [official challenge page](https://ocelot.grand-challenge.org/).

---

## Paper

<!-- Add citation or link when available -->
A paper describing this work was submitted to IUPESM 2025. It will be linked here upon publication.

---

## Author

**Dwi Rezky Fahlan**  
GitHub: [@drFahlan](https://github.com/drFahlan)
