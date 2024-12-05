## Name: Harsh Sanjay Roniyar
### Roll Number: 22B3942

---
Continuing from where we left in the last lecture...

The nature of the bias-variance relations can be better visualized using the contour plots of $y, t, \text{and } x$.

Now, the calculation of the expected loss, as left in [[Lecture 7]] becomes - $$\mathbb{E}[L] = \int\{y({\bf x}) - \mathbb{E}[t|x] \}^2p(x)dx + \int\{\mathbb{E}[t|x] - t \}^2p(x)dx $$The second term in this loss, can be related to the irreducible noise of our data. We can attempt to reduce the first part of the expected loss from our end.

$$h(x) = \mathbb{E}[t|x] = \int tp(t|x)dt $$Now, $\{y(x)-h(x) \}$ is meaningless since our $y(x)$ depends on the data samples. Hence, we will represent it using $\{y(x;D)-h(x)\}^2$ where $D$ is the sample of the distribution.

$$= \{y(x;D) - \mathbb{E}_D[y(x;D)]+\mathbb{E}_D[y(x;D)] - h(x) \}^2, $$where $\mathbb{E}_D[y(x;D)]$ is the expectation over the model. $h(x)$ can be seen as the best theoretical model, and $y(x;D)$ is the particular model under consideration for the given training data.

On further simplification, the final expression reduces to - $$\mathbb{E}_D\left[\{y(x;D)-h(x) \}^2 \right] = \underbrace{\{\mathbb{E}_D[y(x;D)]-h(x) \}^2}_{(\texttt{bias})^2} +\underbrace{\mathbb{E}_D[\{y(x;D) - \mathbb{E}_D[y(x;D)] \}^2]}_{\texttt{variance}} $$Hence, the expected loss can be written as $\texttt{(bias)}^2 + \texttt{ variance } + \texttt{ noise}$. The noise relation will be $$\texttt{noise} = \int \{h(x) - t \}^2p(x, t)\text{d}x\text{d}t $$
#### Model Regularization

##### L2 Regularization
$$y(x_i)=\sum_{j=1}^{D}w_jx_ij + w_0 $$Then, the $L_p$ norm of ${\bf w}$ is given by $$\left(\sum_{j=1}^{D}|w_j|^p\right)^{\frac{1}{p}}$$The norms of $L_{\infty}$ = max $|w_j|$ and $L_0$ = count of non-zero components.

The objective function is - $$\min_w \frac{1}{2}\sum_{i=1}^N(y(x_i)-t_i)^2 + \frac{\lambda}{2}\sum_{j=1}^D|w_j|^q $$with, $$\sum_{j=1}^D|w_j|^q \le \eta $$The objective can be further written as - $$\min_{\bf w} \frac{1}{2}\sum_{i=1}^N(t_i - {\bf w}^T\phi({\bf x}_n))^2 + \frac{\lambda}{2}{\bf w}^T{\bf w} $$$$\implies E_D({\bf w}) + \lambda E_W({\bf w}). $$The optimized solution for ${\bf w}$ is - $$\boxed{{\bf w} = \left(\lambda {\bf I} + \Phi^T\Phi \right)^{-1}\Phi^T{\bf t} }.$$
`The dimension of` $\Phi$ `is` $N\times D$. `Hence, we are taking the pseudo-inverse.`