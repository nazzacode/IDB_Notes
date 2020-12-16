
# IDB Lecture 10: Translating Relational Calculus to Relational Algebra

## Active Domain in Relational Algebra
For a Relation $R$ over attributes $A_1,...,A_n$

Adom(R)
  : given by $\rho_{A_1 \rightarrow A}(\pi_{A_1}(R)) \cup \hdots \cup \rho_{A_n \rightarrow A}(\pi_{A_n}(R))$\
  
Adom(D)
  : $\bigcup_{R \in D} Adom(R)$ (where D is a Database) 

- _Intuition:_ return all elements of database in single column
- we denote $Adom_{N}$ (where N is a name) to the RA expression that returns the query.

## From RC to RA
Translate each FOL formula $\rho$ to a RA expression $E$

### Assumptions

- no universal quantifiers, implications or double negations
  - see L07 "Quantifier Duality" for conversions 
- no distinct pair of quantifiers binds the same variable name
- no variable name occurs both free and bound
- no variable names repeated within a predicate
- no constants in predicates
- no atoms of the form $x$ __op__ $x$ or $c_1$ __op__ $c_2$

### Predicate
$R(x_1,...,x_n) \implies \rho_{A_1 \text{is translated to} \eta(x_1),...,A_n \rightarrow \eta (x_n) } (R)$

_Example:_ For $R$ over $A,B,C$, $R(x,y,z)$ is translated to $\rho_{A \rightarrow A_x, B \rightarrow A_y, C \rightarrow A_z}(R)$

### Existential Quantification
$\exists x \, \varphi \text{ is translated to } \pi_{ \eta (X - \{x\})} (E)$\
where

- E is the translation of $\varphi$
- X is free($\varphi$)

_Example:_ For $\varphi$ with free variables $x,y,z$ and translation $E$,, $\exists y \varphi$ is translated to $\pi_{A_x,A_z}(E)$.

### Comparisons
$x \textbf{ op } y \text{ is translated to } \sigma_{\eta(x) \textbf{ op } \eta(y)} (\textbf{Adom}_{\eta(x)} \times \textbf{Adom}_{\eta(y)})$

$x \textbf{ op } c \text{ is translated to } \sigma_{\eta(x) \textbf{ op } c} (\textbf{Adom}_{\eta(x)})$

- where c is a constant

_Example 1:_ $x = y$ is translated to $\sigma_{A_x=A_y}(\textbf{Adom}_{A_x} \times \textbf{Adom}_{A_y} )$

_Example 2:_ $x > 1$ is translated to $\sigma_{A_x> 1}(\textbf{Adom}_{A_x})$  

### Negation
$\neg \varphi \text{ is translated to} \prod_{x \in \textbf{free}_{\varphi}} \textbf{Adom}_{\eta(x)}) - E$\

- where $E$ is the translation of $\phi$
- $\prod$ is the Cartesian product 

_Example:_ For $\varphi$ with free variables $x,y$ and translation $E$, $\neg \varphi$ is translated to $\textbf{Adom}_{A_x} \times \textbf{Adom}_{A_y} - E$



### Disjunction
$\varphi_{1} \lor \varphi_{2} \text{ is translated to } E_1 \times (\prod_{x \in X_2 - X_1} \textbf{Adom}_{\eta(x)} \cup\, E_2 \times (\prod_{x \in X_1 - X_2} \textbf{Adom}_{\eta(x)})$\
where

- $E_i$ is the translation of $\varphi_i$
- $X_i = \textbf{free}(\varphi_i)$

### Conjunction
Same as disjunction, but uses $\cap$ for $\cup$

_Example:_ For Relations,
  
  - Customer (C) : CustID, Name
  - Account (A) : Number, CustID

Translate $\exists x_4 C(x_1,x_2) \land A(x_3,x_4) \land x_1 = x_4$

_Solution:_\
Environment $\eta =\{x_1 \mapsto A, x_2 \mapsto B, x_3 \mapsto C, x_4 \mapsto D \}$\

  1. $C(x_1,x_2) \Rightarrow C$
  2. $A(x_3,x_4) \Rightarrow \rho_{x_1 \rightarrow x_4}(A)$ 
      - to remove clashes 
  3. $x_1 = x_4 \Rightarrow \sigma_{A=D}(\textbf{Adom}_A \times \textbf{Adom}_D)$
  4. $2 \land 3 \Rightarrow 2 \times \textbf{Adom}_A \cap 3 \times \textbf{Adom}_B$
      - note 2 (LHS) and 3 (RHS) do not have same free variables, so we need to add the missing variables to each side
  5. $1 \land 4 \Rightarrow (C \times \textbf{Adom}_C \times \textbf{Adom}_D) \cap \, 4 \times \textbf{Adom}_B$
  6. $\exists x_4 5 \Rightarrow \pi_{A,B,C}(5)$

Expanding out:
$$
\begin{aligned}
\pi_{A,B,C}(&(C \times \textbf{Adom}_C \times \textbf{Adom}_D) \cap \\
&((\rho_{x_1 \rightarrow x_4}(A) \times \textbf{Adom}_A) \cap \\
&(\sigma_{A=D}(\textbf{Adom}_A \times \textbf{Adom}_D)) \times \textbf{Adom}_B) \times \textbf{Adom}_B)
\end{aligned}
$$

  - suspicious of final adom?

Equivalent to (solution on slides): 
$$
\begin{aligned}
\pi_{A,B,C}(&(C \times \textbf{Adom}_C \times \textbf{Adom}_D) \, \cap\\
&(A \times \textbf{Adom}_A \times \textbf{Adom}_B) \, \cap\\
&(\sigma_{A=D}(\textbf{Adom}_A \times \textbf{Adom}_D)) \times  \textbf{Adom}_B \times \textbf{Adom}_C))
\end{aligned}
$$

  - Where $C = \rho_{CustID \rightarrow A, Name \rightarrow B}(C)$
  - &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; $A = \rho_{Number \rightarrow C, CustID \rightarrow D}(A)$
 
