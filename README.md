# 🛒 Zepto E-commerce: SQL Data Analysis Project  

This is a **real-world data analyst portfolio project** based on an e-commerce inventory dataset scraped from **Zepto** — one of India’s fastest-growing quick-commerce startups.  

It simulates actual analyst workflows, from **raw data exploration** to **business-focused SQL analysis**.  

---

## 📌 Project Overview  
Using PostgreSQL, this project demonstrates how to:  
- ✅ Create and structure SQL databases  
- ✅ Perform **Exploratory Data Analysis (EDA)**  
- ✅ Clean messy e-commerce data  
- ✅ Write **business-driven SQL queries** for insights on stock, pricing, revenue, and discounts  

---

## 📁 Dataset Overview  
The dataset (sourced from Kaggle, scraped from Zepto’s listings) mimics a **real e-commerce inventory system**.  

### 🧾 Columns:  
- `sku_id` → Unique identifier (Primary Key)  
- `name` → Product name  
- `category` → Category like Fruits, Snacks, Beverages  
- `mrp` → Maximum Retail Price (₹)  
- `discountPercent` → Discount percentage  
- `discountedSellingPrice` → Final price after discount  
- `availableQuantity` → Units available  
- `weightInGrams` → Product weight in grams  
- `outOfStock` → Stock availability (TRUE/FALSE)  
- `quantity` → Units per package  

---

## 🔧 Project Workflow  

### 1️⃣ Database & Table Creation  
```sql
DROP TABLE IF EXISTS zepto;

CREATE TABLE zepto (
    sku_id SERIAL PRIMARY KEY,
    category VARCHAR(120),
    name VARCHAR(150) NOT NULL,
    mrp NUMERIC(8,2),
    discountPercent NUMERIC(5,2),
    availableQuantity INTEGER,
    discountedSellingPrice NUMERIC(8,2),
    weightInGrams INTEGER,
    outOfStock BOOLEAN,
    quantity INTEGER
);
```

### 2️⃣ Data Import

Imported the dataset into the `zepto` table using the `\copy` command.

```sql
\copy zepto(category, name, mrp, discountPercent, availableQuantity,
            discountedSellingPrice, weightInGrams, outOfStock, quantity)
FROM 'data/zepto_v2.csv'
WITH (FORMAT csv, HEADER true, DELIMITER ',', QUOTE '"', ENCODING 'UTF8');
```

### 3️⃣ Data Exploration 🔍

- Counted total records in the dataset  
- Viewed a sample of the data to understand structure  
- Checked for missing/null values  
- Listed all distinct product categories  
- Compared in-stock vs out-of-stock products  
- Found products appearing multiple times (different SKUs)  

### 4️⃣ Data Cleaning 🧹
- Removed rows with MRP or discounted price = 0
- Converted prices from paise to rupees
- Checked for missing/null values

### 5️⃣ Business Insights 📊
- Found top products by discount percentage
- Identified high-MRP products that are out of stock
- Estimated total revenue per category
- Filtered expensive products (MRP > ₹500) with low discount
- Ranked top categories with highest average discounts
- Calculated price per gram for value-for-money products
- Grouped products by weight: Low, Medium, Bulk
- Measured total inventory weight per category

---
### 🛠️ How to Use This Project

1. Clone the repository:

```bash
git clone https://github.com/amlanmohanty/zepto-SQL-data-analysis-project.git
cd zepto-SQL-data-analysis-project
```
2. Open zepto_SQL_data_analysis.sql:
 
    This file contains:

     ⚬ Table creation  
     ⚬ Data exploration  
     ⚬ Data cleaning  
     ⚬ SQL business analysis  

4. Load the dataset into pgAdmin or any other PostgreSQL client:

     ⚬ Create a database and run the SQL file  
     ⚬ Import the dataset (convert to UTF-8 if necessary)
---

## 📜 License

**MIT License** — feel free to fork, star ⭐, and use in your portfolio.

---

## 👩‍💻 About the Author

Hey, I’m **Aanshi Gupta** — a **Data Analyst** passionate about uncovering insights from data.  
I turn complex datasets into clear, actionable strategies for real-world impact.

📎 [GitHub Profile](https://github.com/gupta-aanshi)
