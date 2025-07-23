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

#### ✅ **1. Sales Performance Analysis**

* **Total Sales (Revenue):**

  ```DAX
  Total Sales = SUM('Table'[Sales])
  ```

* **Total Units Sold:**

  ```DAX
  Total Units Sold = SUM('Table'[Units Sold])
  ```

* **Sales by Country / Product / Year:**
  Use Matrix visuals or DAX measures like:

  ```DAX
  Sales by Country = CALCULATE([Total Sales], ALLEXCEPT('Table', 'Table'[Country]))
  ```

* **Average Selling Price:**

  ```DAX
  Average Sales Price = AVERAGE('Table'[Sales Price])
  ```

---

#### ✅ **2. Profitability Analysis**

* **Total Profit:**

  ```DAX
  Total Profit = SUM('Table'[Profit])
  ```

* **Profit Margin %:**

  ```DAX
  Profit Margin % = DIVIDE([Total Profit], [Total Sales])
  ```

* **Gross Sales vs Discounts:**

  ```DAX
  Total Discounts = SUM('Table'[Discounts])
  Discount % = DIVIDE([Total Discounts], SUM('Table'[Gross Sales]))
  ```

---

#### ✅ **3. Trend Analysis (Time-Based)**

* **Monthly Sales Trend:**
  Use `Month Number` or `Date`:

  ```DAX
  Monthly Sales = CALCULATE([Total Sales], ALLEXCEPT('Table', 'Table'[Month Number], 'Table'[Year]))
  ```

* **Year-on-Year Sales Growth:**

  ```DAX
  YoY Sales Growth = 
  VAR CurrentYear = [Total Sales]
  VAR LastYear = CALCULATE([Total Sales], SAMEPERIODLASTYEAR('Date'[Date]))
  RETURN DIVIDE(CurrentYear - LastYear, LastYear)
  ```

* **Running Total Sales (YTD):**

  ```DAX
  YTD Sales = TOTALYTD([Total Sales], 'Date'[Date])
  ```

---

#### ✅ **4. Product & Market Segmentation**

* **Top 5 Products by Sales:**
  Use DAX with `TOPN` or visual filter.

* **Sales by Discount Band:**

  ```DAX
  Sales by Discount Band = CALCULATE([Total Sales], ALLEXCEPT('Table', 'Table'[Discount Band]))
  ```

* **Market Share per Country/Product:**

  ```DAX
  Product Market Share = 
  DIVIDE(
    [Total Sales],
    CALCULATE([Total Sales], ALL('Table'[Product]))
  )
  ```

---

#### ✅ **5. Efficiency & Conversion**

* **Profit per Unit:**

  ```DAX
  Profit per Unit = DIVIDE([Total Profit], [Total Units Sold])
  ```

* **Sales Efficiency (Sales vs COGS):**

  ```DAX
  Sales Efficiency = DIVIDE([Total Sales], SUM('Table'[COGS]))
  ```

* **Unit Margin:**

  ```DAX
  Unit Margin = DIVIDE([Total Profit], SUM('Table'[Units Sold]))
  ```

---

#### ✅ **6. Price & Discount Sensitivity**

* **Impact of Discount on Sales:**
  Use scatter chart or correlation between discounts and sales:

  ```DAX
  Discounted Sales = CALCULATE([Total Sales], FILTER('Table', 'Table'[Discount Band] <> "None"))
  ```

* **Sales Price Variance by Country or Product:**

  ```DAX
  Avg Price per Product = CALCULATE(AVERAGE('Table'[Sales Price]), ALLEXCEPT('Table', 'Table'[Product]))
  ```

---

#### ✅ **7. Forecasting & Insights (Optional)**

* Use **DAX to create simple linear forecast**, or leverage Power BI’s built-in **Analytics pane** to forecast based on trendlines.

---

#### 🔎 Optional Deep Dives

* **Basket Analysis (if applicable):** What product combinations occur together?
* **Profitability by Channel (if more channels exist later)**
* **Comparative Analysis:**

  ```DAX
  Profit Comparison Germany vs Canada = 
  CALCULATE([Total Profit], 'Table'[Country] = "Germany") 
  - CALCULATE([Total Profit], 'Table'[Country] = "Canada")
  ```


