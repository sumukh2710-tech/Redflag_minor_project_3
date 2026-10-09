# 🚩 RedFlag – Fraud Detection Analysis

**SQL-Based Transaction Monitoring and Suspicious Activity Detection**

RedFlag is a SQL-based fraud detection and transaction analysis project designed to identify potentially suspicious financial activities using transaction patterns, user behavior, payment information, and location-based anomalies.

The project uses **MySQL** to analyze transaction data, generate structured reports, and highlight suspicious activities through 12 fraud-detection patterns.

## 📌 Project Overview

Financial fraud can involve unusually frequent transactions, repeated payment failures, suspicious refund behavior, abnormal transaction amounts, and unexpected changes in transaction locations.

RedFlag analyzes transaction records using SQL queries to identify these patterns and produce readable, table-based reports that support further investigation.

### 🎯 Objectives

- Analyze transaction data using SQL.
- Identify potentially suspicious transaction patterns.
- Generate structured reports using aggregate functions and filtering.
- Analyze users, merchants, payment methods, transaction amounts, and locations.
- Improve query efficiency through appropriate indexing and optimized query logic.
- Support data-driven fraud investigation and risk monitoring.

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| MySQL 8.0+ | SQL-based data analysis |
| MySQL Workbench | Query execution and result visualization |
| SQL | Data extraction, aggregation, filtering, and fraud-pattern detection |
| CSV | Transaction dataset import, if applicable |

## 🔍 Fraud Detection Patterns

The project analyzes 12 types of potentially suspicious activity.

| No. | Detection Pattern | Description |
|---:|---|---|
| 1 | High-Frequency Transactions | Detects unusually frequent transactions within a short time window. |
| 2 | Round-Amount Transactions | Identifies repeated transactions involving round amounts. |
| 3 | Card Testing Activity | Highlights multiple failed payment attempts that may indicate card testing. |
| 4 | Quick Retry After Failure | Identifies repeated transaction attempts within a short interval after failure. |
| 5 | Odd-Hour Transactions | Flags activity during unusual hours, such as midnight to early morning. |
| 6 | Possible Mule Accounts | Highlights suspicious incoming and outgoing transaction flows. |
| 7 | Refund Abuse | Identifies users with unusually frequent refunds or high refunded amounts. |
| 8 | Merchant Concentration | Detects users conducting a disproportionately high share of transactions with one merchant. |
| 9 | Transaction Structuring | Identifies repeated transactions just below a specified threshold. |
| 10 | Dormant Account Reactivation | Flags accounts that resume activity after a prolonged inactive period. |
| 11 | Unusual Transaction Spikes | Identifies transaction amounts significantly higher than a user's normal activity. |
| 12 | Suspicious Location Changes | Highlights transactions occurring in different locations within a short time interval. |

**Note:** These rules identify potential red flags. A flagged transaction is not automatically confirmed fraud.

## 📊 Reports and Tabular Outputs

RedFlag organizes the analysis into structured SQL result tables.

### 1. Dataset Overview

Provides a high-level summary of the transaction dataset.

| Metric | Description |
|---|---|
| Total Transactions | Number of transaction records |
| Unique Users | Number of distinct users |
| Unique Merchants | Number of distinct merchants |
| Unique Cities | Number of distinct transaction locations |
| Total Transaction Value | Sum of transaction amounts |
| Average Transaction Amount | Average value per transaction |

### 2. Transaction Status Analysis

Summarizes successful and failed transactions.

| Status | Metrics |
|---|---|
| Successful | Transaction count and percentage |
| Failed | Transaction count and percentage |
| Total | Overall transaction count |

### 3. Payment Mode Analysis

Compares transaction behavior across available payment methods.

| Payment Mode | Metrics |
|---|---|
| UPI | Transaction count, total value, average amount |
| Card | Transaction count, total value, average amount |
| Wallet | Transaction count, total value, average amount |
| Net Banking | Transaction count, total value, average amount |

*The categories displayed depend on the values present in the dataset.*

### 4. City-Wise Analysis

Examines transaction distribution and failures across locations, helping identify unusual concentrations of activity.

### 5. Suspicious Activity Reports

Each fraud-detection pattern generates a dedicated result table containing relevant fields such as user ID, transaction count, amount, time interval, merchant, or location.

