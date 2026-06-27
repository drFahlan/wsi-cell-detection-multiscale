# EDA Findings

Exploratory analysis of the OCELOT 2023 dataset, and how findings shaped the experimental design.

Full EDA notebook: [`../notebooks/01_eda.ipynb`](../notebooks/01_eda.ipynb)

---

## Dataset Overview

<!-- Fill in: total sample count, train/val/test split sizes -->

| Split | Samples |
|---|---|
| Train | — |
| Val | — |
| Test | — |

---

## Class Distribution

<!-- Fill in: cell class balance (tumor vs. background cells), tissue class balance -->

- **Cell-level:** The dataset is imbalanced toward background cells. Tumor cells represent approximately —% of labeled cells.
- **Tissue-level:** Tumor tissue regions cover approximately —% of tissue-level crops.

**Design impact:** <!-- Describe how class imbalance was handled, e.g. weighted loss, oversampling -->

---

## Spatial Distribution

<!-- Describe: how cells are distributed within crops, clustering tendencies, edge effects, etc. -->

**Design impact:** <!-- How did spatial patterns influence model architecture or input cropping strategy? -->

---

## Scale Relationship

<!-- Describe: what the tissue-level crop adds that the cell-level crop lacks — contextual tissue regions, spatial orientation, etc. -->

**Design impact:** This observation motivated the multi-scale experimental condition (Notebook 03), where the tissue-scale crop is provided as a second input to give the model access to broader spatial context.

---

## Other Findings

<!-- Any additional observations from EDA that influenced preprocessing, augmentation, or evaluation strategy -->
