# Querying

## `WHERE` Condition

```sql
-- Comparison
SELECT * FROM [person] WHERE [name] <> 'John';
SELECT * FROM [person] WHERE [age] > 18;

-- `NULL` Check
SELECT * FROM [person] WHERE [last_name] IS NULL;

-- `OR`, `AND` & `NOT`
SELECT * FROM [person] WHERE [name] = 'John' OR [name] = 'Jane';
SELECT * FROM [person] WHERE [name] = 'John' AND [last_name] = 'Doe';
SELECT * FROM [person] WHERE NOT [name] = 'John';

-- `LIKE` Pattern
SELECT * FROM [person] WHERE [name] LIKE 'J%';     -- %: any string
SELECT * FROM [person] WHERE [name] LIKE 'J_n_';   -- _: any character
SELECT * FROM [person] WHERE [name] LIKE 'J[ae]n'; -- []: any character in the set

-- `IN` & `NOT IN`
SELECT * FROM [person] WHERE [name] IN ('John', 'Jane');

-- `BETWEEN AND`
SELECT * FROM [person] WHERE [age] BETWEEN 18 AND 30;
```

## Refining Results

```sql
-- `ORDER BY` `ASC` & `DESC`
SELECT * FROM [person] ORDER BY [name] ASC;
SELECT * FROM [person] ORDER BY [name] DESC;

-- `LIMIT`
SELECT * FROM [person] LIMIT 10;

-- `DISTINCT`
SELECT DISTINCT [name] FROM [person];

-- `TOP` & `WITH TIES`
SELECT TOP 1 * FROM [person];
SELECT TOP 1 WITH TIES * FROM [person] ORDER BY [age] ASC;
SELECT TOP 10 PERCENT * FROM [person] ORDER BY [age] ASC;

-- `GROUP BY`
-- Note: columns not in `GROUP BY` must be in an aggregate function.
SELECT [name], AVG([age]) AS [avg_age]
FROM [person]
GROUP BY [name];

-- `HAVING`
SELECT [name], AVG([age]) AS [avg_age]
FROM [person]
GROUP BY [name]
HAVING COUNT(*) > 1;
```

## Joining Tables

```sql
-- `INNER JOIN`
SELECT * FROM [person]
INNER JOIN [address]
ON [person].[person_id] = [address].[person_id];

-- `LEFT JOIN` preserves all left table's rows, leaving `NULL` for unmatched rows.
-- `RIGHT JOIN` is the opposite.
SELECT * FROM [person]
LEFT JOIN [address]
ON [person].[person_id] = [address].[person_id];

-- `FULL JOIN`
-- Preserving all rows from both tables.
SELECT * FROM [person]
FULL JOIN [address]
ON [person].[person_id] = [address].[person_id];

-- `CROSS JOIN`
-- Cartesian product of two tables.
SELECT * FROM [person]
CROSS JOIN [address];

-- Self `JOIN`
-- Joining a table with itself.
SELECT * FROM [person] AS [p1]
INNER JOIN [person] AS [p2]
ON [p1].[person_id] = [p2].[person_id];

-- Chaining `JOIN`
SELECT * FROM [person]
INNER JOIN [address] ON [person].[person_id] = [address].[person_id]
INNER JOIN [phone] ON [person].[person_id] = [phone].[person_id];
```

## Subqueries

```sql
-- Basic Subquery (inner query auto captures the outer query's columns)
SELECT
    [stu_id],
    [crs_id],
    [grade]
FROM [grades]
WHERE [grade] > (
    SELECT AVG([grades_sub].[grade]) AS [grade_avg]
    FROM [Grades] AS [grades_sub]
    WHERE [grades_sub].[stu_id] = [stu_id]
);

-- `ANY`/`SOME`: `true` if any subquery values meet the condition.
SELECT [product_name]
FROM [products]
WHERE [product_id] = ANY (
    SELECT [product_id]
    FROM [order_details]
    WHERE [quantity] = 10
);

-- `ALL`: `true` if every subquery values meet the condition.
SELECT [product_name]
FROM [products]
WHERE [product_id] = ALL (
    SELECT [product_id]
    FROM [order_details]
    WHERE [quantity] = 10
);

-- `IN` & `NOT IN`
SELECT [supplier_name]
FROM [suppliers]
WHERE [supplier_id] IN (
    SELECT [supplier_id]
    FROM [products]
    WHERE [price] > 50
);

-- `EXISTS` & `NOT EXISTS`
SELECT [supplier_name]
FROM [suppliers]
WHERE EXISTS (
    SELECT [product_name]
    FROM [products]
    WHERE [products].[supplier_id] = [suppliers].[supplier_id] AND [price] < 20
);

-- Relational Division
-- select students who selected all the courses
SELECT -- projection
    [students].[name],
    [students].[id]
FROM [students]
WHERE NOT EXISTS( -- divisor
    SELECT *
    FROM [courses]
    WHERE NOT EXISTS( -- dividend
        SELECT *
        FROM [enrollments]
        WHERE [enrollments].[crs_id] = [courses].[id]
            AND [enrollments].[stu_id] = [students].[id] 
    )
);
```

## `INSERT` With `SELECT`

```sql
-- `INSERT INTO SELECT FROM`
INSERT INTO [customers] ([customer_name], [city], [country])
SELECT [supplier_name], [city], [country]
FROM [suppliers];

-- `SELECT INTO`
SELECT [id], [name], [email]
INTO [employees_new]
FROM [users]
WHERE [id] > 200;
```
