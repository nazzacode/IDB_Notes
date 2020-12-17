
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
table1 JOIN table2 ON <condition>       -- defaults to inner
table1 INNER JOIN table2 ON <condition> -- rows in t1 and t2
table1 LEFT JOIN table2 ON <condition>  -- rows in t1
table1 RIGHT JOIN table2 ON <condition> -- rows in t2 
table1 OUTER JOIN table2 ON <condition> -- rows in t1 or t2
```

## (Re)naming Attributes in Queries
```SQL
... FROM Customer C, Account [AS] A ...
```

- the `AS` is optional 

