## Code repo for this book  
https://github.com/PacktPublishing/Data-Analytics-for-Marketing  
## Books and videos  
https://github.com/packtpublishing  

##  Half the money I spent on advertising is wasted; the trouble is I dont know which half  
--John Wanamaker, the forefather of marketing 

## Analytics  
It is the act of extracting meaningful and actionable insights from data by using a set of techniques and tools paired with domain knowledge. It is the joining of three main aspects- doman knowledge, data and techniques.  

## Marketing analytics:  
It is nothing more than the application of analytical methods to said goal, bringing a quantifiable way of guiding investment or consumer targeting decisions. In other words, it is the technology-enabled and model-supported approach to harness customer and market data to enhance marketing decision making.  

# why marketing analytics?  
- Standard techniques frequently used in marketing include media mix modeling, pricing and promotion analyses, sales force optimization, and customer analytics such as segmentation or lifetime value estimation. The optimization of websites and online campaigns now frequently works hand in hand with the more traditional marketing analysis techniques, coupled with attribution modeling and media mix modeling to understand channel interactions and optimal budget allocation.
- It can also helps with how much to spend on marketing and how to allocate budgets across a portfolio of brands and the marketing mix- and more tactical campaign support in terms of targeting the best potential customer with the optimal message in the most cost-effective medium at the ideal time.

# Different types of analytics  
# Analytics maturity model:  
<img width="718" height="483" alt="image" src="https://github.com/user-attachments/assets/980c51b6-70fa-4d4c-bcf0-7b58484fff66" />  

All analytical questions can be boiled into the following categories:  
1. What happened and when did it happen? - Descriptive analytics  
   - limitation: when someone asks you what happened, what they are really asking is why it happened, which lead us to the next step, diagnostic analytics.  
2. Why and how did it happen? - Diagnostics analytics  
   - In most of the cases, this stage of analytics is often skipped and people will jump straight into the predictive analytics. If you cannot infer why your cost per acquisition jumped by 25 percent in the previous quarter, it will be stretch to attempt to forecast what will happen to your cost per acquisition in the next two quarters.  
3. What will happen in the future?- Predictive analytics  
4. How can I make something happen?- Prescriptive analytics  
   caveat: we should not miss the ladder to jump into this directly. We need the outputs from the previous pillars of descriptive, diagnostic and predictive analytics.

---
# Paralysis by analysis is a reality  
 overthinking and endlessly researching a problem prevent you from making a decision. Driven by perfectionism or fear of making the wrong choice, your brain becomes overwhelmed by the information, causing you to freeze and take no action at all.  

 ---

 # Urchin Tracking Module(UTM) parameters:  
 There are introduced by Google to track the conversions from the URLs. They are as follows:  
 - utm_source: The source of the traffic, such as search engine or a newsletter  
 - utm_medium: The medium of the traffic, such as email or CPC.  
 - utm_campaign: The name of the campaign  
 - utm_term: The keyword used to find the site  
 - utm_content: Used for A/B testing and content-targeted ads.

---

# Technical debt:  
It is a concept in programming that reflects the extra development work that arises when code that is easy to implement in the short run is used instead of applying the best overall solution. It is the software engineering equivalent of using your credit card to pay a bill. You will have to pay down the interest,; the longer you wait, the higher the cost you will incur.
 
---
# ETL  
# Singer  
It is an open source standard for ETL created and sponsored by Stitch that lets you write scripts to move data from sources to targets. In essence, it allows us to quickly create a data pipeline.  
Singer defines some core concepts to handle the common data pipeline abstractions:  
# 1. Taps:  
The primary function of a tap is to extract data from its source in a structured format. Taps are designed to be source specific, meaning each tap is tailored to extract data from a particular type of data source. For instance, there might be a tap for salesforce, another for MySQL databases and yet another for Google sheets.  

