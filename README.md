\# 📊 ESG Performance and Financial Distress

\### Empirical Evidence from SET Listed Companies (Thailand)

\---

\## 📌 Repository Purpose

This repository provides a \*\*fully reproducible research pipeline\*\* and manuscript materials for analyzing the relationship between:

\* \*\*Environmental, Social, and Governance (ESG) performance\*\*

\* \*\*Corporate financial distress\*\*

using data from firms listed on the \*\*Stock Exchange of Thailand (SET)\*\*.

The project integrates:

\* Panel econometrics

\* Logistic regression

\* Interaction analysis

\* Machine learning (Random Forest, Gradient Boosting)

\* SHAP explainability

\* Merton Distance-to-Default robustness checks

\---

\## 🧠 Study Overview

This study examines whether ESG performance reduces financial distress risk among SET-listed firms (2020–2024).

\### 🎯 Research Objectives

1\. Assess the relationship between ESG performance and financial distress

2\. Compare ESG pillars (Environmental, Social, Governance)

3\. Test governance as a moderator of leverage–distress relationship

4\. Validate econometric findings using machine learning (SHAP)

\---

\## 🔍 Key Findings

\* \*\*Financial leverage\*\* is the strongest predictor of distress

\* \*\*Return on assets (ROA)\*\* provides a protective effect

\* ESG variables show \*\*limited short-term predictive power\*\*

\* Environmental performance shows \*\*weak protective signals\*\*

\* Financial fundamentals dominate ESG in \*\*near-term distress prediction\*\*

\---

\## 📂 Repository Structure

\`\`\`bash

├── ESG\_Distress\_Pipeline\_Colab\_28042026.ipynb # Main analysis pipeline

├── ESG\_Financial\_Distress\_Thailand\_SET.docx # Research manuscript

├── Thailand\_ESG\_\_data\_30102025.csv # Financial + ESG dataset

├── ALL\_SET\_952\_ESG\_2013-2025\_1.csv # S&P ESG dataset

├── sector\_mapping.csv # Sector classification

├── README.md # Project documentation

\`\`\`

\---

\## ⚙️ Input Data Requirements

Place the following files in the working directory:

\* \`Thailand\_ESG\_\_data\_30102025.csv\`

\* \`ALL\_SET\_952\_ESG\_2013-2025\_1.csv\`

\* \`sector\_mapping.csv\`

\---

\## 🔄 Main Workflow

\### 🧩 Step 0: Setup

\* Install required packages

\* Configure environment (Colab / Google Drive)

\---

\### 📥 Step 1: Data Loading & Merging

\* Load financial dataset

\* Clean ticker symbols

\* Merge ESG and sector data

\---

\### 📉 Step 2: Financial Distress Measurement

Altman Z''-Score:

\[

Z'' = 3.25 + 6.56X\_1 + 3.26X\_2 + 6.72X\_3 + 1.05X\_4

\]

Where:

\* (X\_1): Working Capital / Total Assets

\* (X\_2): Retained Earnings / Total Assets

\* (X\_3): EBIT / Total Assets

\* (X\_4): Equity / Total Liabilities

Outputs:

\* Continuous Z''-Score

\* Binary distress classification

\* Risk zones (Safe / Grey / Distress)

\---

\### 📊 Step 3: Descriptive Analysis

\* Summary statistics

\* Correlation heatmap

\* Year-level trends

\---

\### 📈 Step 4: Econometric Analysis

\* Pooled OLS

\* Logistic regression

\* PanelOLS (fixed effects)

\* First-difference OLS

\* Hausman test

\* VIF diagnostics

\---

\### 🔗 Step 5: Interaction Analysis

\* LEVERAGE × GS moderation

\* OLS + Logit interaction models

\---

\### 🤖 Step 6: Machine Learning

\* Random Forest

\* Gradient Boosting

\* AUC-ROC evaluation

\* ESG-only (no leakage) mode

\---

\### 🔍 Step 7: SHAP Explainability

\* Feature importance

\* Beeswarm plots

\* Model interpretability

\---

\### 📉 Step 8: Merton DD Robustness

\* Distance-to-Default estimation

\* Risk classification

\* Concordance analysis with Z''-Score

\---

\## 📤 Expected Outputs

\`\`\`bash

merged\_esg\_distress\_panel.csv

correlation\_heatmap.png

feature\_importance.png

vif\_results.csv

panel\_regression\_results.txt

shap\_summary\_rf.png

shap\_summary\_gb.png

shap\_beeswarm\_rf.png

shap\_beeswarm\_gb.png

interaction\_regression\_results.csv

merton\_dd\_results.csv

hausman\_test\_results.txt

\`\`\`

\---

\## 💻 Requirements

\### Environment

\* Python 3.x

\* Google Colab (recommended)

\### Libraries

\`\`\`bash

pip install pandas numpy matplotlib seaborn statsmodels linearmodels \\

scikit-learn shap scipy python-docx lxml openpyxl

\`\`\`

\---

\## ▶️ How to Run

1\. Open notebook in Google Colab

2\. Upload required CSV files

3\. Run all cells sequentially

4\. Download outputs or enable:

\`\`\`python

USE\_DRIVE = True

\`\`\`

\---

\## 🔁 Reproducibility Notes

\* Random seed applied for ML models

\* ESG coverage may be incomplete

\* Avoid feature leakage in ML models

\* Use ESG-only mode for interpretability

\* Check missing values and outliers before analysis

\---

\## 🧪 Research Design

This study applies a \*\*sequential mixed-methods approach\*\*:

\* Econometrics → causal inference

\* Logistic regression → classification

\* Machine learning → predictive validation

\* SHAP → interpretability

\---

\## ⚠️ Limitations

\* Short panel period (2020–2024)

\* Partial ESG coverage

\* Potential reverse causality

\* ML results sensitive to imbalance

\* Limited generalizability beyond Thailand

\---

\## 📚 Recommended Citation

\`\`\`

Chansanam, W. (2026).

ESG Performance and Financial Distress:

Empirical Evidence from SET Listed Companies in Thailand.

Khon Kaen University.

\`\`\`

\---

\## 🏷️ Suggested GitHub Description

\> Reproducible Python/Colab pipeline for ESG and financial distress analysis using Altman Z''-Score, panel econometrics, machine learning, SHAP, and Merton Distance-to-Default.

\---

\## 👤 Author

\*\*Assoc. Prof. Dr. Wirapong Chansanam\*\*

Department of Information Science

Khon Kaen University, Thailand

📧 \[wirapongc@kku.ac.th\](mailto:wirapongc@kku.ac.th)

🔗 ORCID: 0000-0001-5546-8485

\---

\## 📜 License

Recommended:

\* \*\*Code:\*\* MIT License

\* \*\*Manuscript:\*\* CC BY 4.0

\* \*\*Data:\*\* Restricted (if proprietary)

\---

\## 📊 Data Availability

Datasets are derived from ESG and financial sources and may be subject to \*\*licensing restrictions\*\*.

Processed datasets may be shared upon request where permitted.

\---

\## 📬 Contact

For replication, collaboration, or questions:

\*\*Assoc. Prof. Dr. Wirapong Chansanam\*\*

Khon Kaen University

Email: \[wirapongc@kku.ac.th\](mailto:wirapongc@kku.ac.th)