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

# STL Decomposition (Seasonal and Trend decomposition using Loess)

**STL** is a robust, versatile statistical method used to decompose a time series dataset into three underlying components:

$$Y_t = T_t + S_t + R_t$$

* **$Y_t$ (Observed Data):** The raw time series value at time $t$.
* **$T_t$ (Trend-Cycle Component):** Long-term directional changes or structural shifts in the data.
* **$S_t$ (Seasonal Component):** Patterns that repeat over a fixed interval (e.g., daily, monthly, annually).
* **$R_t$ (Remainder/Residual):** Random noise or unexpected fluctuations left over after removing trend and seasonality.

---

## Key Characteristics

Unlike classical decomposition methods, STL relies on **LOESS** (Locally Estimated Scatterplot Smoothing), a non-parametric regression technique that fits local polynomials to localized subsets of data.

* **Flexible Seasonality:** Allows seasonal patterns to change over time (e.g., peak demand shifting slightly every year) rather than assuming a strictly fixed shape.
* **Robustness to Outliers:** Employs an outer-loop mechanism using robust weights, preventing anomalous spikes or drops from warping the estimated trend and seasonal components.
* **Controllable Smoothness:** Parameters like the seasonal window size (`s.window`) and trend window size (`t.window`) give precise control over how rapidly components adapt.

---

## How the STL Algorithm Works

STL operates via two main recursive loops: an **Inner Loop** and an **Outer Loop**.  

## Time series Features:  
These are essential characteristics extracted from time series data that capture underlying patterns, trends, and relationships within the data. These features provide valuable insights and diagnostics, improve forecasting accuracy, and help identify anomalies and events in the time series. we can think of these features as a form of exploratory data analysis on time series.  

**ACF Features:**  
The first group of features are autocorrelation features. In the same way as correlation will measure how two variables move together in a linear fashion, autocorrelation will measure how observations move together given lagged values of the time series. For example, if we have a time series of daily sales and we want to know how the sales today are correlated with the sales yesterday, we can calculate the autocorrelation at lag 1. If we want to know how the sales today are correlated with the sales two days ago, we can calculate the autocorrelation at lag2, and so on.  

# Autocorrelation Coefficient Formula

The **autocorrelation coefficient** measures the linear relationship between a time series variable and a lagged version of itself at lag $k$.

---

## Population Autocorrelation Formula

For a stationary time series $Y$, the theoretical autocorrelation coefficient at lag $k$ (denoted as $\rho_k$) is defined as:

$$\rho_k = \frac{\gamma_k}{\gamma_0} = \frac{\operatorname{Cov}(Y_t, Y_{t-k})}{\operatorname{Var}(Y_t)}$$

Expanding the covariance and variance terms:

$$\rho_k = \frac{\mathbb{E}[(Y_t - \mu)(Y_{t-k} - \mu)]}{\mathbb{E}[(Y_t - \mu)^2]}$$

Where:
* **$k$** is the time lag ($k = 0, 1, 2, \dots$).
* **$\mu$** is the mean of the time series ($\mathbb{E}[Y_t]$).
* **$\gamma_k$** is the autocovariance at lag $k$.
* **$\gamma_0$** is the variance of the time series (the autocovariance at lag $0$).

---

## Sample Autocorrelation Formula

In practice, given an observed sample time series $y_1, y_2, \dots, y_n$ with sample mean $\bar{y}$, the sample autocorrelation coefficient $r_k$ (or $\hat{\rho}_k$) is calculated as:

$$r_k = \frac{\sum_{t=k+1}^{n} (y_t - \bar{y})(y_{t-k} - \bar{y})}{\sum_{t=1}^{n} (y_t - \bar{y})^2}$$

Where:
* **$n$** is the total number of observations.
* **$\bar{y}$** is the sample mean: $\bar{y} = \frac{1}{n} \sum_{t=1}^{n} y_t$.
* **$r_k$** ranges from **$-1$** (perfect negative correlation) to **$+1$** (perfect positive correlation).
* At **$k = 0$**, $r_0 = 1$ because a series is perfectly correlated with itself.

---

## Python Implementation Example

