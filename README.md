# Pizza Sales Analysis SQL Server to Power Bi Dashboard

# Project Overview

This project involves the analysis of pizza sales data using SQL for querying and Power BI for visualization. The analysis aims to gain insights into key business performance indicators such as total revenue, sales trends, and customer preferences. These insights can help guide business decisions to optimize sales strategies, improve customer satisfaction, and streamline operations.

# Objectives

The primary goals of this project are:
+ To calculate and visualize key performance indicators (KPIs) related to pizza sales.
+ To uncover insights into sales trends and customer behavior.
+ To identify top and bottom-performing pizza categories and items.
+ To create an interactive Power BI dashboard for easy interpretation of the analysis results.
  
# Data and Analysis

The dataset contains information about pizza sales, including details such as order ID, pizza category, pizza size, quantity sold, and total price. The analysis is broken down into several key sections, each targeting specific business questions and KPIs.

# Key Performance Indicators (KPIs)

## Total Revenue: The sum of all pizza sales.

## SQL Query:

+ Copy code
+ SELECT SUM(total_price) AS Total_Revenue FROM pizza_sales;
  
## Average Order Value: The average amount spent per order.

## SQL Query:

+ Copy code
+ SELECT (SUM(total_price) / COUNT(DISTINCT order_id)) AS Avg_order_Value 
FROM pizza_sales;

## Total Pizzas Sold: The total number of pizzas sold across all orders.

## SQL Query:

+ Copy code
+ SELECT SUM(quantity) AS Total_pizza_sold FROM pizza_sales;
  
## Total Orders: The total number of orders placed.

## SQL Query:

+ Copy code
+ SELECT COUNT(DISTINCT order_id) AS Total_Orders FROM pizza_sales;
  
## Average Pizzas Per Order: The average number of pizzas sold per order.

## SQL Query:

+ Copy code
+ SELECT CAST(SUM(quantity) AS DECIMAL(10,2)) / CAST(COUNT(DISTINCT order_id) AS DECIMAL(10,2)) 
AS Avg_Pizzas_per_order 
FROM pizza_sales;

## Sales Trends

## Daily Sales Trends: The number of orders placed on each day of the week.

SQL Query:
sql
Copy code
SELECT DATENAME(DW, order_date) AS order_day, COUNT(DISTINCT order_id) AS total_orders  
FROM pizza_sales 
GROUP BY DATENAME(DW, order_date);
Monthly Sales Trends: The number of orders placed each month.

## SQL Query:

+ Copy code
+ SELECT DATENAME(MONTH, order_date) as Month_Name, COUNT(DISTINCT order_id) as Total_Orders 
FROM pizza_sales 
GROUP BY DATENAME(MONTH, order_date);

## Sales by Category and Size

## Sales by Pizza Category: Percentage of sales contributed by each pizza category.

## SQL Query:

+ Copy code
+ SELECT pizza_category, CAST(SUM(total_price) AS DECIMAL(10,2)) as total_revenue, 
CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) from pizza_sales) AS DECIMAL(10,2)) AS PCT 
FROM pizza_sales 
GROUP BY pizza_category;

## Sales by Pizza Size: Percentage of sales based on pizza size.

## SQL Query:

+Copy code
+SELECT pizza_size, CAST(SUM(total_price) AS DECIMAL(10,2)) as total_revenue, 
CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) from pizza_sales) AS DECIMAL(10,2)) AS PCT 
FROM pizza_sales 
GROUP BY pizza_size;

## Top and Bottom Performers

## Top 5 Pizzas by Revenue: The top 5 pizzas that generated the most revenue.

## SQL Query:

+ Copy code
+ SELECT Top 5 pizza_name, SUM(total_price) AS Total_Revenue 
FROM pizza_sales 
GROUP BY pizza_name 
ORDER BY Total_Revenue DESC;

## Bottom 5 Pizzas by Revenue: The pizzas with the lowest revenue.

## SQL Query:

+ Copy code
+ SELECT TOP 5 pizza_name, SUM(total_price) AS Total_Revenue 
FROM pizza_sales 
GROUP BY pizza_name 
ORDER BY Total_Revenue ASC;

## Top 5 Pizzas by Quantity Sold: The pizzas that sold the most in terms of quantity.

## SQL Query:

+ Copy code
+ SELECT Top 5 pizza_name, SUM(quantity) AS Total_Pizza_Sold 
FROM pizza_sales 
GROUP BY pizza_name 
ORDER BY Total_Pizza_Sold DESC;

## Bottom 5 Pizzas by Quantity Sold: The pizzas that sold the least.

## SQL Query:

+ Copy code
+ SELECT TOP 5 pizza_name, SUM(quantity) AS Total_Pizza_Sold 
FROM pizza_sales 
GROUP BY pizza_name 
ORDER BY Total_Pizza_Sold ASC;

# Power BI Dashboard

A comprehensive Power BI dashboard was created to visualize the insights from the SQL analysis. Key visualizations include:

## Daily and monthly sales trends.

+ Percentage of sales by pizza category and size.
+ Top and bottom 5 pizzas by revenue and quantity sold.
+ Key metrics like total revenue, average order value, and total pizzas sold.
  
# Installation and Setup

## Clone the repository:

+ bash
+ Copy code
+ git clone https://github.com/your-username/pizza-sales-analysis.git
  
## Set up the SQL database:

+ Import the SQL script PIZZA SALES ANALYSIS SQL QUERIES.sql into your SQL database to run the queries.
  
# Power BI Dashboard:

+ Load the dataset and the results from the SQL queries into Power BI.
+ Use the provided Power BI file (pizza_sales_dashboard.pbix) to explore the visualized results.
  
# Key Insights

+ The highest revenue-generating pizzas and categories can guide marketing and inventory decisions.
+ Certain pizzas consistently rank low in both revenue and sales, which could suggest the need for discontinuation or targeted promotions.
+ Sales trends by day and month provide insights for planning promotions and staffing.

# Power bi Output
 ![Image Alt](image_url).
 ![Image Alt](image_url). 
# Recommendations

+ Optimize Menu Offerings: Based on the top and bottom-performing pizzas, adjust the menu to focus on high-revenue items.
+ Targeted Promotions: Use the data on customer preferences and sales trends to offer targeted discounts and promotions on slower-selling pizzas or during low-sales periods.
+ Inventory Management: Align inventory with the sales trends and pizza categories that are performing well.
