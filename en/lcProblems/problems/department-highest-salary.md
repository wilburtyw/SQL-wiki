# 184. Department Highest Salary

## Solution 1 CTE & RANK() Window Function

```sql
with ranktable as (
  SELECT name AS employee, salary, departmentid AS id, rank() OVER (PARTITION BY departmentid ORDER BY salary DESC) AS 'rank'
  FROM employee
)

SELECT d.name AS department, r.employee, r.salary
FROM ranktable as r
LEFT JOIN department as d
ON d.id = r.id
WHERE r.rank = 1
```

## Solution 2 CTE & MAX()

```sql
SELECT d.name as department, e.name as employee, e.salary
FROM employee as e
LEFT JOIN department as d
ON d.id = e.departmentid
WHERE (e.salary, e.departmentid) in (
    SELECT MAX(salary) AS 'max', departmentid as id
    FROM employee
    GROUP BY departmentid
)
```

## Topic
- [CTE](../../tutorials/syntax.md/#where-clause)
- [MAX()](../../tutorials/syntax.md/#min--max-functions)
- [RANK()](../../tutorials/syntax.md/#rank--dense_rank-function)