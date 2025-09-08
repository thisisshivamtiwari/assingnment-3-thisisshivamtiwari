# DA5401 A3: Clustering-Based Sampling - Product Requirements Document

## Executive Summary
This PRD outlines the complete implementation strategy for addressing class imbalance using clustering and resampling techniques. The deliverable is a comprehensive Jupyter Notebook that demonstrates mastery of unsupervised learning applications in supervised classification improvement.

## Objectives
- Demonstrate understanding of class imbalance challenges in real-world datasets
- Implement and compare multiple resampling strategies
- Evaluate the effectiveness of clustering-based approaches vs. naive methods
- Provide actionable recommendations for fraud detection systems

## Technical Requirements

### Part A: Data Exploration and Baseline Model [10 Points]

#### A1: Dataset Loading and Analysis [1 Point]
**Requirements:**
- Load creditcard.csv from Kaggle Credit Card Fraud Detection dataset
- Display dataset shape, feature names, and basic statistics
- Verify PCA preprocessing (features V1-V28, Time, Amount, Class)

**Implementation Checklist:**
- [ ] Import necessary libraries (pandas, numpy, sklearn, matplotlib, seaborn)
- [ ] Load dataset with proper error handling
- [ ] Display dataset.info() and dataset.describe()
- [ ] Check for missing values

#### A2: Class Distribution Analysis [2 Points]
**Requirements:**
- Calculate exact counts and percentages for each class
- Create both pie chart and bar plot visualizations
- Quantify imbalance ratio (e.g., "99.83% non-fraudulent, 0.17% fraudulent")

**Implementation Checklist:**
- [ ] Use value_counts() for class distribution
- [ ] Calculate imbalance ratio and percentage
- [ ] Create pie chart with proper labels and percentages
- [ ] Create bar plot with count annotations
- [ ] Add interpretive markdown explaining the severity of imbalance

#### A3: Baseline Model Implementation [5 Points]
**Requirements:**
- Train/test split maintaining original class distribution
- Implement Logistic Regression (Model 1)
- Comprehensive evaluation with imbalance-appropriate metrics

**Implementation Checklist:**
- [ ] Use stratified train_test_split (test_size=0.2, random_state=42)
- [ ] Verify class distribution preservation in both sets
- [ ] Train LogisticRegression with default parameters
- [ ] Calculate and display: Accuracy, Precision, Recall, F1-score for both classes
- [ ] Generate confusion matrix with visualization
- [ ] Create classification report
- [ ] Explain why accuracy is misleading (markdown explanation)

### Part B: Resampling Approaches [25 Points]

#### B1: SMOTE Implementation [5 Points]
**Requirements:**
- Apply SMOTE to training data only
- Explain algorithm mechanics and limitations
- Proper citation inclusion

**Implementation Checklist:**
- [ ] Import SMOTE from imblearn.over_sampling
- [ ] Apply SMOTE to training data (sampling_strategy='auto')
- [ ] Display before/after class distributions
- [ ] Create markdown explanation of SMOTE algorithm:
  - How it generates synthetic samples
  - K-nearest neighbors approach
  - Interpolation process
- [ ] Discuss limitations:
  - Potential for noisy sample generation
  - Issues with overlapping classes
  - Computational complexity
- [ ] Include proper citation as specified

#### B2: Clustering-Based Oversampling (CBO) [10 Points]
**Requirements:**
- Theoretical explanation of clustering for diversity
- K-means clustering on minority class
- Strategic oversampling from each cluster

**Implementation Checklist:**
- [ ] Markdown explanation of CBO concept and benefits
- [ ] Separate minority class training samples
- [ ] Implement elbow method for optimal k selection:
  - Test k values from 2 to 10
  - Plot WCSS (Within-Cluster Sum of Squares)
  - Select optimal k value
- [ ] Apply K-means clustering to minority samples
- [ ] Visualize clusters (if possible with PCA/t-SNE)
- [ ] Implement oversampling strategy:
  - Calculate samples needed per cluster
  - Generate synthetic samples within each cluster
  - Use cluster centroids and spread for sample generation
- [ ] Combine oversampled minority with original majority class
- [ ] Display final class distribution

#### B3: Clustering-Based Undersampling (CBU) [5 Points]
**Requirements:**
- Theoretical explanation of strategic undersampling
- Clustering of majority class
- Proportional or strategic sample removal

**Implementation Checklist:**
- [ ] Markdown explanation of CBU rationale
- [ ] Separate majority class training samples
- [ ] Apply K-means clustering to majority samples
- [ ] Implement undersampling strategy options:
  - **Option 1:** Proportional sampling from each cluster
  - **Option 2:** Distance-based removal (closer to minority class)
- [ ] Combine undersampled majority with all minority samples
- [ ] Display final class distribution
- [ ] Note: Can use ClusterCentroids from imblearn as alternative

### Part C: Model Comparison and Analysis [15 Points]

