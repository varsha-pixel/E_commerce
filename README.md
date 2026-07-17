# E-Commerce Sales Dashboard (Olist Brazilian E-Commerce)

**Problem statement**

Leadership wants a single source of truth for core e-commerce KPIs (revenue, AOV, MoM growth), answers on whether customers come back (retention/repeat-purchase), which product categories drive revenue, and how logistics performance varies by region — built on top of properly joined, production-shaped data rather than a single flat CSV.

**Dataset**

**Kaggle**: Olist Brazilian E-Commerce 

**Domain**: end-to-end e-commerce analytics & KPI tracking

**Size**: 9 CSVs — orders, customers, order_items, order_payments, order_reviews, products, sellers, geolocation, category_translation — joined via orders.order_id / order_items.product_id / customers.customer_id / etc.

**Schema gotcha worth knowing up front**: customer_id is generated per order in this dataset — a returning customer gets a brand-new customer_id every time they buy. The stable, person-level identifier is customer_unique_id. Every retention/CLV/repeat-purchase query in this project joins through customer_unique_id, not customer_id — get this wrong and repeat purchase rate silently looks like 0%.

**Tools & Technologies**

**SQL Server** – Data querying and analysis

**Power BI** – Dashboard development

**Python (Pandas)** – Data cleaning and preprocessing

**Jupyter Notebook** – Data preparation

**Analysis walkthrough & key findings**

**Headline KPIs** — ~96.5k delivered orders, ~93.4k distinct customers, R$15.4M total revenue, R$159.86 average order value.

**Revenue trend** — steady growth through 2017, plateauing through most of 2018. The first two months of raw data (2016) are seed-data noise excluded from the trend chart, and the Jan 2017 growth-% figure is excluded from the growth chart specifically since it's a % change against a near-zero December 2016 baseline that would otherwise dwarf every real month-over-month move — both judgment calls stated explicitly rather than silently applied.

**Category performance** — health_beauty, watches_gifts, and bed_bath_table lead by revenue.

**Logistics** — ~12.5 day average delivery time, ~8% late-delivery rate overall, but late rates vary 2-3x by state, concentrated in regions farther from the main São Paulo logistics hub.

**Retention** — the standout finding — only ~3% of customers ever place a second order, confirmed independently by both a repeat-purchase-rate query and a full cohort-retention heatmap (which drops to low single digits by month 1 for every cohort). This is a real, well-documented characteristic of the Olist marketplace, not a query bug — and it reframes the whole "growth" conversation: growth here is acquisition-driven, not retention-driven.
