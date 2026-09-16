# Performance Analysis – Retail Inventory & Sales

Analyzing vendor efficiency and profitability to support strategic purchasing and inventory decisions using SQL and Python.

---

## Table of Contents

* [Overview](#overview)
* [Business Problem](#business-problem)
* [Dataset](#dataset)
* [Tools & Technologies](#tools--technologies)
* [Project Structure](#project-structure)
* [Data Cleaning](#data-cleaning)
* [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
* [Research Questions & Key Findings](#research-questions--key-findings)
* [How to Run This Project](#how-to-run-this-project)

---

## Overview

This project evaluates vendor performance and retail inventory dynamics to generate strategic insights for purchasing, pricing, and inventory optimization. A complete data pipeline was developed using SQL for ETL, Python for analysis and hypothesis testing, and Power BI for visualization.

---

## Business Problem

Effective inventory and sales management are critical in the retail sector. This project aims to:

* Identify underperforming brands requiring pricing or promotional adjustments
* Determine vendor contributions to sales and profitability
* Analyze the cost-benefit of bulk purchasing
* Investigate inventory turnover inefficiencies
* Statistically validate differences in vendor profitability

---

## Dataset

* Multiple CSV files located in the `/data/data` folder, including sales, vendor, and inventory data
* A summary table created from the ingested data and used for analysis

---

## Tools & Technologies

* SQL (Common Table Expressions, Joins, Filtering)
* Python (Pandas, Matplotlib, Seaborn, SciPy)
* Power BI
* GitHub

---

## Project Structure

```text
vendor-performance-analysis/
│
├── README.md
├── .gitignore
├── requirements.txt
├── Vendor Performance Report.pdf
│
├── notebooks/
│   ├── exploratory_data_analysis.ipynb
│   └── vendor_performance_analysis.ipynb
│
├── src/
│   ├── ingestion_db.py
│   └── get_vendor_summary.py
```

---

## Data Cleaning

* Removed transactions with:

  * Gross Profit ≤ 0
  * Profit Margin ≤ 0
  * Sales Quantity = 0
* Created summary tables containing vendor-level metrics
* Converted data types and handled outliers
* Merged relevant lookup tables

---

## Exploratory Data Analysis (EDA)

### Negative or Zero Values Detected

* Gross Profit: Minimum value of -52,002.78, indicating loss-making sales
* Profit Margin: Minimum value of -∞, indicating sales at zero or below cost
* Unsold Inventory: Identified slow-moving stock

### Outliers Identified

* High freight costs of up to 257K
* Large purchase and actual prices

### Correlation Analysis

* Weak correlation between Purchase Price and Profit
* Strong correlation between Purchase Quantity and Sales Quantity (0.999)
* Negative correlation between Profit Margin and Sales Price (-0.179)

---

## Research Questions & Key Findings

### 1. Brands for Promotions

Identified 198 brands with low sales but high profit margins, indicating potential opportunities for promotional strategies.

### 2. Top Vendors

The top 10 vendors account for 65.69% of total purchases, indicating a potential risk of over-reliance on a limited number of vendors.

### 3. Bulk Purchasing Impact

Large orders resulted in approximately 72% cost savings per unit.

### 4. Inventory Turnover

Identified approximately $2.71M worth of unsold inventory, highlighting potential inventory turnover inefficiencies.

### 5. Vendor Profitability

* High Vendors: Mean Profit Margin = 31.17%
* Low Vendors: Mean Profit Margin = 41.55%

### 6. Hypothesis Testing

Statistical testing identified a significant difference in profit margins between vendor groups, indicating distinct vendor profitability patterns.

---

## How to Run This Project

### 1. Clone the Repository

```bash
git clone https://github.com/palak0609/Procurement-Analytics-Vendor-Optimization.git
cd Procurement-Analytics-Vendor-Optimization
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3. Load the CSVs and Ingest Them into the Database

```bash
python src/ingestion_db.py
```

### 4. Create the Vendor Summary Table

```bash
python src/get_vendor_summary.py
```

### 5. Open and Run the Notebooks

* `notebooks/exploratory_data_analysis.ipynb`
* `notebooks/vendor_performance_analysis.ipynb`
