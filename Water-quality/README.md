# Multi-Layer Water Quality Risk & Regulatory Analytics System
Author: Gabriella Marín
Chemical Engineer · Environmental Engineering Specialist
Data Analyst | AI Engineer (in progress)
Location: Colombia
Tools: Python, SQL (SQLite), Pandas, Power BI
Domain: Environmental Engineering · Water Quality · Regulatory Analytics

---
## Project Overview
Traditional water quality assessments frequently rely on binary compliance checks (pass/fail) against regulatory limits. However, environmental monitoring programs often require multi-standard evaluation, contextual interpretation, and prioritization of risk across different regulatory frameworks.

This project implements a multi-layer regulatory risk analytics system that transforms traditional compliance logic into a continuous, regulation-aware risk framework.

Instead of evaluating water quality against a single standard, the system:

- Applies multiple regulatory frameworks simultaneously(Colombia + EPA benchmarks)
- Separates sanitary risk from environmental discharge risk
- Quantifies continuous risk scores (0–100) instead of binary outcomes
- Preserves traceability between measurements, regulatory limits, and risk results
- Produces decision-ready outputs for territorial prioritization and BI dashboards

The architecture reflects real monitoring conditions, including:
- heterogeneous parameters
- incomplete measurements
- regulatory context dependence

---
## Objectives
- Model water quality evaluation as a normative-dependent risk problem
- Apply Colombian regulations and EPA benchmarks computationally
- Quantify severity and frequency of violations across layers
- Compare regulatory thresholds across jurisdictions
- Enable prioritization of samples, monitoring sites, and territories
- Generate BI-ready datasets for executive reporting dashboards

---
## Dataset Context
The dataset used in this project contains water quality measurements collected from monitoring locations across Colombia between 2005 and 2024.

The original purpose of the monitoring program is not explicitly specified in the dataset, meaning that the samples may correspond to different monitoring objectives such as environmental surveillance, water body monitoring, or other regulatory programs.

Therefore, this project approaches the dataset with an exploratory analytical objective, applying different regulatory frameworks to understand how the same set of measurements behaves under different regulatory interpretations.

---
## Regulatory Frameworks Integrated
- Colombian potable water regulation (Resolución 2115)
  Defines quality standards for drinking water intended for human consumption.
- Colombian discharge regulation (Resolución 0631)
  Establishes permissible discharge limits for wastewater and environmental impacts.
- EPA benchmark thresholds (reference comparison layer)
  Reference thresholds from the U.S. Environmental Protection Agency for potable water quality.
The architecture supports adding additional regulatory layers.

Important interpretation note:

The analyzed samples do not necessarily represent treated or potable water sources. Therefore, non-compliance with drinking water standards is expected and should be interpreted as a comparative risk indicator, rather than as an operational failure of a drinking water system.

The environmental discharge regulation (Resolution 0631) provides an additional environmental perspective, allowing the evaluation of contamination pressure even when potable standards are not met.
---
## Project Structure
01-water-quality-normative/
│
├── datos_calidad_del_agua_2005_2024.xlsx
│
├── data/
│   └── water_quality_analysis.db
│
├── norms/
│   └── norm_limits_master.csv
│
├── outputs/
│   ├── phase1_sample_wide.csv
│   ├── phase4_layer_risk_scores.csv
│   ├── phase4_sanitary_risk_comparison_CO_vs_EPA.csv
│   ├── phase5_sample_reporting.csv
│   ├── phase5_point_risk_summary.csv
│   ├── phase5_municipality_risk_summary.csv
│   ├── phase5_department_risk_summary.csv
│   └── phase5_sanitary_vs_discharge_matrix.csv
│
├── notebooks/
│   ├── 01_data_exploration.ipynb
│   ├── 02_data_cleaning_and_standardization.ipynb
│   ├── 03_normative_compliance_sql.ipynb
│   ├── 04_risk_scoring_and_prioritization.ipynb
│   └── 05_aggregation_and_reporting.ipynb
│
└── README.md

---
## Methodlogy (By phase)

# Phase 0 — Dataset Suitability & Scope Redefinition

- Evaluation of dataset realism and regulatory applicability
- Parameter coverage and missingness analysis
- Identification of structural limitations
- Scope refinement toward official monitoring data

# Phase 1 — Data Preparation
- Cleaning and standardization
- Unit harmonization
- Handling censored and missing values
- Construction of sample-level analytical table (long → wide transformation)

# Phase 2 — Relational Modeling (SQL Architecture)
- Separation of measurements, regulations, and evaluation layers
- Design of dimension and fact tables
- Implementation of traceable relationships
- Scalable compliance-ready schema

# Phase 3 — Normative Compliance Computation
- Parameter-level compliance evaluation
- Deviation magnitude calculation
- Multi-standard comparison logic
- Full traceability between samples and regulatory limits

# Phase 4 — Risk Scoring & Prioritization
- Continuous risk scoring (0–100)
- Severity-weighted violations
- Frequency-based penalization
- Critical violation flags
- Sanitary risk comparison: Colombia vs EPA

# Phase 5 — Aggregation & Reporting
- Aggregation by monitoring point, municipality, and department
- Sanitary vs discharge risk matrix
- BI-ready structured outputs
- Reporting tables for Power BI integration

# Power BI Dashboard
The final outputs feed an interactive Power BI dashboard that allows exploration of:
- Distribution of sanitary risk scores
- Comparison of Colombian and EPA drinking water standards
- Environmental discharge risk under Resolution 0631
- Territorial distribution of risk indicators
- Cross-regulatory risk relationships

The dashboard enables multi-layer regulatory interpretation of the monitoring dataset.
---
## Key Analytical Findings
From 6,818 analyzed samples, the system produced several key insights:

- The average sanitary risk score under Resolution 2115 is 55.6, while the average risk under EPA standards is slightly lower (52.8).
- The average difference between both regulatory frameworks is −2.8, suggesting that EPA thresholds tend to produce slightly lower risk scores for the same dataset.
- The average environmental discharge risk under Resolution 0631 is significantly lower (15.1).
- Approximately 95.4% of the samples show at least one critical violation when evaluated against potable water standards, which is consistent with the fact that the dataset likely represents untreated environmental water sources.
- Importantly, while many samples exceed potable water thresholds, the relatively low environmental discharge risk suggests that the monitored waters are not necessarily severely contaminated from an environmental perspective
  
---
# Strategic & Regulatory Impact
This system demonstrates how environmental monitoring can evolve from static compliance checks into structured, multi-layer risk intelligence.

It enables:

- Data-driven inspection prioritization
- Regulatory benchmarking across jurisdictions
- Risk-based territorial management
- Executive-level environmental dashboards
- Scalable integration into environmental governance systems

---
# How to Reproduce
- Clone repository
- Run notebooks sequentially (Phase 1 → Phase 5)
- Generate outputs in /outputs
- Connect aggregated tables to Power BI
- Explore risk layers and territorial prioritization

--- 
# Executive Conclusion
Water quality monitoring frequently relies on binary compliance models that fail to capture severity, recurrence, and regulatory context.

This project proposes a structured, traceable, and risk-based analytical framework that:

- Integrates multiple regulatory standards
- Quantifies deviation magnitude instead of pass/fail status
- Separates sanitary and environmental regulatory layers
- Enables territorial and strategic prioritization

Water quality monitoring frequently relies on binary compliance models that fail to capture severity, recurrence, and regulatory.