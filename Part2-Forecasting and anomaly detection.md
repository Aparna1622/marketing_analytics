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
 
# Simulation

**Definition**

Simulation is the process of creating a model of a real-world system and running experiments on it to study its behavior under different conditions.

### Steps

1. Build a model.
2. Generate input values.
3. Run the simulation.
4. Analyze the results.

### Example

Simulating the roll of a dice **10,000 times** to estimate the probability of getting a **6**.

### Applications

- Risk analysis
- Forecasting
- Machine learning
- Finance
- Healthcare
- Supply chain optimization

### Pros

- Helps analyze complex systems.
- Reduces the cost of real-world experiments.
- Supports decision-making under uncertainty.

### Cons

- Results depend on model assumptions.
- Can be computationally expensive.
- May not perfectly represent real-world behavior.

# ETS Model (Error, Trend, Seasonal)

**Definition**

ETS (Error, Trend, Seasonal) is a time series forecasting model that decomposes a time series into **Error**, **Trend**, and **Seasonal** components using exponential smoothing.

### Formula

```
Observed Value = Error + Trend + Seasonal
```

or

```
Y(t) = E(t) + T(t) + S(t)
```

**Where**

- Y(t) = Observed time series
- E(t) = Error component
- T(t) = Trend component
- S(t) = Seasonal component

### Components

- **Error (E)** → Random variation or noise.
- **Trend (T)** → Long-term increase or decrease.
- **Seasonal (S)** → Repeating pattern over time.

### Common ETS Models

- ETS(A, N, N) → Additive Error, No Trend, No Seasonality
- ETS(A, A, N) → Additive Error, Additive Trend
- ETS(A, A, A) → Additive Error, Additive Trend, Additive Seasonality
- ETS(M, A, M) → Multiplicative Error, Additive Trend, Multiplicative Seasonality

### Pros

- Handles trend and seasonality effectively.
- Simple and interpretable.
- Works well for many forecasting problems.

### Cons

- Assumes historical patterns continue.
- Less effective for highly irregular data.
- Not suitable for data with sudden structural changes.

## What type of patterns are present?  
When forecasting, we need to be aware of the type of patterns present in the time series data. This will determine the type of model we will use. Commonly, time series data is described as having trends and seasonality.  

**Trend:**  
A trend is the general direction of the time series. It can be either positive or negative. It can also be constant or it can change over time, for example, a positive trend might change to a negative trend. The trend can be linear, non-linear, multiplicative or additive.  

**Seasonality:**  
Seasonality is a behavior or pattern that is caused or repeated given some seasonal factor, such as the time of the year or the day of the week. One thing to note is that seasonality is always fixed and of a known period. For example, the period of a year is 12 months, and the period of a week is 7 days, which will correspond to the monthly and weekly seasonality periods respectively. A major source of confusion is when people use seasonality to describe cyclic behavior.  

**Cyclic behavior:**  
A cycle is a behavior or pattern that repeats itself, but the period is not fixed. The reason the period is not fixed is usually due to the influence of an external factor. The most known cycle is the business cycle, caused by economic factors. Another example is cycles induced by competitor activities. In general, cycles are longer than seasonal effects, taking years to complete instead of months or weeks. It is possible to break time series into these patterns, known as time series decomposition.  

**Time series decomposition:**  
This is a method of breaking a time series dataset into components. Usually, the trend and cyclic components are grouped together, and most statitiscal packages will ouutput this as a single component called a trend. We will also have seasonal component. What remains is the residual, which is the noise of the time series. It is essentially the movement from the time series data, we are not limited to just one seasonal component. A time series can have multiple seasonal components, for example, a time series can have a weekly and a monthly seasonal component.  
When breaking down a time series into its basic elements, we can use two appoaches: additive or multiplicative decomposition. With an additive model, we simply add the trend, seasonal and residual components to reconstruct the time series. This implies that the impact of trend and seasonality does not change over time.  
On the other hand, a multiplication model assumes that the time series is a result of multiplying the trend, seasonal, and residual components. Here, the effect of the trend and the seasonaliy increases or decreases in direct proportion of the data. So, as the data grows,the influence similarly reduces. This approach is often more appropriate when the seasonal pattern intensify as the time series value rises.  
If we are taking an additive decomposition, the time series can be written as:  

# ETS Model Formulas

## Additive Model

```
Y(t) = T(t) + S(t) + E(t)
```

**Where**

- Y(t) = Observed value at time t
- T(t) = Trend component
- S(t) = Seasonal component
- E(t) = Error (random noise)

---

## Multiplicative Model

```
Y(t) = T(t) × S(t) × E(t)
```

**Where**

- Y(t) = Observed value at time t
- T(t) = Trend component
- S(t) = Seasonal component
- E(t) = Error (random noise)