# 2. Targets:  
A targets, in Singer parlance, is a data loading script or tool that takes the standardized output from a tap and loads it into a destination system. Destinations can vary widely and can include databases, datawarehouses, analytics platforms, or even other file formats. Like taps, targets are designed to be destination-specific, with each target crafted to load data into a particular type of destination. For example, there might be a target for loading data into PostgreSQL, another for Snowflake, and another for a CSV file.  
The role of the target is to receive the data from the tap, transform it if necessary to fit the destination's requirements, and then manage the process of inserting the data into the destination. This process may involve handling authentication with the destination, managing API request for web-based destinations, executing SQL commands for databases, or simply writing files in the case of file-based destinations.  

Singer has targets for CSV files, databases such as PostgreSQL, and even ETL platforms such as Keboola.  

# Data exchange format:  
A JSON file, with a Singer-specific schema, is used as the data exchange format between taps and targets. While it may seem an unnecessary extra step, it allows us to abstract away the data exchange from the specific tap and target, making it agnostic.  

---

# Descriptive statistics:  
# Histogram:  
It is nothing more than a count of the frequency of the ordered values, in bins of fixed size. This shows us the shape and spread of the data.  

# Percentiles and Quartiles:  
Percentiles split the data from the 1st to the 100th percentile. In numpy, we can control the percentile we want by using the q parameter, with a range from 1 to 100.  

A quantile is simply the percentile that splits the data into quarters and can be calculated with the np.quantile() function, with the difference that the control parameter ranges from 0 to 1.  

The IQR is a good method for spotting outliers as we can use a simple heuristic of calculating the upper and lower bounds.  

```text
lower_bound=Q1-1.5*IQR
upper_bound=Q3+1.5*IQR
```    

Any data point outside of the bounds can be classified as an outlier.  

A good visualization for this is a boxplot, also known as a box and whiskers plot. It plots a box that's bounded by the 1st and 3rd quantiles- that is, the 25% and 75% portions of the data. The line in the middle of the box will show us the median. The length of the box is the IQR, and you know that is contains, by definition, 50% of the dataset. The bars at the edges represent the 1.5*IQR. Everything below, or above, can be considered an outlier.  

<img width="692" height="337" alt="image" src="https://github.com/user-attachments/assets/1df30203-9a9d-4d16-801c-58eec04e689d" />  

An alternative to using a boxplot, but with the same function, is a violin plot. A violin plot blends the characteristics of a box plot with those of a histogram. It will show the distribution of the data, along with the mean, 1st and 3rd quantiles, and the IQR range. The name comes from the shape of how the distribution looks in the chart, shaped like a violin.  

<img width="365" height="365" alt="image" src="https://github.com/user-attachments/assets/d090eb92-ac29-43d0-a330-6744c307b957" />  

# Difference between boxplot and violin plot:  
While a boxplot only shows summary statistics such as the median, interquartile range, and outliers, a violin plot shows the entire distribution of the data. This encompasses additional information, such as the density of the data points around different values, thus providing more nuanced(subtle details) insights into the shape of the data distribution.  

# Descriptive statistics:  
# Mean:  
Definition  
The mean is the average value of a dataset.  
Discrete Data Formula  
Formula  
Mean = (Σx) / n  
Where  
x = observations  
n = number of observations  

Continuous Data Formula (Grouped Data)  
Formula  
Mean = (Σf·m) / (Σf)  
Where  
f = frequency  
m = class midpoint  
Pros  
Easy to calculate.  
Uses all data values.  
Useful for further statistical analysis.  

Cons  
Affected by outliers.  
May not represent skewed data well.

# Weighted Mean  
Definition  
The weighted mean gives different importance (weights) to different observations.  
Discrete Data Formula  
Formula  
Weighted Mean = (Σw·x) / (Σw)  
Where  
x = observations  
w = weights  

Continuous Data Formula  

Formula  
Weighted Mean = (Σw·m) / (Σw)  
Where  
m = class midpoint  
w = weight or frequency  

Pros  
Accounts for importance of observations.  
More accurate when data have different weights.  

Cons  
Requires appropriate weights.  
Can be misleading if weights are chosen poorly. 

# Median:  

**Definition**

The median is the middle value of a dataset when the data is arranged in ascending or descending order.  

