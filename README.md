# Performance Analysis of Tree-Based Regressors in Predicting Protein Tertiary Structure Deviation

## Overview

This project investigates the performance of different tree-based regression algorithms in predicting protein tertiary structure deviation using physicochemical descriptors.

The study uses the *Physicochemical Properties of Protein Tertiary Structure* dataset from the UCI Machine Learning Repository. The target variable is Root Mean Square Deviation (RMSD), which measures structural deviation.

The primary objective is to explore how different tree-based ensemble methods capture nonlinear relationships between physicochemical descriptors and RMSD, and to compare their predictive performance through systematic experimentation.

## Objectives

- Explore relationships between physicochemical features and RMSD.
- Investigate nonlinear regression approaches for predicting protein structural deviation.
- Compare Random Forest, XGBoost, and Extra Trees regressors.
- Experiment with different model configurations and hyperparameters.
- Evaluate and rank configurations primarily using the coefficient of determination (R²).
- Use additional regression metrics to provide a broader view of prediction errors.
- Visualize performance differences across model configurations.

## Dataset

**Dataset:** Physicochemical Properties of Protein Tertiary Structure

**Source:** [UCI Machine Learning Repository](https://doi.org/10.24432/C5QW3H)

The dataset contains approximately 45,730 samples and nine input features describing physicochemical properties. The regression target is RMSD.

The analysis investigates whether these descriptors can capture useful nonlinear relationships for predicting structural deviation.

### Dataset Citation

Rana, P. (2013). *Physicochemical Properties of Protein Tertiary Structure*. UCI Machine Learning Repository. https://doi.org/10.24432/C5QW3H

#### BibTeX

```bibtex
@misc{rana2013protein,
  author    = {Rana, Prashant},
  title     = {Physicochemical Properties of Protein Tertiary Structure},
  year      = {2013},
  publisher = {UCI Machine Learning Repository},
  doi       = {10.24432/C5QW3H},
  url       = {https://doi.org/10.24432/C5QW3H}
}
```

## Models Evaluated

### Tree-Based Regressors

- **Random Forest Regressor:** Combines predictions from multiple decision trees to improve predictive stability.
- **XGBoost Regressor:** Uses gradient boosting, sequentially fitting trees to improve on previous predictions.
- **Extra Trees Regressor:** Introduces additional randomization during tree construction and combines predictions from an ensemble of trees.

### Additional Experiment

A Multilayer Perceptron (MLP) regressor was also investigated to explore whether a neural network could capture nonlinear relationships between the physicochemical descriptors and RMSD.

## Methodology

The project follows an iterative experimental workflow:

1. **Exploratory Data Analysis:** Examined feature correlations and their relationships with the target variable.
2. **Model Selection:** Investigated nonlinear regression methods because the observed relationships suggested that linear models might not adequately capture the underlying patterns.
3. **Hyperparameter Experiments:** Tested multiple configurations, varying parameters such as the number of estimators, tree depth, and other model-specific settings.
4. **Performance Evaluation:** Compared predictions using R² as the primary metric, supported by error-based metrics.
5. **Model Comparison:** Ranked configurations and visualized the strongest results for each tree-based model family.

## Evaluation Metrics

The primary evaluation metric was the **coefficient of determination (R²)**. It was used mainly to compare configurations and identify the best-performing models.

Additional metrics were calculated to provide complementary information about prediction errors.

| Metric | Purpose | Preferred Direction |
|---|---|---|
| R² | Measures the proportion of target variance explained by the model. | Higher |
| MAE | Measures the average absolute prediction error. | Lower |
| RMSE | Penalizes larger prediction errors more heavily. | Lower |
| Normalized MAE (NMAE) | Expresses MAE relative to the observed target range as a percentage. | Lower |
| Within ±1 | Percentage of predictions within 1 RMSD unit of the actual value. | Higher |
| Within ±2 | Percentage of predictions within 2 RMSD units of the actual value. | Higher |

Although all these metrics were considered, **R² was the main criterion used to compare and rank model configurations**. The other metrics provided additional context about prediction errors.

## Results and Observations

Among the evaluated tree-based regression approaches, **Extra Trees achieved the strongest R² performance on the held-out test set, with an R² score of approximately 0.666**.

The experiments revealed several observations:

- Extra Trees outperformed the tested Random Forest and XGBoost configurations in terms of R².
- XGBoost's sequential boosting strategy did not produce the highest R² on this dataset.
- The additional randomization used by Extra Trees may be beneficial for this particular prediction task.
- Testing multiple configurations demonstrated that algorithm choice alone does not determine performance; model settings and dataset characteristics also matter.

The possibility of overfitting was considered when interpreting the boosting results, although confirming this explanation would require further analysis of training performance and generalization.

The accompanying Jupyter Notebook contains the experimental configurations, metric tables, and visualizations used to compare model performance.

## Project Structure

```text
Protein Tertiary Structure Deviation Prediction/
├── ProteinTertiaryStructureDeviationAnalysis.ipynb
├── protein.csv
├── requirements.txt
├── README.md
└── .gitignore
```

## Installation and Usage

### 1. Clone the repository

```bash
git clone <repository-url>
cd "<repository-directory>"
```

### 2. Create and activate a virtual environment

```bash
python -m venv ptenv
source ptenv/bin/activate
```

### 3. Install dependencies

Install the required Python packages using the included requirements file:

```bash
pip install -r requirements.txt
```

### 4. Launch Jupyter Notebook

```bash
jupyter notebook
```

Open `ProteinTertiaryStructureDeviationAnalysis.ipynb` and execute the cells in order.

Ensure that `protein.csv` is available at the path expected by the notebook.

## Limitations and Future Work

- Evaluate model stability using cross-validation.
- Investigate generalization to proteins not represented in the training data.
- Explore feature importance and the contribution of individual physicochemical descriptors.
- Conduct further hyperparameter optimization.
- Investigate additional regression algorithms and compare their performance using the same evaluation protocol.

## Technologies Used

- Python
- NumPy
- Pandas
- Matplotlib
- Scikit-learn
- XGBoost
- Jupyter Notebook

## Conclusion

This project explores the use of nonlinear machine learning methods for predicting protein tertiary structure deviation from physicochemical descriptors.

Through iterative experimentation and systematic comparison, the study found that Extra Trees achieved the highest R² among the evaluated tree-based configurations on the held-out test set.

The project emphasizes empirical model evaluation, hyperparameter experimentation, and the use of R² as the primary metric for comparing regression performance, supported by additional error-based measures.
