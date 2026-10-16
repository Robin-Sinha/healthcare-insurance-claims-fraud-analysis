# Healthcare Insurance Claims and Fraud Risk Analysis

## Project Overview

Healthcare insurance companies process a large number of claims every day. Reviewing every claim manually can be time consuming and it can become difficult to identify unusual claim amounts, differences between requested and approved amounts and patterns that may require further investigation.

In this project, I analysed a dataset containing 10,000 healthcare insurance claims using Python and Power BI. The objective was to understand claims performance, examine financial differences between claims and approved amounts and identify patterns associated with claims labelled as potentially fraudulent in the dataset.

The analysis combines exploratory data analysis in Python with an interactive Power BI dashboard. The findings can help illustrate how claims data can support better monitoring and prioritisation of claims for further review.

## Business Problem

The main business problem was to understand where unusual patterns existed within healthcare insurance claims and which areas could benefit from closer review.

The analysis focused on five questions.

1. What does the overall claims portfolio look like in terms of claim volume, claim amounts and approved amounts?
2. How are claims distributed across approved, rejected and pending statuses?
3. Do claim patterns differ across diagnosis codes and healthcare providers?
4. How do requested claim amounts and approved amounts differ between claims labelled as fraudulent and those not labelled as fraudulent?
5. Which patterns could help a claims review team prioritise cases for further investigation?

## Tools Used

**Python and Pandas**

Used for data inspection, cleaning, validation and exploratory data analysis.

**Power BI**

Used to build an interactive dashboard with KPI cards, charts, date filters and category slicers.

## Dataset Description

The dataset contains 10,000 claim records and 20 columns. It includes claim identifiers, patient information, diagnosis and procedure codes, requested and approved amounts, submission dates, provider information, claim status and a fraud indicator.

Important fields include Claim ID, Provider ID, Diagnosis Code, Procedure Code, Claim Amount, Approved Amount, Claim Submission Date, Days Between Service and Claim, Claim Status, Provider Specialty and Is Fraud.

The Is Fraud column provides the fraud label available in the dataset. The criteria used to assign these labels have not been independently verified. Therefore, the analysis identifies patterns associated with the supplied labels rather than confirming actual fraudulent activity.

The dataset source and licence should be documented using the original dataset page before the project is presented as a fully sourced portfolio case study.

## Python Analysis

### Data Inspection

I started by inspecting the dataset to understand its structure and the information available for analysis.

I reviewed the first few records, checked column data types and examined summary statistics. I also checked missing values, duplicate records and the distribution of important categorical and numerical fields.

This helped establish the quality of the data before drawing conclusions from it.

### Data Cleaning

The dataset contained missing values in Insurance Type, Provider Specialty and Prior Visits in the Previous 12 Months.

There were 350 missing values in Insurance Type and 350 missing values in Provider Specialty. These were replaced with Unknown so that the records could be retained without assigning unsupported category values.

The 350 missing values in Prior Visits in the Previous 12 Months were retained as missing. A missing value does not necessarily mean that a patient had zero prior visits so replacing these values with zero could have changed the meaning of the data.

I also checked for duplicate records and found no duplicate rows. Procedure Code was converted to a string data type because it represents a code rather than a numerical measurement.

I validated the relationship between Claim Amount and Approved Amount and found no records where the approved amount exceeded the requested claim amount.

### Exploratory Data Analysis

After cleaning the data, I examined the main variables to understand claim volumes, financial amounts, claim statuses and the distribution of the dataset-provided fraud labels.

I also compared claim patterns across diagnosis codes and providers. This helped identify areas where the observed rates differed from the overall portfolio.

The analysis was intended to identify patterns worth investigating rather than make definitive judgements about individual patients or providers.

## Power BI Dashboard

The Power BI report contains three pages. Each page addresses a different part of the business problem.

### Page One: Claims Overview

This page provides an overall view of claims performance and financial exposure.

It includes KPI cards for total claims, fraud-labelled rate, total claim amount, total approved amount and average claim amount.

A monthly claims trend chart helps explore changes in claim volumes over time. A claims status donut chart shows how claims are distributed across approved, rejected and pending categories.

Date, insurance type and claim status filters allow users to explore different parts of the portfolio.

### Page Two: Diagnosis and Provider Analysis

This page examines differences across diagnosis codes and healthcare providers.

A diagnosis-level chart compares fraud-labelled rates across diagnosis categories. Provider charts show the highest claim volumes and the highest fraud-labelled rates.

Provider specialty, patient gender and patient state filters allow users to explore the results by different categories.

