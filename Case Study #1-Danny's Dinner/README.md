# Case Study #1-Danny's Dinner 👨🏻‍🍳

<div align="left">
<img src="SQL_Challenge_pic_1.png" width="50%">
</div>

# Contents

* [Introduction](#Introduction)
* [Problem Statement](#Problem-Statement)
* [Entity Relation Diagram](URL)
* [Case Study Questions and Solutions](URL)
* [Bonus Questions and Solutions](URL)
* [Key Insights](URL)

# Introduction
In early 2021, Danny loves to eat Japanese food so he embark a risky venture to open up a cute little Japanese restaurant that sells 3 of his favourite foods like sushi, curry and ramen.However, lacking data analysis expertise, the restaurant struggles to leverage the basic data collected during its initial months to make informed business decisions. Danny's Diner seeks assistance using the data for him to make sure that the restaurant is runnning effectively.

# Problem Statement
Danny wants to use the data to answer a few simple questions about his customers, especially about their visiting patterns, how much money they’ve spent and also which menu items are their favourite. Having this deeper connection with his customers will help him deliver a better and more personalised experience for his loyal customers.

He plans on using these insights to help him decide whether he should expand the existing customer loyalty program - additionally he needs help to generate some basic datasets so his team can easily inspect the data without needing to use SQL.

Danny has provided you with a sample of his overall customer data due to privacy issues - but he hopes that these examples are enough for you to write fully functioning SQL queries to help him answer his questions!

Danny has shared with you 3 key datasets for this case study:
* Sales
* Menu
* Members

# Entity Relationship Diagram

<div align="left">
<img src="Case_Study_1_ERD.jpeg" width="50%">
</div>

# Case Study Questions and Solutions

1. What is the total amount each customer spent at the restaurant?

```sql
SELECT S.customer_id AS customer_id, SUM(M.price) AS total_amount
FROM sales AS S
JOIN menu AS M
ON S.product_id = M.product_id
GROUP BY customer_id
ORDER BY customer_id;
```

**Answer:**

<div align="left">
<img src="Dannys_Diner_1.jpeg" width="20%", height="5%">
</div>

* The SQL query retrieves the <mark>customer_id</mark> and calculate the sum of the price aliasing the name as the <mark>total_amount</mark> by each customer in the restaurant.
* It combines the <mark>sales</mark> and <mark>menu</mark> table based on matching each table's <mark>product_id</mark>.
* The results are grouped by <mark>customer_id</mark>.
* The query calculates each <mark>customer_id</mark> by the sum of the <mark>price</mark> of the product.
* Finally the results are alphabetically ordered by <mark>customer_id<mark>.

2. How many days has each customer visited the restaurant?

```sql
SELECT customer_id, COUNT(DISTINCT order_date) AS No_days
FROM sales
GROUP BY customer_id;
```

**Answer**
