
# IDB Lecture 3: Basic SQL 2

## Database Modification
```SQL
UPDATE <table>
SET <assignments>
WHERE <condition>
```

## Joins 
Joins are syntactic sugar for filters with multiple tables

```SQL
table1 JOIN table2 ON <condition>
table1 INNER JOIN table2 ON <condition>
table1 LEFT JOIN table2 ON <condition>
table1 RIGHT JOIN table2 ON <condition>
table1 OUTER JOIN table2 ON <condition>
```

## Renaming attributes
```SQL
... FROM Customer c, Account [AS] A ...
```

- the `AS` is optional 

