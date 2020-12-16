
# IDB Lecture 5: Relational Algebra on Sets 

## Division
Divison
  : $R$ over a set of attributes $X$\
  $S$ over a set of attributes $Y \subset X$\
  Let $Z =  X - Y$\
  $R \div S = \{ r \in \pi_Z(R) \,|\, \forall s \in S, rs \in R \}$\
  $\quad = \{ r \in \pi_Z(R) \,|\, \{r\} \times S \subseteq R \}$\
  $\quad = \pi_Z (R) - \pi_Z (\pi_Z (R) \times S - R)$

Note: I don't really understand

