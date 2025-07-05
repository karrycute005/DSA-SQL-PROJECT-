# DSA-SQL-PROJECT-

## PROJECT TOPIC: KULTRA MEGA STORES INVENTORY

### PROJECT DESCRIPTION:

This project aims to generate insights into the sales performance of the kultra mega stores in different regions over the year 2009 - 2012. By analyzing the data, we want to present key insights and findings to help the management on how to improve their sales and reduce cost while maximizing their proftits.

### DATA SOURCES:

The primary source of the data used is KMS Case study.csv and KMS Order status.csv . You can download it in file repository at the top.

### TOOL USED:
- SQL server( for Querying and Analysis)

### DATA CLEANING AND PREPARATION

The following actions where taken,
1. Data loading and inspection
2. Data transformation

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
11. if the delivery truck is the most economical but the slowest shiping method and express air is the fastest but the most expensive one, do you think the company appropraitely spent shipping costs based on order priority? explain your answer.

### DATA ANALYSIS
 1. The highest sale of product
```SQL
--HIGHEST SALE OF PRODUCT
select * from [KMS ]
select top 1 Product_category,
sum(sales) as Total_sales
from [KMS ]
group by product_category
order by Total_sales desc
```
2.The top 3 and bottom regions in terms of sale
```SQL
--TOP 3 AND BOTTOM REGIONS IN TERMS OF SALES
--TOP 3
select top 3 Region,sum(sales) as Total_sales
from [KMS ]
group by Region
order by Total_sales desc
--BOTTOM 3
select top 3 Region,sum(sales) as Total_sales
from [KMS ]
group by Region
order by Total_sales asc
```
3. Total sales of appliances in ontario
```SQL
--TOTAL SALES OF APPLIANCES IN ONTARIO-
select Region, sum(sales) as Total_sales_of_appliances
from [KMS ]
where product_sub_category = 'Appliances'
and Region ='ontario'
group by Region
```
4.The bottom 10 customers
```SQL
--BOTTOM 10 CUSTOMERS IN TERMS OF REVENUE
select top 10 Customer_Name, sum(sales) as Revenue
from [KMS ]
group by Customer_Name
order by Revenue asc
```
5. The most shipping cost and the shipping method
```SQL
-- MOST SHIPPING COST AND THE SHIPPING METHOD
Select top 1 Ship_mode, sum(Shipping_cost) as Total_shipping_cost
from [KMS ]
group by Ship_Mode
order by Total_shipping_cost
```
6.The most valuable customer and product purchased
```SQL
--MOST VALUABLE CUSTOMERS AND PRODUCT/SERVICES PURCHASED
select top 3 Customer_Name, Product_category, sum(order_quantity*unit_price) as Total_sales
from [KMS ]
group by customer_name, product_category
order by Total_sales desc
```
7.The small business customer who had the highest sale
```SQL
--SMALL BUSINESS CUSTOMER THAT HAD THE HIGHEST SALE
Select top 1 Customer_Name,sum(sales) as Total_sales
from [KMS ]
where Customer_Segment ='small business'
group by customer_name
order by Total_sales desc
```
8. The corporate customer that placed most number of orders
```SQL
--CORPORATE CUSTOMERS THAT PLACED MOST NUMBER OF ORDERS
select top 1 Customer_name, count(order_quantity) as Orders
from [KMS ]
where Customer_segment ='corporate'
group by Customer_name
order by orders desc
```
9.The most profitable consumer customer
```SQL
--MOST PROFITABLE CONSUMER CUSTOMER
Select top 1 Customer_name, sum(profit) as Profit
from [KMS ]
where Customer_segment='Consumer'
group by Customer_name
order by Profit desc
```
10. The customers who returned items and the segment
```SQL
--CUSTOMER WHO RETURNED ITEMS AND SEGMENT
Select * from [KMS Order Status]
select * from [KMS ]

select distinct
	k.order_id,
	k.customer_name,
	k.customer_segment,
	O.[Status]
from [KMS ] as K
 join
[kms order status] as O
on k.order_id = O.Order_ID
where O.order_id is not null
```
11. SHIPPING METHOD, SHIPPING COSTS BASED ON ORDER PRIORITY
```SQL
--SHIPPING COST BASED ON ORDER PRIORITY
Select 
	Order_Priority,
	ship_mode,
count(order_id) as order_count,
sum(shipping_cost) as Total_shipping_cost
from [KMS ]
group by Order_Priority,Ship_Mode
order by Order_Priority,Total_shipping_cost desc;
```

### RESULTS/FINDINGS

The highest product category that generated more revenue for the company was Technology and they came from these regions. " West, Ontario,and Praine. While the regions that didn't do well in sales are; Nunavut, Northwest Territories, Yukon. S

### RECOMMENDATION

- Provide Early Access to New Products:
Reward loyal customers by offering them early access to new products or limited-edition items. 

- Create Loyalty Programs:
Implement a tiered loyalty program with exclusive benefits based on purchase volume or frequency, encouraging repeat business. 

- Personalized Product Recommendations:
Utilize customer data to suggest relevant products based on their past purchases and browsing history. 

- Exclusive Events and Experiences:
Invite top customers to exclusive events, workshops, or product previews to foster a sense of belonging and appreciation. 

- Customer Service Focus:
Provide excellent customer service to all customers, but prioritize exceptional support and quick issue resolution for your top customers.




