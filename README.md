# IoT Open-Set Intrusion Detection Capstone

This capstone project builds a multi-layer IoT intrusion detection pipeline for known and unknown attack detection. The workflow combines supervised learning, clustering, and autoencoder-based anomaly detection, then compares fusion strategies for open-set performance.

## Project Overview

The notebook:
- Loads processed parquet datasets from Google Drive
- Supports dev-sample mode and full-data mode
- Trains/evaluates:
  - Random Forest
  - XGBoost
  - KMeans
  - Autoencoder
- Evaluates known and unknown attack behavior
- Generates charts and layer-wise result files

## Dataset Files Expected

Place the processed files inside your project data folder:

- `devsample.parquet`
- `train.parquet`
- `val.parquet`
- `test.parquet`
- `unknownholdout.parquet`

## Expected Folder Layout in Google Drive

Use one of these folders:

- `/content/drive/MyDrive/Capstone/CapstoneIoT`
- `/content/drive/MyDrive/CapstoneIoT`

Inside that base folder, the notebook expects:

```text
CapstoneIoT/
├─ DataProcessed/
├─ ResultsLayer3/
├─ ResultsLayer4/
├─ ResultsLayer5/
└─ Figures/
```

## How to Run

### Option 1: Google Colab
1. Open `03_modelingCharts.ipynb` in Google Colab
2. Upload or place your dataset files in the expected Google Drive folder
3. In Cell 1, set:
   - `USE_DEV_SAMPLE = True` for the 50K sample
   - `USE_DEV_SAMPLE = False` for full-data mode
4. Run cells from top to bottom
5. Check generated outputs in:
   - `Figures/`
   - `ResultsLayer3/`
   - `ResultsLayer4/`
   - `ResultsLayer5/`

### Option 2: Jupyter Notebook / VS Code
1. Clone the repo
2. Create a Python virtual environment
3. Install dependencies:
  "pip install xgboost tensorflow scikit-learn seaborn imbalanced-learn"
4. Update the notebook path variables in Cell 1 so `BASE` points to your local project folder
5. Make sure processed parquet files exist inside the expected data folder
6. Run the notebook from top to bottom

## Main Dependencies

- numpy
- pandas
- matplotlib
- seaborn
- scikit-learn
- xgboost
- tensorflow
- pyarrow
- plotly
- kaleido
- ipywidgets
- nbformat

## Notes

- The notebook uses a locked autoencoder threshold based on the 95th percentile of benign validation reconstruction error.
- Results include per-class metrics, reconstruction error analysis, and fusion strategy comparisons.
- Large datasets may require Colab Pro or a local machine with more RAM.
