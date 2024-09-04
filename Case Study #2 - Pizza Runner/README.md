# Case Study #2 - Pizza Runner 🍕

<div>
  <img src="SQL_Challenge_pic_2.png" width="50%"/>
</div>

# Contents

* [Introduction](#Introduction)
* [Problem Statement](#Problem-Statement)
* [Entity Relation Diagram](#Entity-Relationship-Diagram)
* [Case Study Questions and Solutions](#Case-Study-Questions-and-Solutions)
* [Bonus Questions and Solutions](URL)
* [Key Insights](URL)

# Introduction

Welcome to the Pizza Runner Case Study! Follow Danny's journey as he combines the irresistible allure of "80s Retro Styling and Pizza Is The Future" to launch Pizza Runner, an innovative venture in the pizza delivery industry. With his background in data science, Danny understands the significance of data collection for business growth. Now, he seeks assistance in cleaning and analyzing the data to optimize Pizza Runner's operations and guide his runners more efficiently. Join us as we explore how data-driven decisions propel Pizza Runner towards success and elevate the pizza delivery experience to new heights.

# Entity Relationship Diagram

<div>
  <img src="Case_Study_2_ERD.jpeg" width="50%"/>
</div>

# Data Cleaning and Transformation

* customer_orders table before...

<div>
  <img src="customer_table_clean.png" width="50%"/>
</div>

* The customer_orders table consists of individual pizza orders, with each row representing a unique pizza.
* Key columns in the table are pizza_id, exclusions, and extras.
* Before utilizing the data for queries, the exclusions and extras columns require a data cleaning process to ensure accuracy and consistency.
* Data cleaning involves handling missing or null values in the exclusions and extras columns.
* The ingredient_id values in the exclusions and extras columns need to be standardized for uniformity.
* Inconsistencies and duplicates in the exclusions and extras data should be resolved to eliminate ambiguities.
* By performing thorough data cleaning, the customer_orders table will be optimized for effective analysis.
* The cleaned data will provide valuable insights into customer preferences, enabling better decision-making for Pizza Runner's operations.
* With accurate data, Pizza Runner can efficiently meet customer demands and deliver an enhanced pizza ordering experience.

```sql
DROP TABLE IF EXISTS customer_orders_tempp;
CREATE TABLE IF NOT EXISTS customer_orders_tempp AS
SELECT 
  order_id,
  customer_id,
  pizza_id,
  CASE 
    WHEN exclusions IS NULL OR exclusions LIKE 'null' THEN ''
    ELSE exclusions
  END AS exclusions,
  CASE 
    WHEN extras IS NULL OR extras LIKE 'null' THEN ''
    ELSE extras
  END AS extras,
  order_time
FROM customer_orders;

SELECT*
FROM customer_orders_temp
```sql