```python
import numpy as np


def autocorr(y, k):
    """Calculates the sample autocorrelation coefficient for a given lag k."""
    y = np.asarray(y)
    n = len(y)
    y_bar = np.mean(y)

    # Denominator: sample variance sum
    denom = np.sum((y - y_bar) ** 2)

    # Numerator: covariance sum at lag k
    num = np.sum((y[k:] - y_bar) * (y[:-k] - y_bar)) if k > 0 else denom

    return num / denom
```

In the context of marketing analytics, understanding the dynamics of time series data is pivotal for accurate forecasting and strategic decision-making. A core concept in this arena is the analysis of autocorrelation features, which serve as a compass for navigating the temporal relationships within marketing datasets.
Autocorrelation coefficients, denoted as $r_k$, measure the linear relationship between time-lagged observations within a dataset. These coefficients range from -1 to +1, where:  
- A value of +1 signifies a perfect positive correlation, indicating that an increase in one observation directly correlates with an increase in another, separated by a specific lag.
- A value of -1 denotes a perfect negative correlation, suggesting that an increase in one observation corresponds to a decrease in another across the given lag.
- A coefficient near 0 implies a lack of a linear relationship between the observations at the specified lag.

**Important autocorrelation features:**  
1. Initial observation correlation(x_acf1): This represents the immediate linear relationship between successive observations.
2. Collective influence(x_acf10): This aggregates the squared autocorrelation coefficients for the first ten lags, offering insight into the overall temporal dependency. Elevated values suggest pronounced autocorrealation, implying the historical data significantly influences future outcomes.
3. Trend identification through differencing(diff1_acf1): This applies to once-differentiated data, highlighting trends or non-stationarities. Negative values suggest inverse relationships between consecutive changes, indicative of possible market corrections or overreactions.
4. Pattern strenghth in changes(diff1_acf10): This summarizes the squared autocorrelation of the first difference. Higher totals reveal stronger autocorrelated structures post-differencing, suggesting underlying trends or cycles.
5. Complex dynamic detection(diff2_acf1): This focuses on twice-differentiated data uncovering more intricate patterns that may include seasonal trends or deeper cyclical behaviors.
6. Underlying structure in second difference(diff2_acf10): This is similar to diff1_acf10 but for the second differences, indicating even more complex temporal relationships that may necessitate advanced modeling techniques.
7. Seasonal influence(Seasonal ACF): This examines the autocorrelation at specific seasonal lags, with values close to the extemities indicating significant seasonal effects.

## Basics of time series forecasting:  
**1. Data cleaning and preparation**  
**2. Plotting the time series and some Exploratory data analysis**  
**3. Defining the model**  
**4. Fitting the model**  
**5. Evaluating the model**  
**6. Forecasting**  

# Multicollinearity

**Definition**

Multicollinearity occurs when two or more independent variables in a regression model are highly correlated with each other.

### Example

```
X₁ = Years of Experience
X₂ = Age
```

If experience and age are highly correlated, the model may have multicollinearity.

### Formula

Variance Inflation Factor (VIF):

```text
VIF = 1 / (1 - R²)
```

**Where**

- R² = R-squared obtained by regressing one independent variable against the other independent variables.

### Effects

- Makes coefficient estimates unstable.
- Increases standard errors.
- Makes it difficult to determine the individual effect of each predictor.

### Detection

- Correlation Matrix
- VIF (Variance Inflation Factor)

### Common Rule of Thumb

```text
VIF > 5  → Possible multicollinearity
VIF > 10 → High multicollinearity
```

# Holdout Method in Time Series

**Definition**

The Holdout Method is a time series validation technique where the data is divided **chronologically** into a training set and a test set.

### Example

```text
Training Data → Jan 2020 to Dec 2023
Test Data     → Jan 2024 to Dec 2024
```

The model is trained on the **training data** and evaluated on the **test data**.

### Key Point

```text
Past Data → Training Set → Model
Future Data → Test Set → Evaluation
```

