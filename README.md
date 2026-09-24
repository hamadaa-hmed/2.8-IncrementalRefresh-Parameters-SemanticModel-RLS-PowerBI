# 📊 Power BI End-to-End Analytics
### Semantic Modeling · DAX · TMDL · RLS · Incremental Refresh · Parameters · Interactive Dashboard

<p align="center">
  <b>From Raw Data → Transformation → Semantic Model → Security → Performance → Interactive Analytics</b>
</p>

---

## 🚀 Project Overview

This project is an **end-to-end Power BI analytics solution** that combines data transformation, dimensional modeling, DAX calculations, semantic modeling, security, refresh optimization, dynamic parameters, and interactive data visualization.

The project is built on the **original Power BI project and its existing Semantic Model**.

The original project already established the core analytical structure using:

- Power Query
- Custom Columns
- Conditional Columns
- DAX Calendar
- DAX Measures
- Data Modeling
- **Semantic Model**

The current version extends that original project with advanced Power BI capabilities:

- 🔐 **Row-Level Security (RLS)**
- ⚡ **Incremental Refresh**
- 🎛️ **Parameters**
- 🧠 **Semantic Model**
- 📊 **Dynamic Metric Analysis**
- 📈 **Interactive Dashboard**

The final result is a practical Power BI solution that demonstrates not only how to build visuals, but also how to design the model and analytical layer behind them.

---

# 🎯 Project Objectives

The main objective is to demonstrate a complete BI workflow:

```text
Raw Data
   ↓
Power Query
   ↓
Data Transformation
   ↓
Custom Columns
   ↓
Conditional Columns
   ↓
Data Modeling
   ↓
DAX Calendar
   ↓
DAX Measures
   ↓
Existing Semantic Model
   ↓
TMDL / Model-Level Work
   ↓
Incremental Refresh
   ↓
RLS
   ↓
Parameters
   ↓
Interactive Dashboard
   ↓
Business Insights
```

---

# 🛠️ Tools & Technologies

| Technology | Purpose |
|---|---|
| **Power BI Desktop** | Dashboard & semantic model development |
| **Power Query** | Data preparation and transformation |
| **DAX** | Measures, calculations and time intelligence |
| **DAX Calendar** | Time-based analysis |
| **TMDL** | Semantic model metadata and definition |
| **Semantic Model** | Structured analytical layer |
| **RLS** | Row-level data security |
| **Incremental Refresh** | Refresh performance optimization |
| **Parameters** | Dynamic analytical exploration |
| **Data Modeling** | Relationships and model structure |

---

# 🔄 Data Transformation

## 1. Custom Columns

Custom Columns were created during the Power Query stage to generate additional business fields from existing data.

Example:

```text
Revenue = Quantity × Unit Price
```

This allows calculations and transformations to be performed before the data reaches the semantic model.

---

## 2. Conditional Columns

Conditional logic was used to convert numerical values into meaningful business categories.

Example:

```text
Profit Margin
      ↓
Loss
Low
Medium
High
```

This makes analytical results easier to segment and visualize.

---

# 📅 DAX Calendar

A dedicated Calendar table was created using DAX to support proper time-based analysis.

The Calendar contains fields such as:

- Date
- Day
- Day Name
- Day Number
- Week Number
- Month
- Month Name
- Month Number
- Year

Month names are sorted using the Month Number to maintain chronological order in visuals.

The Calendar table is connected to the fact data and supports monthly and yearly analysis.

---

# 🧮 DAX Measures

The project uses reusable DAX Measures instead of relying only on calculated columns.

Examples include:

```DAX
Total Sales =
SUM(FactSales[SalesAmount])
```

```DAX
Total Quantity =
SUM(FactSales[Quantity])
```

```DAX
Sales Count =
COUNTROWS(FactSales)
```

```DAX
Distinct Customers =
DISTINCTCOUNT(FactSales[Customer ID])
```

Additional measures are used for:

- Profit
- Cost
- KPIs
- Profit Margin
- Time-based analysis
- Dynamic dashboard metrics

