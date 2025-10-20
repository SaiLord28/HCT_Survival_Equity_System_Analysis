# Workshop 2: Kaggle Systems Design

## Overview

This repository contains collaborative work for Workshop #2 of the Systems Analysis & Design course (2023). We analyzed the CIBMTR Kaggle competition on post-HCT survival predictions, exploring system elements, relationships, sensitivity considerations, and chaos theory implications.

## Team Contribution

This work represents the combined effort of four contributors, each responsible for different aspects of the analysis and system design, integrated into a complete project.

## Contents

- **System Design Document:** PDF report detailing system elements, relationships, boundaries, complexity, sensitivity analysis, and chaos theory aspects.
- **LaTeX Source Code:** Complete source developed in Overleaf.
- **Diagrams:** System architecture diagrams and flowcharts.
- **References:** Bibliography of cited sources.

## 1. Review Workshop #1 Findings

### Main Findings

* **System Complexity:** Post-HCT survival is a highly complex, non-linear system requiring sophisticated modeling approaches.
* **Critical Equity Constraint:** The Stratified C-Index requires fair performance across all ethnic subgroups.
* **Sensitivity Analysis:** The system exhibits high sensitivity to variables like patient age, disease risk indices, and genetic compatibility, with small variations leading to significant outcome differences.

## 2. System Requirements

### Key Requirements

1. **Performance and Equity:** High overall predictive score with minimal dispersion of C-Index across racial/ethnic subgroups.
2. **Reliability:** Prediction intervals and uncertainty bounds with all risk stratification outputs.
3. **Interpretability:** Detailed explanations for individual predictions to support clinical adoption.

## 3. High-Level Architecture

The system uses a **Modular Pipeline Architecture** integrating equity checks throughout the data lifecycle.

### Architectural Overview

1. **Data Preprocessing:** Data cleaning, standardization, and equity-aware imputation.
2. **Equity Analysis:** Stratified analysis and bias detection on input data.
3. **Feature Selection:** Selection of robust, clinically relevant features.
4. **Predictive Modeling Core:** Ensemble approach combining Cox models and ML algorithms.
5. **Fairness Calibration:** Output adjustments to ensure similar accuracy across patient populations.
6. **Uncertainty Quantification:** Prediction intervals and uncertainty bounds.
7. **System Outputs:** Survival predictions, equity metrics dashboard, and interpretability outputs.

### Engineering Principles

* **Modularity:** Independent components for flexible updates.
* **Scalability:** Support for resource-intensive methods and large data volumes.
* **Robustness:** Ensemble methods and uncertainty quantification to handle sensitivity.

## 4. Addressing Sensitivity and Chaos

### Mitigation Strategies

* **Ensemble Modeling:** Multiple prediction models reduce dependence on single model parameters.
* **Uncertainty Quantification:** Confidence bounds manage inherent unpredictability.
* **Feature Engineering:** Clinical domain knowledge prevents over-reliance on unstable features.

### Monitoring

* **Concept Drift:** Performance monitoring stratified by ethnicity.
* **Data Drift:** Tracking high-sensitivity variables to detect population shifts.

## 5. Technical Stack

* **Core Language:** Python (3.10+)
* **Key Libraries:** scikit-survival, XGBoost, AIF360, Lifelines
* **Infrastructure:** Docker for containerization, MLflow for experiment tracking

### Implementation Patterns

1. **Preprocessing/Equity:** Data Transformer Pattern
2. **Modeling Core:** Ensemble Pattern (Stacking)
3. **Calibration/Uncertainty:** Decorator Pattern

---

The full analysis is available in the compiled report located in the repository.