The data should **not be randomly shuffled**, because time series data depends on the order of time.  

 ## Variable selection in time series regression models:  
 Variable selection in time series models is a crucial step in refining your predictions. The essence of this task lies in identifying which predictors(or features) provide valuable information for forecasting the target variable. The overall goal is to include features that improve the model's performance while excluding those that may make it overly complex without providing additional forecasting value.  
 There are several strategies for the variable selection, two of which will be discussed here: Cross validation and the use of information criteria metrics.  

 **Cross validation**
 The simplest way to select variables is to use cross-validation. This is a method that is commonly used in machine learning to select the best model. In essence, it is a more developed version of the holdout method. In the holdout method, we split the data into two sets: a training set and a test set. You fit the model on the training set and evaluate it on the test set. The problem with this method is that we are only using a fraction of the data to fit the model. This means that you are not using all the information in the data to fit the model. This is why cross-validation is a better method. In cross-validation, we split the data into k folds. We fit the model on k-1 folds and evaluate it on the remaining folds. We repeat this process k times, using a different fold as the test set every time. The final score is the average of k scores. This method is more robust because you are using all the data to fit the model and we are not overfitting the model to a specific fold. Now, the splits in time series cannot be random. We need to make sure that the folds are contiguous(next to each other) in time. This is because the data is not independent. The data is dependent on the previous observations. If we split the data randomly, we will be introducing a bias in the model. Most commonly, we will split the model between a test set of one observation and a training set of all the previous observations. For each k fold, we move it one observation forward. This is called a rolling window. We repeat this process until we reach the end of the time series. The result is a set of predictions for each observation. We then average all the test set predictions to get the final score. This method is also known as "evaluating on a rolling  forecasting origin" because the origin of the test set is rolling forward one point at a time.  

<img width="696" height="184" alt="image" src="https://github.com/user-attachments/assets/d8ba0dec-3ab8-41cf-9f75-1ea4c35e7013" />


# Variable Selection in Time Series Regression

Variable selection is the process of choosing the most useful predictors for a time series regression model. Two common approaches are **Cross-Validation** and **Information Criteria**.

## 1. Cross-Validation

In time series, we cannot randomly split the data because the order of observations matters. Instead, we use **time-based cross-validation**.

### Rolling / Expanding Window Cross-Validation

```text
Train: 1 2 3 4 5       → Test: 6
Train: 1 2 3 4 5 6     → Test: 7
Train: 1 2 3 4 5 6 7   → Test: 8
```

The model is repeatedly trained on past observations and tested on future observations.

### Common Evaluation Metrics

**MAE (Mean Absolute Error)**

```text
MAE = (1/n) × Σ|yᵢ - ŷᵢ|
```

**RMSE (Root Mean Squared Error)**

```text
RMSE = √[(1/n) × Σ(yᵢ - ŷᵢ)²]
```

**MAPE (Mean Absolute Percentage Error)**

```text
MAPE = (100/n) × Σ|(yᵢ - ŷᵢ) / yᵢ|
```

### Selection Rule

```text
Lower MAE  → Better model
Lower RMSE → Better model
Lower MAPE → Better model
```

The model with the lowest validation error is generally preferred.

---

## 2. Information Criteria

Information criteria evaluate a model based on its **goodness of fit** while applying a penalty for the **number of parameters**.

They help prevent overfitting.

### AIC (Akaike Information Criterion)

```text
AIC = 2k - 2ln(L)
```

### BIC (Bayesian Information Criterion)

```text
BIC = k ln(n) - 2ln(L)
```

### AICc (Corrected AIC)

```text
AICc = AIC + [2k(k + 1)] / (n - k - 1)
```

**Where**

- `n` = Number of observations
- `k` = Number of estimated parameters
- `L` = Maximum likelihood of the model
- `ln(L)` = Log-likelihood

### Selection Rule

```text
Lower AIC  → Better model
Lower AICc → Better model
Lower BIC  → Better model
```

### AIC vs BIC

```text
AIC → Smaller penalty for additional parameters
BIC → Larger penalty for additional parameters
```

Therefore, **BIC generally favors simpler models more strongly than AIC**.

---

## Cross-Validation vs Information Criteria

| Method | Main Purpose | Selection Rule |
|---|---|---|
| Cross-Validation | Evaluate out-of-sample forecasting performance | Lower validation error |
| AIC | Balance fit and complexity | Lower AIC |
| AICc | AIC adjusted for small samples | Lower AICc |
| BIC | Stronger penalty for complexity | Lower BIC |

