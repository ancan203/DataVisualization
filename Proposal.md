## Proposal: Investigating Health Disparities and Key Factors in Medical Outcomes

### Dataset Overview
This project utilizes two datasets:

- **Model Data (`model_dat.csv`)** – Contains 6,804 rows and 16 columns, detailing statistical models from various studies.  
  - Key fields: model numbers, outcomes, confidence intervals, stratification groups, and covariates.

- **Article Data (`article_dat.csv`)** – Comprises 318 rows and 65 columns, providing metadata on research articles.  
  - Key fields: study aims, locations, health outcomes, and demographic variables like race and ethnicity.

These datasets will be merged via the **DOI (Digital Object Identifier)** column to explore patterns in medical outcomes across different populations and study conditions.

### Why This Dataset?
Health disparities remain a pressing issue in medicine. Understanding how factors like race, study location, and treatment access influence outcomes can help bridge gaps in healthcare. By analyzing real-world research data, we can quantify disparities and identify key predictors of health outcomes.

### Research Questions

#### 1. How are race and ethnicity categorized in medical research, and what patterns emerge?
- **Which racial and ethnic groups are most frequently reported?**
- Are there inconsistencies or missing data in how race/ethnicity is recorded?
- How do sample sizes vary across groups, and what implications does this have for representation in research?

#### 2. What factors most strongly influence health outcomes across studies?
- We aim to determine which variables (e.g., access to care, study type, or treatment received) are most predictive of health disparities.

### Analysis Plan

#### Merging and Cleaning Data
- The datasets will be linked via **DOI**, ensuring each model is associated with its corresponding study.
- Missing values will be addressed through **imputation** or **filtering**, depending on the extent of the gaps.

#### Health Disparity Analysis
- Stratified comparisons of health outcomes (`point`, `lower`, `upper`) across demographic factors like `race` and `study_location`.
- Statistical tests (e.g., **t-tests**, **ANOVA**) to assess significant differences.
- Visualization through **confidence interval plots** and **bar charts**.

#### Predictive Modeling of Health Outcomes
- Identifying key predictors by analyzing **covariates**, `treatment_received`, and `access_to_care`.
- Running **regression models** to measure the impact of different factors on outcomes.
- Presenting results through **correlation matrices** and **coefficient plots**.

By following this approach, we aim to provide meaningful insights into health disparities and the driving forces behind medical outcomes.
