# SQL-Revision
## A short note for revising the SQL.

What is SQL?
SQL stands for Structured Query Language
SQL lets you access and manipulate databases
SQL became a standard of the American National Standards Institute (ANSI) in 1986, and of the International Organization for Standardization (ISO) in 1987

What Can SQL do?
SQL can execute queries against a database
SQL can retrieve data from a database
SQL can insert records in a database
SQL can update records in a database
SQL can delete records from a database
SQL can create new databases
SQL can create new tables in a database
SQL can create stored procedures in a database
SQL can create views in a database
SQL can set permissions on tables, procedures, and views

RDBMS
RDBMS stands for Relational Database Management System.

RDBMS is the basis for SQL, and for all modern database systems such as MS SQL Server, IBM DB2, Oracle, MySQL, and Microsoft Access.

The data in RDBMS is stored in database objects called tables. A table is a collection of related data entries and it consists of columns and rows.

Every table is broken up into smaller entities called fields. The fields in the Customers table consist of CustomerID, CustomerName, ContactName, Address, City, PostalCode and Country. A field is a column in a table that is designed to maintain specific information about every record in the table.

A record, also called a row, is each individual entry that exists in a table. For example, there are 91 records in the above Customers table. A record is a horizontal entity in a table.

A column is a vertical entity in a table that contains all information associated with a specific field in a table.

SQL keywords are NOT case sensitive: select is the same as SELECT
Some of The Most Important SQL Commands
SELECT - extracts data from a database
UPDATE - updates data in a database
DELETE - deletes data from a database
INSERT INTO - inserts new data into a database
CREATE DATABASE - creates a new database
ALTER DATABASE - modifies a database
CREATE TABLE - creates a new table
ALTER TABLE - modifies a table
DROP TABLE - deletes a table
CREATE INDEX - creates an index (search key)
DROP INDEX - deletes an index

genral syntax for SQL query:
SELECT column1, column2, ...
FROM table_name;

example:
SELECT columname1, columnname2 FROM tablename

selecting distinct values of a column:
SELECT DISTINCT Country FROM Customers

Counting the distinct number of country
SELECT COUNT(DISTINCT Country) FROM Customers

WHERE Syntax
SELECT column1, column2, ...
FROM table_name
WHERE condition1 AND condition2 AND condition3 ...

condition operators for SQL
'=' Equal '>' Greater than '<' Less than '>=' Greater than or equal '<=' Less than or equal '<>' Not equal. Note: In some versions of SQL this operator may be written as '!=' 'BETWEEN' Between a certain range 'LIKE' Search for a pattern 'IN' To specify multiple possible values for a column

Some examples for various conditions
SELECT * FROM Customers WHERE Country='Mexico'

SELECT * FROM Customers
WHERE Country='Germany' AND City='Berlin'

SELECT * FROM Customers
WHERE Country='Germany' AND (City='Berlin' OR City='München')

Order By
SELECT * FROM Customers
ORDER BY Country DESC

SELECT * FROM Customers
ORDER BY Country ASC

sorted by the "Country" and the "CustomerName" column. This means that it orders by Country, but if some rows have the same Country, it orders them by CustomerName

SELECT * FROM Customers
ORDER BY Country, CustomerName

INSERT INTO Statement
Syntax
INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...)

If you are adding values for all the columns of the table, you do not need to specify the column names in the SQL query.
INSERT INTO table_name
VALUES (value1, value2, value3, ...)

Example
INSERT INTO Customers (CustomerName, City, Country)
VALUES ('Cardinal', 'Stavanger', 'Norway')

NULL Values
A field with a NULL value is a field with no value.

Example
SELECT CustomerName, ContactName, Address
FROM Customers
WHERE Address IS NULL

similarly we can use not null
UPDATE
The UPDATE statement is used to modify the existing records in a table.

Syntax
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition

Example
UPDATE Customers
SET ContactName = 'Alfred Schmidt', City= 'Frankfurt'
WHERE CustomerID = 1

Note: Be careful when updating records. If you omit the WHERE clause, ALL records will be updated!

Delete
DELETE FROM Customers WHERE CustomerName='Alfreds Futterkiste'

It is possible to delete all rows in a table without deleting the table. This means that the table structure, attributes, and indexes will be intact:

DELETE FROM table_name

Limit
SELECT column_name(s)
FROM table_name
WHERE condition
LIMIT number

example
SELECT * FROM Customers
LIMIT 3

MIN() and Max()
SELECT MIN(column_name)
FROM table_name
WHERE condition

SELECT MIN(Price) AS SmallestPrice
FROM Products

SELECT MAX(Price) AS LargestPrice
FROM Products

Count(), SUM(), AVG()
SELECT COUNT(ProductID)
FROM Products

SELECT SUM(Quantity)
FROM OrderDetails

SELECT AVG(Price)
FROM Products

LIKE
The LIKE operator is used in a WHERE clause to search for a specified pattern in a column.

Syntax
SELECT column1, column2, ...
FROM table_name
WHERE columnN LIKE pattern

