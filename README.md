# 📊 Digital Banking Transaction Monitoring — Power BI
### Bank M&E Analytics Portfolio Series (Part 2 of 2) | Microsoft Power BI

---

## Overview

This project is the **direct continuation** of the Excel-based data cleaning 
portfolio (Part 1), extending the cleaned dataset into an interactive 
**Monitoring & Evaluation dashboard** built entirely in Microsoft Power BI.

The dashboard simulates the analytical workflow of an **M&E Digital Banking team** 
— monitoring transaction performance, evaluating channel effectiveness, 
detecting system anomalies, and presenting findings in an executive-ready format.

> *Part 2 of 2 — Interactive M&E Dashboard. Data cleaning covered in Part 1 (Excel).*

---

## Relationship to Excel Portfolio

This Power BI project uses the cleaned output from the Excel project as its 
data source. The full analytical pipeline is:

```
Raw CSV (730 rows)
    ↓
[Part 1] Excel — Data Cleaning & Standardization
    ↓
Clean CSV (698 rows)
    ↓
[Part 2] Power BI — M&E Dashboard & Visualization
```

---

## Dataset

| Attribute | Detail |
|---|---|
| Source | Simulated Digital Banking Transaction Data |
| Raw Records | 730 transactions |
| Clean Records | 698 transactions (after Excel cleaning) |
| Period | January — December 2024 |
| Channels | Mobile Banking, Internet Banking, ATM, EDC |

### Data Quality Summary (from Part 1)

| Issue | Rows Affected | Action |
|---|---|---|
| Missing critical values | 30 | Deleted |
| Invalid amount (zero/negative) | 2 | Deleted |
| Duplicate transaction ID | 0 | None needed |
| Inconsistent status labels | Multiple | Standardized |
| Inconsistent channel labels | Multiple | Standardized |
| Inconsistent date formats | Multiple | Standardized |
| **Data Retention Rate** | **95.6%** | |

---

## Report Structure

| # | Page | Focus |
|---|---|---|
| 1 | `Overview` | Transaction volume trend, status distribution, channel comparison |
| 2 | `Channel & Wilayah` | Channel effectiveness, regional distribution, transaction composition |
| 3 | `Kualitas Sistem` | Response time monitoring, system health, anomaly detection |
| 4 | `Evaluasi & Temuan` | Cleaning report, key findings, and business recommendations |

---

## Key Findings

- 📈 **Transaction volume** shows monthly seasonality patterns relevant 
for infrastructure capacity planning
- ✅ **Success Rate** varies significantly across channels — Mobile Banking 
leads while certain channels fall below the 95% SLA target
- ⚠️ **Response time outliers** (>30,000ms) detected — transactions likely 
perceived as failures by customers despite eventual success
- 🌙 **Odd-hour transactions** (02.00–04.00) identified as potential 
fraud indicators requiring AML monitoring
- 🗺️ **Surabaya** dominates transaction volume across all channels, 
followed by other East Java cities
- 📋 **Data Retention Rate of 95.6%** exceeds OJK's 90% minimum 
threshold for regulatory reporting

---

## DAX Measures

```dax
-- Core KPIs
Total Transaksi = COUNTROWS(TrxData)

Success Rate = DIVIDE([Total Sukses], [Total Transaksi], 0)

Failure Rate = DIVIDE([Total Gagal], [Total Transaksi], 0)

-- System Health
Avg Response Time =
CALCULATE(
    AVERAGE(TrxData[Response_Time_ms]),
    TrxData[Response_Time_ms] > 0
)

Transaksi Lambat Kritis =
CALCULATE(
    COUNTROWS(TrxData),
    TrxData[Response_Flag] = "Lambat Kritis"
)

-- Anomaly Detection
Transaksi Anomali =
CALCULATE(
    COUNTROWS(TrxData),
    TrxData[Jam_Tidak_Wajar] = 1
)

Pct Anomali = DIVIDE([Transaksi Anomali], [Total Transaksi], 0)

-- Data Quality
Data Retention Rate = DIVIDE(698, 730, 0)
```

---

## Dashboard Features

- 🔘 **Button-style slicers** on every page for dynamic filtering 
by Quarter, Channel, Region, Status, and Transaction Type
- 📉 **SLA reference lines** at 95% Success Rate and 5,000ms 
response time target on relevant charts
- 🌡️ **Heatmap matrix** for regional × channel volume analysis 
with conditional formatting
- 📊 **Dual constant lines** on system health chart marking 
SLA target (5,000ms) and critical threshold (30,000ms)
- 🎨 **Consistent Bank Jatim color theme** across all pages 
(Navy #003F7F + Gold #F5A623)

---

## Banking Context

Each analytical layer in this dashboard reflects a real M&E workflow 
in digital banking:

| Dashboard Page | Real-World Equivalent |
|---|---|
| Overview | Monthly Digital Banking Performance Report |
| Channel & Wilayah | Channel Migration & Regional Infrastructure Review |
| Kualitas Sistem | System Health Monitoring & IT Incident Escalation |
| Evaluasi & Temuan | Data Quality Audit & M&E Evaluation Report |

Key regulatory and operational references applied in this project:

- **POJK No. 12/2018** — Digital banking service availability standard (≥99.5% uptime)
- **OJK Data Quality Standard** — Minimum 90% usable data for regulatory reporting
- **SLA Convention** — ≥95% transaction success rate as industry benchmark
- **AML Monitoring** — Odd-hour transaction flagging as fraud detection indicator

---

## Tools & Technology

![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=flat&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-0078D4?style=flat&logo=microsoft&logoColor=white)
![Excel](https://img.shields.io/badge/Microsoft_Excel-217346?style=flat&logo=microsoft-excel&logoColor=white)


---

## Project Series

| Part | Tool | Focus | Status |
|---|---|---|---|
| Part 1 | Microsoft Excel | Data Cleaning & Preparation | ✅ Complete |
| **Part 2** | Microsoft Power BI | M&E Dashboard & Visualization | ✅ Complete |

---

## About

**Muhammad Fauzi Romadhoni**
D4 Industrial Electrical Engineering — Politeknik Elektronika Negeri Surabaya
K3 Umum Certified (BNSP) | Internship: PT PLN UPT Gresik (Planning & Evaluation)
Data Analysis Enthusiast | Transitioning into Data Science

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=flat&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/mfauziromadhoni/)
[![Email](https://img.shields.io/badge/Email-Contact-EA4335?style=flat&logo=gmail&logoColor=white)](mailto:mfauzir2477@gmail.com)
[![GitHub](https://img.shields.io/badge/GitHub-Portfolio-181717?style=flat&logo=github&logoColor=white)](https://github.com/mfauziromadhoni?tab=repositories)

---

*Part of a data analytics portfolio series targeting Monitoring & Evaluation
roles in the banking and financial services industry — specifically structured
for Digital Banking M&E positions at regional development banks.*
