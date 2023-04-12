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

## SELECT Statement

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

## WHERE Clause

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

## AND & OR Clause

You can combine multiple conditions in a WHERE clause using the following logical operators:

- `AND`: True if both conditions are true
- `OR`: True if either condition is true
- `NOT`: Negates the condition that follows it

By using the WHERE clause with different operators and logical conditions, we can filter out the desired results from large datasets in SQL.

## Order By Clause

## MIN() & MAX() Functions

## Group By Statement

## Case Expression

**Basic Syntax**

```sql
CASE expression
WHEN when_expression_1 THEN result_1
WHEN when_expression_2 THEN result_2
WHEN when_expression_3 THEN result_3
...
ELSE
	else_result
END
```

## Union Operator

The `UNION` operator is used to combine the result-set of two or more `SELECT` statements.

- Every `SELECT` statement within `UNION` must have the same number of columns
- The columns must also have similar data types
- The columns in every `SELECT` statement must also be in the same order

The `UNION` operator selects only distinct values by default. To allow duplicate values, use `UNION ALL`:


# Window Function

**Basic Syntax**

```sql
window_function_name ( expression ) OVER (
    partition_clause
    order_clause
    frame_clause
)
```

## RANK() & DENSE_RANK() Function

`RANK()` function is a window function that assigns a rank to each row in the partition of a result set. The rank of a row is determined by one plus the number of ranks that come before it.

Different from the `RANK()` function, the `DENSE_RANK()` function always generates consecutive rank values.

**Basic Syntax**

```sql
RANK() OVER (
	PARTITION BY expr1, expr2, ...
	ORDER BY expr1 [ASC | DESC], expr2, ...
)

DENSE_RANK() OVER (
	PARTITION BY expr1, expr2, ...
	ORDER BY expr1 [ASC | DESC], expr2, ...
)
```

The `PARTITION BY` clause distributes the rows in the result set into partitions by one or more criteria.

The `ORDER BY` clause sorts the rows in each a partition.

The `RANK()` and `DENSE_RANK()` function is operated on the rows of each partition and re-initialized when crossing each partition boundary.

## LEAD() Function

`LEAD()` function is a window function that provides access to a row at a specified physical offset which **follows** the current row.

`LAG()` function is a window function that provides access to a row at a specified physical offset which comes **before** the current row.

**Basic Syntax**

```sql
LEAD(return_value, offset, default) OVER (
    PARTITION BY expr1, expr2,...
	ORDER BY expr1 [ASC | DESC], expr2, ...
)

LAG(return_value, offset, default) OVER (
    PARTITION BY expr1, expr2,...
	ORDER BY expr1 [ASC | DESC], expr2, ...
)
```

`return_value`: The return value based on the specified offset. It can be a column of the row at a given offset from the current row.

`offset`: The number of rows forwards(backs) from the current row from which to access data. The offset must be a non-negative integer. If you don’t specify offset, it defaults to 1.

`default`: The function returns default if the offset goes beyond the scope of the partition. If you do not specify default, NULL is returned.

The `PARTITION BY` clause divides rows of the result set into partitions to which the `LEAD()` or `LAG()` function applies. If you do not specify the `PARTITION BY` clause, the whole result set is treated as a single partition.

The `ORDER BY` clause sorts the rows in each partition to which the the `LEAD()` or `LAG()` function applies.

# Common Table Expression

A SQL Common Table Expression (CTE) is a temporary named result set that you can reference within a SELECT, INSERT, UPDATE, or DELETE statement. A CTE is defined within a WITH clause and is similar to a derived table or subquery.

**Basic Syntax**

```sql
WITH Table_Name AS (
    <query>
)
```

# Correlated Subquery

A correlated subquery is a type of subquery that depends on the values from the outer query for its execution. It is called "correlated" because the inner query (subquery) is related to or correlated with the outer query. The correlated subquery is executed once for each row in the outer query, and the result of the inner query can be different for each row of the outer query.

In a correlated subquery, you usually reference one or more columns from the outer query within the subquery. This creates a relationship between the inner and outer queries, as the subquery relies on data from the outer query to produce its results.

# JOIN

A `JOIN` clause is used to combine rows from two or more tables, based on a related column between them.

- `(INNER) JOIN`: Returns records that have matching values in both tables
- `LEFT (OUTER) JOIN`: Returns all records from the left table, and the matched records from the right table
- `RIGHT (OUTER) JOIN`: Returns all records from the right table, and the matched records from the left table
- `FULL (OUTER) JOIN`: Returns all records when there is a match in either left or right table

# MySQL Function

## IF() Function

The IF() function returns a value if a condition is TRUE, or another value if a condition is FALSE.

**Basic Syntax**

```sql
IF(condition, value_if_true, value_if_false)
```

