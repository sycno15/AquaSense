# AquaSense — Water Quality & Potability Prediction

AquaSense is an educational machine-learning project for exploring water-quality measurements and studying how different models classify water samples as potable or non-potable. It includes data exploration, model evaluation, clustering, a regression baseline, and an interactive Gradio dashboard.

> **Note:** AquaSense is for learning and experimentation. A model prediction cannot confirm that water is safe to drink. Drinking-water safety must be established through suitable laboratory testing and applicable standards.

## Project features

- Explore the dataset, including label distribution, missing values, feature distributions, and correlations.
- Prepare and validate the data, handle missing feature values with median imputation, and create a stratified train/test split.
- Train and compare six classification models:
  - Logistic Regression
  - Support Vector Machine (RBF kernel)
  - K-Nearest Neighbors
  - Decision Tree
  - Linear Discriminant Analysis
  - Quadratic Discriminant Analysis
- Evaluate classifiers with accuracy, precision, recall, F1-score, balanced accuracy, ROC-AUC, confusion matrices, ROC curves, and 5-fold cross-validation.
- Experiment with classification thresholds and review their effect on evaluation metrics.
- Explore samples with K-Means clustering and PCA visualizations.
- Review a Linear Regression baseline separately from the classification models.
- Inspect model coefficients or feature influence and run what-if sample experiments.
- Use the interactive dashboard to explore the project through 11 pages.
- Export evaluation tables and the prepared dataset as CSV files.

Random Forest, Extra Trees, and Gradient Boosting are not part of the selected six classifiers.

## Dataset

The notebook expects a CSV file named `water_potability.csv` with these columns:

| Column | Description |
|---|---|
| `ph` | pH measurement |
| `Hardness` | Water hardness |
| `Solids` | Total dissolved solids measurement |
| `Chloramines` | Chloramines measurement |
| `Sulfate` | Sulfate measurement |
| `Conductivity` | Electrical conductivity measurement |
| `Organic_carbon` | Organic carbon measurement |
| `Trihalomethanes` | Trihalomethanes measurement |
| `Turbidity` | Turbidity measurement |
| `Potability` | Target label: `1` for potable and `0` for non-potable |

The notebook checks that the required columns are present, converts values to numeric form, removes rows without a valid target label, and imputes missing feature measurements inside model pipelines where applicable.

## Technology stack

- Python
- Jupyter Notebook / Google Colab
- pandas and NumPy for data handling
- scikit-learn for machine learning and evaluation
- Matplotlib and Seaborn for plotting support
- Plotly for interactive charts
- Gradio for the interactive dashboard

## How to run

The notebook is designed to run in **Google Colab**.

1. Open `Water_Potability_Analysis.ipynb` in Google Colab.
2. Run the dependency-installation cell.
3. Run the notebook cells from top to bottom.
4. When prompted, upload `water_potability.csv`.
5. Continue through the data validation, exploration, training, evaluation, clustering, and regression sections.
6. Run the dashboard cell to launch the Gradio interface.
7. Run the optional export cell to create the CSV output files.

If the runtime is restarted, run the notebook from the beginning before launching the dashboard because it uses variables and trained models created by earlier cells.

## Dashboard pages

1. Overview
2. Logistic Regression
3. SVM (RBF)
4. K-Nearest Neighbors
5. Decision Tree
6. Linear Discriminant Analysis
7. Quadratic Discriminant Analysis
8. K-Means Clustering
9. Linear Regression
10. Model Comparison & Selection
11. Explainability & Insights

## Evaluation approach

The notebook uses a reproducible random seed (`42`) and a stratified 80/20 train/test split for classification. It also uses stratified 5-fold cross-validation on the training portion to inspect model stability. Results can vary if the dataset or model settings change, so use the generated metrics and plots rather than assuming one model is always best.

K-Means is used for unsupervised exploration, not as a potability classifier. Linear Regression is included as a separate baseline with the binary target treated as numeric; its outputs should not be interpreted as calibrated probabilities.

## Exported files

The optional export section creates:

- `aquasense_classifier_evaluation.csv`
- `aquasense_cross_validation.csv`
- `aquasense_threshold_experiments.csv`
- `aquasense_prepared_dataset.csv`

The notebook prints the filenames after creating them. The download statements are commented out by default and can be enabled individually in Google Colab when needed.

## Limitations

- The models learn patterns in the supplied dataset and may not generalize to all water sources or conditions.
- Metrics such as accuracy and F1-score do not establish that a prediction is safe for real-world use.
- Feature influence is not proof of causation, and feature-importance measures are not directly comparable across every model.
- The Linear Regression section is an educational baseline, not a replacement for classification or laboratory analysis.

## Team

- Kirtikumar Mishra
- Vansh Mahalle
- Soumya Gawande
- Archit Deshpande