### Key Difference

```text
Cross-Validation → "Which model forecasts future data better?"

Information Criteria → "Which model balances fit and complexity better?"
```

For **time series forecasting**, time-based cross-validation is particularly useful because it directly evaluates how well the model performs on unseen future observations.  

# Predictor Variable Selection Using Cross-Validation

Cross-validation can be used to select the best set of predictor variables by comparing the forecasting performance of different models.

### Example

Suppose we have:

Target → Sales

Predictors → Price, Advertising, Temperature, Holiday


We create different models:  

Model 1 → Sales ~ Price

Model 2 → Sales ~ Price + Advertising

Model 3 → Sales ~ Price + Advertising + Temperature

Model 4 → Sales ~ Price + Advertising + Temperature + Holiday

For each model, perform time-series cross-validation and calculate the validation error.

Model 1 → RMSE = 15.2
Model 2 → RMSE = 10.5
Model 3 → RMSE = 9.1
Model 4 → RMSE = 9.8

Selection
Lowest Validation RMSE → Model 3

Therefore, the selected predictors are:

Price + Advertising + Temperature

Holiday is excluded because adding it increased the validation error.

General Process
1. Start with a set of candidate predictors.
2. Create different combinations of predictors.
3. Train each model using the training period.
4. Predict the validation/future period.
5. Calculate the validation error.
6. Repeat across multiple time-based folds.
7. Average the validation errors.
8. Select the predictor set with the lowest average validation error.
Important Point
Variable Selection ≠ Selecting variables based only on p-values

Variable Selection using Cross-Validation
→ Select variables that improve out-of-sample prediction.

For time series:

Past Data → Training
Future Data → Validation

So, we select predictors based on how well they help predict unseen future observations, not simply because they are statistically significant.  

## Information criteria metrics:
Another way to select predictor variables for our model is to use an information criteria metric. This is a metric that is used to compare models. The most common metrics are the Akaike information criterion(AIC), the corrected Akaike's information criteria(AICc), and the Bayesian information criterion (BIC). Essentially, they will compare different models for the information they provide and penalize them for the number of parameters they have. The model with the lowest metric is the best model.  

### Akaike Information Criterion (AIC)

AIC = T × log(SSE / T) + 2(k + 2)

Where:

- T = Number of observations
- SSE = Sum of Squared Errors
- k = Number of predictors
- log = Natural logarithm
- k + 2 = Number of estimated parameters, including the intercept and error variance

Lower AIC → Better model  

An interesting characteristic of the AIC is that it is asymptotically equivalent at large Ts to minimize the cross-validation error. This means that the AIC will select the model that will perform the best on the test set.  

## Corrected Akaike information criterion(AICc):  
When we have a short time series, where T is small, the AIC will still tend to select models with too many variables. In this case the AICc is a better metric. It is defined as follows:  

## Corrected Akaike Information Criterion (AICc)

AICc = AIC + [2(k + 2)(k + 3)] / (T - k - 3)

Where:

- AIC = Akaike Information Criterion
- k = Number of predictors
- T = Number of observations

Lower AICc → Better model. Essentially this metric attempts to correct for bias.  

## Schwarz's Bayesian Information Criterion (BIC)

BIC = T × log(SSE / T) + (k + 2) × log(T)

Where:

- T = Number of observations
- SSE = Sum of Squared Errors
- k = Number of predictors
- log = Natural logarithm
- k + 2 = Number of estimated parameters, including the intercept and error variance

Lower BIC → Better model.  
The main difference between BOC and AIC is that BIC will either select the same model as AIC or a model with fewer variables. This is because the penalty term is larger, and the criterion will penalize models with more variables more heavily. In the case of the BIC, it is the equivalent of minimizing the leave-one-out-cross-validation error for large values of T.  

## Advanced Forecasting methods:  
# 1. ETS model:  
## ETS Model

ETS stands for **Error, Trend, and Seasonal** components. It is a time series forecasting model based on exponential smoothing.

### General Form

Y(t) = Error + Trend + Seasonal

