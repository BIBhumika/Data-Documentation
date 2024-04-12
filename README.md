
# Claims Weekly Summary & Detail Report Project Data Documentation
Claims Weekly Summary & Detail report Analysis
## Table of Contents
- [Project Overview](#project-overview)

- [Data Sources](#data-sources)

- [Recommendations](#recommendations)


### Project Overview
This data analysis for Claims Weekly Summary & Detail report project aims to provide weekly insights into the claims volume over the any selected week. This is a new source for our ETL process. As a end result by SSRS report analyzing various aspects of the claims data, we seek to identify trends, make data-driven recommendations, and gain a deeper understanding of the claims.

- Claims Columns Data Mapping
![image](https://github.com/BIBhumika/Data-Documentation/assets/166867548/783812ba-f604-411f-ae02-5be720de989d)

- Claims Summary
![image](https://github.com/BIBhumika/Data-Documentation/assets/166867548/abcea32e-d871-4e2a-a6fa-bdce10825dd7)

- Claims Detail
![image](https://github.com/BIBhumika/Data-Documentation/assets/166867548/c8a0c50a-786c-4bf6-8e43-4c44d412ecd7)






### Data Sources
Claims Data: The primary dataset used for this analysis is the "Claims_DailyLoad.xlsx" file, containing detailed information about each claims made by the LoanID with TaxAgency info.

#### Tools

1. Excel - Data Source
2. SQL Table - Data Destination
3. Excel/SQL - Data Cleaning.
4. SQL Server/SSIS - Data Analysis & ETL.
5. Formatting - Follow company's standard formatting.
6. SSRS - Creating reports.

#### Data Cleaning/Preparation
In the initial data preparation phase, we performed the following tasks:

1. Data loading and inspection.
2. Handling missing values.
3. Data cleaning and formatting.

#### Exploratory Data Analysis
EDA involved exploring the sales data to answer key questions, such as:

1. What is the overall Claims trend?
2. Which Loan has top Claims?
3. What are the peak Claims periods?

#### Data Analysis
Included some interesting code/features worked with CUBE MDX query.

```sql

 SELECT FC.[Amount]
        DC.[Lender Name]
        DC.[Tax Agency ID]
        DC.[Tax Agency Nm]
        DC.[State]
        DC.[Loan ID]
        DC.[Check Number]
        FC.[Claims Payment Date]
   FROM [Edw Reporting].[Dim].[Claims] AS DC LEFT JOIN
        [Edw Reporting].[Fact].[Claims] AS FC on DC.LoanKey = FC.LoanKey
  WHERE CustomerLenderID in (@CustomerLenderID) AND
        ClaimsPayment Between @FromClaimsPaymentDateDateKey and @ToClaimsPaymentDateDateKey
```

#### Results/Findings
The analysis results are summarized as follows:

The company's Claim have been steadily increasing over the past year, with a noticeable peak during the hurrican season.
Claims Category A is the best-performing category in terms of Claims.
Claims segments with low lifetime value (LTV) should be targeted for marketing efforts.

### Recommendations
Based on the analysis, we recommend the following actions:

Invest in marketing and promotions during non-peak hurricane seasons to maximize revenue.
Focus on expanding and promoting products in Category A.
Implement a customer segmentation strategy to target low-LTV customers effectively.

#### Limitations
I had to remove all zero values from Checkamount column because they would have affected the accuracy of my conclusions from the analysis. 
There are still a few outliers even after the omissions but even then we can still see that there is a positive correlation to checkamount.

