# Top Amazon Categories & Consumer Behavior

## Table of Contents
- [Project Overview](#project-overview)
- [Problem Statement](#problem-statement)
- [Data Sources](#data-sources)
- [Tools](#tools)
- [Data Cleaning / Preparation](#data-cleaning--preparation)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Data Analysis & Visualizations](#data-analysis--visualizations)
- [Results / Conclusion](#results--conclusion)
- [Recommendations](#recommendations)
- [References](#references)


## Project Overview
---
An Amazon retailer would like know the most popular categories of products being sold on Amazon.com and which types products are gaining what type of interactions from Amazon shoppers. These types of analysis and insights are crucial to guide retailers' focus on what products to sell given the virtually "unlimited" merchandise category options.
 
<img width="1014" alt="Interactions_per_top_category_plots" src="https://github.com/NateshaMortimer/Amazon-Retail-Analytics/assets/171082935/11997f7f-9391-4ded-a4f3-d16a726ef47c">



## Problem Statement
**Problem:** Online Amazon retailers are offering 10,000+ unique products across several categories, but have no insight into the rank of product categories or if consumer interaction patterns exist across the products from top categories. 

**Goal:** Find the top 10 categories across the 10,000+ unique product offerings and investigate the relationship between products from top categories and the type of consumer interactions they receive. 

## Data Sources
The product details dataset provides product details for each unique product offering on Amazon.com. The key detail we'll be focusing on are the Categories of for each product.

The e-commerce sales dataset provides information on about client interactions such as, whether a customer viewed, liked, or purchased a product.

We'll be using both datasets do analysis on Category frequency and products that received shopper interactions.

- [product_details shortened .csv](https://www.kaggle.com/datasets/datascientist97/e-commerece-sales-data-2024/data?select=product_details.csv)
- [E-commerece sales data 2024.csv](https://www.kaggle.com/datasets/datascientist97/e-commerece-sales-data-2024/data)

## Hypothesis:
I hypothesize that since there are so many different type of product categories, there will not be "1" clear top product category across all category types. Also, I think that of the top few/most fequent categories will have the most product interactions (views, likes, purchases) across the board.

## Tools
- Python - Data Cleaning, Data Analysis, Visualizations
    - String Manipulation
    - String Formating
    - Set Operations
    - Pandas
    - Lambda Functions
    - List Comprehension
    - Nested Data
    - Dictionaries
    - Numpy
    - Pandas
    - Seaborn
    - Matplotlib


## Mathematical & Statistical Concepts
- Linear Algebra
   - Matrix Operations
   - Singular Value Decomposition
   - Principal Component Analysis
- Statistics
   -  Count
   -  Percentages


## Data Cleaning / Preparation
In the initial data preparatiion phase, the following tasks were performed:
1. Data loading and inspection
2. Removal of irrelevant columns in product details dataset
3. Handling missing values
   - Verify no products with missing Product IDs
4. Data cleaning and formatting
   - Find products with missing Category information and fill in "Other" as Category to not remove valuable information from analysis
  
     
## Exploratory Data Analysis
EDA involved exploring the product data to answer key questions, such as:
- What are the top product cateogies for product offerings?
- What products are in the top categories?
- What percentage of the total product offerings are in the top 10 product categories?
- How many product offerings belong to the top 10 product categories?
  <img width="521" alt="top_10_categories_df" src="https://github.com/NateshaMortimer/Amazon-Retail-Analytics/assets/171082935/9ad5b898-7b2d-492d-beb1-e09c9eb86187">


## Secondary Data Cleaning / Preparation
In the initial data preparatiion phase, the following tasks were performed:
1. Data loading and inspection
2. Removal of irrelevant columns in product details dataset
3. Handling missing values
   - Drop rows that contain null values
4. Data cleaning and formatting
   - Find products with missing Category information and fill in "Other" as Category to not remove valuable information from analysis

## Data Analysis & Visualizations
Here's a glimpse of the initial analysis of products in top categories and consumers interactions. I arrived here by completing the following steps.

1. Merge the previously created Top Category Dataframe and the cleaned E-Commerce Dataframe and adding a Value column to count the presence of each interaction.
   
   <img width="339" alt="top_category_interaction_merge" src="https://github.com/NateshaMortimer/Amazon-Retail-Analytics/assets/171082935/5b38c882-7331-493d-b45f-efedc880473a">

2. Group the Top Category by Interaction Type  and summing the Values column.

   <img width="360" alt="group_category_interaction" src="https://github.com/NateshaMortimer/Amazon-Retail-Analytics/assets/171082935/cee0f10c-3ae5-4022-9f3f-f1aee5e85c33">

3. Pivot out the Interaction Types into columns and insert respective values from Values column. Then replace NaN values with zero.
   
<img width="328" alt="top_category_interactions_pivot_table" src="https://github.com/NateshaMortimer/Amazon-Retail-Analytics/assets/171082935/428b190c-ebcb-4c27-b395-21a556ed0b43">


```sql
  SELECT * FROM table1
  WHERE cond = 2;
```

## Results / Conclusion
cdbshjbsvfdbj 

## Recommendations
Based on the the analysis, the following actions are recommended
- Invest in indnsjkd
- Listen todfdf
- Implement survey vfdvf

## Limitations / Challenges
I had to remove all zero values from budget and revenue because they would have negatively affected....There are a still few outliers - remaining outliers were manged by fndjvnfdnvjk extropalation


## References
1. Data Book for Experts by Natesha
2. [Stack Overflow](https://stack.com)

   😄

|Heading1 | Heading2|
|-------- | --------|
|Content | Content2|
| Python | SQL |

`column_1`

**bold**

*italic*
 
