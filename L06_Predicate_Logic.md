
# IDB Lecture 6: Predicate Logic

Free variables
  : variables that are not in the scope of any _quantifier_. A variable that is not free is _bound_.

## Interpretations
A formula may be true or false w.r.t a given _interpretation_.

Interpretation
  : defines the semantics of the language; an assignment of variables that gives meaning to a statement.

## Semantics of FOL: Interpretations
First Order Structure
  : $\mathcal{I} = \langle \Delta, \cdot^{\mathcal{I}} \rangle$\
  $\Delta$ non empty domain of objects (universe)\
  $\; a^{\mathcal{I}}$ function which gives meaning to constant & predicate symbols

    - $a^{\mathcal{I}} \in \Delta$ -- gives meaning to _constants_, "object a by means of interpretation function $\mathcal{I}$".
    - $R^{\mathcal{I}} \subseteq \Delta^{1} \times ... \times \Delta^{n}$ -- gives meaning to _predicates_, "mapping it to an element in our domain (objects in the unverse)" 

Variable Assignment ($v$)
  : maps each variable to an object in $\Delta$
  
    - _Notation:_ $v[x/d]$ is $v$ with x $\rightarrow$ d

## Semantics of FOL: Terms

Interpreatation of terms under $(\mathcal{I},v)$
  : 
  $$x^{\mathcal{I},v} = v(x)$$
  $$a^{\mathcal{I}, v} = a^{x}$$

### Formulas
$(\mathcal{I},v) \models \phi$ means interpretation $(I,v)$ satisfies formula $\phi$

$$
\begin{aligned}
  I,v \models P(t_1,...,t_n) &\iff (t_1^{\mathcal{I},v},...,t_n^{\mathcal{I},v}) \in P \\ 
  I,v \models \neg \phi &\iff \mathcal{I},v \nvDash \phi \\
  I,v \models \phi \land \psi &\iff \mathcal{I},v \models \phi \text{ and } \mathcal{I},v \models \psi \\
  I,v \models \phi \lor \psi &\iff \mathcal{I},v \models \phi \text{ or } \mathcal{I},v \models \psi \\
  I,v \models \phi \to \psi &\iff \mathcal{I},v \models \phi \text{ then } \mathcal{I},v \models \psi \\
  I,v \models \forall x \phi &\iff \text{for every } d \in \Delta : \mathcal{I},v[x/d] \models \phi \\
  I,v \models \exists x \phi &\iff \text{there exists } d \in \Delta \text{ s.t } \mathcal{I},v[x/d] \models \phi \\
\end{aligned}
$$
