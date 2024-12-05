`After MidSem`
## Name: Harsh Sanjay Roniyar
### Roll Number: 22B3942
---
MidSem Solution Discussion

Now, continuing with classifiers - 
#### SVM for distribution-free learning
Empirical risk: risk of misclassifying training data == structural risk

Minimizing empirical risk implies maximizing margin, i.e. having support vectors close to the separating hyperplanes.

$$\text{max}_{w,b}[\text{min}_i ||\textbf{w}^T\textbf{x}_i+b||] $$is the constrained optimization problem subject to the constraints : $||\textbf{w}|| = 1$ and $\forall i, t_i (w^Tx_i+b)\ge 0$.
$t_i \in \{-1,1\}$ 

The above method was one type of formulation for this, another formulation can be:
$$\text{min}_{v,c} ||\textbf{v}||^2$$such that $\forall i,t_i (\textbf{v}^T\textbf{x}_i+c)\ge 1$ and $\textbf{v}/c = \textbf{w}/b$.
