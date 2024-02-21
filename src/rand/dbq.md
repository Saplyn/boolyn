# DBQ

```dbq
/*
CREATE TABLE TableName (
    key_col Type,
    val_col Type,
    ref_col Type
);
*/
table TableName (
    key_col: Type,
    val_col: Type,
    ref_col: Type,
)

// DROP TABLE TableName;
drop TableName;

// CREATE INDEX idx_name ON TableName (key_col);
index TableName.idx_name (key_col);

// DROP INDEX TableName.idx_name;
drop TableName.idx_name;
```

```dbq
// ALTER TABLE TableName ADD PRIMARY KEY (key_col);
rule TableName.Key (key_col);
rule TableName.Constraint key (key_col);

// ALTER TABLE TableName ADD PRIMARY KEY (key_col, val_col);
rule TableName.Key (key_col, val_col);

// ALTER TABLE TableName ADD FOREIGN KEY (ref_col) REFERENCES ref_table (ref_col);
rule TableName.Constraint link (
    ref_col: TableName.key_col,
);

// ALTER TABLE TableName ADD FOREIGN KEY (ref_col_1, ref_col_2) REFERENCES ref_table (ref_col_1, ref_col_2);
rule TableName.Constraint link RefTable (
    ref_col_1: ref_col_1,
    ref_col_2: ref_col_2,
);

// ALTER TABLE TableName DROP CONSTRAINT TableName.Constraint;
// TODO: which is better?
wipe TableName.Constraint;
drop TableName.Constraint;
```

```dbq
// INSERT INTO TableName (key_col, val_col, ref_col) VALUES (key_val, val_val, ref_val);
add TableName (key_col, val_col, ref_col) {
    (val_1, val_2, val_3),
};

// SELECT * FROM TableName WHERE key_col = key_val;

// SELECT grp_col, SUM(val_col) AS alias FROM TableName GROUP BY grp_col;
get TableName (
    grp_col,
    sum(val_col): alias,
) // TODO: GROUP BY grp_col;

// DELETE FROM TableName WHERE key_col = key_val;

// UPDATE TableName SET val_col = val_val WHERE key_col = key_val;
```

```dbq
