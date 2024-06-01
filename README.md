# Top Amazon Categories & Consumer Behavior

## Table of Contents
- [Project Overview](#project-overview)
- [Problem Statement](#problem-statement)
- [Data Sources](#data-sources)
- [Hypothesis](#hypothesis)
- [Tools](#tools)
- [Mathematical & Statistical Concepts](#mathematical--statistical-concepts)
- [Data Cleaning / Preparation](#data-cleaning--preparation)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Secondary Exploratory Data Analysis](#secondary-exploratory-data-analysis)
- [Data Analysis & Visualizations](#data-analysis--visualizations)
- [Results](#results)
- [Recommendations](#recommendations)
- [Limitations](#limitations)
- [Future](#future)


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
### Initial Analysis of Top Categories and Consumer Interactions
Here's a glimpse of the initial analysis of products in top categories and consumers interactions. I arrived here by completing the following steps. Then used the Seaborn library to visualize the pivoted dataframe.

<img width="1014" alt="Interactions_per_top_category_plots" src="https://github.com/NateshaMortimer/Amazon-Retail-Analytics/assets/171082935/11997f7f-9391-4ded-a4f3-d16a726ef47c">


1. Merge the previously created Top Category Dataframe and the cleaned E-Commerce Dataframe and adding a Value column to count the presence of each interaction.
   
   <img width="339" alt="top_category_interaction_merge" src="https://github.com/NateshaMortimer/Amazon-Retail-Analytics/assets/171082935/5b38c882-7331-493d-b45f-efedc880473a">

2. Group the Top Category by Interaction Type  and summing the Values column.

   <img width="360" alt="group_category_interaction" src="https://github.com/NateshaMortimer/Amazon-Retail-Analytics/assets/171082935/cee0f10c-3ae5-4022-9f3f-f1aee5e85c33">

3. Pivot out the Interaction Types into columns and insert respective values from Values column. Then replace NaN values with zero.
   
<img width="328" alt="top_category_interactions_pivot_table" src="https://github.com/NateshaMortimer/Amazon-Retail-Analytics/assets/171082935/428b190c-ebcb-4c27-b395-21a556ed0b43">

### Matrix Transposition, Singular Value Decomposition, Principal Component Analysis....Oh My !!
The analysis thus far does an excellent job at showing us the relationship between a specific interaction and whether or not a product was in a top category. Due to the high-dimensionality of the data we cannot begin to understand relationship "across" interaction types. My solution is to use PCA to "press" 8 dimensions into 2 dimensions (2D) to uncover any hidden pattern across interaction types. 

The below steps were used to get prepare the data for PCA.
1. Retrieve the interaction values from the Top Category Dataframe as an Numpy array, transpose the elements, and mean-center (CRUCIAL for PCA).
``` python
new_x = x_values - np.mean(x_values, axis = 0)
```
   
3. Use Singualar Value Decomposition to "break apart" our matrix into various matrices that when multiplies represents out data.
   
``` python
U, Sigma, VT = np.linalg.svd(new_x, full_matrices=False) 
print("U:", U.shape)
print("Sigma:", Sigma.shape)
print("VT:", VT.shape)
```

5. Use one of the matrices complete PCA by making a 2D projection 


```python
# Project into 2-D
# Note that we "could" choose to project into a higher dimension other than 2, 
# We choose to make a 2D projection and not optimize the dimension, so that we could make a 2D visual
Y_k = new_x.dot(VT[0:2, :].T)

# Print
for x, y, label in zip(Y_k[:, 0], Y_k[:, 1], interactions):
    print(f'* {label}: ({x}, {y})')

# Plot
fig = plt.figure(figsize=(3, 3))
plt.scatter(Y_k[:, 0], Y_k[:, 1])
for x, y, label in zip(Y_k[:, 0], Y_k[:, 1], interactions):
    plt.annotate(label, xy=(x, y))
ax = plt.gca()
ax.axis('square');
fig.suptitle("PCA: Interactions / Top Category")
```
<img width="462" alt="pca_2d_visual" src="https://github.com/NateshaMortimer/Amazon-Retail-Analytics/assets/171082935/bf3b6643-847a-498c-a920-cd882ab93099">

### PCA Results Explanation
From the above visual we can see that there is a clear difference bewteern user interactions. Principal Component Analysis "highlights" the fact that there is a substantial difference/variation in "Liked" products across products in top categories. Note that, PCA does NOT show/tell us that "Liked" products are more or less likely to be in a top categories. PCA shows that of products that have consumer interactions, there is a large variance of products being "liked" across the top categories of products. The variance for "Liked" products is (-146.7396456416586, -0.178752667128817).

If anything, PCA can be starting point to further investigate "why" there is a large instance of products being liked instead of viewed or purchased.

## Results 
Overall, 5.919% of products are not associated with the top 10 categories. This doesn't support the first part of hypothesis that categories are "spread" somewhat evenly accross product offerings.

Secondly, I thought that interaction types would be evenly dispersed across categories of products that consumers interacted with. PCA disproved this part of my hypothesis as well. It found a "hidden" insight that "liked" products variance greatly accross products within top categories.

## Recommendations
Based on the the analysis, the following actions are recommended for Amazon retailers
- Choose to sell niche products that are not part of the top 10 categories
- Try to increase conversion rate for consumer interations of product offering from "likes" to purchases 
- Attempt to gain market share in specific top product categories

## Limitations
Having richer e-commerce sales data would have provided deeper insights. Data that would have made analysis more insghtful are: customer location, product discounts, and customer browsing time.

## Future:
Building on top category and PCA, one can complete a multiple regression analysis to isolate the top factors that influence a person to like a product. Then incorporate those top factors into products to attempt to limit the variation of products being liked. Shift the variation bounds up for products that are being viewed and purchased. Finally,one can focus on finding waysto conver likes and view to purchases. 


 
