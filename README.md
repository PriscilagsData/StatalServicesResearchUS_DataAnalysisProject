# 📄 State Services Market Research (US)
### Contract Bidding & Opportunity Intelligence Dashboard

<p align="left">

<img src="https://upload.wikimedia.org/wikipedia/commons/c/cf/New_Power_BI_Logo.svg" width="40"/>
<img src="https://img.icons8.com/color/48/csv.png" width="40"/>
<img src="https://img.icons8.com/color/48/microsoft-excel-2019.png" width="40"/>
<img src="https://www.vectorlogo.zone/logos/snowflake/snowflake-icon.svg" width="40"/>
<img src="https://img.icons8.com/color/48/html-5--v1.png" width="40"/>
</p>

**Power BI • CSV • Excel • Snowflake • HTML visuals**

#### 📌 Executive Summary

- Analyzed historical US public service contracts and bidding opportunities
- Identified recurring vendors, agency demand patterns, and contract trends
- Built KPI-driven dashboards for opportunity tracking and urgency analysis
- Developed custom HTML visuals and interactive Power BI reporting

**Some data was modified for reasons of corporate confidentiality.**

## 🗃️ Relational model and BI report

### 🗄️ Data Model

<details>
<summary><b> 📑 Table details </b></summary>

<br>

- `Contracts`

| Column | Data Type | Description |
|:---|:---|:---|
| `Contract_ID` | Integer | Unique contract identifier |
| `Operation_Category` | Text | Operation / service category |
| `Record_Type` | Text | Record type |
| `State` | Text | US state |
| `Statal_Agency` | Text | Public entity requesting services |
| `Company` | Text | Awarded company |
| `Description` | Text | Contract description |
| `Amount` | Currency | Total contract value |
| `Start_Date` | Date | Contract start date |
| `End_Date` | Date | Contract end date |
| `Contract_Type` | Text | Contract clasification |


- `Opportunities`

| Column | Data Type | Description |
|:---|:---|:---|
| `Opportunity_ID` | Integer | Unique Opportunity identifier |
| `Operation_Category` | Text | Operation / service category |
| `Record_Type` | Text | Record type |
| `Opportunitie_Type` | Text | Opportunitie clasification |
| `Title` | Text | Contract title |
| `Description` | Text | Contract description |
| `AI_summary` | Text | Contract description by AI |
| `Posted_Date` | Date | Opportunity publication date |
| `Due_Date` | Date | Bid expiration date |
| `Statal_Agency` | Text | Contractor |
| `Estimated_Low_Value` | Currency | Lowest estimated contract value |
| `Estimated_High_Value` | Currency | Highest estimated contract value |
| `Country` | Text | Country name |
| `State` | Text | US state |
| `City` | Text | US city |
| `Zip` | Text | City zip code |

</details>

---

- `Relational model pbix after ETL and DAX measures`
  
<p align="center">
  <img src="relational_model_pbix.png" width="400">
</p>

## 💻 Power BI report


<p align="center">
  <img src="dashboard_pbix.jpg" width="300">
</p>

#### 📊 1st page: Contracts

<p align="center">
  <img src="contracts_page.jpg" width="1100">
</p>

#### 📊 2nd page: Opportunities

<p align="center">
  <img src="opportunities_page.jpg" width="1100">
</p>

### 🗃️ ETL and DAX code

<details>
<summary><b> ✒️ Main DAX measures </b></summary>

<br>
- 1
- 2


</details>

## 🗃️ Contact and info

* You are welcome to:

**Request services**, compose a friendly **e-mail**, **send requests** and **suggestions** to: <sidolipriscilag@gmail.com>
  
Priscila Gutierrez Sídoli - Linkdn  <a href="https://www.linkedin.com/in/priscilagsidoliiq/" target="_blank">
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/linkedin/linkedin-original.svg" width="15"/>
  </a>

> **If you found this project interesting, please consider giving the repository a ⭐ to support the work.**

