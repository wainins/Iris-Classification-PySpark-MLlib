# Iris Classification with PySpark MLlib

<p align="center">
  <img width="100%" alt="Project Banner" src="https://github.com/user-attachments/assets/f2f67a2c-239f-449f-9de8-32c39f9fe67b" />
</p>

<p align="center">
  <a href="#overview">Overview</a> •
  <a href="#dataset">Dataset</a> •
  <a href="#methodology">Methodology</a> •
  <a href="#results">Results</a> •
  <a href="#reproduce-the-analysis">Run Project</a>
</p>

> **Academic Project — STQD6324 Data Management**

> A multiclass classification project using PySpark MLlib to compare Logistic Regression, Decision Tree and Random Forest models on the Iris dataset, with cross-validation and hyperparameter tuning.

---


## Overview

This project demonstrates an end-to-end multiclass classification workflow using PySpark MLlib:

```mermaid
flowchart LR
    A[Data Loading & Preprocessing] --> B[Feature Engineering]
    B --> C[Train-Test Split]
    C --> D[Model Training & Hyperparameter Tuning]
    D --> E[Performance Evaluation]
    E --> F[Model Comparison]
```

## Dataset

**Iris Dataset** (Fisher, 1936)

- **Source**: [GitHub](https://raw.githubusercontent.com/plotly/datasets/master/iris-data.csv)↗️
- **Samples**: 150 iris flowers
- **Features**: 4 continuous measurements
  - Sepal length (cm)
  - Sepal width (cm)
  - Petal length (cm)
  - Petal width (cm)
- **Target**: `species`
  
| Setosa | Versicolor | Virginica |
|---------|---------|---------|
| <img width="2000" height="2000" alt="Image" src="https://github.com/user-attachments/assets/5582d309-3d13-4974-8ccf-8757a5d985ae" /> | <img width="2000" height="2000" alt="Image" src="https://github.com/user-attachments/assets/a1a35740-46d2-409d-94ba-c18c1012abaf" /> | <img width="2000" height="2000" alt="Image" src="https://github.com/user-attachments/assets/356dd710-ee74-4582-92bc-171a65e25c54" /> |

<br>

### Models

Three classification algorithms were implemented and compared:

| Model | Purpose |
|---|---|
| **Logistic Regression** | Linear classification model used as a baseline |
| **Decision Tree** | Tree-based model that captures nonlinear decision boundaries |
| **Random Forest** | Ensemble of decision trees designed to improve predictive performance and reduce overfitting |

<br>

### Model Tuning

Each model was optimized using **5-fold cross-validation** and **grid search** over selected hyperparameters:

- **Logistic Regression:** `regParam`, `elasticNetParam`, `maxIter`
- **Decision Tree:** `maxDepth`, `impurity`, `minInstancesPerNode`
- **Random Forest:** `numTrees`, `maxDepth`, `maxBins`

<br>

### Evaluation Metrics

Models were evaluated using **Accuracy, Weighted Precision, Weighted Recall and F1-Score** to assess overall classification performance across the three classes.

<kbd>🎯 Accuracy</kbd> &nbsp; 
<kbd>🔍 Weighted Precision</kbd> &nbsp; 
<kbd>📈 Weighted Recall</kbd> &nbsp; 
<kbd>⚖️ F1-Score</kbd>

<br> 


```markdown
### Notebook Structure

```yaml
iris_classification_pyspark.ipynb
├── 1. Environment Setup and Imports
├── 2. Load Iris Dataset
├── 3. Data Preprocessing
├── 4. Train-Test Split
├── 5. Model Implementation with Hyperparameter Tuning
│   ├── Logistic Regression
│   ├── Decision Tree
│   └── Random Forest
├── 6. Model Evaluation
├── 7. Predictions on Test Data
└── 8. Comparative Analysis
└── 9. Cleanup
```

<br>

## Results

| Model               | Accuracy | Precision | Recall | F1-Score |
|---------------------|----------|-----------|--------|----------|
| Logistic Regression | ~0.97    | ~0.97     | ~0.97  | ~0.97    |
| Decision Tree       | ~0.91    | ~0.94     | ~0.91  | ~0.91    |
| Random Forest       | ~0.97    | ~0.97     | ~0.97  | ~0.97    |

> [!NOTE]
> ### Key Findings
> - **Top Performers:** Logistic Regression and Random Forest achieved the strongest overall test performance.
> - **Feature Importance:** Petal length and petal width were the most influential features for classification.
> - **Class Separability:** Setosa was easily separated, while most classification errors occurred between Versicolor and Virginica.

### Confusion Matrix

[image]

### Feature Importance

[image]
   
<br>


## Reproduce the Analysis

This project was developed using **Google Colab** to simplify the execution of Apache Spark (PySpark) without requiring local installation of Java or Spark.

### Environment Used

![PySpark](https://img.shields.io/badge/PySpark-4.0.2-E25A1C?logo=apachespark&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-2.2.2-150458?logo=pandas&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-3.10.0-11557C?logo=plotly&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-0.13.2-4C72B0&logo=python&logoColor=white)
![Google Colab](https://img.shields.io/badge/Google%20Colab-F9AB00?logo=googlecolab&logoColor=white)

### Execution Guide

**Recommended: Google Colab**

1. Download the notebook file :  `iris_classification_pyspark.ipynb`
2. Go to: [Google Colab](https://colab.research.google.com/)↗️ 
3. Upload the notebook file
4. Make sure to connect runtime: `Runtime → Connect`
5. Install required libraries (if needed):

```python
!pip install pyspark pandas matplotlib seaborn
```
---

**Alternative: Local Jupyter Notebook**

To run locally, ensure you have **Java JDK 8 or 11** installed for the Spark runtime environment.

1. Download the notebook file :  `iris_classification_pyspark.ipynb`
2. Launch the notebook file in Jupyter Notebook
3. Install required libraries :

```python
!pip install pyspark pandas matplotlib seaborn
```

<br> 

---

<p align="center">
  <i>This project was completed as part of the STQD6324 Data Management course at Universiti Kebangsaan Malaysia.</i>
</p>

