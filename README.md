# AquaSense — Water Quality & Potability Prediction

**Machine Learning Project | 2026–2027**  
**Ramdeobaba University, Nagpur | Department of Computer Science & Engineering**  
**Faculty Guide:** Prof. Sweta Jain  

---

## 🌊 Overview

**AquaSense** is an end-to-end educational machine learning system designed to analyze physical and chemical water quality parameters and predict water potability. The project covers data cleaning, exploratory data analysis, pipeline-based preprocessing, training and tuning seven distinct classification algorithms, cross-validation, threshold sensitivity analysis, unsupervised clustering, model explainability, and an interactive 12-page dashboard built with Gradio and Plotly.

> [!WARNING]
> **Educational & Experimental Disclaimer:** AquaSense is developed for academic study and research benchmarking. Model predictions are based on statistical patterns within the dataset and must **never** be used as a substitute for certified laboratory testing, biochemical assays, or official drinking-water quality standards (WHO / EPA).

---

## 👥 Project Team

| Name | Roll Number | Department |
|---|---|---|
| **Kirtikumar Mishra** | 12 | Computer Science & Engineering |
| **Vansh Mahalle** | 24 | Computer Science & Engineering |
| **Soumya Gawande** | 46 | Computer Science & Engineering |
| **Archit Deshpande** | 55 | Computer Science & Engineering |

---

## ✨ Key Features

- **Robust Data Preprocessing:** Automated schema validation, median imputation via `SimpleImputer` within scikit-learn pipelines to prevent data leakage, and feature scaling with `StandardScaler`.
- **7 Classification Algorithms:**
  1. **Logistic Regression** (L2-regularized linear classifier)
  2. **Support Vector Machine (SVM)** (Non-linear RBF kernel with probability calibration)
  3. **K-Nearest Neighbors (KNN)** (Distance-weighted local neighbor classifier)
  4. **Decision Tree** (Gini-impurity tree classifier)
  5. **Random Forest** (Ensemble bagging classifier optimized with `GridSearchCV`)
  6. **Linear Discriminant Analysis (LDA)** (Generative linear decision boundary)
  7. **Quadratic Discriminant Analysis (QDA)** (Quadrative class-covariance decision surface)
- **Rigorous Evaluation:**
  - Evaluated on a held-out stratified test set (80/20 split, `random_state=42`).
  - Metrics tracked: Accuracy, Precision, Recall, F1-Score, Balanced Accuracy, and ROC-AUC.
  - 5-Fold Stratified Cross-Validation on the training set to evaluate stability and variance.
  - Confusion matrices and per-class classification reports.
  - Combined Plotly ROC curve comparison across all seven classifiers.
- **Decision Threshold Experiments:** Precision-recall-F1 tradeoff curves across classification probability thresholds from 0.10 to 0.90.
- **Unsupervised Exploration:** K-Means clustering ($k=2$) fit on unlabeled features with 2D Principal Component Analysis (PCA) projection.
- **Linear Regression Baseline:** Numeric target regression baseline illustrating boundary characteristics and separating classification from regression.
- **Explainability & Feature Influence:** Extraction and visualization of model weights, odds ratios, and tree-based Gini feature importances.
- **Interactive 12-Page Gradio Dashboard:** Full web-based analytical dashboard featuring responsive Plotly graphs and a real-time "What-If" sample simulator.

---

## 📊 Dataset & Schema

The model analyzes water samples based on nine physicochemical water quality metrics.

