## Merge Sort
$$[4, 5, 2, 12, 8, 9, 10, 3]$$
$$[4, 5, 2, 12] \quad [8, 9, 10, 3]$$
$$[4, 5] \quad [2, 12] \quad \quad [8, 9] \quad [10, 3]$$
$T(n)$ - worst-case running time of Merge Sort with $n$ elements
- Divide - $O(1)$
- Sort - $2T(\frac{n}{2})$
- Merge - $O(n)$

$T(n) = 2 T\left(\frac{n}{2}\right)+ T_{\text{merge}}(n)$
- If $T_{\text{merge}} = n^2$, then $\Omega(n^2)$, which is no better then a trivial sort
- The important part of Divide and Conquer Algorithms is how the sub problems are merged
- For merging efficient , have pointers starting at beginning of the two arrays, compare the two values of the pointers and append to the return array the lower value, increment that arrays pointer, and compare again
	- $O(n)$

**Merge Sort Running Time Recursive Formula**
$T(n) = 2T\left(\frac{n}{2}\right)+ O(n)$
- First term is for sorting
- Second term is dividing + merging
- **Formula after recursion $\rightarrow$ iteration**
	- $T(n) = 2^{k}\frac{n}{2^{k}} + \dots$ **TODO: SEE SLIDES**

**Recursion Analysis** -
$T(n) = 2T\left(\frac{n}{2}\right)+ O(n) + O(1)$
Assuming $n=2^m$
$$T(n) \leq 2 T\left(\frac{n}{2}\right)+ cn \quad \text{(reccursion formula)}$$
$$\leq 2\left(2T\left(\frac{n}{4}\right) + c \frac{n}{2}\right)+ cn \quad \text{expand } T(\frac{n}{2}) \text{ from previous level}$$
$$= 4T(\frac{n}{4}) + 2cn$$
$$\leq 4 \left( 2 T\left(\frac{n}{8}\right)+ c \frac{n}{4} \right) + 2cn$$
$$= 8T\left(\frac{n}{8}\right)+ 3cn$$
$$\vdots$$
$$ \leq 2^{m}T\left(\frac{n}{2^{m}}\right)+ mcn$$
$$= nT(1) + c n \log n$$At level $k$, $2^k$ sub problems, need $2^k$ merging of two arrays of size $\frac{n}{2^{k+1}}$ costing $2^{k}\times c\frac{n}{2^k}=cn$ 

**KEY** - divide + merge need to be at least $O(n)$ to get a final running time of $O(n\log n)$

## Counting Inversion/Sort and Count
Given lists of ranking, each list $a_{1}, a_{2}, \dots, a_{n} \in \{1,2,\dots,n \}$
Goal, count how many swaps must be made between a pairing of lists
Do the same thing as merge sort but when merging, if there is an inversion (two elements need swapped) inversions++

## Closest Pair of Points
Goal, given sorted list of n dimension points: $\{ (x_{1}, y_{1}), \dots (x_{n}, y_{n}) \} \in P$
- Remember - sort is just a possible result of divide and conquer algorithms, not a true functional step, in this case it is a preprocessing step where you must sort by each dimension
**Algorithm** -
Find mid given first dimension, split it into a $R_P$ and $L_P$
Find $d_{L}$ and $d_R$ = $\text{distance}(L_P)$, $\text{distance}(R_P)$
If given $x$ is within $(L_{P}, median)$ recurse on $L_P$
If given $x$ is within $(R_P, median)$ recurse on $R_P$
Else calculate all the points that are within the $x - mid$ and recurse on this