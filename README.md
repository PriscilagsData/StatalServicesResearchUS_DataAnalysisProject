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

📄 **[Download full Power BI (PDF)](https://github.com/PriscilagsData/StatalServicesResearchUS_DataAnalysisProject/blob/main/public_services_PowerBI.pdf)**

<p align="center">
  <img src="dashboard_pbix.jpg" width="300">
</p>

#### 📊 `Contracts`

<p align="center">
  <img src="contracts_page.jpg" width="1100">
</p>

Its purpose is to quickly and easily visualize the **number of contracts** in the database, considering different **States**, **statal agencies**, and **service providers**, to gain insights into **trends and estimated amounts**, **average tickets**, and to identify **frequently contracted companies**. The analysis covers the period **2018-2025**, based on the available database.

#### 📊 `Opportunities`

<p align="center">
  <img src="opportunities_page.jpg" width="1100">
</p>

This section analyzes **contract opportunities**, primarily considering **State**, **government agency**, and **expiration dates**. It displays the **updated status of each contract**: expired, active, and urgent (expiring within the next 7 days). Each opportunity includes a **contract description** and an **AI-generated summary**.
Additionally, **contracting peaks** can be identified through a monthly trend analysis.


### 🗃️ DAX Measures

<details>
<summary><b> ⚡ Main DAX Measures </b></summary>
<br>

- Interactive HTML Content visualization with Recurrent companies (with more than 1 contract within 2018-2025)

```DAX
infoHTML2 = 
VAR BlueBar = "#3b82f6" 
VAR BackgActiveCard = "rgba(30, 58, 138, 0.4)" 
VAR BackgIconCircle = "rgba(255, 255, 255, 0.1)" 
VAR BackgListDetail = "#141a29"
VAR WhiteText = "#e0e0e0"
VAR GreyText = "#e0e0e0"
VAR DividerLine = "rgba(255,255,255,0.08)" 

-- 1. Header
VAR HeaderHTML = 
    "<div style='font-family: Segoe UI, sans-serif; color: " & WhiteText & "; margin-bottom: 10px; padding-left: 5px;'>" &
        "<div style='font-size: 18px; font-weight: bold;'>Recurrent companies</div>" &
    "</div>"

-- 2. List
VAR CardsList = 
    CONCATENATEX(
        FILTER(
            VALUES(contracts[Company]), 
            [Award_Quantity] > 1
        ),
        "<details style='margin-bottom: 6px; font-family: Segoe UI, sans-serif; border-radius: 8px; overflow: hidden; background: " & BackgActiveCard & "; position: relative; border: 1px solid rgba(255,255,255,0.05);'>" &
            
            -- BAR (2px)
            "<div style='position:absolute; left:0; top:0; bottom:0; width:2px; background:" & BlueBar & ";'></div>" &

            "<summary style='list-style: none; cursor: pointer; padding: 12px 15px 12px 20px; display: flex; align-items: center; color: " & WhiteText & ";'>" &
                "<div style='background-color: " & BackgIconCircle & "; border-radius: 50%; min-width: 38px; height: 38px; margin-right: 15px; display: flex; align-items: center; justify-content: center;'>" &
                    "<svg width='20' height='20' viewBox='0 0 24 24' fill='none' stroke='white' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'><path d='M7 21l-4-4 4-4M17 3l4 4-4 4M3 17h18M21 7H3'/></svg>" &
                "</div>" &
                "<div style='flex-grow: 1;'>" &
                    "<div style='font-size: 16px; font-weight: 700; text-transform: uppercase;'>" & contracts[Company] & "</div>" &
                    "<div style='font-size: 13px; color: " & GreyText & ";'>" & [Award_Quantity] & " contracts - Total: " & FORMAT([SumAmount], "$ #,0") & "</div>" &
                "</div>" &
                "<div style='font-size: 15px; font-weight: bold; opacity: 0.8;'>" & [Award_Quantity] & "x ▼</div>" &
            "</summary>" &

            -- CONTRACT LIST
            "<div style='background-color: " & BackgListDetail & "; padding: 0 5px;'>" &
                CONCATENATEX(
                    CALCULATETABLE(contracts),
                    VAR DescText = contracts[Description]
                    VAR Duration = [AwardPeriod_days]
                    VAR StateBadge = contracts[State]
                    
                    VAR DescHTML = IF(DescText = "Nan" || ISBLANK(DescText), "", "<div style='font-size: 14px; color: " & WhiteText & "; font-weight: 500; margin: 5px 0;'>" & DescText & "</div>")
                    
                    RETURN
                    "<div style='padding: 14px 18px; border-bottom: 1px solid " & DividerLine & "; display: flex; justify-content: space-between; align-items: center;'>" &
                        "<div style='flex-grow: 1;'>" &
                            "<div style='display: flex; align-items: center; gap: 10px;'>" &
                                "<span style='font-size: 11px; padding: 2px 6px; border-radius: 4px; background: #ffffff; color: #000; font-weight: 800;'>" & StateBadge & "</span>" &
                                "<span style='font-size: 14px; color: " & GreyText & "; font-weight: 600;'>" & contracts[Company] & "</span>" &
                            "</div>" &
                            
                            DescHTML &
                            
                            "<div style='font-size: 13px; color: " & GreyText & "; margin-top: 3px;'>" &
                                "Start: " & FORMAT(contracts[Start_date], "dd MMM yyyy") & 
                                IF(NOT ISBLANK(contracts[End_date]), "  •  Fin: " & FORMAT(contracts[End_date], "dd MMM yyyy"), "") &
                                IF(NOT ISBLANK(Duration), "  •  <span style='color:" & BlueBar & "; font-weight: bold;'>" & Duration & " days</span>", "") &
                            "</div>" &
                        "</div>" &
                        
                        "<div style='font-size: 17px; font-weight: bold; color: " & WhiteText & ";'>$" & FORMAT(contracts[Amount], "#,0") & "</div>" &
                    "</div>",
                    "",
                    contracts[Start_date], DESC
                ) &
            "</div>" &
        "</details>",
        "", 
        [Award_Quantity], DESC
    )

RETURN
    "<div style='padding: 2px;'>" & HeaderHTML & CardsList & "</div>"
```

- Interactive HTML Content visualization with the opportunities status and details

```DAX
OppTableHTML = 
VAR TextoGrisCasiBlanco = "#e0e0e0" 
VAR TextoGrisAzulado = "#8e9aaf" 
VAR AzulElectrico = "#3b82f6" 
VAR BordeCard = "rgba(255, 255, 255, 0.20)" 
VAR FondoHeader = "#0b0e14"
VAR FondoDetalle = "#141822"

-- 1. Header con proporciones ajustadas
VAR Header = 
"<div style='font-family: Segoe UI, sans-serif; display: flex; background-color: " & FondoHeader & "; padding: 15px 10px; border-bottom: 2px solid " & AzulElectrico & "; font-size: 14px; font-weight: 800; color: " & AzulElectrico & "; text-transform: uppercase;'>
    <div style='flex: 4;'>Title</div>
    <div style='flex: 3;'>Agency</div>
    <div style='flex: 1.5;'>Due Date</div>
    <div style='flex: 1; text-align: center;'>Status</div>
    <div style='width: 35px;'></div>
</div>"

-- 2. Body con Accordion
VAR TableRows = 
CONCATENATEX(
    TOPN(1000, opportunities, [Due_Date], DESC),
    
    VAR DaysDiff = DATEDIFF(TODAY(), [Due_Date], DAY)
    VAR StatusText = IF(DaysDiff < 0, "EXPIRED", "ACTIVE")
    VAR StatusColor = IF(DaysDiff < 0, "#ef4444", "#22c55e")
    
    RETURN
    "<details style='font-family: Segoe UI, sans-serif; border-bottom: 1px solid " & BordeCard & "; background-color: #0b0e14;'>
        
        <summary style='list-style: none; cursor: pointer; padding: 12px 10px; display: flex; align-items: center;'>
            
            <!-- TITLE (Flex 4) -->
            <div style='flex: 4; padding-right: 20px;'>
                <div style='font-weight: 700; font-size: 13px; color: white;'>" & SUBSTITUTE([Title], [City], "") & "</div>
            </div>

            <!-- AGENCY (Flex 3) -->
            <div style='flex: 3; padding-right: 15px;'>
                <div style='font-size: 13px; font-weight: 600; color: white;'>" & COALESCE(opportunities[Statal_Agency], "---") & "</div>
                <div style='font-size: 14px; color: " & TextoGrisAzulado & ";'>" & 
                    COALESCE([City], "---") & ", " & COALESCE([State], "---") & 
                "</div>
            </div>

            <!-- DUE DATE (Flex 1.5) -->
            <div style='flex: 1.5;'>
                <div style='font-size: 13px; font-weight: 600; color: white;'>" & FORMAT([Due_Date], "MMM dd, yyyy") & "</div>
                <div style='font-size: 13px; color: " & TextoGrisAzulado & ";'>" & 
                    IF(DaysDiff < 0, "Expired " & ABS(DaysDiff) & " d. ago", DaysDiff & " d. left") & 
                "</div>
            </div>

            <!-- STATUS (Flex 1) -->
            <div style='flex: 1; text-align: center;'>
                <span style='background: " & StatusColor & "; color: white; padding: 4px 8px; border-radius: 12px; font-size: 10px; font-weight: bold;'>" & StatusText & "</span>
            </div>

            <div style='width: 35px; text-align: right; color: " & TextoGrisAzulado & "; font-size: 12px;'>▼</div>
        </summary>

        <!-- DETALLE INTERNO (Sin cambios en proporciones para lectura vertical) -->
        <div style='padding: 20px; background-color: " & FondoDetalle & "; border-top: 1px dashed " & BordeCard & ";'>
            <div style='display: flex; justify-content: space-between; margin-bottom: 20px;'>
                <div style='flex: 1;'>
                    <div style='color: " & TextoGrisAzulado & "; font-size: 11px; text-transform: uppercase; font-weight: 600;'>Posting Date</div>
                    <div style='color: white; font-size: 14px; font-weight: 700; margin-top: 5px;'>" & FORMAT(opportunities[Posted_Date], "MMMM d, yyyy") & "</div>
                </div>
                <div style='flex: 1;'>
                    <div style='color: " & TextoGrisAzulado & "; font-size: 11px; text-transform: uppercase; font-weight: 600;'>Due Date</div>
                    <div style='color: white; font-size: 14px; font-weight: 700; margin-top: 5px;'>" & FORMAT([Due_Date], "MMMM d, yyyy") & "</div>
                </div>
                <div style='flex: 1;'>
                    <div style='color: " & TextoGrisAzulado & "; font-size: 11px; text-transform: uppercase; font-weight: 600;'>Estimated Value</div>
                    <div style='color: white; font-size: 16px; font-weight: 800; margin-top: 5px;'>" & FORMAT([val_avg_low], "$ #,0") & " - " & FORMAT([val_avg_high], "$ #,0") & "</div>
                </div>
            </div>
            <div style='margin-bottom: 20px;'>
                <div style='color: white; font-size: 14px; font-weight: 700; margin-bottom: 5px;'>Description</div>
                <div style='color: " & TextoGrisCasiBlanco & "; font-size: 12px; line-height: 1.5;'>" & COALESCE([Description], "No description available.") & "</div>
            </div>
            <div style='background: rgba(59, 130, 246, 0.1); padding: 15px; border-left: 4px solid " & AzulElectrico & "; border-radius: 4px;'>
                <div style='color: " & AzulElectrico & "; font-size: 10px; font-weight: 800; text-transform: uppercase; margin-bottom: 5px;'>AI Summary</div>
                <div style='color: " & TextoGrisCasiBlanco & "; font-size: 12px; line-height: 1.4; font-style: italic;'>" & 
                    COALESCE([AI_summary], "No AI summary available.") & 
                "</div>
            </div>
        </div>
    </details>",
    "",
    [Due_Date], DESC
)

RETURN
"<div style='background-color: #080c17; border-radius: 8px; overflow: hidden;'>" & Header & TableRows & "</div>"
```
</details>

## 📨 Contact and info

* You are welcome to:

**Request services**, compose a friendly **e-mail**, **send requests about ETL** and **suggestions** to: <sidolipriscilag@gmail.com>
  
Priscila Gutierrez Sídoli - Linkdn  <a href="https://www.linkedin.com/in/priscilagsidoliiq/" target="_blank">
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/linkedin/linkedin-original.svg" width="15"/>
  </a>

> **If you found this project interesting, please consider giving the repository a ⭐ to support the work.**

