
# IDB Lecture 13: Nested Queries (Subqueries)

_Question 1: Accounts with a higher balance that the average of all accounts?_

```SQL
SELECT A.number
FROM Account A
WHERE A.balance > ( SELECT AVG(A1.balance.)
                    FROM Account A1 ) ;
```

```SQL
SELECT ... 
FROM ...
WHERE (term_1,...,term_n op (subquery ) ;
```
- valid iff size(subquery) == n

## Revisiting `WHERE`
term := attribute | value

### Comparison
  - `(term,...,term)` __op__ `(term,...,term)`
  - `term IS [NOT] NULL`
  - `(term,...,term)` __op__ `ANY (query)` 
  - `(term,...,term)` __op__ `ALL (query)` 
  - `(term,...,term)` __op__ `[NOT] IN (query)` 
  - `EXISTS (query)`

### Condition
  - comparison
  - condition `AND` condition
  - condition `OR` condition
  - `NOT` condition


### All / Any 
- All/Any vs. empty set -> true
