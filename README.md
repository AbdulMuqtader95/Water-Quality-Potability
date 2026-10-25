# Water Quality Potability Prediction

A machine-learning project exploring whether water samples are classified as potable using measured water-quality features.

## Project overview

This project uses the `water_potability.csv` dataset to explore water-quality measurements and compare two classification approaches:

- Decision Tree Classifier
- K-Nearest Neighbors (KNN) Classifier

The notebook includes data inspection, exploratory visualizations, missing-value handling, train/test splitting, model selection with cross-validation, and evaluation on a held-out test set.

> **Important:** This is an educational classification project, not a certified water-safety test. Model predictions must not be used as the sole basis for deciding whether water is safe to drink.

## Repository structure

```text
Water-Quality-Potability/
├── data/
│   └── water_potability.csv
├── notebooks/
│   └── water_quality_prediction.ipynb
├── .gitignore
├── README.md
└── requirements.txt
```

## Dataset

The CSV contains 3,276 rows and 10 columns: nine numeric water-quality features and one target column, `Potability`.

Features:

- `ph`
- `Hardness`
- `Solids`
- `Chloramines`
- `Sulfate`
- `Conductivity`
- `Organic_carbon`
- `Trihalomethanes`
- `Turbidity`

Target:

- `Potability`: `0` or `1`, as encoded in the dataset.

The supplied dataset has missing values in `ph`, `Sulfate`, and `Trihalomethanes`. The notebook handles missing values inside each model pipeline so imputation statistics are learned from training data only, avoiding data leakage from the test set.

## Tools and libraries

- Python
- pandas and NumPy
- Matplotlib and Seaborn
- scikit-learn
- Jupyter Notebook

## Getting started

### 1. Clone the repository

```bash
git clone https://github.com/AbdulMuqtader95/Water-Quality-Potability.git
cd Water-Quality-Potability
```

### 2. Create and activate a virtual environment (recommended)

Windows:

```powershell
py -m venv .venv
.venv\Scripts\activate
```

macOS/Linux:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install dependencies

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### 4. Open the notebook

```bash
jupyter notebook
```

Open `notebooks/water_quality_prediction.ipynb` and run the cells from top to bottom. The notebook loads the dataset using a repository-relative path, so it does not depend on a personal Google Colab path.

## Methodology

1. Load and inspect the dataset.
2. Explore target balance, feature distributions, and correlations.
3. Split the data into training and test sets using a stratified split.
4. Build preprocessing/model pipelines. Missing values are imputed within each pipeline; KNN also uses feature scaling.
5. Tune Decision Tree and KNN hyperparameters using cross-validation on the training set.
6. Evaluate the selected models on the held-out test set using accuracy, precision, recall, F1-score, and confusion matrices.

The test set is kept separate from hyperparameter tuning to provide a more honest estimate of generalization performance.

## Results

Run the notebook to generate the metrics for the current environment and dependency versions. Results are intentionally not hard-coded in this README so that reported values match a fresh execution of the notebook.

## Limitations

- The target and measurements are used as provided in the dataset; this project does not validate the dataset against laboratory standards.
- Accuracy alone is not sufficient to assess water safety or model quality. Review precision, recall, F1-score, class balance, and the confusion matrix.
- A model prediction is not a substitute for certified water testing or public-health guidance.

## Reproducibility

The notebook uses fixed random seeds for the train/test split and cross-validation. Exact scores may still vary across library versions or environments.
