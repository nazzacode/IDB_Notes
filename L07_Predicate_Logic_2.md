
# IDB Lecture 7: Predicate Logic 2

## Satisfiability and Validity
A formula is:
Satisfiable
  : if it has a model.

Unsatisfiable
  : if it has no models.

Falsifiable
  : is thre is some interpretation that is not a model.

Valid (tautology)
  : is every interpretation is a model.

## Equivalence
Equivalence ($\equiv$)
  : Two formulas are _logically equivalent_ if they have the same models.

## Universal and Existential Quantification

### Universal Quantification ($\forall$)
Everyone taking IDS is smart: 
  $$\forall x (Takes(x,dbs) \rightarrow Smart(x))$$

  - typically $\rightarrow$ is the main connective with $\forall$

### Existential Quantification ($\exists$)
Someone takes IDS and fails:
  $$\exists x (Takes(x,dbs) \land Fails(x,dbs))$$
  
  - typically $\land$ is the main connective with $\exists$

## Quantifier duality
Each quantifier can be expressed using the other.
$$\forall x \text{ Likes}(x,cake) \equiv \neg \exists x  \neg \text{ Likes}(x,cake)$$
$$\exists x \text{ Likes}(x,broccoli) \equiv \neg \forall x \neg \text{ Likes}(x,broccoli)$$

## Equivalence Properties
Commutativity, Associativity, Distributivity, Idempotence, Absorption, De Morgan, Implication

