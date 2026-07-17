# Electoral Abstention Analysis in Spanish Municipalities

Final project for the **Data Mining and Predictive Modelling** module, MSc in Big Data, Data Science & Artificial Intelligence (UCM).

## Objective

Analyse the demographic, economic and territorial factors associated with electoral abstention across Spanish municipalities using predictive modelling techniques.

Two models are developed:

- **Linear regression** to predict the abstention percentage (`AbstentionPtge`)
- **Logistic regression** to classify municipalities with high abstention (`AbstencionAlta`)

---

## Project structure

    .
    ├── DatosEleccionesEspaña.xlsx
    ├── FuncionesMineria.py
    ├── Tarea_Final.ipynb
    ├── Tarea_Final_Memoria_Eloy.pdf
    ├── librerias.txt
    └── .gitignore

---

## Dataset

The dataset contains information on **8,117 Spanish municipalities** with variables covering:

- Demographics
- Labour market
- Economic activity
- Territory and population density
- Electoral indicators

Target variables:

| Variable | Description |
|---|---|
| `AbstentionPtge` | Abstention percentage |
| `AbstencionAlta` | 1 if abstention > 30%, 0 otherwise |

---

## Preprocessing

### Data cleaning

- Conversion of categorical variables
- Replacement of artificial missing codes (`999`, `99999`)
- Correction of out-of-range percentages
- Regrouping of underrepresented categories
- Treatment of unknown categories

### Outliers

Detection via standard deviation and interquartile range (IQR). Outliers were transformed to missing for subsequent imputation.

### Missing values

- Missing pattern analysis
- Creation of `prop_missings` variable
- Random imputation of numerical and categorical variables

---

## Models

### Linear regression

Predicts `AbstentionPtge`

| Method | Criterion |
|---|---|
| Forward | AIC / BIC |
| Backward | AIC / BIC |
| Stepwise | AIC / BIC |

Best model: Forward / Stepwise BIC

| Metric | Value |
|---|---|
| R² train | 0.425 |
| R² test | 0.412 |
| No. parameters | 61 |

### Logistic regression

Classifies `AbstencionAlta`

Best model: Forward AIC / BIC — optimal cut-off: **0.30** (Youden index)

| Metric | Value |
|---|---|
| McFadden pseudo-R² (test) | 0.276 |
| AUC ROC (test) | 0.835 |
| Accuracy | 0.779 |
| Sensitivity | 0.709 |

---

## Key findings

- Province (`CodigoProvincia`) is the strongest predictor of abstention.
- Territorial rootedness (`SameComAutonPtge`) is associated with higher electoral participation.
- Municipal economic structure adds additional explanatory power.
- Both models generalise well with low overfitting.

---

## Tech stack

- Python — pandas, numpy, scikit-learn, statsmodels, matplotlib, seaborn

---

## Setup

```bash
pip install -r librerias.txt
jupyter notebook Tarea_Final.ipynb
```

---

## Author

**Eloy Celaya López**
MSc in Big Data, Data Science & Artificial Intelligence — Universidad Complutense de Madrid

Academic project — Data Mining and Predictive Modelling, MSc NTIC (UCM), 2026–2027
*(Full report available in Spanish — `Tarea_Final_Memoria_Eloy.pdf`)*
