README.txt
==========

Project Title
-------------
ESG Performance and Financial Distress: Empirical Evidence from SET Listed Companies in Thailand

Repository Purpose
------------------
This repository contains the reproducible research pipeline and manuscript materials for a study examining the relationship between Environmental, Social, and Governance (ESG) performance and financial distress among firms listed on the Stock Exchange of Thailand (SET).

The project integrates panel econometrics, logistic regression, interaction analysis, ensemble machine learning, SHAP explainability, and robustness checks using the Merton Distance-to-Default framework.

Suggested Repository Name
-------------------------
esg-financial-distress-thailand-set

Author
------
Assoc. Prof. Dr. Wirapong Chansanam
Department of Information Science
Khon Kaen University, Thailand
Email: wirapongc@kku.ac.th
ORCID: 0000-0001-5546-8485

Study Overview
--------------
This study investigates whether ESG performance reduces financial distress risk among SET-listed firms during 2020-2024. Financial distress is measured using the Altman Z''-Score for emerging-market and non-manufacturing firms, supported by a binary distress indicator and the Merton Distance-to-Default measure.

The analysis focuses on the following objectives:

1. To examine whether ESG performance is associated with financial distress risk.
2. To assess whether Environmental, Social, or Governance pillars differ in their protective effects.
3. To test whether governance quality moderates the relationship between financial leverage and financial distress.
4. To compare econometric results with machine-learning-based feature importance using SHAP values.

Main Finding
------------
Financial leverage is the strongest and most consistent predictor of financial distress across econometric and machine learning models. Return on assets provides a protective effect, while ESG variables show limited short-term predictive power. Environmental performance may provide a modest protective signal, but the overall results indicate that financial fundamentals dominate near-term distress prediction among Thai listed firms.

Repository Contents
-------------------
The repository is designed to include the following files:

1. ESG_Distress_Pipeline_Colab_28042026.ipynb
   Main Google Colab notebook for data loading, preprocessing, Z''-Score calculation, regression analysis, machine learning, SHAP analysis, interaction testing, and robustness checks.

2. ESG_Financial_Distress_Thailand_SET - 28042026 - AutoUpdated.docx
   Manuscript draft describing the theoretical background, methodology, findings, discussion, limitations, and conclusion.

3. Thailand_ESG__data_30102025.csv
   Base firm-year financial and ESG dataset.

4. ALL_SET_952_ESG_2013-2025_1.csv
   S&P Global ESG score dataset used for matching ESG indicators.

5. sector_mapping.csv
   Sector classification file for SET-listed firms.

6. README.txt
   Repository documentation file.

Input Data Requirements
-----------------------
The Colab pipeline expects the following CSV files to be placed in the working directory:

- Thailand_ESG__data_30102025.csv
- ALL_SET_952_ESG_2013-2025_1.csv
- sector_mapping.csv

The notebook can run locally in Colab's default environment or write outputs directly to Google Drive by setting:

USE_DRIVE = True

If using local Colab storage, upload the CSV files manually through the Colab Files panel or by using the upload cell provided in the notebook.

Main Workflow
-------------
The analysis pipeline follows these steps:

Step 0: Setup
- Install required Python packages.
- Configure local or Google Drive working directory.
- Load required libraries.

Step 1: Data Loading and Merging
- Load the base financial dataset.
- Clean ticker symbols.
- Merge S&P Global ESG data.
- Merge sector mapping information.

Step 2: Financial Distress Measurement
- Compute Altman Z''-Score using the emerging-market and non-manufacturing specification:

  Z'' = 3.25 + 6.56X1 + 3.26X2 + 6.72X3 + 1.05X4

  where:
  X1 = Working Capital / Total Assets
  X2 = Retained Earnings / Total Assets
  X3 = EBIT / Total Assets
  X4 = Book Value of Equity / Total Liabilities

- Generate binary distress classification.
- Classify firms into safe, grey, and distress zones.

Step 3: Descriptive Analysis
- Produce summary statistics.
- Generate year-level Z''-Score summaries.
- Create Pearson correlation heatmap.

Step 4: Econometric Analysis
- Estimate pooled OLS models.
- Estimate logistic regression models for binary distress.
- Conduct Variance Inflation Factor (VIF) diagnostics.
- Estimate PanelOLS with entity and time fixed effects.
- Estimate First-Difference OLS as a robustness check.
- Conduct Hausman specification testing.

Step 5: Interaction Analysis
- Test LEVERAGE x GS interaction effects.
- Estimate both OLS and logistic interaction models.

