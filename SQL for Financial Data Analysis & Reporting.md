---
title: SQL for Financial Data Analysis & Reporting
tags:
  - SQL
  - database
  - tutorial
  - "#sqlserver"
  - "#AzureDataStudio"
  - "#Docker"
created: 2025-04-12
updated: 2025-05-15
author: Tonmoy Rashid
status: in-progress
resource: https://drive.google.com/file/d/1ieb6T_-3gyJ7F9i6OeyfG7jnWed6KnHb/view?usp=sharing
---

# Install Docker Desktop on Ubuntu
<a id="Install-Docker-Desktop-on-Ubuntu"></a>
```bash
1. sudo apt-get update && sudo apt-get upgrade 
    
2. sudo apt-get install apt-transport-https ca-certificates curl software-properties-common 
    
3. curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg 
    
4. echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null 
    
5. sudo apt-get update 
    
6. sudo apt-get install docker-ce docker-ce-cli containerd.io 
    

- Verify Installation: Check if Docker is installed correctly: 
    
    - sudo docker --version 
        

- Start Docker: Enable and start the Docker service: 
    
    - sudo systemctl enable docker 
        
    - sudo systemctl start docker 
        
- Run a Test Container: Test Docker by running a sample container: 
    
    - sudo docker run hello-world

# General Docker Commands 

docker --version                  # Check Docker version 

docker info                       # Display system info 

# Managing Containers 

docker ps                         # List running containers 

docker ps -a                      # List all containers (including stopped ones) 

docker run <image-name>           # Run a container 

sudo docker run --name my-nginx -d -p 8080:80 nginx 

docker stop <container-id>        # Stop a container 

docker rm <container-id>          # Remove a container 

# Managing Images 

docker images                     # List available images 

docker pull <image-name>          # Pull an image from Docker Hub 

docker rmi <image-id>             # Remove an image 

# Working with Volumes 

docker volume ls                  # List all volumes 

docker volume create <volume-name> # Create a volume 

docker volume rm <volume-name>    # Remove a volume 


# Avoid using sudo for Docker commands by adding your user to the Docker group. Follow these steps: 

- # Create the Docker Group (if it doesn't exist) 
    
- sudo groupadd docker 
    
- # Add Your User to the Docker Group 
    
- sudo usermod -aG docker $USER 
    
    - # Restart Your System to Apply Changes: 
        
        - sudo reboot 
            
    - # Verify Access (Run Docker Without sudo): 
        
        - docker ps 
            
    - # Check Group Membership (if verification fails): 
        
        - groups $USER
```
# Install Microsoft SQL Server - Ubuntu based images Using Docker
<a id="Install-Microsoft-SQL-Server"></a>
```bash
❯ 
docker run --name SQLserver -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=G11" -p 1433:1433 -d mcr.microsoft.com/mssql/server:2022-latest 

 

2. Open Azure Data Studio 

# Download Azure Data Studio .deb package from website and Install azure data studio .deb like -> 
sudo dpkg -i azuredatastudio-linux-1.51.1.deb 

# Launch Azure Data Studio on your system. 

3. Set Up a New Connection 

   # Click on the Connections button or the "New Connection" option in the Welcome page. 

    # Fill in the connection form: 

   # Server Type: Select Microsoft SQL Server. 

   # Server Name: Enter localhost,1433 (or 127.0.0.1,1433 if using the IP). 

   # Authentication Type: Choose SQL Login. 

   # Username: Enter the SQL Server login (e.g., sa). 

   # Password: Enter the password set during the container setup. 

4. Test Connection 

# Click the Connect button. If the connection details are correct, Azure Data Studio will establish a connection to your SQL Server instance. 

 5. Start and Stop Docker Containers
 # List all running containers
docker ps

# List ALL containers (including stopped ones)
docker ps -a

# Start a running container gracefully
docker start <container_id_or_name> # docker start 523
# Stop a running container gracefully
docker stop <container_id_or_name> # docker stop 523


```
# Create Database and Import data from csv
<a id="Create-Database-and-Import-data-from-csv"></a>
```sql

CREATE DATABASE FinDB;
/*
	Drop database FinDB and backup history
		USE [master]
		GO
		ALTER DATABASE [FinDB] SET SINGLE_USER WITH ROLLBACK IMMEDIATE
		GO
		USE [master]
		GO	
		DROP DATABASE [FinDB]
		GO
		EXEC msdb.dbo.sp_delete_database_backuphistory @database_name = N'FinDB'
		GO
*/
/*
	Install SQL Server Import to import csv data into database
	press **Ctrl**+**I** to start the  Import wizard.
*/
/*
	Step 1. Specify the input file
		Server the database  is in: 127.0.0.1,1433
		Database the table is created in: FinDB
		Location of the file to be imported: Browse the csv file
		New table name: The name you want
		Table Schema: dbo
	Step 2. Next
	Step 3. Modify Columns
		Table GL -- no need to modify
		Table COA -- Account_key (primary key)
		Table Territory -- Territory_key (primary key)
		Table Calendar -- Date (primary key)
		
*/

```
# Getting-started-with-SQL-SELECT
<a id="Getting-started-with-SQL-SELECT"></a>
```sql
select * from GL ;
select * from coa;
select * from Territory;
select * from calendar;
```
# SELECT-specific-Columns-and-Rows
<a id="SELECT-specific-Columns-and-Rows"></a>
```sql
select Date, Amount 
from gl;

select * 
from GL
where 
    Account_key =10
AND
    Territory_key =3
AND
    Amount > 100000;

```
# Selecting-WHERE
<a id="Selecting-WHERE"></a>
```sql
select * 
from GL
WHERE
    Date = '2018-10-22';

select * 
from GL
WHERE
    Details = 'Salaries';

select * 
from GL
WHERE
    Account_key <> 230;

select * 
from GL
WHERE
    Account_key between 10 and 60;

select * 
from GL
WHERE
    Date Between '2018-01-01' and '2018-01-31';

```
# Time-Intelligence-Date-Month
<a id="Time-Intelligence-Date-Month"></a>
```sql
select *, YEAR(Date) as 'Year' , MONTH(Date) as 'MONTH', DAY(Date) as 'DAY'
from Gl;

select * 
from GL 
WHERE  
    YEAR([Date]) = 2019
and
    MONTH([Date]) = 9; --The brackets make it explicit that you're referring to a column named Date

/*  When you must use brackets
SELECT [Order Date] FROM Orders  -- Column name with space
SELECT [User] FROM Profiles      -- Reserved keyword as column name
SELECT [Group] FROM Categories  -- Reserved keyword
*/
```
# Time-Intelligence-Part-2-DATEPART
<a id="Time-Intelligence-Part-2-DATEPART"></a>
```sql
--GL has duplicate date so always try to use calendar to extract date

SELECT 
    [Date],
    DATEPART(year, [date]) as 'year',
    DATEPART(month, [date]) as 'month',
    DATEPART(day, [date]) as 'DayofMonth',
    DATEPART(DAYOFYEAR, [date]) as 'DayofYear',
    DATEPART(quarter, [date]) as 'quarter',
    datepart(week, [date]) as 'weekNumber',
    DATEPART(weekday, [date]) as 'weekDay'
    /*  
        By default, SQL Server considers Sunday as the first day of the week (mapped to 1)
        January 1, 2018, was a Monday, so DATEPART(weekday, [date]) returned 2 ,
        (Monday being the second day of the week in this default configuration).
    */
from calendar;
```
# Time-Intelligence-in-Action-Basic-Example
<a id="Time-Intelligence-in-Action-Basic-Example"></a>
```sql

select * 
from gl 
where 
    Account_key = 210 -- Sales Account
AND
    DATEPART(week, [date]) > 46; --month of december and last half of november

-- Thanksgiving  all transaction
WITH ThanksgivingDate AS (
    select *
    from
        (SELECT *, 
            ROW_NUMBER() OVER (PARTITION BY DATEPART(Year, [Date]) ORDER BY [Date]) AS ThursdayRank
        FROM Calendar
        WHERE 
            DATEPART(MONTH, [Date]) = 11
            AND DATEPART(WEEKDAY, [Date]) = 5  -- Filters for Thursdays
        ) as t
    where t.ThursdayRank = 4
)
SELECT g.*    
FROM 
    gl AS g
INNER JOIN 
    ThanksgivingDate AS t 
ON 
    g.Date = t.Date;

-- BlackFriday all transaction
WITH BlackFriday AS (
    select DATEADD(DAY,1, t.[Date]) as BlackFridayDate
    from
        (SELECT *, 
            ROW_NUMBER() OVER (PARTITION BY DATEPART(Year, [Date]) ORDER BY [Date]) AS ThursdayRank
        FROM Calendar
        WHERE 
            DATEPART(MONTH, [Date]) = 11
            AND DATEPART(WEEKDAY, [Date]) = 5  -- Filters for Thursdays
        ) as t
    where t.ThursdayRank = 4 -- filter for thanksgiving date
)
SELECT g.*    
FROM 
    gl AS g
INNER JOIN 
    BlackFriday AS bf
ON 
    g.Date = bf.BlackFridayDate
--where g.Account_key= 210;

```
# SUM-and-Group
<a id="SUM-and-Group"></a>
```sql
select 
    Territory_key, Account_key, sum(Amount) as 'Amount'
from GL
Where 
    Account_key =210
Group by 
    Territory_key, Account_key
Order by 
    Territory_key, Account_key;
```
# Making-and-Using-SubQuery
<a id="Making-and-Using-SubQuery"></a>
```sql
select 
    Year, sum(amount) as TotalAmount
FROM
(
    select Year(date) as 'Year', amount from GL
) as subquery 
group by 
    Year
order by 
    Year;
```
# PIVOT-data-into-Columns
<a id="PIVOT-data-into-Columns"></a>
```sql
select [2018], [2019], [2020]
FROM
    (
        select Year(date) as 'Year', Amount from GL
    ) as subquery 
PIVOT
(
    SUM(Amount) FOR YEAR in ([2018], [2019], [2020])
) as PivotTable

select 
	Account_key, [2018], [2019], [2020]
from 
(
    select Account_key, YEAR(date) as 'Year', Amount from GL
    
)as subquery
PIVOT
(
    SUM(amount) for [Year] in ([2018], [2019], [2020])
) as pivottable
```
# Create-VIEW
<a id="Create-VIEW"></a>
```sql
CREATE VIEW summary as 
select 
	Account_key, [2018], [2019], [2020]
from 
(
    select Account_key, YEAR(date) as 'Year', Amount from GL
    
)as subquery
PIVOT
(
    SUM(amount) for [Year] in ([2018], [2019], [2020])
) as pivottable

select 
    *
from summary 
where 
    account_key = 121;
```
# JOIN-Tables 
<a id="JOIN-Tables"></a>
```sql
select 
    *
from gl
INNER JOIN COA  -- JOIN AND INNER JOIN BOTH WORKS SAME
ON 
    gl.Account_key = coa.account_key;

select 
    *
from gl
JOIN Territory
ON 
    gl.territory_key = Territory.territory_key;

select 
    Date, GL.Territory_key, Amount, Country
from gl
inner JOIN Territory
ON 
    gl.territory_key = Territory.territory_key;

select 
    Date, Amount, Report, SubAccount
from gl
INNER JOIN COA  
ON 
    gl.Account_key = coa.account_key
Order by
    Report;
```
# RIGHT-JOIN-LEFT-JOIN- FULL-JOIN
<a id="RIGHT-JOIN-LEFT-JOIN-FULL-JOIN"></a>
```sql
select 
    Date, GL.Territory_key, Amount, Country
from gl
RIGHT JOIN Territory
ON 
    gl.territory_key = Territory.territory_key;

select 
    Date, GL.Territory_key, Amount, Country
from gl
LEFT JOIN Territory
ON 
    gl.territory_key = Territory.territory_key;

select 
    Date, GL.Territory_key, Amount, Country
from gl
FULL JOIN Territory
ON 
    gl.territory_key = Territory.territory_key;

/*
    inner join:
        JOIN -- ONLY Matching Rows
    outer join:
        RIGHT JOIN -- all the records from the right
        LEFT JOIN -- all the records from the left
        FULL JOIN -- ALL THE Records from all the tables
*/

-- Joining 3 tables
select 
    gl.*, Territory.Country, COA.Account
from gl
JOIN Territory
ON 
    gl.territory_key = Territory.territory_key
JOIN COA
ON
    gl.Account_key = COA.account_key;

-- Joining 4 tables
select 
    *
from gl
JOIN Territory
ON 
    gl.territory_key = Territory.territory_key
JOIN COA
ON
    gl.Account_key = COA.account_key
JOIN Calendar
ON
    gl.[date] = Calendar.[date];
```

