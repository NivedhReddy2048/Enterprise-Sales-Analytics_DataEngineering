# 📊 Enterprise Sales Analytics – End-to-End Azure Data Engineering Project

> A complete cloud-native Data Engineering project built on the Microsoft Azure ecosystem using **Azure Data Lake Storage Gen2**, **Azure Data Factory**, **Azure Databricks**, the **Medallion Architecture (Bronze–Silver–Gold)**, and **Power BI** to transform raw enterprise sales data into interactive business intelligence dashboards.

---

## 📋 Project Overview

This project demonstrates how a modern enterprise builds a scalable analytics platform using Microsoft's cloud technologies.

The objective of this project is to simulate a real-world enterprise sales analytics system where raw transactional data is ingested, processed, transformed, and visualized to support data-driven business decisions.

Instead of directly analyzing CSV files, the project follows the **Lakehouse Architecture** using the **Medallion Data Architecture**, which separates data into three logical layers:

- 🥉 **Bronze Layer** – Raw data
- 🥈 **Silver Layer** – Cleaned and validated data
- 🥇 **Gold Layer** – Business-ready analytical data

The final Gold layer powers an interactive Power BI dashboard designed for executives and business stakeholders.

---

## 🏢 Business Problem

Large organizations generate millions of sales transactions every day from multiple operational systems.

Raw transactional data is not suitable for business reporting because it often contains:

- ❌ Duplicate records
- ❌ Missing values
- ❌ Inconsistent formats
- ❌ Complex relationships
- ❌ Large data volumes

Business users require a single source of truth that provides accurate KPIs and insights without dealing with raw operational data.

This project addresses that problem by building an end-to-end analytical pipeline that transforms operational data into reliable business intelligence.

---

## 🏗️ Project Architecture

```bash
                                      +----------------------+
                                      |   📁 CSV Source Files  |
                                      |----------------------|
                                      | 👤 Customers         |
                                      | 📦 Orders            |
                                      | 🛒 Order Items       |
                                      | 🏷️ Products          |
                                      | 👔 Employees         |
                                      | 💳 Payments          |
                                      +----------+-----------+
                                                 |
                                                 |
                                                 ▼
                          +------------------------------------------+
                          | ☁️ Azure Data Lake Storage Gen2          |
                          | 📥 Raw Landing Zone                      |
                          +----------------+-------------------------+
                                           |
                                           |
                                           ▼
                           +-----------------------------------------+
                           | 🔧 Azure Data Factory                   |
                           | 🔄 Automated Data Ingestion Pipeline    |
                           +----------------+------------------------+
                                            |
                                            ▼
                    +-----------------------------------------------+
                    | ⚡ Azure Databricks                           |
                    | 🏅 Medallion Architecture                     |
                    +-----------------------------------------------+
                                │
          ┌─────────────────────┼─────────────────────┐
          ▼                     ▼                     ▼
   🥉 Bronze Layer       🥈 Silver Layer       🥇 Gold Layer
   📄 Raw Tables         ✨ Cleaned Data       📈 Business KPIs
   🚫 No Transformations  ✅ Validated Data     📊 Aggregated Tables
          │                     │                     │
          └─────────────────────┼─────────────────────┘
                                ▼
                     📊 Power BI Executive Dashboard
                                │
                                ▼
                     🎯 Business Decision Making
```

