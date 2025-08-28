# 🧾 Probabilistic Models & Fraud Detection Analysis

## 📌 About the Project
This project focuses on the **comparison and calibration of probabilistic classification models**, applied to a **credit card fraud detection dataset**. The main goal is to evaluate **which models generate the most reliable and calibrated probability estimates**, especially in a **highly imbalanced dataset** where fraud detection is critical.

## 📊 Dataset Information
- **Name:** [Card Fraud Detection in Luxury Retail Analytics Dataset](https://www.kaggle.com/datasets/pratyushpuri/payment-card-fraud-detection-with-ml-models-2025/data)
- **Records:** 2,133 transactions
- **Features:** 16 (transactional + behavioral attributes)
- **Context:** Luxury cosmetics pop-up events across major global cities
- **Objective:** Identify fraudulent credit card transactions

Although synthetic, the dataset was carefully designed to mimic realistic **fraud patterns**, making it ideal for research in **fraud analytics**.

## ⚙️ Methodology

### 1. Preprocessing
- Separation of numeric and categorical features
- Missing value imputation
- Standardization of continuous variables
- One-Hot Encoding for categorical variables

### 2. Probabilistic Models Compared
- 🎯 **Support Vector Classifier (SVC)** with isotonic calibration
- 📈 **Logistic Regression (LR)**
- 📊 **Linear Discriminant Analysis (LDA)**
- 🌲 **Random Forest (RF)**
- 🔥 **Gradient Boosting (GB)**
- 🧮 **Naive Bayes (NB)**

### 3. Imbalanced Learning Techniques
**Undersampling:**
- Tomek Links
- ENN
- OSS
- NCR
- RENN

**Oversampling:**
- RandomOverSampler
- SMOTE
- BorderlineSMOTE
- ADASYN

### 4. Evaluation Metrics
- **Brier Score Loss (BS):** Quality of predicted probabilities
- **Brier Skill Score (BSS):** Relative improvement vs. trivial baseline
- **Confusion Matrices** and **ROC Curve** at different thresholds
- **Youden's Index (J = Sensitivity + Specificity – 1)** for optimal threshold tuning

## 📈 Key Results

### 🏆 Model Performance (Brier Skill Score)
| Model | BSS Score | Rank |
|-------|-----------|------|
| **SVC (calibrated)** | ~0.646 | 🥇 **Best** |
| Random Forest | ~0.638 | 🥈 |
| Logistic Regression | ~0.634 | 🥉 |
| LDA | ~0.624 | 4th |
| Gradient Boosting | ~0.599 | 5th |
| Naive Bayes | Very poor | Last |

### 🔄 Resampling Techniques Impact
- **One-Sided Selection (OSS)** showed the best improvement (~0.603)
- Oversampling methods (SMOTE, ADASYN) did **not** significantly improve performance

### ⚖️ Threshold Optimization Results
- **Default threshold (0.5):** Almost no fraud cases detected
- **Optimal threshold (~0.034):** Better fraud detection, but increased false positives
- **Key insight:** Threshold optimization is essential in imbalanced problems

## 📊 Visualizations

### Confusion Matrices Analysis
- **At default threshold (0.5):** Almost all predictions classified as "non-fraud"
- **At optimal threshold (0.034):** Better fraud detection with trade-off in false alarms

### ROC Curve Analysis
- ROC curve with optimal Youden's point highlighted
- Clear visualization of sensitivity vs. specificity trade-offs

## 🎯 Main Conclusions

1. **Probability calibration matters** — Success isn't just about classification accuracy, but also about generating trustworthy probability estimates

2. **Best combination:** SVC with isotonic calibration + OSS undersampling provided the most balanced results

3. **Threshold tuning is critical:** Using Youden's Index for threshold optimization is essential in fraud detection scenarios

4. **Visual analysis value:** ROC curves and confusion matrices help stakeholders understand trade-offs between sensitivity and specificity

## 🚀 Technical Implications

This analysis demonstrates that:
- Model sophistication doesn't always translate to better probability estimates in imbalanced scenarios
- Proper calibration can significantly improve model reliability
- Undersampling techniques may outperform oversampling in certain fraud detection contexts
- Threshold optimization is crucial for practical deployment in fraud detection systems

## 📁 Repository Structure
```
├── data/                   # Dataset files
├── notebooks/              # Jupyter notebooks with analysis
├── src/                    # Source code for models and preprocessing
├── results/                # Generated plots and evaluation metrics
└── README.md              # This file
```

## 🔧 Dependencies
- Python 3.8+
- scikit-learn
- pandas
- numpy
- matplotlib
- seaborn
- imbalanced-learn
