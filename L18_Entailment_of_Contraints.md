
# IDB Lecture 18: Entailment of Constraints

## Implication of Constraints
A set $\sigma$ of constraints __implies__ (or __entails__) a constraint $\phi$ if _every_ instance that satisfies $\sigma$ also satisfies $\phi$

Syntax: $\sigma \models \phi$

_Question:_ Does $\sigma$ imply $\phi$?

### Relevance
- do the given constraints imply bad ones
- to the given constraints look bad but imply good ones

## Axiomatisation of Constraints
An axiomatisation is--

Sound
  : if every derived constraint is implied 

Complete 
  : if every implied constraint can be derived

__Sound + Complete__ axiomatisation gives a procedure $\vdash$ such that
$$ \sigma \models \phi \iff \sigma \vdash \phi$$

_Intuition:_ if we derive there is an implicit constraint

## Armstrong's Axioms (for FDs)

### Essential Axioms
Reflexivity
  : $Y \subseteq X \Rightarrow X \rightarrow Y$

Argumentation
  : $X \rightarrow Y \Rightarrow XZ \rightarrow YZ \forall Z$

Transitivity
  : $X \rightarrow Y \land Y \rightarrow Z \Rightarrow X \rightarrow Z$

### Derived Axioms
Union
  : $X \rightarrow Y \land Y \rightarrow Z \Rightarrow X \rightarrow YZ$

Decomposition
  : $X \rightarrow YZ \Rightarrow X \rightarrow Y \land X \rightarrow Z$

## Closure of a set of FDs
Let $F$ be a set of FDs, the  __Closure ($F^+$)__ of F is the set of all FDs implied by the FDs in $F$. 

- can be computed using Armstrong's axioms

## Attribute Closure
The __Closure ($C_f(X)$) of a set X of Attributes w.r.t. a set F of FDs__ is the set of attributes we can derive from X using th FDs in F
$$ C_F (X) = \{ A \,|\, F \vdash X \rightarrow A \}$$ 

### Properties
  - $X \subseteq C_F(X)$
  - $X \subseteq Y \Rightarrow C_F(X) \subseteq C_F(Y)$
  - $C_F(C_F(X)) = C_F(X)$

### Solution to implication Problem
$$ F \models Y \rightarrow Z \iff Z \subseteq C_F(Y)$$

## Closure Algorithm
Input: a set $F$ of of $FDs$ and a set $X$ of attributes\
Output: $C_F(X)$, the closure of $X$ with respect to $F$

 __Algorithm__ _Closure(F : {FD}, X : {Attribute}) $\rightarrow$ CFX : {Attribute}_

1. unused $:=$ $F$
2. closure := $X$
3. __while__ $(Y \rightarrow Z) \in$ unused __and__ $Y \subseteq$ closure
4. $\quad$ closure := closure $\cup Z$
5. $\quad$ unused := unused $- \{ Y \rightarrow Z \}$ 
6. __return__ closure
