# Job-Market-Analytics-End-to-End-BI-Engineering-Case-Study

Overview

This project demonstrates a complete Business Intelligence workflow — from raw data ingestion to executive-level dashboard reporting.

The objective was to transform raw job posting data into a structured analytical model using SQL Server and build an interactive Power BI dashboard capable of answering key workforce intelligence questions such as:

How is hiring demand evolving over time?

Which industries and locations dominate hiring?

What job roles are most in demand?

How do experience requirements correlate with salary?

How competitive is the applicant market?

The solution mirrors enterprise BI architecture by separating data transformation, modeling, and reporting layers.

🏗 Architecture
Raw Job Data
   ↓
SQL Staging & Cleaning
   ↓
Star Schema Modeling (Fact + Dimensions)
   ↓
Analytical Reporting View
   ↓
Power BI Dashboard


The design ensures scalability, performance optimization, and reporting abstraction.

🗄 Data Engineering Layer (SQL Server)
1️⃣ Raw Ingestion

Loaded 25,114 job postings (17 attributes) into:

raw_job_postings

This table stores source-level data without transformations.

2️⃣ Data Cleaning & Staging

Created:

stg_job_postings

Key transformations:

Standardized data types

Extracted job_year from posting date

Cleaned text fields

Removed duplicates

Handled 93% null salary fields

Normalized salary ranges

Structured experience fields

This ensures data consistency before modeling.

3️⃣ Dimensional Modeling (Star Schema)

Designed a scalable star schema:

Fact Table

fact_job_postings

Contains:

Salary metrics

Applicant counts

Experience requirements

Foreign keys to dimensions

Dimension Tables

dim_job

dim_company

dim_location

Benefits:

Optimized performance

Clear separation of concerns

Flexible slicing & filtering

Industry-standard BI modeling

4️⃣ Analytical Reporting View

Created:

vw_job_market_analytics

This reporting view joins fact and dimension tables and exposes analysis-ready columns to Power BI.

This prevents dashboards from querying raw tables directly and improves maintainability.

📊 Business Intelligence Layer (Power BI)

Power BI connects directly to the analytical view.

Core DAX Measures
Total Job Postings = DISTINCTCOUNT(job_posting_id)
Total Applicants = SUM(number_of_applicants)
Avg Minimum Salary = AVERAGE(minimum_pay)
Avg Maximum Salary = AVERAGE(maximum_pay)
Avg Years of Experience = AVERAGE(years_of_experience)


All KPIs were built using explicit measures to ensure proper filter context behavior.

📈 Dashboard Features
🔹 Executive KPI Panel

Total job postings

Salary averages

Experience requirements

Applicant volume

🔹 Hiring Trend Analysis

Time-series analysis showing hiring growth and post-pandemic recovery patterns.

🔹 Top N Market Analysis

Top industries by hiring

Top job titles

Top geographic markets

🔹 Interactive Slicers

Filter by:

Year

Industry

Job level

Location

Enables multi-dimensional workforce analysis.

📌 Key Insights

Hiring demand shows steady year-over-year growth.

Technology and internet industries dominate recruitment.

Major metropolitan regions account for most postings.

Mid-Senior roles represent the largest hiring segment.

Higher experience requirements correlate with higher salary bands.

Applicant volume suggests increasing market competitiveness.

🛠 Tech Stack

SQL Server

T-SQL

Star Schema Dimensional Modeling

Power BI

DAX

Data Modeling

Git Version Control

📁 Repository Structure
├── sql
│   ├── 01_create_database.sql
│   ├── 02_create_tables.sql
│   ├── 03_data_cleaning.sql
│   ├── 04_star_schema.sql
│   ├── 05_create_view.sql
│
├── Job_Market_Analytics_Dashboard.pbix
├── README.md

🚀 Future Enhancements

Year-over-Year growth %

Applicant-to-job competition ratio

Salary distribution histogram

Drill-through reporting

Performance optimization with indexing

DirectQuery integration

🎯 Conclusion

This project demonstrates:

End-to-end BI architecture design

SQL transformation pipelines

Dimensional data modeling

Analytical view abstraction

Executive dashboard development

Structured insight communication

The solution emphasizes scalability, clarity, and maintainability — following enterprise BI best practices.
