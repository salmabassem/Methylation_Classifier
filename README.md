# Random Forest on Mixed Data — PBMC as 14th Epitype

This repository contains an end-to-end analysis and reproducible workflow for retraining a **Random Forest (RF)** classifier on mixed AML epitypes, treating **PBMC** as the 14th epitype.  
The analysis is implemented in R, with outputs summarized in an HTML report.

---

## 📄 Live Report
- **Local:** `reports/Retraining-RF-model-on-Mixed-data-with-PBMC-as-14th-epitype.html`

---

## 🚀 Quick Start

### 1. Clone the repository
```bash
git clone https://github.com/<your-username>/Methylation_Classifier.git
cd Methylation_Classifier
2. Restore the R environment
r
Copy
Edit
install.packages("renv")
renv::init()        # initialize if fresh
renv::restore()     # restore packages from renv.lock


3. Add data

Place full dataset please reach out directly. 

4. Render the analysis
r
Copy
Edit
install.packages("rmarkdown")
rmarkdown::render("notebooks/analysis.Rmd", output_dir = "reports")
5. (Optional) Publish to GitHub Pages
bash
Copy
Edit
make pages   # Copies latest report to docs/index.html
Then enable Pages in the repo settings → Deploy from /docs.

This summary is based on the nested cross-validation and calibrated probability outputs in the HTML report.

| Metric                          | Value       | Notes |
|---------------------------------|------------:|-------|
| **Mean multiclass AUC**         | **0.9948**  | Nested CV with calibration |
| **Mean misclassification error**| **0.1004**  | ~89.96% accuracy |
| **OOB error estimate**          | **12.85%**  | From RF training set |
| **Number of trees**             | 500         | mtry = 6 |
| **Balanced sampling**           | Yes         | Each class matched to smallest class size |
| **Calibration method**          | Multinomial logistic regression (elastic net, α = 0) | Improved probability estimates |

**Performance highlights**
- Strong separation across all **14 epitypes** (including PBMC).
- Minimal confusion between classes in the final confusion matrix.
- Calibration improved reliability of predicted probabilities.
- Top features identified via Gini importance; biological relevance discussed in the report.
