# 📊 Sales Analysis & Data Automation Project

## 📝 Project Overview
This Power BI project analyzes monthly sales performance and employee data. The goal was to create a dynamic report where the client can switch between different months of data using parameters.

## 📂 Data Structure
The project connects to multiple data sources, including:
- **Sales Data:** Separate tables for `sales_jan`, `sales_feb`, and `sales_mar`.
- **Employee Data:** `employees` table containing staff details.
- **Geography:** `list of countries and territories` for regional analysis.

## 🛠️ Key Transformations (Power Query)
I used Power Query Editor to clean and automate the data flow:
1. **Dynamic Parameters:** Created a `ReportMonth` parameter (Text type) to filter specific months dynamically.
2. **Data Cleaning:**
   - Applied `Text.Trim` to remove excess whitespace from the "Customer Name" column.
   - Removed blank rows to ensure data quality.
3. **Data Modeling:** Connected Sales tables to the Employee lookup table.

## 🚀 How to Use
1. Download the `omproject1.pbix` file.
2. Open in Power BI Desktop.
3. Go to **Transform Data > Edit Parameters** to change the month being analyzed (e.g., change "January" to "February").

## 💻 Tech Stack
- **Tool:** Power BI Desktop
- **Language:** Power Query (M), DAX
