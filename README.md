# 📓 Online Retail II ETL Project with PySpark & SQLite

This project demonstrates a complete ETL (Extract → Transform → Load) pipeline built using PySpark, Spark SQL, and SQLite, all executed within Google Colab.

## 🚀 Overview

* Dataset: Online Retail II Excel file from UCI Machine Learning Repository
* Tools Used: PySpark, Spark SQL, Pandas, SQLite, Google Colab
* Final Output: Cleaned and enriched transactional data stored in a portable SQLite database hosted on Google Drive

---

## ✅ ETL Pipeline Breakdown

### 1. Extract

* Read data from the Excel file: Copy of online\_retail\_II.xlsx
* Converted it into CSV to simplify ingestion into Spark

### 2. Transform

* Loaded data into PySpark
* Applied the following transformations:

  * Removed records with nulls in key columns
  * Added a calculated Revenue column (Quantity \* UnitPrice)
  * Extracted clean invoice dates
  * Flagged returns using InvoiceNo pattern
* Created a temporary view to run SQL queries using Spark SQL

### 3. Load

* Converted final Spark DataFrame to pandas
* Saved to SQLite as a table: retail_sales
* Final .db file uploaded to [Google Drive](https://drive.google.com/drive/folders/12k2ccx8qcjTa0mELxJLGCRLQz0_Bm8P_?usp=sharing) for sharing

---

## 📁 Files

| File | Description |
| ---- | ----------- |
|      |             |

|   |
| - |

| [`pyspark_retail_etl.ipynb`](https://colab.research.google.com/github/anujgautam/retail-etl/blob/main/pyspark_retail_etl.ipynb) | Google Colab notebook containing the full ETL pipeline |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------ |
| [`retail_etl.db`](https://drive.google.com/drive/folders/12k2ccx8qcjTa0mELxJLGCRLQz0_Bm8P_?usp=sharing)                         | Final SQLite database hosted on Google Drive           |

---

## 🛠 How to Use

### 1. Run the notebook in Google Colab

```bash
Open pyspark_retail_etl.ipynb in Google Colab and execute all cells
```

### 2. View the final data

* Download and open retail\_etl.db using [DB Browser for SQLite](https://sqlitebrowser.org/), DBeaver, or any SQLite client

---

## 📊 Sample SQL Queries to Explore the Data

```sql
-- View top 10 rows
SELECT * FROM retail_sales LIMIT 10;

-- Daily Revenue
SELECT InvoiceDateOnly, ROUND(SUM(Revenue), 2) AS DailyRevenue
FROM retail_sales
GROUP BY InvoiceDateOnly;

-- Top customers by revenue
SELECT CustomerID, ROUND(SUM(Revenue), 2) AS TotalSpent
FROM retail_sales
GROUP BY CustomerID
ORDER BY TotalSpent DESC
LIMIT 5;
```

---

## 🎓 What I Learned

* Loading large data efficiently in PySpark
* Cleaning and transforming data using both PySpark and SQL
* Saving structured output to a lightweight local database (SQLite)
* Managing real-world datasets and showcasing results in a shareable format

---

## 🔗 Resources

* [Online Retail II Dataset](https://archive.ics.uci.edu/ml/datasets/Online+Retail+II)
* [DB Browser for SQLite](https://sqlitebrowser.org/)
* [Google Colab](https://colab.research.google.com/)

---

## 🤝 Connect

If you have feedback or suggestions, feel free to connect with me on [LinkedIn](https://www.linkedin.com/) or fork the project to build your own ETL version!

---

**#DataEngineering #ETL #PySpark #SQL #SQLite #GoogleColab #PortfolioProject**
