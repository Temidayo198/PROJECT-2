# Project Title: Understanding Subscribers: Customer Segmentation Analysis for a Subscription Service

## Table of Contents
[Project Overview](#project-overview)

[Project Objectives](#project-objectives)

[Data Source](#data-source)

[Tool Used](#tool-used)

[Data Analysis Process](#data-analysis-process)


### Project Overview
---
This project aims to provide a comprehensive analysis of sales data for a retail store, identifying key insights to improve business strategies and drive sales growth. Through this analysis, we explore product performance, regional sales distribution, and monthly sales trends to uncover factors contributing to revenue and customer demand patterns using SQL.

### Project Objectives
---
The objective is to;

- retrieve the total number of customers from each region.
- find the most popular subscription type by the number of customers.
- find customers who canceled their subscription within 6 months.
- calculate the average subscription duration for all customers.
- find customers with subscriptions longer than 12 months.
- calculate total revenue by subscription type.
- find the top 3 regions by subscription cancellations.
- find the total number of active and canceled subscriptions.

### Data Source
---
The dataset used for this analysis was provided by the course facilitator as part of the capstone project for data analysis training.

### Tool Used
---
- SQL [Structured Query Language]
  1. For Data import 
  2. For Analysis

  ###  Data Analysis Process
---

- Data Import:
  To prepare the data for analysis in the SQL environment, the original dataset was converted from Excel to a CSV (Comma-Separated Values) format. This format transformation ensured compatibility and ease of import into SQL, allowing for efficient data querying and manipulation.
  
- Data Analysis Techniques: This involve using analytical functions and **`SQL CLAUSES`** such as **`WHERE`**, **`TOP`**, **`GROUPBY`**, **`ORDERBY`** to derive insights from data. Functions include;
  **`SUM()`**, **`AVG()`**,  **`COUNT()`**.

```SQL
Select region, count(CUSTOMER_ID) as Total_CustomerbyRegion FROM [dbo].[LITA Capstone Dataset (1) CSV 2]
where region is not null
group by region order by Total_CustomerbyRegion 

select [Subscription_Type], count([Customer_ID]) as Number_of_Customers from [dbo].[LITA Capstone Dataset (1) CSV 2]
where [Subscription_Type] is not null
group by [Subscription_Type] order by Number_of_Customers

select [Subscription_Type], sum([Revenue]) as TotalRevenue_by_SubscriptionType from [dbo].[LITA Capstone Dataset (1) CSV 2]
where [Subscription_Type] is not null
group by  [Subscription_Type]  order by TotalRevenue_by_SubscriptionType



```




