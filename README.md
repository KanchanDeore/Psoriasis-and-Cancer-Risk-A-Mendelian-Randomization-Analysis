🔬 Psoriasis and Cancer Risk: A Mendelian Randomization Analysis
Overview
This project recreates the analytical pipeline of the Nature Communications study by Li et al. (2024), using Mendelian Randomization (MR) methods to assess the causal relationship between psoriasis and multiple cancer types.

By leveraging public GWAS datasets and advanced statistical techniques (IVW, MR-Egger, Weighted Median, Weighted Mode), this pipeline estimates the genetic correlation between psoriasis and cancers such as lung, breast, kidney, prostate, colorectal, and skin cancers.

🧠 Motivation
Psoriasis is a chronic inflammatory disease with genetic underpinnings. Understanding whether psoriasis causally increases cancer risk can aid in public health decisions and personalized medicine. The original study used polygenic risk scores and large-scale genetic data. Here, we reproduce their approach with an emphasis on transparency and reproducibility.

🚀 Project Goal
To reconstruct the causal analysis pipeline from the published paper using publicly available GWAS data, validate the findings, and explore the robustness of various MR techniques.

⚙️ How It Works
1. Data Acquisition
Psoriasis data from EBI GWAS Catalog

Cancer datasets from NIH GWAS Explorer and PLCO Atlas

All datasets are stored in psoriasis/ and datasets/ folders.

2. Preprocessing
Common SNPs between exposure and outcome datasets are identified.

SNP-level associations with both psoriasis (exposure) and each cancer type (outcome) are extracted.

3. MR Analysis Pipeline
Inverse Variance Weighted (IVW)

MR-Egger Regression

Weighted Median Estimator

Weighted Mode Estimator

Each method is implemented in gwas.py, with orchestrating logic in main.py.

📁 Repository Structure
bash
Copy
Edit
.
├── gwas.py                    # Core computational functions for MR analysis
├── main.py                    # Main pipeline script
├── run.sh                     # Bash script to run all analyses
├── datasets/                  # Contains all cancer GWAS datasets
├── psoriasis/                 # Contains exposure data (psoriasis)
├── README.md                  # This file
💻 How to Run
To run for all datasets:
bash
Copy
Edit
bash run.sh
To run a specific comparison:
bash
Copy
Edit
python3 main.py psoriasis datasets/breast_cancer.tsv
Replace breast_cancer.tsv with any other dataset in datasets/.

📊 Visualization
Results are visualized using bar plots where:

X-axis = Cancer types

Y-axis = Odds Ratios (OR)

Secondary Y-axis = -log10(p-values) to assess significance

Cancer types with significant associations (p < 0.05) are clearly marked.

📌 Key Findings
Cancer Type	Odds Ratio (OR)	P-value
Kidney Cancer	1.25	0.001
Lung Cancer	1.12	0.013
Breast Cancer	1.02	0.002
Prostate Cancer	1.08	0.045
Colorectal	1.05	0.021
Skin Cancer	1.15	0.022

These results suggest a statistically significant causal association between psoriasis and these six cancers.

🔍 Insights
Confirms the findings by Li et al. (2024) using a different psoriasis dataset.

Data robustness matters: Lung cancer outputs varied depending on dataset.

Demonstrates the power of open-access genetics data for reproducible public health research.

📚 References
Li et al., Nature Communications (2024): https://doi.org/10.1038/s41467-024-17952-6

GWAS Catalog - EBI

GWAS Explorer - NIH

MRC IEU GWAS database: https://gwas.mrcieu.ac.uk/

🙏 Acknowledgements
Special thanks to Prof. Quan Wan — for insightful mentorship

