# Component Consumption Analytics Dashboard

## Project Overview

This project analyzes **component consumption and operational performance** using transaction-level data from a repair-center environment.

The dashboard was built to answer practical business questions such as:

- How much material was consumed over the last six complete months?
- Which months, products, and part codes drive the highest consumption?
- How concentrated is component usage across part codes?
- What percentage of consumed quantity is Closed, Reject, or Ongoing?
- How quickly are requested components issued?
- Which parts should receive higher inventory-monitoring priority?

The analysis focuses on **February 2026 to July 2026** because January and August contain partial-month data and would make month-over-month comparisons misleading.

---

## Dataset Summary

| Metric | Value |
|---|---:|
| Analysis Period | Feb 2026 – Jul 2026 |
| Transaction Records | 87,564 |
| Total Consumption Qty | 183,935 |
| Unique Part Codes | 1,129 |
| Unique Module Serials | 33,717 |
| Unique Products | 71 |
| Average Monthly Consumption | 30,656 |

> The original source contains 90,371 records from January 4, 2026 to August 7, 2026. Only six complete months are used for standard trend analysis.

---

## Key Business KPIs

| KPI | Result |
|---|---:|
| Total Consumption | 183,935 units |
| July 2026 Consumption | 30,585 units |
| July MoM Change | -3.57% |
| Closed Quantity | 178,072 |
| Closed Rate | 96.81% |
| Reject Quantity | 5,473 |
| Reject Rate | 2.98% |
| Ongoing Quantity | 390 |
| Ongoing Rate | 0.21% |
| Top 10 Parts Share | 53.00% |
| Parts Required to Reach ~80% of Consumption | 69 |
| Median Request-to-Issue Time | 1.24 min |
| P90 Request-to-Issue Time | 4.58 min |
| Requests Issued Within 5 Minutes | 91.4% |

---

## Monthly Consumption Trend

| Month | Consumption Qty | MoM Change |
|---|---:|---:|
| Feb 2026 | 26,333 | — |
| Mar 2026 | 34,607 | +31.42% |
| Apr 2026 | 32,352 | -6.52% |
| May 2026 | 28,340 | -12.40% |
| Jun 2026 | 31,718 | +11.92% |
| Jul 2026 | 30,585 | -3.57% |

### Key Finding

**March 2026 recorded the highest consumption at 34,607 units**, increasing by **31.42%** compared with February.

Consumption declined during April and May, recovered by **11.92% in June**, and then decreased slightly by **3.57% in July**.

---

## Top 10 Part Codes by Consumption

| Rank | Part Code | Consumption Qty | Share of Total |
|---|---|---:|---:|
| 1 | P164346 | 32,919 | 17.90% |
| 2 | 5449648 | 17,546 | 9.54% |
| 3 | 2514453 | 14,768 | 8.03% |
| 4 | 4862419 | 8,347 | 4.54% |
| 5 | 4869119 | 5,020 | 2.73% |
| 6 | 4218286 | 4,635 | 2.52% |
| 7 | 4216919 | 4,056 | 2.21% |
| 8 | 4110642 | 3,436 | 1.87% |
| 9 | 5119148 | 3,377 | 1.84% |
| 10 | P189444 | 3,377 | 1.84% |

### Key Finding

- The **Top 10 part codes account for 53.00%** of total component consumption.
- The highest-consumption part, **P164346**, alone contributes **17.90%**.
- Only **69 out of 1,129 part codes** are required to reach approximately **80% of total consumption**.

This helps identify the small group of high-impact components that should receive closer stock and replenishment monitoring.

---

## Consumption by Type

| Type | Consumption Qty | Share |
|---|---:|---:|
| Rework | 98,309 | 53.45% |
| SUI | 76,397 | 41.53% |
| BGA | 9,192 | 5.00% |
| RND | 37 | 0.02% |

### Key Finding

**Rework and SUI together account for 94.98% of total consumption**, making them the primary areas for consumption monitoring.

---

## Top Products

| Rank | Product | Consumption Qty | Share |
|---|---|---:|---:|
| 1 | FXED | 34,041 | 18.51% |
| 2 | FRGU | 26,433 | 14.37% |
| 3 | FXJB | 22,118 | 12.02% |
| 4 | FBBC | 17,865 | 9.71% |
| 5 | FSMF | 10,734 | 5.84% |

The **Top 4 products contribute 54.62%** of total component consumption.

---

## Operational Performance

The dataset also contains request and component-issue timestamps, allowing the dashboard to measure store responsiveness.

| KPI | Result |
|---|---:|
| Median Request-to-Issue Time | 1.24 min |
| P90 Request-to-Issue Time | 4.58 min |
| Issued Within 5 Minutes | 91.4% |
| Issued Within 10 Minutes | 97.7% |
| July Reject Rate | 4.03% |

### Key Finding

The typical component request is fulfilled very quickly, with a **median issue time of 1.24 minutes** and **91.4% of valid requests issued within 5 minutes**.

