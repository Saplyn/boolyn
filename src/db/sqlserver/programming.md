# SQL Programming

<div class="warning">

**This page is <u>INCOMPLETE</u>**

This page is incomplete and is still being written.

</div>

## Variables

```sql
-- Declare a variable
DECLARE @max_id int;

-- Set a variable's value
SET @max_id = 100;
SELECT @max_id = 100, @min_id = 1;

-- SQL variables can only hold one value.
-- If multiple is assigned at a time, the value of the last row is used.
SELECT @employee_name = [employee_name]
FROM [employees]
WHERE [employee_id] = 123;
```

## Control Flow

### Grouping

```sql
-- `BEGIN` & `END`
BEGIN
    PRINT 'statement 1';
    PRINT 'statement 2';
    PRINT 'statement 3';
END
```

### Branching

```sql
-- `IF ELSE` statement
IF EXISTS (
    SELECT *
    FROM [courses]
    WHERE [name] = 'relational database'
)
    BEGIN
        DECLARE @avg_grade FLOAT;
        SET @avg_grade = (
            SELECT AVG([grade])
            FROM [grades]
            INNER JOIN [courses]
            ON [grades].[crs_id] = [courses].[id]
            WHERE [courses].[name] = 'relational database'
        );
    END
ELSE
    PRINT "there is no course named relational database";

-- `CASE WHEN` expression
SELECT
    [order_id],
    [quantity],
    CASE
        WHEN [quantity] > 30 THEN 'The quantity is greater than 30'
        WHEN [quantity] = 30 THEN 'The quantity is 30'
        ELSE 'The quantity is under 30'
    END AS [quantity_text]
FROM [order_details];
```

### Looping

```sql
-- `WHILE` loop
DECLARE @counter INT;
SET @counter = 0;
WHILE @counter < 10
BEGIN
    PRINT 'The counter is ' + CAST(@counter AS VARCHAR);
    SET @counter = @counter + 1;
END

-- `BREAK` & `CONTINUE`
DECLARE @counter INT;
SET @counter = 0;
WHILE (1 = 1)
BEGIN
    SET @counter = @counter + 1;
    IF @counter > 10
        BREAK;
    IF @counter = 5
        CONTINUE;
    PRINT 'The counter is ' + CAST(@counter AS VARCHAR);
END
```

## Stored Procedures

```sql
```

## Functions

```sql
```

## Cursors

```sql
```
