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
## ETL  
# Singer  
It is an open source standard for ETL created and sponsored by Stitch that lets you write scripts to move data from sources to targets. In essence, it allows us to quickly create a data pipeline.  
Singer defines some core concepts to handle the common data pipeline abstractions:  
# 1. Taps:  
The primary function of a tap is to extract data from its source in a structured format. Taps are designed to be source specific, meaning each tap is tailored to extract data from a particular type of data source. For instance, there might be a tap for salesforce, another for MySQL databases and yet another for Google sheets.  

# Targets:  
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

lower_bound=Q1-1.5*IQR  
upper_bound=Q3+1.5*IQR  


