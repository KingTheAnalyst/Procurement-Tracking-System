# Procurement System Dashboard Documentation

## Table of Contents
- [Introduction](#introduction)
- [Purpose](#purpose)
- [Objectives](#objectives)
- [System Overview](#system-overview)
- [Target Audience](#target-audience)
- [Data Model Structure](#data-model-structure)
- [Dashboard Layout & Navigation](#dashboard-layout--navigation)
  - [Landing Page](#landing-page)
  - [Overview](#overview)
  - [Vendor Performance Dashboard](#vendor-performance-dashboard)
  - [Plant Performance Dashboard](#plant-performance-dashboard)
  - [Material Performance Dashboard](#material-performance-dashboard)
  - [Downtime Impact Dashboard](#downtime-impact-dashboard)
- [Data Definition](#data-definition)
- [Calculated Measures](#calculated-measures)

## Introduction

This document serves as a guide to the **Procurement System Dashboard** developed for *Enterprise Manufacturers Ltd.* The purpose of the dashboard is to centralize and analyze supplier quality data, allowing the company to identify patterns and trends in vendor, plant, and material performance, as well as the impacts of defects.

Given the absence of a procurement system, the dashboard is designed to address inconsistencies between different plants and vendors, providing insights into defective quantities, downtime, and the overall performance of suppliers.
## Purpose

*Enterprise Manufacturers Ltd.* needed a solution to validate the quality of goods supplied by vendors and track the consistency of material quality across multiple plants. The goal of this project is to provide concise and informed insights to the management team to optimize procurement decisions, reduce downtime, and minimize manufacturing defects.

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
