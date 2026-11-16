# Customer Shopping Behavior Analysis

**Python | SQL | Power BI** - an end-to-end analysis of 3,900 retail purchases to find out how customers shop and what the business should do about it.

<img width="1481" height="829" alt="image" src="https://github.com/user-attachments/assets/66b0b7aa-3d0c-4404-98f3-a25bf76d2436" />


---

## 1. Business Problem

A retail business has purchase data but no clear picture of its customers. Leadership wants answers to questions like:

- Who are our customers, and which segments bring the most revenue?
- Do subscribers spend more than non-subscribers?
- Are discounts helping or just giving away margin?
- Which categories, products and shipping options perform best?
- Are customers loyal, and are we attracting new ones?

**Goal:** turn raw transaction data into insights and clear actions that improve revenue, retention and subscriptions.

---

## 2. Process to Solve

| Stage | Tool | What was done |
|---|---|---|
| Prepare | Python (pandas) in Google Colab | Cleaned and prepared the data |
| Analyse | SQL (T-SQL syntax) | Answered 10 business questions |
| Present | Power BI | Built an interactive dashboard |

### Dataset
- 3,900 rows, 18 columns (20 after cleaning). One row per purchase, one purchase per customer.
- Demographics (age, gender, location, subscription), purchase details (item, category, amount, season, size, color) and behavior (discount, previous purchases, frequency, rating, shipping, payment).
- Only gap: 37 missing values in `Review Rating`.
- Dataset source: _add the link to your source here._

### Step 1: Data cleaning in Python
Notebook: `Customer_Behavior_Data_cleaning.ipynb`

1. Inspected structure with `df.info()` and `df.describe()`.
2. Filled the 37 missing ratings with the **median rating of each product category**.
3. Renamed all columns to snake_case.
4. Relabeled frequency values (Bi-Weekly to Fortnightly, Every 3 Months to Quarterly).
5. Created **`age_group`** with quartile binning: Young (18-31), Adult (32-44), Middle-Aged (45-57), Old (58-70).
6. Created **`frequency_of_purchases_days`** (7, 14, 30, 90 or 365).
7. Found `promo_code_used` identical to `discount_applied` (redundant).
8. Exported the clean file as `customers.csv`.

### Step 2: SQL analysis
File: `Customer_Behavior_Data_Analysis.sql`

Ten queries covering revenue by gender, discount behavior, top-rated products, shipping comparison, subscribers vs non-subscribers, discount-dependent products, customer segmentation, category volume, repeat buyers and subscriptions, and orders by age group.

### Step 3: Power BI dashboard
Files: `Customer_DB_BI.pbix`, `customer__behavior.pbix`

- **KPIs:** 3.9K customers, $59.76 average purchase, 3.75 average rating
- **Charts:** subscription share, revenue and sales by category, revenue and sales by age group
- **Slicers:** subscription status, gender, category, shipping type

![Dashboard, second theme](dashboard-2.png)

### Repository structure
```
.
├── Customer_Behavior_Data_cleaning.ipynb    # Python cleaning notebook
├── Customer_Behavior_Data_Analysis.sql      # 10 SQL queries
├── Customer_DB_BI.pbix                      # Power BI dashboard
├── customer__behavior.pbix                  # Power BI dashboard (second theme)
├── Customer_Behavior_Analysis_Report.pdf    # Full written report
├── customer_shopping_behavior.csv           # Raw dataset
├── dashboard-1.png / dashboard-2.png        # Dashboard screenshots
└── README.md
```

---

## 3. Insights

**SQL results**

| # | Question | Result |
|---|---|---|
| 1 | Revenue by gender | Male $157,890, Female $75,191 |
| 2 | Discount users above average spend | 839 of 1,677 (about 50%) |
| 3 | Top-rated products | Gloves 3.86, Sandals 3.84, Boots 3.82, Hat 3.80, T-shirt 3.78 |
| 4 | Express vs Standard shipping | $60.48 vs $58.46 |
| 5 | Subscribers vs non-subscribers | 1,053 at $59.49 vs 2,847 at $59.87 |
| 6 | Most discount-dependent products | Hat 50.00%, Sneakers 49.66%, Coat 49.07%, Sweater 48.17%, Pants 47.37% |
| 7 | Customer segments | Loyal 3,116, Returning 701, New 83 |
| 8 | Category volume | Clothing 1,737, Accessories 1,240, Footwear 599, Outerwear 324 |
| 9 | Repeat buyers who subscribe | 27.6% vs 27.0% overall |
| 10 | Orders by age group | Young 1,028, Middle-Aged 986, Old 944, Adult 942 |

**What the data says**

- **Revenue is volume-driven.** The average purchase is about $60 in every category, age group and shipping type. Total revenue is $233,081.
- **Men bring 68% of revenue because they are 68% of customers.** Spend per head is the same ($59.54 vs $60.25).
- **Subscription does not lift spend.** Subscribers spend $59.49 vs $59.87, and repeat buyers subscribe at the same rate as everyone else.
- **The base is loyal but not growing.** 80% of customers are Loyal and only 2% are New.
- **Discounting is widespread.** 43% of purchases use a discount, and half of discount users still spend above average.
- **Two categories carry the business.** Clothing and Accessories are 76% of revenue.
- **Express shipping buyers spend about 3.5% more** than Standard buyers.

---

## 4. Solution

| Problem found | Recommended action |
|---|---|
| Subscription does not lift spend | Add real benefits (free shipping, early access, points) and track frequency and retention |
| Heavy discounting | Test targeted discounts against a control group to protect margin |
| Weak customer acquisition | Run acquisition campaigns and a first-purchase offer; keep rewarding loyal buyers |
| Footwear and Outerwear under-developed | Cross-sell to Clothing and Accessories buyers; bundle offers |
| Women are under-served | Targeted campaigns and assortment for women customers |
| Strong products not promoted | Feature top-rated products (Gloves, Sandals, Boots, Hat) in campaigns |
| Small basket size | Promote Express shipping at checkout and bundle items |

**Next improvements**
- Drop `promo_code_used` before exporting the clean file.
- Rank products within each category in Query 8, and use `SUM(purchase_amount)` for revenue in Query 10.
- Add a date column to enable trend and seasonality analysis.
- Dashboard v2: average order value and rating by category, plus a subscriber comparison.
- Build a model to predict subscribers or high-spending customers.

---

## How to run

1. **Python:** open the notebook in Google Colab or Jupyter, update the CSV path, run all cells. It saves `customers.csv`.
2. **SQL:** import `customers.csv` as a table named `customers` in SQL Server, then run the queries.
3. **Power BI:** open either `.pbix` file in Power BI Desktop.

Full details, query screenshots and insights: [`Customer_Behavior_Analysis_Report.pdf`](Customer_Behavior_Analysis_Report.pdf)

## Author

**Mohit Singh Mandloi** - aspiring Data Analyst (Python, SQL, Power BI, Excel)

- LinkedIn: [linkedin.com/in/mohit-singh-2100a0326](https://linkedin.com/in/mohit-singh-2100a0326)
- GitHub: [github.com/mohetto-creator](https://github.com/mohetto-creator)
