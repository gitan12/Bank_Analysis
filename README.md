# Bank Dataset Query Analysis

This project contains SQL queries used to analyze the **Bank Dataset** for various levels of complexity—beginner, intermediate, and advanced. The queries focus on understanding customer demographics, financial behaviors, and more.

## Table of Contents
- [Introduction](#introduction)
- [Project Structure](#project-structure)
- [SQL Queries](#sql-queries)
  - [Beginner Queries](#beginner-queries)
  - [Intermediate Queries](#intermediate-queries)
  - [Advanced Queries](#advanced-queries)
- [Results](#results)
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

2. **Select specific columns**:
   ```sql
   SELECT age, job, balance FROM bank.bank;
   ```

3. **Filter clients who are married**:
   ```sql
   SELECT * FROM bank.bank WHERE marital = 'married';
   ```

4. **Filter clients with a balance greater than 5000**:
   ```sql
   SELECT * FROM bank.bank WHERE balance > 5000;
   ```

### Intermediate Queries

Here we delve into grouping, averaging, and counting specific subsets of data.

1. **Count the number of clients with a housing loan**:
   ```sql
   SELECT COUNT(*) FROM bank.bank WHERE housing = 'yes';
   ```

2. **Find the average balance of clients based on marital status**:
   ```sql
   SELECT marital, AVG(balance) AS avg_balance 
   FROM bank.bank 
   GROUP BY marital;
   ```

3. **Find the average balance for each education level**:
   ```sql
   SELECT education, AVG(balance) 
   FROM bank.bank 
   GROUP BY education;
   ```

4. **Find the maximum balance among clients with personal loans**:
   ```sql
   SELECT MAX(balance) 
   FROM bank.bank 
   WHERE loan = 'yes';
   ```

### Advanced Queries

In advanced queries, we focus on more complex operations like grouping by job type, calculating percentages, and identifying specific client characteristics.

1. **Find the total balance of customers who subscribed to a term deposit, grouped by job type**:
   ```sql
   SELECT job, SUM(balance) AS Total_balance_by_Job
   FROM bank.bank
   WHERE y = 'yes'
   GROUP BY job;
   ```

2. **Calculate the percentage of customers who have both personal and housing loans**:
   ```sql
   SELECT (COUNT(*) * 100.0 / (SELECT COUNT(*) FROM bank.bank)) AS percentage
   FROM bank.bank
   WHERE loan = 'yes' AND housing = 'yes';
   ```

3. **Identify customers with the longest last contact duration who subscribed to a term deposit**:
   ```sql
   SELECT * 
   FROM bank.bank 
   WHERE y = 'yes' 
   ORDER BY duration DESC 
   LIMIT 10;
   ```

4. **Find the relationship between education and the number of previous contacts**:
   ```sql
   SELECT education, AVG(previous) 
   FROM bank.bank
   GROUP BY education 
   ORDER BY AVG(previous) DESC;
   ```

## Results

You can include visualizations and screenshots of results from running the SQL queries. This section could contain graphs or tables that show the results of queries such as the average balance based on marital status or job type.

Sample visualizations:

1. ![Average Balance by Marital Status](path_to_visualization_image)
2. ![Maximum Balance with Personal Loans](path_to_visualization_image)

## Contributing

If you'd like to contribute to this project, feel free to submit a pull request or open an issue.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---


Let me know if you need further adjustments or more suggestions!
