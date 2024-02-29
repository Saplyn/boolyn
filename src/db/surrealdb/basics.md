# Basics

## CRUD

### Create

```surql
# record id field (`id`) is defined by default
DEFINE TABLE person SCHEMAFULL;
DEFINE FIELD name ON TABLE person TYPE string;

INSERT INTO person (name) VALUES ('John'), ('Jane');

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