This allows the same analytical logic to respond dynamically to filters and slicers.

---

# 🧠 Semantic Model — Finance

After publishing the original Power BI file, a separate **Finance Semantic Model** was created from the published data/model and connected to the report.

The Semantic Model was intentionally separated from the report so that the analytical model can be controlled independently from the dashboard layer.

The **Finance Semantic Model was created by me**, and the dashboard was also created by me, including the DAX measures and analytical logic used in the report.

The purpose of using a separate Semantic Model is to provide a controlled analytical layer where report consumers can use the dashboard without being given permission to modify the underlying model structure or directly access the underlying data.

Conceptually:

```text
              Original Power BI File
                       │
                       ▼
                  Publish
                       │
                       ▼
              ┌──────────────────┐
              │ Finance Semantic │
              │      Model       │
              └────────┬─────────┘
                       │
             ┌─────────┴─────────┐
             ▼                   ▼
        Model / DAX         Controlled Access
             │                   │
             └─────────┬─────────┘
                       ▼
                 Finance Dashboard
                       │
                       ▼
                 Business Insights
```

### 🔐 Semantic Model Access

The Semantic Model is used as a controlled analytical layer.

The goal is that report consumers can interact with the dashboard and its visuals **without having permission to modify the model relationships or directly access the underlying data**.

This separation helps protect:

- 🔒 **Model Relationships**
- 🔒 **Semantic Model Structure**
- 🔒 **Underlying Data Access**
- 🧮 **DAX Measures and Analytical Logic**

The dashboard is therefore presented as the user-facing analytical layer, while the **Finance Semantic Model** remains controlled separately.

> **Note:** Actual access to the Semantic Model and its underlying data depends on the permissions assigned in the Power BI Service. Users must not be given permissions that allow them to edit the model or access/build from the underlying semantic model if those capabilities are intended to remain restricted.


# 🧩 TMDL

The project also includes practical experience with **TMDL — Tabular Model Definition Language**.

TMDL provides a text-based approach for working with the Power BI tabular model.

The project explores model objects such as:

- Tables
- Columns
- Measures
- Metadata
- Model structure
- Semantic definitions

This adds a development-oriented dimension to the project beyond the standard Power BI graphical interface.

---

# ⚡ Incremental Refresh

**Incremental Refresh** was incorporated to demonstrate how large datasets can be refreshed more efficiently.

Instead of processing the entire dataset every time, the refresh strategy can focus on:

```text
Historical Data
       ↓
Keep Existing Partitions
       ↓
Recent Data
       ↓
Refresh Only Recent Period
```

The approach is based on defining:

- `RangeStart`
- `RangeEnd`

and applying the date filter to the relevant fact table.

### Why it matters

Incremental Refresh helps reduce unnecessary processing and becomes particularly valuable when working with larger datasets where refreshing the complete history every time would be inefficient.

---

# 🔐 Row-Level Security (RLS)

The project also demonstrates **Row-Level Security**.

RLS allows different users to see only the rows they are authorized to access.

Conceptually:

```text
User
  ↓
Security Role
  ↓
Filter Condition
  ↓
Allowed Rows
  ↓
Dashboard
```

For example, access can be controlled according to attributes such as:

- Region
- Branch
- Store
- Manager
- User identity

The goal is to demonstrate how security can be implemented at the semantic-model level rather than creating separate reports for different users.

---

# 🎛️ Parameters & Dynamic Analysis

Parameters are used to make the dashboard more interactive.

A **Metric Parameter** can allow the user to switch between metrics such as:

```text
Total Sales
Total Profit
Total Cost
Total Quantity
```

Instead of creating separate charts for every metric, the same visual can dynamically respond to the selected metric.

Example:

```text
Metric Parameter
       ↓
 ┌───────────────┐
 │ Total Sales   │
 │ Total Profit  │
 │ Total Cost    │
 │ Total Quantity│
 └───────────────┘
       ↓
Dynamic Visual
```

This improves dashboard flexibility while reducing unnecessary visual duplication.

---

