# Retail Sales & Customer Analytics

An end-to-end retail analytics project using Python, SQL, and Power BI to understand sales performance, customer behaviour, and opportunities for business growth.

The project uses the UCI Online Retail II dataset, covering transactions from December 2009 to December 2011. Starting with raw Excel data, I worked through data cleaning, exploratory analysis, customer segmentation, forecasting, and dashboard development to turn transaction-level data into business insights.

## Project at a Glance

| Category | Details |
|---|---|
| Dataset | UCI Online Retail II |
| Raw data | Approximately 1.07 million invoice records |
| Cleaned data | Approximately 824K transactions |
| Customers | 5,878 |
| Countries | 38 |
| Analysis period | December 2009 – December 2011 |
| Tools | Python, Pandas, PostgreSQL, Scikit-learn, Power BI |
| Key techniques | RFM analysis, K-Means clustering, cohort analysis, revenue forecasting |
| Deliverables | SQL queries, Python notebooks, visualisations, customer segments, Power BI dashboard |

**Key takeaway:** The analysis identified potential revenue recovery opportunities exceeding £400K through customer retention and win-back scenarios. These are estimated opportunities, not revenue already generated.

---

## 1. Project Overview

Retail businesses collect large amounts of transaction data, but understanding what is happening behind the sales figures is often the bigger challenge.

For this project, I worked with two years of transaction data from a UK-based online gift retailer. The objective was to explore the data from different angles and answer questions that could help a business make better decisions.

Rather than focusing only on total revenue, I wanted to understand:

- Which products and markets contribute the most to sales?
- Which customers bring the most value to the business?
- Which customers have stopped purchasing and may need attention?
- How do purchasing patterns change across months, weekdays, and hours?
- How well does the business retain newly acquired customers?
- What can historical sales trends tell us about future revenue?

To investigate these questions, I developed a multi-stage analytics workflow covering data preparation, SQL analysis, Python-based visualisation, machine learning, forecasting, and Power BI reporting.

## 2. Project Workflow

The project is organised into four main stages.

### Stage 1 – Data Cleaning and Feature Engineering

**Tools:** Python, Pandas, NumPy

The original dataset contained over one million invoice records, including cancellations, missing customer information, duplicate transactions, and invalid quantities or prices.

I used Pandas to clean the data and prepare it for analysis.

Key tasks included:

- Standardising column names and data formats.
- Handling missing customer IDs and invalid dates.
- Removing cancellation invoices and duplicate records.
- Filtering out non-positive quantities and prices.
- Creating transaction-level revenue and additional date-related features.
- Building a customer-level summary using Recency, Frequency, and Monetary (RFM) metrics.

The cleaning process also maintains an audit log so that the changes made to the original dataset can be reviewed.

**Output:** Cleaned transaction data and customer summary files.

### Stage 2 – SQL Business Analysis

**Tool:** PostgreSQL

After preparing the data, I loaded it into PostgreSQL to explore business questions using SQL.

I wrote 25 queries using joins, CTEs, aggregations, window functions, and ranking techniques.

The analysis focused on:

- Monthly and quarterly revenue trends.
- Best-performing products and countries.
- Customer purchasing frequency and spending patterns.
- Identification of inactive and high-value customers.
- Customer retention and repeat purchases.
- Product performance and revenue contribution.

This stage helped me move beyond basic SQL aggregations and work with more practical analytical problems.

**Output:** 17 annotated SQL queries and business findings.

### Stage 3 – Exploratory and Advanced Analytics

**Tools:** Python, Pandas, Matplotlib, Seaborn, Scikit-learn, NumPy

I used Python to explore sales patterns, understand customer behaviour, and identify trends that were not immediately visible in the raw data.

The analysis was divided into three parts.

**Exploratory Data Analysis**

- Monthly and quarterly revenue trends.
- Top-performing products.
- Revenue contribution by country.
- Weekly and hourly purchasing patterns.
- Distribution of RFM customer segments.
- Relationship between customer lifetime revenue and purchase frequency.
- New versus repeat customer analysis.

