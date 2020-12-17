
# IDB Lecture 5: Relational Algebra on Sets 

## Division
For, $R$ over a set of attributes $X$\, $S$ over a set of attributes $Y \subset X$. Let $Z =  X - Y$
$$
\begin{aligned}
  R \div S &= \{ r \in \pi_Z(R) \,|\, \forall s \in S, rs \in R \}\\
  &= \{ r \in \pi_Z(R) \,|\, \{r\} \times S \subseteq R \}\\
  &= \pi_Z (R) - \pi_Z (\pi_Z (R) \times S - R)
\end{aligned}
$$
Note: I don't really understand\
Intuition: remove all data from X relating to Y?

