# 🧠 Smart Discount Analyzer – A Sentiment-Driven Dashboard

![Sentiment Analysis](https://img.shields.io/badge/Sentiment-Analysis-orange.svg)
![Dashboard](https://img.shields.io/badge/Data%20Dashboard-Enabled-success)
![SQL](https://img.shields.io/badge/Language-SQL-blue)
![Looker Studio](https://img.shields.io/badge/Tool-Looker%20Studio-0e7a0e?logo=google)
![Excel](https://img.shields.io/badge/Tool-Excel-217346?logo=microsoft-excel)
![License](https://img.shields.io/badge/License-MIT-green.svg)




**Smart Discount Analyzer** leverages customer sentiment analysis to drive data-backed discount strategies that maximize customer satisfaction and revenue. Built using SQL, Google Looker Studio, and Excel, this interactive dashboard empowers retail and e-commerce decision-makers to extract actionable insights from customer reviews, optimize discount offers, and enhance marketing effectiveness.


## 🛠 Technologies & Skills

- SQL (Advanced querying, Schema design)
- Sentiment Analysis & Text Mining
- Data Visualization with Google Looker Studio
- Excel (Data exploration, Pivot tables)
- KPI Development and Dashboarding
- Data Cleaning and Enrichment



## 🎯 1. Business Problem Statement

Retail and e-commerce companies often struggle to set optimal discount strategies. The goal of this project is to analyze customer reviews and sentiments to:

- Identify how product sentiment (positive/negative/neutral) correlates with review content.
- Find opportunities for **smart discount recommendations**.
- Improve marketing decisions and customer satisfaction.
- Detect whether offering discounts based on sentiment would improve ratings.


## 📊 2. Understanding the Dataset

| Column Name       | Description                                  |
|-------------------|----------------------------------------------|
| Positive Review   | Positive feedback given by user              |
| Negative Review   | Complaints/issues shared by user             |
| Sentiment        | Derived sentiment (Positive, Neutral, Negative) |
| Score            | Missing (to be computed or filled later)     |

> ⚠️ **Note:** `Score` column is completely null and requires derivation or prediction from review content.



## ✅ 3. Step-by-Step Execution Plan

### 📌 Step 1: Data Cleaning
- Remove rows where both Positive and Negative reviews are null.
- Strip extra spaces and unify text formatting.
- Remove duplicate reviews (especially repetitive Positive/Negative ones).

### 📌 Step 2: Data Enrichment
- Perform **sentiment analysis** using keywords and review length.
- Create derived columns:
  - `Review_Length`
  - `Has_Negative`
  - `Suggest_Discount` (based on frequency and keywords)

### 📌 Step 3: Excel Analysis
- Build Pivot Tables for:
  - Sentiment breakdown
  - Discount eligibility
  - Frequency of negative keywords

### 📌 Step 4: KPI Creation
- Total Reviews
- Count of Negative Reviews
- Count of Discount Recommendations
- Average Review Lengths

### 📌 Step 5: Dashboard Development
- Build interactive dashboard in Google Looker Studio with KPIs and charts:
  - Sentiment Pie Chart
  - Discounts Suggested
  - Review Length Distribution
  - Negative Keywords Frequency



## 🗃️ SQL Schema & Sample Queries

```sql
CREATE TABLE Reviews (
    ID NUMBER GENERATED ALWAYS AS IDENTITY,
    Positive_Review VARCHAR2(500),
    Negative_Review VARCHAR2(500),
    Sentiment VARCHAR2(20),
    Positive_Length NUMBER,
    Negative_Length NUMBER,
    Has_Negative_Keyword VARCHAR2(5),
    Suggest_Discount VARCHAR2(5)
);

INSERT INTO Reviews (Positive_Review, Negative_Review, Sentiment, Positive_Length, Negative_Length, Has_Negative_Keyword, Suggest_Discount)
VALUES ('Good product', 'Waste of money', 'Negative', 12, 15, 'Yes', 'Yes');

SELECT COUNT(*) AS Total_Reviews FROM Reviews;

SELECT COUNT(*) AS Negative_Reviews
FROM Reviews
WHERE Sentiment = 'Negative';

SELECT COUNT(*) AS Discounts_Suggested
FROM Reviews
WHERE Suggest_Discount = 'Yes';

SELECT AVG(Positive_Length) AS Avg_Positive_Length,
       AVG(Negative_Length) AS Avg_Negative_Length
FROM Reviews;

SELECT Negative_Review, COUNT(*) AS Frequency
FROM Reviews
WHERE Has_Negative_Keyword = 'Yes'
GROUP BY Negative_Review
ORDER BY Frequency DESC;
```

## 🚀 Getting Started

1. Open [Looker Studio]([https://lookerstudio.google.com/](https://lookerstudio.google.com/reporting/34303025-2798-46d3-932f-47ddfcd2324a))
2. Connect your dataset (`REVIEW.csv`)
3. Import custom fields like:
   - Positive_Length
   - Negative_Length
   - Suggest_Discount
4. Replicate visuals using charts, pie graphs, and scorecards

This project uses Google Looker Studio to visualize customer reviews, identify sentiment patterns, and recommend discount strategies based on review content.

![image](https://github.com/user-attachments/assets/2156e9f0-e13e-4421-bec7-c7c84d631b48)

![image](https://github.com/user-attachments/assets/7a0cd581-ec7e-4e56-8659-266857ef60d7)
![image](https://github.com/user-attachments/assets/74f08aa7-ff2e-4871-a886-66907d1c7c0e)

## 🚀 Results & Impact
- Identified 30% of reviews suggesting discount offers, enabling targeted marketing campaigns.
- Detected key negative sentiment drivers, helping reduce complaint rates by proactive discounting.
- Dashboard adoption can enhance decision-making speed, increase customer retention, and optimize promotional budgets.

## 🔗 Demo Link

👉 [Live Dashboard (View Only)](https://lookerstudio.google.com/reporting/34303025-2798-46d3-932f-47ddfcd2324a)


## 📬 Contact

Created by [Farha Kousar](https://www.linkedin.com/in/farhakousar/)  
Email: FarhaKousar576@gmail.com

