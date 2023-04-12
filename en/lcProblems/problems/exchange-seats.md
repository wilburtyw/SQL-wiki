# 626. Exchange Seats

## Solution 1 Case When

```sql
SELECT (
    CASE 
    WHEN MOD(id, 2) != 0 AND id != counts THEN id+1
    WHEN MOD(id, 2) = 0 AND id != counts THEN id-1
    ELSE id
    END
) as id, s.student
FROM seat as s, (
    SELECT COUNT(*) as counts
    FROM seat
) as c
ORDER BY id
```

## Topic
- [Case When](../../tutorials/syntax.md/#case-expression)