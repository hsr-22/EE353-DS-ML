## Name: Harsh Sanjay Roniyar
### Roll Number: 22B3942

---
`Assignment Questions Overview`
#### SVMs
Continuing from the previous lecture,
We saw multiple (convex) optimization objective functions in [[Lecture 13]]

For mathematical convenience, 
$$\text{max}[0, y]\equiv [y]_+ $$and $$max[0,1-y]\equiv l_{hinge}[y]$$
Up until now, we have discussed <u>`Hard SVM`</u> where, we do not allow points between the margins/support vectors (and the loss between the margins increases linearly up to the boundary, where the loss would already be 1, beyond boundary would be $\gt 1$). If the classification point lies beyond the margins, then the loss is definitely zero.

But, if we add newer points which lies between the current support vectors, then the new points closest to the boundary would end up becoming the new margins (`support vector`).

![[Pasted image 20240926192949.png|500]]
y-axis in this plot is the $l_{hinge}$. And from this plot, it can be seen that the loss function is convex, using `Jensen's Inequality`

#### Soft-Margin SVM
Formulation: $$\text{min} \left(\|w\|_2^2+C\sum_i\zeta_i\right)$$
where, $\zeta_i$ are the slack variables subject to - 
- $\forall i$  $t_i[w^Tx_i+b]\ge 1-\zeta_i$
- $\forall i$ $\zeta_i\ge 0$

Equivalently, $$\text{min}_{w,b} \sum_i l_{hinge}(t_i[w^Tx_i+b]) + Regularization$$
where we can choose the regularization of our choice, $L1$ or $L2$.
`As can be noted again, this optimization is also a convex problem`

For Logistic Regression: $\text{min  } \text{CE} + \frac{\lambda}{2} \|w\|_2^2$
##### Values of $\zeta_i$:
- Correct side of margin = 0
- On the margin = 0
- Inside the margin > 0
- On the boundary = 1
- Beyond the boundary > 1

##### Comparison with Hard SVM:
In Hard SVMs, support vectors define the hyperplane and are closest to the hyperplane, which is usually a sparse set of points. The remaining points do not matter since they cannot affect the values of $w$ and $b$.

In Soft SVMs, all the misclassified points are support vectors too, and consequently all points with $\zeta_i \gt 0$ or just at the cusp (read `margin`).

![[Pasted image 20240926195936.png|500]]
The red curve is the cross entropy over sigmoid of $w^Tx_i+b$. CE(Sigmoid())
`A small caveat to keep in mind is that we considered targets as {-1, +1} but for cross entropy over sigmoid would have to relabel to {0, +1} for usage`

#### SV Regression

We change the mean squared error function to a $\epsilon$-insensitive (fault-tolerant) error function.

$$C\sum_{n=1}^{N}E_{\epsilon}(y(x_n)-t_n)+\frac{1}{2}\|w\|^2$$where, $$E_{\epsilon}(y(x)-t) = \begin{cases}
0 & \text{ if } |y(x)-t|\lt \epsilon\\
|y(x)-t|-\epsilon & \text{ otherwise } 
\end{cases}$$
![[Pasted image 20240926202043.png|500]]

Now, defining the slack variables (for fixed $\epsilon$) - 
$t_i \le y_i+\epsilon +\xi_i$ for $\xi\ge 0$
$t_i\ge y_i-\epsilon-\hat{\xi_i}$ for $\hat{\xi_i}\ge0$

Then, the cost function can be written as - $$\text{min}_{w,b} \text{ C}\sum_i \left(\xi_i+\hat{\xi_i}\right) + \frac{1}{2}\|w\|_2^2$$
