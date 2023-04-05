# SQL Basic Schema

SQL (Structured Query Language) is a language used for interacting with relational database management systems (RDBMS). It is used to query and manipulate data within the database. Some of the main uses of SQL include:

- Defining the structure of the database by creating tables, indexes, views, and other database objects.
- Manipulating data in tables by inserting, updating, and deleting rows.
- Querying data from one or more tables using a variety of SQL commands. This includes filtering rows, sorting results, using joins, and more.
- Controlling access to the database by creating and managing users, roles, and permissions.
- Ensuring data integrity through constraints, checks, foreign keys, and other database features.
- Backing up and restoring databases to protect against data loss.
And more...

While the syntax of SQL varies slightly between database vendors (MySQL, Oracle, SQL Server, etc.), the core commands remain largely the same.

- [SQL Basic Schema](#sql-basic-schema)
  - [SQL SELECT Statement](#sql-select-statement)

## SQL SELECT Statement

The **SELECT** statement retrieves data from one or more tables in a database and returns it as a result set. The result set is a collection of rows and columns that match the specified criteria in the SELECT statement.

The basic syntax of the SELECT statement is as follows:

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