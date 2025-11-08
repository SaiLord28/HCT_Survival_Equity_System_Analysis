# Workshop 3: Robust System Design and Project Management

## Overview

This repository contains collaborative work for Workshop #3 of the Systems Analysis & Design course (2025). We refined the HCT Survival Prediction system architecture with robust engineering principles, performed comprehensive risk analysis, and established a project management plan for the 4-week implementation sprint (November 8 - December 5, 2025).

## Team Contribution

This work represents the combined effort of four contributors, each responsible for different aspects of robust design, risk mitigation, and project management, integrated into a complete operational plan.

## Contents

- **Robust Design Document:** PDF report detailing architecture refinement, quality standards alignment (ISO 9000, CMMI, Six Sigma), risk analysis, and project management plan.
- **LaTeX Source Code:** Complete source with proper citations and formatting.
- **Diagrams:** Updated system architecture and 4-week project timeline (Gantt chart).
- **References:** Bibliography of 30+ cited sources.

## 1. Incremental Improvements from Workshops 1-2

### Evolution Pattern

* **Workshop 1 → Workshop 2:** Identified chaos/sensitivity challenges → Designed Uncertainty Quantification Module (M6) with confidence intervals.
* **Workshop 2 → Workshop 3:** Had architecture but lacked operational controls → Added monitoring framework with concrete thresholds and response protocols.

### Key Progression

Workshop 1 (Problem Identification) → Workshop 2 (Solution Architecture) → Workshop 3 (Operational Quality Control)

## 2. Refined System Architecture

### 7-Module Pipeline (Maintained from Workshop 2)

The architecture remains unchanged but now explicitly addresses reliability, scalability, maintainability, and fault-tolerance:

1. **M1: Data Preprocessing** - Equity-aware imputation with fallback strategies
2. **M2: Equity Analysis** - QA component with stratified analysis and bias detection
3. **M3: Feature Selection** - Cross-demographic validation to prevent bias
4. **M4: Predictive Modeling Core** - Ensemble methods (Cox, RSF, GBM) for stability
5. **M5: Fairness Calibration** - Primary QC mechanism enforcing stratified C-index
6. **M6: Uncertainty Quantification** - Manages chaos/sensitivity with confidence intervals
7. **M7: System Outputs** - SHAP interpretability and equity dashboards

### Robust Design Principles

* **Modularity:** Versioned interfaces; updating M5 doesn't touch M4
* **Scalability:** M4 scales independently via parallel CV folds
* **Maintainability:** Configuration separated from code; MLflow tracks experiments
* **Fault-Tolerance:** M1 triggers fallback imputation when missingness >30%; errors don't cascade

### Standards Alignment

* **ISO 9000:** Customer focus via M7 interpretability; continuous improvement via M2-M5 feedback loop
* **CMMI Level 3:** Defined process with documented module interfaces; MLflow maintains process assets
* **Six Sigma:** "Defect" = inequity (disparity >0.10); M5 acts as Control mechanism

## 3. Risk Analysis and Mitigation

### Identified Risks

**Technical Risks:**
1. **Emergent Behaviors:** Non-linearities causing unpredictable outputs
2. **Feature Selection Bias (M3):** Indices that don't maintain equity
3. **Input Data Quality:** "Garbage in, garbage out" scenarios

**Implementation Risks:**
4. **Data Quality Worse Than Expected:** Missingness exceeding 30% threshold
5. **Model Accuracy Lower Than Goal:** Not achieving C-index >0.70
6. **Schedule and Team Availability:** Tasks taking longer than estimated

### Mitigation Strategies

* **For Emergent Behaviors:** Decision support only (no full automation); continuous monitoring; sensitivity analysis; ensemble diversity
* **For Feature Bias:** Fairness as explicit objective; fairness-aware preprocessing (reweighing); multiple selection strategies
* **For Data Quality:** Robust imputation (MICE/KNN); train with noise; metadata logging; exhaustive documentation
* **For Schedule Risks:** Work redistribution; task prioritization; buffer in Week 4; early escalation

