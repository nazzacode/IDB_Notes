
# IDB Lecture 20: Normal Forms

_Redundancy Principle_ don't repeat constrained information in a table. Every FD should define a key. 

## Boyce Codd Normal Form (BCNF)
"Problems with bad designs are caused by FDs $X \rightarrow Y$ where $X$ is not a key."

A relation with FDs $F$ is in __BCNF__ if $\forall X \rightarrow Y \in F$

1. $Y \subseteq X$ (the FD is trivial), OR
2. $X$ is a key (the closure contains all all attributes in the relation). 

- a database is BCNF is all relations are BCNF

## Decompositions
Given a set of attributes $U$ and a set of FDs $F$, a __decomposition__ of $(U,F)$ is a set
$$(U_1,F_1),...,(U_n,F_n)$$
such that $U = \bigcup_{i=1}^n U_i$ and $F$ is a set of FDs over $U_i$

  - dont really understand

### Criteria for good decompositions
__Lossnessness__ No information is lost

__Dependency Preservation__ no constraints are lost

- formal definitions missed 

## Projections of FDs
The __projection__ of $F$ on $V \subseteq U$ is a subset of the closure containing only the attributes of $V$.

## BCNF Decomposition Algorithm
__Algorithm__ _BCNF-Decomposition($U$: {Attribute}, $F$ : {{FD}}) $\rightarrow$ S : {({Attribute}, {FD})}:_

1. $S := \{(U, F)\}$
2. __while__  $\exists (U_i,F_i) \in S$ __not__ BCNF:
3. $\quad$ $S[U_i,F_i]$ := ___decompose($U_i,F_i)$___
4. __if__ $\exists \, \{U_i \,|\, (U_i,F_i) \in S, U_i \subseteq U_j, (U_j,F_j) \in S\}$ 
4. $\quad$ __remove__ $S[U_i,F_i]$ 
5. __return__ S

__Algorithm__ _Decompose($U_i$ : {Attribute}, ${F_i}$ : {FD})) -> ({U}, {F}):_ 

1. find $(X \rightarrow Y) \in F$ __not__ BCNF
2. $V,\, Z := C_F(X), \, U - V$ 
3. __return__ $(V,\pi_V(F))$ __and__ $(XZ, \pi_{XZ}(F))$



