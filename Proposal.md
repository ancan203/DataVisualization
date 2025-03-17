# Proposal: Investigating Health Disparities and Key Factors in Medical Outcomes
## Members:

- Nguyen Canh Huy
- Can Ha An
- Dao Chi Tuong

## Dataset Details 
### **Dataset name:** **Academic Literature on Racial and Ethnic Disparities in Reproductive Medicine in the US**

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

## Research Questions and Analysis Plan
### Preprocessing: Data Integration & Cleaning
- Merge `model_dat.csv` and `article_dat.csv` using `doi`.
- Handle missing values and inconsistencies in `race1` and `eth1` via interpolation or deletion, depending on the extent of missing data.

### Question 1: How are race and ethnicity categorized in medical research?
We examine how racial and ethnic categories are recorded across studies, identify inconsistencies or missing data, and assess representation.

#### Key Variables:
- **Race/Ethnicity Categorization**: `race1`, `eth1` (Primary categories in studies)
- **Study Metadata**: `study_location`, `year`, `journal`
- **Data Quality Indicators**: Missing values or inconsistencies in `race1`, `eth1`

#### Approach:
1. **Distribution Analysis**
   - Count occurrences of racial/ethnic groups to identify most frequently reported groups.
   - Compare representation across study locations and time periods.
2. **Data Completeness & Consistency**
   - Identify missing or ambiguous values in `race1` and `eth1`.
   - Analyze variations in racial/ethnic categorization across studies.
3. **Sample Size Disparities**
   - Investigate variations in sample sizes by racial/ethnic group.
   - Assess underrepresentation of certain groups.

#### Potential Visualizations:
- **Bar charts & histograms**: Frequency of racial/ethnic groups by year/study location.
- **Heatmaps**: Patterns of missing racial/ethnic data.
- **Box plots**: Sample size distribution across groups.

### Question 2: What factors influence health outcomes across studies?
We identify variables (e.g., access to care, study type, treatment received) that predict health disparities in reproductive medicine.

#### Key Variables:
- **Health Outcomes**: `outcome` (Medical conditions/results)
- **Predictors of Health Disparities**:
  - `treatment_received`, `access_to_care` (Healthcare access/treatment indicators)
  - `measure` (Statistical measure: odds ratio, risk ratio)
  - `point`, `lower`, `upper` (Effect sizes & confidence intervals)
  - `subgrp`, `stratgrp` (Demographic stratifications)

#### Approach:
1. **Correlation Analysis**
   - Assess associations between healthcare access (`treatment_received`, `access_to_care`) and health outcomes (`outcome`).
   - Identify health conditions most linked to disparities in care.
2. **Effect Size Comparison**
   - Analyze odds ratios and risk ratios (`point`, `lower`, `upper`).
   - Compare effect sizes across racial/ethnic subgroups (`subgrp`).
3. **Predictive Modeling (if feasible)**
   - Build regression models to determine key predictors of negative health outcomes.
   - Examine how disparities change when controlling for demographics (`subgrp`, `stratgrp`).

#### Potential Visualizations:
- **Box plots & violin plots**: Effect size comparisons (e.g., odds ratios) across treatment groups.
- **Scatter plots**: Relationship between access to care and health outcomes.
- **Regression coefficient plots**: Identifying key predictors of disparities.
