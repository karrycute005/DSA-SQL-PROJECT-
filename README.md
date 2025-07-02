# DSA-SQL-PROJECT-

## PROJECT TOPIC: KULTRA MEGA STORES INVENTORY

This project aims to generate insights into the sales performance of the kultra mega stores in different regions over the year 2009 - 2012. By analyzing the data, we want to present key insights and findings to help the management on how to improve their sales and reduce cost while maximizing their proftits.

### DATA SOURCES:

The primary source of the data used is KMS Case study.csv and KMS Order status.csv . It was provided by the (DSA Incubator Hub). You can download it in file repository.

### TOOL USED:
- SQL server( for Querying and Analysis)
- Microsoft Excel ( for cfreating a report)

### DATA CLEANING AND PREPARATION

The following actions where taken,
1. Data loading and inspection
2. 

### EXPLORATORY DATA ANALYSIS

It involved the exploring of the data to answer some questions about the data such as;
1. Which product had the highest sales?
2. What are the top 3 and bottom 3 Regions in terms of sales?
3. What where the toatal sales of appliances in Ontario?
4. Advice the manangement of KMS on what to do to increase the revenue from the bottom 10 customers?
5. KMS incurred the most shipping cost using which shipping mode?
6. Who are the most valuable customers, and what products or services do they typically purchase?
7. Which small business cutomer had the highest sale?
8. Which corporate customer placed the most number of orders in 2009 - 2012?
9. Which consumer customer was the most profitable
10. Which customer returned items, and what segment do they belong to?
11. if the delivery truck is the most economical but the slowets shiping methpd and express air is yhe fastst but tge  ose expensove one, doyo think hge company appropraitely spent shi[ping costs baasd on orddr priority? explain your answer.

### DATA ANALYSIS
```SQL
select * from [KMS ]
select top 1 Product_category,
sum(sales) as Total_sales
from [KMS ]
group by product_category
order by Total_sales desc


