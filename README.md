# Stock Price Prediction using Facebook Prophet

In this project, I explore the use of Facebook Prophet, a forecasting tool, to predict the stock price of Tesla (TSLA) over the next 300 business days. The goal is to showcase how to use this powerful tool for time series forecasting and how to compare the predictions with actual data using Google Spreadsheets and Google Finance.

## Table of Contents

- [Introduction](#introduction)
- [Data Collection](#data-gathering)
- [Data Visualization using Plotly](#data-visualization-using-plotly)
- [Model Training](#model-training)
- [Stock Analysis and Forecasting](#stock-analysis-and-forecast)
- [Conclusion](#conclusion)

## Introduction

Stock price prediction is a challenging task due to the complex and volatile nature of financial markets. Facebook Prophet is an open-source forecasting tool designed for time series data like stock prices. It handles various components of time series data, such as trends, seasonality, holidays, and outliers, making it an ideal choice for this project.

## Data Gathering

To get started, I downloaded the historical stock price data of Tesla (TSLA) from [Yahoo Finance](https://finance.yahoo.com/quote/TSLA/history?p=TSLA). This data serves as the basis for training and evaluating the Prophet model. The data includes the date and closing price for each trading day over the past year (24th Aug 2022 to 24th Aug 2023).

## Data Visualization using Plotly

A few visualizations studied are as below:

#### The Close Price for the Stock over the past year
<img align = "center" width = "100%" src="https://github.com/reyvnth/Stock_Price_Prophet/blob/main/Figures/p1.jpg" alt="Image">

</br>

#### The Volume of the Stock over the past year
<img align = "center" width = "100%" src="https://github.com/reyvnth/Stock_Price_Prophet/blob/main/Figures/p2.jpg" alt="Image">

</br>

#### The box plot representing the Closing price of the stock over the last year
<img align = "center" width = "100%" src="https://github.com/reyvnth/Stock_Price_Prophet/blob/main/Figures/p3.jpg" alt="Image">

</br>
</br>

#### The difference between Closing Price and Opening Price of the Stock over the past year
<img align = "center" width = "100%" src="https://github.com/reyvnth/Stock_Price_Prophet/blob/main/Figures/p4.jpg" alt="Image">

</br>
</br>

## Model Training

Using the downloaded TSLA stock price data, I trained a Prophet model to predict the stock price over the next 300 business days. The Prophet model takes into account historical trends and seasonal patterns, enabling it to provide forecasts that capture both short-term fluctuations and long-term trends.

Here's a sample code snippet demonstrating how I trained the Prophet model:

```python
# Importing necessary libraries
from prophet import Prophet

# Loading the TSLA stock price data
data = ...  # Load your data here

# Preparing the data in the required format
data = data.rename(columns={'Date': 'ds', 'Close': 'y'})

# Initializing and fitting the Prophet model
model = Prophet()
model.fit(data)

```

</br>

## Stock Analysis and Forecast

```python
# Creating a dataframe for future predictions
future = model.make_future_dataframe(periods=300, freq='B')

# Generating predictions
forecast = model.predict(future)
```

To assess the accuracy of the model's predictions, I used Google Spreadsheets and Google Finance to compare the predicted values against the actual stock prices for the last one year. This allowed me to visualize the model's performance and identify any discrepancies.

##### Actual Observed Stock price over the predicted trend using Prophet Model
<img align = "center" width = "70%" src="https://github.com/reyvnth/Stock_Price_Prophet/blob/main/Figures/p5.png" alt="Image">

Additionally, I plotted a trend line for the next 300 trading days using the forecast generated by the Prophet model. This visualization provides insights into the expected trajectory of the stock price based on the model's predictions.

#### Trendline depicting the Price of the TSLA :NASDAQ Stock over the next 300 trading days
<img align = "center" width = "70%" src="https://github.com/reyvnth/Stock_Price_Prophet/blob/main/Figures/p6.png" alt="Image">




## Conclusion

In this project, I demonstrated how to use Facebook Prophet for stock price prediction. By training the Prophet model on historical stock price data and comparing its predictions with actual data, I gained insights into its performance. The combination of Prophet's forecasting capabilities and external tools like Google Spreadsheets and Google Finance enables a comprehensive analysis of stock price trends.

Feel free to explore the code and adapt it for your own stock price prediction tasks. _**This is model or code used in predicting stock does not guarantee financial returns when used as the Stock markets are highly volatile and Please do not consider the outputs as a Financial Advice.**_ The world of finance offers a wide range of opportunities for time series forecasting, and Facebook Prophet can be a valuable tool in your data science arsenal.
