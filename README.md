# Power BI - Financials Data Analysis
<p align="center">
    <img src="imgs/powerbi.png" alt="Power BI dashboard displaying financial performance metrics, including charts and tables with revenue, expenses, and profit trends. The dashboard layout is clean and organized, designed for clear data visualization in a professional business environment." width="80%" />
</p>

This project showcases using Power BI to analyze and visualize financial performance data. It includes a sample dataset (financials) containing key financial indicators and demonstrates how to complete data summaries and build interactive dashboards that support data-driven decision-making.

### Dataset Description
- The dataset is a sample data from Microsoft Power BI.
- It captures transactional and financial performance metrics for product sales across multiple countries and time periods. Each row represents a unique sales transaction/aggregate record, with key attributes.

**🏷️ Fields/Columns**
- Segment – Market segment category (e.g., Consumer, Corporate, Home Office).
- Country – The nation where the sale occurred (e.g., Canada, Germany).
- Product – Name or type of product sold.
- Discount Band – The discount category applied (e.g., None, Medium, High).
- Units Sold – Number of product units sold in the transaction.
- Manufacturing Price – Cost to produce one unit of the product.
- Sale Price – The listed selling price before discounts.
- Gross Sales – Total revenue before discounts (Units Sold × Sale Price).
- Discounts – Total value of discounts applied.
- Sales – Actual revenue after discounts (Gross Sales − Discounts).
- COGS (Cost of Goods Sold) – Total cost to produce the units sold.
- Profit – Net profit from the transaction (Sales − COGS).
- Date, Month Number, Month Name, Year – Temporal indicators for time-series analysis.

**Analyses Using DAX**
- Some useful and actionable analyses to depict core insights include:
  1. Performance
  2. Profitability
  3. Time trends
  4. Segmentation

- All workings, and analysis are done in the [financials pbix file](/financials.pbix), with sample output displayed.

---