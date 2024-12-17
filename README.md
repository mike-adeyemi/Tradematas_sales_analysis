# Data Portfolio Excel to Power BI



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

This will help the marketing team make informed decisions about which 

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

Where is the data coming from? The data is sourced from Trademtas Group of Company (an Excel extract)

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
3. Formatting the data types

## Transform the data




## Create the SQL view


# Testing

- What data quality and validation checks are you going to create?

Here are the data quality tests conducted:

## Row count check

