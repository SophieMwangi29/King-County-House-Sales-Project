# King-County-House-Sales-Project
This project is aimed at helping advice home owners by finding out how home renovations might increase estimated value of their homes and by what amount
Below is a screenshot that explains what all the columns mean
![image](https://user-images.githubusercontent.com/104424533/176946181-2be67243-0f73-45d6-8c43-b3bff8aab366.png)

# Introduction
This project analyses the King County House Sales data 

## Packages
This analysis requires these R packages:
** pandas
** numpy
** matplotlib
** scipy stats

## Cleaning the data
The first step was to look at the data structure and find out if there are missing values. We then replace the missing values with zero.The variables with missing values include; yr_renovated, view and waterfront.
we also deleted the ID column as it was not needed. 

We analyse the effect of the variables with the missing data on price. We do this in order to view if lacking a particular feature will change the value of the house. 
We can conclude that indeed that the lack of a waterfront wiew were more expensive compared to those without.

The houses that have been viewed more times also have more value compared to those not viewed at all.
More houses have been renovated in the recent years (the year 2000s), there is no clear linear relationship between price and year of renovation. 


The next step is to the correlation matrix to understand which variables are most correlated with our target (price). Below is the correlation table compared to price
![image](https://user-images.githubusercontent.com/104424533/177147955-cd08cff4-4dd6-4fd5-b8f8-3dbe7b5813d0.png)

We then plot the price variable and the variable most correlated to it (sqft_living). Below is the plot;
![image](https://user-images.githubusercontent.com/104424533/177148679-19f4d548-bc29-4e49-b00f-5d96679b7d01.png)


There is presence of heteroskedasticity which we fix in later stages.
 

### Getting the summary statistics
Below is a table showing the general statistical measures of all columns





## Modeling

We use the linear regression model; OLS (ordinary linear squares method)
### Checking for variable distribution
For the variable price, the values were skewed to the left as seen in the image below;

![image](https://user-images.githubusercontent.com/104424533/177150396-22deef27-8e8f-4a76-95f1-7ab005d516fe.png)

To fix this, by performing log transformation on the data to make it normal.

We then check for distribution of other variables and perform log transformation on them as well. We transform those variables most correlated with the price variable.
After doing this, we established homoskedasticity which is needed before performing linear regression as we can see below;
![image](https://user-images.githubusercontent.com/104424533/177151693-95df2ee7-872e-41e3-89b5-fd59e78809ae.png)

We also performed a Jarque-Bera test to test for nomarlity. This test yielded odd results. We have a JB value = 18735.09910753447, which is extemely high, and the p-value of 0.1685 is low so we reject the null hypothesis for normality. Additionally, the kurtosis is below 3, where a kurtosis higher than 3 indicates heavier tails than a normal distribution. The skewness values however show that underlying data is not very skewed.

We pick the variables with a correlation of 0.75 and above to perform the regression. These are the variable we use; sqft_above, sqft_living+grade, sqft_living15, bathrooms. 
We perform multiple linear regression on this vs log_price (price transformed).
Below are the the results
![image](https://user-images.githubusercontent.com/104424533/177153871-77beffe3-3f7a-4579-a4e1-491a48c32c91.png)




