# Healthcare Insurance Claims and Fraud Risk Analysis

## Project Overview

Healthcare insurance companies process large volumes of claims. Reviewing every claim manually can be time-consuming and identifying unusual claim amounts, differences between requested and approved amounts and patterns that may require further investigation can be challenging.

In this project, I analysed a dataset containing 10,000 healthcare insurance claims using Python and Power BI. The objective was to understand claims performance, examine financial differences between requested and approved amounts and identify patterns associated with claims labelled as potentially fraudulent in the dataset.

The analysis combines exploratory data analysis in Python with an interactive Power BI dashboard. It demonstrates how claims data can be used to monitor financial patterns and prioritise cases for further review.

**Important:** This project uses synthetically generated data. The findings are exploratory and do not represent verified fraud cases from a real insurance company.

## Business Problem

The main business problem was to understand where unusual patterns existed within healthcare insurance claims and which areas could benefit from closer review.

The analysis focused on five questions:

1. What does the overall claims portfolio look like in terms of claim volume, claim amounts and approved amounts?
2. How are claims distributed across approved, rejected and pending statuses?
3. Do claim patterns differ across diagnosis codes and healthcare providers?
4. How do requested claim amounts and approved amounts differ between claims labelled as fraudulent and those not labelled as fraudulent?
5. Which patterns could help a claims review team prioritise cases for further investigation?

## Tools Used

**Python and Pandas**
- Data inspection and cleaning
- Missing-value handling
- Data type validation
- Duplicate checks
- Exploratory data analysis (EDA)
- Comparative analysis of claim amounts and fraud labels

**Power BI**
- Interactive dashboard development
- KPI cards and financial measures
- Trend analysis and category comparisons
- Date filters and slicers
- Diagnosis-level and provider-level analysis
- Financial risk indicator visualisations

## Dataset Description

- **Dataset name:** Healthcare Fraud Detection Dataset
- **Creator:** Nudrat Abbas
- **Source:** Kaggle
- **Licence shown on Kaggle:** CC0: Public Domain
- **Data type:** Synthetically generated
- **Dataset size:** 10,000 rows and 20 columns

The dataset contains claim identifiers, patient information, diagnosis and procedure codes, requested and approved amounts, submission dates, provider information, claim status and a fraud indicator.

Important fields include `Claim_ID`, `Provider_ID`, `Diagnosis_Code`, `Procedure_Code`, `Claim_Amount`, `Approved_Amount`, `Claim_Submission_Date`, `Days_Between_Service_and_Claim`, `Claim_Status`, `Provider_Specialty` and `Is_Fraud`.

### Data Source and Limitations

The dataset page on Kaggle identifies the data as synthetically generated and displays a CC0: Public Domain licence.

Synthetic data is useful for practising data analysis and dashboard development. However, it may not fully represent real-world healthcare claims, provider behaviour or fraud patterns.

The `Is_Fraud` column contains labels supplied with the dataset. The methodology used to assign these labels has not been independently verified.

Therefore, the analysis identifies patterns associated with the supplied labels rather than confirming actual fraudulent activity. Provider-level and diagnosis-level findings should be interpreted as potential review indicators only.

## Python Analysis

### 1. Data Inspection

I started by inspecting the dataset to understand its structure and the information available for analysis.

The initial checks included:
- Reviewing the first few records
- Checking column names and data types
- Examining summary statistics
- Checking missing values
- Identifying duplicate records
- Reviewing categorical and numerical values

These checks helped establish the quality of the data before conducting further analysis.

### 2. Data Cleaning and Validation

The dataset contained missing values in `Insurance_Type`, `Provider_Specialty` and `Prior_Visits_12m`.

- **Insurance Type:** 350 missing values were replaced with `Unknown`.
- **Provider Specialty:** 350 missing values were replaced with `Unknown`.
- **Prior Visits:** 350 missing values were retained as missing because a missing value does not necessarily mean zero previous visits.
- **Duplicate records:** No duplicate rows were found.
- **Procedure Code:** Converted to a string data type because it represents a code rather than a numerical measurement.
- **Financial validation:** Checked the relationship between claim amounts and approved amounts. No records were found where the approved amount exceeded the requested claim amount.

These steps helped preserve the meaning of the available data and reduce the risk of drawing conclusions from incorrect assumptions.

### 3. Exploratory Data Analysis

After cleaning the data, I examined claim volumes, financial amounts, claim statuses and the distribution of the dataset-provided fraud labels.

I also compared patterns across diagnosis codes and providers. This helped identify areas where the observed fraud-labelled rates differed from the overall dataset.

The analysis was designed to identify patterns for further investigation rather than make definitive judgements about individual patients or providers.

## Power BI Dashboard

The Power BI report contains three pages. Each page addresses a different part of the business problem.

### Page 1: Claims Overview

This page provides an overall view of claims performance and financial exposure.

It includes KPI cards for:
- Total Claims
- Fraud-Labelled Rate
- Total Claim Amount
- Total Approved Amount
- Average Claim Amount

A monthly claims trend chart helps explore changes in claim volumes over time. A claims status donut chart shows the distribution of claims across approved, rejected and pending categories.

