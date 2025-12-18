## Las Vega Algorithm
Given a binary array of size $n$ where exactly half the elements are 0's and the other half is 1's
Goal, find index of any 1
**Naive Algorithm** - loop through all elements until you find a 1
- $O(n)$
**Las Vegas Algorithm** - select indices at random until you find a 1
- Worst case $O(\frac{1}{2^{k}})$
- $\Theta(1)$
## Monte Carlo Algorithm
Las Vegas algorithm with that will do at most $k$ number of searches
Does not guarantee to find the answer but terminates after at most $k$ integrations
At iteration $n$ of the Las Vegas/Monte Carlo algorithm, the probability of having found a valid answer at least once by the end of the step is $1-\frac{1}{2^n}$
$O(k)$
$\Theta(1)$
