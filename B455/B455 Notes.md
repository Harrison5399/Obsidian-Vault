
### MLE

$$
X_1, \dots ,X_n \text{ drawn IID from } f(x;\theta) \text{ for some 'true' } \theta=\theta_*
$$
$f(x;\theta)$ being some PDF function from some distribution
**Likelihood**
$$
L_n(\theta) = \prod^n_{i=1}f(X_i;\theta)
$$
**Log-Likelihood**
$$
l_n(\theta) = \log(L_n(\theta)) = \sum^n_{i=1} \log(f(X_i;\theta))
$$
**Maximum Likelihood Estimator**
$$
\hat{\theta}_{MLE} = \arg \max_{\theta} L_n(\theta) = \arg \min_{\theta}  -L_n(\theta)
$$
as $n\rightarrow \infty \implies \hat{\theta}_{MLE} \rightarrow \theta_{*}$
set $\frac{d}{d\theta}=0$ solve for $\theta$
___
**Gaussian MLE parameters**
$$
\hat{\mu}_{MLE} = \frac{1}{n}\sum_{i=1}^n x_i
$$
$$
\hat{\sigma^2}_{MLE} = \frac{1}{n}\sum_{i=1}^n (x_i - \hat{\mu}_{MLE})^2
$$
 $\hat{\sigma^2}_{MLE}$ is biased ($\mathbb{E}[\hat{\sigma^2}_{MLE}] \neq \sigma^2_{*}$) so we use
$$
\hat{\sigma^2}_{unbiased} = \frac{1}{n-1}\sum_{i=1}^n (x_i - \hat{\mu}_{MLE})^2
$$
___
### Regression

$$
\{ (x_{i}, y_{i}) \}^n_{i=1}
$$
#### Linear
$$
y_{i} = x_{i}^T w + \epsilon_{i} \qquad \epsilon \sim^{iid} N(0, \sigma^2)
$$
MLE for $w$ (ordinary least squares (OLS))
$$
\hat{w}_{MLE} = \arg \min_{w} \sum_{i=1}^n (y_{i} - x_{i}^T w)^2 = \arg \min_{w} ||y-Xw||_{2}^2
$$$$
= (\sum^n_{i=1} x_{i}x_{i}^T)^{-1} \sum^n_{i=1} x_{i} y_{i}
$$
$$
= (X^TX)^{-1} X^T Y
$$
With some offset $b$, $\hat{w}_{MLE}$ is the same from above (assuming feature columns are normalized about the average of the features):
$$
y_{i} = x_{i}^T w + b + \epsilon_{i}
$$
$$
\hat{b}_{MLE} = \frac{1}{n} \sum_{i=1}^n y_{i}
$$
___
#### General p-feature
$$
y_{i} = \langle w, h(x_{i}) \rangle
$$
$$
= w_{i}h_{1}(x_{i}) + \dots + w_{p}h_{p}(x_{i})
$$
$h(x)$ can be arbitrary non-linear functions
Feature matrix $H$, each row is $x_{i}$ transformed with feature function $h(x)$
$$
H = \begin{bmatrix}
\dots \; h(x_1)^T \dots \\
\dots \; h(x_2)^T \dots \\
\vdots \\
\dots \; h(x_n)^T \dots
\end{bmatrix}
$$
$$
\hat{w} = \arg \min || Hw-y||_{2}^2
$$
For degree-p polynomial:
$$
h_{i}(x) = x^i
$$
___
#### Lasso Regularization
Sparsity, many entries 0, shrinks some to 0 while only keeping more corelated features
$$
\hat{w}_{lasso} = \arg \min_{w} \sum_{i=1}^n (y_{i}-x_{i}^Tw)^2 + \lambda ||w||_{1}
$$
$\lambda \rightarrow 0$ : $\hat{w}_{lasso} \rightarrow \hat{w}_{OLS}$
$\lambda \rightarrow \infty$ : $\hat{w}_{lasso} \rightarrow 0$
___
#### Ridge Regularization 
Smoothly shrinks weights proportionally to 0
$$
\hat{w}_{ridge} = \arg \min_{w} \sum_{i=1}^n (y_{i}-x_{i}^Tw)^2 + \lambda ||w||_{2}^2
$$
$$
= (X^TX+\lambda I)^{-1}X^Ty
$$
Expected Loss (assume $X^TX = nI \text{ and } y=Xw+\epsilon \quad \epsilon \sim N(0, \sigma^2I)$)
$$
\mathbb{E}_{Y|X, D}[(Y-x^T\hat{w}_{ridge})^2|X=x] = \sigma^2+\frac{\lambda^2}{(n+\lambda)^2}(w^Tx)^2+\frac{\sigma^2n}{(n+\lambda)^2}||x||_{2}^2 
$$
$$
\hat{w}_{ridge} = \frac{n}{n+\lambda}w + \frac{1}{n+\lambda}X^T\epsilon
$$
$\lambda \rightarrow 0$ : $\hat{w}_{ridge} \rightarrow w + \frac{1}{n}X^T\epsilon$
$\lambda \rightarrow \infty$ : $\hat{w}_{ridge} \rightarrow 0$

