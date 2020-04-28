# Exploration-of-Prosper-Loan-Data with R

# About

Prosper Loans is a private personal loan issuer. Univariate, bivariate, and multivariate graphs were made using R to explore loan data.  The overall data set has 82 fields, but here we will look at 18 of them.  They are:

| Field                       | Description                                                                     | Data Type    | 
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

## Univariate Analysis
  

There are 84 variables and 113,937 observations in the Prosper Loan data set. I created a new data frame called “loan” to only include 18 of those variables. Each one is explored in a plot above.

The non-categorical variables appear follow normal or Poisson distributions. Most findings seem resonable, such as most loans being current, more populous states having greater portion of loans, most recipients being employed, middle income ranges for most recipients, and credit scores that are fairly good around 700.


I think it would be interesting to further compare upper and lower credit scores. Side by side box plots can make the comparison more visible, while comparing the standard deviations of the 2 can provide more quantifiable comparison.

Listing category was originally had the awkward name “ProsperLoan$ListingCategory..numeric.” I reassigned that to the new variable ListingCategory. The IncomeRange variable was also re-ordered.

The listing category variable had a numeric key, so I used the description in the Variable Definitions document to create a descriptive factor varaible for this array. The x-axis variables did not appear in a very legible form, so for many plots I had to adjust the format using the ggplot theme layer.
By adjusting the binwidth the peaks observed in the credit score distributions become irrelevant. However, there is still an increase in number of loans for lower credit scores that drops off before increasing again.


# Bivariate Analysis

I was expecting to see a relationship between income and credit score, and credit score and borrower interest rates. I thought a relationship between credit score and DTI would stand out, but the results make sense in that regardless of how much debt one has some are better at making timely payments than others. It also made sense that those with lower incomes tended to take smaller loan amounts. I was expecting to see a noticable trend in income range vs. borrower rate, but people with lower incomes can still have good credit and vice versa so I shouldn’t be surprised.

The outliers in the credit score vs borrower rate plot threw me off. Some loan recipients have extremely low credit scores. There must be some other criteria that would explain the wide range in borrower rates. Perhaps the credit scores of co-signers are not included here, or maybe there are some other criteria in Prosper Score that determines these rates.

The strongest relationship is between Prosper Score and Borrower Rate, as the absolute value of r is the closest to 1. It would’ve been nice if incomes were continuous, since it looks like there may be some correlation in those plots.


# Multivariate Analysis

Prosper Score generally increased with income range, while borrorer rate seemed to decrease as income range rose. The IQR spreads of lower and upper credit scores were very similar.

Of the variables examined so far, there seems to be a more prevalent relationship between Prosper Score and Borrower Rate.

### Description One

Adjusting the binwidth on the histogram for Borrower Rate, we still see the increasing trend from 0.25 to 0.35. This suggests a bi-modal distribution. The range of rates is from 0 to 0.4975, with an IQR of 0.116. There are some outliers above rates of 0.4.

Pearson's Correlation Coefficient, r = -0.649


### Description Two

Here we have Borrorwe Rate vs. Prosper Score, overlayed with mean Borrower Rate, and a trendline. The absolute value of r is 0.65, which isn’t very strong, but stronger than other correlations found in the Bivariate Plots section. With the plots of mean Borrower Score and the trendline, it is easy to see the rates decreasing as Prosper Score increases. This makes sense if higher Prosper Scores reflect loan takers general credit worthiness.

|
