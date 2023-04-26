# Volatility-modelling

This code is an implementation of a financial forecasting model that uses the EGARCH(1,1) model to estimate the volatility of the S&P 500 index returns. The realized variance of the S&P 500 index returns is calculated and used as the dependent variable, while the EGARCH variance estimate and the VIX (a measure of implied volatility of the S&P 500 index) are used as independent variables in two separate linear regression models. The models are trained on data from January 1, 2000, to September 1, 2021, and then tested on the last 150 days of data. The out-of-sample forecasts of the two models are plotted against the actual realized variance to evaluate their performance.

The code begins by importing the necessary libraries, including pandas, numpy, yfinance, arch, statsmodels, and matplotlib.pyplot. The S&P 500 index and VIX data are downloaded from Yahoo Finance using the yfinance library, and the daily returns for the S&P 500 index are calculated using the pct_change() function. The realized variance is then calculated by squaring the daily returns. The two datasets are merged into one dataframe, and the VIX is squared to obtain a measure of the implied volatility.

The EGARCH(1,1) model is then fit to the S&P 500 index returns using the arch_model() function from the arch library. The conditional variance estimates from the EGARCH model are used to calculate the EGARCH variance estimates, which are added to the dataset as a new column. The data are then split into training and testing sets, with the last 150 days of data used for testing.

Two linear regression models are then trained on the training data, with the realized variance as the dependent variable and the EGARCH variance estimate and VIX as the independent variables. The first model includes only the EGARCH variance estimate, while the second model includes both the EGARCH variance estimate and the VIX. The models are trained using the OLS (ordinary least squares) function from the statsmodels library, and the results are stored in results1 and results2, respectively.

The out-of-sample forecasts are then made using the test data, and the predicted values are stored in y_pred_model1 and y_pred_model2. These values are then plotted against the actual realized variance using the plot() function from the matplotlib.pyplot library.

Finally, the plot is customized with a title, axis labels, and a legend, and the plot is displayed using the show() function from the same library.
