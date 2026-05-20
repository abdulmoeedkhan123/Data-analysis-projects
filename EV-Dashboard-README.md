# EV Charging Stations Dashboard

A comprehensive analytics dashboard for Electric Vehicle (EV) charging infrastructure analysis of NSW across councils, operators, and capacity metrics.

## 📊 Dashboard Overview

This interactive dashboard provides deep insights into EV charging station distribution, capacity planning, and operational analytics across multiple dimensions. The dashboard is organized into 5 specialized pages for focused analysis.

### Dashboard Pages

1. **Overview** - High-level insights and key metrics
2. **EV Insights** - AC vs DC charger analysis and distribution
3. **Council & Post Code** - Geographic distribution and council-level analytics
4. **Operators** - Operator performance and market share analysis
5. **Capacity Analysis** - Infrastructure capacity planning and utilization

---

## 📋 Table of Contents

- [Data Sources](#data-sources)
- [Dashboard Pages](#dashboard-pages-detailed)
- [Key Metrics](#key-metrics)
- [Technical Architecture](#technical-architecture)
- [Installation & Setup](#installation--setup)
- [Usage Guide](#usage-guide)
- [Data Models](#data-models)
- [Contributing](#contributing)

---

## 🗄️ Data Sources

### Primary Dataset
- **Table**: `main.default.ev_charging_stations_uk`
- **Source**: UK EV charging infrastructure data
- **Key Fields**:
  - Station address, Post Code, Council
  - Operator information
  - Charger Type (AC/DC)
  - Total Plugs, Total Capacity (kW)
  - Plug Types and individual capacities

### Data Refresh
- Real-time analysis using Unity Catalog tables
- Aggregations computed dynamically via SQL datasets

---

## 📄 Dashboard Pages (Detailed)

### 1. Overview Page
**Purpose**: Executive summary with critical KPIs and trends

**Visualizations**:
- **Stations by Charger Type** (Bar Chart)
  - Distribution of AC vs DC charging stations
  - Helps identify infrastructure balance
  
- **Capacity by Operator** (Bar Chart)
  - Top operators by total capacity (kW)
  - Market share visualization
  
- **Plugs by Council** (Bar Chart)
  - Geographic distribution of charging infrastructure
  - Identifies underserved areas

- **Average Capacity per Plug** (Counter)
  - KPI showing efficiency metric
  - Benchmark: Industry standard comparison

### 2. EV Insights Page
**Purpose**: Deep dive into AC vs DC charging infrastructure

**Visualizations**:
- **AC vs DC Distribution** (Pie Chart)
  - Percentage breakdown of charger types
  - Visual representation of infrastructure mix

- **Top AC Operators** (Bar Chart)
  - Leading operators in AC charging
  - Station count rankings

- **Top DC Operators** (Bar Chart)
  - Leading operators in DC fast charging
  - Critical for long-distance travel infrastructure

- **Detailed Station Table**
  - Comprehensive list with all station attributes
  - Sortable and filterable

### 3. Council & Post Code Page
**Purpose**: Geographic and administrative boundary analysis

**Visualizations**:
- **Top Councils by Station Count** (Bar Chart)
  - Most developed charging infrastructure by council
  
- **Bottom Councils by Station Count** (Bar Chart)
  - Identifies areas needing investment
  - Gap analysis for policy makers

- **Top Councils - AC Chargers** (Bar Chart)
  - AC infrastructure leaders by region

- **Top Councils - DC Chargers** (Bar Chart)
  - Fast charging infrastructure leaders

- **Post Code Analytics** (4 Counters)
  - Post Code with Most Plugs
  - Post Code with Least Plugs
  - Post Code with Most Capacity
  - Post Code with Least Capacity

### 4. Operators Page
**Purpose**: Competitive analysis and operator performance metrics

**Visualizations**:
- **Top Operators by Station Count** (Bar Chart)
  - Market leaders in deployment
  
- **Bottom Operators by Station Count** (Bar Chart)
  - Emerging or niche operators

- **Top Operators by Capacity** (Bar Chart)
  - Ranked by total power output (kW)
  - Shows infrastructure investment

- **Bottom Operators by Capacity** (Bar Chart)
  - Smaller players in the market

- **Operators by Total Plugs** (Bar Chart)
  - Accessibility metric (more plugs = more availability)

- **Average Capacity by Operator** (Bar Chart)
  - Efficiency metric per operator
  - Shows strategy (many small vs few large stations)

### 5. Capacity Analysis Page
**Purpose**: Infrastructure capacity planning and optimization

**KPI Counters**:
- **Total Capacity (kW)** - System-wide power capacity
- **Max Station Capacity (kW)** - Largest single station
- **Average Capacity per Plug (kW)** - Efficiency metric
- **Total Plugs** - Total charging points available

**Charts**:
- **Capacity Distribution by Council** (Bar Chart)
  - Power capacity breakdown by region
  - Identifies capacity hotspots

- **Plugs Distribution by Council** (Bar Chart)
  - Access point distribution
  - Complements capacity view

**Tables**:
- **Station with Most Plugs**
  - Address, Operator, Plug Count, Capacity
  - Highlights hub stations

- **Station with Least Plugs**
  - Identifies minimal infrastructure points
  - Useful for coverage gap analysis

---

## 🎯 Key Metrics

### Infrastructure Metrics
- **Total Charging Stations**: Count of unique locations
- **Total Plugs**: Individual charging points
- **Total Capacity (kW)**: Sum of all charging power
- **Average Capacity per Plug**: Efficiency indicator

### Distribution Metrics
- **AC vs DC Ratio**: Technology mix
- **Council Coverage**: Geographic spread
- **Operator Concentration**: Market competition level

### Performance Indicators
- **Stations per Council**: Coverage metric
- **Capacity per Council**: Power availability
- **Plugs per Station**: Accessibility factor
- **Operator Market Share**: Competitive landscape

---

## 🏗️ Technical Architecture

### Platform
- **Databricks Lakehouse Platform**
- **Unity Catalog** for data governance
- **Lakeview Dashboards** for visualization

### Data Pipeline
```
Source Data (Unity Catalog Table)
    ↓
main.default.ev_charging_stations_uk
    ↓
SQL Datasets (40+ aggregations)
    ↓
Dashboard Widgets (Charts, Tables, Counters)
    ↓
Interactive 5-Page Dashboard
```

### Dataset Layer
The dashboard uses **40+ SQL datasets** for performance optimization:

**Categories**:
1. **Aggregation Datasets** (15+)
   - Summary statistics by Council, Operator, Charger Type
   - COUNT, SUM, AVG calculations

2. **Ranking Datasets** (10+)
   - Top/Bottom N rankings
   - Sorted by various metrics

3. **Filter Datasets** (8+)
   - AC-only and DC-only filters
   - Specific criteria subsets

4. **KPI Datasets** (7+)
   - Single-value metrics for counters
   - MAX, MIN, AVG calculations

### Visualization Types
- **Bar Charts**: Comparative analysis (horizontal orientation)
- **Pie Charts**: Proportional breakdown
- **Counters**: KPI displays
- **Tables**: Detailed data exploration

---

## 🚀 Installation & Setup

### Prerequisites
- Databricks workspace access
- Unity Catalog enabled
- Lakeview dashboards feature enabled
- Access to `main.default.ev_charging_stations_uk` table

### Setup Steps

1. **Data Access**
   ```sql
   -- Verify table access
   SELECT * FROM main.default.ev_charging_stations_uk LIMIT 10;
   ```

2. **Import Dashboard**
   - Navigate to Lakeview Dashboards
   - Import the dashboard JSON file
   - Verify dataset connections

3. **Permissions**
   - Ensure viewer access to the Unity Catalog table
   - Grant dashboard view/edit permissions as needed

4. **Refresh Settings**
   - Configure auto-refresh if required
   - Set cache settings for optimal performance

---

## 📖 Usage Guide

### Navigating the Dashboard

1. **Page Navigation**
   - Use the page selector at the top
   - Each page focuses on a specific analytical dimension

2. **Interactive Features**
   - Click on charts for drill-down (where enabled)
   - Hover for detailed tooltips
   - Use table search and sort features

3. **Filtering**
   - Apply filters at the page level (if configured)
   - Filters cascade to all widgets on the page

### Common Use Cases

**For Policy Makers**:
- Identify underserved councils (Council & Post Code page)
- Assess infrastructure gaps (Capacity Analysis page)
- Track deployment progress over time

**For Operators**:
- Competitive benchmarking (Operators page)
- Market share analysis (Overview + Operators pages)
- Capacity planning insights (Capacity Analysis page)

**For Planners**:
- Geographic distribution analysis (Council & Post Code page)
- Technology mix evaluation (EV Insights page)
- Future capacity requirements (Capacity Analysis page)

---

## 📊 Data Models

### Primary Table Schema
```sql
main.default.ev_charging_stations_uk
├── Station address (STRING)
├── Post Code (STRING)
├── Council (STRING)
├── Operator (STRING)
├── Charger_Type (STRING)          -- AC or DC
├── Total Plugs (INTEGER)
├── Total Capacity(kW) (DOUBLE)
└── [Additional plug-specific fields]
```

### Key Calculations

**Average Capacity per Plug**:
```sql
SUM(`Total Capacity(kW)`) / SUM(`Total Plugs`)
```

**Station Count by Operator**:
```sql
COUNT(DISTINCT `Station address`) 
GROUP BY Operator
```

**Council Coverage**:
```sql
COUNT(DISTINCT Council)
```

---

## 🔍 Dataset Reference

The dashboard uses 40+ optimized datasets. Key categories:

### Summary Datasets
- `Overall Summary` - System-wide KPIs
- `Charger Type Summary` - AC/DC breakdown
- `Council Summary` - Geographic aggregations
- `Operator Summary` - Provider statistics

### Ranking Datasets
- Top/Bottom 10 Councils (by stations, capacity)
- Top/Bottom 10 Operators (by stations, capacity, plugs)
- Post Code extremes (most/least plugs, capacity)

### Filtered Views
- `AC Charger Stations` - AC-only data
- `DC Charger Stations` - DC-only data
- Type-specific operator rankings

---

## 🤝 Contributing

### Reporting Issues
- Include dashboard page and widget names
- Provide screenshots if applicable
- Describe expected vs actual behavior

### Feature Requests
- Describe the use case
- Suggest visualization types
- Indicate priority level

---

## 📝 License

This project is part of a data analytics portfolio demonstrating Databricks capabilities.

---

## 🔄 Version History

### Version 2.0 (Current - May 2026)
- 5-page restructured dashboard
- 40+ optimized SQL datasets
- Enhanced capacity analysis
- Geographic drill-downs
- Operator competitive analysis

### Version 1.0
- Initial release
- Single-page dashboard
- Basic metrics and charts

---

## 🎓 Learning Resources

### Databricks Documentation
- [Lakeview Dashboards Guide](https://docs.databricks.com/dashboards/)
- [Unity Catalog](https://docs.databricks.com/unity-catalog/)
- [SQL Reference](https://docs.databricks.com/sql/language-manual/)

### EV Charging Standards
- UK EV infrastructure guidelines
- AC vs DC charging explained
- Capacity planning best practices

---

**Last Updated**: May 21, 2026  
**Dashboard Version**: 2.0  
**Platform**: Databricks Lakehouse Platform
