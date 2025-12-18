#### 1
**A**
Given
$$T(n) = \sum_{i=1}^{\log_{3}n} T(\frac{n}{3^{i}}) + n$$
$$= T(\frac{n}{3})+ T(\frac{n}{9}) + \dots + T(1)+ n$$
With $T(1) = 0$
What is the $\Theta$
$$T(n/3)=T(n/9)+\dots+T(1)+\frac{n}{3}$$
$$T(n)=2T(n/3)+\frac{2}{3}n$$
$$T(n)=2^kT(\frac{n}{3^k})+\frac{2}{3}n+(\frac{2}{3})^2n+\dots+(\frac{2}{3})^kn$$
$$T(n)=2^{\log_3n}T(1)+n\sum\limits_{m=1}^{\log_3n}(\frac{2}{3})^m$$
Since $T(1)=0$, solving for geometric sum gives $\Theta(1), which means $\Theta(n)$
**B**
Suppose a dynamic programming algorithm creates an n × m memoization table and to  
compute each entry of the table it takes a minimum over at most m (previously computed) other  
entries. What would the running time of this algorithm be, assuming there is no other computations.
$$O(nm \times m) = O(nm^2)$$
#### 2
Consider finding the shortest path in a directed graph using a randomized algorithm. Suppose A is a randomized algorithm used to find the shortest path of a given graph G. Suppose we are guaranteed that the algorithm’s output is the shortest path with probability at least p ∈ (0, 1). However, p is not good enough for us. We want to find the shortest path with a higher probability, say (1 − δ), where δ > 0 is a small number.