# Discrete Data Formula

- If n is odd:
  Median = (n + 1)/2 th observation

- If n is even:
  Median = Average of (n/2)th and (n/2 + 1)th observations

# Continuous Data Formula (Grouped Data)

Median = L + [((N/2) - CF) / f] × h

**Where**

- L = Lower boundary of median class
- N = Total frequency
- CF = Cumulative frequency before the median class
- f = Frequency of the median class
- h = Class width

# Pros

- Not affected by outliers.
- Suitable for skewed data.

# Cons

- Does not use all observations.
- Less useful for advanced statistical analysis.

---

# 4. Mode

**Definition**

The mode is the value that occurs most frequently in a dataset.

# Discrete Data Formula

Mode = Value with the highest frequency.

# Continuous Data Formula (Grouped Data)

Mode = L + [(f₁ - f₀) / (2f₁ - f₀ - f₂)] × h

**Where**

- L = Lower boundary of modal class
- f₁ = Frequency of modal class
- f₀ = Frequency of class before modal class
- f₂ = Frequency of class after modal class
- h = Class width

# Pros

- Easy to identify.
- Can be used for nominal (categorical) data.

# Cons

- May have more than one mode or no mode.
- Does not use all observations.

# Data skewness:  
<img width="539" height="335" alt="image" src="https://github.com/user-attachments/assets/89fb9817-4b29-4ea9-a6e4-b2618de6ad15" />  

# Measures of variability:  
# Range

**Definition**

The range is the difference between the largest and smallest values in a dataset.

# Discrete Data Formula

Range = Maximum Value − Minimum Value

# Continuous Data Formula (Grouped Data)

Range = Upper Boundary of Highest Class − Lower Boundary of Lowest Class

**Pros**

- Very easy to calculate.
- Gives a quick measure of data spread.  


**Cons**

- Uses only the largest and smallest values.
- Highly affected by outliers.

# Variance:  
Here we will calculate the spread of the data from the mean. On a dataset, the sum of absolute deviations from the mean will sum to zero, so you essentially dividing 0 by a number, which is 0, rendering the metric useless. The underlying cause of this is that some data points will deviate with a positive sign from the mean, and others with a negative sign, essentially canceling each other out. 

The obvious solution is just to square the individual deviations from the mean and sum them. This would turn every negative deviation into a positive number while preserving the magnitude of deviation. One caveat here is, we had to square the deviations, meaning we are no longer measuring in the same units as the underlying data. That is where standard deviation comes in.


**Definition**

Variance measures how far the data values are spread from the mean.

# Discrete Data Formula

Population Variance:
σ² = Σ(x − μ)² / N

Sample Variance:
s² = Σ(x − x̄)² / (n − 1)

**Where**

- x = Observation
- μ = Population mean
- x̄ = Sample mean
- N = Population size
- n = Sample size

# Continuous Data Formula (Grouped Data)

Population Variance:
σ² = Σf(m − μ)² / Σf

Sample Variance:
s² = Σf(m − x̄)² / (Σf − 1)

**Where**

- f = Frequency
- m = Class midpoint

# Pros

- Uses all data values.
- Measures data spread accurately.

# Cons

- Affected by outliers.
- Difficult to interpret because units are squared.

# Why do we divide by (n − 1) in Sample Variance?

When calculating **sample variance**, we divide by **(n − 1)** instead of **n** because the sample mean is estimated from the sample itself. This uses **one degree of freedom**, leaving only **(n − 1)** independent observations.

