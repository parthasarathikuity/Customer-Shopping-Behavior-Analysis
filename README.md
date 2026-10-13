# Customer Shopping Behavior Analysis

An end-to-end data analytics project that explores customer purchasing patterns and turns transactional data into business insights using **Python, SQL, and Power BI**.

## Project Overview

Retail businesses need to understand what customers buy, how much they spend, and which factors may influence their purchasing decisions. This project analyzes customer shopping data to identify trends across customer demographics, product categories, discounts, shipping preferences, and subscription status.

**Business question:** How can a company use customer shopping data to identify trends, improve customer engagement, and optimize marketing and product strategies?

## Project Objectives

- Clean and prepare the raw customer dataset.
- Analyze revenue, product ratings, discounts, customer segments, and repeat purchases.
- Compare purchasing behavior across demographic and subscription groups.
- Present key metrics and patterns in an interactive Power BI dashboard.
- Translate analytical findings into practical business recommendations.

## Tools and Technologies

| Tool | Purpose |
|---|---|
| Python | Data inspection, cleaning, transformation, and feature engineering |
| Pandas | Data manipulation and analysis |
| Jupyter Notebook / Google Colab | Running and documenting Python analysis |
| SQL | Business queries and customer behavior analysis |
| PostgreSQL / MySQL | Relational database analysis (use the database configured in your SQL script) |
| Power BI | Interactive dashboard and visual reporting |

## Dataset

The project report describes a dataset containing **3,900 purchase records and 18 columns**. It includes information such as:

- **Customer details:** age, gender, location, and subscription status
- **Purchase details:** item purchased, category, purchase amount, season, size, and color
- **Shopping behavior:** discounts, previous purchases, purchase frequency, review rating, and shipping type

The report notes **37 missing values** in the `review_rating` column. The documented cleaning process fills these using the median rating for the relevant product category.

> Keep the dataset file in the project folder or update the notebook's file path to match your local setup. Do not upload private or sensitive customer data to a public repository.

## Project Workflow

1. **Data preparation with Python**
   - Load and inspect the dataset with Pandas.
   - Review data types, summary statistics, and missing values.
   - Impute missing review ratings using the category median.
   - Standardize column names to `snake_case`.
   - Create an `age_group` feature and a `purchase_frequency_days` feature as documented in the analysis.
   - Check whether `discount_applied` and `promo_code_used` are redundant; the report documents dropping `promo_code_used`.
   - Load the cleaned data into a relational database for SQL analysis.

2. **SQL analysis**
   - Query revenue by gender.
   - Find customers who used discounts but spent at least the average purchase amount.
   - Rank products by average review rating.
   - Compare average purchase amounts for Standard and Express shipping.
   - Compare customer counts, average spend, and revenue for subscribers and non-subscribers.
   - Identify products with the highest discount rates.
   - Segment customers into New, Returning, and Loyal groups.
   - Find the most purchased products in each category.
   - Examine repeat buyers by subscription status.
   - Calculate revenue by age group.

3. **Power BI dashboard**
   - Display customer and purchase KPIs.
   - Explore subscription status and gender.
   - Compare revenue and sales by product category.
   - Compare revenue and sales by age group.
   - Use available slicers to explore the data interactively.

4. **Business recommendations**
   - Promote relevant subscription benefits.
   - Reward repeat purchases and strengthen customer loyalty.
   - Review discount policies while monitoring profitability.
   - Highlight popular and highly rated products.
   - Use customer segments and age-group trends to inform targeted campaigns.

## Key Findings Reported

The accompanying analysis report highlights the following results. These are descriptive findings from this dataset, not proof that one factor caused another.

