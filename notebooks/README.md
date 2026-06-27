# Notebooks

All notebooks are stripped of outputs. Full versions with all outputs are available via Google Drive.

| # | Notebook | Description | Full version |
|---|---|---|---|
| 01 | [01_eda_preprocessing.ipynb](01_eda_preprocessing.ipynb) | Exploratory data analysis: dataset statistics, cell radius distribution, morphological diversity, spatial arrangement findings; point-to-mask annotation conversion | [Google Drive]() |
| 02 | [02_tissue_segmentation.ipynb](02_tissue_segmentation.ipynb) | U-Net++ (SE-ResNet50 encoder) tissue segmentation model: training, hyperparameter sweep, sliding window inference, evaluation | [Google Drive]() |
| 03 | [03_baseline_modeling.ipynb](03_baseline_modeling.ipynb) | Baseline cell detection: Attention U-Net (ResNet34 encoder) trained on small FoV only, post-processing pipeline, evaluation | [Google Drive]() |
| 04 | [04_preprocessing_integration.ipynb](04_preprocessing_integration.ipynb) | Pre-processing integration: tumor probability map concatenated to small FoV as 4-channel input; model retrained end-to-end | [Google Drive]() |
| 05 | [05_postprocessing_integration.ipynb](05_postprocessing_integration.ipynb) | Post-processing integration: Gaussian-weighted tumor probability sampling used to refine per-cell confidence scores; no retraining required | [Google Drive]() |

> Google Drive links will be added once shared folders are set up.

## Environment

All notebooks were developed on **Google Colab** (Python 3, GPU runtime). Key dependencies are in [`../requirements.txt`](../requirements.txt).

To run locally, mount the OCELOT dataset from Google Drive or download it from the [official challenge page](https://ocelot.grand-challenge.org/) and update the data paths at the top of each notebook.