Dividing by **n** tends to **underestimate** the true population variance. Using **(n − 1)** (called **Bessel's Correction**) provides a better estimate of the population variance.

---

## Example 1

Sample data:

```
2, 4
```

Sample mean:

```
(2 + 4) / 2 = 3
```

Squared deviations:

```
(2 − 3)² = 1
(4 − 3)² = 1

Total = 2
```

Using **n**:

```
Variance = 2 / 2 = 1
```

Using **(n − 1)**:

```
Variance = 2 / 1 = 2
```

Dividing by **(n − 1)** gives a better estimate of the population variance.

---

## Example 2 (Understanding Degree of Freedom)

Suppose the sample is:

```
5, 8, ?
```

The sample mean is **10**.

```
(5 + 8 + x) / 3 = 10
```

```
5 + 8 + x = 30
```

```
x = 17
```

Once you know the **sample mean** and the **first two values**, the **last value has no freedom**—it is completely determined.

In general:

> Once the sample mean is fixed, **one observation becomes constrained.**

Therefore:

> **Only (n − 1) values are free to vary.**

This is why the number of **degrees of freedom** is:

```
Degrees of Freedom = n − 1
```

---

# Key Points

- **Population Variance** → Divide by **N**
- **Sample Variance** → Divide by **(n − 1)**
- The sample mean is estimated from the sample itself.
- Once the sample mean is fixed, **one observation becomes constrained**.
- **Only (n − 1) observations are free to vary.**
- Using **(n − 1)** (Bessel's Correction) gives an unbiased estimate of the population variance.

# Standard Deviation

**Definition**

Standard deviation measures how much the data values deviate (spread) from the mean. It is the square root of the variance and is expressed in the same unit as the data.

# Discrete Data Formula

Population Standard Deviation:

σ = √[Σ(x − μ)² / N]

Sample Standard Deviation:

s = √[Σ(x − x̄)² / (n − 1)]

**Where**

- x = Observation
- μ = Population mean
- x̄ = Sample mean
- N = Population size
- n = Sample size

# Continuous Data Formula (Grouped Data)

Population Standard Deviation:

σ = √[Σf(m − μ)² / Σf]

Sample Standard Deviation:

s = √[Σf(m − x̄)² / (Σf − 1)]

**Where**

- f = Frequency
- m = Class midpoint

# Pros

- Uses all data values.
- Expressed in the same unit as the data, making it easy to interpret.
- Widely used in statistics and machine learning.

# Cons

- Affected by outliers.
- Slightly more complex to calculate than the range or variance.

---

## Relationship with Variance

```
Standard Deviation = √Variance
```

```
Variance = (Standard Deviation)²
```

# Example

Suppose the variance of a dataset is:

```
Variance = 25
```

Then,

```
Standard Deviation = √25 = 5
```

This means the data values are, on average, about **5 units** away from the mean.  

# Data standardization or scaling:  
This method is usually done when one of the features has a higher variance than the others. It simply involves two steps:  
1. Subtracting the mean from all data points, also know as centering
2. Dividing the preceding calculations by the standard deviation, also know as scaling.

# Note:  
Data standardization will work if the features you are standardizing follow a linear distribution. A linear distribution is a pattern where the data is distributed evenly around the mean, resulting in a bell-shaped curve when plotted.  

If your features do not follow a linear distribution, it is unwise to attempt to transform the data with the mean and standard deviation. Sales and revenue are usually examples of data that's ill-suited to this form of normalization due to their highly skewed nature. This is where power transformations come in.  

---

# Power transformations:  
The most common power transformations is to log all values in your dataset. In most cases, this simple operation will force your data to "look normal". There are other transformations that you can do to variables like below:  

<img width="707" height="155" alt="image" src="https://github.com/user-attachments/assets/539733e8-282f-4882-ae70-d0775b5815ab" />  


Everything in mathematics, if there is a pattern, a ageneralization usually exists, and this case is no exception: the Box-Cox transformation. The Box-Cox transformation is defined as follows:  

# Box-Cox Transformation Formula

For **λ ≠ 0**:

```text
y(λ) = (x^λ - 1) / λ
```

For **λ = 0**:

```text
y(λ) = ln(x)
```

# min-max scaling:  
The effect of this normalization is to compress all data points in a range between 0 and 1. To achieve this, we must complete two steps:  
1. Subtract the minimum value from each data point
2. Divide the preceding calculation by the maximum value-minimum value. The min-max is nothing more than the range.

### Min-Max Normalization Formula

```
x' = (x - min) / (max - min)
```
while this transformation forces the data to follow a normal distribution, the features will not have unit variance and a mean of 0. Also, its important to note that this transformation does not handle outliers well. Outliers are data points that are significantly different from the other data points. Because min-max scaling compresses all the points into the [0,1] range, outliers will become closer to the bulk of the data, and that reduces the ability to detect and handle these extreme values. It is best to handle outliers before applying min-max scaling.  

# Designing
Desing is not just what it looks like and feels like. Desgin is how it works  
-- Steve Jobs  

# Dashboards:  
A dashboard is, at its simplest, a screen that attempts to condense key metrics and KPIs in an easy and intuitive way, to allow for easy digestion of numerical information. 

# why dashboards?  
As an analyst, we should always save the user time by building a dashboard which helps him/her in the more efficient way in the task that they are aiming for.

# Types of dashboards and their design:  
There are mainly three types of dashboards:  
## 1. Operational dashboards:
These help the user see what's happening right now. They will give one main drivers, that being to give information to the user quickly because they are dealing with the time-sensitive tasks that will most likely require immediate action. We want to present data deviations to the user quickly and accurately.

## 2. Analytical dashboard:  
These help the user understand patterns and trends and have a clear understanding of performance and potential issues for analysis and decision-making. They are not as time-sensitve, nor do they require immediate attention. The goal is to help the user spot trends and make sense of the data.  

## 3. Strategic dashboard:  
These dashboards will help the user track their strategic decisions by tracking key KPIs of the business.  

# Designing concepts of a dashboard:  
When thinking about a dashboard design, it is helpful to consider the exercise as if you were designing a product for consumers. In doing so, you should ask yourself what your target audience is and what they care about.  

# Understanding your audience is key:  
-- Are you talking to the operational side of the business, who need key metrics but a degree of detail to quickly make changes to a maketing campaign on their weekly reviews?
-- Or are you talking to management, who do not need, nor have time for, the nitty-gritty details but need a more bird's-eye view(top down perspective from a high angle, like a bird sees the world) to make quarterly resource allocation of the budge?  

When creating dashboards for marketing analytics, several key heuristics can guide your desing process and ensure the effectiveness of the visualizations. Some of the principles in designing a dashabord are listed below:  
**1. Define the purpose**  
**2. Prioritize important information**  
**3. Optimize data-ink ratio:**  
Minimize the use of decorative elements that do not contribute to the communcation of data. Maximize the proportion of ink(or pixels) used to represent meaningful information.  
**4. Round the numbers for simplicity**    
**5. Choose the right visualization**  
**6. Group related metrics**  
**7. Maintain consistency:**   
Use the same color schema for similar metrics  
**8. Utilize size and position:**  
**9. Provide context for numbers:**   
Accompany numerical values with contextual information to help viewers interpret and evaluate their significance. Provide benchmarks, comparisons, or reference ranges to convey whether a number is good, bad, normal, or unusual.   
**10. Use clear labels**  
**11. User engagement matters:**   
Remember that dashboards are designed for people. While adhering to best practices, dont be afraid to deviate if it enhances viewer engagement and encourages interactions with the data.   
**12. Continuous improvement:**   
Regularly evaluate and evolve your dashboards to ensure they are driving the desired behaviors and delivering actionable insights.  

## Thinking about how to best represent data:  
All too often, analysts just throw charts at the screen. But not all charts are born equal. Each chart serves a purpose, given the information you intend to convey. There are four main categories in charts:  
**Understanding relationships**
**Comparing categories or timeframes**
**Seeing the composition of the data**
**Seeing the distribution or shape of the data**  

**An overview of the chart types. Each chart has a purpose**

<img width="402" height="216" alt="image" src="https://github.com/user-attachments/assets/37b6e13e-f826-47d6-892a-de90290624ce" />  

 # Streamlit:  
 There are increasing limitations to dashboards. They are, by their very nature, statis. Streamlit allows us to move into building dynamic data apps in a way that the user can interact with data in a manner not possible with a dashboard. Three reasons stand out when evaluating Streamlit.  
 - First, Streamlit apps can be set up to reflect changes in real time when the underlying data changes. This means we can create live dashboars that update without user intervention or page refreshes.
 - Secondly, Streamlit is built for Python, making it seamless to integrate with Python's extensive ecosystem of data science libraries such as Pandas, Numpy, and Matplotlib, and machine learning(ML) frameworks such as TensorFlow and scikit-learn.
 - Finally, beyond predefined fileters and selections, Streamlit can take text input, file uploads, and other user-generated content to manipulate data or feed models on the fly, providing a more dynamic interaction model.

# Econometrics and Causal Inference with Statsmodels and PyMC:  
All models are wrong, but some are useful.  
-- George Box  

The differece between a model and an algorithm:  
One should be aware of the fact that a model is not a algorithm. A model is an attempt to represent a phenomenon and the relations betweeen variables mathematically. An algorithm, however is a recipe, a collection of steps, or a set of rules to be followed to achieve a certain outcome. So, a linear regression is a model, but a method such as ordinary least squares is an algorithm that fits a linear regression to the data.  

# Linear regression:  

**Definition**

Linear Regression is a supervised machine learning algorithm used to predict a continuous target variable by finding the best-fit linear relationship between the independent and dependent variables.

### Formula

```
y = β₀ + β₁x
```

**Where**

- y = Predicted (dependent) variable
- x = Independent variable
- β₀ = Intercept
- β₁ = Slope (coefficient)

### Pros

- Simple and easy to interpret.
- Fast to train.
- Works well for linear relationships.

### Cons

- Assumes a linear relationship.
- Sensitive to outliers.
- Performs poorly on non-linear data.

# Assumptions of linear regression:  
- The model will assume that the relationship between dependent and independent variables is linear in nature. This is a very strong assumption, and one might argue that you will most often deal with non-linear data in real life. However, even with a non-linear relationship, a linear regression might still be useful for estimating an average relationship.
- Closely related with the linearity assumption is the additivity assumption. This means that the effect of each independent variable is independent of the other independent variable. When additivity is violated, it makes sense to transform the data. For example, if y=a*b*c, then we can transform the problem with:
  log(y)=log(a)+log(b)+log(b)
- A third assumption of the linear regressions is that the errors from the prediction line are independent from each other. This means that the error of one point does not effect the error of another point. This assumption is violated when you have time series data, or panel data, in a phenomenon called autocorrelation.
- The equal variance of error is out fourth assumption. It is also known as homoscedasticity as opposed to heteroscedasticity, which means we do not have equal variance of errors. This assumption states that the variance of the error is the same for all values of the independent variables. This assumption is violated, for instance, when the relationship between the variables is not linear. While violation of the assumptiom cam be an issue, especially if the regression is to be used for probabilistic prediction., it does not affect the most important aspect of a regression model-how the information is combined and goes into the predictors.
- Our next assumption regarding errors is that they are normally distributed. This assumption is relevant when predicting individual data points. On the other hand, when talking about estimating the regression line, this assumption is not relevant, in most cases. On the topic of the assumption of normality of errors, it is important to emphasize that the normality assumption is for the errors of the regression. The independent variables do not need to be normally distributed. In fact, most of the time, they will not be.
- Finally, the last assumption to be wary(careful) of is the absence of multicollinearity. Thiis means that the independent variables are not highly correlated with each other. This assumption is violated when you have a lot of independent variables and some of them are highly correlated. This is a problem because it makes it difficult to estimate the regression coefficient.

**Note:**  
We have to keep in mind that the model is very sensitive to outliers. We need to handle outliers before running a linear regressions or the model will be biased.  

The most common method to estimate a linear regression model is the OLS method. OLS stands for ordinary least squares, which refers to the way the statisical model fits to the data to produce the best-fit line. The best-fit line is the line that minimizes the sum of the squared errors. The errors are the difference between the actual value of the dependent variable and the predicted value of the dependent variable. The squared errors are used to avoid the errors cancelling each other out, when summing them.  

