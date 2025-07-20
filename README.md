# Identifying-Top-Revenue-Generating-Customers-for-a-Multinational-E-Commerce-Company
This data science research project presents a comprehensive sales analysis of a leading multinational e-commerce company headquartered in the United States, with operations spanning across North and South America, as well as Europe.

# Project Overview
This data science research project presents a comprehensive sales analysis of a leading multinational e-commerce company headquartered in the United States, with operations spanning across North and South America, as well as Europe.

The objective of the study is to analyze and identify the Top 10 highest revenue-generating customers, offering critical business insights into customer value, regional sales dynamics, and strategic growth opportunities.

Leveraging advanced data analytics techniques, including data preprocessing, aggregation, and visualization, this project uncovers key patterns in customer spending behavior across diverse markets.

By ranking customers based on total revenue contribution, the analysis empowers business stakeholders with actionable intelligence to optimize customer relationship management, tailor marketing strategies, and enhance profitability in a globally competitive landscape.

This project serves as a practical application of data science principles in the domain of e-commerce, showcasing the impact of data-driven decision-making on strategic business outcomes.

### Problem Statement
**Who are Top 10 Customers of the Company interms of Total Revenue generated since the company started ?**

### Project Objectives 

1. **To Identify Top Revenue-Generating Customers**

   * By Analyzing sales data to determine the top 10 customers contributing the highest total revenue across all regions.


2. **To Understand Revenue Concentration**

   * By Analyzing how much of the company's total revenue is concentrated among top customers.


3. **To Uncover Geographic Patterns**

   * By Assessing the global distribution of high-value customers across the Countries to identify key markets and regional revenue   clusters.


4. **To Support Strategic Decision-Making**

   * By Providing actionable insights to the company’s sales and marketing teams for developing targeted retention, loyalty, and upselling strategies.



5. **To Demonstrate Real-World Data Science Application**

   * By Showcasing the use of data science tools and techniques (data preprocessing, aggregation, visualization) in solving a real-world business problem.


6. **To Enable Stakeholder Communication**

   * By Creating intuitive visualizations and summaries that allow non-technical stakeholders to understand key findings and insights.


7. **To Lay the Groundwork for Predictive Modeling**

   * By Establishing a foundational dataset and insights that could be extended into customer lifetime value prediction or churn modeling in future phases.

### Data Source
**The Company's central transaction database**

### Project Methodology
- **Data Collection**: Data was collected from the Company's Central Transaction Database

- **Data Pre-processing**: Loaded the data from a CSV file into a Pandas Dataframe

- **Data Inspection and Cleaning**: Checked for Missing values, Checked for Duplicates.

- - Handled missing values
  - Handled duplicate values

- **Data Modification**: generated some  core metrics which were NOT provided from the dataset, and would be required for the purpose of the data   analysis

- **Data Aggregation**: To Compute the major metric : Total Revenue by Customer**

- **Data Sorting/ Data Ranking**: To Determine the Most Importat Metric:  **Top 10 highest revenue-generating customers**

- **Data Visualization**: To uncover the **Top 10 highest revenue-generating customers** in a pictorial form.

- **Data Interpretation**:

- **Key Findings**

- **Conclusions**

- **Reconmendation**

### Data Collection
Sales data was obtained from a central transaction database of the company representing orders placed by customers across multiple countries. Each record included attributes such as:

* `Customer ID`
* `OrderNo`
* `OrderQuantity`
* `CostPrice_usd`
* `SellingPrice_usd`
* `OrderDate`
* `CustomerName`
* `CustomerCity`
* `CustomerState`
* `CustomerCountry`
* `ProductCategory`
* `ProductColor`
* `Model`

### Data Pre-processing
__Task:__ Follow the appropriate steps in reading a CSV file into a pandas Dataframe, 


and  Read the data stored  in the csv file named:  `bikes` From your computer.


The resulting Dataframe should be named : `bikes_df`

```python
# solution
import pandas as pd
bikes_df = pd.read_csv("C:/Users/USER/Downloads/bikes.csv")
bikes_df

```
### Data Inspection and Cleaning
- **1. Check for Missing values**:

```python
# solution 

bikes_df.isna().any()
```

```python

# counting the number of missing value

total_number_of_missing_values_by_column = bikes_df.isna().sum()

total_number_of_missing_values_by_column

```

```python

# visualizing the total number of missing values

import matplotlib.pyplot as plt

total_number_of_missing_values_by_column.plot(kind = "bar")
plt.show()
```
- **2.Handling Missing values**:
```python

# solution 

# bikes_df["ProductColor"].mode()

bikes_df = bikes_df.fillna("Black")

bikes_df
```
```python
# to verify that we have no more missing values on our dataset

bikes_df.isna().any()
```
- **3. Check for  Duplicates**:

```python

# solution

# counting the total number of our datapoint

len(bikes_df)
```

```python

# dropping any duplicates if any exist

bikes_df.drop_duplicates(inplace = True)
```
- **4. Handling Duplicates**:

```python
# solution
# recounting our datapoint again
len(bikes_df)

# this shows there are no duplicates on the dataset
```

### Data Modification

