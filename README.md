# Delay Prediction Project: Handling Severe Class Imbalance

This project focuses on building a predictive model to forecast delivery or operational delays. The primary challenge lies in managing **severe class imbalance** (majority class is composed of approximately 94% of the entire dataset), a common characteristic of real-world risk and failure prediction datasets.
Detailed presentation and analysis can be found here: [View Full Report (PDF)](https://drive.google.com/file/d/1sqwbWzKwdR8Qpkknx1UNKMx88P8FHXE-/view?usp=sharing) (you might have to download it)
> [!IMPORTANT]  
> **Data Privacy Notice:** The dataset used in this project is internal company data and contains sensitive information. Therefore, **no raw data or processed datasets will be provided** in this repository. This project is shared for the purpose of demonstrating the methodology, feature engineering, and modeling scripts only.

## Project Overview
The goal is to predict the binary outcome of whether a delay will occur (1) or not (0) based on temporal factors and order characteristics. The procedure is inspired by the **CRISP-DM** framework (excluding the Deployment phase).

<img width="1204" height="800" alt="CRISP-DM" src="https://github.com/user-attachments/assets/780040e2-85fa-4dd8-b2f5-23ef0d565eda" />

### Key Highlights:
* **Advanced Imbalance Handling:** Implemented a hybrid resampling strategy combining **Random Under-Sampling (RUS)** and **SMOTE** to balance the training set without losing critical information.
* **Rigorous Data Cleaning:** Performed meticulous data sanitization, including the identification and removal of features that could lead to **Data Leakage**, ensuring the model generalizes well to unseen data.
* **Multi-Scenario Validation:** Tested across 7 different scenarios to evaluate model stability and the impact of temporal shifts.
* **Modeling Suite:** Comparative analysis between **KNN, XGBoost, and LightGBM**.
## 📊 Experimental Results (Scenarios Benchmarking)

The table below summarizes the performance across different validation strategies:

| Rank | Method | Validation Type | Minority F1 | Precision | Recall | AUC-ROC | Realism |
|:---:|:---|:---|:---:|:---:|:---:|:---:|:---|
| **1** | A + 70% B → test 30% B | Semi-temporal | **62.06%** | 56.46% | 68.90% | 94.14% | High (leakage) |
| **2** | A + 50% B → test 50% B | Semi-temporal | 61.98% | 57.60% | 67.07% | 93.77% | High |
| **4** | K-Fold CV on full A+B | Random mixed CV | 58.12% | 50.84% | 67.83% | 93.87% | Med-Low |
| **7** | Forward Temporal | **Pure temporal** | **4.19%** | 19.37% | **2.35%** | 72.88% | **Highest** |
---

## Self-Assessment
### 👍 Strengths:
* **Rigorous Methodology:** Tested various data split scenarios to find the "true" performance ceiling.
* **Effective Feature Engineering:** Temporal features provided significant predictive power, aligning with operational reality.
* **Honest Evaluation:** Acknowledged the performance gap between cross-validation and real-world temporal testing.

### 👎 Limitations:
* **Lack of Post-Validation:** The project currently ends at static evaluation. It lacks a "Model Monitoring" phase or error analysis on specific order segments.
* **Performance in Production:** The Recall in the most realistic scenario remains low, suggesting a need for additional operational features (e.g., weather data, staff capacity, or vehicle types).
---
## 🚀 Future Roadmap
* Implement a **Post-validation/Error Analysis** phase.
* Apply **Cost-sensitive Learning** to penalize False Negatives (missing a delay) more heavily.
* Experiment with advanced over-sampling methods like SMOTE-Tomek or ADASYN.

## Contact Information
Thu-Nhi Ho-Huynh - 23521107@gm.uit.edu.vn
