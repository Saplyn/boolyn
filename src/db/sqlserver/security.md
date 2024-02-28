# Security

## Views

Views are virtual tables that are based on the result of a SELECT statement.
They are used to simplify complex queries and to hide the complexity of the
underlying tables.

```sql
-- `CREATE VIEW`
CREATE VIEW [v_users] AS
SELECT [id], [email], [created_at]
FROM [users]
WHERE [is_active] = 1;

-- `SELECT` from a view
SELECT * FROM [v_users];

-- Pass-through `UPDATE` & `DELETE`
-- (The view must be "simple" and directly "computed" from the underlying tables)
UPDATE [v_users]
SET [email] = 'sample@example.com'
WHERE [id] = 123;

-- `WITH CHECK OPTION`
CREATE VIEW [v_active_users] AS
SELECT [id], [email], [created_at]
FROM [users]
WHERE [is_active] = 1
-- this will only allow pass-though modifications that is visible in view
WITH CHECK OPTION;
```

## Schema

A scheme in SQL Server refers is a way to organize database objects, such as
tables, views, procedures, and functions, into logical groups.

```sql
-- Creating a schema
CREATE SCHEMA [security];

-- Creating a table in a schema
CREATE TABLE [security].[users] (
    [id] INT,
    [email] NVARCHAR(50),
    [created_at] DATETIME
);
```

## Logins, Users & Roles

```sql
-- `CREATE LOGIN`: allowing to connect to SQL Server.
CREATE LOGIN [sample_user] WITH PASSWORD = 'password';

-- `CREATE USER`:
-- an identity that can be associated with a login, and can be granted permissions.
CREATE USER [sample_user] FOR LOGIN [sample_user];  -- associate with a login

-- `CREATE ROLE`:
-- a group of users, and can be granted permissions.
CREATE ROLE [sample_role];
CREATE ROLE [sample_role] AUTHORIZATION [sample_user];  -- owned by a user
```

## Permissions

```sql
-- `GRANT`: gives a permission to a user or role.
GRANT SELECT ON [users] TO [sample_role];

-- `REVOKE`: removes a previously granted permission.
REVOKE UPDATE ON [users] FROM [sample_role];

-- `DENY`: explicitly denies a permission to a user or role.
DENY INSERT ON [users] TO [sample_user];

-- `WITH GRANT OPTION`: allows the user to grant the permission to others.
GRANT SELECT ON [users] TO [sample_role] WITH GRANT OPTION;
```
