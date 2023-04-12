# 608. Tree Node

## Solution 1 Union

```sql
SELECT id, 'Root' AS type
FROM tree
WHERE p_id IS NULL

UNION

SELECT id, 'Inner' as type
FROM tree
WHERE id IN (
    SELECT DISTINCT p_id
    FROM tree
    WHERE p_id IS NOT NULL
) AND p_id IS NOT NULL

UNION

SELECT id, 'Leaf' AS type
FROM tree
WHERE id NOT IN (
    SELECT DISTINCT p_id
    FROM tree
    WHERE p_id IS NOT NULL
) AND p_id IS NOT NULL
```

## Solution 2 Case When

```sql
SELECT id, (
    CASE
    WHEN id IN (
        SELECT DISTINCT p_id
        FROM tree
        WHERE p_id IS NOT NULL
    ) AND p_id IS NOT NULL THEN 'Inner'
    WHEN p_id IS NULL THEN 'Root'
    ELSE 'Leaf'
    END
) as type
FROM tree
```

## Solution 3 IF() Function

```sql
SELECT id, IF(
    ISNULL(p_id), 'Root', IF(
        id IN (SELECT p_id FROM tree), 'Inner', 'Leaf'
    )
) as type
FROM tree
ORDER BY id
```

## Topic
- [UNION](../../tutorials/syntax.md/#union-operator)
- [CASE WHEN](../../tutorials/syntax.md/#case-expression)
- [IF()](../../tutorials/syntax.md/#if-function)