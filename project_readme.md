# 📊 Customer Shopping Behavior Analysis

An end-to-end data analytics project uncovering customer spending habits, subscription economics, category trends, and retention opportunities across 3,900 retail transactions.

## 📌 Table of Contents

* [Project Overview](#-project-overview)

* [Key Insights & Findings](#-key-insights--findings)

* [Tech Stack & Architecture](#-tech-stack--architecture)

* [Dataset Summary](#-dataset-summary)

* [Data Pipeline & Workflow](#-data-pipeline--workflow)

* [SQL Analysis & Business Questions](#-sql-analysis--business-questions)

* [Power BI Dashboard](#-power-bi-dashboard)

* [Strategic Recommendations](#-strategic-recommendations)

* [Project Structure](#-project-structure)

* [Getting Started](#-getting-started)

## 🎯 Project Overview

This project simulates a real-world commercial analytics workflow. By examining retail transaction logs spanning demographic data, purchasing patterns, discount usage, and customer reviews, the analysis uncovers friction points in subscription economics and recommends strategies to optimize customer lifetime value (CLV) and product merchandising.

## 💡 Key Insights & Findings

1. **Demographic Disparity:**

   * Male shoppers generated **67.7% (\$157,890)** of total revenue compared to **32.3% (\$75,191)** from female shoppers, driven primarily by higher transaction counts (2,652 vs. 1,248).

2. **The Subscription Paradox:**

   * Subscribers average **\$59.49** per purchase while non-subscribers average **\$59.87**. Subscription status currently acts as an engagement badge rather than driving higher basket value.

3. **Repeat Purchase Opportunity:**

   * Over **2,518 repeat buyers (>5 purchases) are not subscribed**, representing an immediate, high-intent pool for membership conversion.

4. **Discount Vulnerability:**

   * Key categories (notably Hats at **50.0%** and Sneakers at **49.7%**) rely heavily on promotions to convert, presenting margin risk.

5. **Customer Base Health:**

   * **79.9% (3,116 customers)** are classified as *Loyal*, while new customer acquisition represents only **2.1% (83 customers)**.

## 🛠 Tech Stack & Architecture

* **Language:** Python 3.x

* **Libraries:** `pandas`, `numpy`, `psycopg2` / `sqlalchemy`

* **Database:** PostgreSQL (transactional queries, CTEs, window functions)

* **Visualization & BI:** Microsoft Power BI (interactive dashboard, DAX measures)

* **Environment:** Jupyter Notebook / Python Scripts

## 📋 Dataset Summary

* **Records:** 3,900 purchases

* **Columns:** 18 attributes

* **Key Dimensions:**

  * *Customer Profile:* `Age`, `Gender`, `Location`, `Subscription Status`

  * *Purchase Metrics:* `Item Purchased`, `Category`, `Purchase Amount (USD)`, `Season`, `Size`, `Color`

  * *Behavioral Indicators:* `Discount Applied`, `Promo Code Used`, `Previous Purchases`, `Frequency of Purchases`, `Review Rating`, `Shipping Type`

## 🔄 Data Pipeline & Workflow

1. **Data Cleaning & Preprocessing (Python):**

   * Assessed schema and null counts using `df.info()` and `df.describe()`.

   * Imputed 37 missing values in `Review Rating` using the category-level median to preserve category integrity without introducing distribution distortion.

   * Standardized table headers to lowercase `snake_case`.

   * Identified 100% collinearity between `discount_applied` and `promo_code_used`; redundant columns dropped.

2. **Feature Engineering:**

   * Created age cohorts (`Young Adult`, `Middle-aged`, `Adult`, `Senior`).

   * Derived standardized purchase velocity metrics (`purchase_frequency_days`).

3. **Database Integration:**

   * Established automated connection via SQLAlchemy/Psycopg2 to load cleaned data into a PostgreSQL warehouse for transactional analysis.

## 🔍 SQL Analysis & Business Questions

Key transactional queries performed in PostgreSQL:

| Business Query | Insight Extracted | 
| ----- | ----- | 
| **Revenue by Gender** | Measured male contribution (\$157.9K) vs female contribution ($75.2K). | 
| **High-Spending Discount Users** | Filtered customers spending above average (\$59.76) despite discounts applied. | 
| **Category Rating Leaders** | Identified top satisfaction drivers (Gloves: 3.86, Sandals: 3.84). | 
| **Shipping Type Economics** | Compared Express shipping baskets (\$60.48) against Standard shipping ($58.46). | 
| **Subscriber vs Non-Subscriber Spend** | Evaluated spending parity (\$59.49 vs $59.87) to reassess subscriber value propositions. | 
| **Discount Dependency** | Identified products with near 50% discount reliance (Hat, Sneakers, Coat). | 
| **RFM-style Customer Segmentation** | Classified user base into New (83), Returning (701), and Loyal (3,116). | 
| **Repeat Buyer Subscription Likelihood** | Compared repeat buyer volume across subscription tiers (2,518 un-subscribed vs 958 subscribed). | 
| **Age Demographic Contribution** | Balanced cohort revenue: Young Adult (26.7%), Middle-aged (25.4%), Senior (24.0%), Adult (23.9%). | 

## 📈 Power BI Dashboard

The Power BI dashboard translates SQL outputs into interactive management views:

* **KPI Summary Cards:** Total Customers (3.9K), Average Order Value (\$59.76), Average Review (3.75).

* **Subscription Distribution:** Donut chart highlighting the 27% subscriber vs 73% non-subscriber split.

* **Category Performance:** Revenue and total volume breakdowns across Clothing, Accessories, Footwear, and Outerwear.

* **Cohort Analysis:** Visual comparative bars breaking down revenue and volume by age brackets.

* **Slicers:** Interactive filtering by Gender, Subscription Status, Product Category, and Shipping Method.

*(Place your dashboard screenshot here: `assets/dashboard_preview.png`)*

## 🚀 Strategic Recommendations

1. **Restructure Subscription Value Proposition:**

   * Subscribers are currently spending equivalent amounts to non-subscribers. Introduce exclusive perks, tiered loyalty points, or threshold-based free express shipping to stimulate basket growth.

2. **Target High-Intent Repeat Buyers:**

   * Launch automated email workflows offering discounted first-month subscriptions to the 2,518 repeat non-subscribed buyers.

3. **Audit Promotional Margin Leakage:**

   * Review discount rules on Hats and Sneakers (50% promotional dependency) to prevent margin erosion while maintaining conversion rates.

4. **Express Shipping Incentives:**

   * Since Express shoppers spend more (\$60.48 vs $58.46), consider gamified cart thresholds (e.g., *"Add \$15 to unlock Free Express Shipping"*).

## 💻 Getting Started

### Prerequisites

* Python 3.9+

* PostgreSQL

* Microsoft Power BI Desktop

### Installation & Setup

1. **Clone the repository:**

   ```
   git clone https://github.com/your-username/customer-shopping-behaviour-analysis.git
   cd customer-shopping-behaviour-analysis
   
   
   ```

2. **Set up virtual environment & dependencies:**

   ```
   python -m venv venv
   source venv/bin/activate  # On Windows use: venv\Scripts\activate
   pip install -r requirements.txt
   
   
   ```

3. **Run the EDA & Data Pipeline:**

   ```
   jupyter notebook notebooks/data_cleaning_and_eda.ipynb
   
   
   ```

4. **Execute SQL Queries:**

   * Connect your PostgreSQL client (pgAdmin, DBeaver, or psql) to your target database and run `sql/business_queries.sql`.

5. **Open Power BI Dashboard:**

   * Launch `dashboard/customer_behavior.pbix` in Power BI Desktop to inspect visual charts and DAX measures.

## 👤 Author

* **Your Name** – [LinkedIn Profile](https://linkedin.com) | [GitHub Profile](https://github.com)