Wildcards % Represents zero or more characters
_ Represents a single character
[] Represents any single character within the brackets h[oa]t finds hot and hat, but not hit
^ Represents any character not in the brackets h[^oa]t finds hit, but not hot and hat
- Represents any single character within the specified range c[a-b]t finds cat and cbt

Some examples:

WHERE CustomerName LIKE 'a%' Finds any values that start with "a"

WHERE CustomerName LIKE '%a' Finds any values that end with "a"

WHERE CustomerName LIKE '%or%' Finds any values that have "or" in any position

WHERE CustomerName LIKE '_r%
Finds any values that have "r" in the second position

WHERE CustomerName LIKE 'a_%'
Finds any values that start with "a" and are at least 2 characters in length

WHERE CustomerName LIKE 'a__%'
Finds any values that start with "a" and are at least 3 characters in length

WHERE ContactName LIKE 'a%o' Finds any values that start with "a" and ends with "o"

In operator
The IN operator allows you to specify multiple values in a WHERE clause.

syntax:
SELECT column_name(s)
FROM table_name
WHERE column_name IN (value1, value2, ...)

OR

SELECT column_name(s)
FROM table_name
WHERE column_name IN (SELECT STATEMENT)

Example:
SELECT * FROM Customers
WHERE Country IN ('Germany', 'France', 'UK')

SELECT * FROM Customers
WHERE Country NOT IN ('Germany', 'France', 'UK')

SELECT * FROM Customers
WHERE Country IN (SELECT Country FROM Suppliers)

BETWEEN
The BETWEEN operator selects values within a given range. The values can be numbers, text, or dates.

SELECT * FROM Products
WHERE Price BETWEEN 10 AND 20

in and between
SELECT * FROM Products
WHERE Price BETWEEN 10 AND 20
AND CategoryID NOT IN (1,2,3)

Aliases
SQL aliases are used to give a table, or a column in a table, a temporary name.

Aliases are often used to make column names more readable.

An alias only exists for the duration of that query.

An alias is created with the AS keyword.

Example
SELECT CustomerID AS ID, CustomerName AS Customer
FROM Customers

SELECT o.OrderID, o.OrderDate, c.CustomerName
FROM Customers AS c, Orders AS o
WHERE c.CustomerName='Around the Horn' AND c.CustomerID=o.CustomerID

Joins
A JOIN clause is used to combine rows from two or more tables, based on a related column between them.

SELECT Orders.OrderID, Customers.CustomerName, Orders.OrderDate
FROM Orders
INNER JOIN Customers ON Orders.CustomerID=Customers.CustomerID

Different Types of SQL JOINs

(INNER) JOIN: Returns records that have matching values in both tables
LEFT (OUTER) JOIN: Returns all records from the left table, and the matched records from the right table
RIGHT (OUTER) JOIN: Returns all records from the right table, and the matched records from the left table
FULL (OUTER) JOIN: Returns all records when there is a match in either left or right table
image.png

Examples for Joins

Inner Join
SELECT Orders.OrderID, Customers.CustomerName, Shippers.ShipperName
FROM Orders
INNER JOIN Customers ON Orders.CustomerID = Customers.CustomerID
INNER JOIN Shippers ON Orders.ShipperID = Shippers.ShipperID

The INNER JOIN keyword selects all rows from both tables as long as there is a match between the columns. If there are records in the "Orders" table that do not have matches in "Customers", these orders will not be shown!

Left Join SELECT Customers.CustomerName, Orders.OrderID
FROM Customers
LEFT JOIN Orders ON Customers.CustomerID = Orders.CustomerID
ORDER BY Customers.CustomerName

The LEFT JOIN keyword returns all records from the left table (Customers), even if there are no matches in the right table (Orders).

Right Join SELECT Orders.OrderID, Employees.LastName, Employees.FirstName
FROM Orders
RIGHT JOIN Employees ON Orders.EmployeeID = Employees.EmployeeID
ORDER BY Orders.OrderID

The RIGHT JOIN keyword returns all records from the right table (Employees), even if there are no matches in the left table (Orders).

Full outter Join SELECT Customers.CustomerName, Orders.OrderID
FROM Customers
FULL OUTER JOIN Orders ON Customers.CustomerID=Orders.CustomerID
ORDER BY Customers.CustomerName

The FULL OUTER JOIN keyword returns all matching records from both tables whether the other table matches or not. So, if there are rows in "Customers" that do not have matches in "Orders", or if there are rows in "Orders" that do not have matches in "Customers", those rows will be listed as well.

Self Join

SELECT A.CustomerName AS CustomerName1, B.CustomerName AS CustomerName2, A.City
FROM Customers A, Customers B
WHERE A.CustomerID != B.CustomerID
AND A.City = B.City
ORDER BY A.City

A self join is a regular join, but the table is joined with itself.

Union
The UNION operator is used to combine the result-set of two or more SELECT statements.

Every SELECT statement within UNION must have the same number of columns
The columns must also have similar data types
The columns in every SELECT statement must also be in the same order
Syntax
SELECT column_name(s) FROM table1
UNION
SELECT column_name(s) FROM table2

