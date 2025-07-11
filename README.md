# Incidence of progression of Multiple Long Term Conditions
----------------------------------------------------------
**Authors**: _[placeholder]_

----------------------------------------------------------
### **Abstract**

**Background**

The burden of multiple long term conditions (MLTC) requires healthcare systems to respond through proactive disease prevention, however incidence in the context of MLTC is inconsistently defined and infrequently reported. We aimed to define and quantify measures of incidence designed to inform and evaluate preventative interventions.

**Methods**

We defined the MLTC progression rate as the incidence rate of events in which MLTC progresses through the acquisition of one or more conditions. We used the National Bridges to Health Segmentation Dataset to measure this across 49.6 million adults aged 20 years or older registered with a GP practice in England between April 2022 and March 2023. We defined and measured a novel metric, the progression rate ratio (PRR), which, if greater than one, quantifies an ‘acceleration effect’, where progression rate increases with condition count.

**Findings**

The crude MLTC progression rate per 100,000 person years from 0 to 1+ , 1 to 2+, and 2 to 3+ conditions was 4·33 95% CI [4·32, 4·34], 8·69 [8·67, 8·71], and 13·61 [13·58, 13·65] respectively. PRRs were greater than one in all age groups, with age-standardised progression rates three times higher for males in their fourth (PRR 2·99 [2·92, 3·06]) and fifth (PRR 3·08 [3·03, 3·13]) decade with two conditions than those with no conditions. The eight most frequent first conditions - depression, hypertension, cancer, diabetes, asthma, osteoarthritis, coronary heart disease, and osteoporosis - accounted for 79·4% of incident first conditions.

**Interpretation**

Acceleration of MLTC progression at population level suggests that early prevention of first conditions may have a disproportionate impact on health trajectory over the subsequent life course. Monitoring of progression rates over time may facilitate evaluation of the impact of preventative interventions on MLTC.

**Funding**

No dedicated funding


----------------------------------------------------------
### **Requirements**

