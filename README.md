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
