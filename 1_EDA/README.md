# Exploratory Data Analysis w/ SQL: Job Market Analysis

![Project Overview](/images/1_1_Project1_EDA.png)

A SQL project analyzing the data engineer job market using real world job posting data. It demonstrates my ability to **write production-quality analytical SQL, design efficient queries, and turn business questions into data-driven insights.**

## 🧾 Executive Summary

- ✅ Project scope: Built 3 analytical queries that answer key questions about the data engineer job market
- ✅ Data modeling: Used multi-table joins across fact and dimension tables to extract insights
- ✅ Analytics: Applied aggregations, filtering, and sorting to find top skills by demand, salary, and overall value
- ✅ Outcomes: Delivered actionable insights on SQL/Python dominance, cloud trends, and salary patterns

If you only have a minute, review these:

1. [`01_Top_Demanded_Skills.sql`](/1_EDA/01_Top_Demanded_Skills.sql) - demand analysis with multi-table joins
2. [`02_Top_Paying_Skills.sql`](/1_EDA/02_Top_Paying_Skills.sql) - salary analysis with aggregations
3. [`03_Optimal_Skills.sql`](/1_EDA/03_Optimal_Skills.sql) - combined demand/salary optimization query

## 🧩 Problem & Context

Job market analysts need to answer questions like:

- 🎯 **Most in-demand:** _Which skills are most in-demand for data engineers?_
- 💰 **Highest paid:** _Which skills command the highest salaries?_
- ⚖️ **Best trade-off:** _What is the optimal skill set balancing demand and compensation?_

This project analyzes a **data warehouse** built using a star schema design. The warehouse structure consists of:

![](../images/1_2_Data_Warehouse.png)

- **Fact Table:** _job_postings_fact_ - Central table containing job posting details (job titles, locations, salaries, dates, etc.)
- **Dimension Table:**
  - _company_dim_ - Company information linked to job postings
  - _skills_dim_ - Skills catalog with skill names and types
- **Bridge Table:** _skills_job_dim_ - Resolves the many-to-many relationship between job postings and skills

By querying across these interconnected tables, I extracted insights about skill demand, salary patterns, and optimal skill combinations for data engineering roles.

## 🧰 Tech Stack

- 🐤 **Query Engine:** DuckDB for fast OLAP-style analytical queries
- 🧮 **Language:** SQL (ANSI-style with analytical functions)
- 📊 **Data Model:** Star schema with fact + dimension + bridge tables
- 🛠️ **Development:** VS Code for SQL editing + Terminal for DuckDB CLI
- 📦 **Version Control:** Git/GitHub for versioned SQL scripts

## 🏗️ Analysis Overview

### Query Structure

1. [Top Demand Skills](/1_EDA/01_Top_Demanded_Skills.sql) - Identifies the 10 most in-demand skills for remote data engineer positions
2. [Top Paying Skills](/1_EDA/02_Top_Paying_Skills.sql) - Analyzes the 25 highest-paying skills with salary and demand metrics
3. [Optimal Skills](/1_EDA/03_Optimal_Skills.sql) - Calculates an optimal score using natural log of demand combined with median salary to identify the most valuable skills to learn

### Key Insights

- 🧠 Core Languages: SQL and Python each appear in ~29,000 job postings, making them the most demanded skills
- ☁️ Cloud platforms: AWS and Azure are critical for modern data engineering roles
- 🧱 Infra & tooling: Kubernetes, Docker, and Terraform are associated with premium salaries
- 🔢 Big data tools: Apache Spark shows strong demand with competitive compensation

## 💻 SQL Skills Demonstrated

### Query Design & Optimization

- Complex Joins: Multi-table INNER JOIN operations across job_postings_fact, skills_job_dim, and skills_dim
- Aggregations: COUNT(), MEDIAN(), ROUND() for statistical analysis
- Filtering: Boolean logic with WHERE clauses and multiple conditions (job_title_short, job_work_from_home, salary_year_avg IS NOT NULL)
- Sorting & Limiting: ORDER BY with DESC and LIMIT for top-N analysis

### Data Analysis Techniques

- Grouping: GROUP BY for categorical analysis by skill
- Mathematical Functions: LN() for natural logarithm transformation to normalize demand metrics
- Calculated Metrics: Derived optimal score combining log-transformed demand with median salary
- HAVING Clause: Filtering aggregated results (skills with >= 100 postings)
- NULL Handling: Proper filtering of incomplete records (salary_year_avg IS NOT NULL)
