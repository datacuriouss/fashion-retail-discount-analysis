# 👗 Fashion Retail Discount Analysis

Analysis of discount effectiveness across a global fashion retailer operating 
in 7 countries and 35 stores — using Python for data cleaning, SQL for business 
analysis, and Power BI for interactive visualisation.

---

## 📌 Project Overview

This project investigates whether discounting actually drives more sales in 
fashion retail, or whether constant discounting has trained customers to buy 
regardless of whether a discount exists.

This question was inspired by my experience working in retail at Strandbags, 
where promotional sales were near-constant. I wanted to test with real data 
whether discounts genuinely move the needle on sales volume and revenue.

The analysis focuses on three core questions:

- Do discounted transactions generate more revenue than full price ones?
- Which discount levels, categories and months drive the most sales?
- Is discounting consistent across countries, or do some markets respond differently?

---

## 📊 Dashboard

👉 Power BI Dashboard (coming soon)

---

## 🔍 Key Findings

- **70.6% of transactions were at full price** — only 29.4% involved a discount
- **Discounting nearly halves revenue per transaction** — discounted transactions average 80.59 vs 147.35 for full price, yet average quantity purchased is identical at 1.1 items in both cases
- **The 20% discount drives the highest average sale value (117.29)** among all discount levels — while the most common discount (50%) generates only 75.30 per transaction
- **December is the most heavily discounted month** (34% avg discount in 2024) yet generates lower average sale values than zero-discount months like June (169.89)
- **Months with zero discounting consistently outperform discounted months** in average sale value — suggesting customers spend more at full price
- **Feminine products are discounted most aggressively** (43.91% avg discount) but Masculine products generate higher average sale values despite lower discounts
- **The pattern holds across all 7 countries** — discounting reduces revenue per transaction everywhere without driving higher purchase quantities

---

## 🗂️ Dataset

- **Source:** Kaggle — Global Fashion Retail Sales (ricgomes/global-fashion-retail-stores-dataset)
- **Period:** 2 years of synthetic transactional data
- **Size:** 6.4 million transactions across 35 stores in 7 countries
- **Key fields:** Transaction Type, Unit Price, Discount, Line Total, Product Category, Store Country, Payment Method

Note: Raw transaction data not included in this repo due to file size. 
Download from the Kaggle link above.

---

## 🔧 Data Cleaning & Preparation (Python)

| Step | What was done |
|------|--------------|
| Filter returns | Removed 339,627 return transactions — kept only Sales |
| Missing values | Dropped Color column (68% missing, not needed for analysis) |
| Data types | Converted Date from text to datetime for time-based analysis |
| Column names | Standardised all column names — removed spaces, fixed typo ('Discont' → 'Discount') |
| Irrelevant columns | Dropped Currency Symbol, SKU, Line, Employee ID, Size |
| Language columns | Kept only English product descriptions, dropped PT/DE/FR/ES/ZH |

---

## 📐 Features Engineered

Four new columns were created to support the SQL analysis:

- **Discount_Percentage** — discount converted from decimal to percentage (0.4 → 40)
- **Discounted** — True/False flag for whether a discount was applied
- **Year** — extracted from Date for time-based trend analysis
- **Month** — extracted from Date for seasonal analysis

---

## 🔎 SQL Analysis

7 business questions answered using SQLite (sqlite3 inside Python) and DBeaver:

| Query | Business Question |
|-------|------------------|
| Q1 | What % of transactions were discounted vs full price? |
| Q2 | Do discounted transactions have higher quantities? |
| Q3 | Which discount % drives the highest average sale value? |
| Q4 | Which product categories get discounted the most? |
| Q5 | Which months have the highest discount rates? |
| Q6 | Which countries generate the most revenue — discounted vs full price? |
| Q7 | Average revenue per transaction by category — discounted vs full price? |

---

## 🛠️ Tools Used

- **Python** (pandas, numpy) — data cleaning & feature engineering
- **SQL** (sqlite3, DBeaver) — business queries & analysis
- **Power BI** — interactive dashboard & visualisation (Currently in progress)
- **Google Colab** — development environment

---

## 📁 Repository Structure
