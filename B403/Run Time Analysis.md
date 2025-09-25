#### Big O
Gives an upper bound on the running time of an algorithm

We say a function $f(n)$ is $O(g(n))$ as $n \rightarrow \infty$ if there exists a constant $c>0$ such that $|f(n)| \leq c g(n)$ for all $n$ larger than a threshold $n_0$. Equivalently, the following condition must hold

$$
\limsup _{n \rightarrow \infty} \frac{|f(n)|}{g(n)}<\infty
$$
**Trivial Case** - $O(\inf)$

Example:
a) If $f(n)=3 n^2+2 n+5$ then $f(n)=O\left(n^2\right)$
b) If $f(n)=2 n+5$ then $f(n)=O\left(n^2\right)$ and $O(n)$
c) If $f(n)=4 n^3+5$ then $f(n) \neq O\left(n^2\right)$


#### Big $\Omega$
Gives a lower bound on the running time of an algorithm

We say a function $f(n)$ is $\Omega(g(n))$ as $n \rightarrow \infty$ if there exists a constant $c>0$ such that $|f(n)| \geq c g(n)$ for all $n$ larger than a threshold $n_0$. Equivalently, the following condition must hold

$$
\limsup _{n \rightarrow \infty} \frac{|f(n)|}{g(n)}>0
$$
**Trivial Case** - $\Omega(0)$

Example:
a) If $f(n)=3 n^2+2 n+5$ then $f(n)=\Omega\left(n^2\right), \Omega(n), \Omega(1)$.
b) If $f(n)=2 n+5$ then $f(n) \neq \Omega\left(n^2\right)$

#### Big $\Theta$

Gives a more accurate estimate of the running time. It considers both an upper bound and a lower bound.

We say a function $f(n)$ is $\Theta(g(n))$ as $n \rightarrow \infty$ if there exist two constants $c_1>0$ and $c_2>0$ such that $c_1 g(n) \leq|f(n)| \leq c_2 g(n)$ for all $n$ larger than a threshold $n_0$. Equivalently, the following condition must hold

$$
f(n)=O(g(n)) \quad \text { and } \quad f(n)=\Omega(g(n))
$$
Example:
a) If $f(n)=3 n^2+2 n+5$ then $f(n)=\Theta\left(n^2\right)$.
b) If $f(n)=2 n+5$ then $f(n)=\Theta(n)$.

For every function $f=\Theta(f)$, every function is big theta of itself (at least)

#### Summary
$f(n)=n^2+2 n+1$
a) $f(n)=\Theta\left(n^2\right)$
b) $f(n)=O\left(n^3\right)$ or $O (n^2)$
c) $f(n)=\Omega(20 n)$

Notice that the constant $c$'s must be positive

#### Properties

**Transitivity**
- If $f=O(g)$, and $g=O(h)$, then $f=O(h)$
	- Holds for each notation, not just big O
**Additivity**
- If $f=O(h)$, and $g=O(h)$, then $f + g = O(h)$
	- Holds for each notation
- Given: $f=O(h)$, and $g=\Omega(h)$, then $f+g=\Omega(h)$
	- You cannot determine the upper bound of g, but you can determine the lower
- If $f=\Omega(h_1)$, and $g=\Omega(h_2)$, then $f+g = \Omega(h_1 + h_2)$
	- -If given $h_1 = O(h_2)$, then $f+g=\Omega(h_2)$
**Note**: The constants $c$ change but the notations are still the same

If $f_1 = O(n^2), f_2=O(n), f_3=\Omega(n \log(n))$, conclude these together run at $\Omega(n \log(n))$, cannot say anything about $O()$?

if $f_1=O(n^2), f_2=\Omega(n^3)$, conclude these together run at least $\Omega(n^3)$, cannot say anything about $O()$

If $g(n) = O(f(n))$ then $f(n) + g(n) = \Theta(f(n))$

$f(n) = O(f(n))$ and $\Omega(f(n))$ and $\Theta(f(n))$

$\log_b (n) = O(n^k)$ for base $b>1$ and any degree $k>0$
- Note: $k>0$ so $k$ can be less than one and be in square root time with $k=\frac{1}{2}$

$O(\log n^k) = O(k \log n) = O(\log n)$

If $p(n)$ and $q(n)$ are two positive functions and $p = \Theta(h)$ and $q = \Theta(r)$ then $\frac{p}{q} = \frac{\Theta(h)}{\Theta(r)}$
**Proof**:
$c'h \leq p \leq ch$
$d'r \leq q \leq dr$
$\frac{p}{q} \leq \frac{ch}{q} \leq \frac{ch}{d'r} = \frac{c}{d'} (\frac{h}{r})$
$\frac{p}{q} \leq \frac{c'h}{q} \leq \frac{c'h}{dr} = \frac{c'}{d} (\frac{h}{r})$

#### Analysis with Summations

**Reminder** - $\sum_{i=1}^k i = \frac{k(k+1)}{2}$

$T$ = True running time
```python
def Alg(n):
	for i in range(n):
		func_3(i) # T=i log i
```
$T_{Alg} = \sum_{i=1}^n i \log i$

**Finding Big O**
$O(\text{\#Steps} \times \text{Largest})$
**Proof**:
$T_{Alg} = \sum_{i=1}^n i \log i$
$\leq \sum_{i=1}^n n \log n$
$= n \times n \log n$
$\text{Therefor, } O(n \times n \log n)$

**Finding Big $\Omega$**
- Approach 1
	- $\Omega (\text{\#Steps} \times \text{Smallest})$
		- $T(n) = \sum_{i=1}^n i$
			- $= \Omega (n)$
- Approach 2
	- $\Omega (\text{Largest})$
		- $T(n) = \sum_{i=1}^n i$
			- $= \Omega (n)$
- Approach 3
	- $\Omega (\text{\#Steps} \times \text{Middle Step})$
		- $T(n) = \sum_{i=1}^n i$
			- $= \Omega (n^2)$
		- $T(n) = \sum_{i=1}^n i \log i$
			- $= \Omega (n \times \frac{n}{2} \log \frac{n}{2})$
			- $= \Omega (n^2 \log n)$

**Example**:
$\sum_{i=1}^n \sum_{j=1}^{i^2} 1$
$O(n \times n^2)$
$\Omega (n \times \frac{n^2}{2}) = \Omega (n \times n^2)$

#### Common Algorithmic Running Times

| Running Time | Big O Notation |
| ------------ | -------------- |
| Constant     | O(1)           |
| Logarithmic  | O(log n)       |
| Linear       | O(n)           |
| Loglinear    | O(n log n)     |
| Quadratic    | O(n²)          |
| Polynomial   | O(nᵏ)          |
| Exponential  | O(2ⁿ)          |
| Factorial    | O(n!)          |