# 📊 Dashboard

The final dashboard combines the analytical model with multiple visualizations.

### Main KPI Cards

The Finance analysis includes approximately:

| KPI | Value |
|---|---:|
| 💰 Total Sales | **39.70M** |
| 📈 Total Profit | **11.2M** |
| 💵 Total Cost | **28.5M** |
| 📦 Total Quantity | **155K** |

> Values are based on the dashboard figures shown in the project material and may be rounded as displayed by Power BI.

---

## 📈 Dashboard Visuals

The dashboard is designed around several analytical views:

### 💰 Sales & Profit KPIs

High-level KPI cards provide an immediate view of overall business performance.

### 🌍 Regional Analysis

Sales and profit can be analyzed across regions to understand geographic contribution.

### 🏪 Store / Branch Analysis

Store and branch-level visuals allow performance to be investigated below the overall business level.

### 👥 Customer Type Analysis

Customer types can be compared to understand how different customer groups contribute to sales.

### 📅 Monthly Trend

A line chart is used to analyze sales or profit over time.

The Calendar table enables chronological monthly analysis.

### 👨‍💼 Manager Analysis

Manager-level analysis allows performance to be examined through:

- Sales
- Quantity
- Profit
- Store/branch contribution

### 🎛️ Dynamic Metric Analysis

The Metric Parameter allows the same visual to switch between:

```text
Sales
Profit
Cost
Quantity
```

---

# 💡 Business Insights

## 1. Strong Overall Sales Volume

The Finance dashboard shows approximately **39.70M in total sales**, representing the overall scale of the analyzed business activity.

## 2. Profit Represents a Significant Portion of Sales

With approximately **11.2M profit** against **39.70M sales**, the displayed figures indicate a substantial contribution from profit relative to revenue.

An approximate displayed profit-to-sales ratio is:

```text
11.2M ÷ 39.70M ≈ 28.2%
```

## 3. Cost Structure Is Clearly Visible

Total cost is approximately **28.5M**.

The combination of:

```text
Sales
Profit
Cost
```

provides a useful high-level view of the relationship between revenue generation and cost structure.

## 4. Transaction Volume Is Significant

The dashboard shows approximately **155K units** in total quantity.

This provides another perspective on business scale beyond monetary KPIs.

## 5. Regional Performance Can Be Compared

The regional visual allows the business to compare performance across different geographic areas.

The dashboard displays multiple regions with relatively close sales levels, making regional comparison useful for identifying differences in contribution.

## 6. Customer Segments Behave Differently

The customer-type analysis shows that different customer groups contribute differently to overall sales.

This enables further investigation into:

- Customer behavior
- Sales contribution
- Profit contribution
- Segment performance

## 7. Store Performance Is Not Uniform

The store-level analysis shows differences in contribution between individual stores.

This allows management to move from:

```text
Overall Business
      ↓
Region
      ↓
Store
      ↓
Manager
```

and identify where performance is being generated.

## 8. Time-Based Analysis Adds Another Dimension

Monthly analysis reveals changes in performance throughout the year.

The DAX Calendar makes it possible to analyze:

- Monthly performance
- Yearly performance
- Trends
- Period comparisons

without relying directly on raw date fields.

---

# 🔎 Analytical Questions Answered

The dashboard can be used to investigate questions such as:

- What is the total sales value?
- How much profit is generated?
- How large is the total cost?
- How many units were sold?
- Which regions contribute most to sales?
- How does performance differ between stores?
- How do customer types contribute to sales?
- How does performance change over time?
- Which managers or branches contribute most to the reported metrics?
- How does the selected metric change across different dimensions?
- How can access to specific data rows be controlled?
- How can large historical datasets be refreshed efficiently?

---

# 🏗️ Project Architecture

The architecture below represents the evolution of the **original project** into the advanced version:

