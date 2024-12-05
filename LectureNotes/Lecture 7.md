## Name: Harsh Sanjay Roniyar
### Roll Number: 22B3942

----
### Linear Regression

Data: $[x_1 \ldots x_D]$, $t$ 
Predictions: $y=f_w(\bar x)$
where, $t_i, y_i \in \mathbb{R}, \forall i$

$$y_i = \left(\sum_{j=1}^Dw_jx_{ij}\right) + w_0  = W^Tx$$This acts as a linear approximation of our data. 

Since $x_i \in \mathbb{R}$. Then I can create $D+1$ features in $\phi_i = \begin{bmatrix}1\\x_i\\x_i^2\\\vdots\\x_i^D\end{bmatrix}$. Then this is a polynomial representation in the x-space, but in linear form in the space $\phi$.

For (all) the data-points, fitting a Gaussian curve at those points and then adding the distributions also gives us a fit for the data.$$\phi = \left[e^{-\frac{(x-x_i)^2}{2\sigma^2}} \right]$$where $\phi$ is a $W\times N$ matrix which can be reduced to $W\times D$. 

**Radial Basis Function**. Similar to Kernel Density Estimation.

---
Now, back to linear regression. 
The predictions $t$, would have some stochastic noise. $$t = y(\textbf{x},{\bf w}) + \epsilon$$Assuming the noise term to be Gaussian and $\beta = \frac{1}{\sigma^2}$
$$p({\bf t}|{\bf X}, {\bf w}, \beta) = \prod_{i=1}^N N(t_i|{\bf w}^T\phi(x_i), \beta^{-1}) $$Now, since this has product terms, taking $\log$:
$$\ln p({\bf t}|{\bf w}, \beta) = \sum_{i=1}^N\ln\frac{1}{\sqrt{2\pi\sigma^2}} - \frac{\{t_i-{\bf w}^T\phi(x_i)\}^2}{2\sigma^2} $$$$ E_D(w) = \frac{1}{2}\sum_{i=1}^N\{t_i - {\bf w}^T\phi(x_i)\}^2 $$
Now, going on to maximizing the likelihood - for this we need to set the gradients w.r.t x to zero. So, we are maximizing, 
$$\nabla \ln p({\bf t|w}, \beta) = \sum_{i=1}^N\{t_n - {\bf w}^T\phi(x_n) \}\phi(x_n)^T $$which finally gives,$${\bf w_{ML}} = (\Phi^T\Phi)^{-1}\Phi^T{\bf t} $$where, $$\Phi = \begin{bmatrix} \phi(x_1)^T \\ \phi(x_2)^T \\\vdots\\ \phi(x_N)^T \end{bmatrix}$$

---
### Conclusions:
1. Assume linear model
2. Assume error is Gaussian distributed
	1. M.S.E is the metric to maximize data likelihood
	2. The analytical solution for $w = \text{PseudoInv}({\bf w})\times{\bf t}$


---
### Bias-Variance Decomposition 
`of linear regression and gaussian noise`

$$L_i = \text{Loss} = (y(x_i)-t_i)^2 $$
Then, $$\mathbb{E}(L) = \int\int L\cdot p(x,t)dxdt = \int\int(y(x) - t)^2p(x,t)dxdt $$
$$\frac{\delta\mathbb{E}(L)}{\delta y(x)} = 2\int\{y(x)-t \}p(x,t)dt = 0 $$This gives, $$y(x)=\frac{\int tp(x,t)\text{d}t}{p(x)} = \mathbb{E}_t(t|x) $$Now, if we try to do manipulation with $$\{y(x)-t \}^2 = \{y(x)-\mathbb{E}(t|x) +\mathbb{E}(t|x)-t \}^2 $$$$=\{y(x)-\mathbb{E}(t|x) \}^2+\{\mathbb{E}(t|x) - t \}^2 + 2\{y(x)-\mathbb{E}(t|x) \}\{\mathbb{E}(t|x)-t \} $$

