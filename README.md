# SQL-Revision
## A short note for revising the SQL.

SQL stands for “structured query language”. It is a language used to query,
analyze, and manipulate data from databases. Today, SQL is one of the most
widely used tools in data.


**Title: SELECT and WHERE for Filtering and Selection in SQL**

Introduction:
SQL (Structured Query Language) is a powerful language used for managing and manipulating data in relational database management systems. Two essential components of SQL, SELECT and WHERE, are fundamental for filtering and selecting data. In this lesson, we will explore how to effectively use SELECT and WHERE clauses to retrieve specific information from a database.

I. The SELECT Statement:
The SELECT statement is used to retrieve data from one or more tables in a database. Its basic syntax is as follows:
```
SELECT column1, column2, ...
FROM table_name;
```
1. Retrieve All Columns:
   - To retrieve all columns from a table, use an asterisk (*) in the SELECT statement:
   ```
   SELECT *
   FROM table_name;
   ```

2. Retrieve Specific Columns:
   - Specify the columns you want to retrieve by listing their names after the SELECT keyword:
   ```
   SELECT column1, column2
   FROM table_name;
   ```

II. The WHERE Clause:
The WHERE clause is used to filter data based on specific conditions. It allows us to retrieve only the rows that meet certain criteria. The basic syntax is as follows:
```
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

1. Filtering Rows:
   - Use comparison operators (=, <, >, <=, >=, <>) to compare column values with specific values.
   ```
   SELECT column1, column2
   FROM table_name
   WHERE column_name = value;
   ```

2. Combining Conditions:
   - Use logical operators (AND, OR, NOT) to combine multiple conditions for more complex filtering.
   ```
   SELECT column1, column2
   FROM table_name
   WHERE condition1 AND condition2;
   ```

3. Pattern Matching:
   - The WHERE clause can employ pattern matching with the LIKE operator and wildcard characters (% and _).
   ```
   SELECT column1, column2
   FROM table_name
   WHERE column_name LIKE 'pattern';
   ```

4. NULL Values:
   - Use IS NULL or IS NOT NULL to filter rows with NULL values in a specific column.
   ```
   SELECT column1, column2
   FROM table_name
   WHERE column_name IS NULL;
   ```

Conclusion:
In SQL, the SELECT and WHERE clauses are indispensable tools for filtering and selecting specific data from a database. By using these concepts effectively, you can extract meaningful information and perform complex queries. Understanding how to construct SELECT statements and utilize the WHERE clause empowers you to retrieve precise results tailored to your requirements.


## Aggregating Data:
Aggregating data in SQL involves performing calculations and generating summary information from our database tables. Here are some key concepts and functions that help in aggregating data:

1. COUNT: The COUNT function is used to count the number of rows in a table or the number of occurrences of a particular value in a column. For example, "SELECT COUNT(*) FROM Customers;" will give you the total number of customers in the table.

2. SUM: The SUM function calculates the sum of the values in a column. It is typically used with numerical data types. For instance, "SELECT SUM(Quantity) FROM Orders;" will give you the total quantity of all orders.

3. MAX: The MAX function returns the maximum value from a column. It is commonly used to find the highest value in a set of data. For example, "SELECT MAX(Price) FROM Products;" will give you the highest price among all products.

4. GROUP BY: The GROUP BY clause is used to group rows based on one or more columns. It allows us to aggregate data on a specific attribute or combination of attributes. For instance, "SELECT Department, COUNT(*) FROM Employees GROUP BY Department;" will give you the count of employees in each department.

5. HAVING: The HAVING clause is used in conjunction with the GROUP BY clause to filter the grouped data based on specified conditions. It helps in selecting groups that meet specific criteria. For example, "SELECT Department, COUNT(*) FROM Employees GROUP BY Department HAVING COUNT(*) > 5;" will give you the departments with more than 5 employees.

**Producing Distinct Lists:**
Producing distinct lists allows us to retrieve unique values from a column or set of columns. Here are some concepts that help in producing useful distinct lists:

1. DISTINCT: The DISTINCT keyword is used to eliminate duplicate values from the result set. It ensures that each value appears only once in the output. For example, "SELECT DISTINCT City FROM Customers;" will give you a distinct list of cities where customers are located.

2. COUNT DISTINCT: The COUNT DISTINCT function is used to count the number of unique/distinct values in a column. For instance, "SELECT COUNT(DISTINCT Category) FROM Products;" will give you the count of distinct categories among all products.

Understanding these concepts and functions will empower students to analyze and summarize data effectively. They are valuable tools in extracting meaningful insights from large datasets.

**Joins**
When working with relational databases, it is often necessary to combine data from multiple tables to extract meaningful insights. SQL provides different types of JOIN operations for this purpose, including OUTER JOIN (e.g., LEFT JOIN) and INNER JOIN. Here's an overview of when and where to use them:

INNER JOIN:
An INNER JOIN combines rows from two or more tables based on a related column between them. It returns only the rows that have matching values in both tables. The INNER JOIN focuses on the intersection of the tables, ensuring that only the matched data is included in the result set. Use INNER JOIN when you want to retrieve records that exist in both tables and have a common relationship.

For example, consider two tables: "Customers" and "Orders." To retrieve customer information along with their corresponding orders, you can use the following INNER JOIN query:

```
SELECT Customers.CustomerID, Customers.CustomerName, Orders.OrderID, Orders.OrderDate
FROM Customers
INNER JOIN Orders ON Customers.CustomerID = Orders.CustomerID;
```

This query combines the "Customers" and "Orders" tables based on the matching "CustomerID" column and retrieves the Customer ID, Customer Name, Order ID, and Order Date for all matching records.

OUTER JOIN (e.g., LEFT JOIN):
An OUTER JOIN retrieves all rows from one table and the matching rows from another table. It includes unmatched rows as well, filling the gaps with NULL values in the columns from the table without a match. There are different types of OUTER JOINs, such as LEFT JOIN, RIGHT JOIN, and FULL JOIN. Here, we'll focus on LEFT JOIN.

Use OUTER JOIN, specifically LEFT JOIN, when you want to retrieve all records from the "left" table (the one specified before the LEFT JOIN keyword) and matching records from the "right" table (the one specified after the LEFT JOIN keyword). This is useful when you want to include unmatched records from the left table in the result set.

For example, consider the "Customers" and "Orders" tables again. If you want to retrieve all customers along with their orders (if any), you can use the following LEFT JOIN query:

```
SELECT Customers.CustomerID, Customers.CustomerName, Orders.OrderID, Orders.OrderDate
FROM Customers
LEFT JOIN Orders ON Customers.CustomerID = Orders.CustomerID;
```

This query retrieves all customers from the "Customers" table, including those who have not placed any orders yet. The matching orders are included in the result set, and for the customers without orders, the OrderID and OrderDate columns will contain NULL values.

By understanding the differences between INNER JOIN and OUTER JOIN (specifically LEFT JOIN), you can choose the appropriate type of join based on your data requirements. INNER JOIN focuses on matching records, while OUTER JOIN includes unmatched records from the left table.



