# PPARgamma_Type2 Diabetes Mellitus_AIML_Drug_Discovery
AI-Driven ML pipeline for predicting PPARγ EC50 bioactivity using similarity-based labeling
Overview:
This project presents an AI driven drug discovery workflow for PPARγ bioactivity associated with Type 2 Diabetes Mellitus(T2DM)
The pipeline integrates 
  1. ChEMBL dataset extraction, Total Compounds count initially - 5305
  2. Similarity - based compound labeling
  3. Descriptor and fingerprint generation
  4. Machine learning model building
  5. Performance Evaluation
The goal was to compare between Descriptor based and fingerprint based models which is having high performance for predicting PPARγ in the Holdout set.

Labeling Strategy :
PPARγ is involved in multiple pathological conditions, a similarity-based approach was used to identify the diabetes-relevant compounds.
  1. Tanimoto similarity was calculated against: Rosiglitazone and Pioglitazone (Reference Drugs), Average similarity score was computed.
  2. Primary labeling rule: Threshold value - 0.5245
       Average similarity ≥ 0.5245 → Active (1)
       Average similarity < 0.5245 → Inactive (0)
  3. Seconadry labeling rule: Borderline compounds (0.50–0.53 similarity):
      EC50 ≤ 1000 nM or missing EC50 → Active
      EC50 > 1000 nM → Inactive
This approach integrates both structural similarity and experimental bioactivity data.

