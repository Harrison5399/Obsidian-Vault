P - all problems that can be solved in polynomial time
NP - all problems that can be checked in polynomial time

## Subset Sum

Brut force - $O(n2^n)$

Dynamic programming -
- Given $\{ x_{1}, x_{2}, \dots, x_{n} \}, T$
- Build tree that incudes/excludes $x_i$
- Left (exclude $x_i$) - $\{ x_{1}, x_{2}, \dots, x_{n} \} - \{x_{1}\}, T$
- Right (include $x_i$) - $\{ x_{1}, x_{2}, \dots, x_{n} \} - \{ x_i \}, T - x_i$
- When $T = 0$ - trivial case, return true
- When $T < 0$ - trivial case, return false, but keep searching for true
- When $i > n$ - trivial case, return false
	- This is breaking the problem down into a bunch of trivial cases
- Running time - $O(2^n)$, generating a tree with height = $n$ and each node splits 2 times
- Recursion formula - $T(n) = 2T(n-1) + O(1)$
	- Merge and divide is $O(1)$ because there is none of that
	- Exponential because first term is linear

Notation -
- Given - $\{ 3, 4, 5, 2 \}, T=9$
- $(k, R)$  - $\{x_{k}, \dots, x_{n}\}$, target value $R$
- $(1, 9)$ - $\{ 3, 4, 5, 2 \}, T=9$
- $(2, 6)$ - $\{ 4, 5, 2 \}, T=6$
- **Note** - 1 based indexing

#### Using Memoization/Caching
Use a $(n+1) \times (T+1)$ matrix, reserving 0 indices for trivial cases
- Starting at $(1, T)$, can reference this value for any repeated values 
- Running time with this is $O(nT)$
- But this is still not actually linear because running time is a function of **problem size** in number of bits
	- As $n$ increases linearly, the number of bits to store $T$ increases periodically exponentially, therefore, if you define $T$ as a 10 bit int you get $O(n2^{10})$ with a more general definition as $O(n2^{\log T})$

**Problem with negative numbers** -
When doing algorithm, T will become very large
## Knapsack Problem
Extension of the subset sum problem
Consider a backpack with capacity $W$ with $n$ objects with weights $w_{i}> 0$ and values $v_{i}>0$
**Goal** - maximize the total value of the items in the backpack while not exceeding the weight limit

## Sequence Alignment
Comparing $X^{m}=x_{1}, x_{2}, \dots, x_m$ with $Y^{n}=y_{1}, y_{2}, \dots, y_n$
- Each $x_i$ can be paired with $y_j$ or no pair (gap)
- The order of the letters must remain unchanged
- If $(x_{i}, y_{j})$ and $(x_{i'}, y_{j'})$ are two pairs, if $i < i'$ then it must be that $j<j'$

**Edit Distance** -
Minimum amount of changes needed to one word, to get the other
- oc**ur**r**ance-**
- oc**cu**r**renc**e
- $a_{u,c}+ a_{r,u}+a_{a,r}+a_{n,e} + a_{c,n}+a_{e,c}+\delta$
- **a** - mismatch penalties
- **$\delta$** - gap penalties from both words 

**Algorithm** - 
Given - $X^{m}, Y^{n}$
Creates a node with 3 sub problems -
- $X^{m-1}, Y^{n-1}$
	- Add $\alpha_{X_{m}, Y_{n}}$
- $X^{m-1}, Y^{n}$
	- Add $\delta$
- $X^{m}, Y^{n-1}$
	- Add $\delta$

```pseudo
OPT(i, j):
	if i == 0:
		return j * \delta
	if j == 0:
		return i * \delta
	return min(
		\alpha_{x_i, y_i} + OPT(i-1, j-1),
		\delta + OPT(i-1, j),
		\delta + OPT(i, j-1)
	)
```

For caching, use an $m \times n$ matrix, start solving at point $(m,n)$

Running time - $O(nm)$
Space complexity - $O(nm)$
- Check book for $O(n + m)$ implementation (chapter 6.7)

