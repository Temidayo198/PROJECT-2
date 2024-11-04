# Project Title: Understanding Subscribers: Customer Segmentation Analysis for a Subscription Service

## Table of Contents
[Project Overview](#project-overview)

[Project Objectives](#project-objectives)

[Data Source](#data-source)

[Tool Used](#tool-used)

[Data Analysis Process](#data-analysis-process)


### Project Overview
---
This project involve analyzing customer data from a subscription service to identify distinct customer segments based on their subscription patterns, preferences, and behaviors.

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

```

```SQL
select [Subscription_Type], count([Customer_ID]) as Number_of_Customers from [dbo].[LITA Capstone Dataset (1) CSV 2]
where [Subscription_Type] is not null
group by [Subscription_Type] order by Number_of_Customers

```

```SQL
SELECT [Customer_ID], [Subscription_Start], [SubscriptionEnd] FROM [dbo].[LITA Capstone Dataset (1) CSV 2]
WHERE [Canceled] = 'TRUE' AND DATEDIFF(month, [Subscription_Start], [SubscriptionEnd]) <= 6

```

```SQL
select AVG(DATEDIFF(day, [Subscription_Start], [SubscriptionEnd])) as Average_Subscription_Duration from [dbo].[LITA Capstone Dataset (1) CSV 2]
```

```SQL
SELECT [Customer_Id] FROM [dbo].[LITA Capstone Dataset (1) CSV 2]
WHERE DATEDIFF(MONTH, [Subscription_Start], [SubscriptionEnd]) > 12

```

```SQL
select [Subscription_Type], sum([Revenue]) as TotalRevenue_by_SubscriptionType from [dbo].[LITA Capstone Dataset (1) CSV 2]
where [Subscription_Type] is not null
group by  [Subscription_Type]  order by TotalRevenue_by_SubscriptionType

```

```SQL
SELECT TOP 3 [Region], COUNT([Canceled]) AS Sum_of_SubscriptionCancellation
FROM [dbo].[LITA Capstone Dataset (1) CSV 2]
WHERE [Canceled] = 'TRUE'
GROUP BY [Region] ORDER BY Sum_of_SubscriptionCancellation DESC

```

```SQL
SELECT [Canceled], COUNT([Canceled]) AS STATUS_COUNT FROM [dbo].[LITA Capstone Dataset (1) CSV 2]
WHERE [Revenue] IS NOT NULL
GROUP BY [Canceled] ORDER BY STATUS_COUNT

```