# FORMAT-numbers
<a id="FORMAT-numbers"></a>
```sql
select 
    Date, FORMAT(amount, 'N0') as amount -- 'N1' is for one decimal place
from gl
```
# Preparing-Profit-Loss-Statement
<a id="Preparing-Profit-Loss-Statement"></a>
```sql
SELECT 
    Gl.Account_key, report, class, account, SUM(amount ) as 'Total Amount'
from GL
JOIN COA
ON
    GL.Account_key = COA.Account_key
WHERE
    Report = 'Profit and Loss'
AND
    --YEAR([Date]) = 2018
    [Date] BETWEEN '2020-01-01' AND '2020-01-31'
GROUP by 
    report, class, account, Gl.Account_key
ORDER by 
    Gl.Account_key ;

SELECT 
    Report, Class, Account, 
    FORMAT([2018],'N0') AS '2018', 
    FORMAT([2019],'N0') AS '2019',
    FORMAT([2020],'N0') AS '2020'
FROM
(
    SELECT 
        Gl.Account_key, report, class, account,
        YEAR([DATE]) as 'Year', 
        SUM(amount ) as 'Total Amount'
    from GL
    JOIN COA
    ON
        GL.Account_key = COA.Account_key
    WHERE
        Report = 'Profit and Loss'
    GROUP by 
        report, class, account, Gl.Account_key, YEAR([date])
   -- ORDER by 
    --    Gl.Account_key
) as Table1
PIVOT
(
    SUM([Total Amount])for [Year] in ([2018], [2019], [2020])
) as PivotTable;

-- Profit and Loss	by Country
SELECT 
    Country,Report, Class, Account, 
    FORMAT([2018],'N0') AS '2018', 
    FORMAT([2019],'N0') AS '2019',
    FORMAT([2020],'N0') AS '2020'
FROM
(
    SELECT 
        Country, Gl.Account_key, report, class, account,
        YEAR([DATE]) as 'Year', 
        SUM(amount ) as 'Total Amount'
    from GL
    JOIN COA
    ON
        GL.Account_key = COA.Account_key
    JOIN Territory 
    ON
        GL.Territory_key = Territory.Territory_key
    WHERE
        Report = 'Profit and Loss'
    --AND
    --    Country = 'France'
    GROUP by 
        Country, report, class, account, Gl.Account_key, YEAR([date])
   -- ORDER by 
    --    Country
) as Table1
PIVOT
(
    SUM([Total Amount])for [Year] in ([2018], [2019], [2020])
) as PivotTable;
```
# Preparing-Balance-Sheet-Understanding-the-problem
<a id="Preparing-Balance-Sheet-Understanding-the-problem"></a>
```sql
/*
	* In the profit and loss statement the figures are reported for the period
	* like, 2018 -> 1M profit, 2019 -> 3M profit, 2020 -> 2M loss
	* But, in the balance sheet the figures are reported as comulative way like,
	* 2018 banance sheet -> 1 million,
	* 2019 balance sheet -> another 1 million + previous 1 million become (2M)
*/
```
# SQL-for-Cumulative-SUM
<a id="SQL-for-Cumulative-SUM"></a>
```sql
-- Comulative sum over distinct date
select 
    distinct date,sum(amount) over (order by date) as Amount
from gl
order by 
    [Date];
-- run these two query and compare the column to understand the comulative sum totally
SELECT 
    [Date], sum(amount) as amount
from GL
GROUP by [Date]
ORDER by [Date];

select 
    distinct [date], territory_key, account_key,
    sum(amount) over(partition by territory_key, account_key order by date) as Amount
from gl 
order by [Date];
```
# Cumulative-SUM-Part-2
<a id="Cumulative-SUM-Part-2"></a>
```sql
select 
    DISTINCT [date], territory_key, account_key,
    sum(amount ) over(partition by territory_key, account_key order by date) as Amount
from gl 
order by [Date];

-- run below these two queries at once to understand the above query properly
SELECT DISTINCT 
    [date], 
    territory_key, 
    account_key,
    SUM(amount) OVER (PARTITION BY territory_key, account_key ORDER BY [date]) AS Amount
FROM gl
WHERE account_key = 20 AND territory_key = 1
ORDER BY [date];

SELECT DISTINCT 
    [date], 
    territory_key, 
    account_key,
    amount
FROM gl
WHERE account_key = 20 AND territory_key = 1
ORDER BY [date];

-- Comulative sum separate by year
select 
    distinct Year([date]) as 'Year', territory_key, account_key,
    sum(amount ) over(partition by territory_key, account_key order by Year([date])) as Amount
from gl 
order by Year([date]);
```
# Preparing Balance-Sheet
<a id="Preparing-Balance-Sheet"></a>
```sql
select 
    DISTINCT YEAR([date]) as 'Year', 
    country, report, class, subclass, subclass2, account, subaccount, 
    sum(amount) over( partition by country, subaccount order by YEAR([Date])) as Amount
    /*
        over( partition by country, report, class, subclass, subclass2, account, subaccount order by YEAR([Date]))
        same as
        over( partition by country, subaccount order by YEAR([Date]))
            * when partition happen in the lowest class all above class autometically get partitioned
    */
from GL
JOIN Territory
on 
    gl.territory_key = territory.territory_key
JOIN COA
on 
    coa.account_key = gl.account_key
WHERE
    Report = 'Balance Sheet';

```
# Balance-Sheet-Final
<a id="Balance-Sheet-Final"></a>
```sql
-- balance sheet report 
select 
    report, class, subclass, subclass2, account, subaccount,
    [2018], [2019], [2020]
FROM
(
    select 
        DISTINCT YEAR([date]) as 'Year', 
        report, class, subclass, subclass2, account, subaccount, 
        sum(amount) over( partition by subaccount order by YEAR([Date])) as Amount
        /*
            over( partition by report, class, subclass, subclass2, account, subaccount order by YEAR([Date]))
            same as
            over( partition by subaccount order by YEAR([Date]))
                * when partition happen in the lowest class all above class autometically get partitioned
        */
    from GL
    JOIN Territory
    on 
        gl.territory_key = territory.territory_key
    JOIN COA
    on 
        coa.account_key = gl.account_key
    WHERE
        Report = 'Balance Sheet'

) as Table1
PIVOT
(
    sum(amount) for [Year] in ([2018], [2019], [2020])
)as PivotTable
order by 
    class, subclass, subclass2, account, subaccount

-- balance sheet report by country
select 
    country, report, class, subclass, subclass2, account, subaccount,
    [2018], [2019], [2020]
FROM
(
    select 
        DISTINCT YEAR([date]) as 'Year', 
        country, report, class, subclass, subclass2, account, subaccount, 
        sum(amount) over( partition by country, subaccount order by YEAR([Date])) as Amount
        /*
            over( partition by country, report, class, subclass, subclass2, account, subaccount order by YEAR([Date]))
            same as
            over( partition by country, subaccount order by YEAR([Date]))
                * when partition happen in the lowest class all above class autometically get partitioned
        */
    from GL
    JOIN Territory
    on 
        gl.territory_key = territory.territory_key
    JOIN COA
    on 
        coa.account_key = gl.account_key
    WHERE
        Report = 'Balance Sheet'

) as Table1
PIVOT
(
    sum(amount) for [Year] in ([2018], [2019], [2020])
)as PivotTable

 -- to verify the above query
 select 
        DISTINCT YEAR([date]) as 'Year', 
        country, report, class, subclass, subclass2, account, subaccount, 
        sum(amount) over( partition by country, subaccount order by YEAR([Date])) as Amount
        /*
            over( partition by country, report, class, subclass, subclass2, account, subaccount order by YEAR([Date]))
            same as
            over( partition by country, subaccount order by YEAR([Date]))
                * when partition happen in the lowest class all above class autometically get partitioned
        */
from GL
JOIN Territory
on 
    gl.territory_key = territory.territory_key
JOIN COA
on 
    coa.account_key = gl.account_key
WHERE
    Report = 'Balance Sheet'
AND 
    SubAccount='cash at bank'
AND
    class = 'assets'
AND
    subclass='assets'
and 
    Country = 'australia';
```
# Learning-the-CASE-WHEN-statement
<a id="Learning-the-CASE-WHEN-statement"></a>
```sql
-- creating column using case statement
select 
    sum(
        case 
            when year(date) = 2018 then amount 
            else 0
        end 
    ) as '2018',
    sum(
        case 
            when year(date) = 2019 then amount 
            else 0
        end 
    ) as '2019',
    sum(
        case 
            when year(date) = 2020 then amount 
            else 0
        end 
    ) as '2020'
from GL

-- Adding some column to case statement

select
    account_key, territory_key,
    sum(
        case 
            when year(date) = 2018 then amount 
            else 0
        end 
    ) as '2018',
    sum(
        case 
            when year(date) = 2019 then amount 
            else 0
        end 
    ) as '2019',
    sum(
        case 
            when year(date) = 2020 then amount 
            else 0
        end 
    ) as '2020'
from GL
group  by account_key, Territory_key
order by account_key, territory_key;
```
# Calculating-Sales
<a id="Calculating-Sales"></a>
```sql
--showing yearly Net_Sales row-wise
select 
    YEAR([date]) as 'Year',
    sum(case when SubClass = 'sales' then amount else 0 end) as Net_Sales
from GL
join coa on gl.account_key = coa.account_key
group by YEAR([date])
order by YEAR([DATE]);

-- showing yearly Net_Sales column-wise
select 
    sum(case when SubClass = 'sales' and YEAR([date])= 2018 then amount else 0 end) as '2018',
    sum(case when SubClass = 'sales' and YEAR([date])= 2019 then amount else 0 end) as '2019',
    sum(case when SubClass = 'sales' and YEAR([date])= 2020 then amount else 0 end) as '2020'
from GL
join coa on gl.account_key = coa.account_key;
```
# Calculating-Gross-Profit-and-Net-Profit
<a id="Calculating-Gross-Profit-and-Net-Profit"></a>
```sql
--showing yearly sales, gorss_profit and net_profit row-wise
select 
    YEAR([date]) as 'Year',
    sum(case when SubClass = 'sales' then amount else 0 end) as 'Net_Sales',
    sum(case when Class = 'Trading account' then amount else 0 end) as 'Gross_Profit',
    sum(case when Report = 'Profit and Loss' then amount else 0 end) as 'Net_Profit'

from GL
join coa on gl.account_key = coa.account_key
group by YEAR([date])
order by YEAR([DATE]);

-- showing yearly sales, gorss_profit and net_profit column-wise USING PIVOT TABLE
SELECT 'Net_Sales' AS Metric, 
       [2018] AS [2018], [2019] AS [2019], [2020] AS [2020] -- add more years as needed
FROM (
    SELECT YEAR([date]) AS Year, 
           SUM(CASE WHEN SubClass = 'sales' THEN amount ELSE 0 END) AS Net_Sales
    FROM GL 
    JOIN coa ON gl.account_key = coa.account_key 
    GROUP BY YEAR([date])
    /*
    SELECT YEAR([date]) AS Year, 
           SUM(amount) AS Sales
    FROM GL 
    JOIN coa ON gl.account_key = coa.account_key 
    where  SubClass = 'sales'
    GROUP BY YEAR([date])
    */
) AS SourceTable
PIVOT (
    SUM(Net_Sales) FOR Year IN ([2018], [2019], [2020]) -- add more years as needed
) AS PivotTable

UNION ALL

SELECT 'Gross_Profit' AS Metric, 
       [2018], [2019], [2020]
FROM (
    SELECT YEAR([date]) AS Year, 
           SUM(CASE WHEN Class = 'Trading account' THEN amount ELSE 0 END) AS Gross_Profit
    FROM GL 
    JOIN coa ON gl.account_key = coa.account_key 
    GROUP BY YEAR([date])
) AS SourceTable
PIVOT (
    SUM(Gross_Profit) FOR Year IN ([2018], [2019], [2020])
) AS PivotTable

UNION ALL

SELECT 'Net_Profit' AS Metric, 
       [2018], [2019], [2020]
FROM (
    SELECT YEAR([date]) AS Year, 
           SUM(CASE WHEN Report = 'Profit and Loss' THEN amount ELSE 0 END) AS Net_Profit
    FROM GL 
    JOIN coa ON gl.account_key = coa.account_key 
    GROUP BY YEAR([date])
) AS SourceTable
PIVOT (
    SUM(Net_Profit) FOR Year IN ([2018], [2019], [2020])
) AS PivotTable;

-- showing yearly sales, gorss_profit and net_profit column-wise USING CASE STATEMENT

SELECT 
    Metric,
    SUM(CASE WHEN Year = 2018 THEN Value ELSE 0 END) AS [2018],
    SUM(CASE WHEN Year = 2019 THEN Value ELSE 0 END) AS [2019],
    SUM(CASE WHEN Year = 2020 THEN Value ELSE 0 END) AS [2020]
    -- Add more years as needed
FROM (
    SELECT 
        YEAR([date]) AS Year,
        'Net_Sales' AS Metric,
        SUM(CASE WHEN SubClass = 'sales' THEN amount ELSE 0 END) AS Value
    FROM GL 
    JOIN coa ON gl.account_key = coa.account_key 
    GROUP BY YEAR([date])
    /*
    SELECT YEAR([date]) AS Year,
           'Net_Sales' as Metric,
           SUM(amount) AS Value
    FROM GL 
    JOIN coa ON gl.account_key = coa.account_key 
    where  SubClass = 'sales'
    GROUP BY YEAR([date])
    */
    
    UNION ALL
    
    SELECT 
        YEAR([date]) AS Year,
        'Gross_Profit' AS Metric,
        SUM(CASE WHEN Class = 'Trading account' THEN amount ELSE 0 END) AS Value
    FROM GL 
    JOIN coa ON gl.account_key = coa.account_key 
    GROUP BY YEAR([date])
    
    UNION ALL
    
    SELECT 
        YEAR([date]) AS Year,
        'Net_Profit' AS Metric,
        SUM(CASE WHEN Report = 'Profit and Loss' THEN amount ELSE 0 END) AS Value
    FROM GL 
    JOIN coa ON gl.account_key = coa.account_key 
    GROUP BY YEAR([date])
) AS CombinedData
GROUP BY Metric
ORDER BY 
    CASE Metric 
        WHEN 'Net_Sales' THEN 1
        WHEN 'Gross_Profit' THEN 2
        WHEN 'Net_Profit' THEN 3
    END;
```
# Calculating-EBITDA-Operating-Profit-and-PBIT
<a id="Calculating-EBITDA-Operating-Profit-and-PBIT"></a>
```sql
/*
	### Steps to Calculate EBITDA:
		1. Start with **Net Sales** = `Sales - Sales Return`.
		2. Subtract **Cost of Sales** (COGS).  # this is gross profit  
		3. Subtract all **Operating Expenses** (Sales & Distribution, Marketing, Administration).  
		4. Add back all **Depreciation and Amortization** (non-cash expenses).
*/

select 
    YEAR([date]) as 'Year',
    sum(case when SubClass = 'sales' then amount else 0 end) as 'Net_Sales',
    sum(case when Class = 'Trading account' then amount else 0 end) as 'Gross_Profit',
    sum(case when Subclass = 'Sales' or Subclass = 'Cost of Sales' or Subclass = 'Operating Expenses' Then amount else 0 end) as 'EBITDA', -- Earnings Before Interest, Taxes, Depreciation, and Amortization
    sum(case when Class = 'Operating account' or Class = 'Trading account' Then amount else 0 end) as 'Operating_profit',
    sum(case when Class = 'Operating account' or Class = 'Trading account' or Class = 'Non-operating' Then amount else 0 end) as 'PBIT', -- Profit Before Interest and Taxes
    sum(case when Report = 'Profit and Loss' then amount else 0 end) as 'Net_Profit'
 
from GL
join coa on gl.account_key = coa.account_key
group by YEAR([date])
order by YEAR([DATE]);

```
# Creating-view-for-Gross-Profit-Margin-EBITDA-Operating-Profit-and-PBIT
<a id="Creating-view-for-Gross-Profit-Margin-EBITDA-Operating-Profit-and-PBIT"></a>
```sql
CREATE VIEW PLValues as 
select 
    YEAR([date]) as 'Year',
    sum(case when SubClass = 'sales' then amount else 0 end) as 'Net_Sales',
    sum(case when Class = 'Trading account' then amount else 0 end) as 'Gross_Profit',
    sum(case when Subclass = 'Sales' or Subclass = 'Cost of Sales' or Subclass = 'Operating Expenses' Then amount else 0 end) as 'EBITDA', -- Earnings Before Interest, Taxes, Depreciation, and Amortization
    sum(case when Class = 'Operating account' or Class = 'Trading account' Then amount else 0 end) as 'Operating_profit',
    sum(case when Class = 'Operating account' or Class = 'Trading account' or Class = 'Non-operating' Then amount else 0 end) as 'PBIT', -- Profit Before Interest and Taxes
    sum(case when Report = 'Profit and Loss' then amount else 0 end) as 'Net_Profit'
from GL
join coa on gl.account_key = coa.account_key
group by YEAR([date]);

select 
    [Gross_Profit]/[Net_Sales]*100 as GP_Margin 
FROM
plvalues;

-- breaking down values by country

CREATE VIEW PLValues1 as  
select 
    country,
    YEAR([date]) as 'Year',
    sum(case when SubClass = 'sales' then amount else 0 end) as 'Net_Sales',
    sum(case when Class = 'Trading account' then amount else 0 end) as 'Gross_Profit',
    sum(case when Subclass = 'Sales' or Subclass = 'Cost of Sales' or Subclass = 'Operating Expenses' Then amount else 0 end) as 'EBITDA', -- Earnings Before Interest, Taxes, Depreciation, and Amortization
    sum(case when Class = 'Operating account' or Class = 'Trading account' Then amount else 0 end) as 'Operating_profit',
    sum(case when Class = 'Operating account' or Class = 'Trading account' or Class = 'Non-operating' Then amount else 0 end) as 'PBIT', -- Profit Before Interest and Taxes
    sum(case when Report = 'Profit and Loss' then amount else 0 end) as 'Net_Profit'
from GL
join coa on gl.account_key = coa.account_key
join territory on gl.territory_key = territory.territory_key
group by YEAR([date]), country ;

select * FROM plvalues1;

select 
    year, sum(net_sales ) as 'Net_Sales'
from plvalues1
group by year;
```
# Calculating-Ratios
<a id="Calculating-Ratios"></a>
```sql
-- Profit margin by Year
select 
    year, 
    sum(Gross_Profit)/sum(net_sales) * 100 as GP_Margin,
    sum(Operating_Profit)/sum(net_sales) * 100 as Operating_Margin,
    sum(net_profit)/sum(net_sales) * 100 as Net_Margin

from plvalues1
group by year;

-- Gross profit margin by Year for selective country
select 
    year, sum(Gross_Profit)/sum(net_sales) * 100 as GP_Margin
from plvalues1
where country = 'France'
group by year
order by 1;
```
# Calculating-Balance-Sheet-Related-Values
<a id="Calculating-Balance-Sheet-Related-Values"></a>
```sql
-- balance sheet value by Year
select 
    distinct year(date) as 'Year',
    sum(case when class = 'Assets' then amount else 0 end) over(order by year(date)) as 'Assets',
    sum(case when subclass2 = 'Current Assets' then amount else 0 end) over(order by year(date)) as 'Current_Assets',
    sum(case when subclass2 = 'Non-Current Assets' then amount else 0 end) over(order by year(date)) as 'Non-Current_Assets',
    sum(case when subclass = 'Liabilities' then amount else 0 end) over(order by year(date)) as 'Liabilities',
    sum(case when subclass2 = 'Current Liabilities' then amount else 0 end) over(order by year(date)) as 'Current_Liabilities',
    sum(case when subclass2 = 'Long Term Liabilities' then amount else 0 end) over(order by year(date)) as 'NonCurrent_Liabilities',
    sum(case when subclass = 'Owners Equity' then amount else 0 end) over(order by year([date])) as 'Equity',
    sum(case when class = 'Liabilities and Owners Equity' then amount else 0 end) over(order by year([date])) as 'Liabilities_and_Equity',
    sum(case when Account = 'Inventory' then amount else 0 end) over(order by year(date)) as 'Inventory'
from GL
join COA
ON
    gl.account_key = coa.account_key
order by 1;

-- Balance sheet value by country

select 
    distinct country,
    year(date) as 'Year',
    sum(case when class = 'Assets' then amount else 0 end) over(partition by country order by year(date)) as 'Assets',
    sum(case when subclass2 = 'Current Assets' then amount else 0 end) over(partition by country order by year(date)) as 'Current_Assets',
    sum(case when subclass2 = 'Non-Current Assets' then amount else 0 end) over(partition by country order by year(date)) as 'Non-Current_Assets',
    sum(case when subclass = 'Liabilities' then amount else 0 end) over(partition by country order by year(date)) as 'Liabilities',
    sum(case when subclass2 = 'Current Liabilities' then amount else 0 end) over(partition by country order by year(date)) as 'Current_Liabilities',
    sum(case when subclass2 = 'Long Term Liabilities' then amount else 0 end) over(partition by country order by year(date)) as 'NonCurrent_Liabilities',
    sum(case when subclass = 'Owners Equity' then amount else 0 end) over(partition by country order by year([date])) as 'Equity',
    sum(case when class = 'Liabilities and Owners Equity' then amount else 0 end) over(partition by country order by year([date])) as 'Liabilities_and_Equity',
    sum(case when Account = 'Inventory' then amount else 0 end) over(partition by country order by year(date)) as 'Inventory'
from GL
join COA
ON
    gl.account_key = coa.account_key
join territory
on 
    gl.territory_key = territory.territory_key
order by 1;
```
# Compiling-all-key-values-in-one-VIEW
<a id="Compiling-all-key-values-in-one-VIEW"></a>
```sql
CREATE VIEW BSValues as
select 
    distinct country,
    year(date) as 'Year',
    sum(case when class = 'Assets' then amount else 0 end) over(partition by country order by year(date)) as 'Assets',
    sum(case when subclass2 = 'Current Assets' then amount else 0 end) over(partition by country order by year(date)) as 'Current_Assets',
    sum(case when subclass2 = 'Non-Current Assets' then amount else 0 end) over(partition by country order by year(date)) as 'Non-Current_Assets',
    sum(case when subclass = 'Liabilities' then amount else 0 end) over(partition by country order by year(date)) as 'Liabilities',
    sum(case when subclass2 = 'Current Liabilities' then amount else 0 end) over(partition by country order by year(date)) as 'Current_Liabilities',
    sum(case when subclass2 = 'Long Term Liabilities' then amount else 0 end) over(partition by country order by year(date)) as 'NonCurrent_Liabilities',
    sum(case when subclass = 'Owners Equity' then amount else 0 end) over(partition by country order by year([date])) as 'Equity',
    sum(case when class = 'Liabilities and Owners Equity' then amount else 0 end) over(partition by country order by year([date])) as 'Liabilities_and_Equity',
    sum(case when Account = 'Inventory' then amount else 0 end) over(partition by country order by year(date)) as 'Inventory'
from GL
join COA
ON
    gl.account_key = coa.account_key
join territory
on 
    gl.territory_key = territory.territory_key ;

--select * from BSValues ;
--select * from PLValues1 ;

CREATE VIEW FinValues AS
select 
    bs.*,
    pl.Net_Sales,
    pl.Gross_Profit,
    pl.EBITDA,
    pl.Operating_Profit,
    pl.PBIT,
    pl.Net_Profit

from BSValues as bs
JOIN PLValues1 as pl on bs.country = pl.country and bs.year = pl.year ;

Select * from FinValues;
```
# Calculating-Ratios-FinValues-Table
<a id="Calculating-Ratios-FinValues-Table"></a>
```sql
select 
    year, 
    sum(Gross_Profit) / sum(net_sales) * 100 as GP_Margin,
    sum(Operating_Profit) / sum(net_sales) * 100 as Operating_Margin,
    sum(net_profit) / sum(net_sales) * 100 as Net_Margin,
    sum(Net_sales) / sum(Assets) *100 as 'Asset_Turnover',
    sum(PBIT) / sum(Equity+NonCurrent_Liabilities) * 100 as 'ROCE', --Return on Capital Employed
    SUM(Net_profit) / sum(Equity) * 100 as 'ROE', --Return on Equity
    Sum(Liabilities) / sum(Equity) * 100 as 'Gearing',
    sum(current_assets) / sum(current_liabilities) as 'Current_Ratio',
    (sum(current_assets) - sum(Inventory)) / sum(Current_liabilities) as 'Quick_Ratio'
from FinValues
group by year
order by YEAR;
```
# Calculating-further-values-for-Ratios-and-updating-VIEW-PLValues1
<a id="Calculating-further-values-for-Ratios-and-updating-VIEW-PLValues1"></a>
```sql
DROP VIEW PLValues1;

CREATE VIEW PLValues1 AS
select 
    country,
    YEAR([date]) as 'Year',
    sum(case when SubClass = 'sales' then amount else 0 end) as 'Net_Sales',
    sum(case when Class = 'Trading account' then amount else 0 end) as 'Gross_Profit',
    sum(case when Subclass = 'Sales' or Subclass = 'Cost of Sales' or Subclass = 'Operating Expenses' Then amount else 0 end) as 'EBITDA', -- Earnings Before Interest, Taxes, Depreciation, and Amortization
    sum(case when Class = 'Operating account' or Class = 'Trading account' Then amount else 0 end) as 'Operating_profit',
    sum(case when Class = 'Operating account' or Class = 'Trading account' or Class = 'Non-operating' Then amount else 0 end) as 'PBIT', -- Profit Before Interest and Taxes
    sum(case when Report = 'Profit and Loss' then amount else 0 end) as 'Net_Profit',
    sum(case when subclass = 'Cost of Sales' then amount else 0 end) as 'Cost_of_Sales',
    sum(case when subclass = 'Interest Expense' then amount else 0 end) as 'Interest_Expense'
from GL
join coa on gl.account_key = coa.account_key
join territory on gl.territory_key = territory.territory_key
group by YEAR([date]), country ;

select * from PLValues1;
```
# Calculating-Receivables-and-Payables-and-updating-VIEW-BSValues
<a id="Calculating-Receivables-and-Payables-and-updating-VIEW-BSValues"></a>
```sql
DROP VIEW BSValues;

CREATE VIEW BSValues AS
select 
    distinct country,
    year(date) as 'Year',
    sum(case when class = 'Assets' then amount else 0 end) over(partition by country order by year(date)) as 'Assets',
    sum(case when subclass2 = 'Current Assets' then amount else 0 end) over(partition by country order by year(date)) as 'Current_Assets',
    sum(case when subclass2 = 'Non-Current Assets' then amount else 0 end) over(partition by country order by year(date)) as 'Non-Current_Assets',
    sum(case when subclass = 'Liabilities' then amount else 0 end) over(partition by country order by year(date)) as 'Liabilities',
    sum(case when subclass2 = 'Current Liabilities' then amount else 0 end) over(partition by country order by year(date)) as 'Current_Liabilities',
    sum(case when subclass2 = 'Long Term Liabilities' then amount else 0 end) over(partition by country order by year(date)) as 'NonCurrent_Liabilities',
    sum(case when subclass = 'Owners Equity' then amount else 0 end) over(partition by country order by year([date])) as 'Equity',
    sum(case when class = 'Liabilities and Owners Equity' then amount else 0 end) over(partition by country order by year([date])) as 'Liabilities_and_Equity',
    sum(case when Account = 'Inventory' then amount else 0 end) over(partition by country order by year(date)) as 'Inventory',
    sum(case when SubAccount = 'Trade Receivables' then amount else 0 end) over(Partition by country order by year(date)) as 'Trade_Receivables',
    sum(case when Account = 'Trade Payables' then amount else 0 end) Over(partition by country order by year(date)) as 'Trade_Payables'
from GL
join COA
ON
    gl.account_key = coa.account_key
join territory
on 
    gl.territory_key = territory.territory_key ;

select * from BSVlaues;
```
# Updating-VIEW-FinValues
<a id="Updating-VIEW-FinValues"></a>
```sql
DROP VIEW FinValues;

CREATE VIEW FinValues AS
select 
    bs.*,
    pl.Net_Sales,
    pl.Gross_Profit,
    pl.EBITDA,
    pl.Operating_Profit,
    pl.PBIT,
    pl.Net_Profit,
    pl.Cost_of_Sales,
    pl.Interest_Expense

from BSValues as bs
JOIN PLValues1 as pl on bs.country = pl.country and bs.year = pl.year ;

Select * from FinValues;
```
# Calculating-FinValues-Ratios-of-Interest-Cover-Inventory-Receivables-Payables-Turnover-Period
<a id="Calculating-FinValues-Ratios-of-Interest-Cover-Inventory-Receivables-Payables-Turnover-Period"></a>
```sql
select 
    year, 
    sum(Gross_Profit) / sum(net_sales) * 100 as GP_Margin,
    sum(Operating_Profit) / sum(net_sales) * 100 as Operating_Margin,
    sum(net_profit) / sum(net_sales) * 100 as Net_Margin,
    sum(Net_sales) / sum(Assets) *100 as 'Asset_Turnover',
    sum(PBIT) / sum(Equity+NonCurrent_Liabilities) * 100 as 'ROCE', --Return on Capital Employed
    SUM(Net_profit) / sum(Equity) * 100 as 'ROE', --Return on Equity
    Sum(Liabilities) / sum(Equity) * 100 as 'Gearing',
    sum(current_assets) / sum(current_liabilities) as 'Current_Ratio',
    (sum(current_assets) - sum(Inventory)) / sum(Current_liabilities) as 'Quick_Ratio',
    sum(PBIT) / Sum(Interest_Expense) * -1 as 'Interest_Cover',
    sum(Inventory) / sum(Cost_of_Sales) * 365 * -1 as 'Inventory_turnover_period',
    sum(Trade_Receivables) / Sum(Net_Sales) * 365 as 'Receivables_turnover_period',
    sum(Trade_Payables) / Sum(Cost_of_Sales) * 365 * -1 as 'Payables_turnover_period'
from FinValues
group by year
order by YEAR;
```
# Slicing-Ratios-for-Country
<a id="Slicing-Ratios-for-Country"></a>
```sql
select 
    year, 
    sum(Gross_Profit) / sum(net_sales) * 100 as GP_Margin,
    sum(Operating_Profit) / sum(net_sales) * 100 as Operating_Margin,
    sum(net_profit) / sum(net_sales) * 100 as Net_Margin,
    sum(Net_sales) / sum(Assets) *100 as 'Asset_Turnover',
    sum(PBIT) / sum(Equity+NonCurrent_Liabilities) * 100 as 'ROCE', --Return on Capital Employed
    SUM(Net_profit) / sum(Equity) * 100 as 'ROE', --Return on Equity
    Sum(Liabilities) / sum(Equity) * 100 as 'Gearing',
    sum(current_assets) / sum(current_liabilities) as 'Current_Ratio',
    (sum(current_assets) - sum(Inventory)) / sum(Current_liabilities) as 'Quick_Ratio',
    sum(PBIT) / Sum(Interest_Expense) * -1 as 'Interest_Cover',
    sum(Inventory) / sum(Cost_of_Sales) * 365 * -1 as 'Inventory_turnover_period',
    sum(Trade_Receivables) / Sum(Net_Sales) * 365 as 'Receivables_turnover_period',
    sum(Trade_Payables) / Sum(Cost_of_Sales) * 365 * -1 as 'Payables_turnover_period'
from FinValues
where country = 'USA'
group by year
order by YEAR;
```
# Uploading-CF-Table-to-our-Database
<a id="Uploading-CF-Table-to-our-Database"></a>
```sql
/*
	press **Ctrl**+**I** to start the  Import wizard.
*/
/*
	Step 1. Specify the input file
		Server the database  is in: 127.0.0.1,1433
		Database the table is created in: FinDB
		Location of the file to be imported: Browse the csv file
		New table name: CF
		Table Schema: dbo
	Step 2. Next
	Step 3. Modify Columns
		Table CF -- no need to modify
	Step 4. click Import Data
		
*/

```
# Calculating-Values-for-Cash-Flow-Statement-Part-1
<a id="Calculating-Values-for-Cash-Flow-Statement-Part-1"></a>
```sql
Select Rank, Type, SubType, [2018], [2019], [2020]
FROM
(
    select Rank, Type, Subtype, YEAR(Date) 'Year', 
        Sum(
            Case 
                when ValueType = 'All_FTP' Then Amount
                When ValueType = 'All_FTP_CS' Then Amount *-1
                when ValueType = 'All_FTP_Negative' And Amount < 0 Then Amount
                when ValueType = 'All_FTP_Positive' And Amount > 0 Then Amount
                when ValueType = 'All_FTP_Negative_CS' And Amount < 0 Then Amount * -1
                when ValueType = 'All_FTP_Positive_CS' And Amount > 0 Then Amount * -1


            else 0
            end
        ) as 'Amount'
    from GL
    JOIN CF on Gl.Account_key = CF.Account_key
    WHERE ValueType NOT IN ('Opening_balance', 'Closing_balance')
    Group BY Rank, Type, Subtype, YEAR(Date)
) as Table1
PIVOT
(
    Sum(Amount) FOR [Year] IN ([2018], [2019], [2020])
)as PivotTable
```
# Calculating-Cash-Cash-Equivalents-at-the-end-of-the-Year
<a id="Calculating-Cash-Cash-Equivalents-at-the-end-of-the-Year"></a>
```sql
Select Rank, Type, SubType, [2018], [2019], [2020]
FROM
(
    select 
        Distinct Rank, Type, Subtype, YEAR(Date) 'Year', 
        Sum(Amount) Over(Partition by Rank, Type, Subtype Order by YEAR(Date)) AS Amount
    from GL
    JOIN CF on Gl.Account_key = CF.Account_key
    WHERE 
    Type = 'Cash and Cash equivalents at the end of the year'
) as Table1
PIVOT
(
    Sum(Amount) FOR [Year] IN ([2018], [2019], [2020])
)as PivotTable
```
# Calculating-Cash-Cash-Equivalents-at-the-start-of-the-year
<a id="Calculating-Cash-Cash-Equivalents-at-the-start-of-the-year"></a>
```sql
-- First Year's ending Capital is Next year's Working Capital
Select Rank, Type, SubType, [2018], [2019], [2020]
FROM
(
    Select 
        1 as Rank, 
        'Cash and Cash equivalents at the start of the year' as Type, 
        SubType, 
        Year,
        LAG(Amount, 1, 0) OVER(Order by Year ASC) as Amount
    FROM
    (
        select 
            Distinct Rank, Type, Subtype, YEAR(Date) 'Year', 
            Sum(Amount) Over(Partition by Rank, Type, Subtype Order by YEAR(Date)) AS Amount
        from GL
        JOIN CF on Gl.Account_key = CF.Account_key
        WHERE 
            Type = 'Cash and Cash equivalents at the end of the year'
    ) as subquery
) as Table1
PIVOT
(
    Sum(Amount) FOR [Year] IN ([2018], [2019], [2020])
)as PivotTable ;
```

