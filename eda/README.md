# EDA Findings

Exploratory analysis of the OCELOT 2023 dataset. Full notebook: [`../notebooks/01_eda_preprocessing.ipynb`](../notebooks/01_eda_preprocessing.ipynb)

---

## Dataset Structure

Each sample consists of a paired dual-scale image:
- **Small FoV** (1024×1024 px, ~0.19 µm/px): high-magnification crop with cell point annotations
- **Large FoV** (4096×4096 px, ~0.77 µm/px): lower-magnification crop with pixel-level tissue annotations
- **Relative coordinates** of the small FoV center within the large FoV

673 total samples from 306 TCGA WSIs, split 6:2:2 stratified per WSI across 6 organs.

---

## Cell Class Distribution

The two cell classes — **tumor** and **background** — are approximately **balanced** in the dataset. This is a deliberate design choice of the OCELOT benchmark to enable fair per-class evaluation.

**Design impact:** No class-weighted loss or oversampling was needed for cell detection. However, the Tversky loss was used alongside BCEWithLogitsLoss to allow fine-grained control over class attention during training.

---

## Cell Morphology and Spatial Arrangement

EDA revealed **high intra-class morphological diversity** in both cell classes — tumor cells and background cells do not separate cleanly on appearance alone.

However, **spatial arrangement consistently emerged as the main discriminating factor**: tumor cells tend to cluster together within cancer tissue regions. This means a cell's class is often better predicted by its neighborhood than by its own appearance.

**Design impact:** This observation directly motivated the integration strategy experiments. Rather than improving the cell detection model itself, the focus shifted to injecting tissue-level spatial context (the tumor region probability map) into the cell detection pipeline. It also motivated maximizing tissue segmentation performance first, since the quality of the injected information directly bounds the cell detection gain.

---

## Cell Radius Distribution

Typical cell radius in the small FoV patches ranges from **12 to 30 pixels**.

**Design impact:** Gaussian dot masks used to convert point annotations to segmentation targets were set with a maximum radius of **11 pixels** (to cover the cell body without exceeding its boundary) and a standard deviation of **4** (to emphasize the cell center). Post-processing local maxima detection used a minimum inter-peak distance of **15 pixels**.

---

## Tissue Region Distribution

The large FoV tissue annotations assign each pixel to **cancer area** or **non-cancer area**. The tissue segmentation model is trained as a binary classifier (0 = non-cancer, 1 = cancer).

---

## Patch Extraction Strategy

During tissue segmentation inference, rather than directly using the large FoV, a **512×512 patch centered on the small FoV** is extracted. This gives the model access to the immediate tissue context surrounding the cell region without processing the full 4096×4096 large FoV.

**Design impact:** The model can leverage tissue context beyond the small FoV boundary when predicting tumor region probability, improving the quality of the probability map used by the cell detection pipeline.
