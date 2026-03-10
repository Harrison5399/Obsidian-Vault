# Machine Learning Overview

## Types of Learning

- **Supervised Learning:**
  - *Regression*: Predict continuous outcomes (e.g., house prices).
  - *Classification*: Assign labels (e.g., coin classifier).
- **Unsupervised Learning:**
  - *Clustering & Dimensionality Reduction (PCA)*
- **Reinforcement Learning:**
  - Learning via rewards to optimize decision making.

## ML Process Outline

1. Data Collection & Preparation
2. Feature Selection/Engineering
3. Exploratory Data Analysis
4. Model & Parameter Selection
5. Training (e.g., by maximizing likelihood)
6. Evaluation (using cross‑validation and test splits)

---

# Linear Algebra & Calculus

$$
\|x-a\|^2_2 = (x-a)^T(x-a)
$$
$$
\|x\|_2 = \sqrt{x_1^2 + x_2^2 + \dots + x_d} \\
= \sqrt{x^T x}
$$

$$
\|x\|_2^2 = x_1^2 + x_2^2 + \dots + x_n^2 \\
= x^T x
$$

$$
\frac{\partial \|x\|_2^2}{\partial x} = 2x
$$

$$
\frac{\partial}{\partial x} \|x-a\|_2 = \frac{x-a}{\|x-a\|_2}
$$

$$
\frac{\partial}{\partial x} x^T x A = 2 x A
$$

$$
\frac{\partial}{\partial x} a x^T = \frac{\partial}{\partial x} a^T x = a
$$

$$
\frac{\partial}{\partial X} a^T X b = a b^T \\
\frac{\partial}{\partial X} a^T X^T b = b a^T \\
\frac{\partial}{\partial X} a^T X a = \frac{\partial}{\partial X} a^T X^T a = a a^T
$$

inner product formula <>

# Maximum Likelihood Estimation (MLE)

## Concept

Choose parameters that maximize the likelihood of the observed data.

- **Likelihood Function:**

$$
L(\theta) = \prod_{i=1}^{n} f(x_i;\theta)
$$

- **Log-Likelihood:**

$$
\ell(\theta) = \sum_{i=1}^{n} \log f(x_i;\theta)
$$

## Examples

- **Coin Tosses:**

$$
P(\mathcal{D}|\theta) = \theta^k (1-\theta)^{n-k}
$$

- **Gaussian Distribution:**

$$
P(x \mid \mu,\sigma) = \frac{1}{\sigma\sqrt{2\pi}} \exp\!\left(-\frac{(x-\mu)^2}{2\sigma^2}\right)
$$

---

# Linear Regression

## Problem Setup

Given training pairs $\{(x_i, y_i)\}_{i=1}^n$, predict $y$ using:

$$
y_i \approx w^T x_i + b.
$$

## Least Squares Objective

$$
\hat{w}_{LS} = \arg\min_w \sum_{i=1}^n (y_i - x_i^T w)^2,
$$

with closed-form solution (if $X^T X$ is invertible):

$$
\hat{w}_{LS} = (X^T X)^{-1} X^T y.
$$

## Prediction

For a new input $x_{\text{new}}$:

$$
\hat{y}_{\text{new}} = x_{\text{new}}^T \hat{w}_{LS} + \hat{b}_{LS},
$$

with the offset often given by

$$
\hat{b}_{LS} = \frac{1}{n} \sum_{i=1}^n y_i.
$$

---

# Polynomial Regression (Nonlinear Regression)

## Using Basis Functions

Transform the input using nonlinear functions $h(x)$. For example:

- **Linear:** $\hat{y} = b + w_1 x$
- **Quadratic:** $\hat{y} = b + w_1 x + w_2 x^2$
- **General:** $\hat{y} = \langle w, h(x) \rangle$ where $h(x)$ might include $\log(x)$, $\sin(x)$, $\sqrt{x}$, $x^2$, etc.

## Model Complexity

The number and type of basis functions control model complexity, affecting both in-sample fit and generalization.

---

# Regularization in Linear Regression

Regularization penalizes complex models to improve generalization.

## Ridge Regression

### Objective

$$
\hat{w}_{\text{ridge}} = \arg\min_w \sum_{i=1}^n (y_i - x_i^T w)^2 + \lambda \|w\|_2^2.
$$

**Closed-form solution:**

$$
\hat{w}_{\text{ridge}} = (X^T X + \lambda I)^{-1} X^T y. \\
= \frac{n}{n+\lambda} w + \frac{1}{n+\lambda} X^T \epsilon.
$$

### Effect of Regularization

- **Visualization:**  
  The solution is indexed by the regularization parameter $\lambda$:
  - As $\lambda \to 0$, the solution approaches the unregularized least-squares solution.
  - As $\lambda \to \infty$, the weights shrink toward zero.

- **Insight:**  
  The gain in test MSE comes from shrinking $w$ to produce a less sensitive (lower-variance) predictor.

## Lasso Regression

### Objective

