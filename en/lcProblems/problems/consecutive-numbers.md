# 180. Consecutive Numbers

## Solution 1 INNER JOIN

```sql
SELECT DISTINCT l1.num AS ConsecutiveNums
FROM logs AS l1, logs AS l2, logs AS l3
WHERE l1.num = l2.num
AND l2.num = l3.num
AND l1.id - l2.id = 1
AND l2.id - l3.id = 1
```

## Solution 2 LEAD() & LAG() Functions

```sql
SELECT distinct a.num as ConsecutiveNums
FROM (
  SELECT id, num, LEAD(num, 1) OVER () as next, LEAD(num, 2) OVER () as next2
  FROM logs
) as a
WHERE a.num = a.next AND a.num = a.next2
```


## Topic
- [WHERE](../../tutorials/syntax.md/#where-clause)
- [AND](../../tutorials/syntax.md/#and--or-clause)
- [INNER JOIN](../../tutorials/syntax.md/#self-join)
- [LEAD() & LAG()](../../tutorials/syntax.md/)