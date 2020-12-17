
# IDB Lecture 4: Relational Algebra (RA)

## Relational Algebra
Relational Algrbra Expression
  : takes an input of relation(s) ($R$), applies a sequence of operations and returns a relation as an output.

## Operations
Projection ($\pi$)
  : vertical operation which chooses columns. Of general form
  $$\pi_{A_1,...,A_n}(R)$$
  taking only the values of attributes $A_1$ to $A_n$ for each tuple in $R$.\

Selection ($\sigma$)
  : horizontal operation on rows. Of general form 
  $$\sigma_{condition}(R)$$
  taking only the tuples in $R$ for which the condition is satisfied.

  - for $\sigma_{\theta_1}(\sigma_{\theta_2}(R)) = \sigma_{\theta_1 \land \theta_2}(R)$, the RHS generally has faster runtime.\
  
Product ($\times$)
  : cartesian product _concatenates_ each tuple of $R$ with each tuples of $S$. Of general form
  $$R \times S.$$ 
  
  - relations mut have a disjoint set of atributes
  - $cardinality(R \times S) = cardinality(R) \times cardinality(S)$
    - where __Cardinality__ is the number of _rows_.
  - $arity(R \times S) = arity(R) + arity(S)$
    - where __Arity__ is the number of _attributes_.\

Renaming ($\rho$)
  : gives a new name to some attribute of a relation with syntax 
  $$\rho_{replacements}(R)$$ 
  where a replacement has the form $A \rightarrow B$.

### Union, Intersection & Difference
_Note:_ Relations must have the same attributes.

Union ($\cup$)
  : set of all rows in $R$ and $S$

Intersection ($\cap$)
  : all rows that belong to both $R$ and $S$

Difference ($-$)
  : all rows in $A$ that are not in $B$

## Joining relations
Joins can be created by combining Cartesian product $(\times)$ with selection $(\sigma)$.

Natural Join ($\bowtie$)
  : joins two tables on their _common attributes_

Theta-join
  : $R \bowtie_{ \theta} S = \sigma_{\theta}(R \times S$)

Equijoin
  : $\bowtie_{\theta}$ where $\theta$ is a _conjunction of equalities_

Semijoin
  : $R \ltimes_{\theta} S = \pi_X (R \bowtie_{\theta} S)$ where $X$ is the set of attributes of $R$

Antijoin
  : $R \bar{\ltimes_{\sigma}}S = R - (R \ltimes_{\sigma} S$)


## Translating SQL to/from Relational Algebra
`SELECT` $\iff$ projection ($\pi$)\
`FROM`  $\iff$ Product ($\times$)\
`WHERE` $\iff$ selection ($\sigma$)

`SELECT` $A_1, ... , A_n$\
`FROM` $T_1, ... , T_m$\
`WHERE` <condition>\
$\quad \updownarrow$\
$\pi_{A_1,...,A_n}(\sigma_{<condition>}(T_1 \times ... \times T_m))$\
where common attributes in $T_1,...,T_m$ must be renamed.
