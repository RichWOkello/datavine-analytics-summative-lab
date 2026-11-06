# DataVine Analytics | Machine Learning Projects

**Wine classification · Agricultural feed similarity · Regional crime pattern clustering**

This repository contains three Python machine learning projects developed in a single executed Jupyter Notebook. The analysis follows a consistent workflow: Exploratory Data Analysis (EDA), preprocessing, Principal Component Analysis (PCA), model development, hyperparameter selection, evaluation, and interpretation.

**Developed by:** [Richard Okello (@RichWOkello)](https://github.com/RichWOkello)  
**Technical focus:** Data Science & Control and Instrumentation Engineering

## Project overview

| Project | Approach | Main results |
| --- | --- | --- |
| Wine classification | `StandardScaler` → PCA (≥95% explained variance) → tuned k-Nearest Neighbors (k-NN) with `GridSearchCV` | **95.6% test accuracy** (43/45 correct); classification report and confusion matrix |
| Agricultural feed similarity | Standardized chicken weights → one-component PCA → cosine similarity | Similarity-based recommendations for **6 feed types**, with PC1 distance used to resolve cosine similarity ties |
| Regional crime pattern clustering | PCA loading-based selection of 3 variables → two-component PCA → K-Means and Gaussian Mixture Models (GMM) | **4 K-Means clusters** based on an elbow heuristic; GMM evaluated using BIC, with an exploratory 2-component comparison |

The selected datasets represent instructional case studies rather than production deployment data. In particular, feed-level similarity is not evidence of causality, and historical `USArrests` statistics do not represent present-day conditions.

## Analysis workflow

### 1. Data preparation and EDA

Each dataset is loaded from its CSV file and assessed for data types, dimensions, missing values, duplicate rows, distributions, and descriptive statistics. `StandardScaler` is applied where appropriate, while model-specific preprocessing is kept inside the classification pipeline to limit data leakage.

### 2. Wine classification — PCA + k-NN

The wine features undergo a stratified train/test split. A scikit-learn pipeline integrates missing-value imputation, standardization, PCA with **95% retained variance**, and k-NN classification. `GridSearchCV` tunes the number of neighbors and distance metric. Model performance is evaluated using test accuracy, precision, recall, F1-score, and a confusion matrix.

### 3. Feed recommendation — PCA + cosine similarity

Chicken weights are standardized and projected onto one principal component. Feed-level representations are compared using cosine similarity, with absolute PC1 distance as a secondary ranking criterion. The notebook explains why cosine similarity in one dimension has limited ability to distinguish positive-valued representations.

### 4. Crime pattern analysis — K-Means + GMM

Three crime indicators are selected using PCA loading contributions. A two-component PCA projection is used for clustering. The elbow method and silhouette scores inform K-Means evaluation, while Bayesian Information Criterion (BIC) assesses GMM specifications. The notebook compares assignments with Adjusted Rand Index (ARI) and visualizes cluster profiles.

**GMM qualification:** The unrestricted BIC optimum was **one component**. The two-component GMM is included solely for an exploratory, multi-group comparison; it is not presented as the BIC-optimal model.

## Repository structure

```text
datavine-analytics-summative-lab/
├── .github/
│   └── workflows/
│       └── execute-notebook.yml
├── .gitignore
├── DataVine_Analytics_Summative_Lab.ipynb
├── USArrests.csv
├── chickwts.csv
├── wine.csv
├── README.md
├── GITHUB_SETUP.md
└── requirements.txt
```

The CSV files remain in the same directory as the notebook so relative file paths work without editing the code.

## Local setup

**Prerequisite:** Python 3.13 (used for the executed notebook) and an available terminal.

```bash
python -m venv .venv
```

Activate the virtual environment:

- **Windows PowerShell:** `.venv\Scripts\Activate.ps1`
- **macOS/Linux:** `source .venv/bin/activate`

Install the dependencies:

```bash
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
jupyter lab
```

Open `DataVine_Analytics_Summative_Lab.ipynb`. The notebook includes saved outputs, so its tables and figures are available in GitHub's notebook preview without executing the code.

### Reproducibility check

From the repository root:

```bash
jupyter nbconvert --to notebook --execute DataVine_Analytics_Summative_Lab.ipynb \
  --output DataVine_Verified.ipynb --ExecutePreprocessor.timeout=900
```

The `.github/workflows/execute-notebook.yml` workflow performs the same execution check for GitHub pushes and pull requests. Random state `42` is used for reproducibility in the applicable models.

## Interpretation notes

- The classification accuracy reflects performance on the supplied, held-out wine test set; it is not a guarantee of performance on other sources.
- PCA projections are used for dimensionality reduction and visualization; the principal components are mathematical combinations of original variables.
- Feed recommendations describe similarity in recorded outcomes, not controlled comparisons of feed effectiveness.
- Clustering results describe patterns within historical observations; the analyses do not establish causes of crime.

## Author

**Richard Okello** — [GitHub: @RichWOkello](https://github.com/RichWOkello)  
Data Science & Control and Instrumentation Engineering

For repository creation details, see [GITHUB_SETUP.md](GITHUB_SETUP.md).
