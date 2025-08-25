# 🚕 NYC Taxi Data Analytics  

Analyzing **NYC Yellow and Green Taxi Trip Records** to identify key **trends, routes, and patterns** using an **ELT (Extract, Load, Transform) pipeline**.  
This project integrates **Airflow, DBT, GCP (BigQuery + GCS), Terraform, and Looker Studio** to deliver a modern, scalable data analytics workflow.  
<img width="1864" height="1515" alt="Image" src="https://github.com/user-attachments/assets/3ee673f0-95e5-4a7a-bdac-bf8ee0cb8042" />
---

## 📑 Table of Contents  
- [Overview](#overview)  
- [Source Data](#source-data)  
- [Architecture](#architecture)  
- [Infrastructure](#infrastructure)  
- [ETL Pipeline](#etl-pipeline)  
- [Airflow DAGs](#airflow-dags)  
- [DBT Cloud](#dbt-cloud)  
- [Dashboard](#dashboard)  
- [Key Learnings](#key-learnings)  
- [Acknowledgments](#acknowledgments)  

---

## 📂 Overview  

- **Goal:** Explore taxi trip records to extract meaningful insights.  
- **Pipeline:**  
  1. **Extract** raw taxi data from the TLC website.  
  2. **Load** data into **Google Cloud Storage (GCS)** and **BigQuery**.  
  3. **Transform** data using **DBT Cloud**.  
  4. **Visualize** insights using **Looker Studio dashboards**.  

---

## 🗂️ Source Data  

- **Official TLC Trip Data Portal:** [NYC Taxi Trip Records](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page)  
- **Schemas:**  
  - [Yellow Trips Schema PDF](https://www.nyc.gov/assets/tlc/downloads/pdf/data_dictionary_trip_records_yellow.pdf)  
  - [Green Trips Schema PDF](https://www.nyc.gov/assets/tlc/downloads/pdf/data_dictionary_trip_records_green.pdf)  

---

## 🏗️ Architecture  

**ELT Pipeline Flow:**  

![Architecture Diagram](Alt text)  

1. Data extracted from TLC open data portal.  
2. Loaded into **GCS (data lake)**.  
3. Loaded into **BigQuery** as **external and partitioned tables**.  
4. **DBT Cloud** applies transformations and creates refined tables in BigQuery.  
5. **Looker Studio** connects to BigQuery for visualization.  

---

## ⚙️ Infrastructure  
<img width="1864" height="1515" alt="Image" src="https://github.com/user-attachments/assets/bd9e915e-35dd-498f-a864-a4fa46d6b0ec" />

- **Terraform** → Infrastructure provisioning.  
- **Docker** → Containerized execution environment.  
- **Airflow** → Pipeline orchestration and scheduling.  
- **Google Cloud Storage (GCS)** → Data lake.  
- **BigQuery** → Data warehouse.  
- **Postgres** → Development/testing database.  
- **DBT Cloud** → Transformations & data modeling.  

---

## 🔄 ETL Pipeline  

### Airflow DAGs  

1. **`src_to_gcs_dag.py`**  
   - Downloads taxi trip data from TLC portal.  
   - Uploads to **GCS bucket**.  
   - Cleans up local storage on VM.  
<img width="2661" height="663" alt="Image" src="https://github.com/user-attachments/assets/ebaf9315-cb48-44d6-a42f-82d44001ac1d" />

2. **`gcs_to_bq_dag.py`**  
   - Organizes files within GCS.  
   - Creates **external tables** in BigQuery.  
   - Builds **partitioned tables** from external tables for optimization.  
<img width="2764" height="639" alt="image" src="https://github.com/user-attachments/assets/d6e093be-b824-45ae-9ab8-838ff6283bad" />


3. **`src_to_postgres_dag.py`**  
   - Loads data from TLC portal into a **Postgres database** for testing/development.  

---

### DBT Cloud  

- Transformations are defined and executed in **DBT Cloud**.  
- Refined models are written back into **BigQuery**.  
- DBT Cloud project files are available in this repo:  
  👉 [DBT Models Repo](https://github.com/LaeekAhmed/dtc-de-analytics)  

---

## 📊 Dashboard  

- **Looker Studio Dashboard:** [View Dashboard ↗](looker studio dashboard)  
- Provides insights such as:  
  - Popular pickup/drop-off locations.  
  - Peak hours and seasonal trends.  
  - Fare patterns and revenue insights.  
  - Comparison between **Yellow vs Green Taxi trips**.  

<img width="2399" height="1743" alt="image" src="https://github.com/user-attachments/assets/b8cc1149-664e-41e7-8435-102c8c472fc7" />

---

## 🌐 Key Learnings  

✅ Building **ELT pipelines** with Airflow, DBT, and GCP.  
✅ Using **Terraform** for reproducible infrastructure.  
✅ Efficient data management with **partitioned tables in BigQuery**.  
✅ Creating **interactive BI dashboards** with Looker Studio.  

---

## 🎉 Acknowledgments  

- **NYC Taxi & Limousine Commission (TLC)** for providing open datasets.  
- **DBT + GCP + Airflow communities** for open-source workflows and inspiration.  

---