**Data**:
- Access to the [National Bridges to Health Segmentation Dataset](https://outcomesbasedhealthcare.com/national-bridges-to-health-segmentation-dataset/) (and accompanying pipeline tables), NHS England UDAL Dataset ID 330
  
**Environment**:
This project was run in Azure Synapse Analytics, using Spark SQL, PySpark and R
- [![Spark](https://img.shields.io/badge/Spark-3.4.3-blue)](https://spark.apache.org/releases/spark-release-3-4-3.html)
- [![Python](https://img.shields.io/badge/Python-3.10.13-blue)](https://docs.python.org/3.13/whatsnew/changelog.html#python-3-10-13)
- [![R](https://img.shields.io/badge/R-4.4.1-blue)](https://cran.r-project.org/bin/windows/base/old/4.4.1/NEWS.R-4.4.1.html) 


R package requirements:
- Pre-installed in Azure Synapse
   - SparkR
   - ggplot2
   - patchwork
   - stringr
- To install as per steps in notebooks
   - PHEindicatormethods
   - svglite

----------------------------------------------------------
### **Contents**

⚠️**Note**: notebooks may not be rendered correctly in GitHub - suggested approach is to open notebooks in VSCode or Jupyter Notebook:

**Data preparation**:
- **[01A_incidence_subsegment_configuration](analysis/01A_incidence_subsegment_configuration.ipynb)**: selects conditions for inclusion
- **[01B_incidence_data_preparation](analysis/01B_incidence_data_preparation.ipynb)**:  creates person-level incidence base table, and aggregate person time denominator table

**Data results**:
- **[01C01_incidence_results_main_table](analysis/01C01_incidence_results_main_table.ipynb)**: calculates progression rates 
- **[01C02_incidence_results_main_table_PRRs](analysis/01C02_incidence_results_main_table_PRRs.ipynb)**: calculates Progression Rate Ratios (PRRs), and confidence intervals (for rates and PRRs)
- **[01D01_incidence_results_age_standardisation_inputs](analysis/01D01_incidence_results_age_standardisation_inputs.ipynb)**: creates input table for age standardisation, with incidence count numerators, person year denominators and the required standard population
- **[01D02_incidence_results_age_standardisation_outputs](analysis/01D02_incidence_results_age_standardisation_outputs.ipynb)**: calculates age-standardised rates and PRRs, split by socio-demographic breakdowns
- **[01E_incidence_results_trend](analysis/01E_incidence_results_trend.ipynb)**: calculates crude progression rates from 1 to 2+ conditions, and associated confidence intervals, by financial year
- **[01F_incidence_results_by_initial_condition_count](analysis/01F_incidence_results_by_initial_condition_count.ipynb)**: calculates crude progression rates, and associated confidence intervals, by initial condition count
- **[01G_incidence_results_first_conditions](analysis/01G_incidence_results_first_conditions.ipynb)**: calculates first condition incidence rates by condition, and associated confidence intervals
- **[01H01_incidence_results_all_conditions](analysis/01H01_incidence_results_all_conditions.ipynb)**: calculates condition-specific incidence rates, and associated confidence intervals, by age band

**Charts**:
- **[01D02_incidence_results_chart_01_age_gender_rates](analysis/01D02_incidence_results_chart_01_age_gender_rates.ipynb)**: produces side-by-side bar charts for progression rates by sex, age group and initial condition count
- **[01D02_incidence_results_chart_02_age_gender_prrs](analysis/01D02_incidence_results_chart_02_age_gender_prrs.ipynb)**: produces side-by-side bar charts for PRRs by sex, age group and initial condition count
- **[01D02_incidence_results_chart_03_imd_rates](analysis/01D02_incidence_results_chart_03_imd_rates.ipynb)**: produces side-by-side bar charts for progression rates by sex, IMD quintile and initial condition count
- **[01D02_incidence_results_chart_04_imd_prrs](analysis/01D02_incidence_results_chart_04_imd_prrs.ipynb)**: produces side-by-side bar charts for PRRs by sex, IMD quintile and initial condition count
- **[01D02_incidence_results_chart_05_ethnicity_rates](analysis/01D02_incidence_results_chart_05_ethnicity_rates.ipynb)**: produces side-by-side bar charts for progression rates by sex, ethnicity and initial condition count
- **[01D02_incidence_results_chart_06_ethnicity_prrs](analysis/01D02_incidence_results_chart_06_ethnicity_prrs.ipynb)**: produces side-by-side bar charts for PRRs by sex, ethnicity and initial condition count
- **[01D02_incidence_results_chart_07_imd_ethnicity_rates_0_1](analysis/01D02_incidence_results_chart_07_imd_ethnicity_rates_0_1.ipynb)**: produces side-by-side bar charts for progression rates from 0 to 1+ condition(s) by sex, ethnicity and IMD quintile
- **[01D02_incidence_results_chart_08_imd_ethnicity_rates_1_2](analysis/01D02_incidence_results_chart_08_imd_ethnicity_rates_1_2.ipynb)**: produces side-by-side bar charts for progression rates from 1 to 2+ conditions by sex, ethnicity and IMD quintile
- **[01D02_incidence_results_chart_09_imd_ethnicity_rates_2_3](analysis/01D02_incidence_results_chart_09_imd_ethnicity_rates_2_3.ipynb)**: produces side-by-side bar charts for progression rates from 2 to 3+ conditions by sex, ethnicity and IMD quintile
- **[01E_incidence_results_trend_chart_01](analysis/01E_incidence_results_trend_chart_01.ipynb)**: produces bar chart for progression rates from 1 to 2+ conditions by financial year, and corresponding box plots for incidence age distribution
- **[01F_incidence_results_by_initial_condition_count_chart_01](analysis/01F_incidence_results_by_initial_condition_count_chart_01.ipynb)**: produces bar chart for progression rates by initial condition count, and corresponding box plots for incidence age distribution
- **[01G_incidence_results_first_conditions_chart_01](analysis/01G_incidence_results_first_conditions_chart_01.ipynb)**: produces bar chart for progression rate from 0 to 1+ condition(s) by condition, and corresponding box plots for incidence age distribution
- **[01H02_incidence_results_all_conditions_plots](analysis/01H02_incidence_results_all_conditions_plots.ipynb)**: produces grid of line charts for incidence rates by condition, sex and age group

----------------------------------------------------------
### **Citation**

_[placeholder]_

----------------------------------------------------------
### **License**

See [Outcomes Based Healthcare Source Code License Agreement](/LICENSE.md)
