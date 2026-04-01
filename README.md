# Olist E-Commerce Sales & Logistics Dashboard

## Project Overview

This Power BI dashboard provides a comprehensive analysis of the Olist E-commerce marketplace, a Brazilian platform connecting small businesses to customers. The project analyzes a dataset of 100,000+ orders placed between 2016 and 2018.

The dashboard is designed to help stakeholders monitor sales performance, optimize logistics, and understand customer behavior. It highlights key performance indicators (KPIs), seasonal trends, payment preferences, and delivery efficiency.

The project demonstrates skills in:
- Data Modeling (Star Schema design)
- Power Query (ETL & Data Cleaning)
- DAX (Complex measures & calculated columns)
- Data Visualization (Interactive charts & maps)
- UI/UX Design (Navigation & Bookmarks)

## Dashboard Preview

### Home Page
The landing page provides a high-level summary of the entire business, showing Total Revenue, Total Orders, and the overall Delivery Status.
![Home Page Screenshot](https://github.com/AnveshDhamane/Olist-Store-Analysis-Power-BI/blob/eba3ca089a2471e6618c7dd7f8968f04a354592d/Screenshots/image.png)

---

## Navigation & Analysis Views

The dashboard features a navigation menu in the **bottom-left corner** with four distinct buttons, allowing users to drill down into specific analytical areas.

### 1. Payment vs Price Report
**Focus:** Financial reconciliation and revenue breakdown.
**Description:** This report compares the **Total Payment Value** (Gross Revenue including freight) against the **Total Product Price** (Net Sales). It identifies which payment methods are most popular and which states contribute the most to revenue.
* **Key Visuals:**
    * *Payment Value by Payment Type* (Donut Chart) - Highlights the dominance of Credit Cards.
    * *Price by Category* (Bar Chart) - Shows top revenue-generating categories like 'Bed Bath & Table'.
    * *Payment Value by State* - Visualizes revenue concentration in São Paulo (SP).
![Payment Report Screenshot](https://github.com/AnveshDhamane/Olist-Store-Analysis-Power-BI/blob/1323aaa70acb219ca94e0e89e1dd49e531c6ac99/Payment%20vs%20Price%20Report%20Screenshot.png)

### 2. Avg Shipping Days Report
**Focus:** Logistics efficiency and Customer Satisfaction.
**Description:** This detailed logistics report analyzes the time taken for deliveries and its direct correlation with customer review scores. It includes category-level filtering (e.g., **Pet Shop**) to identify specific product lines facing shipping bottlenecks.
* **Key Visuals:**
    * *Avg Shipping Days by Review Score:* Demonstrates the correlation between faster shipping and higher ratings (5-star reviews typically have the shortest delivery times).
    * *Shipping Days by State:* Identifies regions with logistical challenges (e.g., North/Northeast states).
![Avg Days Report Screenshot](https://github.com/AnveshDhamane/Olist-Store-Analysis-Power-BI/blob/1323aaa70acb219ca94e0e89e1dd49e531c6ac99/Avg%20Shipping%20Days%20Report%20screenshot.png)

### 3. No. of Orders (Review Score 5)
**Focus:** Drivers of Customer Loyalty & Satisfaction.
**Description:** This view filters the dataset to analyze exclusively **5-star rated orders**. By isolating the "perfect" transactions, we can understand the characteristics of successful sales—such as optimal delivery times, popular product categories, and top-performing regions.
* **Key Visuals:**
    * *Monthly Trend of 5-Star Orders:* Tracks the volume of highly satisfied customers over time.
    * *Top Categories for 5-Star Reviews:* Shows which products (e.g., Health & Beauty) consistently delight customers.
    * *Geographic Heatmap:* Maps where the happiest customers are located.
![Review Score 5 Screenshot](https://github.com/AnveshDhamane/Olist-Store-Analysis-Power-BI/blob/1323aaa70acb219ca94e0e89e1dd49e531c6ac99/No.%20of%20Orders%20(Review%20Score%205)%20screenshot.png)

### 4. Geographical Analysis
**Focus:** Regional Market Penetration & Strategy.
**Description:** This page visualizes the spatial distribution of customers and sales across Brazil. It is essential for identifying the "powerhouse" states (like São Paulo and Rio de Janeiro) and spotting under-served regions for potential marketing expansion.
* **Key Visuals:**
    * *Total Payment by State (Map):* A geospatial view showing revenue density.
    * *State-wise Performance:* Detailed breakdown of order volumes per state (SP, RJ, MG, etc.).
    * *City-level Granularity:* Analysis of top performing cities within the major states.
![Geographical Analysis Screenshot](https://github.com/AnveshDhamane/Olist-Store-Analysis-Power-BI/blob/1323aaa70acb219ca94e0e89e1dd49e531c6ac99/Geographical%20Analysis%20screenshot.png)

---

## Data Modeling

The data model follows a **Star Schema** architecture to optimize performance and simplify DAX calculations.

- **Fact Table:** `Order_Items` (Contains transactional data like Price, Freight, and Quantity).
- **Dimension Tables:** `Customers`, `Products`, `Sellers`, `Payments`, `Reviews`, and `Date` (Calendar).

![Data Model Screenshot](https://github.com/AnveshDhamane/Olist-Store-Analysis-Power-BI/blob/4d479c629ca1d5d62763e3f02b0d883abe1db3b2/Data%20Model.png)

### Model Details:
- **Relationships:** One-to-Many relationships are established between Dimension tables and the Fact table.
- **Star Schema:** The `Order_Items` table acts as the central fact table, connected to `Products`, `Sellers`, and `Orders`.
- **Snowflake Schema:** Used for the `Product_Category_Translation` table, which filters the `Products` table to provide English category names.
- **Date Table:** A dedicated Date table was created using DAX to handle time-intelligence functions accurately.

## Features

### 1. Key KPIs
- Total Revenue: Global sales volume over the selected period.
- Total Orders: Count of unique orders placed.
- Average Order Value (AOV): Revenue per transaction.
- Average Delivery Days: Time taken from order approval to customer delivery.
- Freight Ratio: Percentage of total cost attributed to shipping.

### 2. Visual Insights
- Sales Trends: Monthly and yearly revenue tracking (identifying Seasonality/Black Friday).
- Geographic Distribution: Heatmap of sales by State and City.
- Category Performance: Top 10 product categories by revenue and volume.
- Payment Analysis: Breakdown of payment methods (Credit Card, Boleto, Voucher).

### 3. Interactive Filters
- Navigation Buttons: Switch between "Sales," "Logistics," and "Customer" views.
- Date Slicer: Filter by Year, Quarter, and Month.
- Region Filter: Drill down by State (UF) or City.

## Tools Used

- Microsoft Power BI Desktop: Dashboarding and visualization.
- Power Query: Merging 9 distinct datasets and handling null values.
- DAX (Data Analysis Expressions): Creating measures for time-intelligence and ratios.
- Excel/CSV: Source data format.

## Dataset Description

The dataset consists of 9 relational CSV files provided by Olist. It covers the entire order journey: from purchase to payment, shipping, and customer review.

## Data Dictionary

| Table Name | Description |
|:---|:---|
| olist_orders_dataset | Core table containing Order ID, status, timestamps (purchase, approval, delivery). |
| olist_order_items_dataset | Details of items within an order (Product ID, Price, Freight Value, Seller ID). |
| olist_products_dataset | Product metadata including category name, weight, and dimensions. |
| olist_customers_dataset | Customer demographic info (City, State, Zip Code). |
| olist_order_payments_dataset | Payment details (Method: Credit Card/Voucher, Installments, Transaction Value). |
| olist_order_reviews_dataset | Customer satisfaction data (Review Score 1-5, Comments). |
| olist_sellers_dataset | Seller location and ID information. |
| olist_geolocation_dataset | Latitude and Longitude coordinates for mapping customers and sellers. |
| product_category_translation | Translations of category names from Portuguese to English. |

## DAX Measures & Calculations

This project uses advanced DAX (Data Analysis Expressions) to create dynamic measures and field parameters. Below is the documentation for the core calculations used in the dashboard.

### 1. Key Performance Indicators (KPIs)

These measures calculate the core business metrics shown on the top-level cards.

**Total Payment (Gross Revenue)**
* **Code:**
    ```dax
         Total payment = CALCULATE(SUM(olist_order_payments_dataset[payment_value]))
    ```
* **What it tells:** The total monetary value captured by the platform (includes product price + freight).
* **Used in:** Home Page KPI Cards.

**Total Product Price (Net Sales)**
* **Code:**
    ```dax
        Total price = CALCULATE(SUM(olist_order_items_dataset[price]))
    ```
* **What it tells:** The total revenue generated strictly from product sales (excluding freight).
* **Used in:** Financial analysis views to separate logistics revenue from product revenue.

**Average Payment**
* **Code:**
    ```dax
         AVERAGE PAYMENT = CALCULATE(AVERAGE(olist_order_payments_dataset[payment_value]))
    ```
* **What it tells:** The average transaction value per order. High values indicate customers buying expensive items or multiple items at once.

**Average Price**
* **Code:**
    ```dax
          AVERAGE PRICE = CALCULATE(AVERAGE(olist_order_items_dataset[price]))
    ```
* **What it tells:** The average cost of a single item sold on the platform.

### 2. Advanced Analysis Measures

**Shipping Efficiency vs. Satisfaction**
* **Code:**
    ```dax
    Avg shipping days by score =
    ROUNDUP(
        AVERAGEX(
            VALUES(olist_order_reviews_dataset[review_score]),
            CALCULATE(AVERAGE(olist_orders_dataset[Days taken]))
        ),
        0
    )
    ```
* **What it tells:** Calculates the average number of delivery days for each review score (1-5 stars).
* **Insight:** This measure is crucial for proving the correlation that **faster shipping leads to higher review scores**.
* **Used in:** "Logistics" view, likely in a Bar Chart comparing Delivery Days by Review Score.

### 3. Dynamic Field Parameters

These tables allow the dashboard user to toggle between different metrics on a single chart using a slicer.

**Metric Switcher (Totals)**
* **Code:**
    ```dax
    Parameter = {
        ("Total payment", NAMEOF('olist_customers_dataset'[Total payment]), 0),
        ("Total price", NAMEOF('olist_customers_dataset'[Total price]), 1)
    }
    ```
* **Usage:** Used in trend charts (e.g., "Revenue by Month") to allow users to switch between viewing **Total Revenue** vs. **Product Sales**.

**Metric Switcher (Averages)**
* **Code:**
    ```dax
    AVG parameter = {
        ("AVERAGE PAYMENT", NAMEOF('Parameter'[AVERAGE PAYMENT]), 0),
        ("AVERAGE PRICE", NAMEOF('Parameter'[AVERAGE PRICE]), 1)
    }
    ```
* **Usage:** Used in charts analyzing ticket size to compare **Order Value** vs. **Item Price**.

**Comprehensive Metric Selector**
* **Code:**
    ```dax
    Parameter 3 = {
        ("Total Payment", NAMEOF('olist_customers_dataset'[Total payment]), 0),
        ("Average Payment", NAMEOF('Parameter'[AVERAGE PAYMENT]), 1),
        ("Total Price", NAMEOF('olist_customers_dataset'[Total price]), 2),
        ("Average Price", NAMEOF('Parameter'[AVERAGE PRICE]), 3)
    }
    ```
* **Usage:** Used in the "Grid" or "Deep Dive" views where the user needs full control to swap any metric into the X or Y axis of a chart. *


## Key Insights

### 1. Geographic Concentration
The Southeast region (especially Sao Paulo) accounts for the vast majority of orders and revenue, indicating a need for logistics optimization in other regions.

### 2. Seasonality & Peaks
There is a significant spike in sales during Black Friday (November), requiring scaled-up inventory and server capacity during Q4.

### 3. Delivery Efficiency
While most orders arrive on time, there is a visible gap between Estimated Delivery Date and Actual Delivery Date in northern states, often leading to lower review scores.

### 4. Payment Preferences
Credit Cards are the dominant payment method, with a high usage of installments (Parcelado), suggesting customers prefer spreading costs for higher-value items.

## Recommendations

### 1. Logistics Optimization
Establish warehousing partnerships in the North/Northeast regions to reduce delivery times and freight costs.

### 2. Inventory Planning
Sellers should use the seasonality data to stock up heavily on "Bed & Bath" and "Decor" items specifically for the Q4 Black Friday rush.

### 3. Payment Incentives
Since Credit Card installments are popular, offer interest-free installment promotions to increase the Average Order Value (AOV).


