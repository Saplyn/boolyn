# Basics

## CRUD

### Create

```surql
-- record id field (`id`) is defined by default
DEFINE TABLE person SCHEMAFULL;
DEFINE FIELD name ON TABLE person TYPE string;

INSERT INTO person (name) VALUES ("John"), ("Jane");
INSERT INTO person { name: "John" };
INSERT INTO person [{ name: "John" }, { name: "Jane" }];
CREATE person SET name = "John";

DEFINE INDEX idx_name ON TABLE person COLUMNS name;
```

### Read

```surql
SELECT * FROM person;

SELECT name
FROM person
WHERE name = "Jane";

SELECT count() AS person_count
FROM person
GROUP ALL;
```

### Update

```surql
DEFINE FIELD last_name ON TABLE person TYPE string;

UPDATE person
SET last_name = "Doe"
WHERE name = "Jane";

REMOVE FIELD last_name ON TABLE person;
```

### Delete

```surql
DELETE person WHERE name = "Jane";

REMOVE TABLE person;
```

## Using Namespaces/Databases

```surql
USE NS test; -- Switch to the 'test' Namespace
USE DB test; -- Switch to the 'test' Database

-- Switch to the 'test' Namespace and 'test' Database
USE NS test DB test;
```

## Data Relationships

<div class="warning">

**This page is <u>INCOMPLETE</u>**

This page is incomplete and is still being written.

</div>

In SurrealDB, data relationships can be model in three ways:

- embedded record: storing a document within another record field, sacrificing type safety and referential integrity.
- record link: storing a reference to another record, sacrificing referential integrity.
- graph relation:

```surql
-- embedded record
DEFINE TABLE person SCHEMAFULL;
DEFINE FIELD name ON TABLE person TYPE string;
DEFINE FIELD address ON TABLE person FLEXIBLE TYPE object; -- flexible typed document
INSERT INTO person:john {
    name: "John",
    address: { street: "123 Main St", city: "City" }
};

-- record link
DEFINE TABLE person SCHEMAFULL;
DEFINE FIELD name ON TABLE person TYPE string;
DEFINE FIELD address ON TABLE person TYPE record<address>; -- record link to 'address' table
DEFINE TABLE address SCHEMALESS;
INSERT INTO address:john_addr { street: "123 Main St", city: "City" };
INSERT INTO person:john {
    name: "John",
    address: address:john_addr
};

-- graph relation
```