**Customer Segmentation**

I applied two approaches to understand customer value:

1. RFM scoring to classify customers based on purchasing recency, frequency, and monetary value.
2. K-Means clustering using customer recency, total orders, and total revenue.

I used the Elbow Method and Silhouette Score to evaluate the clustering structure before selecting four customer groups.

**Revenue Forecasting and Cohort Analysis**

- Used a three-month rolling average and an OLS linear trend to forecast revenue for the next three months.
- Calculated customer retention across acquisition cohorts.
- Built a cohort retention heatmap to understand how customer activity changed after the first purchase.

**Output:** EDA charts, revenue forecasts, customer clusters, and cohort retention analysis.

### Stage 4 – Power BI Dashboard

**Tool:** Power BI Desktop

The final stage was to bring the major business metrics and findings together in an interactive dashboard.

The dashboard includes:

- Revenue and order-related KPIs.
- Customer and average order value metrics.
- Revenue trends over time.
- Customer segment breakdowns.
- Product and geographic performance.

I included slicers for Year, Quarter, and Country so that users can explore the results without having to work directly with the underlying data.

The intention was to make the analysis accessible to someone who may not have a technical background.

---

## 3. Dashboard Preview

The dashboard was developed in Power BI Desktop.

### Overall Dashboard

![Dashboard Overview](dashboard/dashboard_overview.png)

### KPI Summary

Revenue, Orders, Customers, and Average Order Value.

![KPI Section](dashboard/kpi_section.png)

### Revenue Trends and Customer Segments

![Revenue Chart](dashboard/revenue_trend_chart.png)

The Power BI file is available at `dashboard/retail_dashboard.pbix`.

---

## 4. Key Business Questions

Throughout the project, I focused on questions that could help a retail business understand its performance and identify areas for improvement.

1. How much of the total revenue comes from the highest-spending customers?
2. Which customers have not purchased recently, and how much lifetime revenue have they contributed?
3. Which months and quarters consistently generate the highest revenue?
4. Which products contribute most to overall sales?
5. Which international markets show potential for further growth?
6. On which days and at what times are customers most active?
7. How many customers return after their first purchase?
8. What does customer retention look like across different acquisition cohorts?
9. Can historical revenue patterns provide a reasonable baseline for future planning?

These questions guided the SQL queries, Python analysis, and dashboard design.

---

## 5. Key Findings and Business Recommendations

The following findings are based on the project's analysis. Financial opportunities and potential improvements are estimates based on the assumptions described, not confirmed business outcomes.

### 1. A significant share of revenue comes from a relatively small customer group

**Finding:** The top 20% of customers account for approximately 71.4% of total revenue.

**Why it matters:** Losing even a small number of high-value customers could have a noticeable impact on overall sales.

**Recommendation:** Introduce a tiered loyalty programme with benefits such as exclusive offers, early access to new products, and incentives for repeat purchases.

### 2. A group of previously valuable customers is no longer purchasing regularly

**Finding:** 892 customers were classified as At Risk based on 90–180 days of inactivity. Their combined lifetime revenue is approximately £1.2 million.

**Why it matters:** These customers have already demonstrated purchasing interest, making them potential candidates for re-engagement.

**Recommendation:** Run a targeted win-back campaign with personalised offers and follow-up communication. At an assumed 20% conversion rate, the scenario indicates approximately £240K in potential revenue recovery.

### 3. The Netherlands shows strong year-on-year growth

**Finding:** Revenue from the Netherlands increased by approximately 61% year over year, reaching around £285K.

**Why it matters:** This market could offer room for expansion beyond the retailer's established UK business.

**Recommendation:** Investigate local customer preferences, test market-specific promotions, and evaluate whether additional sales support is justified.

### 4. A portion of the product catalogue has limited repeat demand

**Finding:** 847 SKUs recorded no repeat purchases during the two-year analysis period.

**Why it matters:** Products with consistently low repeat demand may require additional storage and inventory management without contributing proportionately to sales.

**Recommendation:** Review these products individually before considering discontinuation. A potential range-rationalisation exercise could improve inventory efficiency.