```python

# generating some core metrics which were NOT provided from the dataset, which would be required for the purpose of the data analysis

# solution 

# (1) TotalCostPrice : To be obtained by (OrderQuantity x CostPrice_usd)


bikes_df["TotalCostPrice"] = bikes_df["OrderQuantity"] * bikes_df["CostPrice_usd"] 


# (2) SalesRevenue : To be obtained by (OrderQuantity x SellingPrice_usd)


bikes_df["SalesRevenue"] = bikes_df["OrderQuantity"] * bikes_df["SellingPrice_usd"] 


# (3) Profit : To be obtained by (SalesRevenue - TotalCostPrice)


bikes_df["Profit"] = bikes_df["SalesRevenue"]  - bikes_df["TotalCostPrice"]


# Displaying the result

bikes_df.head()

```
### Data Aggregation

```python

# Computing/ Aggregating the sales data to show Total Revenue by Customer , including their City, State and Country. 

# solution 
total_revenue_by_customer = bikes_df.groupby(["CustomerName", "CustomerCity", "CustomerState", "CustomerCountry",])["SalesRevenue"].sum().reset_index()
# computing the total revenue by customers 
total_revenue_by_customer

```
### Data Sorting/ Data Ranking

```python

# To Determine the Most Importat Metric: Top 10 highest revenue-generating customers 

# solution 

the_top_10_customers = total_revenue_by_customer.sort_values("SalesRevenue", ascending = False).head(10)
the_top_10_customers

```

### Comparison of the Total Revenue Generated by the Top-10 Customers to the Entire Total Revenue of the company

```python

# The Total Revenue Generated by the Top-10 Customers

revenue_summary_of_top_ten_customers = the_top_10_customers["SalesRevenue"].sum().round(1)
revenue_summary_of_top_ten_customers
```
```python

#  entire total revenue of the company
revenue_sum_of_entire_company = bikes_df["SalesRevenue"].sum().round(1)

revenue_sum_of_entire_company
```

```python

percentage_revenue_top_10_customers = (revenue_summary_of_top_ten_customers / revenue_sum_of_entire_company) * 100

ratio = percentage_revenue_top_10_customers.round(2)
ratio
```

```python
print(f"the total revenue generated by the top 10 customers, accounts for {ratio} % of the company's total revenue")
```

### Data Visualization

```python

#  To uncover the Top 10 highest revenue-generating customers in a pictorial form.

# solution 
import matplotlib.pyplot as plt

the_top_10_customers.plot(kind = "bar", x = "CustomerName", y = "SalesRevenue")

# labelling the x and y axis
plt.xlabel("CustomerName")
plt.ylabel("Total Revenue in US Dollars")

# title label
plt.title("The Top 10 Customers By Total Revenue Since The Company Started")

# to show the plot
plt.show
```

### Data Interpretation

The result from the data visualization above shows that all the **Top 10 customers** are all based in **France**

### Key Findings

---

1. **France Dominates among Top-Tier-High-Value-Customers**: 
   All **The Top 10 Customers** are based in **France**, indicating a strong customer base and market penetration in this region.


2. The Company's **Top 10 Customers** Contribute Less Than **1% of Total Revenue of the entire company**.

   
   Despite **France** being the **top revenue generators**, these customers collectively account for a **very small fraction** of the company's overall sales — indicating **broad and diversified revenue streams**.

4. **Revenue is Distributed, Not Concentrated**
   Unlike typical e-commerce businesses that follow the Pareto Principle (80% of revenue from 20% of customers), this company’s revenue is **evenly spread across thousands of customers**, highlighting a mass-market model.


5. **High-Value Customers Are Geographically Clustered**
   The top revenue-generating customers are concentrated in specific cities and departments such as:

   * **Tremblay-en-France**, **Les Ulis**, and **Saint-Denis** in **Seine Saint Denis** and **Essonne**
   * Major urban centers like **Paris**, **Metz**, and **Dunkerque**

6. **Narrow Revenue Spread Among Top Customers**
   The revenue range of the top 10 customers is relatively narrow—from **\$13,144.88** to **\$13,708.12**, suggesting consistent purchasing behavior across the top customer tier.

7. **Top Customers Still Exhibit Stable Purchasing Behavior**
   While their individual contribution is small relative to total revenue, the top customers show **stable, high-value purchasing patterns** — useful for identifying ideal customer personas or retention targets.

8. **Customer Loyalty and Repeat Purchases Likely**
   Given the similar revenue volumes, it’s likely that these customers have regular or subscription-based purchasing behavior.

---

### Conclusions


The company's sales data analysis reveals that the company operates a **high-volume, low-concentration revenue model**, where no single customer or small group significantly influences total revenue. 

This suggests a **wide customer base**, possibly driven by individual, one-time, or small-ticket purchases.

Furthermore, the sales data reveals that the company’s **top 10 most valuable customers are concentrated entirely in France**, with a significant cluster in **Île-de-France** and surrounding regions. 


This concentration indicates a **strong local market presence**, but also highlights a **potential risk** if the company's sales efforts are overly dependent on a single region.

While the **top 10 customers** do not represent a **major share of total sales**, understanding their behavior is still useful for profiling ideal, repeat-purchase customers. Moreover, the fact that all top performers are from France indicates a **regional pattern** in customer loyalty or market engagement.


However, the **absence of high-revenue customers** from other regions such as the **United States, Canada, Germany, UK, and Australia** points to a **potential gap in customer acquisition** or expansion strategy.

---







