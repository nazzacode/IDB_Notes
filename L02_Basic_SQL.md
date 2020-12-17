
# IDB Lecture 2: Basic Structured Query Language (SQL)

## SQL Data Model
  - Data is organised in _tables_ (aka _relations_)

__Tables (Relations)__ are a collection of _tuples_ (aka _rows_ or _records_)

## SQL
Consists of two sublanguages,\
__Data Definition Language (DDL):__ operations on the schema\
__Data Manipulation Language (DML):__ operations on the instance\ 

## Getting to the UOE psql prompt
Better instructions on piazza:

1. `ssh s1869292@ssh.inf.ed.ac.uk`
2. `ssh student.login`
3. `ssh student.compute` (unnecessary?)
4. `psql -h pgteach`

## PostgreSQL (pqsl)
  - psql command are case insensitive

## Changing the Definition of a Table
```SQL
ALTER TABLE <name>
    RENAME TO <new_name>;
    RENAME <column> TO <new_column>;
    ADD <column> <type>;
    DROP <column>;
    ALTER <column>
        TYPE <type>;
	SET DEFAULT <value>;
	DROP DEFAULT;

TRUNCATE TABLE <name>  -- removes all entries;
DROP TABLE <name>   -- deletes table;
```

## Basic Queries
```SQL
SELECT <list_of_attributes>
FROM <list_of_tables>
WHERE <condtion>
```
- when multiples tables are selected in 'FROM', the tables are concatenated using the cartesian product