# Compiling-Cash-Flow-Statement
<a id="Compiling-Cash-Flow-Statement"></a>
```sql
Select Rank, Type, SubType, [2018], [2019], [2020]
FROM
(
    Select 
        1 as Rank, 
        'Cash and Cash equivalents at the start of the year' as Type, 
        SubType, 
        Year,
        LAG(Amount, 1, 0) OVER(Order by Year ASC) as Amount
    FROM
    (
        select 
            Distinct Rank, Type, Subtype, YEAR(Date) 'Year', 
            Sum(Amount) Over(Partition by Rank, Type, Subtype Order by YEAR(Date)) AS Amount
        from GL
        JOIN CF on Gl.Account_key = CF.Account_key
        WHERE 
            Type = 'Cash and Cash equivalents at the end of the year'
    ) as subquery
) as Table1
PIVOT
(
    Sum(Amount) FOR [Year] IN ([2018], [2019], [2020])
)as PivotTable 

UNION ALL

Select Rank, Type, SubType, [2018], [2019], [2020]
FROM
(
    select Rank, Type, Subtype, YEAR(Date) 'Year', 
        Sum(
            Case 
                when ValueType = 'All_FTP' Then Amount
                When ValueType = 'All_FTP_CS' Then Amount *-1
                when ValueType = 'All_FTP_Negative' And Amount < 0 Then Amount
                when ValueType = 'All_FTP_Positive' And Amount > 0 Then Amount
                when ValueType = 'All_FTP_Negative_CS' And Amount < 0 Then Amount * -1
                when ValueType = 'All_FTP_Positive_CS' And Amount > 0 Then Amount * -1


            else 0
            end
        ) as 'Amount'
    from GL
    JOIN CF on Gl.Account_key = CF.Account_key
    WHERE ValueType NOT IN ('Opening_balance', 'Closing_balance')
    Group BY Rank, Type, Subtype, YEAR(Date)
) as Table1
PIVOT
(
    Sum(Amount) FOR [Year] IN ([2018], [2019], [2020])
)as PivotTable

UNION ALL

Select Rank, Type, SubType, [2018], [2019], [2020]
FROM
(
    select 
        Distinct Rank, Type, Subtype, YEAR(Date) 'Year', 
        Sum(Amount) Over(Partition by Rank, Type, Subtype Order by YEAR(Date)) AS Amount
    from GL
    JOIN CF on Gl.Account_key = CF.Account_key
    WHERE 
    Type = 'Cash and Cash equivalents at the end of the year'
) as Table1
PIVOT
(
    Sum(Amount) FOR [Year] IN ([2018], [2019], [2020])
)as PivotTable

```
