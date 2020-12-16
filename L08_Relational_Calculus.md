
# IDB Lecture 8: Relational Calculus (RC)

- extension of predicate logic

## Relational Calculus
A __relational calculus query__ is an expression of the form $\{\bar{x} \,|\, \phi \}$ where,

  - head ($\bar{x}$) is a tuple of variables
  - body ($\varphi$) is a FOL formula 
  - all the free variables in the body must be mentioned in the head.
  - queries without heads are called boolean queries.

_Example 1:_ Name the customers younger than 33 or older than 50 (where Customer = Id, Name, Age).
$$\{ y \,|\, \exists x,z \, \text{ Customer}(x,y,z) \land (z < 33 \lor z > 50) \}$$

_Example 2:_ Name and age of customers having an account in London (where Account = Number, Branch, CustID).
  $$\{y,z \,|\, \exists x \, \text{ Customer}(x,y,z) \land \exists w \, \text{Account}(w,\text{'London'},x)\}$$

_Example 3:_ ID of customers who have and account in _every_ branch.
  $$\{x \,|\, \exists y,x \text{ Customer}(x,y,z) \land (\forall u,w,v \text{ Account}(u,w,v) \rightarrow \exists u' \text{ Account}(u',w,x)) \}$$
  
## Interpretations in RC
Every constant is interpreted as itself

## Answer to Queries
With every constant fixed, relational calculus queries are really a 'database' as they only operate over the relations.

The answer to a query $Q = \{ \bar{x} \varphi \}$ on a database $D$ is
  $$Q(D) = \{ v(\bar{x}) \,|\, v: \textbf{free}(\varphi) \rightarrow \delta \text{ such that } D,v \models \varphi \}$$

## Safety
Safety 
  : A query is safe if it gives a finite answer on all databases and this answer does not depend on the universe $\Delta$.

  - Safety Test: can this query give me an infinite answer (on an infinite database)?

