# ⚙️ Data Extraction and Transformation (Power Query Phase) 🧰

## Project Overview

This phase focused entirely on advanced data extraction and robust transformations using **Power Query**. The goal was to clean, standardize, merge, and enrich the raw source data, preparing it for the final data modeling stage.

---

## 1. Data Extraction & Ingestion

Multiple diverse data sources were connected and loaded into the environment:

* 🌐 **Web Data:** An **HTML table** (e.g., public statistics) was successfully loaded from the web.
* 📁 **Folder Integration:** Three monthly Excel files (`Sales_Jan.xlsx`, `Sales_Feb.xlsx`, `Sales_Mar.xlsx`) were loaded from a **folder source** using the **Append Queries from Folder** feature, ensuring efficient scaling for new months.
* 🧑‍💻 **Employee Data:** An `employee dataset` (containing EmployeeID, Name, Department, Region, Join Date) was loaded from a separate Excel source.

## 2. Core Data Cleansing and Quality

Standard fundamental transformations were applied across all datasets to establish a clean starting point.

* 🧹 **Basic Cleaning:** Blank rows and columns were removed, the first row was promoted to headers, and columns were renamed to meaningful names.
* 📊 **Data Types & Locales:** Data types were changed appropriately, utilizing **Change Type with Locale** for accurate handling of currency and date formats.
* 🗑️ **Duplication & Nulls:** Duplicates were removed, and null values were filtered out to ensure data quality.

## 3. Data Enhancement Transformations

Advanced functions were used to enrich the data, standardize fields, and derive new analytical columns.

### Text & Standardization Tools
* 📝 **Field Standardization:** Utilized functions like `UPPER()`, `LOWER()`, `TRIM()`, `CLEAN()`, `REPLACE()`, and **Split Column by Delimiter** to clean and standardize customer names and address fields.

### Numeric & Calculation Tools
* 💰 **Revenue Precision:** Revenue columns were rounded to 2 decimal places.
* ➕ **Derived Metrics:** A new calculated column for **Profit** was created using the formula: $\text{Profit} = \text{Revenue} - \text{Cost}$.

### Date & Time Intelligence Tools
* 📅 **Date Components:** Day, Month, Year, and Quarter were extracted from the $\text{Order Date}$.
* 🗓️ **Fiscal Month:** A **custom Fiscal Month** column was created.
* ⏳ **Age Calculation:** An age column was added, calculated from the `Birthdate` field.

### Conditional Logic & Indexing
* 🏷️ **Sales Category:** A new conditional column, **Sales Category**, was created to bucket sales values:
    * **High** ($\ge$ 10,000)
    * **Medium** (5,000 – 9,999)
    * **Low** ($<$ 5,000)
* 🔢 **Indexing:** Both 0-based and 1-based Index columns were added for positional referencing.

### Pivoting & Reshaping
* 🔄 **Reshaping Data:** Performed both **Pivot** operations (to convert monthly columns into a single column) and subsequent **Unpivot** operations (to revert sales data back into a normalized, tidy format).

## 4. Integration, Aggregation, & Profiling

The final steps involved combining datasets, aggregating data for summary metrics, and ensuring overall data quality.

* 🤝 **Merging & Appending:**
    * Sales data was **Merged** with Employee Data using either **Region** or **EmployeeID**.
    * Jan-Mar sales data was **Appended** using the `Append Queries as New` feature.
* 📈 **Grouping & Aggregation:** Data was grouped by **Region** to compute key summary metrics:
    * Total Sales
    * Average Order Value
    * Transaction Count
* 🔬 **Data Profiling:** Utilized the **Column Profile, Column Distribution, and Column Quality** tools to:
    * Identify missing values.
    * Detect column-level errors.
    * Understand distinct and unique values.

## 5. Source Management & Refresh Simulation

The project included steps to make the data solution dynamic, configurable, and ready for future monthly refreshes.

* 🛠️ **Source Configuration:** **Parameters** were configured to support a dynamic folder path, and data source credentials were modified under **Data Source Settings**.
* ♻️ **Refresh Simulation:** The process was validated by simulating the addition of a new monthly file (`Sales_Apr.xlsx`) to ensure queries **auto-load** and transformations are **maintained** upon refresh.

---
