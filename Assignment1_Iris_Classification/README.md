# Iris Classification with PySpark MLlib

<img width="1584" height="396" alt="Image" src="https://github.com/user-attachments/assets/f2f67a2c-239f-449f-9de8-32c39f9fe67b" />

A machine learning project demonstrating multiclass classification using Apache Spark MLlib. This project implements and compares three classification algorithms on the classic Iris dataset.


## Overview

This project showcases a complete ML workflow in PySpark:

```mermaid
flowchart LR
    A[Data Loading & Preprocessing] --> B[Feature Engineering]
    B --> C[Train-Test Split]
    C --> D[Model Training & Hyperparameter Tuning]
    D --> E[Performance Evaluation]
    E --> F[Model Comparison]
```

## 📂 Project Structure

- `iris_classification_pyspark.ipynb`
  - 1. Environment Setup and Imports
  - 2. Load the Iris dataset
  - 3. Data Preprocessing
  - 4. Train-Test Split
  - 5. Model Implementation with Hyperparameter Tuning
    - Logistic Regression
    - Decision Tree
    - Random Forest
  - 6. Model Evaluation
  - 7. Predictions on Test Data
  - 8. Comparative Analysis
  - 9. Cleanup

## Dataset

**Iris Dataset** (Fisher, 1936)
- **Source**: [GitHub](https://raw.githubusercontent.com/plotly/datasets/master/iris-data.csv)↗️
- **Samples**: 150 iris flowers
- **Features**: 4 continuous measurements
  - Sepal length (cm)
  - Sepal width (cm)
  - Petal length (cm)
  - Petal width (cm)
- **Target**:
  
| Setosa | Versicolor | Virginica |
|---------|---------|---------|
| <img width="2000" height="2000" alt="Image" src="https://github.com/user-attachments/assets/5582d309-3d13-4974-8ccf-8757a5d985ae" /> | <img width="2000" height="2000" alt="Image" src="https://github.com/user-attachments/assets/a1a35740-46d2-409d-94ba-c18c1012abaf" /> | <img width="2000" height="2000" alt="Image" src="https://github.com/user-attachments/assets/356dd710-ee74-4582-92bc-171a65e25c54" /> |

<br>

## Methodology

### Algorithms Implemented
| Logistic Regression | Decision Tree | Random Forest |
|---------|---------|---------|

<br>

### Hyperparameter Tuning
Each model is optimized using:
- **5-fold Cross-Validation** for robust performance estimation
- **Grid Search** over key hyperparameters:
  - Logistic Regression: `regParam`, `elasticNetParam`, `maxIter`
  - Decision Tree: `maxDepth`, `impurity`, `minInstancesPerNode`
  - Random Forest: `numTrees`, `maxDepth`, `maxBins`

<br>

### Evaluation Metrics
<kbd>🎯 Accuracy</kbd> &nbsp; 
<kbd>🔍 Weighted Precision</kbd> &nbsp; 
<kbd>📈 Weighted Recall</kbd> &nbsp; 
<kbd>⚖️ F1-Score</kbd>

<br> 

## Results Summary

| Model               | Accuracy | Precision | Recall | F1-Score |
|---------------------|----------|-----------|--------|----------|
| Logistic Regression | ~0.97    | ~0.97     | ~0.97  | ~0.97    |
| Decision Tree       | ~0.91    | ~0.94     | ~0.91  | ~0.91    |
| Random Forest       | ~0.97    | ~0.97     | ~0.97  | ~0.97    |


### Key Findings

1. **Random Forest** and **Logistic Regression** achieved the highest observed performance across all evaluation.
2. **Petal measurements** (length and width) are the most important features for classification.
3. **Setosa** is perfectly separable. Most misclassifications occur between Versicolor and Virginica.

<br>

## Reproduce the Analysis
### Prerequisites
![PySpark](https://img.shields.io/badge/PySpark-MLlib-orange)
![Python](https://img.shields.io/badge/Python-3.10-blue)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Processing-150458)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-11557c)
![Seaborn](https://img.shields.io/badge/Seaborn-Statistics-2E8B57)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626)

### Installation
This project was developed using **Google Colab** to simplify the execution of Apache Spark (PySpark) without requiring local installation of Java or Spark.

1. Open the notebook file:  
`iris_classification_pyspark.ipynb`

2. Open Google Colab:  
https://colab.research.google.com/

3. Upload the notebook and connect runtime:
- `Runtime → Connect`

### Install Required Libraries

```bash id="bash2"
pip install pyspark pandas matplotlib seaborn
