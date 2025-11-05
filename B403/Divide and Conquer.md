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
$$= nT(1) + c n \log n$$
At level $k$, $2^k$ sub problems, need $2^k$ merging of two arrays of size $\frac{n}{2^{k+1}}$ costing $2^{k}\times c\frac{n}{2^k}=cn$ 

What if $n$ is not a power of two, (there are no trivial base cases)
$T(n) \leq T\left(\lfloor \frac{n}{2} \rfloor\right)+ T\left(\lceil \frac{n}{2} \rceil \right)+ cn$
- Base case ($n=1$)
- Induction Hypothesis - assume true for $n=1,2,\dots,n-1$
- Let $n_{1}= \lfloor \frac{n}{2} \rfloor, n_{2}= \lceil \frac{n}{2} \rceil$
- $T(n) \leq T(n_{1)}+ T(n_{2)}+ cn$
-  
- $\log n_{1}= \log \lfloor \frac{n}{2} \rfloor$
- $n_{1}= 2^{\log \lfloor \frac{n}{2} \rfloor}$
- $\leq 2^{\log \frac{n}{2}}$
- $= \frac{n}{2}$
- $=> \log n_{1} \leq \log \frac{n}{2}$
- Can do similar for $n_2$




**KEY** - divide + merge need to be at least $O(n)$ to get a final running time of $O(n\log n)$
