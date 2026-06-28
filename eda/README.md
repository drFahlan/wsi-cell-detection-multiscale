# EDA Findings

Key observations from exploratory analysis of the OCELOT 2023 dataset, and the design decisions they led to. Full notebook: [`../notebooks/01_eda_preprocessing.ipynb`](../notebooks/01_eda_preprocessing.ipynb)

---

### Spatial arrangement is the primary discriminating factor

Tumor and background cells show high intra-class morphological diversity — appearance alone is not a reliable classifier. However, spatial arrangement consistently separates the two classes: tumor cells tend to cluster within cancer tissue regions, while background cells do not.

**Decision:** Rather than improving cell-level feature extraction, the focus shifted to injecting tissue-level spatial context into the cell detection pipeline — motivating the entire integration strategy study.

---

### Cancer boundaries in the tissue FoV are visually ambiguous

The boundary between cancer and non-cancer regions in the large FoV is not always clear-cut. Simple or shallow models are likely to misclassify ambiguous boundary regions.

**Decision:** U-Net++ with SE-ResNet50 encoder was chosen for tissue segmentation — dense feature reuse across scales for boundary detail, channel-wise attention for distinguishing ambiguous regions. High tissue segmentation accuracy was treated as a prerequisite, since the probability map feeds all splits (train/val/test) of the cell detection pipeline.

---

### Cells are visually distinguishable at the small FoV scale

At the high-magnification small FoV, individual cell nuclei are clearly visible and separable from surrounding tissue. Deep feature extraction is not necessary for cell localization.

**Decision:** A lightweight Attention U-Net with ResNet34 encoder was chosen for cell detection. This keeps model complexity low so that performance differences between experimental conditions reflect the integration strategy rather than the model itself.