The exact columns depend on the detection rule and available dataset fields.

## ⚙️ SQL Concepts Used

- `SELECT`, `WHERE`, and `ORDER BY`
- `GROUP BY` and `HAVING`
- Aggregate functions: `COUNT()`, `SUM()`, and `AVG()`
- Date and time functions
- Conditional logic using `CASE`
- Subqueries and `EXISTS`
- Common Table Expressions (CTEs), where appropriate
- Window functions, where appropriate
- Indexing and query optimization

## 🚀 Getting Started

### Prerequisites

- MySQL Server 8.0 or later
- MySQL Workbench
- The transaction dataset used by the project
- The project's SQL script

### Step 1: Clone the Repository

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
cd <YOUR_REPOSITORY_FOLDER>
```

Replace the placeholders with your actual GitHub repository URL and folder name.

### Step 2: Import the Dataset

Import your transaction dataset into MySQL Workbench and create or select the database and table expected by the SQL script.

For example, if your table is named `transactions` inside the `redflag` database:

```sql
USE redflag;

SELECT *
FROM transactions
LIMIT 10;
```

Confirm that the column names and data types match the SQL queries before running the complete analysis.

### Step 3: Execute the SQL Script

1. Open MySQL Workbench.
2. Connect to your MySQL Server.
3. Open the project's SQL file.
4. Confirm the database and table names.
5. Execute the queries.
6. Review the result grids for the summary reports and fraud-detection patterns.

### Step 4: Review the Results

Examine the generated tables to identify suspicious activity, compare transaction behavior, and determine which records require further investigation.

## ⚡ Query Optimization

The project can use several techniques to improve query performance:

- Create indexes on frequently filtered or joined columns.
- Use composite indexes when queries repeatedly filter by combinations of columns.
- Filter records before performing expensive aggregations when logically appropriate.
- Avoid unnecessary `SELECT *` statements in analytical queries.
- Use `EXPLAIN` to inspect query execution plans.
- Avoid duplicate calculations by reusing suitable intermediate results.
- Validate query performance against the actual dataset size.

Example:

```sql
EXPLAIN
SELECT user_id, COUNT(*) AS transaction_count
FROM redflag.transactions
GROUP BY user_id;
```

Index selection should depend on the actual schema, query patterns, and execution plans. Indexes can improve read performance but add storage and write overhead.

## 🔐 Data Integrity and Responsible Use

- The analysis should preserve the original transaction records.
- Fraud-detection thresholds should be configurable and validated against the dataset.
- Sensitive transaction and user information should be handled securely.
- Suspicious activity should be reviewed before any account or transaction is classified as fraudulent.
- Query results should be validated against known cases where possible.

## 📁 Project Structure

An example repository structure is shown below. Adjust the filenames to match your actual repository.

```text
RedFlag-Fraud-Detection/
├── README.md
├── redflag_fraud_detection.sql
├── dataset/
│   └── transactions.csv
└── reports/
    └── fraud_detection_results/
```

Do not upload confidential or personally identifiable financial data to a public repository.

## 💡 Applications

- Financial transaction monitoring
- Payment fraud investigation
- Banking and fintech analytics
- Suspicious account activity analysis
- Merchant risk monitoring
- SQL-based data analytics projects

## 🔮 Future Enhancements

- Build an interactive fraud-monitoring dashboard using Power BI or Tableau.
- Integrate Python for statistical analysis and anomaly detection.
- Develop machine-learning models for transaction risk scoring.
- Automate scheduled transaction analysis and reporting.
- Introduce configurable thresholds and severity levels.
- Evaluate detection accuracy using labeled transaction data.

## 👨‍💻 Author

**Sumukh R.**

Computer Science and Business Systems  
Maharaja Institute of Technology Mysuru

## ⭐ Conclusion

RedFlag demonstrates how SQL can be used to analyze financial transactions, identify suspicious behavioral patterns, and generate structured reports for fraud investigation.

By combining analytical queries, clear tabular outputs, and query optimization techniques, the project provides a foundation for more advanced fraud-monitoring solutions.

If you find this project useful, consider giving the repository a ⭐ on GitHub.

---

*Disclaimer: RedFlag is an analytical project for educational and investigative purposes. Its detection rules are indicators of potentially suspicious activity, not proof of fraud.*