### Monitoring Framework

Risk monitoring table with specific metrics, alert thresholds, and response protocols:
- Emergent instability: Std. dev. >0.15 → Sensitivity analysis
- Selection bias: C-index gap >0.10 → Apply reweighing
- Data quality: Missingness >30% → Advanced imputation
- Model drift: C-index drop >5% → Retrain and recalibrate
- Schedule delay: >2 days behind → Team meeting and escalation
- Milestone risk: Success criteria unmet → Block progression

## 4. Project Management Plan

### Team Roles and Responsibilities

**Sergio Mendivelso - Programmer (20-25h/week)**
* Write and test code for M1-M7
* Manage GitHub repository
* Final deliverable: predictions.csv

**Sergio Moreno - Project Coordinator (5-8h/week)**
* Organize meetings and communication
* Track progress and manage deadlines
* Final deliverable: Submission coordination

**Juan Otalora - Data Analyst (15-20h/week)**
* Clean data and analyze fairness (M1-M3)
* Validate results
* Final deliverable: Technical report (8-10 pages)

**Juan Diego Moreno - Quality Specialist (10-15h/week)**
* Testing and validation
* Quality assurance checks
* Final deliverable: QA report

### 4-Week Timeline (Nov 8 - Dec 5, 2025)

**Week 1 (Nov 8-14) - Milestone M1: Kickoff Complete**
* Deliverables: Project charter, data overview, GitHub setup
* Success criteria: Team understands goals; dataset accessible; environment ready

**Week 2 (Nov 15-21) - Milestone M2: Data Ready**
* Deliverables: Cleaned dataset, fairness analysis, data processing functions
* Success criteria: Data clean; missing values handled; features selected

**Week 3 (Nov 22-28) - Milestone M3: Models Working**
* Deliverables: Working models, accuracy results, fairness validation
* Success criteria: C-index >0.70; fairness gap <0.10; code documented

**Week 4 (Nov 29 - Dec 5) - Milestone M4: Project Delivered**
* Deliverables: Final predictions.csv, code documentation, technical report, presentation
* Success criteria: All deliverables complete; submitted on time

### Communication Protocol

* **Weekly Monday Meetings:** 9:00 AM, 15 minutes (completed work, plans, blockers)
* **Daily Updates:** Slack/WhatsApp for quick questions
* **Friday Professor Reviews:** Optional guidance sessions
* **Tools:** GitHub (code), Python (development), MLflow (tracking), Slack/WhatsApp (communication)

## 5. Success Criteria

### Technical Goals
* Prediction model works accurately (stratified C-index >0.70)
* Fairness similar across all demographic groups (gap <0.10)
* Code clean and well-documented with passing tests

### Project Goals
* All 4 milestones completed on time
* Team collaboration effective with clear communication
* Final submission by December 5, 2025

### Learning Goals
* Team learns about fairness in machine learning
* Team practices data analysis and prediction techniques
* Team develops teamwork and project management skills

## 6. Repository Structure
```
HCT-Survival-Prediction/
|-- data/
|   |-- raw/           # Original dataset
|   |-- processed/     # Cleaned data
|   +-- predictions/   # Final predictions.csv
|-- src/
|   |-- preprocessing.py    # M1: Data Preprocessing
|   |-- equity.py           # M2: Equity Analysis
|   |-- features.py         # M3: Feature Selection
|   |-- models.py           # M4: Predictive Modeling
|   |-- calibration.py      # M5: Fairness Calibration
|   |-- uncertainty.py      # M6: Uncertainty Quantification
|   +-- outputs.py          # M7: System Outputs
|-- tests/                  # Unit and integration tests
|-- docs/
|   |-- reports/            # Analysis and technical reports
|   +-- presentation/       # Final presentation
|-- requirements.txt        # Python dependencies
+-- README.md               # Setup and usage instructions
```