![Architecture](https://github.com/NivedhReddy2048/Enterprise-Sales-Analytics_DataEngineering/blob/main/Images/Architecture/Archi.png?raw=true)

---

## 🛠️ Technology Stack

| Technology                   | Purpose                |
| ---------------------------- | ---------------------- |
| ☁️ Microsoft Azure           | Cloud Platform         |
| 📦 Azure Data Lake Storage Gen2 | Centralized Data Lake  |
| 🔧 Azure Data Factory        | Data Ingestion         |
| ⚡ Azure Databricks          | Data Engineering & ETL |
| 🐍 PySpark                   | Data Processing        |
| 🗄️ SQL                       | Data Transformation    |
| 🗂️ Delta Tables              | Optimized Storage      |
| 📊 Power BI                  | Business Intelligence  |
| 🐙 GitHub                    | Version Control        |

---

## 📂 Dataset

The project uses six enterprise sales datasets.

| Dataset    | Description                      |
| ---------- | -------------------------------- |
| 👤 Customers  | Customer master data             |
| 📦 Orders     | Customer orders                  |
| 🛒 OrderItems | Products purchased in each order |
| 🏷️ Products   | Product catalog                  |
| 👔 Employees  | Sales representatives            |
| 💳 Payments   | Payment information              |

These datasets simulate data generated from an enterprise ERP/POS system.

---

## 🔄 Data Engineering Pipeline

### 📥 Step 1 — Raw Data Storage

The source CSV files are uploaded into **Azure Data Lake Storage Gen2**, which acts as the enterprise data lake.

Benefits include:

- 📈 Highly scalable storage
- 🔒 Secure cloud storage
- 💰 Cost-effective
- 🗂️ Centralized data repository
- ⚖️ Separation of storage and compute

---

### 🔄 Step 2 — Data Ingestion

Azure Data Factory is responsible for orchestrating data movement.

The pipeline:

- 📖 Reads CSV files
- ✅ Validates availability
- 📤 Copies data into Databricks
- ⏰ Supports automated execution

Instead of manually importing files, the ingestion process can be executed through a pipeline.

---

## ⚡ Databricks Implementation

The core data engineering work is performed inside Azure Databricks.

The project follows the Medallion Architecture.

---

## 🥉 Bronze Layer

The Bronze layer stores raw enterprise data exactly as received.

No transformations are applied.

Purpose:

- 📄 Preserve source data
- 📚 Maintain historical records
- 🔄 Provide recovery layer
- 🧪 Enable reproducibility

### 🥉 Bronze Tables

```bash
customers
employees
orders
orderitems
products
payments
```

### 🥉 Characteristics

- 📄 Raw data
- 🔒 Immutable
- 🚫 No business logic
- 🏗️ Original schema preserved

---

## 🥈 Silver Layer

The Silver layer transforms raw data into trusted analytical datasets.

Transformations performed include:

- 🧹 Duplicate removal
- 🔧 Missing value handling
- ✅ Data validation
- 🔢 Data type conversion
- 📅 Date formatting
- 🎯 Standardization
- 📋 Business rule validation
- ✨ Data quality improvements

The Silver layer serves as the organization's trusted source of clean operational data.

---

## 🥇 Gold Layer

The Gold layer contains business-ready aggregated datasets optimized for reporting.

Instead of millions of transactional records, Gold stores summarized metrics that Power BI can query efficiently.

### 🥇 Gold Tables

#### 📊 Executive KPIs

Contains:

- 💰 Total Revenue
- 📦 Total Orders
- 👥 Total Customers
- 📈 Average Order Value

---

#### 📅 Monthly Sales

Provides:

- 💰 Revenue by Month
- 💰 Revenue by Year
- 📦 Monthly Order Counts

---

#### 🏷️ Product Sales

Provides:

- 💰 Product Revenue
- 📦 Quantity Sold
- 📊 Category Performance

---

#### 👔 Employee Sales

Provides:

- 💰 Revenue by Employee
- 📦 Orders Processed
- 📊 Department Performance

---

#### 💳 Payment Analysis

Provides:

- 💰 Revenue by Payment Method
- 💳 Number of Payments

---

#### 🗺️ State Sales

Provides:

- 💰 Revenue by State
- 📦 Total Orders by State

---

## 🏅 Why Medallion Architecture?

The Medallion Architecture separates data into logical processing layers.

| Layer  | Purpose                       |
| ------ | ----------------------------- |
| 🥉 Bronze | Raw data ingestion            |
| 🥈 Silver | Cleansed and validated data   |
| 🥇 Gold   | Aggregated business analytics |

### 🏅 Advantages

- 📈 Better scalability
- 🐛 Easier debugging
- ✨ Improved data quality
- ⚖️ Separation of responsibilities
- 🏢 Enterprise-ready architecture
- ⚡ Faster reporting

---

## 📊 Power BI Dashboard

The Gold layer is connected to Power BI to create an executive dashboard.

### 📊 Dashboard Features

#### 📊 Executive KPIs

- 💰 Total Revenue
- 📦 Total Orders
- 👥 Total Customers
- 📈 Average Order Value

---

#### 📈 Monthly Revenue Trend

Visualizes monthly revenue across multiple years.

Helps identify:

- 🌤️ Seasonality
- 📈 Growth trends
- 📉 Revenue fluctuations

---

#### 💳 Payment Method Distribution

Displays:

- 📱 UPI
- 💳 Credit Card
- 💳 Debit Card
- 💵 Cash
- 🌐 Net Banking

Used for customer payment behavior analysis.

---

#### 🗺️ State Sales Analysis

Shows revenue generated by each state.

Supports geographical business analysis.

---

Additional dashboard pages can include:

- 🏷️ Product Performance
- 👔 Employee Performance
- 📊 Category Analysis
- 🗺️ Regional Sales
- 💡 Executive Insights

---

## 🔄 Project Workflow

```bash
📁 CSV Files
      │
      ▼
☁️ Azure Data Lake Storage Gen2
      │
      ▼
🔧 Azure Data Factory
      │
      ▼
🥉 Bronze Layer
      │
      ▼
🥈 Silver Layer
      │
      ▼
🥇 Gold Layer
      │
      ▼
📊 Power BI Dashboard
      │
      ▼
🎯 Business Insights
```

---

## 🎓 Key Learnings

Through this project, I gained hands-on experience with:

- 🏗️ Designing a modern Lakehouse architecture
- 🔧 Building data pipelines using Azure Data Factory
- 🏅 Implementing the Medallion Architecture
- ⚡ Processing large datasets using Azure Databricks
- 🐍 Writing SQL and PySpark transformations
- 📊 Creating analytical Gold-layer tables
- 📈 Building executive dashboards in Power BI
- ☁️ Working with cloud-native data engineering services
- 🐙 Organizing projects using GitHub

---

## 📂 Project Structure

```bash
Enterprise-Sales-Analytics_DataEngineering
│
├── 📁 data/
│   ├── 👤 customers.csv
│   ├── 👔 employees.csv
│   ├── 📦 orders.csv
│   ├── 🛒 orderitems.csv
│   ├── 🏷️ products.csv
│   └── 💳 payments.csv
│
├── 📁 notebooks/
│   ├── 🥉 bronze_ingestion.py
│   ├── 🥈 silver_transformation.py
│   ├── 🥇 gold_aggregation.py
│
├── 📁 adf/
│   └── 🔧 sales_pipeline.json
│
├── 📁 powerbi/
│   └── 📊 Executive_Overview.pbix
│
├── 📁 screenshots/
│
├── 📁 architecture/
│   └── 🏗️ architecture.png
│
├── 📄 README.md
│
└── 📄 LICENSE
```

---

## 🚀 Future Enhancements

- 🔄 Incremental data loading
- 📡 Change Data Capture (CDC)
- ⚡ Real-time streaming with Azure Event Hubs
- 🏅 Delta Live Tables (DLT)
- 📊 Data quality monitoring
- 🔗 Azure Synapse integration
- 🔄 CI/CD using Azure DevOps or GitHub Actions
- 🔒 Row-level security in Power BI
- ⏰ Automated pipeline scheduling and monitoring

---

## ✅ Conclusion

This project demonstrates a complete end-to-end Azure Data Engineering workflow that mirrors enterprise practices. Starting from raw sales data, it uses Azure Data Lake Storage for scalable storage, Azure Data Factory for orchestration, Azure Databricks with the Medallion Architecture for data transformation, and Power BI for executive reporting. The layered design improves data quality, performance, and maintainability, while the final dashboards provide actionable insights for business decision-making.

---

## Images

![Data factory](https://github.com/NivedhReddy2048/Enterprise-Sales-Analytics_DataEngineering/blob/main/Images/AzureDataFactory/Datafactory_Main.png?raw=true)

![Admin Dashboard](https://github.com/NivedhReddy2048/Enterprise-Sales-Analytics_DataEngineering/blob/main/Images/AzureDatabricks/db_2.png?raw=true)

![Admin Dashboard](https://github.com/NivedhReddy2048/Enterprise-Sales-Analytics_DataEngineering/blob/main/Images/AzureDatabricks/db_3.png?raw=true)

---

## 👨‍💻 Author

**🚀 Nivedh Pingili**

**📊 Enterprise Sales Analytics – Azure Data Engineering Project**

**🛠️ Technologies:** Azure Data Lake Storage Gen2 • Azure Data Factory • Azure Databricks • PySpark • SQL • Delta Tables • Power BI • GitHub
