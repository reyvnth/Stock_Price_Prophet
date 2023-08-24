# Stock Price Prediction using Facebook Prophet

In this project, I explore the use of Facebook Prophet, a forecasting tool, to predict the stock price of Tesla (TSLA) over the next 300 business days. The goal is to showcase how to use this powerful tool for time series forecasting and how to compare the predictions with actual data using Google Spreadsheets and Google Finance.

## Table of Contents

- [Introduction](#introduction)
- [Data Collection](#data-collection)
- [Model Training](#model-training)
- [Comparison and Visualization](#comparison-and-visualization)
- [Conclusion](#conclusion)

## Introduction

Stock price prediction is a challenging task due to the complex and volatile nature of financial markets. Facebook Prophet is an open-source forecasting tool designed for time series data like stock prices. It handles various components of time series data, such as trends, seasonality, holidays, and outliers, making it an ideal choice for this project.

## Data Collection

To get started, I downloaded the historical stock price data of Tesla (TSLA) from Yahoo Finance. This data serves as the basis for training and evaluating the Prophet model. The data includes the date and closing price for each trading day over the past year (24th Aug 2022 to 24th Aug 2023).

## Model Training

Using the downloaded TSLA stock price data, I trained a Prophet model to predict the stock price over the next 300 business days. The Prophet model takes into account historical trends and seasonal patterns, enabling it to provide forecasts that capture both short-term fluctuations and long-term trends.

Here's a code snippet demonstrating how I trained the Prophet model:

```python
# Importing necessary libraries
from fbprophet import Prophet

# Loading the TSLA stock price data
data = ...  # Load your data here

# Preparing the data in the required format
data = data.rename(columns={'Date': 'ds', 'Close': 'y'})

# Initializing and fitting the Prophet model
model = Prophet()
model.fit(data)

# Creating a dataframe for future predictions
future = model.make_future_dataframe(periods=300, freq='B')

# Generating predictions
forecast = model.predict(future)
