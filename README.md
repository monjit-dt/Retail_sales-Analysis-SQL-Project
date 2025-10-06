# 🛍️ Retail Sales Analysis SQL Project  

[![](https://i.postimg.cc/rpD2mxFj/retail.jpg)]

## 📌 Project Overview  
This project analyzes **retail sales data** using SQL to uncover insights on customer behavior, product performance, and sales trends.  
The goal was to clean raw transactional data, perform exploratory data analysis (EDA), and answer key business questions to simulate real-world data analytics work.  


## 📊 Dataset  
- **Source:** Simulated retail sales dataset (2021–2024)  
- **Files Included:**  
   - `retail Sales Analysis.csv` → Raw dataset used for import and testing
  -`cleaning_and_exploratory_analysis.sql` → Contains database creation, data cleaning, and analysis queries  
   

**Key Columns:**  
| Column | Description |
|--------|--------------|
| `transaction_id` | Unique transaction identifier |
| `sale_date` | Date of sale (YYYY-MM-DD) |
| `sale_time` | Time of transaction |
| `customer_id` | Unique customer ID |
| `gender` | Customer gender |
| `age` | Customer age |
| `category` | Product category (e.g., Clothing, Beauty, Electronics) |
| `quantity` | Number of items sold |
| `price_per_unit` | Selling price per unit |
| `cogs` | Cost of goods sold |
| `total_sale` | Total sale amount per transaction |



## 🧹 Data Cleaning Performed  
Data was carefully cleaned and validated before performing any analysis:  
- ✅ Removed rows with `NULL` values in key fields (`transaction_id`, `sale_date`, `category`, etc.)  
- ✅ Verified data types for numerical, date, and time fields  
- ✅ Checked for duplicates and inconsistent entries  
- ✅ Ensured valid category and gender values  

**Example cleaning snippet:**  

DELETE FROM retail_sales
WHERE 
    transaction_id IS NULL
    OR sale_date IS NULL
    OR sale_time IS NULL
    OR gender IS NULL
    OR category IS NULL
    OR quantity IS NULL
    OR cogs IS NULL
    OR total_sale IS NULL;



🔎 Exploratory Data Analysis (EDA)

Key analytical questions solved using SQL:

How many total sales transactions are recorded?

How many unique customers purchased items?

What are the top product categories by total sales?

What is the average age of customers purchasing from specific categories (e.g., Beauty)?

Which transactions had total sales greater than 1000?

How do sales vary by gender and category?

What is the best-selling month each year?

Who are the top 5 customers by total spending?

How many unique customers purchased from each category?

What are the sales trends by time of day (Morning, Afternoon, Evening)?



💡 Example Insights

🛒 Clothing and Electronics were the most popular categories by sales volume.

👩 Female customers contributed slightly higher average sales in Beauty and Clothing categories.

📅 November and December were the best-performing months across years (holiday spike).

💰 Top 5 customers generated over 15% of total sales revenue.

🌞 Most transactions occurred during the Afternoon shift (12–17 hrs).



🧠 Sample Analysis Queries

🏆 Top 5 Customers by Total Sales

SELECT 
    customer_id,
    SUM(total_sale) AS total_sales
FROM retail_sales
GROUP BY customer_id
ORDER BY total_sales DESC
LIMIT 5;

🌙 Shift-Wise Order Analysis

WITH hourly_sale AS (
    SELECT *,
        CASE
            WHEN EXTRACT(HOUR FROM sale_time) < 12 THEN 'Morning'
            WHEN EXTRACT(HOUR FROM sale_time) BETWEEN 12 AND 17 THEN 'Afternoon'
            ELSE 'Evening'
        END AS shift
    FROM retail_sales
)
SELECT 
    shift,
    COUNT(*) AS total_orders
FROM hourly_sale
GROUP BY shift;



🛠 Tools Used

SQL for data cleaning and analysis

GitHub for documentation and version control

MySQL Workbench for executing and validating queries



🚀 Why This Project Matters

This project showcases:

Proficiency in SQL data cleaning, transformation, and analysis

Ability to derive actionable business insights from transactional datasets

Experience working with date, time, and categorical data

A deep understanding of real-world retail performance metrics such as revenue, quantity sold, and customer segmentation



🏁 Conclusion

The Retail Sales SQL Project highlights strong analytical thinking, practical SQL expertise, and a structured approach to solving business problems using data.
It reflects real-world data analyst tasks — cleaning messy data, exploring KPIs, and uncovering insights that drive business growth.
