# 595. Big Countries

[Easy](../problemList/easy.md)

## Description
Given a table 'World' with columns name, continent, area, population, and gdp. Write an SQL query to report the name, population, and area of the big countries. A country is considered big if it has an area of at least three million square kilometers or a population of at least twenty-five million.

Return the result table in any order.

## Solution
```SQL
SELECT name, population, area
FROM World
WHERE area >= 3000000 OR population >= 25000000;
```

## Topic
- [SELECT](../../tutorials/syntax.md/#sql-select-statement)
- [WHERE](../../tutorials/syntax.md/#WHERE)
- [OR](../../tutorials/syntax.md/#OR)