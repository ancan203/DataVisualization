# Proposal: Investigating Health Disparities and Key Factors in Medical Outcomes

## Members:
- Nguyen Canh Huy
- Can Ha An
- Dao Chi Tuong

## Dataset Details

### Dataset Name
**Academic Literature on Racial and Ethnic Disparities in Reproductive Medicine in the US**

### Dataset Provenance
The dataset we are using was explored in the July 2023 article [Racial and ethnic disparities in reproductive medicine in the United States: a narrative review of contemporary high-quality evidence](https://www.ajog.org/article/S0002-9378(24)00775-0/fulltext), published in the *American Journal of Obstetrics and Gynecology* in January 2025. The original paper focuses on racial and ethnic inequities in ob/gyn. The dataset suggestion is credited to [Kat Correia from Amherst College](https://github.com/katcorr).

The dataset consists of two related tables, `article_dat.csv` and `model_dat.csv`. `article_dat.csv` contains metadata for articles published in medical journals, including bibliographic identifiers (PubMed ID, DOI), journal details, publication date, and study characteristics. The `model_dat.csv` file focuses on statistical models within these articles: model numbers, stratification details, subanalysis, outcome measures, effect size estimates (e.g., odds ratio, risk ratio), covariates, and confidence intervals.

### Dataset Dimensions

#### Model Data (`model_dat.csv`)
- **Provenance**: Extracted from medical research studies.
- **Dimensions**: 6,804 rows × 16 columns.
- **Key Variables**:
  - `doi`: Unique study identifier.
  - `model_number`: Statistical model reference.
  - `outcome`: Health outcome analyzed.
  - `measure`: Reported statistical measure (e.g., odds ratio).
  - `point`, `lower`, `upper`: Estimate and confidence intervals.
  - `stratgrp`, `subgrp`: Stratification variables (e.g., demographics).

#### Article Data (`article_dat.csv`)
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
This dataset provides a rich and structured source of information on medical research, particularly in the context of healthcare disparities and gynecological health outcomes, both article-level and model-level. It allows exploration of how different factors contribute to various gynecological conditions, quantifying disparities, and identifying key predictors of health outcomes.

## Research Questions and Analysis Plan

### Preprocessing: Data Integration & Cleaning
- Merge `model_dat.csv` and `article_dat.csv` using `doi`.
- Analyze missing data patterns using visualizations such as Missingno matrix and bar plots.
- Depending on the extent and type of missingness, apply deletion (for minimal missingness) or imputation methods such as K-Nearest Neighbor (KNN) imputation.

---

### Question 1: How are race and ethnicity categorized in medical research?
We examine how racial and ethnic categories are recorded and represented across studies.

#### Key Variables
- **Race/Ethnicity Categorization**: Explicitly defined categories: White, Black or African American, Hispanic or Latino, Asian, Indigenous, Other/Multiracial. Categories with insufficient representation will be noted.
- **Study Metadata**: `study_location`, `year`, `journal`
- **Representation in Literature**: `abstract`, `title`

#### Approach
1. **Distribution Analysis**
   - Count occurrences to identify frequently reported racial/ethnic groups.
   - Compare representation by location and over time.
   - Identify underrepresented groups.

2. **Thematic Context Analysis (Interactive Visualization)**
   - Create an interactive bar chart showing group frequencies.
   - Dynamically generate word clouds from abstracts upon clicking bar chart elements.

#### Visualizations
- Interactive bar chart + word clouds.

#### Expected Deliverables
- Summary analysis of racial/ethnic distribution.
- Visualizations: bar charts, word clouds.

---

### Question 2: What factors influence health outcomes across studies?
Identify key predictors of health disparities, such as healthcare access (`access_to_care`), treatment received (`treatment_received`), and demographics (`stratgrp`, `subgrp`).

#### Key Variables
- **Health Outcomes**: `outcome`
- **Predictors of Health Disparities**:
  - `treatment_received`, `access_to_care`
  - Effect sizes (`measure`, `point`, `lower`, `upper`)
  - Demographics (`subgrp`, `stratgrp`)

#### Approach
1. **Correlation Analysis**
   - Assess associations between healthcare access and outcomes.
   - Identify conditions linked to care disparities.

2. **Effect Size Comparison**
   - Analyze and compare odds ratios and risk ratios.
   - Visualize disparities using forest plots.

3. **Predictive Modeling (if feasible)**
   - Conduct predictive modeling if minimum criteria are met (≥500 complete cases, <20% missingness).
   - Build regression models identifying key outcome predictors.

#### Potential Visualizations
- Box plots & violin plots (effect sizes)
- Scatter plots (healthcare access vs. outcomes)
- Forest plots (effect sizes and confidence intervals)
- Regression coefficient plots (key predictors)

#### Expected Deliverables
- Statistical report detailing health disparity correlations.
- Visualizations: scatter plots, box plots, forest plots, regression coefficient plots.
- Predictive model output and interpretation.

