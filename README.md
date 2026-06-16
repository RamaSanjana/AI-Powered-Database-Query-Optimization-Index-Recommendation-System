AI-Powered Database Performance Optimizer
Overview

A real AI-driven DBMS performance optimization tool that connects to live MySQL databases and analyzes actual queries, tables, indexes, and execution plans.

Features include:

Analyze live SQL queries
Visualize execution plans
Recommend indexes
Simulate performance improvements
Rewrite inefficient queries
Interactive Streamlit dashboard

Tech Stack: Python, Streamlit, Plotly, SQLParse, MySQL

Source content:

🚀 Features (18 Implemented & Verified)
#	Feature	Purpose	Status
1	SQL Query Input	Accept SELECT, JOIN, aggregation, and subqueries	✅
2	Query Analyzer	Detect inefficient SQL patterns	✅
3	Optimization Engine	Suggest optimized SQL examples	✅
4	Query Score	Performance score (0–100)	✅
5	Complexity Detection	Classify queries as Simple / Moderate / Complex	✅
6	Index Recommendation	Generate CREATE INDEX statements	✅
7	Cost Estimation	LOW / MEDIUM / HIGH runtime estimation	✅
8	Performance Charts	Visual analytics dashboard	✅
9	Query History	Track analyzed queries	✅
10	Sample Dataset	25 annotated sample queries	✅
11	AI Insights	Natural-language query analysis	✅
12	Optimization Simulation	Compare original vs optimized performance	✅
13	Best Practices Panel	SQL optimization guidelines	✅
14	Architecture Viewer	Interactive architecture diagram	✅
15	Export Reports	JSON / CSV / TXT export	✅
16	Execution Plan Visualizer	Interactive EXPLAIN visualization	✅
17	Index Impact Simulator	Performance gain estimation	✅
18	Query Rewrite Engine	Automatic query rewriting	✅
📁 Project Structure
AI-Powered Database Query Optimization & Index Recommendation System/

├── app.py
├── db_connection.py
├── analyzer.py
├── optimizer.py
├── scoring.py
├── recommendations.py
├── execution_plan.py
├── simulator.py
├── rewrite_engine.py
├── requirements.txt
├── README.md

├── data/
│   └── sample_queries.csv

└── utils/
    ├── __init__.py
    └── helpers.py
🛠️ Setup & Installation
Prerequisites
Python 3.11+
pip
MySQL Server
Install Dependencies
pip install -r requirements.txt
Required Packages
Package	Version
streamlit	≥ 1.32
plotly	≥ 5.18
pandas	≥ 2.0
sqlparse	≥ 0.4.4
mysql-connector-python	Latest
sqlalchemy	Latest
pymysql	Latest
Create Sample Database
CREATE DATABASE company_db;

USE company_db;

CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    department VARCHAR(100),
    salary INT,
    hire_date DATE
);

INSERT INTO employees VALUES
(1,'John','Engineering',90000,'2022-01-10'),
(2,'Alice','HR',60000,'2021-02-15'),
(3,'Bob','Engineering',95000,'2023-03-12'),
(4,'Eve','Finance',80000,'2022-04-18');
Configure Database Connection
DB_CONFIG = {
    "host": "localhost",
    "user": "root",
    "password": "yourpassword",
    "database": "company_db"
}
Run Application
streamlit run app.py

Open:

http://localhost:8501
🏗️ System Architecture
Streamlit Dashboard
        │
        ▼
User SQL Query Input
        │
        ▼
MySQL Database Connection
        │
        ▼
Query Analyzer
        │
        ▼
Performance Scoring Engine
        │
        ▼
Index Recommendation Engine
        │
        ▼
Query Rewrite Engine
        │
        ▼
Execution Plan Visualizer
        │
        ▼
Results Dashboard
🔍 Module Breakdown
analyzer.py
Pattern detection using regex + sqlparse
Detects:
SELECT *
Missing WHERE
Excessive JOINs
Nested subqueries
Missing LIMIT
Leading wildcard LIKE
Function-on-column usage
DISTINCT with JOIN
Aggregate full scans
scoring.py
Base score: 100
16 scoring rules
Returns:
Performance score
Cost estimate
Rows scanned estimate
optimizer.py
8 optimization recommendation generators
Priority-based suggestions
AI-generated query insights
recommendations.py
Generates:
B-tree indexes
Composite indexes
Covering indexes
Full-text indexes
Includes 12 SQL best practices
execution_plan.py
Simulated PostgreSQL-style execution plans
12 execution node types
Cost modeling engine
simulator.py

Provides:

Before/after performance comparison
Score improvement
Cost reduction
Speedup estimation

Impact Levels:

Transformative (≥50×)
Major (≥10×)
Moderate (≥2×)
Minor
rewrite_engine.py

Automatic transformations:

IN Subquery → INNER JOIN
SELECT * → Explicit columns
Function-on-column fix
Leading wildcard detection
LIMIT injection
utils/helpers.py
SQL formatting
Export generation
Session history
UI helper utilities
app.py
Dashboard Tabs
Query Analyzer
Query History
Sample Dataset
Best Practices
Advanced Analysis
Dashboard Components
KPI Cards
Plotly Charts
Export Buttons
Query History Trends
Execution Plan Visualizer
Index Impact Simulator
📊 Scoring Rules
Rule	Type	Score Impact
SELECT *	Penalty	-25
Missing WHERE	Penalty	-20
Excessive JOINs	Penalty	-15
JOIN Present	Penalty	-10
Nested Subquery	Penalty	-10
Missing LIMIT	Penalty	-10
Leading Wildcard LIKE	Penalty	-10
Function on Column	Penalty	-10
Aggregate Without Filter	Penalty	-10
DISTINCT + JOIN	Penalty	-5
WHERE Present	Bonus	+10
LIMIT Present	Bonus	+10
Specific Columns	Bonus	+10
Filter Columns Found	Bonus	+5
GROUP BY	Bonus	+5
ORDER BY	Bonus	+5
📈 Cost Estimation
Score	Cost	Rows Scanned
80–100	LOW	~1K–10K
50–79	MEDIUM	~10K–500K
0–49	HIGH	~1M+
📤 Export Formats
Format	Purpose
JSON	API Integration
CSV	Excel / Reporting
TXT	Documentation / Sharing
🧪 Example Analysis
Input Query
SELECT * FROM orders WHERE customer_id = 10;
Output
Score:        65/100
Complexity:   Moderate
Cost:         MEDIUM
Rows Scanned: ~10K–500K
Recommendations
CREATE INDEX idx_orders_customer_id
ON orders(customer_id);

Performance Improvement:

Original Score: 65
Optimized Score: 95
Gain: +30
🧱 Technologies Used
Technology	Purpose
Python 3.11+	Core Language
Streamlit	Dashboard
Plotly	Visualizations
SQLParse	SQL Parsing
Pandas	Data Processing
MySQL Connector	Database Connectivity
🔧 Troubleshooting
Issue	Solution
No module named 'utils'	Ensure utils/__init__.py exists
CSV Loading Errors	Verify CSV formatting
Database Connection Failure	Check MySQL credentials and service
Advanced Analysis Empty	Run a query first
Charts Not Showing	Upgrade Plotly to ≥ 5.18
