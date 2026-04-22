# End-to-End Hotel Business Intelligence Solution
**Author:** Osanda Madugalle (IT23555594)  
**License:** MIT  

## 📌 Project Overview
This repository hosts a comprehensive Business Intelligence implementation based on a 2024 Hotel Sales dataset (6,050 records). The project demonstrates the full BI lifecycle: Data Warehousing, ETL, Multidimensional Modeling (OLAP), and Interactive Visualization.

## 🏗️ Technical Architecture
The solution is built using the **Microsoft BI Stack**:
1. **Data Warehouse:** SQL Server Star Schema design.
2. **ETL (Assignment 01):** SSIS packages for data cleaning, transformation, and loading.
3. **OLAP (Assignment 02):** SSAS Multidimensional Cube with custom hierarchies and measures.
4. **Visualization:** Power BI (Live Connection) and MS Excel (Pivot Operations).

## 📂 Repository Structure
```text
.
├── Analysis_Services_Backup/      # SSAS Cube Backup (.abf)
│   └── CubeProject_IT23555594.abf
├── Database_Backup/               # SQL Server DW Backup (.bak)
│   └── DataWarehouse_IT23555594.bak
├── Documentation/                 # Project Reports & Assignment Briefs
│   ├── Assignment_01_Report.pdf
│   ├── Assignment_02_Report.pdf
│   ├── IT3021 - DWBI - Assignment 1 - 2026.pdf
│   └── IT3021 - DWBI - Assignment 2 - 2026.pdf
├── Excel_Analytics/               # OLAP Validation via Excel Pivot
│   └── Excel_IT23555594.xlsx
├── Integrated_BI_Project/         # Unified Visual Studio Solution
│   ├── Hotel_DW_ETL/              # SSIS Project (Extraction & Transformation)
│   │   ├── OLTP Source/           # Local project data copies
│   │   ├── Package.dtsx           # Core ETL workflow
│   │   └── Update_Accumulating_Fact.dtsx
│   └── CubeProject_IT23555594/    # SSAS Project (OLAP Cube)
│       ├── Hotel DW.cube          # Multidimensional Cube definition
│       ├── Hotel DW.ds            # Data Source connection
│       ├── Hotel DW.dsv           # Data Source View (Star Schema)
│       └── Dim *.dim              # Dimension definitions
├── OLTP_Data_Sources/             # Raw Source Files & OLTP Backup
│   ├── booking_data.xlsx
│   ├── customer_data.csv
│   └── Hotel_OLTP_Source.bak
├── Original_Dataset/              # Initial Transactional Data
│   └── transactions.xlsx
├── Assignment_01-Task_06_Dataset/ # Specific Task 06 Data
│   └── Completion_Data.csv
└── PowerBI_Reports/               # Visual Analytics & Dashboards
    ├── PowerBIReports_IT23555594.pbix
    └── PowerBIReports_IT23555594.pdf
```

## 🚀 Key BI Features
* **Time Hierarchy:** Drill-down from Year > Quarter > Month > Day for seasonal trend analysis.
* **Cascading Slicers:** Dynamic regional filtering (Region > Hotel Type).
* **Advanced Analytics:** Gauge charts for Net Sales targets and Drill-through pages for hotel-specific details.
* **OLAP Operations:** Verified Slicing, Dicing, and Pivoting functionality via Excel connection.

## 📖 Data Dictionary
This dictionary explains the core components of `Hotel_DW`, bridging the gap between raw OLTP data and the Fact/Dimension model.

### Fact Table: `FactBookings`
| Attribute | Type | Description |
| :--- | :--- | :--- |
| **BookingKey** | PK (Int) | Surrogate Key for the unique booking transaction. |
| **Gross_Amount** | Decimal | The total price of the booking before discounts. |
| **Discount_Amt** | Decimal | Total discount value applied to the booking. |
| **Net_Sales** | Decimal | The actual revenue earned (Gross_Amount - Discount_Amt). |
| **ADR** | Decimal | Average Daily Rate; measures the average income per occupied room. |
| **Stay_Duration** | Int | Calculated column (Days) representing length of stay. |
| **Adult/Child Count** | Int | Quantitative measures for guest occupancy analysis. |

### Key Dimensions
| Dimension | Primary Attributes | Business Use |
| :--- | :--- | :--- |
| **DimHotel** | Hotel_Name, Reg, State, Types | Allows slicing by branch location and hotel category. |
| **DimDate** | FullDate, Year, Quarter, Month, Day | Supports the Time Hierarchy and trend analysis. |
| **DimCustomer** | Membership, Cus_Seg, Phone_No | Used to analyze loyalty tiers and customer demographics. |
| **DimRoom** | Room_Type | Analyzes product performance and inventory usage. |
| **DimSalesperson** | Rep_Name, Position | Analyzes sales performance across different regions and representatives. |

## ⚙️ ETL Workflow (SSIS)
The ETL process is designed to handle incremental updates and data quality:
- **Source Systems:** Excel files and CSVs are staged into a SQL Server environment.
- **Transformation:** Includes Lookups for surrogate key mapping, Derived Columns for `Net_Sales` calculation, and Data Conversions.
- **Fact Loading:** Implements an **Accumulating Snapshot Fact Table** logic for tracking booking lifecycles.

## 📊 Interaction & Visuals
The Power BI solution connects to the SSAS Cube via **Live Connection**:
- **Drill-Downs:** Enabled on the `DimDate` hierarchy (Year > Quarter > Month > Day).
- **Drill-Through:** Allows users to right-click a hotel and view detailed guest-level transaction data.
- **KPI Monitoring:** Uses Gauge charts to track performance against a 10% year-over-year growth target.


## 🛠️ Setup Instructions
1. **Restore Database:** Import `DataWarehouse_IT23555594.bak` (SQL DW) and `Hotel_OLTP_Source.bak` (OLTP Source) into your SQL Server instance.
2. **Restore Cube:** Use `CubeProject_IT23555594.abf` to restore the SSAS database if you are not deploying from the source.
3. **Open Solution:** Launch the `Hotel_DW_ETL.slnx` or relevant project files in Visual Studio (requires SSIS/SSAS extensions).
4. **Power BI:** Open `PowerBIReports_IT23555594.pbix`. *Note: Data Source settings may need adjustment to point to your local server.*

## 👨‍💻 Author
**Osanda Madugalle**  
[osandamadugalle.me](https://osandamadugalle.me) | [GitHub](https://github.com/OsandaMadugalle) | [LinkedIn](https://www.linkedin.com/in/osandamadugalle/) | [osandamadugalle@gmail.com](mailto:osandamadugalle@gmail.com)

## �📄 License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.