Provider-level rates should always be considered alongside the number of claims behind each rate. A high rate based on a relatively small number of records may be less stable than a similar rate based on a larger sample.

### Page Three: Fraud Risk Analysis

This page compares the financial patterns of claims labelled as fraudulent and claims not labelled as fraudulent.

A clustered column chart compares average claim amounts with average approved amounts for both groups. A separate bar chart compares the average difference between the requested and approved amounts.

Claim submission delay and prior visit filters allow users to explore whether the results change across different groups of claims.

These comparisons help highlight financial patterns that may be useful when prioritising claims for further review. They do not establish that a claim is fraudulent.

## Key Findings

### Overall Claims Portfolio

The dataset contains 10,000 claims. The average requested claim amount was 572.80 and the average approved amount was 475.51.

These figures provide a baseline for understanding the overall financial profile of the claims in the dataset.

### Distribution of Fraud Labels

A total of 829 claims were labelled as fraudulent in the dataset, representing 8.29 percent of all claims. The remaining 9,171 claims were not labelled as fraudulent.

This percentage describes the supplied dataset labels. It should not be interpreted as a verified fraud rate for a real insurance company.

### Diagnosis-Level Patterns

Diagnosis code I25.10 had 1,025 claims and 102 fraud-labelled claims. Its fraud-labelled rate was approximately 9.95 percent.

Diagnosis code F41.9 had the lowest observed fraud-labelled rate at approximately 6.71 percent.

These differences suggest that diagnosis-level patterns can be useful for further investigation. They do not establish that any particular diagnosis is associated with confirmed fraud.

### Provider-Level Patterns

Provider P0086 had the highest observed fraud-labelled rate at approximately 42.11 percent across 38 claims. Other providers also showed elevated rates in the dataset.

These results are potential review indicators only. The number of claims, the underlying case details and the reliability of the supplied labels should be considered before drawing conclusions about a provider.

### Differences in Claim Amounts

The average claim amount for fraud-labelled claims was 990.93 compared with 535.01 for claims not labelled as fraudulent.

The average approved amount was 545.87 for fraud-labelled claims and 469.15 for claims not labelled as fraudulent.

The difference between the average requested and approved amounts was 445.06 for fraud-labelled claims compared with 65.85 for claims not labelled as fraudulent.

The results show a substantial difference in the average financial gap between the two groups. This makes the gap a useful measure to examine when identifying claims that may require additional review.

## Business Recommendations

### Prioritise Claims with Unusual Financial Differences

Claims with unusually large differences between requested and approved amounts could be prioritised for a closer review of supporting documentation, policy coverage and approval decisions.

A large difference alone should not be treated as evidence of fraud.

### Review High-Risk Patterns Alongside Claim Volumes

Diagnosis and provider-level patterns can help guide further investigation. However, review decisions should consider claim volumes and relevant case details rather than relying only on a percentage or ranking.

### Monitor Claim Amounts and Approval Patterns

Claims teams could monitor average claim amounts, approved amounts and the gap between them over time. This may help identify changes in financial patterns that deserve further investigation.

### Use Multiple Indicators Before Escalating a Claim

A review process should consider several indicators together, including claim amount, approval gap, submission delay, prior visits and relevant supporting documents.

No single indicator should be used as proof of fraudulent activity.

### Improve Data Quality and Label Transparency

Before using a model or dashboard for operational decisions, the organisation should understand how fraud labels were assigned, validate the accuracy of the labels and investigate missing data. This would help improve confidence in future analysis.

## Project Limitations

The analysis is based on the supplied dataset and does not represent verified claims data from a named insurance company.

The methodology used to assign the Is Fraud labels has not been independently verified. The findings therefore describe associations within the dataset and do not confirm actual fraud.

The analysis is exploratory. The results should be validated against supporting documentation and appropriate investigation procedures before being used to make operational decisions.

## Conclusion

This project demonstrates how Python and Power BI can be used together to explore healthcare insurance claims and present findings in a business-focused format.

Python was used to inspect, clean and analyse the dataset. Power BI was used to turn the analysis into an interactive dashboard covering claims performance, diagnosis and provider patterns and differences in financial amounts.

The key takeaway is that combining claim volumes, financial differences and multiple risk indicators can help prioritise cases for further review. The analysis also highlights the importance of data quality and careful interpretation when working with fraud labels.

## Skills Demonstrated

Python, Pandas, data cleaning, exploratory data analysis, data validation, Power BI, dashboard development, KPI reporting, data visualisation and business recommendations.

