## 📚 Documentation  
Full project documentation is available in **Polish**.  
Even if you don’t speak Polish, you’ll find **many valuable screenshots** from SSIS and SSAS projects — all labels, menus, and configuration settings are in **English**, making it easy to follow.

---

# Real Estate Data Warehouse with SSAS Cube and Power BI Reports

This project demonstrates a complete data warehousing and analytics pipeline focused on the UK property market.  
It includes building an ETL process, a structured SQL Server Data Warehouse, a **multidimensional SSAS cube**, and interactive **Power BI** reports.

> **Pipeline**: Raw CSVs → ETL (SSIS) → SQL Server DWH → Cube (SSAS) → Visualization (Power BI)

---

## 🎯 Project Goals

- Analyze long-term trends in UK property prices and sales volume
- Evaluate correlation with macroeconomic indicators like inflation and GDP
- Compare performance across property types, ownership forms, and regions
- Identify top-performing investment areas using multi-dimensional analysis

---

## 📂 Data Sources

| Dataset             | Description                                      | Size     |
|---------------------|--------------------------------------------------|----------|
| `pp-complete.csv`   | UK property transactions (1995–2024)             | ~5.1 GB  |
| `series-030525.csv` | Monthly inflation (ONS)                          | 624 rows |
| `series-260625.csv` | Quarterly GDP data (ONS)                         | 288 rows |

---

## 🏗️ Data Warehouse Schema

The project uses a **star schema** with one central fact table `FactSell` and multiple dimensions:

- `DimDate` – full calendar hierarchy
- `DimLocation` – from county to street
- `DimPropertyType` – housing types (Detached, Flat, etc.)
- `DimNewBuild` – new vs resale
- `DimTenure` – ownership type (Freehold/Leasehold)
- `DimInflation` – CPI % per month
- `DimGdp` – GDP % per quarter

All dimensions use **surrogate keys** and are fed from an automated SSIS ETL pipeline.

---

## ⚙️ ETL Implementation (SSIS)

- Dynamic file import using `Foreach Loop Containers`
- Raw → staging → cleaned → dimensionalized pipeline
- Invalid data redirected to `*_error` tables with descriptions
- Use of:
  - Derived columns
  - Lookups
  - Data validation
  - Unicode & date format fixes
- All flows constructed in **Control Flow** and **Data Flow** layers

---

## 🧠 Multidimensional Cube (SSAS)

Created using SQL Server Analysis Services (SSAS) and deployed from Visual Studio:

- **Measures**:
  - `Total Sales Value`
  - `Average Price`
  - `Transaction Count`
  - `Inflation %` (avg over time)
  - `GDP %` (sum per year)
- **Calculated Members**:
  - Price categories (Luxury, Mid-Range, Budget, etc.)
  - GDP and inflation classification
- **Hierarchies**:
  - Time: Year → Quarter → Month
  - Location: County → District → Town → Locality → Street
- **Drill-down** analysis and KPIs implemented inside cube

---

## 📈 Power BI Reports

Interactive dashboards visualizing:

- Average price and inflation correlation
- Transaction volume vs macroeconomic shifts
- Regional price distribution (from county to street level)
- Price vs property type, tenure, and build status
- Top 10 expensive areas and outliers like "The Vale, Chelsea"

---


## 🧠 Skills Demonstrated

- Building ETL pipelines using **SSIS**
- Designing a normalized **Data Warehouse** in SQL Server
- Creating a full **SSAS cube** with hierarchies, measures, and calculated members
- Managing real-world datasets (30M+ records)
- Advanced visualization and interpretation using **Power BI**

---

## 🧑‍💻 Author

**Zlata Ranchukova**  
Wroclaw University of Science and Technology (PWr)  
Bachelor’s program — Data Warehousing project (2025)

---

## 📄 License

This project is provided for educational and portfolio purposes.  
For non-commercial use only.