### Components

- **E = Error** → Random variation in the data
- **T = Trend** → Long-term upward or downward movement
- **S = Seasonal** → Repeating pattern over time

### Types

- **A** = Additive
- **M** = Multiplicative
- **N** = None

Examples:

```text
ETS(A,N,N) → Additive Error, No Trend, No Seasonality

ETS(A,A,N) → Additive Error, Additive Trend, No Seasonality

ETS(A,A,A) → Additive Error, Additive Trend, Additive Seasonality

ETS(M,A,M) → Multiplicative Error, Additive Trend, Multiplicative Seasonality
```

**Additive Model**  
Y(t) = T(t) + S(t) + E(t)  
**Multiplicative Model**  
Y(t) = T(t) × S(t) × E(t)   
**Key Point:**  
ETS = Error + Trend + Seasonality  
The model can use A (Additive), M (Multiplicative), or N (None) for each component.  


## 2.ARIMA models(Autoregressive Integrated Moving Average):  
Another very common type of model is the ARIMA model. ARIMA stands for autoregressive integrated moving average models. The main difference between ETS models and ARIMA models lies in what they are modeling. ETS models are modeling the state of the system based on a description of the trend and seasonality, while ARIMA models are modeling the auto-correlations in the time series.  

## Stationarity in the time series:  
A time series is stationary if its statistical properties do not change over time. This means that the mean, variance, and autocorrelation structure are constant over time. White noise is a good example of a stationary time series. A non-stationary time series will have trend and seasonality, which will affect the time series at different points in time. A time series with cyclic behavior is stationary, provided it has neither trend nor seasonality. There are several methods to check for stationarity such as: the augmented Dickey-Fuller test and the Kwiatkowski-Phillips-Schmidt-Shin test. A more visual test is to plot the ACF. If it drops quickly to 0, we are in the presence of a stationary time series.  

## Differencing a time series for stationarity:  
We can turn a non-stationary time series into a stationary time series through a process called differencing. Differencing is a very simple operation. We take the difference between the current observation and the previous observation. This is known as the first-order differencing. If we want to difference the differenced time series, we are doing second-order differencing, and so on. The number of times we difference a time series is known as the order of differencing. A variation of this method is when we take the difference between a data point and the previous observation of the same season. This is know as seasonal differencing, or lag-m differences, because we are subtracting the observation of the same season, m periods ago.  

## Autoregressive models:  
In the case of an autoregressive model, the dependent variable is a linear combination of the previous observations. This is known as an autoregressive model. The order of the autoregressive model is the number of previous observations that are used to predict the current observation and is denoted by p. These type of models are extremely flexible and can be used to model a wide variety of time series.  

## Moving average models:  
If instead of using the previous observations to predict the current observation, we use the errors of the previous observations, we get a moving average model. The order of the moving average model is the number of previous observations that are used to predict the current observation and is usually denoted by q. If we combine both of these models, we reach the ARIMA model. The ARIMA model is a combination of autoregressive and moving average models and is denoted by ARIMA(p,d,q). The p is the order of the autoregressive model, the d is the order of differencing, and the q is the order of the moving average model.  

## SARIMA models:  
ARIMA models do not handle seasonality well. This is where SARIMA models come in. SARIMA stands for Seasonal autoregressive integrated moving average. SARIMA models are a combination of ARIMA models and seasonal differencing. The SARIMA model is denoted by SARIMA(p,d,q)(P,D,Q)m, where the first three parameters are the same as the ARIMA model, and the last three parameters are the seasonal parameters. P is the order of the seasonal autoregressive model, D is the order of seasonal differencing, and Q is the order of the seasonal moving average model, m is the number of periods in a season.  

## The Prophet model:  
It was introduced by Facebook and it aims to forecast daily data with weekly and yearly seasonality. Behind the hood, this is an additive model in which a non-linear trend is established, incorporating yearly, weekly and daily cyclical patterns, as well as impacts from holidays. Its performance is optimal when used with data that exhibits strong seasonal fluctuations and a history featuring multiple seasonal cycles. It is also very easy to use, and it is very fast. It is very robust to missing data and shifts in the trend, and it handles outliers quite well.


