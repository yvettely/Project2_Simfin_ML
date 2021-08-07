# Project 10K #
By: Thomas Mitrevski, Paul Gill, Yvette Ly and Racim Badsi

## Proposal ##
- Through sentiment analysis, investors can quickly understand if the tone of annual (10K) and quarterly (10Q) are positive, negative, or litigious etc. The overall sentiment expressed in these reports can then be used to help investors decide if they should invest in a company.
- On the other hand, many would argue that nothing beats the numbers, and many investors would prefer to look at a company’s financials before they invest.

## Story: ##
Our client wants to know if he should focus on the financials or the sentiment of the reports or both?

## Hypothesis ##
- Is it possible, using sentiment analysis, to predict revenue increases or decreases of certain stocks using a company’s financial reports from the last 10 years?
- OR is a Time Series Analysis of financial statements (balance sheets, income statements) a better predictor?



This particular repository presents the time series analysis part of the project.

We want to look at the contents of 10-K and 10-Q statements to determine if the contents of the Income Statement, Balance Sheet and Statement of Cash Flows will predict a shift in the prices on the dates the statements are published.

If we can show that the Key Performance Indicators (KPIs) contained in the Financial Statements affect the price in a fashion different from the normal price movement, we  may be able to take advantage of that in an algorithmic trading signal in the future.

### ROADBLOCK ###
Because raw data from the 10-K and 10-Q SEC filings is extremely robust, we chose to retrieve data from SimFin.

By using SimFin Python API, we were able to download and use not just the raw financial data but the KPIs of publicly traded companies as well.  For this particular machine learning model, we performed a time series analysis from the information derived from the Income Statement, Balance Sheet and Statement of Cash Flows.

### Time Series Analysis Model Summary ###
- We downloaded datasets to include the Income Statements, Balance Sheets, Cash-Flow Statements, and Share Prices of companies traded in the US.  Then used quarterly data for financial reports, and daily data for share-price.
- With a SimFin+ subscription, we were able to load the derived figures & ratios dataset. This dataset contains pre-calculated fundamental ratios which we then used as our signals.
- We used the SimFin tutorial presented by Hvass Laboratories as a guide for our models.
- Since some of the signals have a lot of missing data which causes problems in the statistical analysis, we removed all signals that have more than 25% missing data. Examples include, R&D/Revenue, Inventory Turnover, etc.
- From the remaining data, we used the mean-log returns of 1-3 year periods in the dataset.  This is because data from the financial statements will be exactly the same for 3 months at a time, it cannot be used to predict short-term stock-returns.
- We removed outliers by “Winsorization” of the data.
- We looked at the linear correlation between the signals and stock-returns, to roughly assess which signals might be the best predictors for stock-returns. 
- We split the dataset according to stock-tickers, so a ticker belongs to either the training- or test-set, but not both. We used 80% of all the tickers in the training-set, and 20% in the test-set.

