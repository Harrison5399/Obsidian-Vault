
#### Interval Scheduling
- Each job $i$ has a start time $S(i)$ and a finish time $f(i)$
- **Greedy** - maximize with soonest finishing time $f(i)$

```psuedo
Sort jobs by finish times so that f(i_1) <= f(i_2) <= ... <= f(i_n)
A = \EmptySet
for j=1 to n{
	if (job j compatable with A) {
		A = A \Union {j}
	}
}
return A
```
- $O(n \log n)$ because of sorting, for loop runs in $O(n)$

Optimal solution is not unique
Let $O=\{j_{1}, j_{2}, \dots, j_{m}\}$ be an optimal set of selected jobs, $m$ is maximal
Let $A=\{i_{1}, i_{2}, \dots, i_{k}\}$ be the output of the Greedy Algorithm above

**Claim** Greedy algorithm guarantees that $f(i_{r}) \leq f(j_r)$ for all $r\leq j$
- Base case (r=1) -
	- $f(i_{1)}\leq f(j_1)$ because greed algorithm chooses the job with the soonest finishing time
- Induction Hypothesis - 
	- Assume $f(i_{r})\leq f(j_{r}$) for some $r\leq k$
	- $f(i_{r+1}) \leq f(j_{r+1})$ because $f(i_r)$ finishes at the same time or before $f(j_r)$ so any jobs compatible to be $j_{r+1}$ are also compatible to be $i_{r+1}$
	- $S(j_{r+1}) > f(j_{r}) \geq f(i_r)$  from IH


#### Dijkstra Algorithm

**Given** - weighted directed graph
**Goal** - Find shortest path

**Algorithm** - Doing BFS, sort next level of nodes to be enqueued by the distance from the start 

Basic implementation -
```psuedo
Let S be the set of explored nodes
	For each u \in S, we store a distnace d(u)
Initially S = {s} and d(s) = 0
While S != V
	Select a node v not \in S with at least one edge from S for which
		d'(v) = min_{e=(u,v) : u \in S} d(u) + l_e is as small as possible (make v be the shortest edge connecting to u)
	Add v to S and define d(v)=d'(v)
EndWhile
```
- Running time - $O(n \times m)$ = $O(n^3)$

Priority queue implementation - 
```pseudo
Set tentative(s) = 0 and tentative(v) = +\inf for all v != s
Let Q be a priority queue/heap over V with priority decreasing in tentative(v)
While Q is not empty
	Remove the vertex v of minimum tentative(v) from Q
	Set distance(v) = tentative(v)
	For each outgoing edge (v, w):
		Set tentative(w) = min(tenative(w), distance(v) + l(v,w))
		and change priority of w in Q accordingly
Return the distance labels
```
- Running time - $O((n+m) \log n)$
- Running time using a Fibonacci heap instead - $O(m + n \log n)$

This algorithm cannot have negative length edges, because once you consider a negative edge, it can decrease the total length of everything but this doesn't work in this greedy scenario 

#### Priority Queue Running Time
- Enqueue - $O(\log n)$
- Dequeue - $O(\log n)$
- Change Priority (update all priorities not change condition) - $O(\log n)$
