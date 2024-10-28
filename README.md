# Procurement Tracking System Documentation

## Table of Contents
- [Introduction](#introduction)
- [Purpose](#purpose)
- [Objectives](#objectives)
- [System Overview](#system-overview)
- [Target Audience](#target-audience)
- [Data Model Structure](#data-model-structure)
- [Dashboard Layout & Navigation](#dashboard-layout--navigation)
- [Data Definition](#data-definition)
- [Calculated Measures](#calculated-measures)
- [Parameters](#parameters)

## Introduction

This document serves as a guide to the **Procurement System Dashboard** developed for *Enterprise Manufacturers Ltd.* The purpose of the dashboard is to centralize and analyze supplier quality data, allowing the company to identify patterns and trends in vendor, plant, and material performance, as well as the impacts of defects.

Given the absence of a procurement system, the dashboard is designed to address inconsistencies between different plants and vendors, providing insights into defective quantities, downtime, and the overall performance of suppliers.
## Purpose

*Enterprise Manufacturers Ltd.* needed a solution to validate the quality of goods supplied by vendors and track the consistency of material quality across multiple plants. The goal of this syste, is to provide concise and informed insights to the management team to optimize procurement decisions, reduce downtime, and minimize manufacturing defects.

## Objectives

The dashboard aims to solve the following business problems:
- Help the management team make informed procurement decisions.
- Centralize supplier quality data from various plants and vendors.
- Identify vendors and plants that contribute the most to defects and downtime.
- Provide insights on material and vendor performance across different locations.

## System Overview

The **Procurement Tracking System** enables monitoring of the quality of materials supplied by vendors as well as the performance of the company's manufacturing plants. Each page of the system contains key performance indicators (KPIs) that provide insights into both vendor and plant efficiency. Users can apply various parameters and filters to gain a comprehensive overview and drill down into specific areas for deeper analysis.

## Target Audience

**Management Team**: This dashboard is meant for decision makers who need to monitor and improve supplier and plant efficiency.

## Data Sources

- **Excel Sheets**

## Data Model Structure

- **Fact Table**: Contains essential production and supplier-related data.
  - **Fields**:
    - Date
    - Vendor
    - Plant Location
    - Category
    - Material Type
    - Defect Type
    - Defect
    - Total Defect Qty
    - Total Downtime Minutes

- **Dimension Tables**:
  - **Plant**: `PlantID`, `Plant Location`
  - **Vendor**: `VendorID`, `Vendor`
  - **Procurement Category**: `CategoryID`, `Category`
  - **Material**: `Material ID`, `Material Type`
  - **Defect Type**: `Defect Type ID`, `Defect Type`
  - **Defect**: `Defect ID`, `Defect`

---

## Dashboard Layout & Navigation

### 1. Home Page
![alt text](https://github.com/KingTheAnalyst/Procurement-Tracking-System/blob/main/Home%20Page.png "Home Page")
**Purpose**: Provides an entry point to navigate the Supplier Quality Performance dashboard. It offers a brief overview of the dashboard's purpose with easy access to key performance indicators and analysis pages.

**Features**:
- **Company Name**: "Enterprise Manufacturers Ltd"
- **Dashboard Title**: "Supplier Quality Performance Dashboard"
- **Description**: Overview of the dashboard’s objective.
- **Navigation Tabs**:
  - Landing Page
  - Overview
  - Vendor
  - Plant
  - Material
  - Impact

### 2. Overview
This dashboard page provides a comprehensive view of production defects and downtime, helping users monitor key metrics and trends.
![alt text](https://github.com/KingTheAnalyst/Procurement-Tracking-System/blob/main/Overview.png "Overview Page")
**Components**:
- **Top Metrics Panel**: Displays total defects, downtime hours, and downtime costs with month-over-month (MoM) and year-over-year (YoY) comparisons.
- **Monthly Trend Chart**: Visualizes defects or downtime trends over time.
- **Worst Performers**: Highlights underperforming vendors, plants, defect types, and categories.
- **Defect Impact Summary**: Categorizes impacts into Impact, No Impact, and Rejected.

**Interactive Features**:
- Toggle between "Defects" and "Downtime" to update charts.
- Adjust "Downtime Cost per Hour" for financial impact visualization.
- Filters for time periods, vendors, plants, and defect types

---
### 3. Vendor Performance Dashboard
![alt text](https://github.com/KingTheAnalyst/Procurement-Tracking-System/blob/main/Vendor.png "Vendor's Performance Dashboard")
**Purpose**: Provides insights into vendor performance by tracking defect quantities, downtime hours, and impacts.

**Components**:
- **Defect Quantity by Vendor** (Bar Chart): Shows top/bottom vendors by performance.
- **Impact Analysis** (Scatter Plot): Highlights high, medium, and low-risk vendors.
- **Vendor Performance Table**: Lists vendors with metrics like Impact, No Impact, and Rejected.

**Interactive Features**:
- Toggle between top/bottom performers.
- Filters for time periods, vendors, plants, and defect types

---
### 4. Plant Performance Dashboard
![alt text](https://github.com/KingTheAnalyst/Procurement-Tracking-System/blob/main/Plant.png "Plant's Performance Page")
**Purpose**: Tracks plant locations and their contribution to defects and downtime, supporting geographical and quantitative analysis of plant efficiency.

**Components**:
- **Defect Quantity by Plant** (Bar Chart): Shows defects across plant locations.
- **Geographical Mapping**: Maps plant locations and defect quantities.
- **Plant Performance Table**: Lists plants with KPIs such as defects, downtime impact, and rejected products.

**Interactive Features**:
- Toggle between top/bottom performing plants.
- Filters for time periods, vendors, plants, and defect types

---
### 5. Material Performance Dashboard
![alt text](https://github.com/KingTheAnalyst/Procurement-Tracking-System/blob/main/Material.png "Materials Performance Page")
**Purpose**: Tracks downtime hours related to various material types, defect types, and categories, helping assess materials and defects impacting production.

**Components**:
- Toggle Between Views: Switch between defect quantity and downtime hours metrics.
- **Downtime Hours by Material Type** (Bar Chart): Downtime associated with material types.
- **Downtime Hours by Defect** (Bar Chart): Lists defects causing the most downtime.
- **Downtime Hours by Category** (Bar Chart): Categorizes downtime (e.g., mechanicals, logistics).
- **Monthly Trend Line Chart**: Tracks monthly downtime trends across categories.

---

### 6. Downtime Impact Dashboard
![alt text](https://github.com/KingTheAnalyst/Procurement-Tracking-System/blob/main/Downtime%20Impact.png "Downtime Impact Page")
**Purpose**: Provides an overview of downtime costs and associated defects across vendors, plants, and materials.

**Components**:
- **Downtime Cost by Day and Month** (Table): Breakdown of daily and monthly downtime costs.
- **Monthly Downtime Cost** (Bar Chart): Visualizes monthly downtime costs.
- **Vendor and Plant Performance** (Table): Links downtime and defects to vendors and plants.
- **Vendor and Material Downtime Analysis** (Table): Breaks down downtime by vendor and materials.

**Interactive Features**:
- Filters for time periods, vendors, plants, and defect types.

---
# Data Definition

1. **Category**: Record Category
2. **Date**: Date of record
3. **Defect**: The specific defect
4. **Defect Type**: The type of defect (Impact, No impact, or Rejected)
5. **Material Type**: Type of material supplied

---

# Calculated Measures

1. **Defect Qty PY**:
   - **Formula**:
     ```DAX
     CALCULATE([Total Defect Qty], SAMEPERIODLASTYEAR('Date'[Date]))
     ```
   - **Description**: This measure calculates the total quantity of defects for the same period in the previous year (PY). It uses the `SAMEPERIODLASTYEAR` function to compare the current period to the corresponding period one year ago.

2. **MOM Defect Trend Color**:
   - **Formula**:
     ```DAX
     IF([MOMGrowthDefectQty] > 0, "Red", "Green")
     ```
   - **Description**: This measure changes the color of the Month-over-Month (MOM) defect trend based on whether there is growth. If the MOM defect growth is positive, it returns "Red"; otherwise, it returns "Green."

3. **MOM Defects Trend Icon**:
   - **Formula**:
     ```DAX
     VAR Positive_Icon = UNICHAR(9650)
     VAR Negative_Icon = UNICHAR(9660)
     VAR Trend_Icon = IF([MOMGrowthDefectQty] > 0, Positive_Icon, Negative_Icon)
     VAR DisplayTrend = Trend_Icon & " " & FORMAT([MOMGrowthDefectQty], "0.00%")
     RETURN DisplayTrend
     ```
   - **Description**: This measure displays an icon (up arrow for positive growth, down arrow for negative) next to the MOM growth percentage. It formats the growth rate as a percentage and attaches the appropriate icon.

4. **MOMGrowthDefectQty**:
   - **Formula**:
     ```DAX
     DIVIDE([Total Defect Qty] - [Total Defect Qty PM], [Total Defect Qty PM])
     ```
   - **Description**: This measure calculates the growth rate of the total defect quantity compared to the previous month (PM). It divides the difference between the current and previous month's defect quantities by the previous month's defect quantity.

5. **Total Defect Qty**:
   - **Formula**:
     ```DAX
     SUM('Fact Table'[Total Defect Qty])
     ```
   - **Description**: This measure calculates the total number of defects by summing up the defect quantities in the fact table.

6. **Total Defect Qty PM**:
   - **Formula**:
     ```DAX
     CALCULATE([Total Defect Qty], PARALLELPERIOD('Date'[Date], -1, MONTH))
     ```
   - **Description**: This measure calculates the total quantity of defects for the previous month (PM), using `PARALLELPERIOD` to shift the date back by one month.

7. **YOY Defect Trend Color**:
   - **Formula**:
     ```DAX
     IF([YOYGrowthDefectQty] > 0, "Red", "Green")
     ```
   - **Description**: Similar to the MOM trend color, this measure changes the color based on the Year-over-Year (YOY) defect growth. Red indicates positive growth, and green indicates negative growth.

8. **YOY Defects Trend Icon**:
   - **Formula**:
     ```DAX
     VAR Positive_Icon = UNICHAR(9650)
     VAR Negative_Icon = UNICHAR(9660)
     VAR Trend_Icon = IF([YOYGrowthDefectQty] > 0, Positive_Icon, Negative_Icon)
     VAR DisplayTrend = Trend_Icon & " " & FORMAT([YOYGrowthDefectQty], "0.00%")
     RETURN DisplayTrend
     ```
   - **Description**: This measure displays an icon (up/down arrow) based on the YOY defect growth rate, followed by the percentage change.

9. **YOYGrowthDefectQty**:
   - **Formula**:
     ```DAX
     DIVIDE([Total Defect Qty] - 'Defect Quantity'[Defect Qty PY], 'Defect Quantity'[Defect Qty PY])
     ```
   - **Description**: This calculates the YOY growth rate for total defect quantities by comparing the current total defect quantity with that of the same period last year.

10. **Total Defect Reports**:
    - **Formula**:
      ```DAX
      COUNTROWS('Fact Table')
      ```
    - **Description**: Counts the total number of defect reports in the fact table.

11. **Impact Defect Type**:
    - **Formula**:
      ```DAX
      VAR Impact = CALCULATE(COUNT('Fact Table'[DefectID]), KEEPFILTERS('Fact Table'[Defect Type] = "Impact"))
      VAR Defects = COUNT('Fact Table'[DefectTypeID])
      RETURN DIVIDE(Impact, Defects)
      ```
    - **Description**: This calculates the proportion of defects categorized as "Impact" out of the total defects.

12. **No Impact Defect Type**:
    - **Formula**:
      ```DAX
      VAR NoImpact = CALCULATE(COUNT('Fact Table'[DefectID]), KEEPFILTERS('Fact Table'[Defect Type] = "No Impact"))
      VAR Defects = COUNT('Fact Table'[DefectTypeID])
      RETURN DIVIDE(NoImpact, Defects)
      ```
    - **Description**: Calculates the percentage of defects classified as "No Impact."

13. **Rejected Defect Type**:
    - **Formula**:
      ```DAX
      VAR Rejected = CALCULATE(COUNT('Fact Table'[DefectID]), KEEPFILTERS('Defect Type'[Defect Type] = "Rejected"))
      VAR Defects = COUNT('Fact Table'[DefectTypeID])
      RETURN DIVIDE(Rejected, Defects)
      ```
    - **Description**: Calculates the percentage of defects classified as "Rejected."

14. **MOM Downtime Growth Icon**:
    - **Formula**:
      ```DAX
      VAR Positive_Icon = UNICHAR(9650)
      VAR Negative_Icon = UNICHAR(9660)
      VAR Trend_Icon = IF([MOMGrowthDowntime] > 0, Positive_Icon, Negative_Icon)
      VAR DisplayTrend = Trend_Icon & " " & FORMAT([MOMGrowthDowntime], "0.00%")
      RETURN DisplayTrend
      ```
    - **Description**: Displays an icon (up/down arrow) based on Month-over-Month downtime growth and appends the growth percentage.

15. **MOMGrowthDowntime**:
    - **Formula**:
      ```DAX
      DIVIDE([Total DownTime(Hours)] - [Total Downtime Hours PM], [Total Downtime Hours PM])
      ```
    - **Description**: Calculates the growth rate of downtime hours compared to the previous month (PM).

16. **Total Downtime Hours PM**:
    - **Formula**:
      ```DAX
      CALCULATE([Total DownTime(Hours)], PARALLELPERIOD('Date'[Date], -1, MONTH))
      ```
    - **Description**: Total downtime hours for the previous month.

17. **Total Downtime PY**:
    - **Formula**:
      ```DAX
      CALCULATE([Total DownTime(Hours)], SAMEPERIODLASTYEAR('Date'[Date]))
      ```
    - **Description**: Total downtime hours for the same period last year (PY).

18. **Total Downtime (Hours)**:
    - **Formula**:
      ```DAX
      [Total Downtime(Minutes)] / 60
      ```
    - **Description**: Converts total downtime from minutes to hours.

19. **Total Downtime (Minutes)**:
    - **Formula**:
      ```DAX
      SUM('Fact Table'[Total Downtime Minutes])
      ```
    - **Description**: Total downtime in minutes.

20. **YOY Downtime Trend Color**:
    - **Formula**:
      ```DAX
      IF([YOYGrowthDowntime] > 0, "Red", "Green")
      ```
    - **Description**: Changes the color based on Year-over-Year downtime growth (red for growth, green for reduction).

21. **YOY Downtime Trend Icon**:
    - **Formula**:
      ```DAX
      VAR Positive_Icon = UNICHAR(9650)
      VAR Negative_Icon = UNICHAR(9660)
      VAR Trend_Icon = IF([YOYGrowthDowntime] > 0, Positive_Icon, Negative_Icon)
      VAR DisplayTrend = Trend_Icon & " " & FORMAT([YOYGrowthDowntime], "0.00%")
      RETURN DisplayTrend
      ```
    - **Description**: Displays a trend icon and YOY downtime growth percentage.

22. **YOYGrowthDowntime**:
    - **Formula**:
      ```DAX
      DIVIDE([Total DownTime(Hours)] - [Total Downtime PY], [Total Downtime PY])
      ```
    - **Description**: Year-over-Year growth of downtime hours.

23. **Downtime Cost per Hour**:
    - **Formula**:
      ```DAX
      [Total DownTime(Hours)] * 'Downtime Cost Parameter'[Downtime Cost Value]
      ```
    - **Description**: Calculates total cost of downtime based on hours and defined cost per hour.

24. **Defect Cost per Defect**:
    - **Formula**:
      ```DAX
      [Total Defect Qty] * 'Defect Cost Parameter'[Defect Cost Value]
      ```
    - **Description**: Calculates the total cost associated with defects.

---
## Parameters

1. **Top N Parameter**
   - **Formula**:
     ```DAX
     [Top N Parameter] = GENERATESERIES(0, 20, 1)
     Top N Parameter Value = SELECTEDVALUE('Top N Parameter'[Top N Parameter], 10)
     ```
   - **Description**: This parameter generates a series of values ranging from 0 to 20, allowing users to select the "Top N" number of plants or vendors they wish to focus on based on defect quantity or downtime hours. The default value is set to 10 but can be adjusted by the user.
   - **Effect on Data**: It filters the data to display only the top or bottom N plants or vendors based on the selected metric (defect quantity or downtime hours).
   - **User Interaction**: Users can select their desired ranking (e.g., top 5, top 10) which influences the visualizations presented in the report.

2. **Downtime Cost Parameter**
   - **Formula**:
     ```DAX
     Downtime Cost Value = SELECTEDVALUE('Downtime Cost Parameter'[Downtime Cost], 10)
     Downtime Cost Parameter = GENERATESERIES(0, 20, 1)
     ```
   - **Description**: This parameter creates a series of values from 0 to 20, representing the downtime cost per hour. Users can modify this value according to actual business data.
   - **Effect on Data**: Adjusting the downtime cost value will directly influence all measures related to downtime costs, including Total Downtime Cost and Month-Over-Month/Year-Over-Year Downtime Cost, which will recalculate accordingly.
   - **User Interaction**: Users can enter or select a specific cost per hour (e.g., $10/hour or $15/hour), and the entire report will update to reflect these changes in downtime cost metrics.

3. **Plant Parameter**
   - **Formula**:
     ```DAX
     Plant Parameter = {
         ("Defect Quantity", NAMEOF('Rank Measures'[Rank_Plant_by_Defect_Qty]), 0),
         ("Downtime Hours", NAMEOF('Rank Measures'[Rank_Plant_by_Downtime_Hours]), 1)
     }
     ```
   - **Description**: This parameter allows users to toggle between analyzing plants based on defect quantity or downtime hours, enabling a focus shift between different ranking criteria.
   - **Effect on Data**: Selecting either “Defect Quantity” or “Downtime Hours” will adjust the data and visualizations to reflect the chosen ranking and performance metrics.
   - **User Interaction**: Users can choose whether to rank plants by defect quantity or total downtime hours, simplifying the analysis of plant performance based on specific KPIs.

4. **Vendor Parameter**
   - **Formula**:
     ```DAX
     Vendor Parameter = {
         ("Defect Quantity", NAMEOF('Rank Measures'[Rank_Vendor_by_Defect_Qty]), 0),
         ("Downtime Hours", NAMEOF('Rank Measures'[Rank_Vendor_by_Downtime_Hours]), 1)
     }
     ```
   - **Description**: Similar to the Plant Parameter, this parameter enables users to toggle between analyzing vendors based on defect quantity or downtime hours.
   - **Effect on Data**: The report will adjust to rank vendors either by the total number of defects or by the total downtime hours caused by their supplies, depending on the selection.
   - **User Interaction**: Users can switch between metrics (defect quantity or downtime hours) for vendor performance analysis, aiding in identifying which vendors impact quality or downtime the most.

5. **Risk Category Parameter**
   - **Formula**:
     ```DAX
     Risk Category = 
     VAR CurrentVendor = SELECTEDVALUE(Vendor[Vendor])
     VAR TotalDowntimeHours = CALCULATE([Total DownTime(Hours)], FILTER(Vendor, Vendor[Vendor] = CurrentVendor))
     RETURN IF(TotalDowntimeHours > 800, "High Risk", 
               IF(TotalDowntimeHours <= 800 && TotalDowntimeHours >= 400, "Medium Risk", "Low Risk"))
     ```
   - **Description**: This indirect parameter classifies vendors into risk categories (High, Medium, Low) based on their total downtime hours, providing insights into their impact on operational efficiency.
   - **Effect on Data**: Vendors are automatically categorized, which influences the display of risk analysis visualizations throughout the report.
   - **User Interaction**: Users do not directly interact with this parameter, but it provides valuable insights into which vendors present the greatest risk to operations due to downtime, assisting in decision-making processes.
