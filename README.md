# PPARgamma_Type2 Diabetes Mellitus_AIML_Drug_Discovery
AI-Driven ML pipeline for predicting PPARγ EC50 bioactivity using similarity-based labeling

**Project Overview:** 
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

**Dataset Contain**
1. Molecule ChEMBL ID
2. Canonical SMILES
3. EC50 values
4. Binary activity labels
5. Total compounds count initial: 5,305
6. After Cleaning, the total compounds count: 4,285
7. Active compounds count: 23
8. Inactive compounds count: 4262

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

**Descriptor and Fingerprint Model Performance Summary**

| Feature Type  |  Best Model | Precision  |  Recall | F1 Score  |   ROC-AUC|
|---|---|---|---|---|---|
| Molecular Descriptors  |  XGBoost(Tuned)  |  0.562  |  1.00  |  0.720  |   0.999 |
| Molecular Fingerprints  |  Random Forest(Deafult)|  0.889 |  0.889  |   0.889 |  1.00  |

A total of 12 models were trained (3 Models with default and tuned hyperparameters) across two feature representations: molecular descriptors and molecular fingerprints.

Fingerprint-based models consistently outperformed descriptor-based models across all evaluation metrics. The best overall model was Random Forest trained on molecular fingerprints, achieving an F1-score of 0.889 and ROC-AUC of 1.00.

Hyperparameter tuning improved descriptor-based models; however, they did not surpass fingerprint-based approaches in predictive performance.


**How to Run the Project**

1. Clone the repository:
   git clone https://github.com/suja-suji/PPARgamma_T2DM_AI_Drug_Discovery
2. Navigate into the project folder:
   PPARgamma_T2DM_AI_Drug_Discovery
3. Install required libraries:
   pip install -r requirements.txt
4. Open the notebooks in order:
   - 01_data_collection_and_similarity_labeling.ipynb
   - 02_dataset_cleaning.ipynb
   - 03_rosiglitazone_derivative_analysis.ipynb
   - 04_pioglitazone_derivative_analysis.ipynb
   - 05_1D_2D_descriptor_generation.ipynb
   - 06_morgan_fingerprint_generation.ipynb
   - 07_descriptor_based_ml_models.ipynb
   - 08_fingerprint_based_ml_models.ipynb


**Tools and Libraries**

1. Python
2. RDKit
3. Pandas
4. NumPy
5. Scikit-learn
6. XGBoost
7. Matplotlib

