# Walmart Sales Data Analysis

## Overview

This project analyzes Walmart sales data to identify top-performing branches and products, sales trends, and customer behavior. The dataset is from the [Kaggle Walmart Sales Forecasting Competition](https://www.kaggle.com/c/walmart-recruiting-store-sales-forecasting).

## Dataset

The data contains sales transactions from Walmart branches in Mandalay, Yangon, and Naypyitaw. It includes 17 columns and 1000 rows.

| Column                  | Description                             |
| ----------------------- | --------------------------------------- |
| invoice_id              | Invoice of the sales made               |
| branch                  | Branch at which sales were made         |
| city                    | The location of the branch              |
| customer_type           | The type of the customer                |
| gender                  | Gender of the customer making purchase  |
| product_line            | Product line of the product sold        |
| unit_price              | The price of each product               |
| quantity                | The amount of the product sold          |
| VAT                     | The amount of tax on the purchase       |
| total                   | The total cost of the purchase          |
| date                    | The date on which the purchase was made |
| time                    | The time at which the purchase was made |
| payment_method          | The payment method used                 |
| cogs                    | Cost of Goods Sold                      |
| gross_margin_percentage | Gross margin percentage                 |
| gross_income            | Gross income                            |
| rating                  | Rating given by the customer            |

## Analysis

1. **Product Analysis**

   - Identify top and underperforming product lines.

2. **Sales Analysis**

   - Examine sales trends and measure the effectiveness of sales strategies.

3. **Customer Analysis**
   - Understand customer segments, purchase trends, and profitability.

## Approach

1. **Data Wrangling**

   - Handle missing values and clean data.

2. **Feature Engineering**

   - Add columns for time of day, day of the week, and month to analyze sales patterns.

3. **Exploratory Data Analysis (EDA)**
   - Answer business questions and derive insights from the data.

## Business Questions

### General

1. How many unique cities are in the data?
2. In which city is each branch located?

### Product

1. How many unique product lines are there?
2. What is the most common payment method?
3. Which product line has the highest revenue?
4. Which city has the largest revenue?

### Sales

1. Number of sales made at different times of the day.
2. Which customer type generates the most revenue?
3. Which city has the highest VAT percentage?
4. Which customer type pays the most in VAT?

### Customer

1. How many unique customer types and payment methods are there?
2. What is the most common customer type?
3. Which gender is most common among customers?

## Calculations

### Formulas

- **COGS:** `unitsPrice * quantity`
- **VAT:** `5% * COGS`
- **Total (gross sales):** `VAT + COGS`
- **Gross Profit:** `total - COGS`
- **Gross Margin:** `(gross profit / total revenue) * 100`

### Example Calculation

- **Unit Price:** 45.79
- **Quantity:** 7
- **COGS:** 45.79 \* 7 = 320.53
- **VAT:** 5% \* 320.53 = 16.0265
- **Total:** 336.5565
- **Gross Margin Percentage:** 4.7619%

## SQL Code

For detailed SQL queries, see the [SQL_queries.sql](https://github.com/Princekrampah/WalmartSalesAnalysis/blob/master/SQL_queries.sql) file.

```sql
-- Create database
CREATE DATABASE IF NOT EXISTS walmartSales;

-- Create table
CREATE TABLE IF NOT EXISTS sales(
	invoice_id VARCHAR(30) NOT NULL PRIMARY KEY,
    branch VARCHAR(5) NOT NULL,
    city VARCHAR(30) NOT NULL,
    customer_type VARCHAR(30) NOT NULL,
    gender VARCHAR(30) NOT NULL,
    product_line VARCHAR(100) NOT NULL,
    unit_price DECIMAL(10,2) NOT NULL,
    quantity INT NOT NULL,
    tax_pct FLOAT(6,4) NOT NULL,
    total DECIMAL(12, 4) NOT NULL,
    date DATETIME NOT NULL,
    time TIME NOT NULL,
    payment VARCHAR(15) NOT NULL,
    cogs DECIMAL(10,2) NOT NULL,
    gross_margin_pct FLOAT(11,9),
    gross_income DECIMAL(12, 4),
    rating FLOAT(2, 1)
);
```
