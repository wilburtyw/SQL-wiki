# 180. Consecutive Numbers

## Solution 1 Case When, SUM() and GROUP BY

```sql
SELECT stock_name, sum((
    CASE
    WHEN operation = 'Buy' THEN price * -1
    ELSE price
    END
)) AS capital_gain_loss
FROM stocks AS capitals
GROUP BY stock_name
ORDER BY capital_gain_loss DESC
```

## Topic
- [Case When](../../tutorials/syntax.md/#case-expression)
- [Group By](../../tutorials/syntax.md/#group-by-statement)
- [Order By](../../tutorials/syntax.md/#order-by-clause)