Step 6: Machine Learning Analysis
- Train Random Forest classifier.
- Train Gradient Boosting classifier.
- Evaluate accuracy and AUC-ROC.
- Use a no-leakage mode that can restrict features to ESG variables when the target is derived from financial ratios.

Step 7: SHAP Explainability
- Compute SHAP values for Random Forest and Gradient Boosting models.
- Generate SHAP feature importance and beeswarm plots.
- Interpret variable-level contributions to financial distress prediction.

Step 8: Merton Distance-to-Default Robustness Check
- Estimate Merton Distance-to-Default.
- Classify observations into low-risk, moderate-risk, and high-risk groups.
- Compare Merton-based classifications with Altman Z''-Score classifications.

Expected Outputs
----------------
After successful execution, the working directory should contain:

- merged_esg_distress_panel.csv
- merged_esg_distress_panel_v2.csv
- correlation_heatmap.png
- feature_importance.png
- vif_results.csv
- panel_regression_results.txt
- shap_summary_rf.png
- shap_summary_gb.png
- shap_beeswarm_rf.png
- shap_beeswarm_gb.png
- interaction_regression_results.csv
- merton_dd_results.csv
- hausman_test_results.txt

Software and Package Requirements
---------------------------------
The notebook is designed for Google Colab and Python 3.x.

Main Python packages:

- pandas
- numpy
- matplotlib
- seaborn
- statsmodels
- linearmodels
- scikit-learn
- shap
- scipy
- python-docx
- lxml
- openpyxl

In Colab, missing packages can be installed using:

pip install -q linearmodels shap python-docx lxml openpyxl

How to Run
----------
1. Open ESG_Distress_Pipeline_Colab_28042026.ipynb in Google Colab.
2. Upload the required CSV files to the working directory.
3. Run the setup cells.
4. Run the main pipeline cells sequentially.
5. Review output files generated in the Colab working directory.
6. Download the outputs or set USE_DRIVE = True to save them directly to Google Drive.

Reproducibility Notes
---------------------
- The notebook uses a random_state value for machine learning train-test splitting where applicable.
- Continuous variables should be checked for missing values and outliers before final analysis.
- ESG variables may have incomplete coverage; users should verify ESG matching quality before interpretation.
- Financial-ratio leakage should be avoided when using machine learning to predict a target derived from Altman Z''-Score.
- The no-leakage mode is recommended for ESG-only predictive interpretation.

Research Design Summary
-----------------------
The study applies a sequential mixed-methods design. Panel regression provides coefficient-level inference while controlling for unobserved firm and time effects. Logistic regression models binary distress classification. Machine learning models provide non-parametric prediction and feature-importance validation. SHAP explainability bridges predictive modeling with interpretable economic analysis.

Limitations
-----------
Users should consider the following limitations when interpreting results:

1. The study period covers 2020-2024, which may be too short to capture long-term governance effects.
2. ESG data coverage is incomplete and may introduce sample selection bias.
3. Fixed-effects models mitigate time-invariant unobserved heterogeneity but do not fully resolve reverse causality.
4. Machine learning performance must be interpreted carefully because financial distress labels are partly derived from financial ratios.
5. Findings are based on SET-listed companies and may not generalize to unlisted firms or other emerging markets without further testing.

Recommended Citation
--------------------
Chansanam, W. (2026). ESG performance and financial distress: Empirical evidence from SET listed companies in Thailand. Khon Kaen University.

Suggested GitHub Description
----------------------------
Reproducible Python/Colab pipeline for analyzing ESG performance and financial distress among SET-listed firms in Thailand using Altman Z''-Score, panel regression, logistic regression, SHAP explainability, and Merton Distance-to-Default robustness checks.

License
-------
Please specify the repository license before public release.

Suggested options:
- MIT License for code.
- CC BY 4.0 for manuscript text and documentation.
- Restricted access for raw financial and ESG datasets if the data are proprietary or obtained from licensed databases.

Data Availability Statement
---------------------------
The analysis uses financial and ESG datasets compiled from SET-listed firms and ESG data sources. Raw datasets may be subject to licensing restrictions. Processed or anonymized data can be shared only where permitted by the original data providers.

Contact
-------
For questions about the research pipeline, manuscript, or replication materials, please contact:

Assoc. Prof. Dr. Wirapong Chansanam
Department of Information Science
Khon Kaen University
Email: wirapongc@kku.ac.th
