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
* `/01_Documentation`: Final PDF reports for Assignment 01 and 02.
* `/02_Database_Backup`: `Hotel_DW.bak` SQL Server backup file.
* `/03_Integrated_Solution`: Unified Visual Studio solution containing **SSIS (ETL)** and **SSAS (Cube)** projects.
* `/04_Visualizations`: Power BI Dashboard (`.pbix`) and Excel OLAP demo.

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
| **DimRoom** | Room_Type, Meal_Plan | Analyzes product performance and inventory usage. |


## 🛠️ Setup Instructions
1. **Restore Database:** Import `Hotel_DW.bak` into your SQL Server instance.
2. **Open Solution:** Launch the `.sln` file in Visual Studio (requires SSIS/SSAS extensions).
3. **Power BI:** Open the `.pbix` file. *Note: Data Source settings may need adjustment to point to your local server (LAPTOP-LENOVO).*

## 📄 License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.