# Lec Task: GreenStream Energy Serverless ETL Architecture

## 1. Project Overview & Business Case
**GreenStream Energy** is a major utility provider managing millions of **Smart Meters (IoT devices)**. The challenge was to process a massive influx of high-frequency energy readings and convert them into high-quality, actionable data assets.

This project implements a state-of-the-art **Serverless ETL (Extract, Transform, Load) Pipeline**. The architecture is designed to be event-driven, cost-effective, and highly scalable, ensuring that raw energy data is refined for both real-time operational monitoring and long-term analytical research.

## 2. System Architecture
The system follows a modern serverless design where compute resources are only utilized when data is present, reducing overhead costs significantly.

### The Pipeline Flow:
1.  **Ingestion Zone:** IoT devices upload raw CSV files to a transient "Landing Zone" in object storage.
2.  **Event Trigger:** Each upload automatically triggers the **Serverless Orchestrator**, which manages the lifecycle of the data record.
3.  **Transformation Layers (T1-T3):** Data passes through three distinct serverless workers, each adding a layer of quality and optimization.
4.  **Dual-Destination Output:** Cleaned data is simultaneously sent to a SQL database (Hot Path) and a Parquet archive (Cold Path).

## 3. The ETL Transformation Process
To ensure data integrity, the pipeline executes three critical transformation stages:

### T1: Standardization & Validation
* **Unit Conversion:** Automatically detects readings in Watts (W) and converts them to Kilowatts (kW).
* **Schema Enforcement:** Validates that `MeterID` is an integer and timestamps follow the ISO-8601 standard.

### T2: Data Cleaning & Imputation
* **Missing Value Handling:** Uses linear interpolation to fill gaps in time-series data, ensuring continuity for forecasting models.
* **Outlier Detection:** Filters out invalid spikes (e.g., negative values or extreme readings) caused by sensor malfunctions.

### T3: Format Optimization
* **Columnar Conversion:** Converts the final cleaned data from CSV to **Parquet** format. This drastically reduces storage costs and speeds up complex analytical queries.

## 4. Business Rules & Logic
The transformation logic is governed by specific business rules designed to refine "Dark Data" into high-value assets:

| Rule Category | Business Logic Applied | Purpose |
| :--- | :--- | :--- |
| **Standardization** | `Value = Value / 1000` if Unit is "W". | Ensures all grid data is mathematically consistent. |
| **Data Quality** | Check for NULL values in `ReadingValue`. | Prevents errors in downstream aggregate functions. |
| **Feature Engineering** | Calculate peak usage hours from timestamps. | Enables the company to identify high-demand periods. |
| **Format Conversion** | Compress raw CSV into snappy-parquet. | Optimized for long-term "Cold Data" storage. |

## 5. Storage Strategy: Hot vs. Cold Data
The pipeline feeds into a hybrid storage model to satisfy different business needs:

* **Hot Data (Structured SQL):** This serving layer powers **Real-Time Dashboards**. It allows the operations team to monitor grid load and identify peak energy periods immediately.
* **Cold Data (Analytics Archive):** Optimized Parquet files stored in a Data Lake. This is designed for Data Scientists to perform historical analysis over several years without the high cost of traditional databases.

## 6. Resilience & Error Handling
A critical feature of this architecture is its ability to handle failures without data loss:
* **Retry Logic:** The Orchestrator automatically retries failed transformation steps up to 3 times.
* **Dead Letter Queue (DLQ):** Records that consistently fail validation are moved to a **Quarantine Zone**. This allows for manual inspection and debugging without stopping the entire pipeline.
* **Success Logging:** Every successfully processed file is logged and moved to a "Processed" folder for auditing purposes.

## 7. Tools & Technologies
* **Serverless Computing:** For T1, T2, and T3 transformation workers.
* **Cloud Orchestration:** For managing the state, sequence, and retry logic.
* **Object Storage:** Used for Ingestion, Processed, and Archive zones.
* **SQL Serving Layer:** For structured queries and business intelligence.
