#### Undirected
$G = (V,E)$
$V = \text{Nodes}$
$E = \text{Edges}$

**Path** - Sequence of nodes $v_1, v_2, \dots, v_k$
**Simple Path** - A path with no reptation of nodes $\forall i,j \quad v_i \not = v_j$
**Cycle** - A path with $v_1 = v_k, \space k>2$
**Connected Graph** - If for any pair of nodes $(v, u)$ there exists a path connecting them
**Acyclic Graph** - If there exists no cycles

#### Tree
Acyclic Connected Graph

**Degree** - Given a node, returns number of edges connected
**Leaf** - Nodes with Degree of 1

###### Properties
- Any tree has a leaf, with $n \geq 2$
- Any tree with n nodes has exactly (n-1) edges
	- Base
		- True for $n=1$
	- Induction Hypothesis
		- Holds for $n=k+1$
		- From property 1, the (k+1) node tree has a leaf
		- Remove it so it will remove one edge
		- The remaining k nodes is still a tree because removing the leaf still keeps it acyclic and connected 
		- Continue this on the k nodes tree and you will get to the base tree of $k=n=1$ 
- Let $G$ be an undirected graph on $n$ nodes, any two of the following statements imply the third
	- $G$ is connected
	- $G$ is acyclic
	- $G$ has $n-1$ edges

#### BFS
###### Graph Representation
**Adjacency Matrix**
- $n$ by $n$ matrix $A = [A_{ij}]$
- $A_{ij} = 1$ if $(i,j)$ is an edge
- $A_{ij} = 0$ if there is no edge between $i, j$

Given $A$
- To check if ($i, j)$ is an edge takes $\Theta (1)$
- To list all edges takes $\Theta (n^2)$

**BFS with Adjacency Matrix** - $O(n^2)$
- Each layer takes O(n) and worst case n layers


**Claim** - Layer $L_j$ contains all nodes at distance exactly $j$ from starting node $s$
- Base case n=1:
	- The layer 0 only contains node $s$
- Induction hypothesis: assume for $\forall j \leq k$ $L_j$ has all nodes at distance $j$ from $s$
- Induction case n=k+1:
	- $L_{k+1} =$ Nodes that have an edge to some node in $L_k$
	- So nodes in $L_{k+1}$ are at most distance $k+1$
	- This node cannot be at distance less than $k+1$ from $s$, because if it were, it would already be in some $L_j$ for $j \leq k$ by the induction hypothesis. 
	- Thus, $L_{k+1}$ contains exactly the nodes at distance $k+1$ from $s$.

**Strong Induction** - used in the induction hypothesis, instead of saying assume something about $k$, assume something for everything up to $k$ 
- used above instead of 'suppose $L_k$ has all the nodes that are at distance $k$ from $s$'

There is a path from $s$ to $t$ if and only if $t$ appears in some layer

If $x,y$ are two nodes in the BFS tree and are connected by an $(x,y)$ then,
- either $x$ and $y$ belong to the same layer $L_i$ in BFS
- or they belong to a neighboring layers $L_i$ and $L_{i\pm}$
- prove this claim with contradiction

**Connect Component** - all nodes reachable from $s$

**Adjacency List**
- Storage is $O(n+m)$
	- Pointer to each node, $n$ nodes
	- The total length of the lists: $2m$, each edge appears twice
- More efficient representation as $m\leq n^2$
- Identifying all edges takes $\Theta (n+m)$
- Checking if $(u,v)$ is an edge takes $O(deg(u))$
- Normally represents outgoing edges, can also have another with incoming edges

**BFS with Adjacency List** - $O(n+m)$


#### DFS

**Claim** - Let $T$ be a DFS Tree, let $x$ and $y$ be nodes in $T$ and let $(x,y)$ be an edge of $G$ that is not and edge of $T$. Then one of $x$ or $y$ is an ancestor of the other

Running time of DFS is $O(n+m)$


#### DAG (Directed Acyclic Graph)

**Topological Order** - A labeling of the nodes as $v_1, v_2, \dots, v_n$ so that whenever there is an edge $(v_i, v_j)$ then it must be that $i<j$
- Not all directed graphs have a topological ordering, that is if it has a cycle, it has no topological order
- If a graph has a topological ordering, it must be a DAG

**Claim** - If G has a topological ordering, then G is a DAG, proof by contradiction or induction

**Claim** - If G is a DAG, then G has a node with no incoming edges, proof by contradiction
- If every node had an incoming edge then there would be a cycle

**Topological Order Algorithm**
1. Find a node $v$ with no incoming edges and place it first
2. Delete $v$ from $G$
	- $G - \{v\}$ must be a DAG as deleting cannot introduce a cycle
3. Recursively compute a topological ordering of $G - \{v\}$ and append this order after $v$
- O($n^2$) with adjacency list (of incoming edges), O($n^3$) with adjacency matrix




