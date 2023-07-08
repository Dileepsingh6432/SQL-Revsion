# SQL-Revision
## A short note for revising the SQL.


{
  "nbformat": 4,
  "nbformat_minor": 0,
  "metadata": {
    "colab": {
      "provenance": [],
      "authorship_tag": "ABX9TyNftW9SWDgOhWa/L2gzZYn9"
    },
    "kernelspec": {
      "name": "python3",
      "display_name": "Python 3"
    },
    "language_info": {
      "name": "python"
    }
  },
  "cells": [
    {
      "cell_type": "markdown",
      "source": [
        "##What is SQL?  \n",
        "SQL stands for Structured Query Language  \n",
        "SQL lets you access and manipulate databases  \n",
        "SQL became a standard of the American National Standards Institute (ANSI) in 1986, and of the International Organization for Standardization (ISO) in 1987\n",
        "\n",
        "##What Can SQL do?\n",
        "SQL can execute queries against a database  \n",
        "SQL can retrieve data from a database  \n",
        "SQL can insert records in a database  \n",
        "SQL can update records in a database  \n",
        "SQL can delete records from a database  \n",
        "SQL can create new databases  \n",
        "SQL can create new tables in a database  \n",
        "SQL can create stored procedures in a database  \n",
        "SQL can create views in a database  \n",
        "SQL can set permissions on tables, procedures, and views  \n",
        "\n",
        "##RDBMS\n",
        "RDBMS stands for Relational Database Management System.\n",
        "\n",
        "RDBMS is the basis for SQL, and for all modern database systems such as MS SQL Server, IBM DB2, Oracle, MySQL, and Microsoft Access.\n",
        "\n",
        "The data in RDBMS is stored in database objects called tables. A table is a collection of related data entries and it consists of columns and rows.\n",
        "\n",
        "Every table is broken up into smaller entities called fields. The fields in the Customers table consist of CustomerID, CustomerName, ContactName, Address, City, PostalCode and Country. A field is a column in a table that is designed to maintain specific information about every record in the table.\n",
        "\n",
        "A record, also called a row, is each individual entry that exists in a table. For example, there are 91 records in the above Customers table. A record is a horizontal entity in a table.\n",
        "\n",
        "A column is a vertical entity in a table that contains all information associated with a specific field in a table.\n",
        "\n",
        "#SQL keywords are NOT case sensitive: select is the same as SELECT\n",
        "\n"
      ],
      "metadata": {
        "id": "dD2rdKd_t6rw"
      }
    },
    {
      "cell_type": "markdown",
      "source": [],
      "metadata": {
        "id": "Z5Ph1ihlt_mh"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "## Some of The Most Important SQL Commands\n",
        "SELECT - extracts data from a database  \n",
        "UPDATE - updates data in a database  \n",
        "DELETE - deletes data from a database  \n",
        "INSERT INTO - inserts new data into a database  \n",
        "CREATE DATABASE - creates a new database  \n",
        "ALTER DATABASE - modifies a database  \n",
        "CREATE TABLE - creates a new table  \n",
        "ALTER TABLE - modifies a table  \n",
        "DROP TABLE - deletes a table  \n",
        "CREATE INDEX - creates an index (search key)  \n",
        "DROP INDEX - deletes an index  "
      ],
      "metadata": {
        "id": "AqbcaHzNthY_"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "###genral syntax for SQL query:  \n",
        "SELECT column1, column2, ...  \n",
        "FROM table_name;  \n",
        "\n",
        "example:  \n",
        "SELECT columname1, columnname2 FROM tablename\n",
        "\n",
        "---\n",
        "###selecting distinct values of a column:  \n",
        "SELECT DISTINCT Country FROM Customers\n",
        "\n",
        "\n",
        "---\n",
        "###Counting the distinct number of country\n",
        "SELECT COUNT(DISTINCT Country) FROM Customers\n",
        "\n",
        "---\n",
        "###WHERE Syntax\n",
        "SELECT column1, column2, ...  \n",
        "FROM table_name  \n",
        "WHERE condition1 AND condition2 AND condition3 ...   \n",
        "\n"
      ],
      "metadata": {
        "id": "Htpd7VlxvR02"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "###condition operators for SQL\n",
        "'='\tEqual\n",
        "'\\>'\tGreater than\n",
        "'<'\tLess than\n",
        "\\'>='\tGreater than or equal\n",
        "'<='\tLess than or equal\n",
        "'<>'\tNot equal. Note: In some versions of SQL this operator may be written as '!='\n",
        "'BETWEEN'\tBetween a certain range\n",
        "'LIKE'\tSearch for a pattern\n",
        "'IN'\tTo specify multiple possible values for a column  "
      ],
      "metadata": {
        "id": "88LQGxB2yWEY"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "#Some examples for various conditions\n",
        "\n",
        "---\n",
        "SELECT * FROM Customers\n",
        "WHERE Country='Mexico'\n",
        "\n",
        "---\n",
        "SELECT * FROM Customers  \n",
        "WHERE Country='Germany' AND City='Berlin'  \n",
        "\n",
        "---\n",
        "SELECT * FROM Customers  \n",
        "WHERE Country='Germany' AND (City='Berlin' OR City='München')  \n"
      ],
      "metadata": {
        "id": "uNWol2pizOs_"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "###Order By\n",
        "\n",
        "SELECT * FROM Customers  \n",
        "ORDER BY Country DESC  \n",
        "\n",
        "---\n",
        "SELECT * FROM Customers  \n",
        "ORDER BY Country ASC  \n",
        "\n",
        "---\n",
        "sorted by the \"Country\" and the \"CustomerName\" column. This means that it orders by Country, but if some rows have the same Country, it orders them by CustomerName\n",
        "\n",
        "SELECT * FROM Customers  \n",
        "ORDER BY Country, CustomerName  "
      ],
      "metadata": {
        "id": "ITRGaZfgzl22"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "###INSERT INTO Statement\n",
        "####Syntax  \n",
        "INSERT INTO table_name (column1, column2, column3, ...)  \n",
        "VALUES (value1, value2, value3, ...)  \n",
        "\n",
        "If you are adding values for all the columns of the table, you do not need to specify the column names in the SQL query.  \n",
        "INSERT INTO table_name  \n",
        "VALUES (value1, value2, value3, ...)  \n",
        "\n",
        "####Example\n",
        "INSERT INTO Customers (CustomerName, City, Country)  \n",
        "VALUES ('Cardinal', 'Stavanger', 'Norway')  \n"
      ],
      "metadata": {
        "id": "Hw_w92Nw0F9u"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "###NULL Values\n",
        "A field with a NULL value is a field with no value.\n",
        "#### Example\n",
        "SELECT CustomerName, ContactName, Address  \n",
        "FROM Customers  \n",
        "WHERE Address IS NULL  \n",
        "\n",
        "\n",
        "####similarly we can use not null"
      ],
      "metadata": {
        "id": "1_0Enos90iCB"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "###UPDATE\n",
        "The UPDATE statement is used to modify the existing records in a table.\n",
        "\n",
        "####Syntax\n",
        "UPDATE table_name  \n",
        "SET column1 = value1, column2 = value2, ...  \n",
        "WHERE condition  \n",
        "\n",
        "####Example\n",
        "UPDATE Customers  \n",
        "SET ContactName = 'Alfred Schmidt', City= 'Frankfurt'  \n",
        "WHERE CustomerID = 1  \n",
        "\n",
        "**Note: Be careful when updating records. If you omit the WHERE clause, ALL records will be updated!**\n"
      ],
      "metadata": {
        "id": "PR7x6Iak03EH"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "###Delete\n",
        "DELETE FROM Customers WHERE CustomerName='Alfreds Futterkiste'\n",
        "\n",
        "**It is possible to delete all rows in a table without deleting the table. This means that the table structure, attributes, and indexes will be intact:**\n",
        "\n",
        "DELETE FROM table_name  \n"
      ],
      "metadata": {
        "id": "Fg7KmCdf5B2z"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "###Limit\n",
        "\n",
        "SELECT column_name(s)  \n",
        "FROM table_name  \n",
        "WHERE condition  \n",
        "LIMIT number  \n",
        "\n",
        "example  \n",
        "SELECT * FROM Customers  \n",
        "LIMIT 3  "
      ],
      "metadata": {
        "id": "iz2Bmprm6ucO"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "###MIN() and Max()\n",
        "SELECT MIN(column_name)  \n",
        "FROM table_name  \n",
        "WHERE condition  \n",
        "\n",
        "SELECT MIN(Price) AS SmallestPrice  \n",
        "FROM Products  \n",
        "\n",
        "SELECT MAX(Price) AS LargestPrice  \n",
        "FROM Products  "
      ],
      "metadata": {
        "id": "qDRZuR0468ai"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "###Count(), SUM(), AVG()\n",
        "\n",
        "SELECT COUNT(ProductID)  \n",
        "FROM Products  \n",
        "\n",
        "---\n",
        "SELECT SUM(Quantity)  \n",
        "FROM OrderDetails  \n",
        "\n",
        "---\n",
        "SELECT AVG(Price)  \n",
        "FROM Products  "
      ],
      "metadata": {
        "id": "sqOR4fHM8IVa"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "###LIKE\n",
        "\n",
        "The LIKE operator is used in a WHERE clause to search for a specified pattern in a column.\n",
        "\n",
        "####Syntax\n",
        "SELECT column1, column2, ...  \n",
        "FROM table_name  \n",
        "WHERE columnN LIKE pattern  \n",
        "\n",
        "**Wildcards**\n",
        "%\tRepresents zero or more characters  \n",
        "_\tRepresents a single character  \n",
        "[]\tRepresents any single character within the brackets\th[oa]t finds hot and hat, but not hit  \n",
        "^\tRepresents any character not in the brackets\th[^oa]t finds hit, but not hot and hat  \n",
        "\\-\tRepresents any single character within the specified range c[a-b]t finds cat and cbt  \n",
        "\n",
        "**Some examples:**  \n",
        "\n",
        "**WHERE CustomerName LIKE 'a%'**\n",
        "Finds any values that start with \"a\"  \n",
        "\n",
        "**WHERE CustomerName LIKE '%a'**\n",
        "Finds any values that end with \"a\"  \n",
        "\n",
        "**WHERE CustomerName LIKE '%or%'**\n",
        "Finds any values that have \"or\" in any position  \n",
        "\n",
        "**WHERE CustomerName LIKE '_r%**  \n",
        "Finds any values that have \"r\" in the second position  \n",
        "\n",
        "**WHERE CustomerName LIKE 'a_%'**  \n",
        "Finds any values that start with \"a\" and are at least 2 characters in length  \n",
        "\n",
        "**WHERE CustomerName LIKE 'a__%'**  \n",
        "Finds any values that start with \"a\" and are at least 3 characters in length  \n",
        "\n",
        "**WHERE ContactName LIKE 'a%o'**\n",
        "Finds any values that start with \"a\" and ends with \"o\"  "
      ],
      "metadata": {
        "id": "m33D3yQS8mZl"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "###In operator\n",
        "The IN operator allows you to specify multiple values in a WHERE clause.\n",
        "####syntax:\n",
        "SELECT column_name(s)  \n",
        "FROM table_name  \n",
        "WHERE column_name IN (value1, value2, ...)  \n",
        "\n",
        "**OR**\n",
        "\n",
        "SELECT column_name(s)  \n",
        "FROM table_name  \n",
        "WHERE column_name IN (SELECT STATEMENT)  \n",
        "\n",
        "**Example:**  \n",
        "SELECT * FROM Customers  \n",
        "WHERE Country IN ('Germany', 'France', 'UK')  \n",
        "\n",
        "SELECT * FROM Customers  \n",
        "WHERE Country NOT IN ('Germany', 'France', 'UK')  \n",
        "\n",
        "SELECT * FROM Customers  \n",
        "WHERE Country IN (SELECT Country FROM Suppliers)  "
      ],
      "metadata": {
        "id": "lvCEV8G6_eMO"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "###BETWEEN\n",
        "\n",
        "The BETWEEN operator selects values within a given range. The values can be numbers, text, or dates.\n",
        "\n",
        "SELECT * FROM Products  \n",
        "WHERE Price BETWEEN 10 AND 20  \n",
        "\n",
        "**in and between**  \n",
        "SELECT * FROM Products  \n",
        "WHERE Price BETWEEN 10 AND 20  \n",
        "AND CategoryID NOT IN (1,2,3)  "
      ],
      "metadata": {
        "id": "0HHDkdy0AHQL"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "###Aliases\n",
        "SQL aliases are used to give a table, or a column in a table, a temporary name.\n",
        "\n",
        "Aliases are often used to make column names more readable.\n",
        "\n",
        "An alias only exists for the duration of that query.\n",
        "\n",
        "An alias is created with the AS keyword.\n",
        "\n",
        "**Example**  \n",
        "SELECT CustomerID AS ID, CustomerName AS Customer  \n",
        "FROM Customers\n",
        "\n",
        "SELECT o.OrderID, o.OrderDate, c.CustomerName  \n",
        "FROM Customers AS c, Orders AS o  \n",
        "WHERE c.CustomerName='Around the Horn' AND c.CustomerID=o.CustomerID  "
      ],
      "metadata": {
        "id": "X97OkFAqAtIk"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "###Joins\n",
        "A JOIN clause is used to combine rows from two or more tables, based on a related column between them.\n",
        "\n",
        "SELECT Orders.OrderID, Customers.CustomerName, Orders.OrderDate  \n",
        "FROM Orders  \n",
        "INNER JOIN Customers ON Orders.CustomerID=Customers.CustomerID  \n",
        "\n",
        "**Different Types of SQL JOINs**\n",
        "\n",
        "* **(INNER) JOIN**: Returns records that have matching values in both tables\n",
        "* **LEFT (OUTER) JOIN**: Returns all records from the left table, and the matched records from the right table\n",
        "* **RIGHT (OUTER) JOIN**: Returns all records from the right table, and the matched records from the left table\n",
        "* **FULL (OUTER) JOIN**: Returns all records when there is a match in either left or right table\n",
        "\n",
        "![image.png](data:image/png;base64,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)"
      ],
      "metadata": {
        "id": "RP7Film_BLzT"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "**Examples for Joins**\n",
        "\n",
        "**Inner Join**  \n",
        "SELECT Orders.OrderID, Customers.CustomerName, Shippers.ShipperName  \n",
        "FROM Orders  \n",
        "INNER JOIN Customers ON Orders.CustomerID = Customers.CustomerID  \n",
        "INNER JOIN Shippers ON Orders.ShipperID = Shippers.ShipperID  \n",
        "\n",
        "\n",
        "**The INNER JOIN keyword selects all rows from both tables as long as there is a match between the columns. If there are records in the \"Orders\" table that do not have matches in \"Customers\", these orders will not be shown!**  \n",
        "\n",
        "**Left Join**\n",
        "SELECT Customers.CustomerName, Orders.OrderID  \n",
        "FROM Customers  \n",
        "LEFT JOIN Orders ON Customers.CustomerID = Orders.CustomerID  \n",
        "ORDER BY Customers.CustomerName  \n",
        "\n",
        "\n",
        "**The LEFT JOIN keyword returns all records from the left table (Customers), even if there are no matches in the right table (Orders).**\n",
        "\n",
        "**Right Join**\n",
        "SELECT Orders.OrderID, Employees.LastName, Employees.FirstName  \n",
        "FROM Orders  \n",
        "RIGHT JOIN Employees ON Orders.EmployeeID = Employees.EmployeeID  \n",
        "ORDER BY Orders.OrderID  \n",
        "\n",
        "**The RIGHT JOIN keyword returns all records from the right table (Employees), even if there are no matches in the left table (Orders).**\n",
        "\n",
        "**Full outter Join**\n",
        "SELECT Customers.CustomerName, Orders.OrderID  \n",
        "FROM Customers  \n",
        "FULL OUTER JOIN Orders ON Customers.CustomerID=Orders.CustomerID  \n",
        "ORDER BY Customers.CustomerName  \n",
        "\n",
        " **The FULL OUTER JOIN keyword returns all matching records from both tables whether the other table matches or not. So, if there are rows in \"Customers\" that do not have matches in \"Orders\", or if there are rows in \"Orders\" that do not have matches in \"Customers\", those rows will be listed as well.**\n",
        "\n",
        " **Self Join**\n",
        "\n",
        " SELECT A.CustomerName AS CustomerName1, B.CustomerName AS CustomerName2, A.City  \n",
        "FROM Customers A, Customers B  \n",
        "WHERE A.CustomerID != B.CustomerID  \n",
        "AND A.City = B.City  \n",
        "ORDER BY A.City  \n",
        "\n",
        "**A self join is a regular join, but the table is joined with itself.**"
      ],
      "metadata": {
        "id": "L6z-NRzeB2gi"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "###Union\n",
        "The UNION operator is used to combine the result-set of two or more SELECT statements.\n",
        "\n",
        "* Every SELECT statement within UNION must have the same number of columns\n",
        "* The columns must also have similar data types\n",
        "* The columns in every SELECT statement must also be in the same order\n",
        "\n",
        "####Syntax\n",
        "SELECT column_name(s) FROM table1  \n",
        "UNION  \n",
        "SELECT column_name(s) FROM table2  \n",
        "\n",
        "###Example\n",
        "SELECT City FROM Customers  \n",
        "UNION  \n",
        "SELECT City FROM Suppliers  \n",
        "ORDER BY City  \n",
        "\n",
        "\n",
        "####UNION ALL\n",
        "**returns the cities (duplicate values also)**\n",
        "###Example\n",
        "SELECT City, Country FROM Customers  \n",
        "WHERE Country='Germany'  \n",
        "UNION ALL  \n",
        "SELECT City, Country FROM Suppliers  \n",
        "WHERE Country='Germany'  \n",
        "ORDER BY City  \n",
        "\n",
        "This SQL statement returns the German cities (duplicate values also) from both the \"Customers\" and the \"Suppliers\" table"
      ],
      "metadata": {
        "id": "-ORiIAv7Uw7i"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "###GROUP BY\n",
        "The GROUP BY statement groups rows that have the same values into summary rows, like \"find the number of customers in each country\".\n",
        "\n",
        "The GROUP BY statement is often used with aggregate functions (COUNT(), MAX(), MIN(), SUM(), AVG()) to group the result-set by one or more columns.\n",
        "\n",
        "####Syntax\n",
        "SELECT column_name(s)  \n",
        "FROM table_name  \n",
        "WHERE condition  \n",
        "GROUP BY column_name(s)  \n",
        "ORDER BY column_name(s)  \n",
        "\n",
        "####Example\n",
        "SELECT COUNT(CustomerID), Country  \n",
        "FROM Customers  \n",
        "GROUP BY Country  \n",
        "ORDER BY COUNT(CustomerID) DESC   \n",
        "\n"
      ],
      "metadata": {
        "id": "SwViv7E3X1Bi"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "###HAVING\n",
        "\n",
        "The HAVING clause was added to SQL because the WHERE keyword cannot be used with aggregate functions.\n",
        "\n",
        "####Syntax\n",
        "SELECT column_name(s)  \n",
        "FROM table_name  \n",
        "WHERE condition  \n",
        "GROUP BY column_name(s)  \n",
        "HAVING condition  \n",
        "ORDER BY column_name(s)  \n",
        "\n",
        "####Example\n",
        "SELECT COUNT(CustomerID), Country  \n",
        "FROM Customers  \n",
        "GROUP BY Country  \n",
        "HAVING COUNT(CustomerID) > 5  \n",
        "ORDER BY COUNT(CustomerID) DESC  "
      ],
      "metadata": {
        "id": "2qx8MQIvZAXs"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "###EXISTS\n",
        "The EXISTS operator is used to test for the existence of any record in a subquery.  \n",
        "The EXISTS operator returns TRUE if the subquery returns one or more records.\n",
        "\n",
        "####Syntax\n",
        "SELECT column_name(s)  \n",
        "FROM table_name  \n",
        "WHERE EXISTS  \n",
        "(SELECT column_name FROM table_name WHERE condition)  \n",
        "\n",
        "####Example\n",
        "SELECT SupplierName  \n",
        "FROM Suppliers  \n",
        "WHERE EXISTS (SELECT ProductName FROM Products WHERE Products.SupplierID = Suppliers.supplierID AND Price = 22)\n"
      ],
      "metadata": {
        "id": "XBDD1KSAZYOr"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "###ANY and ALL\n",
        "The ANY and ALL operators allow you to perform a comparison between a single column value and a range of other values.\n",
        "\n",
        "####Any\n",
        "The ANY operator:\n",
        "\n",
        "* returns a boolean value as a result\n",
        "* returns TRUE if ANY of the subquery values meet the condition  \n",
        "\n",
        "ANY means that the condition will be true if the operation is true for any of the values in the range.\n",
        "\n",
        "####Syntax\n",
        "SELECT column_name(s)  \n",
        "FROM table_name  \n",
        "WHERE column_name operator ANY  \n",
        "  (SELECT column_name  \n",
        "  FROM table_name  \n",
        "  WHERE condition)  \n",
        "\n",
        "####Example\n",
        "SELECT ProductName  \n",
        "FROM Products  \n",
        "WHERE ProductID = ANY  \n",
        "  (SELECT ProductID  \n",
        "  FROM OrderDetails  \n",
        "  WHERE Quantity = 10)  \n",
        "\n",
        "---\n",
        "####ALL\n",
        "The ALL operator:\n",
        "* returns a boolean value as a result\n",
        "* returns TRUE if ALL of the subquery values meet the condition\n",
        "is used with SELECT, WHERE and HAVING statements\n",
        "\n",
        "\n",
        "ALL means that the condition will be true only if the operation is true for all values in the range.\n",
        "\n",
        "####Syntax\n",
        "SELECT column_name(s)  \n",
        "FROM table_name  \n",
        "WHERE column_name operator ALL  \n",
        "  (SELECT column_name  \n",
        "  FROM table_name  \n",
        "  WHERE condition)  \n",
        "\n",
        "####Example\n",
        "SELECT ProductName  \n",
        "FROM Products  \n",
        "WHERE ProductID = ALL  \n",
        "  (SELECT ProductID  \n",
        "  FROM OrderDetails  \n",
        "  WHERE Quantity = 10)  "
      ],
      "metadata": {
        "id": "8zbBXE9NZ_bu"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "###SELECT INTO\n",
        "The SELECT INTO statement copies data from one table into a new table.\n",
        "\n",
        "####Example\n",
        "SELECT * INTO CustomersGermany  \n",
        "FROM Customers  \n",
        "WHERE Country = 'Germany'  \n",
        "\n",
        "SELECT CustomerName, ContactName INTO CustomersBackup2017  \n",
        "FROM Customers  \n",
        "\n"
      ],
      "metadata": {
        "id": "aEfMwSIcbEJf"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "###INSERT INTO SELECT\n",
        "The INSERT INTO SELECT statement copies data from one table and inserts it into another table.\n",
        "\n",
        "The INSERT INTO SELECT statement requires that the data types in source and target tables match.\n",
        "\n",
        "####Example\n",
        "INSERT INTO Customers (CustomerName, City, Country)  \n",
        "SELECT SupplierName, City, Country FROM Suppliers  "
      ],
      "metadata": {
        "id": "IC8GK62LbkEN"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "###CASE\n",
        "The CASE expression goes through conditions and returns a value when the first condition is met (like an if-then-else statement). So, once a condition is true, it will stop reading and return the result. If no conditions are true, it returns the value in the ELSE clause.\n",
        "\n",
        "If there is no ELSE part and no conditions are true, it returns NULL.\n",
        "\n",
        "####Syntax\n",
        "CASE  \n",
        "    WHEN condition1 THEN result1  \n",
        "    WHEN condition2 THEN result2  \n",
        "    WHEN conditionN THEN resultN  \n",
        "    ELSE result  \n",
        "END  \n",
        "\n",
        "####Example\n",
        "SELECT OrderID, Quantity,  \n",
        "CASE  \n",
        "    WHEN Quantity > 30 THEN 'The quantity is greater than 30'  \n",
        "    WHEN Quantity = 30 THEN 'The quantity is 30'  \n",
        "    ELSE 'The quantity is under 30'  \n",
        "END AS QuantityText  \n",
        "FROM OrderDetails  "
      ],
      "metadata": {
        "id": "H9NMyT8-bycr"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "###NULL\n",
        "**The MySQL IFNULL() function lets you return an alternative value if an expression is NULL**\n",
        "###Example\n",
        "SELECT ProductName, UnitPrice * (UnitsInStock + IFNULL(UnitsOnOrder, 0))  \n",
        "FROM Products  \n",
        "\n",
        "**we can use the COALESCE() function, like this**  \n",
        "SELECT ProductName, UnitPrice * (UnitsInStock + COALESCE(UnitsOnOrder, 0))  \n",
        "FROM Products  \n",
        "\n",
        "**The SQL Server ISNULL() function lets you return an alternative value when an expression is NULL**  \n",
        "SELECT ProductName, UnitPrice * (UnitsInStock + ISNULL(UnitsOnOrder, 0))  \n",
        "FROM Products  "
      ],
      "metadata": {
        "id": "j0cYV1E4cNTd"
      }
    },
    {
      "cell_type": "markdown",
      "source": [],
      "metadata": {
        "id": "R0IwmspLc6j2"
      }
    },
    {
      "cell_type": "markdown",
      "source": [],
      "metadata": {
        "id": "_N7moyI0x2nd"
      }
    }
  ]
}
