
# IDB Lecture 12: Aggregation with Grouping

For table `Account` with columns `Number, Branch, CustID, Balance, Spend`

1. _How much money does each customer have in total across all of their accounts?_

```SQL
SELECT A.custID, SUM(A.balance)
FROM Account A
GROUP BY A.custID ; 
```

2. _How much money is there total in each branch?_

```SQL
SELECT A.branch SUM(A.balance)
FROM Account A
GROUP BY A.branch ;
```

3. _How much money does each customer have in each branch?_

```SQL
SELECT A.custID, A.branch, SUM(A.balance)
FROM Account A
GROUP BY A.custID, A.branch ;
```

4. _Branches with a total balance (across accounts) of at least 500?_

```SQL 
SELECT A.branch SUM(A.balance)
FROM Account A
GROUP BY A.branch
HAVING SUM(A.balance) >= 500 ;
```
- can't use `WHERE` as its has evaluation precedence over `GROUP BY`

## Order of Evaluation Precedence
1. `FROM` -- taking rows from (joined) tables listed
2. `WHERE` -- discard rows not satisfying the condition
3. `GROUP BY` -- partition rows according to attributes
4. __Compute Aggregates__
5. `HAVING` -- discard rows not satisfying
6. `SELECT` -- output the value of expressions listed


5. _Money available in total to each customer across their accounts?_

```SQL
SELECT custID, SUM(A.balance - A.spend)
FROM Account A
GROUP BY A.custID ;
```



