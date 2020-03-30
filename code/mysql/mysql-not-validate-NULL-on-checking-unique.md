# MySQL does not validate NULL on checking unique

MySQL allows multiple NULLs in a column with a unique constraint.

    CREATE TABLE table1 (x INT NULL UNIQUE);
    INSERT table1 VALUES (1);
    INSERT table1 VALUES (1);   -- Duplicate entry '1' for key 'x'
    INSERT table1 VALUES (NULL);
    INSERT table1 VALUES (NULL);
    SELECT * FROM table1;

Result:

    x
    NULL
    NULL
    1

**This is not true for all databases.** SQL Server 2005 and older, for example, only allows a single NULL value in a column that has a unique constraint.

Ref: https://stackoverflow.com/questions/3712222/does-mysql-ignore-null-values-on-unique-constraints
