# Uber End-to-End Data Engineering & Analytics Project

## 🎯 Project Goal
The objective of this project is to build an automated, end-to-end ETL pipeline that extracts raw Uber trip data, transforms it into a structured data model, and loads it into a cloud data warehouse for analysis. The final pipeline runs on a cloud virtual machine, orchestrating data moving from storage to production-ready analytical dashboards.

---

## 💾 Data Source
The dataset used in this project originates from the open-source **TLC Trip Record Data** provided by the **New York City Taxi and Limousine Commission (TLC)**. 

* **Dataset Details:** It includes fields capturing pick-up and drop-off dates/times, pick-up and drop-off locations, trip distances, itemized fares, rate types, payment types, and driver-reported passenger counts.
* **Access:** The public data can be found and downloaded via the [NYC Open Data Portal](https://opendata.cityofnewyork.us/) or the official [NYC TLC Trip Record Data Page](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page).


---

## 🛠️ Tech Stack & Tools
* **Orchestration:** Mage AI
* **Compute:** Google Cloud Compute Engine (Virtual Machine)
* **Storage:** Google Cloud Storage (GCS)
* **Data Warehouse:** Google BigQuery
* **Data Transformation:** Python & JupyterLab
* **Business Intelligence:** Tableau

---

## 🏗️ Architecture & Workflow
<img width="629" height="197" alt="image" src="https://github.com/user-attachments/assets/92d84b3f-d364-446c-bddd-593e53bf71b6" />

---

## 🚀 Step-by-Step Implementation

### Step 1: Data Modeling & Schema Design
To optimize analytical query performance, the raw dataset was restructured into a relational star schema composed of dimension tables and a centralized fact table.

![Uber Data Model Data Diagram](https://github.com/user-attachments/assets/cd4d9b66-6890-4f4a-aff0-1060a2b33457)

### Step 2: Prototype Transformations in JupyterLab
Using Python and `pandas`, the initial extraction and dimension mapping logic were prototyped and validated locally in a Jupyter Notebook to ensure data integrity before scaling to production scripts.

### Step 3: Data Ingestion to Google Cloud Storage
The raw Uber trip dataset was securely uploaded into a Google Cloud Storage bucket to serve as the landing area (data lake) for our automated pipeline.

![Google Cloud Storage Bucket View](https://github.com/user-attachments/assets/30d24f44-00ee-4df9-a8d9-7b3df65e5c61)

### Step 4: Automate the ETL Pipeline via Mage on a VM
A Virtual Machine instance was provisioned on GCP to host **Mage AI**. The data pipeline was configured to automatically ingest data from GCS, execute the Python transformation logic, and load the clean, structured tables directly into BigQuery.

![Mage AI ETL Pipeline Execution](https://github.com/user-attachments/assets/122c994a-9937-49f0-9f0f-880e2dbf26f6)

### Step 5: Interactive Analytics in Tableau
With the clean star-schema loaded into Google BigQuery, a live data connection was established with Tableau to build a dynamic executive dashboard tracking hourly metrics, pickup volumes by borough, and vendor performance.

![Final Tableau Analytics Dashboard](https://github.com/user-attachments/assets/6fb1e0cd-704f-41d4-8d21-be2c728bcd22)

---
## 📊 Key Results & Insights

The final interactive Tableau dashboard yields critical operational insights from the processed Uber dataset:

* **Peak Operational Hours:** The *Hourly Passenger Volume* analysis reveals a distinct drop in ride demand during the early morning hours (dipping significantly around 5:00 AM) before surging rapidly through the afternoon, peaking around 1:00 PM to 2:00 PM.
* **Vendor Revenue Performance:** *Curb Mobility, LLC* dominates the revenue share for this dataset, pulling in over $2,000K in total revenue, drastically outperforming *Creative Mobile Technologies, LLC* and *Helix*.
* **Geographic Concentration:** The *Pick Up Location* map visually underscores that the vast majority of ride demand is heavily clustered within Manhattan, with minor bubbles scaling out to Queens and Brooklyn.

---

## ⚡ Engineering Impact: Why Automated ETL Matters

A core achievement of this project was migrating from local, manual notebook executions to a **fully automated production pipeline** running via Mage AI on a cloud VM instance. 

Automating this data infrastructure provides several vital engineering benefits:

1. **Scalability & Cost Efficiency:** Processing raw data manually scales poorly as data volumes grow. Automating workflows inside Google Cloud allows compute resources to scale dynamically, keeping warehouse tables up to date with zero human intervention.
2. **Data Consistency & Reliability:** By removing manual data uploads and manual data cleaning steps, we eliminate human error. Mage handles execution retries, structured logging, and strict data validation at every node in the pipeline.
3. **From Data Lake to BI in Real Time:** Because the ETL continuously cleans and pipes data directly into BigQuery, business tools like Tableau are always backed by a single source of truth that updates dynamically, providing decision-makers with fresh metrics instantly.
