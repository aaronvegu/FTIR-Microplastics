# FTIR Plastic Classification Using Machine Learning

This repository documents the end-to-end process of classifying plastic types using FTIR (Fourier-transform infrared) spectroscopy data and machine learning techniques. It includes data preprocessing, dimensionality reduction, model training, and evaluation.

## 📌 Project Objective

To build and validate baseline machine learning models for classifying three types of plastics:
- Polyethylene (PE)
- Polypropylene (PP)
- Polystyrene (PS)

using spectroscopic fingerprint data extracted from `.dpt` files.

## 🧪 Methodology Overview

### 1. **Data Preparation**
- Raw `.dpt` spectroscopy files are converted into structured DataFrames.
- Samples with outlier absorbance values (>1.1 or <0.8) are removed.
- Filtered datasets are visualized and optionally saved as `.csv` files.

### 2. **Dimensionality Reduction (PCA)**
- FTIR spectra are scaled and reduced to 5 principal components.
- The PCA and StandardScaler models are saved as `.pkl` for reuse.

### 3. **Model Training**
- Models trained: Random Forest, SVM, and Logistic Regression.
- Hyperparameters optimized via Grid Search with 5-fold cross-validation.
- Accuracy tested on held-out test set.

### 4. **Validation**
- Performance validated on a separate labeled set of known samples.
- Evaluation metrics include accuracy and confusion matrix.

### 5. **Scoring Unknown Samples**
- Trained models predict on new, unlabeled data.
- A confidence threshold is applied; predictions below threshold are labeled "unknown."
- Predictions are visualized and exported as `.csv`.

## 📂 Folder Structure
```
.
├── data/
│   ├── raw/                # Raw .dpt files
│   ├── processed/          # Cleaned and PCA-reduced CSVs
│   └── models/             # Trained models (.joblib)
├── notebooks/
│   └── FTIR_Classification.ipynb
├── pca/
│   ├── std_scaler.pkl
│   └── pca.pkl
├── predictions/
│   └── *.csv
└── README.md
```

## 📊 Results Summary

| Model              | CV Accuracy | Test Accuracy | Precision (Validation) |
|-------------------|-------------|---------------|-------------------------|
| Random Forest      | 88.00%      | 78.95%        | High for PE             |
| SVM                | 41.33%      | 57.89%        | Confusion PP/PS         |
| Logistic Regression| 41.33%      | 57.89%        | Confusion PP/PS         |

- Polyethylene was classified with high accuracy.
- Confusion was observed between Polypropylene and Polystyrene.

## 📈 Visual Outputs
- FTIR spectral plots pre- and post-cleaning
- Confusion matrices
- Confidence-based prediction charts

## 🛠️ Requirements
```bash
pip install pandas numpy scikit-learn matplotlib joblib
```

## 📚 References
- Scikit-learn Documentation: https://scikit-learn.org/
- Microsoft AutoML: https://learn.microsoft.com/en-us/azure/machine-learning/concept-automated-ml
- Thermo Fisher FTIR Basics: https://www.thermofisher.com

## 🔬 Research Context
This work is part of a broader academic research project investigating methods for plastic classification using spectroscopic data. For a theoretical background and results discussion, see the accompanying research reports.

## 📥 License
This repository is provided for academic and research purposes only. Please cite appropriately if you use this material.

---

For questions, contact: `aaronvegu@gmail.com`