- **Dataset Source:** [Kaggle — Water Probability / Potability Dataset](https://www.kaggle.com/datasets/bsf23ooo354humaira/water-probability)
- **File:** [`water_potability.csv`](water_potability.csv)

### Feature Descriptions

| Feature | Description | Reference Range / Units |
|---|---|---|
| `ph` | Acidity or alkalinity level of the water | 0 – 14 (WHO recommended: 6.5 – 8.5) |
| `Hardness` | Capacity of water to precipitate soap | mg/L (Calcium & Magnesium salts) |
| `Solids` | Total dissolved solids (TDS) | ppm / mg/L |
| `Chloramines` | Disinfectant agent concentration | ppm |
| `Sulfate` | Dissolved sulfate mineral concentration | mg/L |
| `Conductivity` | Electrical conductivity | μS/cm |
| `Organic_carbon` | Total organic carbon content (TOC) | ppm |
| `Trihalomethanes` | Disinfection by-products (THMs) | μg/L |
| `Turbidity` | Measure of light-emitting properties / clarity | NTU (Nephelometric Turbidity Units) |
| `Potability` | **Target label**: `1` = Potable (Safe), `0` = Non-potable (Unsafe) | Binary |

---

## 🛠️ Technology Stack

- **Core Language:** Python 3.10+
- **Environment:** Jupyter Notebook / Google Colab
- **Data Manipulation:** `pandas`, `numpy`
- **Machine Learning & Preprocessing:** `scikit-learn` (`Pipeline`, `GridSearchCV`, `SimpleImputer`, `StandardScaler`)
- **Interactive Visualizations:** `plotly` (express & graph_objects)
- **Static Plotting:** `matplotlib`, `seaborn`
- **Interactive UI / Dashboard:** `gradio`

---

## 🚀 How to Run

### Option 1: Running in Google Colab (Recommended)

1. Open [`AquaSense.ipynb`](file:///c:/Users/kiran/Downloads/Aqua-Sense/AquaSense.ipynb) in **Google Colab**.
2. Run **Section 1: Install required libraries** to install `gradio`, `plotly`, `scikit-learn`, `pandas`, `numpy`, `matplotlib`, and `seaborn`.
3. Run **Section 2 & 3: Import libraries and upload dataset**. When prompted by the Colab upload widget, select [`water_potability.csv`](file:///c:/Users/kiran/Downloads/Aqua-Sense/water_potability.csv).
4. Run all cells sequentially through data validation, EDA, model training, evaluation, clustering, and baseline comparisons.
5. Launch **Section 17: Launch the interactive AquaSense dashboard** to run the 12-page Gradio UI directly within the notebook (or via the generated shareable link).
6. (Optional) Run **Section 18: Export project results** to download the evaluation summary CSVs.

### Option 2: Running Locally

1. Clone this repository:
   ```bash
   git clone https://github.com/sycno15/AquaSense.git
   cd AquaSense
   ```
2. Install required dependencies:
   ```bash
   pip install gradio plotly scikit-learn pandas numpy matplotlib seaborn jupyter
   ```
3. Start the Jupyter Notebook server:
   ```bash
   jupyter notebook AquaSense.ipynb
   ```
4. Run all notebook cells.

---

## 🖥️ Interactive Dashboard Breakdown

The integrated Gradio dashboard provides an 11-page guided exploration plus a dedicated Overview:

1. **Overview:** Project summary, metric descriptions, dataset statistics, and quick-start instructions.
2. **Logistic Regression:** Linear classification metrics, confusion matrix, threshold tuning, and feature odds ratios.
3. **SVM (RBF):** Non-linear support vector machine performance and decision boundaries.
4. **K-Nearest Neighbors:** Distance-weighted local neighborhood metrics and predictions.
5. **Decision Tree:** Single decision-tree metrics and Gini feature importances.
6. **Random Forest:** Hyperparameter-tuned ensemble evaluation with feature importance breakdown.
7. **Linear Discriminant Analysis:** Generative linear boundary classification results.
8. **Quadratic Discriminant Analysis:** Quadratic decision boundary results for differing class covariances.
9. **K-Means Clustering:** Unsupervised cluster distributions and 2D PCA visual projections.
10. **Linear Regression:** Numeric baseline analysis contrasting regression against classification.
11. **Model Comparison & Selection:** Side-by-side leaderboard across all seven classifiers, multi-model ROC curves, and cross-validation stability scores.
12. **Explainability & Insights:** Global feature influence summaries and interactive **"What-If"** sample prediction simulator.

---

## 📁 Output Artifacts

When running the optional export cell, the following evaluation reports are generated:

- `aquasense_classifier_evaluation.csv`: Test-set metrics (Accuracy, Precision, Recall, F1, Balanced Accuracy, ROC-AUC) across all 7 classifiers.
- `aquasense_cross_validation.csv`: 5-fold stratified cross-validation mean and standard deviation scores.
- `aquasense_threshold_experiments.csv`: Threshold sensitivity grid (0.10 to 0.90) for all probabilistic models.
- `aquasense_prepared_dataset.csv`: Processed dataset with cleaned features and potability indicators.

---

## 📜 License & Academic Integrity

This project is submitted as part of the academic curriculum for the Department of Computer Science & Engineering at **Ramdeobaba University, Nagpur**. It is intended strictly for academic, research, and educational purposes.