```text
                         ┌─────────────────┐
                         │    Raw Data     │
                         └────────┬────────┘
                                  │
                                  ▼
                         ┌─────────────────┐
                         │  Power Query    │
                         └────────┬────────┘
                                  │
                    ┌─────────────┴─────────────┐
                    ▼                           ▼
             Custom Columns              Conditional Columns
                    │                           │
                    └─────────────┬─────────────┘
                                  ▼
                         ┌─────────────────┐
                         │  Data Modeling  │
                         └────────┬────────┘
                                  │
                     ┌────────────┴────────────┐
                     ▼                         ▼
               DAX Calendar               DAX Measures
                     │                         │
                     └────────────┬────────────┘
                                  ▼
                         ┌─────────────────┐
                         │ Semantic Model  │
                         └────────┬────────┘
                                  │
              ┌───────────────────┼───────────────────┐
              ▼                   ▼                   ▼
       Incremental Refresh       RLS             Parameters
              │                   │                   │
              └───────────────────┼───────────────────┘
                                  ▼
                         ┌─────────────────┐
                         │   Dashboard     │
                         └────────┬────────┘
                                  ▼
                         ┌─────────────────┐
                         │ Business        │
                         │ Insights        │
                         └─────────────────┘
```

---

# 📚 Key Learning Outcomes

Through this project, I practiced:

### Power Query

- Data loading
- Data transformation
- Custom Columns
- Conditional Columns
- Data preparation

### Data Modeling

- Fact & Dimension modeling
- Relationships
- Keys
- Filter propagation
- Model organization

### DAX

- Measures
- Aggregations
- Filter context
- Time intelligence
- KPI calculations

### Semantic Modeling

- Semantic model structure
- Reusable analytical logic
- Model metadata
- TMDL

### Advanced Power BI

- Row-Level Security
- Incremental Refresh
- Parameters
- Dynamic Metrics

### Visualization

- KPI Cards
- Bar Charts
- Column Charts
- Line Charts
- Donut Charts
- Tables
- Slicers
- Interactive filtering

---

# 📂 Project Structure

```text
📦 Power-BI-End-to-End-Analytics
│
├── 📊 PowerBI/
│   └── Project.pbix
│
├── 📁 Data/
│   ├── Finance/
│   └── Project/
│
├── 🖼️ Images/
│   ├── dashboard.png
│   ├── semantic-model.png
│   ├── rls.png
│   └── incremental-refresh.png
│
├── 🎥 Demo/
│   └── project-demo.mp4
│
└── 📄 README.md
```

---

# 🧠 What Makes This Project Different?

This project is not limited to creating charts.

It demonstrates the complete journey of transforming raw data into a controlled analytical environment:

```text
Transform
   ↓
Model
   ↓
Calculate
   ↓
Secure
   ↓
Optimize
   ↓
Parameterize
   ↓
Visualize
   ↓
Analyze
```

The focus is therefore on both:

**Data Engineering + Business Intelligence**

rather than visualization alone.

---

# 🎓 Skills Demonstrated

**Power BI · Power Query · DAX · TMDL · Semantic Modeling · Data Modeling · Custom Columns · Conditional Columns · DAX Calendar · DAX Measures · RLS · Incremental Refresh · Parameters · Data Visualization · Business Intelligence · Performance Optimization**

---

# 📌 Conclusion

This project demonstrates an end-to-end Power BI workflow that combines **data transformation, semantic modeling, DAX, TMDL, security, refresh optimization, parameters, and interactive visualization**.

The final solution connects the technical side of Power BI with business analysis:

```text
Raw Data
→ Transformation
→ Modeling
→ DAX
→ Semantic Model
→ Security
→ Performance
→ Dynamic Analysis
→ Dashboard
→ Insights
```

It demonstrates how Power BI can be used not only to **visualize data**, but to build a structured, reusable, secure, and scalable analytical solution.

---

<p align="center">

### 📊 Power BI · DAX · TMDL · Semantic Model · RLS · Incremental Refresh

**From Data → Model → Intelligence**

</p>

---

## 👤 Author

**Hamada Ahmed**

**Data Analyst | Power BI | Excel | SQL | Python**

⭐ *Building analytical solutions and continuously developing Data Analytics & Business Intelligence skills.*
