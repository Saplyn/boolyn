# Basic CRUD

## Create

```sql
CREATE TABLE [person] (
    [person_id] bigint PRIMARY KEY NOT NULL,
    [name] varchar(255) NOT NULL
);

INSERT INTO [person] ([person_id], [name])
VALUES
    (1, 'John'),
    (2, 'Jane');

CREATE INDEX [idx_person_name]
ON person (name);
```

## Read

```sql
SELECT * FROM [person];

SELECT [name]
FROM [person]
WHERE [name] = 'Jane';

SELECT count(*) AS [person_count]
FROM [person];
```

## Update

```sql
ALTER TABLE [person]
ADD [last_name] varchar(255) NULL;

UPDATE [person]
SET [last_name] = 'Doe'
WHERE [name] = 'Jane';

ALTER TABLE [person]
DROP COLUMN [last_name];
```

## Delete

```sql
DELETE FROM [person]
WHERE [name] = 'Jane';

DROP TABLE [person];
```
