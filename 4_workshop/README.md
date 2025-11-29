# Workshop 4: Kaggle System Simulation

## Overview

This folder contains all deliverables for Workshop #4 of the Systems Analysis & Design course (2025-III). The assignment required computational simulation to validate the system architecture designed in previous workshops through two distinct scenarios: data-driven machine learning and event-based cellular automata.

## Contents

- **Simulation1.ipynb:** Data-driven simulation using Gradient Boosting Machine (GBM)
- **Simulation2.ipynb:** Event-based simulation using Cellular Automata
- **data/:** Dataset files from the CIBMTR Kaggle competition
- **figures/:** Generated visualizations and plots
- **requirements.txt:** Python dependencies for running simulations
- **Simulation Report:** PDF document in the LaTeX source folder

## 1. Simulation Scenarios

### Scenario 1: Data-Driven Machine Learning

**Objective:** Validate the predictive core (Module M4) through iterative training and chaos sensitivity analysis.

**Methodology:**
- Gradient Boosting Machine with 5 training iterations
- Perturbation analysis (1%, 5%, 10%, 15% noise)
- SHAP feature importance analysis

**Key Results:**
| Metric | Value |
|--------|-------|
| Mean Accuracy | 0.6784 |
| Mean AUC-ROC | 0.7391 |
| Stability (CV) | 0.012 |
| Chaos Sensitivity | 4.7% predictions changed at 15% noise |

**Top Features (SHAP):**
1. conditioning_intensity
2. sex_match
3. year_hct
4. age_at_hct
5. prim_disease_hct

### Scenario 2: Event-Based Cellular Automata

**Objective:** Model emergent behaviors and validate system response to parameter variations.

**Methodology:**
- 40×40 toroidal grid (1,600 cells/patients)
- Three states: Stable (0), At Risk (1), Event (2 - absorbing)
- 80 time steps with probabilistic transition rules

**Key Results:**
| Metric | Initial | Final |
|--------|---------|-------|
| Event Rate | 53.1% | 100. 0% |
| Stable Patients | 186 | 0 |
| At Risk Patients | 564 | 0 |

**Finding:** Complete system collapse to absorbing state, demonstrating the "critical threshold" phenomenon where high initial event rates lead to inevitable cascade failure.

## 2. Environment Setup

### Requirements

```bash
pip install -r requirements.txt
```

### Dependencies

```
pandas>=2.0.0
numpy>=1.24.0
scikit-learn>=1.3.0
matplotlib>=3.7.0
seaborn>=0.12.0
shap>=0.42.0
```

### Running the Simulations

**Option 1: Google Colab (Recommended)**
1. Open the notebook in Google Colab
2. Run all cells sequentially
3. Results will be saved to `figures/`

**Option 2: Local Environment**
```bash
cd 4_workshop
pip install -r requirements.txt
jupyter notebook Simulation1.ipynb
jupyter notebook Simulation2.ipynb
```

## 3. Generated Outputs

| File | Description |
|------|-------------|
| `simulation1_results.png` | GBM performance across iterations, chaos sensitivity, feature importance |
| `shap_simulation1.png` | SHAP feature importance analysis |
| `simulation2_results.png` | CA temporal evolution, scenario comparison, grid states |
| `sensitivity_simulation2.png` | Parameter sensitivity analysis |

## 4. Key Findings

### Emergent Behaviors

1. **Graceful Degradation (Simulation 1):** GBM model maintains stability under input perturbations up to 15% noise. 

2. **Cascade Failure (Simulation 2):** Patient populations with >50% initial event rates experience inevitable collapse regardless of intervention parameters.

3. **Critical Threshold:** Below ~20% initial event rate, mixed equilibrium states become possible where intervention strategies are meaningful.

### Architectural Implications

- **M6 Validation:** Uncertainty quantification is mandatory given observed sensitivity patterns
- **Early Intervention:** Systems must identify at-risk populations before critical thresholds are crossed
- **Fairness Considerations:** Cascade failure disproportionately affects high-risk demographic groups

## 5. Alignment with Previous Workshops

| Workshop | Contribution | Validation in W4 |
|----------|--------------|------------------|
| W1 | Identified chaos/sensitivity challenges | Chaos sensitivity analysis confirms robustness |
| W2 | Designed 7-module architecture | M1, M4, M6, M7 validated through simulations |
| W3 | Defined quality thresholds (CV < 0.15) | Stability check PASSED (CV = 0.012) |

## 6. Limitations

1. **Accuracy Gap:** GBM achieved 67.84% < 70% target
2. **CA Calibration:** Initial conditions place system in supercritical regime
3. **No Survival Analysis:** Time-to-event modeling not implemented
4. **No Equity Metrics:** Demographic subgroup analysis pending

## 7. Future Work

- Subcritical CA exploration with initial event rates <30%
- Hyperparameter optimization via GridSearchCV
- Cox proportional hazards integration
- Fairlearn demographic parity evaluation

## References

- [CIBMTR Kaggle Competition](https://www.kaggle.com/competitions/equity-post-HCT-survival-predictions)
- [Scikit-learn GBM Documentation](https://scikit-learn.org/stable/modules/ensemble.html#gradient-boosting)
- [SHAP Documentation](https://shap.readthedocs.io/)
