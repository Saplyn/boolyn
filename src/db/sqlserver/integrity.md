# Integrity

<div class="warning">

**This page is <u>IMCOMPLETE</u>**

This page is incomplete and is still being written.

</div>

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

## Triggers

The example below uses [SQL Programming](programming.md), refer to that page
for more information.

```sql
-- `CREATE TRIGGER`
-- `AFTER` & `INSTEAD OF`
```

## Transactions

```sql
```
