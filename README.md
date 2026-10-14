# Telecom Customer Churn Analysis (SQL + Power BI)

A 3-page Power BI dashboard and SQL analysis that answers: **who is leaving a telecom company, why, and what should the business do about it?**

![Overview](<img width="778" height="436" alt="page1_overview" src="https://github.com/user-attachments/assets/0294d74d-b4b5-4922-90d7-e8802d8ed873" />
)

## Business question

A telecom company is losing about 1 in 4 customers. Which customers churn, what reasons do they give, and where should retention effort go first?

## Key findings

- **Churn is concentrated in one group.** Month-to-month customers are 51% of the base (3,610 of 7,043) but account for 89% of all churn (1,655 of 1,869).
- **Overall churn rate is 26.54%** (1,869 of 7,043 customers), with about **$139K in monthly revenue lost**.
- **Contract type matters most:** churn is 45.84% on month-to-month, 10.71% on one-year and 2.55% on two-year contracts.
- **The first year is the danger zone:** churn is 47.44% at 0-12 months and falls to 9.51% after 49+ months.
- **Fiber Optic customers churn most** (40.72%) compared with DSL (18.58%) and no internet (7.40%).
- **Payment method:** mailed check (36.88%) and bank withdrawal (34.00%) customers churn far more than credit card customers (14.48%).
- **Competitors are the main exit:** 841 of 1,869 churned customers (45%) left for a competitor, mostly citing better devices or offers. Attitude of staff (16.8%) and dissatisfaction (16.2%) follow, then price (11.3%).
- **Churned customers pay more:** $74.44 per month on average vs $61.27 for retained customers (about 21% higher), so the revenue loss is larger than the headcount suggests.
- **Power BI's Key Influencers visual** ranks month-to-month contracts first (7.35x more likely to churn), then no dependents (5.00x), Fiber Optic (2.58x), higher monthly charges (2.35x) and no online security (2.14x).

## Recommendations

1. Move month-to-month customers to annual contracts with a small switching incentive.
2. Protect high-paying customers from competitor offers with retention deals and device upgrades.
3. Bundle online security and tech support, starting with a free trial for at-risk customers.
4. Investigate Fiber Optic service quality (speed, pricing, support complaints).
5. Improve support follow-up for unhappy customers.

## Dashboard pages

| Page | What it shows |
|---|---|
| **Overview** | KPIs (customers, churned, churn rate, retention rate, revenue lost) and churn rate by contract, internet type, tenure band and payment method, with slicers |
| **Churn Drivers** | Top churn reasons, churn by category, average monthly charge of churned vs retained customers, and takeaways |
| **Risk & Actions** | Key Influencers (Power BI AI visual) with recommendations |

![Churn Drivers](<img width="776" height="434" alt="page2_churn_drivers" src="https://github.com/user-attachments/assets/7bb39678-1f8e-4b12-9864-ffdb0079ff1c" />
)
![Risk and Actions](<img width="743" height="415" alt="page3_risk_actions" src="https://github.com/user-attachments/assets/0578bda7-7bde-4c17-a989-a4bcef0be754" />
)

## Data

IBM telecom customer churn dataset (Kaggle), 7,043 customers. Each row is one customer with contract, services, charges, tenure, churn label and, for churned customers, a churn reason and category.

## Approach

1. **Cleaning and checks (SQL / Power Query):** checked row counts and duplicates, converted charge columns to numeric, and handled blanks.
2. **SQL analysis:** churn rate overall and by segment, share of customers vs share of churn, tenure bands, revenue lost, and churn reasons. See `churn_analysis.sql`.
3. **Dashboard (Power BI):** DAX measures (Total Customers, Churned Customers, Churn Rate, Retention Rate, Monthly Revenue Lost, Avg Charge Churned/Retained), a tenure-band column with a sort order, and a navy and coral theme.
4. **AI visual:** Power BI's Key Influencers visual, run on fields known before a customer leaves.

## How AI was used

- Power BI's built-in **Key Influencers** visual to rank churn drivers.
- An AI assistant (Claude) helped with dashboard layout, DAX and SQL drafts, and wording. I checked every figure against my own charts and queries.

## Limitations

- The data is a single snapshot with no dates, so I can't analyse churn over time or build monthly cohorts.
- Findings are **associations, not proven causes** (for example, month-to-month contracts may attract customers who were more likely to leave anyway).
- Churn reasons exist only for customers who left, and 130 are "Don't know".
- I excluded churn reason, churn category, churn score, customer status and satisfaction score from the Key Influencers analysis, because they are only known after (or come from a model of) churn.
- No predictive model yet. A next step is a per-customer churn risk score with logistic regression.

## Files

- `churn_dashboard.pbi`: Power BI report
- `churn_dashboard.pdf`: exported dashboard (3 pages)
- `churn_analysis.sql`: SQL queries
- `page1_overview.png`, `page2_churn_drivers.png`, `page3_risk_actions.png`: screenshots

## Tools

SQL, Power BI (DAX, Power Query, Key Influencers), Excel
