
# IDB Lecture 19: Entailment of Constraints 2

## Keys, candidate keys and prime candidate
Let $R$ be a relation with set of attributes $U$ and FDs $F$. $X \in U$ is a __key__ for $R$ if $F \models X \rightarrow U$. Equivalently, $X$ is a key if $C_F(X) = U$ as $C_F(X) = U \iff \{ A \,|\, F \models X \rightarrow A \}$.

__Candidate Key__ (minimal set of attributes) $X$ such that  $\forall \,Y \subset X$, $Y$ is not a key.

__Prime attribute__ an attribute of a candidate key.

### Computing all Candidate Keys
 __Algorithm__ _CandidateKeys(U : {Attribute}, F : {FD}) $\rightarrow$ CK : {{Attribute}}_

 1. $ck$ := $\emptyset$
 2. $G(V,E)$ := $V = \{v \,|\, v \in \mathcal{P}(U)\}$, $E = \{ \overrightarrow{XY} \,|\, X \in v,\, Y \in V,\, X - Y = \{A\}\}$
 3. __while__ $G$ is not empty:
 4. $\quad$ $v$ := node without children
 5. $\quad$ __if__ $C_F(X) = U$:
 6. $\quad \quad$ $ck$ := $ck$ $\cup \{X\}$
 7. $\quad \quad$ $G$ := $G - (X + X_{ancestors})$
 8. $\quad$ __else__:
 7. $\quad \quad$ $G$ := $G - X$  

- more optimal variant in the tutorial (lazy expansion of graph)

## Implication of Inclusion Dependencies (INDs)
__Inclusion Dependency__ 
  Every $X$ is a $Y$, such as in a foreign key constraint.\
_Example:_ every manager is an employee.

### Axiomatisation
Reflexivity
  : $R[X] \subseteq R[X]$\

Transitivity
  : $R[X] \subseteq S[Y] \land S[Y] \subseteq T[Z] \Rightarrow R[X] \subseteq R[Z]$\

Projection
  : $R[X,Y] \subseteq S[W,Z] \text{ with } |X| = |W| \Rightarrow R[X] \subseteq S[W]$\

Permutation
  : $R[A_1,...,A_n] \subseteq S[B_1,...,B_n] \Rightarrow R[A_{i_1},...,A_{i_n}] S[B_{i_1},...,B_{i_n}]$ where $i_1,...i_n$ is a permutation of $1,...,n$.

## FDs and INDs Together
We have shown, 

1. Given a set $F$ of FDs and an FD $f$ we can decide whether $F \models f$
2. Given a set $G$ of INDs and an INDs $g$ we can decide whether $G \models g$

_Implication Problem:_ Asking $F \cup G \models f$ or $F \cup G \models g$ is UNDECIDABLE, no algorithm exists can always solve it. This holds for the case of _keys_ and _foreign keys_ .