| Property                        | Lasso Regression                                          | Ridge Regression                             |
| ------------------------------- | --------------------------------------------------------- | -------------------------------------------- |
| Feature selection?              | Yes (some coefficients exactly 0)                         | No (all coefficients are small but nonzero)  |
| Handling of correlated features | Selects one feature, others set to 0                      | Keeps all, shrinks them together             |
| Stability                       | Less stable (different data → different selected feature) | More stable (coefficients smoothly adjusted) |
| Interpretability                | Easier (fewer features remain)                            | Harder (all features contribute)             |
___
### Bias-Variance Tradeoff
**Biased** - model too simple, does not fit data well
**High-Variance** - model too complex, small changes to data changes solution a lot
___
$\boldsymbol{f(x|D)}$ : predicted value of x trained on D ($y_{i}$ value using model)
$\boldsymbol{(x_{*},y_{*})}$ : test data
$\boldsymbol{y_{*}=h(x_{*})+\epsilon_{*}}$ : used to define $h(x_{*})$, $\quad \epsilon_{*}$ is noise independent of $x_*$
$h(x_{i})$ is the true underlying function that generates data, $f(x|D)$ is the prediction function given the dataset $D$
$$
\mathbb{E}_{D,y_{*}}[(y-f(x_{*}))] = \text{Expected Loss}
$$
$$
= \text{Noise} \; + \; \text{Bias}^2 \; +\; \text{Variance}
$$
$$
= \mathbb{E}_{\epsilon_{*}}[(y_{*}-h(x_{*})^2)]\; +\; (h(x_{*})-\mathbb{E}_{D}[f(x_{*}|D)])^2\; +\; \mathbb{E}_{D}[(f(x_{*}|D)-\mathbb{E}_{D}[f(x_{*}|D)])^2]
$$
**Simple Model** : high bias, low variance
**Complex Model** : low bias, high variance
___
#### Generalization
**Generalizes** : if a model performs as well on unseen data as on training data
- In-sample MSE $\approx$ out-sample MSE
**Train error** monotonically decreases with model complexity
**Test error** has a U shape
- As training error goes up, model fails to genializes to new data
___
#### Process
1. Split dataset into **Train**, **Test**, **Validation** (if doing validation)
2. Choose a model
3. Choose a loss function
4. Choose optimization procedure (set $\frac{d}{d\theta_{\text{MLE}}}=0$)
5. Justify accuracy of the estimate (report **Test** error)
___
### Gradient Decent
$$
w_{k+1} = w_{k} - \eta \nabla_{w}f(w_{k})
$$
$\eta$ : step size/learning rate, too large $\rightarrow$ not converge, too small $\rightarrow$ converge slowly, want largest $\eta$ that converges 
$\nabla_{w}f(w_{k}) = \left. \frac{df(w)}{dw} \right|_{w=w_{k}}$ : gradient of error function w.r.t. w
$k \rightarrow \infty$ : $\frac{df(w)}{dw} \rightarrow 0$
Linear Regression Gradient:
$$
\nabla f(w_{t}) = -2X^T(y-Xw_{t})
$$
$$
w_{t+1} = (I-2\eta X^TX)w_{t}+2\eta X^Ty$$
Ridge Regression Gradient:
$$
\nabla f(w_{t}) = -X^T(y-Xw_{t}) + \lambda w _{t}
$$
$$
w_{t+1} = (1 - \lambda)w_{t} + \eta X^T(y-Xw_t)
$$
Lasso Regression Gradient:
$$
\nabla f(w_{t}) = -X^T(y-Xw_{t}) + \lambda\text{sign}(w_{t})
$$
$$
w_{t+1} = w_{t}+\eta X^T(y-Xw_{t}) - \lambda \text{sign}(w_{t})
$$
Ridge converges faster than Lasso because Ridge is convex and smooth, Lasso is convex but non-smooth
___
#### Stochastic Gradient Decent
Instead of computing the gradient over the entire dataset, update weights using gradient from single data point
$$
w_{k+1} = w_{k} - \eta \nabla f_{i}(w_{k})
$$
$\nabla f_{i}(w_{k})$ : gradient of the loss function for a single data point $(x_i, y_i)$
___
#### Mini-Batch SGD
Instead of computing the gradient over just one data point, generate it using the average of a batch of data points
$$
w_{t+1} = w_{t} - \eta \nabla_{w} \frac{1}{B} \sum_{i=1}^B f_{i}(w_{t})
$$
$B$ : batch size
$\nabla_{w} \frac{1}{B} \sum_{i=1}^B f_{i}(w_{t})$: average loss function output from random batches
___
### Kernel
$K : \mathbb{R}^d \times \mathbb{R}^d \rightarrow \mathbb{R}$ is a kernel for a map $\phi : \mathbb{R}^d \rightarrow \mathbb{R}^p$ where $K(x, x') = \langle \phi(x), \phi(x') \rangle$
- $K$ is symmetric
- $K$ is positive semi-definite, $\sum_{i=1}^N\sum_{j=1}^N K(x_{i}, x_{j})c_{i}c_{j} \geq 0$, for all $c_{1}, \dots ,c_{N} \in \mathbb{R}$ 
**RBF Kernel/Gaussian Kernel**
$$
K(x,x') = \exp(-\frac{||x-x'||_{2}^2}{2\sigma^2})
$$
$\boldsymbol{\sigma^2}$ : bandwidth parameter, controls how quickly the kernel value decreases as the distance between points increases
**Polynomial Kernel**
$$
K(x,x') = (x^Tx'+c)^d
$$
**Kernel Trick**
Instead of computing $\langle\phi(x),\phi(x')\rangle$ (computationally inefficient and could be casting into infinite dimension space) kernel trick relies on the fact that many models only need pairwise similarities between data points (Euclidean distance, dot prod, RBF, and polynomial kernel) so you can derive a formula for $K(x,x')$ directly, from Mercers Theorem of kernel being positive semi-definite
$$
\text{there exists some } \alpha \in\mathbb{R}^n\;:\;\hat{w}=\sum_{i=1}^n \alpha_{i}x_{i}
$$
recall what $\hat{w}$ is in cases for linear, ridge, or lasso regression, in the case for ridge regression:
$$
\hat{\alpha}=\arg\min_{\alpha} \sum_{i=1}^n \left(  y_{i}-\sum_{j=1}^n \alpha_{j} \langle x_{j}, x_{i} \rangle \right)^2 + \lambda \sum_{i=1}^n\sum_{j=1}^n\alpha_{i}\alpha_{j}\langle x_{i}, x_{j} \rangle
$$
$$
=\arg\min_{\alpha} \sum_{i=1}^n \left(  y_{i}-\sum_{j=1}^n \alpha_{j} K(x_{i}, x_{j}) \right)^2 + \lambda \sum_{i=1}^n\sum_{j=1}^n\alpha_{i}\alpha_{j}K(x_{i}, x_{j})
$$
$$
= (K + \lambda I_{n \times n})^{-1}y
$$
$\lambda \rightarrow \infty$ : $\alpha \rightarrow 0$, model becomes constant function, biased
$\lambda \rightarrow \infty$ : $K^{-1}$ may not be able to be calculated, overfitting, high variance
**Kernel Regression model** becomes:
$$
f(x) = \sum_{i=1}^n \alpha_{i} K(x,x_{i})
$$
___
### Classification
**Loss function**
$$
\ell(f(x),y) = {1[f(x)\neq y]}
$$
**Expected loss of $f$**
$$
\mathbb{E}_{XY}[1[f(X)\neq Y]] = \mathbb{E}_{X}[1-\mathbb{P}(Y=f(x)|X=x)]
$$
#### Bayes Optimal Binary Classifier 
$$
\hat{f}(x) = \arg \max \mathbb{P}(Y=y|X=x) 
$$
$$
= \arg \max_{y\in \{0, 1\}} \frac{\sum_{i=1}^n 1[x_{i}=x, y_{i}=y]}{\sum_{i=1}^n 1[x_{i}=x]}
$$
$X$ : discrete, $X\in \{1,2, \dots, m\}$
$Y \in \{ 0,1 \}$
#### Logistic Regression
Suppose $X$ is continuous such $X\in \mathbb{R}^d$ and $Y\in \{0,1\}$
$$
P[Y=1|X=x,w]=\sigma(w^Tx)
$$
$$
P[Y=0|X=x,w]=1-\sigma(w^Tx)=-\sigma(w^tx)
$$
$$
\sigma(z)=\frac{1}{1+e^{-z}}
$$
**Intuition** : as $w^Tx$ increases, the likelihood of $Y=1$ increases
**Linear Decision Rule**
Using $P[Y=1|X=x,w]=\sigma\left( w_{0}+\sum_{k}w_{k}X_{k} \right)$ (with offset and multiple features)
$$
\log\left( \frac{P[Y=1|X=x,w]}{P[Y=0|X=x,w]} \right) = w_{0}+\sum_{k}w_{k}X_{k}
$$
Equation represents a hyperplane that separates feature space into two regions, >0 and <0 
$$
\hat{w}_{MLE} = \arg \min_{w} \sum_{i=1}^n \log(1+\exp(-y_{i}x^T_{i}w))
$$
$$
y = \text{sign}(b+x^Tw)
$$
**Multiclass Logistic Regression**
$$
P[y_{i}=c_{j}|x_{i}] = \frac{\exp(w[:,j]^Tx_{i})}{\sum_{j'=1}^k \exp(w[:,j']^Tx_{i})}
$$
$$
\hat{w} = \arg \max_{w\in \mathbb{R}^{d\times k}} \frac{1}{n} \sum_{i=1}^n \sum_{j=1}^k I\{y_{i}=c_{j} \} \log(\frac{\exp(w[:,j]^Tx_{i})}{\sum_{j'=1}^k \exp(w[:,j']^Tx_{i})})
$$
**One-hot Encoding** : casting n dimensional discrete set to n dimensional vector with index representing some index in set, (equally distant from each other)
___
### Cross Validation
#### Leave-one-out
**D** : training data
**D\j** : training data with jth data pont $(x_{i}, y_{i})$ moved to validation set
$\boldsymbol{f_{D \backslash j}}$ : learned prediction function with $D\backslash j$ dataset
$$
\text{error}_{LOO} = \frac{1}{n} \sum_{j=1}^n (y_{j - f_{d\backslash j}}(x_{j}))^2
$$
___
#### k-fold
$\boldsymbol{D \backslash D_{i}}$ : randomly divided training data into **k** equal parts, $D_{1},\dots,D_{k}$, $D$ minus $D_i$
$\boldsymbol{f_{D\backslash D_{i}}}$ : learned prediction function using  $D\backslash D_{i}$ dataset
$$
\text{error}_{k-fold} = \frac{1}{k} \sum^k_{i=1} \frac{1}{|D_{i}|} \sum_{(x_{j}, y_{j}) \in D_{i}} (y_{j} - f_{D\backslash D_{i}}(x_{j}))^2
$$
___
### Clustering 
#### K-Means
Randomly initialize $k$ centers:
$$
\mu^t = \{ \mu_{1}^t, \mu_{2}^t, \dots, \mu_{k}^t \} \quad t=0, \text{(for index of itteration, not exponential) }
$$
Assign each point $j \in \{ 1, \dots, N \}$ to nearest center:
$$
C^t(j)  = \arg \min_{i} ||\mu_{i} - x_{j} ||^2_{2}
$$
$\boldsymbol{C^t(j)}$: cluster assignment, maps some point $x_{j}$ to its assigned cluster $i$ and therefore centroid $\mu_i$