### 5. Purchasing activity varies by day and time

**Finding:** Thursday, particularly between 10:00 and 14:00, was identified as a strong trading window. Average order value during this period was approximately 12% higher than the daily average.

**Why it matters:** Understanding when customers are most active can help businesses plan marketing communication and promotional campaigns.

**Recommendation:** Test different email campaign timings around high-activity periods and compare engagement and conversion results before changing the overall campaign schedule.

### 6. Customer retention drops after the first purchase

**Finding:** Month-2 customer retention was below 35% across the analysed cohorts.

**Why it matters:** Acquiring new customers without encouraging repeat purchases can make long-term growth difficult to sustain.

**Recommendation:** Introduce post-purchase communication, such as personalised follow-ups around Day 7 and Day 30, and monitor whether these interventions improve repeat purchasing.

---

## 6. Business Impact Scenarios

The findings can be translated into potential business actions.

| Finding | Potential opportunity or action |
|---|---|
| 892 At-Risk customers with £1.2M lifetime revenue | A 20% reactivation scenario implies approximately £240K in potential recovery |
| Top 20% of customers contribute 71.4% of revenue | Prioritise retention of high-value customers |
| Netherlands revenue grew by 61% YoY | Evaluate additional support for this market |
| 847 SKUs have no repeat purchases | Review inventory allocation and product range |
| High-activity trading window on Thursday | Test more effective marketing schedules |
| Month-2 retention below 35% | Improve post-purchase engagement |

These figures should be treated as analytical estimates and recommendations. Implementing them would require further testing and validation against actual business performance.

---

## 7. Tools and Technologies

| Area | Technology | Application |
|---|---|---|
| Data Cleaning | Python, Pandas, NumPy | Cleaning, transformation, and feature engineering |
| SQL Analysis | PostgreSQL | Business queries, joins, CTEs, and window functions |
| Visualisation | Matplotlib, Seaborn | Sales trends and customer behaviour analysis |
| Machine Learning | Scikit-learn | K-Means customer clustering |
| Forecasting | NumPy | Linear trend-based revenue forecasting |
| Dashboarding | Power BI | Interactive business reporting |
| Notebooks | Jupyter Notebook | Organising and executing analytical workflows |
| Version Control | Git, GitHub | Project management and version history |

---

## 8. Dataset Information

The project uses the **UCI Online Retail II** dataset.

| Property | Details |
|---|---|
| Dataset | Online Retail II |
| Source | [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/502/online+retail+ii) |
| Period | December 2009 – December 2011 |
| Original records | Approximately 1,067,371 invoice lines |
| Cleaned records | Approximately 824,000 transactions |
| Countries | 38 |
| Unique customers | 5,878 |
| Unique SKUs | Approximately 4,000 |

The dataset contains transaction-level information such as invoice number, product description, quantity, invoice date, unit price, customer ID, and country.

The raw Excel file is not included in the repository because of its size. Download instructions are available in `Data/README.md`.

---


## 9. What I Learned

Working through this project helped me understand how different parts of a data analytics workflow fit together.

**Data cleaning and preparation:** I learned that cleaning transaction data involves more than removing missing values. Each decision needs to be considered in the context of the business question being analysed.

**SQL for business analysis:** Working with PostgreSQL helped me practise CTEs, window functions, ranking, date-based aggregations, and customer-level analysis on a relatively large dataset.

**Customer analytics:** Implementing RFM scoring and K-Means clustering helped me understand how transaction history can be used to group customers with different purchasing behaviours.

**Time-based analysis:** Revenue forecasting and cohort analysis gave me a better understanding of how historical trends and customer retention can be studied over time.

**Data visualisation:** I learned to choose visuals based on the question being answered rather than simply presenting as many charts as possible.

**Communicating business insights:** One of the biggest lessons was that identifying a trend is only the first step. Explaining why it matters and what a business could do next makes the analysis more useful.

---


**Original project reference:** [Retail Sales Analytics System](https://github.com/Manalkh16/Retail-Sales-Analytics-System)

