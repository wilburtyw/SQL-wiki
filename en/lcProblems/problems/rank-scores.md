# 178. Ranked Score

## Solution 1 DENSE_RANK() Window Function

```sql
SELECT score, DENSE_RANK() OVER (ORDER BY score DESC) as 'rank'
FROM scores
```

## Solution 2 Correlated Subquery

```sql
SELECT s1.score, (
  SELECT COUNT(DISTINCT s2.score)
  FROM scores as s2
  WHERE s2.score >= s1.score
) as 'rank'
FROM scores as s1
ORDER BY s1.score DESC;
```

## Solution 3 INNER JOIN

```sql
SELECT s1.score, COUNT(DISTINCT s2.score) AS 'rank'
FROM scores as s1
INNER JOIN scores as s2
ON s1.score <= s2.score
GROUP BY s1.id, s1.score
ORDER BY s1.score DESC;
```

## Topic

- [RANK()](../../tutorials/syntax.md/#rank-function)
- [Correlated Subquery](../../tutorials/syntax.md/#correlated-subquery)
- [INNER JOIN](../../tutorials/syntax.md/#join)