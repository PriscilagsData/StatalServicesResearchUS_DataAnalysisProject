## 📄 State Services Market Research (US)
### Contract Bidding & Opportunity Intelligence Dashboard

<p align="left">

<img src="https://upload.wikimedia.org/wikipedia/commons/c/cf/New_Power_BI_Logo.svg" width="40"/>
<img src="https://img.icons8.com/color/48/csv.png" width="40"/>
<img src="https://img.icons8.com/color/48/microsoft-excel-2019.png" width="40"/>
<img src="https://www.vectorlogo.zone/logos/snowflake/snowflake-icon.svg" width="40"/>
<img src="https://img.icons8.com/color/48/html-5--v1.png" width="40"/>
</p>
<sub> Power BI • Excel • CSV • Snowflake • HTML visuals </sub>

#### 📌 Executive Summary

<sub>  - Analyzed historical US public service contracts and bidding opportunities</sub>

<sub>  - Identified recurring vendors, agency demand patterns, and contract trends</sub>

<sub>  - Built KPI-driven dashboards for opportunity tracking and urgency analysis</sub>

<sub>  - Developed custom HTML visuals and interactive Power BI reporting</sub>

**Some data was modified for reasons of corporate confidentiality.**

---

### 🗃️ Data ETL and BI report

#### 🗄️ Data Model

- `Contracts`

| Column | Data Type | Description |
|:---|:---|:---|
| `Contract_ID` | Integer | Unique contract identifier |
| `Operation_Category` | Text | Awarded company |
| `Record_Type` | Text | Awarded company |
| `State` | Text | US state |
| `Statal_Agency` | Text | Public entity requesting services |
| `Company` | Text | Awarded company |
| `Description` | Text | Contract description |
| `Amount` | Currency | Total contract value |
| `Start_Date` | Date | Contract start date |
| `End_Date` | Integer | Contract duration |
| `Contract_Type` | Text | Awarded company |

- `Opportunities`

| Column | Data Type | Description |
|:---|:---|:---|
| `Opportunity_ID` | Integer | Opportunity identifier |
| `Operation_Category` | Text | Awarded company |
| `Record_Type` | Text | Awarded company |
| `Opportunitie_Type` | Text | Awarded company |
| `Title` | Text | Contract title |
| `Description` | Text | Contract description |
| `AI_summary` | Text | Contract description by AI |
| `Posted_Date` | Date | Opportunity publication date |
| `Due_Date` | Date | Bid expiration date |
| `Statal_Agency` | Text | Active / Expired |
| `Estimated_Low_Value` | Currency | Estimated contract value |
| `Estimated_High_Value` | Currency | Estimated contract value |
| `Country` | Text | Country name |
| `State` | Text | US state |
| `City` | Text | US city |
| `Zip` | Text | City zip code |


#### 🗄️ Power BI report

<p align="center">
  <img src="dashboard_pbix.jpg" width="700">
</p>







