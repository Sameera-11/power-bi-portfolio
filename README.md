📊 Pareto Sales Analysis — Power BI Dashboard
A Power BI dashboard built to identify the top-contributing countries driving sales and profitability, using Pareto Analysis (80/20 principle). Designed to help business stakeholders prioritize focus areas based on cumulative contribution.

Dataset Overview:
FieldDetailsSourceSales transaction data (CSV/Excel)Records600 ordersPeriodJan 2024 – Dec 2024Countries8 (India, USA, UK, Germany, Australia, Brazil, Singapore, South Africa)Products10 unique productsKey MetricsNet Sales, Profit, Customer Count
Columns: OrderID, OrderDate, Product, Customer, Country, Region, NetSales, Profit

📌Dashboard Features:
KPI Cards

Total Sales — Overall Net Sales across all countries and periods
Total Profit — Aggregate profit for the selected filter context
Total Customers — Distinct customer count
Top Contributors — Dynamic label showing countries crossing the 80% threshold

Pareto Combo Chart

Bar chart — Net Sales by Country (sorted descending)
Line chart — Cumulative Sales % overlaid on the same axis
Built using Visual Calculations (RUNNINGSUM with ORDERBY) for dynamic cumulative percentage
80% reference line to visually identify the Pareto threshold

Slicers

Region filter
Product filter
Date / Period filter


Technical Implementation
DAX Measures
DAX-- Total Sales
Total Sales = SUM(Sales[NetSales])

Total Profit
Total Profit = SUM(Sales[Profit])

-- Total Customers
Total Customers = DISTINCTCOUNT(Sales[Customer])

-- Cumulative Sales % (Visual Calculation)
Cumulative Sales % = 
DIVIDE(
    RUNNINGSUM([Total Sales], ORDERBY([Total Sales], DESC)),
    CALCULATE([Total Sales], REMOVEFILTERS(Sales[Country]))
)
Key Techniques Used

Visual Calculations — RUNNINGSUM with ORDERBY for accurate cumulative % (order-dependent, runs in visual context)
RANKX — Dynamic country ranking within filter context
DIVIDE — Safe division to avoid blank/error on zero denominators
REMOVEFILTERS — Grand total denominator for cumulative % calculation
Star Schema — Clean single-table model with proper data types
Conditional Formatting — Highlighting top contributors visually


Business Insight

In this dataset, the top 3–4 countries account for ~80% of total Net Sales — validating the Pareto principle. This helps business teams prioritize sales efforts and resource allocation geographically.


🚀 How to Use

Download Pareto_Sales_Analysis.pbix
Open in Power BI Desktop (free)
Use the slicers to filter by Region, Product, or Date
The Pareto chart and KPIs update dynamically


🧰 Tools & Technologies
<img width="1195" height="684" alt="image" src="https://github.com/user-attachments/assets/459a0779-9214-4704-b079-62c57d82fed2" />


Power BI Desktop
DAX (Visual Calculations, RUNNINGSUM, RANKX)
Power Query (M) for data loading and type formatting
Excel as data source


👩‍💻 Author
Sameera Ganta
Power BI Developer | PL-300 Certified | Power Platform
📧 gantasameerashekhar@gmail.com
🔗 https://www.linkedin.com/in/sameera-ganta-332a191a8/

Part of my Power BI Portfolio — more dashboards coming soon!
