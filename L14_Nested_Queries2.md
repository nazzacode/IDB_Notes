
# IDB Lecture 14: Nested Queries (Subqueries) 2

_Question 1. Id of customers from London who own an account?_

```SQL
SELECT C.ID
FROM Customer C
WHERE C.City = 'London'
  AND C.ID = ANY (  SELECT A.custID 
                    FROM Account A ) ;
```

_Question 2. Customers living in a city without a branch?_

```SQL
SELECT * 
FROM Customer C 
WHERE C.city <> ALL ( SELECT A.branch
                      FROM Account A ) ;
```
 - `<> ALL` could be replaced with `NOT IN` 

_Question 3. Return all the customers if there are some accounts in London?_

```SQL
SELECT * 
FROM Customer C
WHERE EXISTS (  SELECT 1
                FROM Account A
                WHERE A.branch = 'London'
                  AND A.CustID = C.id ) ;
```


_Question 4. ID of customers who own an account (living in London)?_

```SQL
SELECT C.Id 
FROM Customer C
WHERE C.City = 'London'
  AND EXISTS (  SELECT * 
                FROM Account A
                WHERE A.CustId = C.id ) ;
```


