# Notebooks

All notebooks are stripped of outputs. Full versions with all outputs are available via Google Drive.

| # | Notebook | Description | Full version |
|---|---|---|---|
| 01 | [01_eda_preprocessing.ipynb](01_eda_preprocessing.ipynb) | Exploratory data analysis: dataset statistics, cell radius distribution, morphological diversity, spatial arrangement findings; point-to-mask annotation conversion | [Google Colab](https://colab.research.google.com/drive/1m-kak3zxljU7f_teOXn9Ym8xvA87zoMp?usp=sharing) |
| 02 | [02_tissue_segmentation.ipynb](02_tissue_segmentation.ipynb) | U-Net++ (SE-ResNet50 encoder) tissue segmentation model: training, hyperparameter sweep, sliding window inference, evaluation | [Google Colab](https://colab.research.google.com/drive/1aORR7NOgO3AG5n2NkpTfmb29Jolki2nm?usp=sharing) |
| 03 | [03_baseline_modeling.ipynb](03_baseline_modeling.ipynb) | Baseline cell detection: Attention U-Net (ResNet34 encoder) trained on small FoV only, post-processing pipeline, evaluation | [Google Colab](https://colab.research.google.com/drive/1wQav2hZuTMQnYmtFMGXVLPhnnX6IPRs7?usp=sharing) |
| 04 | [04_preprocessing_integration.ipynb](04_preprocessing_integration.ipynb) | Pre-processing integration: tumor probability map concatenated to small FoV as 4-channel input; model retrained end-to-end | [Google Colab](https://colab.research.google.com/drive/1ulbA7q2YMUm19MQRq2cZT9q3gbT0sprO?usp=sharing) |
| 05 | [05_postprocessing_integration.ipynb](05_postprocessing_integration.ipynb) | Post-processing integration: Gaussian-weighted tumor probability sampling used to refine per-cell confidence scores; no retraining required | [Google Colab](https://colab.research.google.com/drive/1EC8igZHOK9D5iidvuxPb2SrMJTayuEVQ?usp=sharing) |

> Google Drive links will be added once shared folders are set up.

## Environment

All notebooks were developed on **Google Colab** (Python 3, GPU runtime). Key dependencies are in [`../requirements.txt`](../requirements.txt).

To run locally, mount the OCELOT dataset from Google Drive or download it from the [official challenge page](https://ocelot2023.grand-challenge.org/datasets/) and update the data paths at the top of each notebook.
