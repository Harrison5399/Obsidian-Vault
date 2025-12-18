## Weighted Interval Scheduling
Regular interval scheduling but with weights, trying to create valid schedule with highest weight
**Basic Recursion Formula**
$\text{opt}(n) = \max \{ v_{n} + \text{opt}(p(n)), \text{opt}(n-1) \}$
- Does taking some option $n$ reward you more than not taking it?
- $p(n)$ - Latest non-overlapping job
	- With binary search, takes $O(n \log n)$
Use Memoization as there will be multiple calls of the same $\text{opt}(x)$, this turns an $O(2^n)$ into $O(n \log n)$

## Subset Sum
Given a set of numbers
Goal determine if a subset of these numbers adds up to a target value, say $T=9$
**Note** - NP-Complete, no poly time algorithm can solve this unless P=NP
Same idea as weighted interval scheduling, creating subsets and calculating sums based on to take or not to take some node in the graph

## Knapsack Problem
Extension of the subset sum problem,
- Instead of having a set target, you are just trying to maximize total numbers
- But each number has a weight with some given max weight you can exceed
$\text{opt}(n, W) = \max \{ \text{opt}(n-1, W), \text{opt}(n-1, W-w_{n}) + v_{n} \}$

## Sequence Alignment
**Edit Distance** - cost of an alignment
- Gap penalty - $\delta$
- Mismatch penalty $(x, y) : a_{x,y}$
	- Usually some constant for each pair of letters
	- If $x = y$ then give 0 penalty

| o   | c   | ==-== | u   | r   | r   | ==**a**== | n   | c   | e   |
| --- | --- | ----- | --- | --- | --- | --------- | --- | --- | --- |
| o   | c   | c     | u   | r   | r   | ==e==     | n   | c   | e   |
- $\delta + a_{c,e}$
**Recursion Formula**
$$ \text{opt}(i, j) = \begin{cases} j \delta & \text{if } i = 0 \\ i \delta & \text{if } j = 0 \\ \min \begin{cases} \alpha_{x_i y_j} + \text{opt}(i-1, j-1) \\ \delta + \text{opt}(i-1, j) \\ \delta + \text{opt}(i, j-1) \end{cases} & \text{otherwise} \end{cases} $$
Can also be done with Dijkstra to construct and traverse a similarly constructed tree as recursion