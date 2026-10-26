# E-Commerce Sales & Customer Analytics

End-to-end analysis of an Indian e-commerce business (Jan 2023 - Dec 2025): data cleaning and validation in Python, KPI and segmentation queries in SQL, and an interactive 4-page Power BI dashboard.

**Tools:** Python (Pandas, NumPy), SQL, Power BI, Jupyter Notebook, Git

![Dashboard preview](images/dashboard_preview.png) <!-- add a screenshot of your Power BI dashboard here -->

---

## Business Questions

1. How large is the business, and how profitable is it (sales, profit, margin, AOV)?
2. Which categories, regions and sales channels drive revenue?
3. How do discounts affect profitability?
4. Which customers and segments are the most valuable?
5. When does demand peak across the year?
6. How satisfied are customers, and how many orders are lost to cancellations and returns?

---

## Dataset

Five related tables, about 291K rows in total (amounts are in INR).

| Table | Rows | Description |
| --- | --- | --- |
| `orders.csv` | 60,000 | Order date, channel, payment method, status, shipping city/state, delivery date |
| `order_items.csv` | 167,150 | Product, quantity, unit price, discount %, line total |
| `customers.csv` | 20,000 | Age, gender, city/state, signup date, segment, acquisition channel |
| `products.csv` | 2,000 | Category, sub-category, brand, price, cost price, stock |
| `reviews.csv` | 42,132 | Rating (1-5), review title, review date |

**Order statuses:** Delivered, Shipped, Processing, Cancelled, Returned.

---

## Approach

1. **Cleaning and validation (Python):** checked data types, duplicates and missing values; confirmed that every order links to a customer, items and products; verified that `line_total = unit_price x quantity x (1 - discount%)`; treated empty delivery dates as non-delivered orders.
2. **Metrics (SQL and Pandas):** built the KPI definitions below and joined all tables into one analysis view.
3. **Analysis:** segmentation, product and category ranking, regional and monthly trends, discount impact on margin, review analysis.
4. **Dashboard (Power BI):** 4 interactive pages with KPI cards, charts, a map and slicers.

### KPI Definitions

Revenue KPIs exclude **Cancelled** and **Returned** orders.

| KPI | Definition |
| --- | --- |
| Total Sales | Sum of `line_total_inr` |
| Profit | Sales - (`cost_price_inr` x quantity) |
| Profit Margin | Profit / Sales |
| AOV | Total Sales / number of orders |
| Orders | Distinct `order_id` |
| Customer Count | Distinct `customer_id` |

---

## Key Results

| KPI | Value |
| --- | --- |
| Total Sales | INR 174.8 Cr |
| Profit | INR 45.9 Cr |
| Profit Margin | 26.2% |
| AOV | INR 33.9K |
| Orders | 51,542 |
| Customers | 17,324 |

---

## Key Insights

- **Discounts erode profit.** Margin falls from 32.3% on full-price items to 10.0% at 25% off. About 62% of sales come from discounted items.
- **Electronics dominates.** It generates 67.7% of sales, with a 26.4% margin; no other category exceeds 14%.
- **A small group of customers drives most of the revenue.** The top 20% of customers contribute 55.6% of sales.
- **Demand peaks in October and November.** These two months bring about 29% of annual sales.
- **Sales are concentrated by region.** Maharashtra leads with 15.2%, followed by Tamil Nadu (10.0%), Madhya Pradesh (9.7%) and Gujarat (9.6%).
- **Mobile app leads.** It accounts for about 58% of sales, with the website at 32% and the desktop app at 10%.
- **Order losses are notable.** 7.9% of orders are cancelled and 6.2% are returned.
- **Customers are fairly satisfied.** Average rating is 4.04 and 74.8% of reviews are 4 stars or higher.
- **Sales are flat year over year.** Annual sales stayed close to INR 58 Cr per year from 2023 to 2025.

---

## Recommendations

1. Cap discounts at 10-15% on high-volume items, since margin drops sharply beyond that.
2. Plan stock, ads and delivery capacity ahead of the October-November peak.
3. Build a retention and loyalty program for the top 20% of customers.
4. Investigate the causes of cancellations and returns, starting with Electronics.
5. Expand marketing in high-potential states outside the current top four.

---

## Project Structure

```
.
├── data/                      # the five CSV files
├── notebooks/                 # [Jupyter notebook: cleaning and EDA]
├── sql/                       # [SQL queries for KPIs and segmentation]
├── dashboard/
│   └── E-Commerce_Sales__Customer_Analytics.pbix
├── images/                    # dashboard screenshots
└── README.md
```

---

## How to Run

1. Clone the repository: `git clone https://github.com/sumanth-3004/[repo-name].git`
2. Install dependencies: `pip install pandas numpy matplotlib seaborn jupyter`
3. Open the notebook in `notebooks/` and run all cells.
4. Run the queries in `sql/` on MySQL or PostgreSQL after importing the CSVs.
5. Open the `.pbix` file in Power BI Desktop. If prompted, point the data source to the `data/` folder.

---

## Author

**Sumanth V** | Data Analyst
[LinkedIn](https://linkedin.com/in/sumanth3004) | [GitHub](https://github.com/sumanth-3004) | sumanthv3004@gmail.com
