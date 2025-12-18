## Network Flow


## Max Flow
How much flow can we send from $s$ to $t$
Rules:
- **Capacity:** $f(e) < C(e)$
- **Conservation**: incoming flow == outgoing flow
**$c(e)$** - capacity at edge $e$
**$f(e)$** - current amount flow sending at edge $e$
#### Naive Greedy Algorithm
- Find a path from $s$ to $t$ where each edge has $f(e) < c(e)$
- Add to the flow of the path as much as possible
- Repeat until no paths left
This fails because there is no way to undo a bad decision and send flow through another path that it's needed
#### Ford-Fulkerson Algorithm
**Residual Graph** -
- Original edge $e = (u, v) \in E$
- "Undo" flow sent
	- $e = (u, v)$ and $e^{R}= (v, u)$
	- Residual capacity
		- $c_f(e) = \begin{cases} c(e) - f(e) & \text{if } e \in E \\ f(e^R) & \text{if } e^R \in E \end{cases}$
		- Shows how much more flow you can still push through an edge
**Algorithm** -
- While there exists some edge has residual capacity > 0
	- Augment - Add new flow to original edges, subtract new flow from residual edges
		- The new flow = original flow + maximum you can push through original edges (bottleneck)
If capacities and non-integer, not guaranteed to terminate
**Running Time** - $O(C(n+m))$
- $C = \max(c(e_{1}), \dots, c(e_{m}))$
	- There for $C$ scales exponentially
**Min-Cut Problem**
Goal find a cut that shows the minimum capacity of a flow
- Partition graph $V$ into $(A, B)$ so that $s \in A$ and $t \in B$
- Capacity of a cut - $\text{capacity}(A, B) = \sum_{e out of A} c(e)$
Flow value lemma - Left $f$ be any flow and let $(A. B)$ be any s-t cut, then the net flow sent across the cut is equal to the amount leaving s (because of conservation)
- $\sum_{e out of A} f(e) - \sum_{e in to A} f(e) = v(f)$
- Shows that max-flow $\leq$ min-cut 
Max-flow min-cut theorem - The value of the max flow is equal to the value of the min cut
- You must pass the min-cut as a bottle neck when doing max-flow so you will always be restricted to the min-cut capacity