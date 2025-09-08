# DA5401 Assignment 3 - Clustering Based Sampling

## Overview
This repository contains the implementation of clustering-based sampling techniques for handling class imbalance in fraud detection datasets.

## Dataset
- Credit Card Fraud Detection Dataset
- Highly imbalanced binary classification problem
- 284,807 transactions with extreme class imbalance
- **Note**: The `creditcard.csv` file (143.84 MB) is not included in this repository due to GitHub size limits. Please ensure you have this file in your local directory before running the notebook.

## Objectives
1. Explore and analyze class imbalance in the dataset
2. Implement various clustering-based sampling techniques:
   - SMOTE (Synthetic Minority Oversampling Technique)
   - ADASYN (Adaptive Synthetic Sampling)
   - BorderlineSMOTE
   - ClusterCentroids
3. Evaluate the impact of different sampling methods on model performance
4. Compare clustering-based approaches with traditional sampling methods

## Files Structure
- `clustering_based_sampling.ipynb` - Main analysis notebook
- `creditcard.csv` - Dataset (fraud detection transactions) - **Download separately**
- `da5401_a3_prd.md` - Project requirements document
- `DA5401 A3 Clustering Based Sampling.pdf` - Assignment instructions

## Requirements
- Python 3.x
- pandas, numpy, scikit-learn
- matplotlib, seaborn for visualization
- imbalanced-learn for sampling techniques
- jupyter notebook

## Installation
```bash
pip install pandas numpy scikit-learn matplotlib seaborn imbalanced-learn jupyter
```

## Usage
1. Clone this repository
2. Open `clustering_based_sampling.ipynb` in Jupyter
3. Run cells sequentially to reproduce the analysis

## Author
Shivam Tiwari

## Course
DA5401 - Advanced Data Analytics
