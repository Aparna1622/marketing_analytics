## Forecasting with Prophet, ARIMA, and Other Models Using StatsForecast:  

**what is Forecasting?**  
Forecasting is the process of making predictions about the future.  

**Why is forecasting important?**  
Forecasting is important because it allows you to make decisions based on the future. For example, if you are a marketing data analyst,
you can use forecasting to predict the number of sales you will have in the next quarter. This will allow you to make decisions about how
many products to order, how many people to hire, and how much money to spend on advertising.  

**Types of time series data:**  
Time series data exhibits a wide variety of patterns, frequencies, and complexities. Understanding the characteristics of different types of
time series data is crucial for selecting the appropriate forecasting model and accurately predicting future observations. These types are
follows:  
**Univariate time series:**  
A univariate time series consists of single observations recorded sequentially over time. For example, the monthly sales of a specific product
or the daily closing price of a company's stock can be represented as individual univariate time series. Univariate time series analysis focuses on
forecasting future values based solely on the past and present values of a single variable.  
**Panel data:**  
Panel data(also known as longitudinal or cross-sectional time series data) is a type of time series data where you have multiple time series
for the same entity. For example, we might have a time series for the number of sales for each month for each store in a chain of stores.
In this case, we have a time series for each store. Panel data analysis aims to understand and model the behavior of the variabls across
individual entities(such as different stores) and over time, allowing for the identification of both entity-specific and time-specific
effects on the forecasts.  
**Hierarchical time series:**  
Hierarachical time series data consist of time series arranged in a hierarchical structure, where each level of the hierarchy provides
additional aggregation or disaggregation of the data. For instance, a retail company might have sales data per product, per category, per 
store, and per region, creating a multilevel hierarchy. Forecasting hierarchical time series data involves reconciling forecasts at different
levels of the hierarchy, which helps to improve the accuracy of predictions and alignment with the overall business strategy.  
**Seasonal time series:**  
Seasonaly is a pattern that repeats at a fixed interval of time, such as daily, weekly, or annually. Seasonal time series data exhibits 
such reccurent patterns that can be leveraged to improve forecasting accuracy. Examples include monthly sales data influenced by holidays, seasons
or daily website traffic data affected by weekdays and weekends. Seasonal decompositions and seasonal models, such as SARIMA and Holt-Winters,
can be applied to better capture and forecast the underlying seasonal patterns.  
**Non-stationary time series:**  
Non-stationary time series data exhibits properties that change over time, such as mean, variance, or seasonality patterns. This data often
presents more challenges for forecasting, as its statistical properties cannot be assumed constant in the future. Examples include stock
prices, economic indicators, and population growth. To improve forecasting accuracy of the non-stationary time series, transformations or
different techniques may be applied to make the data stationary before employing traditional forecasting methods.  

## Exploratory Data Analysis:
Always do not confuse seasonality spike with outliers. Seasonality spikes are expected and should be taken into account when forecasting.
There are several ways to deal with outliers:  
**1. Winsorization:**  
This is the process of replacing outliers that exceed a specific percentile. This is useful when the outliers are due to measurement 
errors. We can do this by using the clip() function.  
**2.Dummy variables**  
This is the process of creating a dummy variable for each outlier. This is useful whent the outliers are due to a specific event so you 
can model them accordingly. We can do this by using the get_dummies() function.  
**3.Visualize trend, seasonality, and cyclic behavior:**  
If cyclic behavior is present, we need to decompose the time series. Be mindful of the distinction between seasonality and cyclic behaviours.
Seasonality is perodic behavior that repeats itself every year, month, week, day and so on. Cyclic behavior is non-periodic that repeats itself
every few years. We can do this by using the seasonal_decompose() function.  

# Seasonal Trend Decomposition using LOESS (STL)

**Definition**

Seasonal Trend Decomposition using LOESS (STL) is a time series decomposition method that separates a time series into **Trend**, **Seasonal**, and **Residual** components using **LOESS (Locally Estimated Scatterplot Smoothing)**.

### Formula

```
Y(t) = T(t) + S(t) + R(t)
```

**Where**

- Y(t) = Original time series
- T(t) = Trend component
- S(t) = Seasonal component
- R(t) = Residual (remainder) component

### Components

- **Trend** → Long-term movement in the data.
- **Seasonality** → Repeating patterns over fixed intervals.
- **Residual** → Random noise after removing trend and seasonality.

### Pros

- Handles complex seasonal patterns.
- Robust to outliers.
- Flexible and widely used for time series analysis.

### Cons

- Computationally slower than simple decomposition.
- Requires choosing an appropriate seasonal period.
- Primarily designed for additive decomposition.
 

