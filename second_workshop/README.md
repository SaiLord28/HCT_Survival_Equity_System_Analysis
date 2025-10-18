# Workshop 2: Kaggle Systems Design

## Overview

This repository contains the collaborative work of four team members for Workshop #2 of the Systems Analysis & Design course (2023). This project required a detailed analysis of a Kaggle competition, exploring its elements, relationships, sensitivity considerations, and chaos theory implications. As the integrator, I have compiled the contributions from all team members into this cohesive deliverable.

## Team Contribution

This work represents the combined effort of four contributors, each responsible for different aspects of the analysis and system design. This repository serves as a compilation and integration of these individual contributions into a complete project.

## Contents

- **System Design Document:** PDF report detailing identified elements, relationships, boundaries, complexity, sensitivity analysis, and reflections on chaos theory aspects.
- **LaTeX Source Code:** Complete source for the report developed in Overleaf.
- **Diagrams:** System architecture diagrams and flowcharts illustrating the proposed design.
- **References:** Bibliography of cited sources and materials used throughout the report.
- **Step-by-Step Guide:** Explanation of the workshop's development process and methodology.

## 1. Review Workshop #1 Findings

This section summarizes the critical outcomes from the initial systems analysis, which directly shaped the proposed architecture.

### How it was done 

The initial analysis, detailed in the Workshop #1 PDF, was reviewed to extract the core constraints and system behaviors.

### Main Findings

* **System Complexity and Non-linearity:** Post-HCT survival is a highly complex, non-linear system, making simple models insufficient to capture the patient's true trajectory.
* **Critical Equity Constraint:** The primary metric, the **Stratified C-Index**, mandates that model performance must be fair and consistent across all ethnic subgroups. Equity is a non-negotiable architectural requirement.
* **Chaos and Sensitivity:** The system exhibits high sensitivity to variables like **patient age**, **disease risk indices**, and **genetic compatibility**. Small variations in these inputs can lead to significant changes in prognosis, highlighting the need for robust design strategies.

## 2. Define System Requirements

The critical findings were translated into measurable design requirements, focusing on performance, reliability, and user-centric needs.

### How it was done 

The identified system weaknesses such as sensitivity and data disparities were converted into measurable performance goals for the final system.

### Key Requirements

1. **Performance and Equity:** The system must achieve a high overall predictive score while maintaining minimal dispersion (low standard deviation) of the C-Index across different racial/ethnic subgroups.
2. **Reliability (Uncertainty):** Given the high-stakes nature and system sensitivity, the design requires the provision of **Prediction Intervals** and **uncertainty bounds** with all risk stratification outputs, preventing overconfidence in a single point prediction.
3. **Interpretability:** The system must include a mechanism to generate detailed explanations for individual predictions (e.g., SHAP values) to support clinical adoption and auditing.

## 3. High-Level Architecture

The system utilizes a **Modular Pipeline Architecture** to address complexity and integrate equity checks throughout the data lifecycle.

### How it was done 

A sequential data processing pipeline was designed, explicitly incorporating modules dedicated to the constraints identified in Workshop #1 (Equity, Uncertainty).

### Architectural Overview

The architecture consists of seven interconnected modules:

1. **Data Preprocessing:** Handles data cleaning, standardization, and uses **equity-aware imputation methods** to address missing data.
2. **Equity Analysis:** Performs **stratified analysis** and applies **bias detection algorithms** on the input data to quantify disparities before modeling.
3. **Feature Selection:** Selects robust, clinically relevant features while avoiding those that might be systematically missing for certain demographic groups.
4. **Predictive Modeling Core:** The central prediction engine, employing an **Ensemble Approach** to combine Cox proportional hazards models with advanced Machine Learning algorithms like Gradient Boosting Machines (GBMs).
5. **Fairness Calibration:** A post-processing step that adjusts model outputs to guarantee similar prediction accuracy across different patient populations, directly optimizing the Stratified C-Index metric.
6. **Uncertainty Quantification:** Generates **prediction intervals** and associates uncertainty bounds with risk stratification to manage system sensitivity.
7. **System Outputs:** Delivers Survival Probability Predictions, a comprehensive **Equity Metrics Dashboard**, and **Model Interpretability Outputs**.

### Systems Engineering Principles

* **Modularity:** Separating concerns (e.g., modeling from calibration) ensures that different components can be updated independently without affecting the system's core integrity.
* **Scalability:** The pipeline design supports the implementation of resource-intensive Ensemble Methods and the large volume of CIBMTR data.
* **Robustness:** Achieved through the use of Ensemble Methods and the dedicated Uncertainty Quantification module.

## 4. Addressing Sensitivity and Chaos

The design implements specific strategies to mitigate the unpredictable and highly sensitive behavior of the post-HCT system.

### How it was done 

Design strategies were chosen based on Chaos Theory principles, focusing on dampening the "butterfly effect" (where small input changes lead to major output changes).

### Mitigation Strategies

* **Ensemble Modeling:** By combining multiple prediction models, the design reduces the dependence on a single model's parameters, making the final prediction more stable and robust against noise and random variations.
* **Uncertainty Quantification:** Providing confidence bounds formally manages the system's inherent unpredictability, informing clinicians when a prediction is less reliable.
* **Feature Engineering:** Integrating strong **Clinical Domain Knowledge** helps prevent the model from over-relying on spurious correlations or features that are prone to measurement instability.

### Monitoring Routines

The system includes essential monitoring routines for unanticipated conditions:

* **Concept Drift Monitoring:** Continuously evaluates the model's performance *stratified by ethnicity*. A drop in subgroup performance signals that the underlying medical concept may have changed, triggering a necessary retraining loop.
* **Data Drift Monitoring:** Tracks changes in the distribution of high-sensitivity input variables (Age, Risk Index) to detect shifts in the patient population that require model recalibration.

## 5. Technical Stack and Implementation Sketch

### How it was done 

The technical stack was chosen to support the specific requirements of survival analysis, ensemble modeling, and fairness assessment.

### Recommended Technical Stack

* **Core Language:** **Python** (3.10+). Justified by its robust ecosystem for Machine Learning and data science (e.g., `scikit-learn`, `NumPy`).
* **Key Libraries:** We rely on specialized libraries such as **`scikit-survival`** for time-to-event modeling, high-performance gradient boosters like **`XGBoost`** for the Ensemble Core, and **`AIF360`** for implementing the Fairness Calibration module.
* **Infrastructure:** **Docker** is essential for containerization, ensuring the system's **reproducibility** and **maintainability** across different environments.

### Implementation Patterns

1. **Preprocessing and Equity (M1, M2):** Implemented using the **Data Transformer Pattern** (Pipeline), where each transformation step (imputation, scaling, reweighting) is encapsulated and applied sequentially.
2. **Modeling Core (M4):** Uses an **Ensemble Pattern (Stacking)** where raw predictions from different models (Cox, GBM) are combined by a meta-learner for optimal stability.
3. **Calibration and Uncertainty (M5, M6):** These post-processing components are implemented using the **Decorator Pattern**, wrapping the raw output of the Modeling Core to apply necessary adjustments (fairness calibration and uncertainty calculation) without altering the core prediction logic.

---

The full analysis is available in the compiled report located in the repository.
