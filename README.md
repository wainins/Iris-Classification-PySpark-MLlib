# Iris Classification with PySpark MLlib

<p align="center">
  <img width="100%" alt="Project Banner" src="https://github.com/user-attachments/assets/f2f67a2c-239f-449f-9de8-32c39f9fe67b" />
</p>

<p align="center">
  <a href="#overview">Overview</a> •
  <a href="#dataset">Dataset</a> •
  <a href="#methodology">Methodology</a> •
  <a href="#results">Results</a> •
  <a href="#run-project">Run Project</a>
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

## Methodology
### Models

Three classification algorithms were implemented and compared:

| Model | Purpose |
|---|---|
| **Logistic Regression** | Linear classification model used as a baseline |
| **Decision Tree** | Tree-based model that captures nonlinear decision boundaries |
| **Random Forest** | Ensemble of decision trees designed to improve predictive performance and reduce overfitting |

### Model Tuning

Each model was optimized using **5-fold cross-validation** and **grid search** over selected hyperparameters:

- **Logistic Regression:** `regParam`, `elasticNetParam`, `maxIter`
- **Decision Tree:** `maxDepth`, `impurity`, `minInstancesPerNode`
- **Random Forest:** `numTrees`, `maxDepth`, `maxBins`

### Evaluation Metrics

Models were evaluated using **Accuracy, Weighted Precision, Weighted Recall and F1-Score** to assess overall classification performance across the three classes.

<kbd>🎯 Accuracy</kbd> &nbsp; 
<kbd>🔍 Weighted Precision</kbd> &nbsp; 
<kbd>📈 Weighted Recall</kbd> &nbsp; 
<kbd>⚖️ F1-Score</kbd>

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
├── 8. Comparative Analysis
└── 9. Cleanup
```

## Results

| Model               | Accuracy | Precision | Recall | F1-Score |
|---------------------|----------|-----------|--------|----------|
| Logistic Regression |  0.97    |  0.97     |  0.97  |  0.97    |
| Decision Tree       |  0.91    |  0.94     |  0.91  |  0.91    |
| Random Forest       |  0.97     | 0.97     |  0.97  |  0.97    |

> [!NOTE]
> ### Key Findings
> - **Top Performers:** Logistic Regression and Random Forest achieved the strongest overall test performance.
> - **Feature Importance:** Petal length and petal width were the most influential features for classification.
> - **Class Separability:** Setosa was easily separated, while most classification errors occurred between Versicolor and Virginica.

### Confusion Matrix

The confusion matrices show the classification performance of each model across the three Iris species. Most errors occur between **Versicolor** and **Virginica**, while **Setosa** is more easily distinguished.

#### Logistic Regression

<img width="913" height="646" alt="Image" src="https://github.com/user-attachments/assets/10fe19ba-e3df-4cb3-a188-0473c84b606a" />

#### Decision Tree

<img width="885" height="646" alt="Image" src="https://github.com/user-attachments/assets/c5272263-7a35-4037-bb73-b4975512eabb" />

#### Random Forest

<img width="878" height="646" alt="Image" src="https://github.com/user-attachments/assets/d3a5f74f-8b82-47f5-ae59-3859397bead5" />

### Feature Importance

Random Forest feature importance indicates that **petal measurements contributed most strongly to the classification**, while the sepal measurements had comparatively lower importance.

<img width="1682" height="558" alt="Image" src="https://github.com/user-attachments/assets/1e6ad3c6-85e4-440e-b6ab-7fb5a680ecca" />

## Run Project

This project was developed in **Google Colab** using PySpark, providing a convenient environment for running Apache Spark without a local Spark installation.

### Environment Used

![PySpark](https://img.shields.io/badge/PySpark-4.0.2-E25A1C?logo=apachespark&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-2.2.2-150458?logo=pandas&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-3.10.0-11557C?logo=plotly&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-0.13.2-4C72B0&logo=python&logoColor=white)
![Google Colab](https://img.shields.io/badge/Google%20Colab-F9AB00?logo=googlecolab&logoColor=white)

### Google Colab

1. Download `iris_classification_pyspark.ipynb`.
2. Open [Google Colab](https://colab.research.google.com/).
3. Upload the notebook.
4. Connect to a runtime using **Runtime → Connect**.
5. Install the required libraries:

```python
!pip install pyspark pandas matplotlib seaborn
```
6. Run the notebook cells sequentially.
---

**Alternative: Local Jupyter Notebook**

For local execution, ensure Java JDK 8 or 11 is available for the Spark runtime.

1. Download the notebook file :  `iris_classification_pyspark.ipynb`
2. Open the notebook in Jupyter
3. Install the required libraries :

```python
!pip install pyspark pandas matplotlib seaborn
```

<br> 

---

<p align="center">
  <i>This project was completed as part of the STQD6324 Data Management course at Universiti Kebangsaan Malaysia.</i>
</p>

