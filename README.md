# Banking Data Analysis

This project contains SQL queries used to analyze the **Bank Dataset** for various levels of complexity—beginner, intermediate, and advanced. The queries focus on understanding customer demographics, financial behaviors, and more.

## Table of Contents
- [Introduction](#introduction)
- [Project Structure](#project-structure)
- [SQL Queries](#sql-queries)
  - [Beginner Queries](#beginner-queries)
  - [Intermediate Queries](#intermediate-queries)
  - [Advanced Queries](#advanced-queries)
- [Contributing](#contributing)
- [License](#license)

## Introduction

This project is centered around a **bank's client dataset**, analyzing various factors such as client demographics, loan details, and term deposits. Using SQL, we extract meaningful insights from the dataset. This README provides an overview of the queries used to extract and analyze key data points, along with some advanced operations like grouping, filtering, and aggregation.

### Dataset

The dataset is structured as a relational database with columns like **age**, **job**, **balance**, **marital status**, and more.

## Project Structure

- `bank.bank`: The main dataset from which all the queries extract data.

## SQL Queries

### Beginner Queries

These queries focus on basic SQL operations such as viewing all records, selecting specific columns, and filtering data based on conditions.

1. **View all records**:
   ```sql
   SELECT * FROM bank.bank;
   ```
   - *Explanation*: This query retrieves all the records and columns from the dataset, allowing us to view the full data available in the bank table.

2. **Select specific columns**:
   ```sql
   SELECT age, job, balance FROM bank.bank;
   ```
   - *Explanation*: Here, we are selecting only the `age`, `job`, and `balance` columns from the dataset. This is useful when we need specific data points without pulling the entire dataset.

3. **Filter clients who are married**:
   ```sql
   SELECT * FROM bank.bank WHERE marital = 'married';
   ```
   - *Explanation*: This query filters the dataset to show only the records of clients who are married. The condition `WHERE marital = 'married'` is used to achieve this.

4. **Filter clients with a balance greater than 5000**:
   ```sql
   SELECT * FROM bank.bank WHERE balance > 5000;
   ```
   - *Explanation*: We use this query to find all clients who have a balance greater than 5000. It helps in identifying clients with significant deposits.

### Intermediate Queries

Here we delve into grouping, averaging, and counting specific subsets of data.

1. **Count the number of clients with a housing loan**:
   ```sql
   SELECT COUNT(*) FROM bank.bank WHERE housing = 'yes';
   ```
   - *Explanation*: This query counts the total number of clients who have taken a housing loan. It gives an overview of how many clients are using the bank's housing loan service.

2. **Find the average balance of clients based on marital status**:
   ```sql
   SELECT marital, AVG(balance) AS avg_balance 
   FROM bank.bank 
   GROUP BY marital;
   ```
   - *Explanation*: This query calculates the average balance for clients based on their marital status. The `GROUP BY` clause groups the data by `marital` status, and `AVG(balance)` calculates the average balance for each group.

3. **Find the average balance for each education level**:
   ```sql
   SELECT education, AVG(balance) 
   FROM bank.bank 
   GROUP BY education;
   ```
   - *Explanation*: Similar to the previous query, this one groups clients by `education` level and calculates the average balance for each group. It helps in understanding the relationship between education level and financial standing.

4. **Find the maximum balance among clients with personal loans**:
   ```sql
   SELECT MAX(balance) 
   FROM bank.bank 
   WHERE loan = 'yes';
   ```
   - *Explanation*: This query finds the highest balance among clients who have personal loans. It’s useful for determining the top depositors among loan holders.

### Advanced Queries

In advanced queries, we focus on more complex operations like grouping by job type, calculating percentages, and identifying specific client characteristics.

1. **Find the total balance of customers who subscribed to a term deposit, grouped by job type**:
   ```sql
   SELECT job, SUM(balance) AS Total_balance_by_Job
   FROM bank.bank
   WHERE y = 'yes'
   GROUP BY job;
   ```
   - *Explanation*: This query sums the total balance for customers who subscribed to a term deposit (where `y = 'yes'`), and it groups the results by job type. This helps in understanding which professions are more likely to have higher deposits.

2. **Calculate the percentage of customers who have both personal and housing loans**:
   ```sql
   SELECT (COUNT(*) * 100.0 / (SELECT COUNT(*) FROM bank.bank)) AS percentage
   FROM bank.bank
   WHERE loan = 'yes' AND housing = 'yes';
   ```
   - *Explanation*: Here, we calculate the percentage of clients who have both a personal loan and a housing loan. The main query counts the number of such clients, while the subquery counts the total number of clients to calculate the percentage.

3. **Identify customers with the longest last contact duration who subscribed to a term deposit**:
   ```sql
   SELECT * 
   FROM bank.bank 
   WHERE y = 'yes' 
   ORDER BY duration DESC 
   LIMIT 10;
   ```
   - *Explanation*: This query finds the top 10 customers with the longest last contact duration (where they subscribed to a term deposit). It orders the records by `duration` in descending order and limits the results to 10 rows.

4. **Find the relationship between education and the number of previous contacts**:
   ```sql
   SELECT education, AVG(previous) 
   FROM bank.bank
   GROUP BY education 
   ORDER BY AVG(previous) DESC;
   ```
   - *Explanation*: This query groups clients by their education level and calculates the average number of previous contacts for each group. It’s useful for analyzing how education influences engagement with the bank.


## Contributing

If you'd like to contribute to this project, feel free to submit a pull request or open an issue.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---
Let me know if you need further adjustments or more suggestions!
