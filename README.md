# spark-employee-insights-pipeline-BigData
An end-to-end ETL pipeline built with Apache Spark (PySpark) that cleans, enriches, and analyzes employee records to generate dashboard-style workforce insights.

## Overview

This project simulates a real-world Big Data workflow: extracting raw employee data, cleaning it, enriching it with a derived feature, and producing multiple aggregated summary views — the kind of pipeline used to feed business dashboards in industry.

## Dataset

Synthetic employee records (1500 rows) with intentional data quality issues (missing values, duplicate rows) to practice real-world cleaning techniques.

**Columns:** `emp_id`, `department`, `salary`, `age`, `city`, `status`, `years_experience`

## Tools Used

- **PySpark** (DataFrame API + Spark SQL) — data cleaning, transformation, and aggregation
- **pandas** — exporting final results to CSV

## Pipeline Steps

1. **Extract** — Load raw CSV into a Spark DataFrame
2. **Transform (Clean)** — Remove duplicate rows; fill missing `salary` (with dataset average), `city`, and `department` (with `"Unknown"`)
3. **Transform (Enrich)** — Add a `seniority_level` column (Senior / Mid / Junior) based on `years_experience`
4. **Transform (Aggregate)** — Generate 5 summary views answering distinct business questions
5. **Load** — Export each summary view as a separate CSV into `output/`

## Key Insights

- **Headcount:** Finance has the largest headcount (270 employees); Support the smallest (216).
- **Salary vs. Seniority:** HR (Mid-level) has the highest average salary (₹96,041) of any department-seniority group — higher than any Senior-level average, showing salary isn't purely seniority-driven.
- **Top-Paying Department:** Engineering leads overall with an average salary of ₹90,034.72.
- **Status Distribution:** Employment status (Active/Inactive/On Leave) is fairly evenly spread across departments, with no extreme outliers.
- **Workforce Seniority:** 64.4% of employees are Senior-level, indicating an experienced, senior-heavy workforce.
- **Salary by City:** Mumbai has the highest average salary (₹90,194.96); Delhi the lowest (₹83,497.85) — a relatively modest ~8% spread.
