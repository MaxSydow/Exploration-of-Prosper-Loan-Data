# Exploration-of-Prosper-Loan-Data with R

# About

Prosper Loans is a private personal loan issuer. Univariate, bivariate, and multivariate graphs were made using R to explore loan data.  The overall data set has 82 fields, but here we will look at 18 of them.  They are:

| Field                       |
|:---------------------------:|:-------------------------------------------------------------------------------:|:-----------:|
| Term                        | Length of loan in months                                                        | integer     |
| LoanStatus                  | Current status of loan; Current, Defaulted, Completed, etc.                     | categorical |
| BorrowerRate                | Interest rate                                                                   | number      |
| BorrowerAPR                 | Annual percentage rate                                                          | number      |
| ProsperScore                | Custom risk score based on Prosper data; ranging 1-10; 10 being lowst risk      | integer     |
| BorrowerState               | US state of residence for borrower                                              | categorical |
| EmploymentStatus            | Borrower's employment status                                                    | categorical |
| EmploymentStatusDuration    | Length of borrower's employment in months                                       | integer     |
| IncomeRange                 | Borrower's income range                                                         | categorical |
| LoanOriginalAmount          | Original amount of loan                                                         | integer     |
| DebtToIncomeRatio           | Ratio of debt to income                                                         | number      |
| IncomeVerifiable            | Borrower has verifiable income or not                                           | binary      |
| TotalProsperLoans           | Number of existing Prosper loans at time of current loan application            | integer     |
| Investors                   | Number of investors funding the loan                                            | integer     |
| Occupation                  | Borrower's occupation, selected from pre-defined categories                     | categorical |
| CreditScoreRangeLower       | Lower value of borrower's credit score                                          | integer     |
| CreditScoreRangeUpper       | Upper value of borrower's credit score                                          | integer     |
| ListingCategory             | Reason for loan; e.g. Auto, Home Improvement, etc. categories assigned number   | integer     |

* R uses 'Factor' to describe categorical variables, and 'logi' to describe binary variables


The data can be found at 

https://s3.amazonaws.com/udacity-hosted-downloads/ud651/prosperLoanData.csv.

A description of each variable is included in this link: 

https://docs.google.com/spreadsheets/d/1gDyi_L4UvIrLTEC6Wri5nbaMmkGmLQBk-Yx3z0XDEtI/edit#gid=0.

## Findings from univariate plots



There are only 3 lengths of loan terms. Most are for 36 months, fewer have a duration of 60, and a small number were payed off in 12 months.

The majority of loans are current or completed. More loans were cancelled than defaulted, and there’s a slight decrease in past due loans as time goes on.