Recenter $\mu_i$ so it becomes centroid of its point:
$$
\mu_{i}^{t+1} = \arg \min_{\mu} \sum_{j:C(j)=i} ||\mu - x_{j} ||_{2}^2
$$
$$
= \frac{\sum x_{j}}{|C(j)=i|}
$$
$\boldsymbol{j:C(j)=i}$: all data points  $x_{j}$ such that the cluster is $i$

Objective function (minimizing $\mu$ given its cluster $j$, minimizes the within-cluster sum of squares):
$$
F(\mu, C) = \arg \min_\mu \min_C \sum_{i=1}^k \sum_{j:C(j)=i} || \mu_i - x_j ||_2 ^2 
$$
___
### Dimensionality Reduction
#### SVD
$$
A_{m\times n} = U\Sigma V^T
$$
$k = \min(m, n)$
$\boldsymbol{U}$ : $m \times k$ matrix, $n\geq m \implies$ square
- left singular vectors, word embeddings
$\boldsymbol{\Sigma}$ : $k \times k$ matrix, diagonal, sorted such $\sigma_{1} \geq \sigma_{2} \geq \dots$
- singular values, scaling factor
$\boldsymbol{V}$ : $m \times k$ matrix, $m\geq n \implies$ square
- right singular vectors, document embeddings 





