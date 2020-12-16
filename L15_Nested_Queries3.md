
# IDB Lecture 15: Nested Queries (Subqueries) 3

## Examples with Exists / Not Exists 
- universal quantification expressed with `NOT EXISTS`
_Question 1. Customers living in a city without a branch (repeat question)?_

```SQL
SELECT * 
FROM Customer C 
WHERE NOT EXISTS ( SELECT *
                      FROM Account A
                      WHERE A.brach = c.city ) ;
```

## Scoping
A subquery has
- a local scope (its `FROM` clause)
- an outer scope

_Question 2. Branches with a total balance (across accounts) of at least 500?_

```SQL
SELECT subquery.branch
FROM ( SELECT A.branch, SUM(A.balance) AS total 
       FROM   Account A
       GROUP BY A.branch ) AS subquery
WHERE subquery.total >= 500 ;
```

_Question 3: Average the total balances across each customer's accounts?_

Strategy 
1. find the total balance across each customers accounts
2. take the average of the totals

```SQL
SELECT AVG(subquery.tot)
FROM   ( SELECT   A.custid, SUM(A.balance) AS tot
         FROM     Account A
         GROUP BY A.custid ) AS subquery ;
```

## Ordering
Syntax: `ORDER BY` $\langle \text{column}_1 \rangle$ [`DESC`] ,..., $\langle \text{column}_n \rangle$ [`DESC`] 

_Example 1_

```SQL
SELECT * 
FROM Accounts
ORDER BY custid ASC, balance DESC; 
```

## Casting 
syntax: `CAST`(term `AS` $\langle$ type $\rangle$

## Conditional Expressions

```SQL
CASE WHEN (bool-exp)
     THEN (value-exp)
     ...
     WHEN (bool-exp)
     THEN (value-exp)
     ELSE (value-exp)
END
```
- ELSE is optional -> NULL if no match 


## Pattern Matching
Syntax: `term LIKE pattern` 

_Question 4: Customers with a name that begins with 'K' and has at least 5 characters?_

```SQL
SELECT *
FROM Customer 
WHERE name LIKE 'K____%' ;
```

