# Data Portfolio Excel to Power BI

![Kaggle_to_powerbi properties](https://github.com/user-attachments/assets/f7ff0928-5839-4e80-b639-9ee8a5ba70fe)

# Table of Contents
- <span style="color: red">[Objective](#objective)</span>
- <span style="color: blue">[Data Source](#data-source)</span>
- <span style="color: green">[Stages](#stages)</span>
- [Design](#design)
  - [Tools](#tools)
  - [Dashboard Mockup](#dashboard-mockup)
- [Development](#development)
  - [Pseudocode](#pseudocode)
  - [Data Exploration Notes](#data-exploration-notes)
  - [Data Cleaning](#data-cleaning)
  - [Transform the Data](#transform-the-data)
  - [Create the SQL View](#create-the-sql-view)
- [Testing](#testing)
  - [Data Quality](#data-quality)
- [Visualization](#visualization)
  - [Results](#results)
  - [DAX Measures](#dax-measures)
- [Analysis](#analysis)
  - [Findings](#findings)
  - [Validation](#validation)
  - [Discovery](#discovery)
- [Recommendations](#recommendations)
  - [Potential ROI](#potential-roi)
  - [Action Plan](#action-plan)
- [Conclusion](#conclusion)


### Objective
  - What is the key pain point?

As a data analyst, I received a dataset for analysis with the following key objectives:
  -  What is the ideal solution?


To create a dashboard that provides insights into the questions below with their metrics
- The total number of products sold across all countries
- Which country has the highest total sales?
- What is the top-selling product across all countries?
- What is the average sale price and manufacturing price across all products?
- What is the total profit earned by the company in the given time period?

This will help the mamagement team make informed decisions about which 

## User Story
As the Data Analyst, I want to use a dashboard that analyses data-driven strategy for the company to expand its products portfolio 

This dashboard should allow me to identify the total number of product sold, country with the highest sales, top selling product, an average price and manufacturing price with the total profit earned by the company within the period of 2018 - 2019

With this information, I can make more informed decisions about the best selling products and profit earned in the space of 2018 - 2019 accross all countries


# Data source
What data is needed to achieve our objective?
We need the company datasets about

- Products
  
- Period of time (The years and months name)
  
- All regions
  
- Manufacturing price
  
- Units sold

- Sale Price

- Gross sales

- COGS

Where is the data coming from? The data is sourced from the management team, Trademtas Group of Company (an text extract)

# Stages
- Design
- Developement
- Testing
- Analysis

# Design

## Dashboard components required
 - What should the dashboard contain based on the requirements provided?

To understand what it should contain, we need to figure out what questions we need the dashboard to answer:

1. The total number of products sold across all countries
2. Which country has the highest total sales?
3. What is the top-selling product across all countries?
4. What is the average sale price and manufacturing price across all products?
5. What is the total profit earned by the company in the given time period?

For now, these are some of the questions we need to answer, this may change as we progress down our analysis.

## Dashboard mockup

- What should it look like?

Some of the data visuals that may be appropriate in answering our questions include:

1. Table
2. Treemap
3. Scorecards
4. Horizontal bar chart

![Dashboard_image](https://github.com/user-attachments/assets/9320bdb7-6cc0-4be1-a02a-1677b3228aa5)



## Tools

|Tool|Purpose|
|----|-------|
|Excel|	Exploring the data|
|SQL Server|	Cleaning, testing, and analyzing the data|
|Power BI|	Visualizing the data via interactive dashboards|
|GitHub	|Hosting the project documentation and version control|
|Mokkup AI|	Designing the wireframe/mockup of the dashboard|

# Development

## Pseudocode

- What's the general approach in creating this solution from start to finish?
1. Get the data
2. Explore the data in Excel
3. Load the data into SQL Server
4. Clean the data with Excel
5. Test the data with SQL
6. Visualize the data in Power BI
7. Generate the findings based on the insights
8. Write the documentation + commentary
9. Publish the data to GitHub Pages


## Data exploration notes
This is the stage where you have a scan of what's in the data, errors, inconcsistencies, bugs, weird and corrupted characters etc

- What are your initial observations with this dataset? What's caught your attention so far?
1. The data given for analysis are in scattered text format with delimiter "tab", so some of the columns must be properly arranged in tables
2. There are at least 13 columns that contain the data we need for this analysis, which signals we have everything we need from the file without needing to contact the client for any more data.
3. We have more data than we need in text format, so some of these columns would need to be removed.

## Data cleaning
- What do we expect the clean data to look like? (What should it contain? What contraints should we apply to it?)

The aim is to refine our dataset to ensure it is structured and ready for analysis.

The cleaned data should meet the following criteria and constraints:

- Only relevant columns should be retained.
- All data types should be appropriate for the contents of each column.
- No column should contain null values, indicating complete data for all records.

Below is a table outlining the constraints on our cleaned dataset:

|Property|Description|
|--------|-----------|
|Number of Rows|700|
|Number of Columns|13|


And here is a tabular representation of the expected schema for the clean data:

|Column Name|Data Type|Nullable
|-----------|---------|--------|
|Country|VARCHAR|NO|
|Product|VARCHAR|NO|
|Units_sold|SMALLINT|NO|
|Manufacturing_Price|SMALLINT|NO|
|Sale_price|SMALLINT|NO|
|Gross_sales|INT|NO|
|Discounts|MONEY|NO|
|Sales|FLOAT|NO|
|COGS|FLOAT|NO|
|Profit|FLOAT|NO|
|Date|date|NO|
|Month_name|NVARCHAR|
|Year|smallint|NO|

- What steps are needed to clean and shape the data into the desired format?

1. Change the data delimiter to a table
2. Remove unnecessary columns by only selecting the ones you need
3. Formatting the data type

# Testing

- What data quality and validation checks are you going to create?

Here are the data quality tests conducted:

## Row count check

```sql
/*
# Data quality tests 
1. The data needs to be 700 records sales_data (row count test)	--- (passed!!!)

Row count - 700 
Column count - 13        */

-- 1. ROW COUNT

SELECT * FROM Sales_data;
	SELECT 
	COUNT(*) as no_of_rows
FROM 
	Sales_data

```

![Data_quality_tests_row_count_1](https://github.com/user-attachments/assets/9fad3420-7534-4e1d-9b73-58acbfef17e5)


## Column count check

### SQL query

```sql

/*
# Data quality tests 
2. The data needs 13 fields (column count test)								--- (passed!!!)

Row count - 700 
Column count - 13				*/
-- 2. COLUMN COUNT

SELECT * FROM Sales_data;

SELECT 
	COUNT(*) as column_count 
FROM 
	INFORMATION_SCHEMA.COLUMNS
WHERE 
	TABLE_NAME = 'sales_data'

```


### Output


![Data_quality_tests_column_count_2](https://github.com/user-attachments/assets/463b6a3e-94fe-43d8-a84d-ad90c139ea05)




## Data Type check




### SQL query

```sql
/*
# Data quality tests 
3. The country, product column must be string format, and the other columns must be 
	numerical data types (data type check)    --- (passed!!!)			*/
-- 3. Check data type 

	SELECT 
	COLUMN_NAME, DATA_TYPE
FROM 
	INFORMATION_SCHEMA.COLUMNS
WHERE 
		TABLE_NAME = 'sales_data'

```

### Output

![Check_data_type_3 ](https://github.com/user-attachments/assets/cb891ecc-cd21-42ca-b98f-2b5a11c0b41c)

## Replace null value

### SQL query

```sql

/*

	CREATE VIEW view_sales_data AS
	SELECT * FROM Sales_data;

	*/

-- 4 Replace the null value in the column discount with 0

UPDATE view_sales_data
SET Discounts = 0
WHERE Discounts is NULL;

```

### Output

# Visualization

### Results
- What does the dashboard look like?


This shows the insights analyses of the datasets

## DAX Measures


**1. Total number of products sold accross all countries**




**2. Country with the highest total sales (M)**


**3. Top-selling product accross all countries**


**4. Average sale price and manufacturing price across all products (M)**



**5. Total profit earned by the company in the given time period**


# Analysis

## Findings

- What did we find?

For this analysis, we're going to focus on the questions below to get the information we need for the management -

Here are the key questions we need to answer for our analysis:

1. What is the total number of products sold across all countries?
2. Which country has the highest total sales?
3. What is the top-selling product across all countries?
4. What is the average sale price and manufacturing price across all products?
5. What is the total profit earned by the company in the given time period?


### 1. What is the total number of products sold across all countries?

![image](https://github.com/user-attachments/assets/cf6db583-489c-40c8-8ba4-a59af4c75fab)


### 2. Country with the highest total sales


|Country|	Sales|
|----|--------------|
|India|	$40,809,250|


![image](https://github.com/user-attachments/assets/e80cf5e5-79f1-4361-8d4b-28dfb827d10a)



### 3. Top-selling product across all countries

|Products	|Sum of Units Sales| 
|-----------|-------------|
|Vermont |	506598|
|Burlington |	264238|
|Mandarin |	262837|
|Royal Oak |	225466|
|Kensington |	204165|
|Luxe| 	202791|


![image](https://github.com/user-attachments/assets/10ae5f69-bff2-47d4-a03f-526a9ce916df)




### 4. Average sale price and manufacturing price across all products

|Products|	Average of  Sale Price| 	Average of  Manufacturing Price |
 |-------|------------------------|----------------------------------|
 |Vermont       |	    108	              |10                      |
 |Burlington       |	        115|                          	120|
 |Mandarin |	139	|250|
 |Royal Oak |117	|5|
 |Kensington |	112	|3|
 |Luxe |	129	|260|
|Grand Total	|118	|96|


![image](https://github.com/user-attachments/assets/1e0cd256-cb1a-4b6c-90ba-da719bd619dd)


### 5. Total profit earned by the company in the given time period

|Products	|Sum of  Profit |
|---------------|-----------|
|2018	|$23,591,334|
|2019|	$63,856,287| 
|Grand Total	|$87,447,621| 


### Notes

For this analysis, we'll prioritize analysing the metrics that are important in generating the expected ROI for our marketing client, which are the YouTube channels wuth the most

- subscribers
- total views
- videos uploaded

## Validation

#### 1. Youtubers with the most subscribers

#### Calculation breakdown

Campaign idea = product placement
