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

## Knapsack Problem
check book