Date, insurance type and claim status slicers allow users to explore different parts of the portfolio.

### Page 2: Diagnosis and Provider Analysis

This page examines differences across diagnosis codes and healthcare providers.

It includes:
- Fraud-labelled rate by diagnosis code
- Top 10 providers by claim volume
- Top 10 providers by fraud-labelled rate

Provider specialty, patient gender and patient state filters allow users to explore the results across different categories.

Provider-level rates should always be considered alongside the number of claims behind each rate. A high rate based on a relatively small number of records may be less stable than a similar rate based on a larger sample.

These rankings are intended to support further review and should not be interpreted as evidence of wrongdoing.

### Page 3: Fraud Risk Analysis

This page compares the financial patterns of claims labelled as fraudulent and claims not labelled as fraudulent.

It includes:
- Average claim amount compared with average approved amount by fraud label
- Average claim approval gap by fraud label
- Claim submission delay and prior visit filters

These comparisons help highlight financial patterns that may be useful when prioritising claims for further review. They do not establish that a claim is fraudulent.

## Key Findings

The following figures describe the full dataset. Dashboard figures may vary when filters are applied.

### 1. Overall Claims Portfolio

- Total claims: 10,000
- Average requested claim amount: 572.80
- Average approved amount: 475.51

These figures provide a baseline for understanding the financial profile of the dataset.

### 2. Distribution of Fraud Labels

- Claims labelled as fraudulent: 829
- Claims not labelled as fraudulent: 9,171
- Fraud-labelled rate: 8.29%

This percentage represents the distribution of the supplied dataset labels. It should not be interpreted as a verified fraud rate for a real insurance company.

### 3. Diagnosis-Level Patterns

Diagnosis code `I25.10` had 1,025 claims, including 102 fraud-labelled claims. Its observed fraud-labelled rate was approximately 9.95%.

Diagnosis code `F41.9` had the lowest observed fraud-labelled rate at approximately 6.71%.

These differences suggest that diagnosis-level analysis can help identify patterns for further investigation. They do not establish that any particular diagnosis is associated with confirmed fraud.

### 4. Provider-Level Patterns

Provider `P0086` had the highest observed fraud-labelled rate at approximately 42.11% across 38 claims.

Other providers also showed elevated rates in the dataset.

These results are potential review indicators only. Claim volumes, underlying case details and the reliability of the supplied labels should be considered before drawing conclusions about any provider.

### 5. Differences in Claim Amounts

The average claim amount was:
- Fraud-labelled claims: 990.93
- Claims not labelled as fraudulent: 535.01

The average approved amount was:
- Fraud-labelled claims: 545.87
- Claims not labelled as fraudulent: 469.15

The average difference between requested and approved amounts was:
- Fraud-labelled claims: 445.06
- Claims not labelled as fraudulent: 65.85

The results show a substantial difference in the average financial gap between the two groups. This makes the gap a useful measure to examine when identifying claims that may require additional review.

These are observed differences within synthetic data and should not be assumed to hold in actual insurance operations.

## Business Recommendations

### 1. Prioritise Claims with Unusual Financial Differences

Claims with unusually large differences between requested and approved amounts could be prioritised for a closer review of supporting documentation, policy coverage and approval decisions.

A large difference alone should not be treated as evidence of fraud.

### 2. Review Patterns Alongside Claim Volumes

Diagnosis and provider-level patterns can help guide further investigation. Review decisions should consider the number of claims and relevant case details rather than relying only on a percentage or ranking.

### 3. Monitor Claim Amounts and Approval Patterns

Claims teams could monitor average claim amounts, approved amounts and the gap between them over time. This may help identify changes in financial patterns that deserve further investigation.

### 4. Use Multiple Indicators Before Escalating a Claim

A review process should consider several indicators together, including claim amount, approval gap, submission delay, prior visits and relevant supporting documents.

No single indicator should be used as proof of fraudulent activity.

### 5. Improve Data Quality and Label Transparency

Before using a model or dashboard for operational decisions, an organisation should understand how fraud labels were assigned and validate their accuracy. Missing data and other data quality issues should also be investigated.

## Project Limitations

- The dataset is synthetically generated and does not represent verified claims data from a named insurance company.
- The methodology used to assign the `Is_Fraud` labels has not been independently verified.
- The findings describe patterns within the supplied dataset and do not confirm actual fraud.
- Provider-level rates may be influenced by the number of claims available for each provider.
- The analysis is exploratory. Results should be validated against appropriate evidence and investigation procedures before being used for operational decisions.

## Conclusion

This project demonstrates how Python and Power BI can be used together to explore healthcare insurance claims and present findings in a business-focused format.

Python was used to inspect, clean and analyse the dataset. Power BI was used to turn the analysis into an interactive dashboard covering claims performance, diagnosis and provider patterns and differences in financial amounts.

The key takeaway is that combining claim volumes, financial differences and multiple risk indicators can help prioritise cases for further review. The project also highlights the importance of data quality, transparent labelling and careful interpretation when working with synthetic fraud-labelled data.

## Skills Demonstrated

Python, Pandas, data cleaning, exploratory data analysis, data validation, Power BI, dashboard development, KPI reporting, data visualisation, financial analysis and business recommendations.
