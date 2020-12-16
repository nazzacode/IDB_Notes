
# IDB Lecture 16: Database Constraints

## Integrity constraints
- instances that satisfy the constraints are called __legal__

## Functional Dependencies (FD)
Syntax: $X \rightarrow Y$, read _X determines Y_

__Definition:__ A relation $R$ satisfies $X \rightarrow Y$ if for every two tuples $t_1,t_2 \in R$
$$\pi_X (t_1) =  \pi_X (t_2) \implies  \pi_Y (t_1) =  \pi_Y (t_2)$$

## Keys (special case FD)
__Definition:__ A set of attributes $X$ which satisfy
$$ \pi_X(t_1) = \pi_X(t_2) \implies t_1 = t_2 \quad \forall t_1,t_2 \in R$$

_Intuition:_ each value in the attribute (column) uniquely identifies the tuple (row)

## Inclusion Dependencies (IND)
Syntax: $R[X] \subseteq S[Y]$ where $R,S$ are relations and $X,Y$ are __sequences__ of attributes

__Definition:__ $R$ and $S$ satisfy $R[X] \subseteq S[Y]$ if
$$ \pi_X (t_1) =  \pi_Y (t_2) \quad \forall t_1 \in R \quad \exists t_2 \in S$$

- Note: the projection must respect attribute order

_Intuition:_ the projection of one table must be a subset of a projection of another table 


