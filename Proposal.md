# Proposal: Investigating Health Disparities and Key Factors in Medical Outcomes
## Members:

- Nguyen Canh Huy
- Can Ha An
- Dao Chi Tuong

## Dataset 
### **Dataset name:** Academic Literature on Racial and Ethnic Disparities in Reproductive Medicine in the US

### **Dataset Provenance**:

The dataset we are using was explored in the July 2023 article a review article [Racial and ethnic disparities in reproductive medicine in the United States: a narrative review of contemporary high-quality evidence](https://www.ajog.org/article/S0002-9378(24)00775-0/fulltext), published in the *American Journal of Obstetrics and Gynecology* in January 2025. The original paper focuses on the racial and ethnic inequities in ob/gyn. The dataset suggestion is credited to [Kat Correia from Amherst College](https://github.com/katcorr).

The dataset consists of two related tables, **`article_dat.csv`** and **`model_dat.csv`**. **`article_dat.csv`** contains metadata for articles published in medical journals, including bibliographic identifiers (PubMed ID, DOI), journal details, publication date, and study characteristics. The **`model_dat.csv`** file focuses on statistical models within these articles: model numbers, stratification details, subanalysis, outcome measures, effect size estimates (e.g., odds ratio, risk ratio), covariates, and confidence intervals.

### **Dataset Dimensions**:

#### 1. Model Data (`model_dat.csv`)
- **Provenance**: Extracted from medical research studies.
- **Dimensions**: 6,804 rows × 16 columns.
- **Key Variables**:
  - `doi`: Unique study identifier.
  - `model_number`: Statistical model reference.
  - `outcome`: Health outcome analyzed.
  - `measure`: Reported statistical measure (e.g., odds ratio).
  - `point`, `lower`, `upper`: Estimate and confidence intervals.
  - `stratgrp`, `subgrp`: Stratification variables (e.g., demographics).

#### 2. Article Data (`article_dat.csv`)
- **Provenance**: Metadata on medical research articles.
- **Dimensions**: 318 rows × 65 columns.
- **Key Variables**:
  - `doi`, `pmid`: Study identifiers.
  - `journal`, `year`, `title`, `abstract`: Study metadata.
  - `study_location`: Geographic study area.
  - `race1`, `eth1`: Reported racial and ethnic categories.
  - `health_outcome`: Primary health outcome studied.
  - `treatment_received`, `access_to_care`: Healthcare access and treatment indicators.

The datasets are merged via `doi` to connect study-level information with statistical models, allowing for in-depth analysis of research representation and health disparities.

## Why This Dataset?
This dataset provides a rich and structured source of information on medical research, particularly in the context of healthcare disparities and gynecological health outcomes, both article-level and model-level. It allows for exploration of how different factors contribute to various gynecological conditions and how they have been studied over time, and allows us to quantify disparities and identify key predictors of health outcomes.

## Research Questions

### 1. How are race and ethnicity categorized in medical research, and what patterns emerge?
- **Which racial and ethnic groups are most frequently reported?**
- Are there inconsistencies or missing data in how race/ethnicity is recorded?
- How do sample sizes vary across groups, and what implications does this have for representation in research?

### 2. What factors most strongly influence health outcomes across studies?
- We aim to determine which variables (e.g., access to care, study type, or treatment received) are most predictive of health disparities.

## Analysis Plan

### Merging and Cleaning Data
- The datasets will be linked via **DOI**, ensuring each model is associated with its corresponding study.
- Missing values will be addressed through **interpolation** or **filtering**, depending on the extent of the gaps.

### For Question 1: Health Disparity Analysis
- Stratified comparisons of health outcomes (`point`, `lower`, `upper`) across demographic factors like `race` and `study_location`.
- Statistical tests (e.g., **t-tests**, **ANOVA**) to assess significant differences.
- Visualization through **confidence interval plots** and **bar charts**.

### For Question 2: Predictive Modeling of Health Outcomes
- Identifying key predictors by analyzing **covariates**, `treatment_received`, and `access_to_care`.
- Running **regression models** to measure the impact of different factors on outcomes.
- Presenting results through **correlation matrices** and **coefficient plots**.

By following this approach, we aim to provide meaningful insights into health disparities and the driving forces behind medical outcomes.