The **July reject rate increased to 4.03%**, compared with the six-month overall reject rate of **2.98%**, making it a useful exception metric to monitor.

---

## Dashboard Pages

### 1. Executive Summary
Provides a management-level view of:

- Total Consumption
- Latest Month Consumption
- Month-over-Month Change
- Unique Part Codes
- Unique Modules
- Closed and Reject %
- Monthly Consumption Trend
- Consumption by Type
- Top Products
- Top 10 Part Codes
- Management Insights

### 2. Part & Product Analysis
Focuses on material-level analysis:

- Top 10 Part Codes by Consumption
- Top 10 Parts vs All Other Parts
- Parts Driving 80% of Usage
- Part-level Contribution %
- Active Months
- Module Count
- Reject %
- Monthly Usage Pattern for Top Parts

### 3. Operational Performance
Focuses on process performance:

- Median Request-to-Issue Time
- P90 Issue Time
- % Issued Within 5 Minutes
- Monthly Reject Rate
- Status Mix
- Data-quality checks

---

## Data Validation Performed

Before building the dashboard, the following checks were performed:

- Date fields converted to proper date/time format
- Six complete months selected for fair MoM comparison
- Partial January and August periods excluded from the standard trend view
- Request Qty and Picked Qty compared for consistency
- Status values validated
- Negative/invalid issue-time durations excluded from response-time analysis
- Duplicate and transaction-level behavior reviewed before aggregation

One important observation was that **Request Qty and Picked Qty are equal throughout the source**, so a fulfillment-rate KPI would remain constant at 100% and was not treated as a major analytical KPI.

---

## Power BI / Analytics Skills Demonstrated

- Power Query data cleaning and transformation
- Date table creation
- Data modeling
- Star-schema design
- DAX measures
- Month-over-Month analysis
- Ranking
- Contribution %
- Distinct counts
- Conditional calculations
- KPI design
- Interactive filtering
- Drill-down analysis
- Business insight generation
- Data-quality validation

---

## Core DAX Measures

```DAX
Total Consumption =
SUM(FactConsumption[Picked Qty])
```

```DAX
Unique Parts =
DISTINCTCOUNT(FactConsumption[Part Code])
```

```DAX
Unique Modules =
DISTINCTCOUNT(FactConsumption[Module Serial Number])
```

```DAX
Previous Month Consumption =
CALCULATE(
    [Total Consumption],
    DATEADD(DimDate[Date], -1, MONTH)
)
```

```DAX
MoM % =
DIVIDE(
    [Total Consumption] - [Previous Month Consumption],
    [Previous Month Consumption],
    0
)
```

```DAX
Closed Qty =
CALCULATE(
    [Total Consumption],
    FactConsumption[Status] = "Closed"
)
```

```DAX
Closed % =
DIVIDE(
    [Closed Qty],
    [Total Consumption],
    0
)
```

```DAX
Reject Qty =
CALCULATE(
    [Total Consumption],
    FactConsumption[Status] = "Reject"
)
```

```DAX
Reject % =
DIVIDE(
    [Reject Qty],
    [Total Consumption],
    0
)
```

```DAX
Part Rank =
RANKX(
    ALLSELECTED(FactConsumption[Part Code]),
    [Total Consumption],
    ,
    DESC,
    DENSE
)
```

---

## Business Value

This dashboard converts transaction-level component data into decision-support information.

It can help management:

- identify high-consumption components,
- prioritize critical part codes,
- understand monthly consumption changes,
- monitor reject levels,
- identify the products driving material usage,
- monitor component-issue responsiveness,
- and focus inventory attention on the parts with the highest operational impact.

---

## Tools Used

- **Power BI** — Data modeling, DAX, dashboard design
- **Power Query** — Data cleaning and transformation
- **Excel** — Source data and validation
- **Python / Pandas** — Data profiling and analytical validation

---

## Suggested Repository Structure

```text
component-consumption-analytics/
│
├── README.md
├── dashboard/
│   └── Component_Consumption_Dashboard.pbix
│
├── screenshots/
│   ├── executive-summary.png
│   ├── part-product-analysis.png
│   └── operational-performance.png
│
├── data/
│   └── anonymized_consumption_data.xlsx
│
└── docs/
    └── dax-measures.md
```

---

## Data Privacy

This project is based on operational business data.

For the public GitHub version, the dataset should be **anonymized before upload**. Do not publish confidential information such as:

- employee or repairer names,
- original module serial numbers,
- rack or internal storage locations,
- internal URLs or system identifiers,
- customer-sensitive information,
- proprietary descriptions or mappings that are not approved for public sharing.

A sanitized sample dataset can be used to reproduce the dashboard while keeping the analytical logic and results demonstrable.

---

## Project Outcome

The project demonstrates an end-to-end analytics workflow:

**Business Requirement → Data Validation → Power Query → Data Modeling → DAX → Dashboard → Insights → Business Action**

The objective was not only to visualize consumption data, but to identify the **main consumption drivers, operational exceptions, and areas where management attention can create the most value**.