### Probability

$$
X \sim N(\mu_X, \sigma^2_X),\quad T \sim N(\mu_T, \sigma^2_T) 
$$
$$
Y = aX+b \implies Y \sim N(a\mu_X+b, a^2\sigma^2_X)
$$
$$
Z = X + T \implies Z \sim N(\mu_X + \mu_T, \sigma^2_X+\sigma^2_T)
$$
$$
\mathbb{E}[aX+bY] = a\mathbb{E}[X]+b\mathbb{E}[Y], \; \text{for some constants }a,b
$$
$$
\mathbb{E}[XY] = \mathbb{E}[X]\;\mathbb{E}[Y]
$$
$$
\mathbb{E}_{x}, \text{expected value with respect to } x
$$
$$
P(A|B)=\frac{P(B|A)P(A)}{P(B)}
$$
**Binomial Distribution**
$$
P(D|\theta) = \theta^k(1-\theta)^{n-k}
$$
**Gaussian/Normal Distribution**
$$
f(x) = \frac{1}{\sqrt{ 2 \pi \sigma^2 }} e^{-\frac{(x-\mu)^2}{2\sigma^2}}
$$
___
### Linear Algebra
$$
||z||_{2} = \sqrt{ \sum_{i=1}^n z_{i}^2} = \sqrt{ z^T z } \implies ||z||_{2}^2 = z^T z 
$$
$$
x^Tw = w^Tx
$$
$$
\langle u, v \rangle = u^Tv = \sum_{i=1}^n u_{i} v_{i}
$$
$$
\|x-a\|^2_2 = (x-a)^T(x-a)
$$
$$
\frac{\partial \|x\|_2^2}{\partial x} = 2x
$$$$
\frac{\partial}{\partial x} \|x-a\|_2 = \frac{x-a}{\|x-a\|_2}
$$
$$
\frac{\partial}{\partial x} x^TxA = 2xA
$$
$$
\frac{\partial}{\partial x} ax^T = \frac{\partial}{\partial x} a^Tx = a
$$
$$
\frac{\partial}{\partial X} a^T Xb =ab^T\\
$$
$$
\frac{\partial }{\partial X} a^TX^Tb =ba^T \\
$$
$$
\frac{\partial }{\partial X} a^TXa=\frac{\partial }{\partial X} a^TX^Ta =aa^T
$$