Example
SELECT City FROM Customers
UNION
SELECT City FROM Suppliers
ORDER BY City

UNION ALL
returns the cities (duplicate values also)

Example
SELECT City, Country FROM Customers
WHERE Country='Germany'
UNION ALL
SELECT City, Country FROM Suppliers
WHERE Country='Germany'
ORDER BY City

This SQL statement returns the German cities (duplicate values also) from both the "Customers" and the "Suppliers" table

GROUP BY
The GROUP BY statement groups rows that have the same values into summary rows, like "find the number of customers in each country".

The GROUP BY statement is often used with aggregate functions (COUNT(), MAX(), MIN(), SUM(), AVG()) to group the result-set by one or more columns.

Syntax
SELECT column_name(s)
FROM table_name
WHERE condition
GROUP BY column_name(s)
ORDER BY column_name(s)

Example
SELECT COUNT(CustomerID), Country
FROM Customers
GROUP BY Country
ORDER BY COUNT(CustomerID) DESC

HAVING
The HAVING clause was added to SQL because the WHERE keyword cannot be used with aggregate functions.

Syntax
SELECT column_name(s)
FROM table_name
WHERE condition
GROUP BY column_name(s)
HAVING condition
ORDER BY column_name(s)

Example
SELECT COUNT(CustomerID), Country
FROM Customers
GROUP BY Country
HAVING COUNT(CustomerID) > 5
ORDER BY COUNT(CustomerID) DESC

EXISTS
The EXISTS operator is used to test for the existence of any record in a subquery.
The EXISTS operator returns TRUE if the subquery returns one or more records.

Syntax
SELECT column_name(s)
FROM table_name
WHERE EXISTS
(SELECT column_name FROM table_name WHERE condition)

Example
SELECT SupplierName
FROM Suppliers
WHERE EXISTS (SELECT ProductName FROM Products WHERE Products.SupplierID = Suppliers.supplierID AND Price = 22)

ANY and ALL
The ANY and ALL operators allow you to perform a comparison between a single column value and a range of other values.

Any
The ANY operator:

returns a boolean value as a result
returns TRUE if ANY of the subquery values meet the condition
ANY means that the condition will be true if the operation is true for any of the values in the range.

Syntax
SELECT column_name(s)
FROM table_name
WHERE column_name operator ANY
(SELECT column_name
FROM table_name
WHERE condition)

Example
SELECT ProductName
FROM Products
WHERE ProductID = ANY
(SELECT ProductID
FROM OrderDetails
WHERE Quantity = 10)

ALL
The ALL operator:

returns a boolean value as a result
returns TRUE if ALL of the subquery values meet the condition
is used with SELECT, WHERE and HAVING statements

ALL means that the condition will be true only if the operation is true for all values in the range.

Syntax
SELECT column_name(s)
FROM table_name
WHERE column_name operator ALL
(SELECT column_name
FROM table_name
WHERE condition)

Example
SELECT ProductName
FROM Products
WHERE ProductID = ALL
(SELECT ProductID
FROM OrderDetails
WHERE Quantity = 10)

SELECT INTO
The SELECT INTO statement copies data from one table into a new table.

Example
SELECT * INTO CustomersGermany
FROM Customers
WHERE Country = 'Germany'

SELECT CustomerName, ContactName INTO CustomersBackup2017
FROM Customers

INSERT INTO SELECT
The INSERT INTO SELECT statement copies data from one table and inserts it into another table.

The INSERT INTO SELECT statement requires that the data types in source and target tables match.

Example
INSERT INTO Customers (CustomerName, City, Country)
SELECT SupplierName, City, Country FROM Suppliers

CASE
The CASE expression goes through conditions and returns a value when the first condition is met (like an if-then-else statement). So, once a condition is true, it will stop reading and return the result. If no conditions are true, it returns the value in the ELSE clause.

If there is no ELSE part and no conditions are true, it returns NULL.

Syntax
CASE
WHEN condition1 THEN result1
WHEN condition2 THEN result2
WHEN conditionN THEN resultN
ELSE result
END

Example
SELECT OrderID, Quantity,
CASE
WHEN Quantity > 30 THEN 'The quantity is greater than 30'
WHEN Quantity = 30 THEN 'The quantity is 30'
ELSE 'The quantity is under 30'
END AS QuantityText
FROM OrderDetails

NULL
The MySQL IFNULL() function lets you return an alternative value if an expression is NULL

Example
SELECT ProductName, UnitPrice * (UnitsInStock + IFNULL(UnitsOnOrder, 0))
FROM Products

we can use the COALESCE() function, like this
SELECT ProductName, UnitPrice * (UnitsInStock + COALESCE(UnitsOnOrder, 0))
FROM Products

The SQL Server ISNULL() function lets you return an alternative value when an expression is NULL
SELECT ProductName, UnitPrice * (UnitsInStock + ISNULL(UnitsOnOrder, 0))
FROM Products

