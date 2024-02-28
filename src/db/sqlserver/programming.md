# SQL Programming

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

A procedure in SQL Server is a named set of SQL statements, stored in the
database, that can be executed as a single unit. It can alter database
tables, execute queries, and perform other operations.

```sql
-- Declaring a stored procedure
CREATE PROC [proc_customer_info]
    -- `@customer_id` is the input parameter
    @customer_id INT
AS  -- start the procedure's code block
BEGIN
    SELECT * FROM [customers]
    WHERE customer_id = @customer_id
END

-- Executing a stored procedure
EXEC [proc_customer_info] 123;

-- Output parameters
CREATE PROC [proc_customer_info]
    @customer_id INT,
    -- `@customer_name` is the output parameter
    @customer_name NVARCHAR(50) OUTPUT
AS
BEGIN
    SELECT @customer_name = [customer_name]
    FROM [customers]
    WHERE [customer_id] = @customer_id
END
```

## Functions

A function in SQL Server is a reusable piece of code that performs a specific
task and returns a value. It must have at lease one input parameter and returns
a value. It may not alter database objects.

```sql
-- Declaring a function
CREATE FUNCTION [fn_get_customer_name]
    -- `@customer_id` is the input parameter
    (@customer_id INT)
RETURNS NVARCHAR(50)  -- the return type
AS
BEGIN
    DECLARE @customer_name NVARCHAR(50);
    SELECT @customer_name = [customer_name]
    FROM [customers]
    WHERE [customer_id] = @customer_id;
    RETURN @customer_name;
END

-- Calling a function
SELECT [fn_get_customer_name](123) AS [customer_name];

-- Inline `RETURNS TABLE` function
CREATE FUNCTION [fn_get_orders]
    (@customer_id INT)
RETURNS TABLE
AS
RETURN (
    SELECT *
    FROM [orders]
    WHERE [customer_id] = @customer_id
);

-- Calling an inline `RETURNS TABLE` function
SELECT * FROM [fn_get_orders](123);

-- Multi-statement `RETURNS TABLE` function
CREATE FUNCTION [fn_get_orders]
    (@customer_id INT)
RETURNS @orders TABLE (
    [order_id] INT,
    [order_date] DATETIME,
    [total_amount] DECIMAL(10, 2)
)
AS
BEGIN
    INSERT INTO @orders
    SELECT [order_id], [order_date], [total_amount]
    FROM [orders]
    WHERE [customer_id] = @customer_id;
    RETURN;
END
```

## Triggers

Triggers are a special type of stored procedure that are automatically executed
when certain events occur in the database.

```sql
-- `CREATE TRIGGER`
CREATE TRIGGER [trg_orders_insert]
ON [orders]
AFTER INSERT
AS
BEGIN
    PRINT 'A new order has been inserted.';
END;

-- `INSTEAD OF`
CREATE TRIGGER [trg_orders_update]
ON [orders]
INSTEAD OF UPDATE
AS
BEGIN
    PRINT 'An order has been updated.';
    PRINT 'The update has been ignored.';
END;

-- `inserted` and `deleted` tables
CREATE TRIGGER [trg_orders_update]
ON [orders]
AFTER UPDATE
AS
BEGIN
    DECLARE @order_id INT;
    SELECT @order_id = [order_id] FROM [inserted];
    PRINT 'An order has been updated.';
    PRINT 'The order ID is ' + CAST(@order_id AS NVARCHAR(10));
END;
```

## Cursors

A cursor in SQL Server is a database object used to retrieve and manipulate
data row by row, allowing for sequential access to query results.

```sql
-- Declaring a cursor
DECLARE [customer_cursor] CURSOR FOR
SELECT [customer_name], [email]
FROM [customers]
WHERE [last_purchase_date] >= DATEADD(MONTH, -1, GETDATE());

-- Opening a cursor: before fetching rows, the cursor must be opened
OPEN [customer_cursor];

-- Fetching rows
DECLARE @customer_name NVARCHAR(50);
DECLARE @email NVARCHAR(50);
FETCH NEXT FROM [customer_cursor] INTO @customer_name, @email;

-- Closing a cursor & deallocating resources
CLOSE [customer_cursor];
DEALLOCATE [customer_cursor];
```
