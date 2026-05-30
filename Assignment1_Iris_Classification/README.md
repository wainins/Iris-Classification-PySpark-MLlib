# Iris Classification with PySpark MLlib

A machine learning project demonstrating multiclass classification using Apache Spark MLlib. This project implements and compares three classification algorithms on the classic Iris dataset.

## Overview

This project showcases a complete ML workflow in PySpark:
- Data loading and preprocessing
- Feature engineering with VectorAssembler
- Model training with cross-validation and hyperparameter tuning
- Performance evaluation using multiple metrics
- Comparative analysis of different algorithms

## Project Flow

This project follows a structured machine learning pipeline:

Raw Data → Preprocessing → Feature Engineering → Model Training → Hyperparameter Tuning → Evaluation → Comparison


## Dataset

**Iris Dataset** (Fisher, 1936)
- **Samples**: 150 iris flowers
- **Features**: 4 continuous measurements
  - Sepal length (cm)
  - Sepal width (cm)
  - Petal length (cm)
  - Petal width (cm)
- **Target**: 3 species (Setosa, Versicolor, Virginica)
- **Source**: (https://raw.githubusercontent.com/plotly/datasets/master/iris-data.csv)

## Methodology

### Algorithms Implemented
1. **Logistic Regression** - Multinomial classification with regularization
2. **Decision Tree** - Single tree with tuned depth and impurity
3. **Random Forest** - Ensemble of trees for improved generalization

### Hyperparameter Tuning
Each model is optimized using:
- **5-fold Cross-Validation** for robust performance estimation
- **Grid Search** over key hyperparameters:
  - Logistic Regression: `regParam`, `elasticNetParam`, `maxIter`
  - Decision Tree: `maxDepth`, `impurity`, `minInstancesPerNode`
  - Random Forest: `numTrees`, `maxDepth`, `maxBins`
  

### Evaluation Metrics
- Accuracy
- Weighted Precision
- Weighted Recall
- F1-Score

## Results Summary

| Model               | Accuracy | Precision | Recall | F1-Score |
|---------------------|----------|-----------|--------|----------|
| Decision Tree       | ~0.93    | ~0.93     | ~0.93  | ~0.93    |
| Random Forest       | ~0.97    | ~0.97     | ~0.97  | ~0.97    |
| Logistic Regression | ~0.97    | ~0.97     | ~0.97  | ~0.97    |


### Key Findings

1. **Random Forest** and **Logistic Regression** achieved the highest accuracy, both approaching 97%.
2. **Petal measurements** (length and width) are the most important features for classification.
3. **Setosa** is perfectly separable; most misclassifications occur between Versicolor and Virginica.

## Reproduce the Analysis
### Prerequisites