#### C1: Model Training and Evaluation [5 Points]
**Requirements:**
- Train three additional Logistic Regression models
- Consistent evaluation methodology
- Same test set for all comparisons

**Implementation Checklist:**
- [ ] Model 2: Train on SMOTE-balanced data
- [ ] Model 3: Train on CBO-balanced data  
- [ ] Model 4: Train on CBU-balanced data
- [ ] For each model:
  - Use identical LogisticRegression parameters
  - Evaluate on original imbalanced test set
  - Calculate Precision, Recall, F1-score for minority class
  - Generate confusion matrix
  - Store results for comparison

#### C2: Performance Comparison [5 Points]
**Requirements:**
- Comprehensive comparison table/visualization
- Focus on minority class metrics
- Clear visual presentation

**Implementation Checklist:**
- [ ] Create comparison DataFrame with columns:
  - Model Name
  - Precision (Fraud Class)
  - Recall (Fraud Class)
  - F1-Score (Fraud Class)
  - Overall Accuracy
- [ ] Generate comparison bar chart:
  - Grouped bars for Precision, Recall, F1
  - Proper labels and legend
  - Color-coded for easy interpretation
- [ ] Optional: ROC curves comparison
- [ ] Statistical significance testing (if applicable)

#### C3: Conclusion and Recommendations [5 Points]
**Requirements:**
- Comprehensive analysis of results
- Benefits/drawbacks discussion
- Actionable business recommendations

**Implementation Checklist:**
- [ ] Results interpretation:
  - Which method performed best and why?
  - Trade-offs between precision and recall
  - Business impact analysis
- [ ] Method comparison:
  - SMOTE vs. clustering approaches
  - Computational efficiency considerations
  - Scalability factors
- [ ] Business recommendations:
  - Recommended approach for production
  - Implementation considerations
  - Monitoring and maintenance suggestions

## Technical Specifications

### Required Libraries
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import classification_report, confusion_matrix, precision_recall_fscore_support
from sklearn.cluster import KMeans
from imblearn.over_sampling import SMOTE
from imblearn.under_sampling import ClusterCentroids
import warnings
warnings.filterwarnings('ignore')
```

### Code Quality Standards
- **Documentation:** Every function and complex code block must have docstrings/comments
- **Reproducibility:** Set random_state=42 for all stochastic operations
- **Error Handling:** Include try-catch blocks for data loading and model training
- **Visualization:** Professional plots with titles, labels, and legends
- **Markdown:** Clear section headers and explanatory text throughout

### Performance Metrics Focus
- **Primary:** Precision, Recall, F1-score for minority class (fraud detection)
- **Secondary:** Overall accuracy, confusion matrix analysis
- **Advanced:** ROC-AUC, Precision-Recall curves (bonus points)

## Deliverable Structure

### Notebook Organization
1. **Introduction and Setup**
   - Problem statement recap
   - Library imports
   - Dataset loading

2. **Part A: Data Exploration**
   - Dataset analysis
   - Class distribution visualization
   - Baseline model implementation

3. **Part B: Resampling Methods**
   - SMOTE implementation and analysis
   - CBO implementation and analysis
   - CBU implementation and analysis

4. **Part C: Model Comparison**
   - Model training and evaluation
   - Comprehensive comparison
   - Business recommendations

5. **Conclusion**
   - Key findings summary
   - Future work suggestions

### Success Metrics
- **Technical Accuracy:** All models implemented correctly with proper evaluation
- **Code Quality:** Clean, commented, reproducible code
- **Analysis Depth:** Insightful interpretation of results and business implications
- **Presentation:** Professional visualizations and clear explanations

## Risk Mitigation

### Common Pitfalls to Avoid
1. **Data Leakage:** Never apply resampling to test data
2. **Evaluation Errors:** Don't use accuracy as primary metric for imbalanced data
3. **Implementation Issues:** Ensure clustering is applied to correct class subsets
4. **Citation Missing:** Include proper SMOTE citation
5. **Reproducibility:** Always set random seeds

### Quality Assurance Checklist
- [ ] All code cells execute without errors
- [ ] Results are reproducible (fixed random seeds)
- [ ] Proper train/test split maintained throughout
- [ ] Evaluation metrics correctly calculated
- [ ] Visualizations are clear and informative
- [ ] Markdown explanations are comprehensive
- [ ] Business recommendations are actionable

## Timeline and Milestones

### Day 1-2: Setup and Part A
- Environment setup and data loading
- Exploratory data analysis
- Baseline model implementation

### Day 3-4: Part B Implementation
- SMOTE implementation
- Clustering-based oversampling
- Clustering-based undersampling

### Day 5-6: Part C and Analysis
- Model comparison
- Results analysis
- Business recommendations

### Day 7: Final Review
- Code review and cleanup
- Documentation completion
- Final testing and submission

This PRD ensures comprehensive coverage of all assignment requirements while maintaining focus on achieving maximum marks through technical excellence and insightful analysis.