$$
\hat{w}_{\text{lasso}} = \arg\min_w \sum_{i=1}^n (y_i - x_i^T w)^2 + \lambda \|w\|_1.
$$

- **Key Feature:**  
  The $\ell_1$ penalty tends to produce sparse solutions (many coefficients exactly zero), aiding in feature selection.

### Comparison: Ridge vs. Lasso

| Property                     | Lasso                                | Ridge                                |
|------------------------------|--------------------------------------|--------------------------------------|
| Feature Selection            | Yes (sparse solution)                | No (coefficients are shrunk but nonzero) |
| Handling Correlated Features | Chooses one feature                  | Shrinks coefficients together        |
| Computational Efficiency     | May require iterative methods        | Closed-form for linear regression    |

---

# Bayesian Perspective and MAP Estimation

MAP (Maximum A Posteriori) estimation extends MLE by incorporating prior beliefs.

## Definitions

- **MLE:**

$$
\theta^{\text{MLE}} = \arg\max_{\theta} \prod_{i=1}^n p(x_i|\theta)
$$

- **MAP:**

$$
\theta^{\text{MAP}} = \arg\max_{\theta} p(\theta | x_1, \dots, x_n)
= \arg\max_{\theta} \Bigl[\prod_{i=1}^n p(x_i|\theta)\Bigr] p(\theta).
$$

Here, $p(\theta)$ is the prior, representing our knowledge about $\theta$ before seeing the data.

## MAP and Ridge Regression

Assuming a Gaussian prior on $w$:

$$
p(w) \propto \exp\!\left(-\frac{\lambda}{2}\|w\|_2^2\right),
$$

the MAP estimator becomes:

$$
\hat{w}_{\text{MAP}} = \arg\min_w \Bigl( \|y - Xw\|^2 + \lambda \|w\|_2^2 \Bigr),
$$

which is exactly the ridge regression objective.

## Additional Bayesian Notes

- MAP estimation balances the data fit (likelihood) with prior beliefs.
- Different priors yield different regularization effects (e.g., a Laplace prior leads to Lasso).

---

# Gradient Descent and Its Variants

Gradient descent is an iterative optimization method used to minimize loss functions.

## Basic Gradient Descent

### Principle

For a differentiable function $f(w)$, the update rule is:

$$
w_{t+1} = w_t - \eta \nabla f(w_t),
$$

where $\eta$ is the learning rate.

### 1-Dimensional Example

Using a Taylor series approximation for $w$ near $w_0$:

$$
f(w) \approx f(w_0) + (w-w_0) f'(w_0).
$$

For a sufficiently small $\eta$, this update guarantees that $f(w_{t+1}) < f(w_0)$.

## Gradient Descent for Linear Regression

Given data $\{(x_i, y_i)\}_{i=1}^n$ and the least-squares loss:

$$
f(w) = \|y - Xw\|_2^2,
$$

the gradient is:

$$
\nabla f(w) = -2 X^T (y - Xw).
$$

Thus, the update rule becomes:

$$
w_{t+1} = w_t + 2\eta X^T (y - Xw_t).
$$

In matrix form, one can express the error evolution as:

$$
w_{t+1} - w^* = (I - 2\eta X^T X)(w_t - w^*),
$$

with $w^*$ being the least-squares solution.

## Step Size (Learning Rate) Considerations

- **Too large:** May not converge.
- **Too small:** Convergence is very slow.
- **Practice:** Often choose the largest $\eta$ that still ensures convergence.

## Stochastic Gradient Descent (SGD)

Instead of computing the gradient on the full dataset:

$$
w_{t+1} = w_t - \eta \nabla_w \Bigl(\frac{1}{n}\sum_{i=1}^n \ell_i(w)\Bigr),
$$

SGD updates using a single (or a mini-batch of) randomly selected data point(s):

$$
w_{t+1} = w_t - \eta \nabla_w \ell_{i_t}(w),
$$

where $i_t$ is drawn uniformly from $\{1,\ldots,n\}$. Its expected gradient equals the full gradient:

$$
\mathbb{E}[\nabla_w \ell_{i_t}(w)] = \nabla \ell(w).
$$

## Mini-batch Gradient Descent

- Uses a batch of $B$ samples to compute the gradient.
- **Advantage:** Reduced variance in the gradient estimate (variance reduced by a factor of $1/\sqrt{B}$) and potential for parallel computation.

---

# Final Remarks

## Learning Pipeline Summary

1. **Model Selection:** Choose a model (linear, polynomial, or regularized regression).
2. **Loss Function:** Define a loss function (e.g., least squares with/without regularization).
3. **Optimization:** Use methods such as closed-form solutions, gradient descent, SGD, or mini-batch SGD.
4. **Evaluation:** Assess performance with cross-validation and test splits.
5. **Bias-Variance Tradeoff:** Manage the tradeoff using regularization and model complexity choices.

*This document consolidates key topics—from MLE and regression to MAP estimation and gradient descent methods—into a comprehensive reference in Markdown format.*