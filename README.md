# PPARgamma_Type2 Diabetes Mellitus_AIML_Drug_Discovery
AI-Driven ML pipeline for predicting PPARγ EC50 bioactivity using similarity-based labeling

**Project Overview**
This project presents an end-to-end AI-driven drug discovery workflow for predicting PPARγ bioactivity associated with Type 2 Diabetes Mellitus (T2DM).

**The pipeline integrates:**
    * ChEMBL data extraction
    * Similarity-based compound labeling
    * Descriptor and fingerprint feature engineering
    * Machine learning modeling
    * Performance evaluation
The goal was to compare descriptor-based and fingerprint-based approaches for predicting PPARγ activity.

**Target and Disease Context**
1. Target: PPARγ (Peroxisome Proliferator-Activated Receptor Gamma)
2. Disease: Type 2 Diabetes Mellitus
3. Reference drugs:
    * Rosiglitazone
    * Pioglitazone
4. Bioactivity metric: EC50

**Dataset**
Dataset contained:
1. Molecule ChEMBL ID
2. Canonical SMILES
3. EC50 values
4. Binary activity labels
5. Total compounds: 5,305

**Labeling Strategy**
1. Compounds were labeled using a similarity-based approach:
2. Tanimoto similarity was calculated between to fix a threshold : Rosiglitazone and Pioglitazone
3. Average similarity score was computed.
4. Primary labeling rule: Thershold - 0.5245
    * Average similarity ≥ 0.5245 → Active (1)
    * Average similarity < 0.5245 → Inactive (0)
5. Secondary labeling rule: Borderline compounds (0.50–0.53 similarity):
    * EC50 ≤ 1000 nM or missing EC50 → Active
    * EC50 > 1000 nM → Inactive
This approach integrates both structural similarity and experimental bioactivity data.

**Workflow**
1. Data collection from ChEMBL
2. Similarity-based labeling
3. Data cleaning and duplicate removal
4. Derivative analysis
5. 1D/2D descriptor generation
6. Morgan fingerprint generation
7. ML modeling:
    * Random Forest
    * SVM
    * XGBoost
8. Model evaluation:
    * Precision
    * Recall
    * F1-score
    * Accuracy
    * ROC-AUC
    * Confusion matrix

**Tools and Libraries**
1. Python
2. RDKit
3. Pandas
4. NumPy
5. Scikit-learn
6. XGBoost
7. Matplotlib