- **Shipping:** The reported average purchase amount was 60.48 for Express shipping and 58.46 for Standard shipping.
- **Subscriptions:** Non-subscribers generated more total revenue in the analyzed records because they represented a larger customer count; the report gives average spend as 59.87 for non-subscribers and 59.49 for subscribers.
- **Customer segments:** The report classified 3,116 customers as Loyal, 701 as Returning, and 83 as New.
- **Age groups:** Young Adults had the highest reported revenue contribution among the listed age groups.
- **Discounts:** Hats, Sneakers, Coats, Sweaters, and Pants were listed as the five products with the highest discount-purchase rates in the report.

See the project report and dashboard for the full context and visualizations.

## Repository Structure

A suggested GitHub layout (adjust names to match the files you upload):

```text
customer-shopping-behavior-analysis/
├── README.md
├── data/
│   └── customer_shopping_behavior.csv
├── notebooks/
│   ├── Customer_Behavior.ipynb
│   └── Customer_Shopping_Behaviour_Analysis_usingCOLAB.ipynb
├── sql/
│   └── customer_behavior.sql
├── dashboard/
│   └── Customer_Behavior_Dashboard.pbix
└── reports/
    ├── Business_Problem_Document.pdf
    └── Customer_Shopping_Behavior_Analysis.pdf
```

This is a suggested structure; move or rename files as needed. If the dataset is large or its license does not permit redistribution, exclude it from GitHub and document how to obtain it instead.

## How to Run

### 1. Get the project

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
cd customer-shopping-behavior-analysis
```

Replace `<YOUR_GITHUB_REPOSITORY_URL>` with your repository URL.

### 2. Install Python dependencies

```bash
python -m venv .venv
```

Activate the environment:

**Windows PowerShell**
```powershell
.venv\Scripts\Activate.ps1
```

**macOS / Linux**
```bash
source .venv/bin/activate
```

Install the packages used by your notebook:

```bash
pip install pandas numpy sqlalchemy jupyter
```

If the notebook uses PostgreSQL, also install the appropriate PostgreSQL driver, for example:

```bash
pip install psycopg2-binary
```

If you use Google Colab, upload the CSV to the runtime or mount Google Drive, then update the file path in the notebook.

### 3. Run the Python notebook

Open either notebook in Jupyter Notebook or Google Colab. Update the CSV path and database connection settings before running the cells in order.

### 4. Run the SQL queries

- Create or select the database configured for your environment.
- Create/load the `customer` table using the cleaned dataset and the schema expected by `customer_behavior.sql`.
- Run the SQL statements in your database client.
- The provided SQL file contains `USE customer_behavior;`, which is supported by MySQL but not PostgreSQL. If you use PostgreSQL, connect to the target database first and remove or adapt that statement.

### 5. Open the Power BI dashboard

Open the `.pbix` file in Microsoft Power BI Desktop. If prompted, update the data source path or database connection and refresh the data.

## Limitations

- The dataset contains 3,900 purchase records, so findings may not represent all retail customers.
- The available data may not contain every factor in the original business problem, such as detailed online/offline channel data.
- Observational patterns do not establish causation.
- Confirm the database dialect and schema before executing SQL because syntax and connection settings can differ between MySQL and PostgreSQL.
- Results depend on the data-cleaning rules and customer-segmentation thresholds used in the notebook and SQL.

## Future Improvements

- Add time-based sales and demand trend analysis if reliable transaction dates are available.
- Evaluate campaign performance and customer retention over time.
- Add profit-margin analysis to assess whether discounts improve profitability.
- Automate the Python-to-database ETL pipeline.
- Add data validation, reproducible environment files, and automated tests.
- Explore customer clustering or purchase prediction only if the available data supports a well-defined target and evaluation method.

## Deliverables

- Python notebooks for data cleaning and exploratory analysis
- SQL queries for business questions
- Power BI dashboard (`.pbix`)
- Project report and business recommendations

## Author

**Partha Sarathi Kuity**

B.Tech — Computer Science and Engineering

## License

No license has been specified for this repository yet. Add a `LICENSE` file only after deciding how the project and included data may be reused. Check the dataset's original license before sharing it.

