# SQL for Financial Data Analysis & Reporting

![SQL](https://img.shields.io/badge/SQL-Database-blue) ![Tutorial](https://img.shields.io/badge/Type-Tutorial-green) ![Status](https://img.shields.io/badge/Status-In%20Progress-orange)

**Author**: Tonmoy Rashid   
**Created**: 2025-04-12  
**Updated**: 2025-05-15 
**Resource**: [Google Drive](https://drive.google.com/file/d/1ieb6T_-3gyJ7F9i6OeyfG7jnWed6KnHb/view?usp=sharing)

---

## Table of Contents
1. [Installation](#installation)
   - [Docker Desktop on Ubuntu](#Install-Docker-Desktop-on-Ubuntu)
   - [Microsoft SQL Server on Ubuntu](#Install-Microsoft-SQL-Server)
2. [Database Setup](#database-setup)
   - [Create Database and Import Data](#create-database-and-import-data-from-csv)
3. [SQL Queries](#sql-queries)
   - [Getting-started-with-SQL-SELECT](#getting-started-with-sql-select)
   - [SELECT-specific-Columns-and-Rows](#SELECT-specific-Columns-and-Rows)
   - [Selecting-WHERE](#Selecting-WHERE)
   - [Time-Intelligence-Date-Month](#Time-Intelligence-Date-Month)
   - [Time-Intelligence-Part-2-DATEPART](#Time-Intelligence-Part-2-DATEPART)
   - [Time-Intelligence-in-Action-Basic-Example](#Time-Intelligence-in-Action-Basic-Example)
   - [SUM-and-Group](#SUM-and-Group)
   - [Making-and-Using-SubQuery](#Making-and-Using-SubQuery)
   - [PIVOT-data-into-Columns](#PIVOT-data-into-Columns)
   - [Create-VIEW](#Create-VIEW)
   - [JOIN-Tables](#JOIN-Tables)
   - [RIGHT-JOIN-LEFT-JOIN-FULL-JOIN](#RIGHT-JOIN-LEFT-JOIN-FULL-JOIN)
   - [FORMAT-numbers](#FORMAT-numbers)
   - [Preparing-Profit-Loss-Statement](#Preparing-Profit-Loss-Statement)
   - [Preparing-Balance-Sheet-Understanding-the-problem](#Preparing-Balance-Sheet-Understanding-the-problem)
   - [SQL-for-Cumulative-SUM](#SQL-for-Cumulative-SUM)
   - [Cumulative-SUM-Part-2](#Cumulative-SUM-Part-2)
   - [Preparing Balance-Sheet](#Preparing-Balance-Sheet)
   - [Balance-Sheet-Final](#Balance-Sheet-Final)
   - [Learning-the-CASE-WHEN-statement](#Learning-the-CASE-WHEN-statement)
   - [Calculating-Sales](#Calculating-Sales)
   - [Calculating-Gross-Profit-and-Net-Profit](#Calculating-Gross-Profit-and-Net-Profit)
   - [Calculating-EBITDA-Operating-Profit-and-PBIT](#Calculating-EBITDA-Operating-Profit-and-PBIT)
   - [Creating-view-for-Gross-Profit-Margin-EBITDA-Operating-Profit-and-PBIT](#Creating-view-for-Gross-Profit-Margin-EBITDA-Operating-Profit-and-PBIT)
   - [Calculating-Ratios](#Calculating-Ratios)
   - [Calculating-Balance-Sheet-Related-Values](#Calculating-Balance-Sheet-Related-Values)
   - [Compiling-all-key-values-in-one-VIEW](#Compiling-all-key-values-in-one-VIEW)
   - [Calculating-Ratios-FinValues-Table](#Calculating-Ratios-FinValues-Table)
   - [Calculating-further-values-for-Ratios-and-updating-VIEW-PLValues1](#Calculating-further-values-for-Ratios-and-updating-VIEW-PLValues1)
   - [Calculating-Receivables-and-Payables-and-updating-VIEW-BSValues](#Calculating-Receivables-and-Payables-and-updating-VIEW-BSValues)
   - [Updating-VIEW-FinValues](#Updating-VIEW-FinValues)
   - [Calculating-FinValues-Ratios-of-Interest-Cover-Inventory-Receivables-Payables-Turnover-Period](#Calculating-FinValues-Ratios-of-Interest-Cover-Inventory-Receivables-Payables-Turnover-Period)
   - [Slicing-Ratios-for-Country](#Slicing-Ratios-for-Country)
   - [Uploading-CF-Table-to-our-Database](#Uploading-CF-Table-to-our-Database)
   - [Calculating-Values-for-Cash-Flow-Statement-Part-1](#Calculating-Values-for-Cash-Flow-Statement-Part-1)
   - [Calculating-Cash-Cash-Equivalents-at-the-end-of-the-Year](#Calculating-Cash-Cash-Equivalents-at-the-end-of-the-Year)
   - [Calculating-Cash-Cash-Equivalents-at-the-start-of-the-year](#Calculating-Cash-Cash-Equivalents-at-the-start-of-the-year)
   - [Compiling-Cash-Flow-Statement](#Compiling-Cash-Flow-Statement)
   


---

## Installation

### Install Docker Desktop on Ubuntu
[Click here](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#Install-Docker-Desktop-on-Ubuntu)  
### Install Microsoft SQL Server - Ubuntu based images Using Docker
[Click here](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#Install-Microsoft-SQL-Server)  

## Database Setup

### Create Database and Import Data from CSV
[Click here](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#Create-Database-and-Import-data-from-csv)  
## SQL Queries

### Getting Started with SQL SELECT
[Click here for code](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#Getting-started-with-SQL-SELECT)  
- **Purpose of Query 1**: Retrieve all records from the General Ledger
  - **Tables Used**: `GL`
  - **Columns Selected**: All (`*`)
  - **Output**: Complete dataset of all transactions
  - **Use Case**: Reviewing all financial transactions stored in the General Ledger

- **Purpose of Query 2**: Retrieve all records from the Chart of Accounts
  - **Tables Used**: `coa`
  - **Columns Selected**: All (`*`)
  - **Output**: Complete dataset of all accounts
  - **Use Case**: Understanding account structures and classifications

- **Purpose of Query 3**: Retrieve all records from the Territory table
  - **Tables Used**: `Territory`
  - **Columns Selected**: All (`*`)
  - **Output**: Complete dataset of all territories
  - **Use Case**: Identifying geographic regions and their associated attributes

- **Purpose of Query 4**: Retrieve all records from the Calendar table
  - **Tables Used**: `calendar`
  - **Columns Selected**: All (`*`)
  - **Output**: Complete dataset of all dates and periods
  - **Use Case**: Understanding date-related dimensions for time-based analysis

### SELECT-specific-Columns-and-Rows
[Click here for code](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#SELECT-specific-Columns-and-Rows)  
- **Purpose of Query 1**: Retrieve only date and amount data from the General Ledger
  - **Tables Used**: `GL`
  - **Columns Selected**: `Date`, `Amount`
  - **Output**: All records showing transaction dates and amounts
  - **Use Case**: Basic financial analysis focusing on transaction amounts over time

- **Purpose of Query 2**: Find high-value transactions for a specific account and territory
  - **Tables Used**: `GL`
  - **Filters Applied**:
    - Account: `10`
    - Territory: `3`
    - Minimum Amount: `100,000`
  - **Output**: Complete records of qualifying transactions
  - **Use Case**: Identifying significant transactions in a specific region/account

### Selecting-WHERE
[Click here for code](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#Selecting-WHERE)  
- **Purpose of Query 1**: Retrieve all transactions that occurred on a specific date
  - **Tables Used**: `GL`
  - **Filters Applied**: `Date = '2018-10-22'`
  - **Output**: Complete records of transactions from October 22, 2018
  - **Use Case**: Examining financial activity on a specific day

- **Purpose of Query 2**: Retrieve all transactions related to salaries
  - **Tables Used**: `GL`
  - **Filters Applied**: `Details = 'Salaries'`
  - **Output**: Complete records of salary-related transactions
  - **Use Case**: Isolating payroll expenses for analysis

- **Purpose of Query 3**: Retrieve all transactions except those for a specific account
  - **Tables Used**: `GL`
  - **Filters Applied**: `Account_key <> 230`
  - **Output**: Complete records excluding transactions for account 230
  - **Use Case**: Viewing all financial activity except a specific account

- **Purpose of Query 4**: Retrieve transactions for accounts within a specific range
  - **Tables Used**: `GL`
  - **Filters Applied**: `Account_key BETWEEN 10 AND 60`
  - **Output**: Complete records of transactions for accounts within the range
  - **Use Case**: Identifying financial activity for a set of accounts

- **Purpose of Query 5**: Retrieve transactions within a specific date range
  - **Tables Used**: `GL`
  - **Filters Applied**: `Date BETWEEN '2018-01-01' AND '2018-01-31'`
  - **Output**: Complete records of transactions from January 2018
  - **Use Case**: Analyzing financial activity within a monthly period

### Time-Intelligence-Date-Month
[Click here for code](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#Time-Intelligence-Date-Month)  
- **Purpose of Query 1**: Retrieve all records from the General Ledger while extracting year, month, and day from the date column
  - **Tables Used**: `GL`
  - **Columns Selected**: All (`*`), plus derived columns:
    - `YEAR(Date) AS 'Year'`
    - `MONTH(Date) AS 'MONTH'`
    - `DAY(Date) AS 'DAY'`
  - **Output**: Complete dataset with additional columns for year, month, and day extracted from the date
  - **Use Case**: Facilitates date-based filtering and analysis by structuring date components separately

- **Purpose of Query 2**: Retrieve all transactions that occurred in September 2019
  - **Tables Used**: `GL`
  - **Filters Applied**:
    - `YEAR([Date]) = 2019`
    - `MONTH([Date]) = 9`
  - **Output**: Complete records of transactions from September 2019
  - **Use Case**: Analyzing financial activities within a specific month of a given year

- **Notes on Using Brackets in SQL**:
  - Brackets (`[]`) are used when a column name contains spaces or special characters.
  - They are also required when column names are reserved keywords.
  - **Examples**:
    - `SELECT [Order Date] FROM Orders` → Column name includes a space.
    - `SELECT [User] FROM Profiles` → "User" is a reserved keyword.
    - `SELECT [Group] FROM Categories` → "Group" is a reserved keyword.

### Time-Intelligence-Part-2-DATEPART
[Click here for code](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#Time-Intelligence-Part-2-DATEPART)  
- **Purpose of Query 1**: Extract detailed date attributes from the `calendar` table
  - **Tables Used**: `calendar`
  - **Columns Selected**:
    - `[Date]` → The original date field
    - `DATEPART(year, [date]) AS 'year'` → Extracts the year
    - `DATEPART(month, [date]) AS 'month'` → Extracts the month
    - `DATEPART(day, [date]) AS 'DayofMonth'` → Extracts the day of the month
    - `DATEPART(DAYOFYEAR, [date]) AS 'DayofYear'` → Extracts the day of the year
    - `DATEPART(quarter, [date]) AS 'quarter'` → Identifies the quarter
    - `DATEPART(week, [date]) AS 'weekNumber'` → Identifies the week number
    - `DATEPART(weekday, [date]) AS 'weekDay'` → Identifies the weekday number
  - **Output**: A structured dataset with individual components of the date broken down
  - **Use Case**: Useful for time-based analysis, ensuring dates are extracted from the `calendar` table to maintain consistency and avoid duplicates

- **Additional Notes on `DATEPART(weekday, [date])`**:
  - SQL Server considers **Sunday as the first day of the week** (mapped to `1`).
  - For example, **January 1, 2018, was a Monday**, so `DATEPART(weekday, [date])` returned `2`, meaning Monday is treated as the second day of the week.

### Time-Intelligence-in-Action-Basic-Example
[Click here for code](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#Time-Intelligence-in-Action-Basic-Example)  
- **Purpose of Query 1**: Retrieve sales transactions occurring in late November and December
  - **Tables Used**: `GL`
  - **Filters Applied**:
    - `Account_key = 210` → Sales Account
    - `DATEPART(week, [date]) > 46` → Transactions in December and last half of November
  - **Output**: Complete records of sales transactions during the holiday season
  - **Use Case**: Analyzing sales trends around key shopping periods

- **Purpose of Query 2**: Retrieve all transactions occurring on Thanksgiving Day
  - **Tables Used**: `GL`, `Calendar`
  - **Filters Applied**:
    - Identifies Thanksgiving as the **fourth Thursday of November** using `ROW_NUMBER()`
    - Filters transactions occurring on the extracted Thanksgiving date
  - **Output**: Complete records of financial transactions on Thanksgiving
  - **Use Case**: Understanding financial activities specific to Thanksgiving

- **Purpose of Query 3**: Retrieve all transactions occurring on Black Friday
  - **Tables Used**: `GL`, `Calendar`
  - **Filters Applied**:
    - Identifies Thanksgiving date using `ROW_NUMBER()`
    - Determines Black Friday as the **day after Thanksgiving** using `DATEADD(DAY,1, ThanksgivingDate)`
  - **Output**: Complete records of financial transactions on Black Friday
  - **Use Case**: Analyzing spending patterns on one of the biggest shopping days of the year

### SUM-and-Group
[Click here for code](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#SUM-and-Group)  
- **Purpose of Query 1**: Summarize total transaction amounts for each territory related to a specific account (Sales Account)
  - **Tables Used**: `GL`
  - **Columns Selected**:
    - `Territory_key`
    - `Account_key`
    - `SUM(Amount) AS 'Amount'` → Aggregates total transaction amounts
  - **Filters Applied**:
    - `Account_key = 210` → Sales Account
  - **Grouping Applied**:
    - `GROUP BY Territory_key, Account_key` → Summarizes transactions by territory and account
  - **Ordering Applied**:
    - `ORDER BY Territory_key, Account_key` → Sorts results by territory and account
  - **Output**: Aggregated transaction amounts grouped by territory for Account `210`
  - **Use Case**: Analyzing total sales performance across different territories

### Making-and-Using-SubQuery
[Click here for code](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#Making-and-Using-SubQuery)  
- **Purpose of Query 1**: Aggregate total transaction amounts by year
  - **Tables Used**: `GL`
  - **Columns Selected**:
    - `Year` → Extracted from `Date`
    - `SUM(Amount) AS TotalAmount` → Aggregates total transaction amounts
  - **Subquery Used**:
    - Extracts the year from the `Date` column before aggregation
  - **Grouping Applied**:
    - `GROUP BY Year` → Aggregates transactions by year
  - **Ordering Applied**:
    - `ORDER BY Year` → Sorts results chronologically
  - **Output**: Aggregated transaction amounts grouped by year
  - **Use Case**: Analyzing yearly financial trends and total transaction values

### PIVOT-data-into-Columns
[Click here for code](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#PIVOT-data-into-Columns)  
- **Purpose of Query 1**: Pivot transaction amounts to display yearly totals in separate columns
  - **Tables Used**: `GL`
  - **Columns Transformed**:
    - Extracts `Year` from `Date`
    - Aggregates `SUM(Amount)` for each year `[2018], [2019], [2020]`
  - **Pivot Applied**:
    - Converts years into column headers using `PIVOT`
  - **Output**: Yearly financial summaries structured in a columnar format
  - **Use Case**: Simplifies comparison of total transaction amounts across multiple years

- **Purpose of Query 2**: Pivot transaction amounts by account to display yearly totals per account
  - **Tables Used**: `GL`
  - **Columns Transformed**:
    - Extracts `Year` from `Date`
    - Groups transactions by `Account_key`
    - Aggregates `SUM(Amount)` for each year `[2018], [2019], [2020]`
  - **Pivot Applied**:
    - Converts years into column headers, displaying yearly totals per account
  - **Output**: Transaction amounts summarized per account across multiple years
  - **Use Case**: Facilitates financial analysis of account-level trends over multiple years

### Create-VIEW
[Click here for code](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#Create-VIEW)  
- **Purpose of Query 1**: Create a view to store a pivoted summary of transaction amounts by account across multiple years
  - **Tables Used**: `GL`
  - **Columns Transformed**:
    - Extracts `Year` from `Date`
    - Aggregates `SUM(Amount)` for each year `[2018], [2019], [2020]`
    - Groups transactions by `Account_key`
  - **Pivot Applied**:
    - Converts years into column headers using `PIVOT`
  - **View Created**:
    - `CREATE VIEW summary` → Stores the pivoted table for future queries
  - **Output**: A structured, reusable summary of yearly transaction amounts per account
  - **Use Case**: Simplifies recurring analysis of financial trends over multiple years

- **Purpose of Query 2**: Retrieve records from the pivoted view where `Account_key = 121`
  - **Tables Used**: `summary` (created view)
  - **Filters Applied**:
    - `Account_key = 121` → Retrieves transactions only for account `121`
  - **Output**: Filtered data showing yearly transaction amounts for account `121`
  - **Use Case**: Isolating financial performance for a specific account across multiple years

### JOIN-Tables
[Click here for code](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#JOIN-Tables)  
- **Purpose of Query 1**: Retrieve all records from `GL` with corresponding account details from `COA`
  - **Tables Used**: `GL`, `COA`
  - **Join Applied**:
    - `INNER JOIN` → Matches records based on `Account_key`
  - **Output**: Complete transaction data with account details
  - **Use Case**: Combining financial transactions with account descriptions for detailed analysis

- **Purpose of Query 2**: Retrieve all records from `GL` with territory details
  - **Tables Used**: `GL`, `Territory`
  - **Join Applied**:
    - `JOIN` → Matches records based on `Territory_key`
  - **Output**: Complete transaction data enriched with territory information
  - **Use Case**: Understanding transactions in relation to geographic territories

- **Purpose of Query 3**: Retrieve specific transaction attributes along with country details
  - **Tables Used**: `GL`, `Territory`
  - **Columns Selected**:
    - `Date`
    - `GL.Territory_key`
    - `Amount`
    - `Country`
  - **Join Applied**:
    - `INNER JOIN` → Matches records based on `Territory_key`
  - **Output**: Transactions with territory details including country
  - **Use Case**: Analyzing transactions by geographic location

- **Purpose of Query 4**: Retrieve transaction details with account reporting categories
  - **Tables Used**: `GL`, `COA`
  - **Columns Selected**:
    - `Date`
    - `Amount`
    - `Report`
    - `SubAccount`
  - **Join Applied**:
    - `INNER JOIN` → Matches records based on `Account_key`
  - **Ordering Applied**:
    - `ORDER BY Report` → Sorts results by reporting category
  - **Output**: Transactions categorized by financial reporting structure
  - **Use Case**: Organizing transactions based on financial reporting groups

### RIGHT-JOIN-LEFT-JOIN-FULL-JOIN
[Click here for code](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#RIGHT-JOIN-LEFT-JOIN-FULL-JOIN)  
- **Purpose of Query 1**: Retrieve transactions along with territory details, including unmatched records from `Territory`
  - **Tables Used**: `GL`, `Territory`
  - **Join Applied**:
    - `RIGHT JOIN` → Returns all records from `Territory` and matching records from `GL`
  - **Output**: Transactions with territory details, including territories without matching transactions
  - **Use Case**: Identifying territories with or without recorded financial activity

- **Purpose of Query 2**: Retrieve transactions along with territory details, including unmatched records from `GL`
  - **Tables Used**: `GL`, `Territory`
  - **Join Applied**:
    - `LEFT JOIN` → Returns all records from `GL` and matching records from `Territory`
  - **Output**: Transactions with territory details, including transactions without matching territory records
  - **Use Case**: Ensuring all financial transactions are accounted for, even if territories are missing

- **Purpose of Query 3**: Retrieve transactions along with territory details, ensuring all records from both tables appear
  - **Tables Used**: `GL`, `Territory`
  - **Join Applied**:
    - `FULL JOIN` → Returns all records from both `GL` and `Territory`
  - **Output**: Complete dataset combining transactions and territories, even when there’s no matching data
  - **Use Case**: Comprehensive financial analysis covering all transactions and territories

- **Notes on Join Types**:
  - **INNER JOIN** → Returns only matching records
  - **RIGHT JOIN** → Includes all records from the right-side table (`Territory`)
  - **LEFT JOIN** → Includes all records from the left-side table (`GL`)
  - **FULL JOIN** → Includes all records from both tables

- **Purpose of Query 4**: Retrieve transactions with territory and account details (joining three tables)
  - **Tables Used**: `GL`, `Territory`, `COA`
  - **Join Applied**:
    - `JOIN Territory` → Matches transactions to territories
    - `JOIN COA` → Matches transactions to accounts
  - **Output**: Enriched dataset containing financial transactions, associated territories, and account details
  - **Use Case**: Analyzing financial transactions in relation to both geographic and account-based attributes

- **Purpose of Query 5**: Retrieve transactions enriched with territory, account, and calendar information (joining four tables)
  - **Tables Used**: `GL`, `Territory`, `COA`, `Calendar`
  - **Join Applied**:
    - `JOIN Territory` → Matches transactions to territories
    - `JOIN COA` → Matches transactions to accounts
    - `JOIN Calendar` → Matches transactions to specific calendar dates
  - **Output**: Complete financial dataset enriched with all relevant attributes for deeper analysis
  - **Use Case**: Generating fully detailed transaction reports that incorporate geographic, account, and time-based insights

### FORMAT-numbers
[Click here for code](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#FORMAT-numbers)  
- **Purpose of Query 1**: Retrieve transaction dates while formatting the amount column for readability
  - **Tables Used**: `GL`
  - **Columns Selected**:
    - `Date` → Displays transaction date
    - `FORMAT(Amount, 'N0') AS Amount` → Formats amount with thousand separators (no decimal places)
  - **Comment Included**:
    - `'N1'` → Can be used for one decimal place formatting
  - **Output**: Transaction dates and amounts with formatted number display
  - **Use Case**: Improving numerical readability for financial reports or data presentation

### Preparing-Profit-Loss-Statement
[Click here for code](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#Preparing-Profit-Loss-Statement)  
- **Purpose of Query 1**: Summarize total profit and loss transactions for January 2020
  - **Tables Used**: `GL`, `COA`
  - **Columns Selected**:
    - `Account_key`
    - `Report`
    - `Class`
    - `Account`
    - `SUM(Amount) AS 'Total Amount'`
  - **Filters Applied**:
    - `Report = 'Profit and Loss'`
    - `Date BETWEEN '2020-01-01' AND '2020-01-31'`
  - **Grouping Applied**:
    - `GROUP BY report, class, account, Account_key`
  - **Ordering Applied**:
    - `ORDER BY Account_key`
  - **Output**: Aggregated total profit and loss values for January 2020
  - **Use Case**: Reviewing financial performance within a specific monthly period

- **Purpose of Query 2**: Pivot profit and loss transactions to show yearly totals across accounts
  - **Tables Used**: `GL`, `COA`
  - **Transformation Applied**:
    - Extracts `Year` from `Date`
    - Aggregates `SUM(Amount)` grouped by `Report`, `Class`, and `Account`
  - **Pivot Applied**:
    - Converts `Year` into column headers `[2018], [2019], [2020]`
  - **Output**: Structured yearly profit and loss totals for each account
  - **Use Case**: Simplifying financial trend analysis across multiple years

- **Purpose of Query 3**: Pivot profit and loss transactions by country to show yearly totals
  - **Tables Used**: `GL`, `COA`, `Territory`
  - **Transformation Applied**:
    - Extracts `Year` from `Date`
    - Aggregates `SUM(Amount)` grouped by `Country`, `Report`, `Class`, and `Account`
  - **Pivot Applied**:
    - Converts `Year` into column headers `[2018], [2019], [2020]`
  - **Output**: Profit and loss summaries for each country across multiple years
  - **Use Case**: Comparing financial performance by geographic region over time

### Preparing-Balance-Sheet-Understanding-the-problem
[Click here for code](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#Preparing-Balance-Sheet-Understanding-the-problem)  
## Financial Reporting Differences: Profit & Loss vs. Balance Sheet

- **Profit and Loss Statement**:
  - Reports **figures for a specific period** (e.g., annual profit/loss)
  - Example:
    - **2018** → $1M profit
    - **2019** → $3M profit
    - **2020** → $2M loss

- **Balance Sheet**:
  - Reports figures **cumulatively**, carrying over previous balances
  - Example:
    - **2018 Balance Sheet** → $1M
    - **2019 Balance Sheet** → Previous $1M + another $1M = $2M
    - **2020 Balance Sheet** → Previous $2M + new financial outcome

### Key Takeaways:
- Profit and loss statements **reset** each year, showing revenue and expenses for that period.
- Balance sheets **accumulate** over time, reflecting total financial position.
### SQL-for-Cumulative-SUM
[Click here for code](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#SQL-for-Cumulative-SUM)  
- **Purpose of Query 1**: Compute cumulative sum of amounts over distinct dates
  - **Tables Used**: `GL`
  - **Columns Selected**:
    - `DISTINCT Date` → Ensures unique dates
    - `SUM(Amount) OVER (ORDER BY Date)` → Computes running total
  - **Ordering Applied**:
    - `ORDER BY Date` → Ensures progressive accumulation
  - **Output**: Running total of transaction amounts for distinct dates
  - **Use Case**: Understanding how financial figures accumulate over time

- **Purpose of Query 2**: Compute total transaction amounts grouped by date
  - **Tables Used**: `GL`
  - **Columns Selected**:
    - `Date`
    - `SUM(Amount)` → Aggregates total per date
  - **Grouping Applied**:
    - `GROUP BY Date` → Ensures aggregation per unique date
  - **Ordering Applied**:
    - `ORDER BY Date` → Sorts results chronologically
  - **Output**: Summarized total transaction amounts per day
  - **Use Case**: Comparing total daily transactions versus cumulative running totals

- **Purpose of Query 3**: Compute cumulative sum partitioned by territory and account over dates
  - **Tables Used**: `GL`
  - **Columns Selected**:
    - `DISTINCT Date`
    - `Territory_key`
    - `Account_key`
    - `SUM(Amount) OVER (PARTITION BY Territory_key, Account_key ORDER BY Date)` → Computes running total for each territory-account pair
  - **Ordering Applied**:
    - `ORDER BY Date` → Ensures chronological accumulation
  - **Output**: Running total of transactions per territory-account grouping
  - **Use Case**: Analyzing cumulative financial flows within specific geographic and account segments

### Cumulative-SUM-Part-2
[Click here for code](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#Cumulative-SUM-Part-2)  
- **Purpose of Query 1**: Compute cumulative sum of amounts partitioned by territory and account over dates
  - **Tables Used**: `GL`
  - **Columns Selected**:
    - `DISTINCT Date`
    - `Territory_key`
    - `Account_key`
    - `SUM(Amount) OVER (PARTITION BY Territory_key, Account_key ORDER BY Date) AS Amount`
  - **Ordering Applied**:
    - `ORDER BY Date` → Ensures chronological accumulation
  - **Output**: Running total of transactions per territory-account grouping
  - **Use Case**: Analyzing cumulative financial flows within specific geographic and account segments

- **Purpose of Query 2**: Run a filtered version of Query 1 for specific `Account_key = 20` and `Territory_key = 1`
  - **Tables Used**: `GL`
  - **Filters Applied**:
    - `Account_key = 20`
    - `Territory_key = 1`
  - **Output**: Running total transactions **only** for `Account_key = 20` and `Territory_key = 1`
  - **Use Case**: Narrowing down cumulative transaction analysis to a specific account and territory

- **Purpose of Query 3**: Retrieve distinct transaction amounts for `Account_key = 20` and `Territory_key = 1` without cumulative calculations
  - **Tables Used**: `GL`
  - **Columns Selected**:
    - `DISTINCT Date`
    - `Territory_key`
    - `Account_key`
    - `Amount` (raw transaction value)
  - **Filters Applied**:
    - `Account_key = 20`
    - `Territory_key = 1`
  - **Output**: Raw transactions without cumulative summation
  - **Use Case**: Comparing individual transactions against the cumulative sum computed earlier

- **Purpose of Query 4**: Compute cumulative sum partitioned by territory and account, grouped by year
  - **Tables Used**: `GL`
  - **Columns Selected**:
    - `Year(Date) AS 'Year'` → Extracts year component
    - `Territory_key`
    - `Account_key`
    - `SUM(Amount) OVER (PARTITION BY Territory_key, Account_key ORDER BY Year(Date)) AS Amount`
  - **Ordering Applied**:
    - `ORDER BY Year(Date)` → Ensures accumulation progresses annually
  - **Output**: Cumulative total transactions per territory-account grouping, calculated separately for each year
  - **Use Case**: Understanding how financial figures build up across different years within geographic and account segments

### Preparing Balance-Sheet
[Click here for code](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#Preparing-Balance-Sheet)  
- **Purpose of Query 1**: Compute cumulative balance sheet values per country and subaccount by year
  - **Tables Used**: `GL`, `Territory`, `COA`
  - **Columns Selected**:
    - `DISTINCT YEAR([Date]) AS 'Year'` → Extracts year component
    - `Country`
    - `Report`
    - `Class`
    - `Subclass`
    - `Subclass2`
    - `Account`
    - `SubAccount`
    - `SUM(Amount) OVER (PARTITION BY Country, SubAccount ORDER BY YEAR([Date])) AS Amount` → Computes cumulative total per partitioned country and subaccount
  - **Joins Applied**:
    - `JOIN Territory ON GL.Territory_key = Territory.Territory_key` → Adds geographic details
    - `JOIN COA ON COA.Account_key = GL.Account_key` → Adds financial account categorization
  - **Filters Applied**:
    - `Report = 'Balance Sheet'` → Ensures the data pertains to balance sheet transactions
  - **Output**: Cumulative balance sheet totals by country and subaccount per year
  - **Use Case**: Analyzing cumulative financial positions year-over-year, ensuring balance sheet values carry forward instead of resetting annually

- **Notes on Partitioning Behavior**:
  - `PARTITION BY Country, Report, Class, Subclass, Subclass2, Account, SubAccount ORDER BY YEAR([Date])`
    - Equivalent to `PARTITION BY Country, SubAccount ORDER BY YEAR([Date])`
    - If partitioning occurs at the **lowest class**, all **higher-level categories automatically inherit the partition**

### Balance-Sheet-Final
[Click here for code](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#Balance-Sheet-Final)  
- **Purpose of Query 1**: Generate a balance sheet report with cumulative totals per subaccount
  - **Tables Used**: `GL`, `Territory`, `COA`
  - **Columns Selected**:
    - `Report`
    - `Class`
    - `Subclass`
    - `Subclass2`
    - `Account`
    - `SubAccount`
    - `[2018]`, `[2019]`, `[2020]` → Pivoted cumulative totals for each year
  - **Joins Applied**:
    - `JOIN Territory ON GL.Territory_key = Territory.Territory_key` → Adds geographic details
    - `JOIN COA ON COA.Account_key = GL.Account_key` → Adds financial account categorization
  - **Partition Applied**:
    - `PARTITION BY SubAccount ORDER BY YEAR(Date)` → Computes cumulative amounts per subaccount
  - **Pivot Applied**:
    - Converts years into columns `[2018], [2019], [2020]`
  - **Ordering Applied**:
    - `ORDER BY Class, Subclass, Subclass2, Account, SubAccount`
  - **Output**: Structured balance sheet displaying cumulative financial values per subaccount
  - **Use Case**: Understanding long-term account balances with year-over-year accumulation

- **Purpose of Query 2**: Generate a balance sheet report with cumulative totals grouped by country
  - **Tables Used**: `GL`, `Territory`, `COA`
  - **Columns Selected**:
    - `Country`
    - `Report`
    - `Class`
    - `Subclass`
    - `Subclass2`
    - `Account`
    - `SubAccount`
    - `[2018]`, `[2019]`, `[2020]` → Pivoted cumulative totals for each year
  - **Partition Applied**:
    - `PARTITION BY Country, SubAccount ORDER BY YEAR(Date)` → Computes cumulative amounts per country-subaccount combination
  - **Pivot Applied**:
    - Converts years into columns `[2018], [2019], [2020]`
  - **Output**: Country-specific balance sheet showcasing cumulative totals over time
  - **Use Case**: Analyzing account balances at a geographic level

- **Purpose of Query 3**: Verify the balance sheet report by filtering specific conditions
  - **Filters Applied**:
    - `SubAccount = 'Cash at Bank'`
    - `Class = 'Assets'`
    - `Subclass = 'Assets'`
    - `Country = 'Australia'`
  - **Output**: Returns only records matching specified financial and geographic criteria
  - **Use Case**: Ensuring accuracy of cumulative balance computations for a specific asset category in Australia

- **Notes on Partition Behavior**:
  - `PARTITION BY SubAccount ORDER BY YEAR(Date)` automatically partitions higher-level categories (`Report`, `Class`, `Subclass`, etc.).
  - Partitioning at the **lowest class** ensures correct accumulation across all financial classifications.

### Learning-the-CASE-WHEN-statement
[Click here for code](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#Learning-the-CASE-WHEN-statement)  
- **Purpose of Query 1**: Create separate columns for yearly totals using a `CASE` statement
  - **Tables Used**: `GL`
  - **Columns Created**:
    - `SUM(CASE WHEN YEAR(Date) = 2018 THEN Amount ELSE 0 END) AS '2018'`
    - `SUM(CASE WHEN YEAR(Date) = 2019 THEN Amount ELSE 0 END) AS '2019'`
    - `SUM(CASE WHEN YEAR(Date) = 2020 THEN Amount ELSE 0 END) AS '2020'`
  - **Output**: Aggregated yearly transaction totals, displayed as separate columns
  - **Use Case**: Simplifying year-over-year comparisons without requiring a pivot transformation

- **Purpose of Query 2**: Create yearly transaction totals while grouping by account and territory
  - **Tables Used**: `GL`
  - **Columns Created**:
    - `Account_key`
    - `Territory_key`
    - `SUM(CASE WHEN YEAR(Date) = 2018 THEN Amount ELSE 0 END) AS '2018'`
    - `SUM(CASE WHEN YEAR(Date) = 2019 THEN Amount ELSE 0 END) AS '2019'`
    - `SUM(CASE WHEN YEAR(Date) = 2020 THEN Amount ELSE 0 END) AS '2020'`
  - **Grouping Applied**:
    - `GROUP BY Account_key, Territory_key` → Aggregates yearly totals for each account-territory combination
  - **Ordering Applied**:
    - `ORDER BY Account_key, Territory_key`
  - **Output**: Yearly financial summaries structured by account and territory
  - **Use Case**: Understanding account-level financial trends across multiple years and territories

### Calculating-Sales
[Click here for code](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#Calculating-Sales)  
- **Purpose of Query 1**: Calculate yearly net sales and display results row-wise
  - **Tables Used**: `GL`, `COA`
  - **Columns Selected**:
    - `YEAR(Date) AS 'Year'` → Extracts year component
    - `SUM(CASE WHEN SubClass = 'sales' THEN Amount ELSE 0 END) AS Net_Sales` → Computes total net sales for each year
  - **Joins Applied**:
    - `JOIN COA ON GL.Account_key = COA.Account_key` → Adds account categorization
  - **Grouping Applied**:
    - `GROUP BY YEAR(Date)` → Aggregates net sales by year
  - **Ordering Applied**:
    - `ORDER BY YEAR(Date)` → Sorts results chronologically
  - **Output**: Total net sales per year presented in rows
  - **Use Case**: Reviewing yearly financial performance of net sales

- **Purpose of Query 2**: Calculate yearly net sales and display results column-wise
  - **Tables Used**: `GL`, `COA`
  - **Columns Created**:
    - `SUM(CASE WHEN SubClass = 'sales' AND YEAR(Date) = 2018 THEN Amount ELSE 0 END) AS '2018'`
    - `SUM(CASE WHEN SubClass = 'sales' AND YEAR(Date) = 2019 THEN Amount ELSE 0 END) AS '2019'`
    - `SUM(CASE WHEN SubClass = 'sales' AND YEAR(Date) = 2020 THEN Amount ELSE 0 END) AS '2020'`
  - **Joins Applied**:
    - `JOIN COA ON GL.Account_key = COA.Account_key` → Adds account categorization
  - **Output**: Total net sales per year presented in separate columns
  - **Use Case**: Simplifying year-over-year comparison of net sales

### Calculating-Gross-Profit-and-Net-Profit
[Click here for code](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#Calculating-Gross-Profit-and-Net-Profit)  
- **Purpose of Query 1**: Calculate yearly net sales, gross profit, and net profit row-wise
  - **Tables Used**: `GL`, `COA`
  - **Columns Selected**:
    - `YEAR(Date) AS 'Year'` → Extracts year component
    - `SUM(CASE WHEN SubClass = 'sales' THEN Amount ELSE 0 END) AS 'Net_Sales'`
    - `SUM(CASE WHEN Class = 'Trading account' THEN Amount ELSE 0 END) AS 'Gross_Profit'`
    - `SUM(CASE WHEN Report = 'Profit and Loss' THEN Amount ELSE 0 END) AS 'Net_Profit'`
  - **Joins Applied**:
    - `JOIN COA ON GL.Account_key = COA.Account_key` → Adds account categorization
  - **Grouping Applied**:
    - `GROUP BY YEAR(Date)` → Aggregates financial metrics by year
  - **Ordering Applied**:
    - `ORDER BY YEAR(Date)` → Sorts results chronologically
  - **Output**: Yearly totals displayed row-wise
  - **Use Case**: Understanding profit progression year-over-year

- **Purpose of Query 2**: Display yearly net sales, gross profit, and net profit column-wise using a pivot table
  - **Tables Used**: `GL`, `COA`
  - **Transformation Applied**:
    - Extracts `Year` from `Date`
    - Uses `SUM(CASE WHEN SubClass = 'sales' THEN Amount ELSE 0 END) AS Net_Sales` for pivoting
    - Pivots columns `[2018], [2019], [2020]` to create separate year-based fields
  - **Pivot Applied**:
    - Converts years into column headers for financial metrics (`Net_Sales`, `Gross_Profit`, `Net_Profit`)
  - **Output**: Yearly financial data structured in columns
  - **Use Case**: Simplifies multi-year comparison of sales and profitability

- **Purpose of Query 3**: Display yearly financial metrics column-wise using a `CASE` statement
  - **Tables Used**: `GL`, `COA`
  - **Transformation Applied**:
    - Combines multiple yearly queries using `UNION ALL`
    - Uses `SUM(CASE WHEN Year = 2018 THEN Value ELSE 0 END) AS [2018]`, etc.
  - **Output**: Yearly financial metrics (`Net_Sales`, `Gross_Profit`, `Net_Profit`) structured in separate columns
  - **Use Case**: Alternative to pivot tables for handling multi-year comparisons

### Calculating-EBITDA-Operating-Profit-and-PBIT
[Click here for code](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#Calculating-EBITDA-Operating-Profit-and-PBIT)  
**EBITDA Calculation and Financial Metrics Query**
**Steps to Calculate EBITDA:**
1. Start with **Net Sales** = `Sales - Sales Return`.
2. Subtract **Cost of Sales** (COGS) → This results in **Gross Profit**.
3. Subtract all **Operating Expenses** (Sales & Distribution, Marketing, Administration).
4. Add back all **Depreciation and Amortization** (non-cash expenses).

---

**Purpose of Query**: Calculate yearly financial metrics including EBITDA, Gross Profit, Operating Profit, and Net Profit
- **Tables Used**: `GL`, `COA`
- **Joins Applied**:
  - `JOIN COA ON GL.Account_key = COA.Account_key` → Incorporates account classifications
- **Columns Calculated**:
  - `YEAR(Date) AS 'Year'` → Extracts year component
  - `SUM(CASE WHEN SubClass = 'sales' THEN Amount ELSE 0 END) AS 'Net_Sales'` → Total net sales
  - `SUM(CASE WHEN Class = 'Trading account' THEN Amount ELSE 0 END) AS 'Gross_Profit'` → Gross profit
  - `SUM(CASE WHEN SubClass IN ('Sales', 'Cost of Sales', 'Operating Expenses') THEN Amount ELSE 0 END) AS 'EBITDA'` → Earnings Before Interest, Taxes, Depreciation, and Amortization
  - `SUM(CASE WHEN Class IN ('Operating account', 'Trading account') THEN Amount ELSE 0 END) AS 'Operating_profit'` → Operating profit
  - `SUM(CASE WHEN Class IN ('Operating account', 'Trading account', 'Non-operating') THEN Amount ELSE 0 END) AS 'PBIT'` → Profit Before Interest and Taxes
  - `SUM(CASE WHEN Report = 'Profit and Loss' THEN Amount ELSE 0 END) AS 'Net_Profit'` → Net profit
- **Grouping Applied**:
  - `GROUP BY YEAR(Date)` → Aggregates financial figures annually
- **Ordering Applied**:
  - `ORDER BY YEAR(Date)` → Sorts results chronologically
- **Output**: Comprehensive yearly financial summary including key profitability metrics
- **Use Case**: Provides a structured financial analysis by breaking down profit generation and operational performance over time

### Creating-view-for-Gross-Profit-Margin-EBITDA-Operating-Profit-and-PBIT
[Click here for code](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#Creating-view-for-Gross-Profit-Margin-EBITDA-Operating-Profit-and-PBIT)  
**Creating Financial Views for Profit & Loss Analysis**

**Purpose of Query 1**: Create a view (`PLValues`) for financial metrics based on yearly data
- **Tables Used**: `GL`, `COA`
- **Joins Applied**:
  - `JOIN COA ON GL.Account_key = COA.Account_key` → Adds account categorization
- **Columns Created**:
  - `YEAR(Date) AS 'Year'`
  - `SUM(CASE WHEN SubClass = 'sales' THEN Amount ELSE 0 END) AS 'Net_Sales'` → Total net sales
  - `SUM(CASE WHEN Class = 'Trading account' THEN Amount ELSE 0 END) AS 'Gross_Profit'` → Gross profit
  - `SUM(CASE WHEN SubClass IN ('Sales', 'Cost of Sales', 'Operating Expenses') THEN Amount ELSE 0 END) AS 'EBITDA'` → Earnings Before Interest, Taxes, Depreciation, and Amortization
  - `SUM(CASE WHEN Class IN ('Operating account', 'Trading account') THEN Amount ELSE 0 END) AS 'Operating_profit'` → Operating profit
  - `SUM(CASE WHEN Class IN ('Operating account', 'Trading account', 'Non-operating') THEN Amount ELSE 0 END) AS 'PBIT'` → Profit Before Interest and Taxes
  - `SUM(CASE WHEN Report = 'Profit and Loss' THEN Amount ELSE 0 END) AS 'Net_Profit'` → Net profit
- **Grouping Applied**:
  - `GROUP BY YEAR(Date)` → Aggregates financial figures annually
- **Output**: Creates a stored view `PLValues` for future queries
- **Use Case**: Simplifies recurring financial analysis and comparisons

**Purpose of Query 2**: Calculate Gross Profit Margin (`GP_Margin`)
- **Table Used**: `PLValues` (previously created view)
- **Formula Applied**:
  - `Gross_Profit / Net_Sales * 100 AS GP_Margin`
- **Output**: Returns a percentage-based Gross Profit Margin
- **Use Case**: Helps evaluate profitability relative to sales

**Purpose of Query 3**: Create a view (`PLValues1`) for financial metrics segmented by country
- **Tables Used**: `GL`, `COA`, `Territory`
- **Joins Applied**:
  - `JOIN COA ON GL.Account_key = COA.Account_key` → Adds account categorization
  - `JOIN Territory ON GL.Territory_key = Territory.Territory_key` → Adds geographic details
- **Columns Created**:
  - **Same metrics as `PLValues`** plus `Country`
- **Grouping Applied**:
  - `GROUP BY YEAR(Date), Country` → Aggregates financial figures annually per country
- **Output**: Creates a stored view `PLValues1` for future queries
- **Use Case**: Enables country-level profitability analysis

**Purpose of Query 4**: Retrieve all records from `PLValues1`
- **Table Used**: `PLValues1`
- **Output**: Full dataset showing yearly profit & loss metrics segmented by country
- **Use Case**: Provides a complete financial breakdown across different regions

 **Purpose of Query 5**: Compute total net sales per year from `PLValues1`
- **Table Used**: `PLValues1`
- **Aggregation Applied**:
  - `SUM(Net_Sales) GROUP BY Year`
- **Output**: Displays total yearly net sales across all countries
- **Use Case**: Tracks total revenue trends across multiple years

### Calculating-Ratios
[Click here for code](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#Calculating-Ratios)  
**Profit Margin Analysis**

**Purpose of Query 1**: Calculate profit margins by year
- **Table Used**: `PLValues1`
- **Metrics Calculated**:
  - **Gross Profit Margin** → `SUM(Gross_Profit) / SUM(Net_Sales) * 100`
  - **Operating Profit Margin** → `SUM(Operating_Profit) / SUM(Net_Sales) * 100`
  - **Net Profit Margin** → `SUM(Net_Profit) / SUM(Net_Sales) * 100`
- **Grouping Applied**:
  - `GROUP BY Year` → Aggregates financial figures annually
- **Output**: Yearly profit margins expressed as percentages
- **Use Case**: Assessing overall profitability across multiple years

**Purpose of Query 2**: Compute gross profit margin by year for a selected country
- **Table Used**: `PLValues1`
- **Filters Applied**:
  - `WHERE Country = 'France'` → Limits results to France
- **Metrics Calculated**:
  - **Gross Profit Margin** → `SUM(Gross_Profit) / SUM(Net_Sales) * 100`
- **Grouping Applied**:
  - `GROUP BY Year` → Aggregates financial figures annually
- **Ordering Applied**:
  - `ORDER BY 1` → Sorts results by year
- **Output**: Yearly gross profit margins for France
- **Use Case**: Evaluating profitability trends within a specific geographic region

### Calculating-Balance-Sheet-Related-Values
[Click here for code](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#Calculating-Balance-Sheet-Related-Values)  
**Balance Sheet Analysis Queries**

**Purpose of Query 1**: Compute balance sheet values by year
- **Tables Used**: `GL`, `COA`
- **Joins Applied**:
  - `JOIN COA ON GL.Account_key = COA.Account_key` → Incorporates financial account classification
- **Columns Calculated**:
  - `YEAR(Date) AS 'Year'` → Extracts year component
  - `SUM(CASE WHEN Class = 'Assets' THEN Amount ELSE 0 END) OVER(ORDER BY YEAR(Date)) AS 'Assets'`
  - `SUM(CASE WHEN SubClass2 = 'Current Assets' THEN Amount ELSE 0 END) OVER(ORDER BY YEAR(Date)) AS 'Current_Assets'`
  - `SUM(CASE WHEN SubClass2 = 'Non-Current Assets' THEN Amount ELSE 0 END) OVER(ORDER BY YEAR(Date)) AS 'Non-Current_Assets'`
  - `SUM(CASE WHEN SubClass = 'Liabilities' THEN Amount ELSE 0 END) OVER(ORDER BY YEAR(Date)) AS 'Liabilities'`
  - `SUM(CASE WHEN SubClass2 = 'Current Liabilities' THEN Amount ELSE 0 END) OVER(ORDER BY YEAR(Date)) AS 'Current_Liabilities'`
  - `SUM(CASE WHEN SubClass2 = 'Long Term Liabilities' THEN Amount ELSE 0 END) OVER(ORDER BY YEAR(Date)) AS 'NonCurrent_Liabilities'`
  - `SUM(CASE WHEN SubClass = 'Owners Equity' THEN Amount ELSE 0 END) OVER(ORDER BY YEAR(Date)) AS 'Equity'`
  - `SUM(CASE WHEN Class = 'Liabilities and Owners Equity' THEN Amount ELSE 0 END) OVER(ORDER BY YEAR(Date)) AS 'Liabilities_and_Equity'`
  - `SUM(CASE WHEN Account = 'Inventory' THEN Amount ELSE 0 END) OVER(ORDER BY YEAR(Date)) AS 'Inventory'`
- **Ordering Applied**:
  - `ORDER BY YEAR(Date)`
- **Output**: Cumulative balance sheet totals displayed by year
- **Use Case**: Understanding long-term financial structure trends across multiple years

 **Purpose of Query 2**: Compute balance sheet values segmented by country and year
- **Tables Used**: `GL`, `COA`, `Territory`
- **Joins Applied**:
  - `JOIN COA ON GL.Account_key = COA.Account_key` → Adds financial classification
  - `JOIN Territory ON GL.Territory_key = Territory.Territory_key` → Adds geographic categorization
- **Partitioning Applied**:
  - `PARTITION BY Country ORDER BY YEAR(Date)` → Computes cumulative totals per country
- **Output**: Country-specific balance sheet values displayed by year
- **Use Case**: Analyzing geographic variations in financial statements across multiple years

### Compiling-all-key-values-in-one-VIEW
[Click here for code](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#Compiling-all-key-values-in-one-VIEW)  
**Creating Balance Sheet and Financial Views**

**Purpose of View 1 (`BSValues`)**: Store balance sheet metrics by country and year
- **Tables Used**: `GL`, `COA`, `Territory`
- **Joins Applied**:
  - `JOIN COA ON GL.Account_key = COA.Account_key` → Adds financial account classification
  - `JOIN Territory ON GL.Territory_key = Territory.Territory_key` → Incorporates geographic details
- **Partitioning Applied**:
  - `PARTITION BY Country ORDER BY YEAR(Date)` → Computes cumulative totals per country
- **Columns Created**:
  - Balance sheet components (`Assets`, `Liabilities`, `Equity`, `Inventory`, etc.)
  - Breakdown of financial categories (`Current_Assets`, `Non-Current_Assets`, `Current_Liabilities`, `NonCurrent_Liabilities`)
- **Output**:
  - Creates a stored view (`BSValues`) for use in financial analysis
- **Use Case**: Provides cumulative balance sheet data structured by year and country
 
 **Purpose of View 2 (`FinValues`)**: Store both balance sheet and profit & loss metrics by country and year
- **Tables Used**: `BSValues`, `PLValues1`
- **Joins Applied**:
  - `JOIN BSValues AS bs ON bs.Country = pl.Country AND bs.Year = pl.Year` → Merges balance sheet and profit & loss data
- **Columns Selected**:
  - `BSValues` → All balance sheet values
  - `PLValues1` → `Net_Sales`, `Gross_Profit`, `EBITDA`, `Operating_Profit`, `PBIT`, `Net_Profit`
- **Output**:
  - Creates a combined financial dataset (`FinValues`) for further analysis
- **Use Case**:
  - Allows financial comparison between balance sheet and profitability metrics in a unified structure

### Calculating-Ratios-FinValues-Table
[Click here for code](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#Calculating-Ratios-FinValues-Table)  
**Financial Ratio Analysis**

**Purpose of Query**: Compute key financial ratios by year
- **Table Used**: `FinValues`
- **Metrics Calculated**:
  - **Gross Profit Margin** → `SUM(Gross_Profit) / SUM(Net_Sales) * 100`
  - **Operating Profit Margin** → `SUM(Operating_Profit) / SUM(Net_Sales) * 100`
  - **Net Profit Margin** → `SUM(Net_Profit) / SUM(Net_Sales) * 100`
  - **Asset Turnover** → `SUM(Net_Sales) / SUM(Assets) * 100`
  - **Return on Capital Employed (ROCE)** → `SUM(PBIT) / SUM(Equity + NonCurrent_Liabilities) * 100`
  - **Return on Equity (ROE)** → `SUM(Net_Profit) / SUM(Equity) * 100`
  - **Gearing Ratio** → `SUM(Liabilities) / SUM(Equity) * 100`
  - **Current Ratio** → `SUM(Current_Assets) / SUM(Current_Liabilities)`
  - **Quick Ratio** → `(SUM(Current_Assets) - SUM(Inventory)) / SUM(Current_Liabilities)`
- **Grouping Applied**:
  - `GROUP BY Year` → Aggregates financial ratios annually
- **Ordering Applied**:
  - `ORDER BY Year` → Sorts results chronologically
- **Output**: Financial ratios displayed by year
- **Use Case**:
  - Evaluating profitability, efficiency, liquidity, and leverage across multiple years
  - Assessing financial health through key performance indicators

### Calculating-further-values-for-Ratios-and-updating-VIEW-PLValues1
[Click here for code](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#Calculating-further-values-for-Ratios-and-updating-VIEW-PLValues1)  
**Updating Profit & Loss View (`PLValues1`)**

**Purpose of View (`PLValues1`)**: Store profit and loss metrics segmented by country and year
- **Tables Used**: `GL`, `COA`, `Territory`
- **Joins Applied**:
  - `JOIN COA ON GL.Account_key = COA.Account_key` → Adds financial account classification
  - `JOIN Territory ON GL.Territory_key = Territory.Territory_key` → Incorporates geographic details
- **Columns Created**:
  - `YEAR(Date) AS 'Year'` → Extracts year component
  - `Country` → Adds geographic segmentation
  - **Profitability and Expense Metrics**:
    - `Net_Sales`
    - `Gross_Profit`
    - `EBITDA` → Earnings Before Interest, Taxes, Depreciation, and Amortization
    - `Operating_Profit`
    - `PBIT` → Profit Before Interest and Taxes
    - `Net_Profit`
    - `Cost_of_Sales`
    - `Interest_Expense`
- **Grouping Applied**:
  - `GROUP BY YEAR(Date), Country` → Aggregates financial data annually per country
- **Output**:
  - Creates an updated stored view (`PLValues1`) for use in financial reporting
- **Use Case**:
  - Enables structured multi-year profitability analysis, including interest expenses

 **Verification Query**: Retrieve all records from `PLValues1`
- **Table Used**: `PLValues1`
- **Output**:
  - Displays all financial records stored in the updated view
- **Use Case**:
  - Ensuring data integrity and validating financial calculations

### Calculating-Receivables-and-Payables-and-updating-VIEW-BSValues
[Click here for code](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#Calculating-Receivables-and-Payables-and-updating-VIEW-BSValues)  
 **Updating Balance Sheet View (`BSValues`)**

**Purpose of View (`BSValues`)**: Store balance sheet metrics segmented by country and year
- **Tables Used**: `GL`, `COA`, `Territory`
- **Joins Applied**:
  - `JOIN COA ON GL.Account_key = COA.Account_key` → Adds financial account classification
  - `JOIN Territory ON GL.Territory_key = Territory.Territory_key` → Incorporates geographic details
- **Partitioning Applied**:
  - `PARTITION BY Country ORDER BY YEAR(Date)` → Computes cumulative totals per country
- **Columns Created**:
  - `YEAR(Date) AS 'Year'` → Extracts year component
  - `Country` → Adds geographic segmentation
  - **Balance Sheet Components**:
    - `Assets`
    - `Current_Assets`
    - `Non-Current_Assets`
    - `Liabilities`
    - `Current_Liabilities`
    - `NonCurrent_Liabilities`
    - `Equity`
    - `Liabilities_and_Equity`
    - `Inventory`
    - `Trade_Receivables`
    - `Trade_Payables`
- **Output**:
  - Creates an updated stored view (`BSValues`) for use in financial analysis
- **Use Case**:
  - Allows structured multi-year financial analysis, including trade receivables and payables
  
**Verification Query**: Retrieve all records from `BSValues`
- **Table Used**: `BSValues`
- **Output**:
  - Displays all financial records stored in the updated view
- **Use Case**:
  - Ensuring data integrity and validating balance sheet calculations

### Updating-VIEW-FinValues
[Click here for code](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#Updating-VIEW-FinValues)  
 **Updating Financial View (`FinValues`)**

 **Purpose of View (`FinValues`)**: Store combined balance sheet and profit & loss metrics by country and year
- **Tables Used**: `BSValues`, `PLValues1`
- **Joins Applied**:
  - `JOIN BSValues AS bs ON bs.Country = pl.Country AND bs.Year = pl.Year` → Combines balance sheet and profitability data
- **Columns Included**:
  - All balance sheet values from `BSValues`
  - Key financial metrics from `PLValues1`:
    - `Net_Sales`
    - `Gross_Profit`
    - `EBITDA`
    - `Operating_Profit`
    - `PBIT` → Profit Before Interest and Taxes
    - `Net_Profit`
    - `Cost_of_Sales`
    - `Interest_Expense`
- **Output**:
  - Creates a stored view (`FinValues`) for consolidated financial analysis
- **Use Case**:
  - Allows structured multi-year financial comparison, integrating balance sheet values and profitability indicators
 **Verification Query**: Retrieve all records from `FinValues`
- **Table Used**: `FinValues`
- **Output**:
  - Displays combined financial data across countries and years
- **Use Case**:
  - Ensures completeness and accuracy of integrated financial reports

### Calculating-FinValues-Ratios-of-Interest-Cover-Inventory-Receivables-Payables-Turnover-Period
[Click here for code](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#Calculating-FinValues-Ratios-of-Interest-Cover-Inventory-Receivables-Payables-Turnover-Period)  
 **Financial Ratio Analysis with Efficiency Metrics**

 **Purpose of Query**: Compute key financial ratios by year, including efficiency metrics
- **Table Used**: `FinValues`
- **Metrics Calculated**:
  - **Profitability Ratios**:
    - **Gross Profit Margin** → `SUM(Gross_Profit) / SUM(Net_Sales) * 100`
    - **Operating Profit Margin** → `SUM(Operating_Profit) / SUM(Net_Sales) * 100`
    - **Net Profit Margin** → `SUM(Net_Profit) / SUM(Net_Sales) * 100`
  - **Efficiency & Performance Ratios**:
    - **Asset Turnover** → `SUM(Net_Sales) / SUM(Assets) * 100`
    - **Return on Capital Employed (ROCE)** → `SUM(PBIT) / SUM(Equity + NonCurrent_Liabilities) * 100`
    - **Return on Equity (ROE)** → `SUM(Net_Profit) / SUM(Equity) * 100`
  - **Leverage & Liquidity Ratios**:
    - **Gearing Ratio** → `SUM(Liabilities) / SUM(Equity) * 100`
    - **Current Ratio** → `SUM(Current_Assets) / SUM(Current_Liabilities)`
    - **Quick Ratio** → `(SUM(Current_Assets) - SUM(Inventory)) / SUM(Current_Liabilities)`
  - **Financial Stability Metrics**:
    - **Interest Cover Ratio** → `SUM(PBIT) / SUM(Interest_Expense) * -1`
    - **Inventory Turnover Period** → `SUM(Inventory) / SUM(Cost_of_Sales) * 365 * -1`
    - **Receivables Turnover Period** → `SUM(Trade_Receivables) / SUM(Net_Sales) * 365`
    - **Payables Turnover Period** → `SUM(Trade_Payables) / SUM(Cost_of_Sales) * 365 * -1`
- **Grouping Applied**:
  - `GROUP BY Year` → Aggregates financial ratios annually
- **Ordering Applied**:
  - `ORDER BY Year` → Sorts results chronologically
- **Output**: Financial ratios displayed by year
- **Use Case**:
  - Evaluating profitability, efficiency, liquidity, leverage, and financial stability over multiple years
  - Assessing cash flow management through working capital turnover ratios

### Slicing-Ratios-for-Country
[Click here for code](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#Slicing-Ratios-for-Country)  
 **Financial Ratio Analysis for USA**

 **Purpose of Query**: Compute key financial ratios for the USA by year
- **Table Used**: `FinValues`
- **Filters Applied**:
  - `WHERE Country = 'USA'` → Limits results to financial data specific to the USA
- **Metrics Calculated**:
  - **Profitability Ratios**:
    - **Gross Profit Margin** → `SUM(Gross_Profit) / SUM(Net_Sales) * 100`
    - **Operating Profit Margin** → `SUM(Operating_Profit) / SUM(Net_Sales) * 100`
    - **Net Profit Margin** → `SUM(Net_Profit) / SUM(Net_Sales) * 100`
  - **Efficiency & Performance Ratios**:
    - **Asset Turnover** → `SUM(Net_Sales) / SUM(Assets) * 100`
    - **Return on Capital Employed (ROCE)** → `SUM(PBIT) / SUM(Equity + NonCurrent_Liabilities) * 100`
    - **Return on Equity (ROE)** → `SUM(Net_Profit) / SUM(Equity) * 100`
  - **Leverage & Liquidity Ratios**:
    - **Gearing Ratio** → `SUM(Liabilities) / SUM(Equity) * 100`
    - **Current Ratio** → `SUM(Current_Assets) / SUM(Current_Liabilities)`
    - **Quick Ratio** → `(SUM(Current_Assets) - SUM(Inventory)) / SUM(Current_Liabilities)`
  - **Financial Stability Metrics**:
    - **Interest Cover Ratio** → `SUM(PBIT) / SUM(Interest_Expense) * -1`
    - **Inventory Turnover Period** → `SUM(Inventory) / SUM(Cost_of_Sales) * 365 * -1`
    - **Receivables Turnover Period** → `SUM(Trade_Receivables) / SUM(Net_Sales) * 365`
    - **Payables Turnover Period** → `SUM(Trade_Payables) / SUM(Cost_of_Sales) * 365 * -1`
- **Grouping Applied**:
  - `GROUP BY Year` → Aggregates financial ratios annually
- **Ordering Applied**:
  - `ORDER BY Year` → Sorts results chronologically
- **Output**: Financial ratios displayed by year for the USA
- **Use Case**:
  - Evaluating profitability, efficiency, liquidity, leverage, and financial stability over multiple years for the USA
  - Assessing financial health through key performance indicators specific to this geographic region

### Uploading-CF-Table-to-our-Database
[Click here for code](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#Uploading-CF-Table-to-our-Database)  
 **Steps to Import a CSV File into SQL Server Using the Import Wizard**

 **Step 1: Open the Import Wizard**
- Press **Ctrl** + **I** to start the Import Wizard.

 **Step 2: Specify the Input File**
- **Server:** `127.0.0.1,1433`
- **Database:** `FinDB`
- **File Location:** Browse and select the CSV file.
- **New Table Name:** `CF`
- **Table Schema:** `dbo`

 **Step 3: Proceed to Next Steps**
- Click **Next** to continue.

 **Step 4: Modify Columns (if needed)**
- **Table CF:** No need to modify the columns.

 **Step 5: Execute the Import**
- Click **Import Data** to finalize the process.

 **Notes**
- Ensure the CSV file format matches the column structure expected in the `CF` table.
- If column modifications are required, adjust them before confirming the import.
- After importing, verify the data using:
  ```sql
  SELECT * FROM CF;
  ```

### Calculating-Values-for-Cash-Flow-Statement-Part-1
[Click here for code](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#Calculating-Values-for-Cash-Flow-Statement-Part-1)  
 **Financial Data Transformation Using PIVOT**

 **Purpose of Query**: Transform financial data into a structured pivot table format for analysis
- **Tables Used**: `GL`, `CF`
- **Joins Applied**:
  - `JOIN CF ON GL.Account_key = CF.Account_key` → Merges financial transaction data with classification details
- **Filters Applied**:
  - `WHERE ValueType NOT IN ('Opening_balance', 'Closing_balance')` → Excludes opening and closing balances
- **Case Statement Logic**:
  - Applies conditional transformations to `Amount` based on `ValueType`:
    - `All_FTP` → Keeps original `Amount`
    - `All_FTP_CS` → Negates `Amount`
    - `All_FTP_Negative` → Includes negative values only
    - `All_FTP_Positive` → Includes positive values only
    - `All_FTP_Negative_CS` → Negates negative values
    - `All_FTP_Positive_CS` → Negates positive values
- **Grouping Applied**:
  - `GROUP BY Rank, Type, Subtype, YEAR(Date)` → Aggregates financial totals by category and year
- **Pivot Applied**:
  - Converts years into columns `[2018], [2019], [2020]`
- **Output**:
  - Structured pivot table displaying financial values by `Rank`, `Type`, and `SubType`
- **Use Case**:
  - Simplifies comparative analysis of financial values across multiple years
### Calculating-Cash-Cash-Equivalents-at-the-end-of-the-Year
[Click here for code](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#Calculating-Cash-Cash-Equivalents-at-the-end-of-the-Year)  
 **Cash Flow Analysis Using PIVOT**

 **Purpose of Query**: Retrieve cumulative cash flow values categorized by year
- **Tables Used**: `GL`, `CF`
- **Joins Applied**:
  - `JOIN CF ON GL.Account_key = CF.Account_key` → Merges financial transaction data with cash flow classifications
- **Filters Applied**:
  - `WHERE Type = 'Cash and Cash equivalents at the end of the year'` → Selects final cash balance values
- **Partitioning Applied**:
  - `SUM(Amount) OVER (PARTITION BY Rank, Type, SubType ORDER BY YEAR(Date)) AS Amount` → Computes cumulative total cash flow within categories
- **Pivot Applied**:
  - Converts years into columns `[2018], [2019], [2020]`
- **Output**:
  - Structured pivot table displaying cumulative cash flow values categorized by `Rank`, `Type`, and `SubType`
- **Use Case**:
  - Provides a clear breakdown of yearly cash movements, tracking liquidity trends over multiple years
### Calculating-Cash-Cash-Equivalents-at-the-start-of-the-year
[Click here for code](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#Calculating-Cash-Cash-Equivalents-at-the-start-of-the-year)  
 **Carrying Forward Ending Capital as Next Year's Working Capital**

 **Purpose of Query**: Compute the starting cash balance for each year based on the previous year's ending balance
- **Tables Used**: `GL`, `CF`
- **Joins Applied**:
  - `JOIN CF ON GL.Account_key = CF.Account_key` → Merges financial transaction data with classification details
- **Subquery Logic**:
  - Selects financial values where `Type = 'Cash and Cash equivalents at the end of the year'`
  - Computes cumulative cash flow values using `SUM(Amount) OVER (PARTITION BY Rank, Type, SubType ORDER BY YEAR(Date))`
- **LAG Function Applied**:
  - `LAG(Amount, 1, 0) OVER (ORDER BY YEAR(Date) ASC) AS Amount` → Retrieves prior year's ending cash balance to establish next year's starting cash balance
- **Pivot Applied**:
  - Converts years into columns `[2018], [2019], [2020]`
- **Output**:
  - Displays cash flow carried forward from the previous year in a structured pivot format
- **Use Case**:
  - Ensures financial continuity by recognizing that **"First year's ending capital becomes next year's working capital."**

### Compiling-Cash-Flow-Statement
[Click here for code](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#Compiling-Cash-Flow-Statement)  
 **Cash Flow and Financial Data Analysis Using PIVOT and UNION**

 **Purpose of Query**: Consolidate financial metrics into a pivoted format for multi-year comparisons
- **Tables Used**: `GL`, `CF`
- **Joins Applied**:
  - `JOIN CF ON GL.Account_key = CF.Account_key` → Merges financial transaction data with classification details

 **Breakdown of Query Components**:

 **Query 1: Starting Cash Balance for Each Year**
- Uses **LAG function** to retrieve previous year's ending balance as the new year's starting capital.
- Subquery extracts **cumulative cash flow values** from `Type = 'Cash and Cash equivalents at the end of the year'`.
- **Pivot Applied**:
  - Converts yearly values into columns `[2018], [2019], [2020]`.

 **Query 2: Transaction-Based Financial Data**
- Uses `CASE` statements to classify and transform financial transactions:
  - **All_FTP**, **Negative/Positive CS Adjustments**, **Exclude Opening/Closing Balance**.
- Aggregates data with `SUM(Amount)`.
- **Pivot Applied**:
  - Converts yearly values into columns `[2018], [2019], [2020]`.

 **Query 3: Ending Cash Balance for Each Year**
- Extracts **cumulative cash flow values** for `Type = 'Cash and Cash equivalents at the end of the year'`.
- **Partition Applied**:
  - `SUM(Amount) OVER (PARTITION BY Rank, Type, SubType ORDER BY YEAR(Date))` → Computes running totals.
- **Pivot Applied**:
  - Converts yearly values into columns `[2018], [2019], [2020]`.

 **Final Combination Using UNION ALL**
- Merges results of all three queries into a single structured financial dataset.
- Ensures continuity between **starting balances, transactional data, and ending balances**.

 **Use Case**:
- Enables clear year-over-year financial comparisons.
- Tracks financial movements efficiently for structured decision-making.

## Acknowledgment

This project incorporates ideas and techniques I learned from [SQL for Financial Data Analysis & Reporting - Zero to Pro] by [Irfan Sharif](https://www.udemy.com/user/irfansharif/)  . 
**Note**: The course is no longer offered on Udemy. This repository contains my independent implementations.
## License

This project is licensed under the MIT License. See the [resource link](./SQL%20for%20Financial%20Data%20Analysis%20\&%20Reporting.md#LICENSE) for more details.



