# Integrity

## Constraints

```sql
-- `PRIMARY KEY`
ALTER TABLE [users]
ADD CONSTRAINT [pk_users_id]
PRIMARY KEY ([id]);

-- `FOREIGN KEY`
ALTER TABLE [orders]
ADD CONSTRAINT [fk_orders_customer_id]
FOREIGN KEY ([customer_id]) REFERENCES [customers]([id])
-- When referenced row is deleted, delete the row with the foreign key.
ON DELETE CASCADE
-- When referenced row is updated, do nothing.
ON UPDATE NO ACTION;

-- `UNIQUE`
ALTER TABLE [users]
ADD CONSTRAINT [uq_users_email]
UNIQUE ([email]);

-- `CHECK`
ALTER TABLE [orders]
ADD CONSTRAINT [ck_orders_quantity]
CHECK ([quantity] > 0 AND [quantity] < 100);

-- `DEFAULT`
ALTER TABLE [users]
ADD CONSTRAINT [df_users_created_at]
DEFAULT GETDATE() FOR [created_at];

-- `IDENTITY`: an auto-incr column, typically for generating primary keys.
ALTER TABLE [users]
ADD CONSTRAINT [df_users_id]
IDENTITY(1, 1);
```

## Transactions

Transactions are used to ensure that a series of SQL statements are executed as
a single unit. If any of the statements fail, the entire transaction is rolled
back.

```sql
-- `BEGIN TRANSACTION` and `COMMIT TRANSACTION`
BEGIN TRANSACTION;
PRINT 'SQL statements...';
PRINT 'SQL statements...';
COMMIT TRANSACTION;

-- `ROLLBACK` to undo the transaction
BEGIN TRANSACTION;
PRINT 'SQL statements...';
PRINT 'Oops, something went wrong...';
ROLLBACK;
```
