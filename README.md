
# 🏥 Hospital Waiting List Dashboard (2018–2021)

A Power BI-based interactive dashboard that analyzes hospital waiting list trends for both **inpatients** and **outpatients** over four years (2018–2021). The dashboard supports decision-making by helping stakeholders track the **current status**, explore **historical trends**, and conduct **granular analysis** by specialty and age profile.

## 🎯 Objective

- Track current status of hospital patient waiting lists
- Analyze monthly trends in inpatient and outpatient data
- Deep-dive into specialties and age profiles
- Provide a dynamic summary and detailed visual views for all stakeholders

## 🗃️ Data Scope

- **Years Covered**: 2018 to 2021
- **Data Type**: Inpatient & Outpatient waiting list statistics
- **Metrics**:
  - Total Patients on Wait List
  - Average & Median Wait List Sizes
  - Age Profile & Time Band Classification
  - Specialty-level Aggregation

## 📁 Dataset Files

- `IN_WL 2019.csv` – Year 2019 data
- `IN_WL 2020.csv` – Year 2020 data
- *(Other years assumed to follow similar structure)*

## 🔗 Data Integration

Data is imported into Power BI using the **Folder Connector**, which supports dynamic refreshes as files in the folder are updated. This enables automation and scalable deployment.

Supported data connectors in Power BI (used or available for future extension):

- CSV / Excel
- Folder
- SQL Server / Any RDBMS
- Power BI Services
- SharePoint, Web APIs, JSON
- Cloud platforms (Azure, AWS, GCP)

## 🛠️ Data Transformation Process

Performed using **Power Query Editor** in Power BI:

- Renamed columns for consistency across datasets
- Rearranged columns and standardized structure
- Appended inpatient and outpatient tables into a unified `All_Data` table
- Cleaned redundant or inconsistent values (e.g., `"18+ months"` vs `"18 month +"`)
- Used `Trim`, `Replace`, `Custom Columns` for data cleanup
- Integrated with a **Specialty Mapping** table for grouping categories

## 📐 Data Modelling

- Created relationships between `All_Data` and `Specialty Mapping` tables
- Modeled using `Case_Type`, `Specialty_Name`, `Age_Profile`, and `Time_Band`
- Enabled efficient slicers and filters across visuals

## 📊 Visualization Blueprint

### 🔹 Summary Page

- Key KPIs: Latest Month Wait List, Previous Year Comparison
- Dynamic Chart Titles (Average vs Median)
- Charts:
  - Doughnut Chart (Case Type Split)
  - Clustered Column Chart (Top Specialties)
  - Line Chart (Trend over Time)
- Slicers for `Archive_Date`, `Specialty`, and `Case_Type`

### 🔹 Detailed Page

- Matrix Table: `Archive_Date`, `Specialty_Name`, `Age_Profile`, `Time_Band`, and `Total`
- Tooltip Page for enhanced hover insights

### 🔹 Interactivity & UX Enhancements

- Calculation method slicer (Average vs Median)
- Dynamic titles and chart visibility
- Custom tooltip page integration
- Clean layout using background images and color themes from Adobe Color

## 🧮 Measures (DAX Examples)

```DAX
Latest Month Wait List = CALCULATE(SUM(All_Data[Total]), All_Data[Archive_Date] = MAX(All_Data[Archive_Date])) + 0

PY Latest Month Wait List = CALCULATE(SUM(All_Data[Total]), All_Data[Archive_Date] = EDATE(MAX(All_Data[Archive_Date]), -12)) + 0

Median Wait List = MEDIAN(All_Data[Total])
Average Wait List = AVERAGE(All_Data[Total])

Avg/Med Wait List = SWITCH(VALUES('Calculation Method'[Calc Method]), "Average", [Average Wait List], "Median", [Median Wait List])
```

## 📌 Key Insights (Example)

- Significant waitlist spikes in early 2020—correlated with pandemic disruptions
- Specialty-level disparities in patient load
- Outpatient demand more volatile than inpatient

## ✅ Testing & Deployment

- UAT conducted to validate data accuracy and interactivity
- Row-Level Security (RLS) implemented for secure sharing via Power BI Service
- Regular refresh enabled via folder-based data source

## 📷 Screenshots

*(Optional: Upload and embed visuals of key dashboard views here)*

## 👤 Author

- **Your Name**
- [GitHub Profile](https://github.com/mukulgarg0097)

## 📄 License

This project is open-source under the MIT License.
