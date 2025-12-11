# ✨ 𝐏𝐫𝐨𝐣𝐞𝐜𝐭 𝐑𝐄𝐀𝐃𝐌𝐄: 𝐄𝐧𝐝-𝐭𝐨-𝐄𝐧𝐝 𝐃𝐚𝐭𝐚 𝐌𝐨𝐝𝐞𝐥𝐢𝐧𝐠 𝐚𝐧𝐝 𝐓𝐫𝐚𝐧𝐬𝐟𝐨𝐫𝐦𝐚𝐭𝐢𝐨𝐧 🚀

## 📜 𝐏𝐫𝐨𝐣𝐞𝐜𝐭 𝐎𝐯𝐞𝐫𝐯𝐢𝐞𝐰

This comprehensive project established a robust, relational **Star Schema** for BI reporting, focusing on Sales and Returns data. It covered all phases, from initial data extraction and advanced Power Query transformations to defining the final dimensional model, relationships, and hierarchies.

---

## 🛠️ 𝐏𝐡𝐚𝐬𝐞 𝐈: 𝐀𝐝𝐯𝐚𝐧𝐜𝐞𝐝 𝐃𝐚𝐭𝐚 𝐄𝐱𝐭𝐫𝐚𝐜𝐭𝐢𝐨𝐧 & 𝐓𝐫𝐚𝐧𝐬𝐟𝐨𝐫𝐦𝐚𝐭𝐢𝐨𝐧

This section highlights the rigorous data preparation and standardization conducted using **Power Query**.

### 1. 𝙸𝚗𝚐𝚎𝚜𝚝𝚒𝚘𝚗 & 𝚂𝚘𝚞𝚛𝚌𝚎 𝙼𝚊𝚗𝚊𝚐𝚎𝚖𝚎𝚗𝚝
* **Diverse Sources:** Loaded data from an $\text{HTML table}$ (web source), a folder containing multiple $\text{monthly Excel files}$ (using Append Queries from Folder), and a separate $\text{employee dataset}$.
* **Query Appending:** Used the **Append Queries as New** feature to append Jan-Mar sales data.
* **Dynamic Configuration:** Configured a dynamic folder path using **Parameters** and modified data source credentials under **Data Source Settings**.

### 2. 𝚃𝚛𝚊𝚗𝚜𝚏𝚘𝚛𝚖𝚊𝚝𝚒𝚘𝚗𝚜 & 𝙳𝚊𝚝𝚊 𝚀𝚞𝚊𝚕𝚒𝚝𝚢
| Area | Techniques Applied |
| :--- | :--- |
| **Basic Cleaning** | Removed blank rows and columns; promoted first row to headers; renamed columns; removed duplicates and filtered null values. |
| **Text Tools** | Used $\text{UPPER(), LOWER(), TRIM(), CLEAN(), REPLACE()}$, and $\text{SPLIT COLUMN BY DELIMITER}$ to clean and standardize customer names and address fields. |
| **Numeric Tools** | Rounded revenue to 2 decimal places and created the calculated column: $\text{Profit} = \text{Revenue} - \text{Cost}$. |
| **Date Tools** | Extracted Day, Month, Year, and Quarter from $\text{Order Date}$; created a **custom Fiscal Month** column; and added an age column from $\text{Birthdate}$. |
| **Merging & Grouping** | $\text{Merged}$ Sales Data with Employee Data using $\text{Region}$ or $\text{EmployeeID}$; $\text{Grouped}$ data by Region to compute Total Sales, Average Order Value, and Transaction Count. |
| **Quality** | Used **Column Profile, Distribution, and Quality tools** to identify missing values, detect errors, and understand distinct and unique values. |

### 3. 𝙲𝚘𝚗𝚍𝚒𝚝𝚒𝚘𝚗𝚊𝚕 𝙻𝚘𝚐𝚒𝚌 & 𝚁𝚎𝚜𝚑𝚊𝚙𝚒𝚗𝚐
* 🏷️ **Conditional Column:** Created a **Sales Category** column (High $\ge$ 10,000, Medium 5,000–9,999, Low $<$ 5,000).
* 🔢 **Indexing:** Added both 0-based and 1-based Index columns.
* 🔄 **Data Reshaping:** Performed both $\text{Pivoting}$ (to convert monthly columns to a single column) and subsequent $\text{Unpivoting}$ (to return data to a normalized form).
* ♻️ **Refresh Simulation:** Successfully simulated adding a new file ($\text{Sales\_Apr.xlsx}$) and verified that queries auto-load and transformations are maintained.

---

## 🏗️ 𝐏𝐡𝐚𝐬𝐞 𝐈𝐈: 𝐒𝐜𝐡𝐞𝐦𝐚 𝐃𝐞𝐬𝐢𝐠𝐧 & 𝐑𝐞𝐥𝐚𝐭𝐢𝐨𝐧𝐬𝐡𝐢𝐩 𝐂𝐨𝐧𝐬𝐭𝐫𝐮𝐜𝐭𝐢𝐨𝐧

This section details the construction of the dimensional model and its usability features.

### 1. 𝕯𝖆𝖙𝖆 𝕸𝖔𝖉𝖊𝖑 𝕬𝖗𝖈𝖍𝖎𝖙𝖊𝖈𝖙𝖚𝖗𝖊
* **Schema:** Implemented a **Star Schema** using $\text{Sales\_Fact}$ as the central table.
* **Data Preparation:** Imported all files via **Power Query**, applied proper data types, and removed blank rows.
* **Relationships:** Defined $\text{Primary Keys}$ and $\text{Foreign Keys}$ manually and created all core relationships:
    * `Sales_Fact` $\rightarrow$ `Customer_Dim`, `Product_Dim`, `Region_Dim`, `Date_Dim`
    * `Returns_Fact` $\rightarrow$ `Sales_Fact`
* **Advanced Filtering:** The $\text{Returns\_Fact} \rightarrow \text{Date\_Dim}$ relationship was set as an **inactive relationship** for the $\text{ReturnDateKey}$.
* **Integrity:** Set appropriate $\text{cardinalities}$ and $\text{cross-filter directions}$ (preferably single), enabled bidirectional filters only where justified, and resolved all **filter ambiguity** issues.

### 2. 𝕽𝖊𝖕𝖔𝖗𝖙𝖎𝖓𝖌 𝕰𝖓𝖍𝖆𝖓𝖈𝖊𝖒𝖊𝖓𝖙𝖘
* **Data Categories:** Defined categories (e.g., City, Country, ProductName) for proper sorting.
* **Reporting Hierarchies:** Built essential drill-down structures for intuitive analysis:
    * $\text{Date\_Dim}$: Year $>$ Quarter $>$ Month $>$ Date
    * $\text{Region\_Dim}$: Country $>$ State $>$ City
    * $\text{Product\_Dim}$: Category $>$ Subcategory $>$ ProductName

## ✅ 𝐕𝐞𝐫𝐢𝐟𝐢𝐜𝐚𝐭𝐢𝐨𝐧 𝐒𝐭𝐞𝐩

The complete model was validated using a **Matrix Table** (the only allowed visual) to confirm accuracy across key analytical dimensions:
* Sales grouped by Product Category and Region.
* Return reasons by Fiscal Year.
* Revenue by Customer Segment.

---
