# SQL Basic Syntax

SQL (Structured Query Language) is a language used for interacting with relational database management systems (RDBMS). It is used to query and manipulate data within the database. Some of the main uses of SQL include:

- Defining the structure of the database by creating tables, indexes, views, and other database objects.
- Manipulating data in tables by inserting, updating, and deleting rows.
- Querying data from one or more tables using a variety of SQL commands. This includes filtering rows, sorting results, using joins, and more.
- Controlling access to the database by creating and managing users, roles, and permissions.
- Ensuring data integrity through constraints, checks, foreign keys, and other database features.
- Backing up and restoring databases to protect against data loss.
And more...

While the syntax of SQL varies slightly between database vendors (MySQL, Oracle, SQL Server, etc.), the core commands remain largely the same.

## SQL SELECT Statement

The **SELECT** statement retrieves data from one or more tables in a database and returns it as a result set. The result set is a collection of rows and columns that match the specified criteria in the SELECT statement.

**Basic Syntax**

```sql
SELECT column1, column2, ...
FROM table_name;
```
Here, `column1`, `column2`, ... are the names of the columns you want to retrieve data from, and `table_name` is the name of the table from which you want to retrieve data. You can retrieve data from one or more tables by specifying multiple table names in the FROM clause, separated by commas.

You can also use the * wildcard character to select all columns from a table:

```sql
SELECT *
FROM table_name;
```

Overall, the SELECT statement is the **foundation** of SQL and is essential for querying data from a database.

## SQL WHERE Clause

The WHERE clause is an essential part of the SELECT statement used to filter records based on specific conditions. It allows us to extract only those records that satisfy the given condition(s) and exclude all other records from the result set.

**Basic Syntax**

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```
Here, `table_name` is the name of the table from which you want to retrieve data, and `condition` is the filter expression used to extract only the matching records.

**Operators**

The WHERE clause can use the following operators to build complex conditions:

- `=`: Equal to
- `<>` or `!=`: Not equal to
- `<`: Less than
- `>`: Greater than
- `<=`: Less than or equal to
- `>=`: Greater than or equal to
- `BETWEEN`: Between an inclusive range of values
- `LIKE`: Search for a pattern in a column
- `IN`: Match any of a set of values
- `NOT`: Negates a condition

**Combining Conditions**

You can combine multiple conditions in a WHERE clause using the following logical operators:

- `AND`: True if both conditions are true
- `OR`: True if either condition is true
- `NOT`: Negates the condition that follows it

By using the WHERE clause with different operators and logical conditions, we can filter out the desired results from large datasets in SQL.