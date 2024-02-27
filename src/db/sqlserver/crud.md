# Basic CRUD

<div class="warning">

**All examples are <u>NOT CHECKED</u> for correctness against a real database.**

The check is not performed due to the lack of a real database at the time of
writing to test against. This will be fixed shortly.

</div>

## Create

```sql
CREATE TABLE [dbo].[Employee](
    [EmployeeID] [int] NOT NULL,
    [FirstName] [varchar](50) NOT NULL,
    [LastName] [varchar](50) NOT NULL,
);

INSERT INTO [dbo].[Employee]
    ([EmployeeID], [FirstName], [LastName])
VALUES
    (1, 'John', 'Doe'),
    (2, 'Jane', 'Doe');

CREATE INDEX [IX_Employee_EmployeeID]
ON [dbo].[Employee] ([EmployeeID]);
```

## Read

```sql
SELECT * FROM [dbo].[Employee];

SELECT [EmployeeID], [FirstName], [LastName]
FROM [dbo].[Employee]
WHERE [EmployeeID] = 1;

SELECT count(*) AS [Total]
FROM [dbo].[Employee];
```

## Update

```sql
ALTER TABLE [dbo].[Employee]
ADD [MiddleName] [varchar](50) NULL;

UPDATE [dbo].[Employee]
SET [MiddleName] = 'D'
WHERE [EmployeeID] = 1;

ALTER TABLE [dbo].[Employee]
DROP COLUMN [MiddleName];
```

## Delete

```sql
DELETE FROM [dbo].[Employee]
WHERE [EmployeeID] = 1;

DROP TABLE [dbo].[Employee];
```
