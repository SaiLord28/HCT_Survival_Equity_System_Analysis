# <div align="center">System Analysis Project: CIBMTR Equity in post-HCT survival predictions </div>

---

## <div align="center">Universidad Distrital Francisco José de Caldas</div>

### <div align="center">Faculty of Systems Engineering</div>


### <div align="center">Authors</div>
 <div align="center">Sergio Nicolás Mendivelso - 20231020227 - snmendivelsom@udistrital.edu.co - @SaiLord28</div>
 <div align="center">Sergio Leonardo Moreno Granado - 20242020091 - slmorenog@udistrital.edu.co - @slmorenog-ud</div>
 <div align="center">Juan Manuel Otálora Hernandez - 20242020018 - jmotalorah@udistrital.edu.co - @otalorah</div>
 <div align="center">Juan Diego Moreno Ramos - 20242020009 - juandmorenor@udistrital. edu.co - @juandyi</div>
 
 
---

## Table of Contents
- [Project Overview](#project-overview)
- [Objectives](#objectives)
- [Technologies](#technologies)
- [Workshops Summary](#workshops-summary)
- [Repository Structure](#repository-structure)
- [Final Version](#final-version)
- [Conclusions](#conclusions)


## Project Overview

Welcome to the Equity in post-HCT survival predictions project! This project was developed as part of the System Analysis course at Universidad Distrital Francisco José de Caldas.  

**Competition Link:** https://www.kaggle.com/competitions/equity-post-HCT-survival-predictions

The goal of this project is to build a machine learning model that accurately ranks patients by their risk of a survival event (like relapse or death) after a Hematopoietic Cell Transplant (HCT), while ensuring **equitable performance across demographic groups**.

### Objectives

- Understand the structure of the competition's system
- Learn about the medical context to apply ideas accurately
- Identify the system's elements, relationships, and boundaries
- Analyze the sensitivity and complexity of the problem
- Design and validate a modular prediction system
- Propose recommendations to improve accuracy and fairness of the models

### Technologies

- **Language:** Python 3.10+
- **ML Libraries:** scikit-learn, XGBoost, SHAP
- **Survival Analysis:** scikit-survival, Lifelines
- **Fairness:** Fairlearn, AIF360
- **Visualization:** Matplotlib, Seaborn
- **Documentation:** LaTeX (Overleaf)

## Workshops Summary

### 1. Workshop 1: Kaggle Competition Systems Analysis
- **Folder:** `1_workshop/`
- **Description:** Systems analysis of the CIBMTR Kaggle competition, exploring elements, relationships, boundaries, complexity, and sensitivity considerations.
- **Key Findings:**
  - System complexity: Post-HCT survival is highly complex and non-linear
  - Critical equity constraint: Stratified C-Index requires fair performance across ethnic subgroups
  - High sensitivity to patient variables (age, disease risk, genetic compatibility)
- **Deliverables:** Systems analysis report (PDF), LaTeX source code, diagrams

### 2. Workshop 2: Kaggle Systems Design
- **Folder:** `2_workshop/`
- **Description:** Comprehensive system design with modular pipeline architecture addressing equity throughout the prediction lifecycle. 
- **Key Deliverables:**
  - 7-Module Architecture (M1-M7)
  - Technical stack definition (Python, XGBoost, AIF360)
  - Implementation patterns (Transformer, Ensemble, Decorator)
- **Architecture Modules:**
  1. M1: Data Preprocessing
  2. M2: Equity Analysis
  3. M3: Feature Selection
  4.  M4: Predictive Modeling Core
  5. M5: Fairness Calibration
  6. M6: Uncertainty Quantification
  7. M7: System Outputs

### 3. Workshop 3: Robust System Design and Project Management
- **Folder:** `3_workshop/`
- **Description:** Architecture refinement with robust engineering principles, risk analysis, and project management plan aligned with ISO 9000, CMMI Level 3, and Six Sigma standards. 
- **Key Deliverables:**
  - Risk monitoring framework (6 risks with mitigations)
  - 4-week project timeline (Nov 8 - Dec 5, 2025)
  - Team roles and responsibilities
  - Quality thresholds: C-index >0.70, fairness gap <0.10, CV <0.15

### 4.  Workshop 4: Kaggle System Simulation
- **Folder:** `4_workshop/`
- **Description:** Computational simulation to validate the system architecture through two scenarios: data-driven machine learning and event-based cellular automata. 
- **Simulation Scenarios:**

| Scenario | Methodology | Key Results |
|----------|-------------|-------------|
| **Scenario 1:** Data-Driven | Gradient Boosting Machine (GBM) | AUC = 0.7391, Accuracy = 67.84%, CV = 0.012 (PASS) |
| **Scenario 2:** Event-Based | Cellular Automata (40×40 grid) | 100% event absorption, critical threshold identified |

- **Key Findings:**
  - **Graceful Degradation:** GBM robust to 15% input noise (only 4.7% predictions changed)
  - **Cascade Failure:** High initial event rates (>50%) lead to inevitable system collapse
  - **Critical Threshold:** Below ~20% initial events, mixed equilibrium states become possible
- **Deliverables:** 
  - `Simulation1.ipynb` - GBM training and chaos sensitivity analysis
  - `Simulation2.ipynb` - Cellular automata simulation
  - Simulation report (PDF), visualizations, requirements. txt

## Repository Structure

```
HCT_Survival_Equity_System_Analysis/
│
├── 1_workshop/                 # Workshop 1: Systems Analysis
│   ├── latex/                  # LaTeX source code
│   ├── figures/                # Diagrams
│   └── README.md
│
├── 2_workshop/                 # Workshop 2: System Design
│   ├── latex/                  # LaTeX source code
│   ├── figures/                # Architecture diagrams
│   └── README.md
│
├── 3_workshop/                 # Workshop 3: Robust Design & PM
│   ├── latex/                  # LaTeX source code
│   ├── figures/                # Gantt charts
│   └── README.md
│
├── 4_workshop/                 # Workshop 4: Simulation
│   ├── Simulation1.ipynb       # Data-Driven ML (GBM)
│   ├── Simulation2.ipynb       # Event-Based CA
│   ├── data/                   # Dataset files
│   ├── figures/                # Generated plots
│   ├── requirements.txt        # Python dependencies
│   └── README.md
│
└── README.md                   # This file
```

## Final Version

-

## Conclusions

-

---

Thank you for your consideration and evaluation. We look forward to discussing our project in further detail during the assessment.
