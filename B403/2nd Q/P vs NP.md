**Decision problem** - binary output problem
**P** - polynomial time ($O(n^k$), for some constant $k$), a group of decision problems -
- The **solving** part of a decision problem can be done in poly time
	- "tractably solvable"
- No need to have a **certifier** because you can just run this solver
**NP** - nondeterministic poly time, a group of decision problems -
- The **certification** part of a decision problem output can be done in poly time
- Finding the solution **certificate** might be hard (exponential time worst case) but checking is easy (poly time)

If P=NP, every problem with an efficient certifier also has an efficient solver
- can be generalized to saying a problem is P=NP
If P!=NP, widely believed, verification is easier than creation, we can prove things efficiently but not always find solutions efficiently
**3-SAT**
CNF composed of 3 variable clauses
NP-complete
- Hardest problems in the NP class
Almost every other NP problem reduces to 3-SAT, so solving that would solve all those other problems in poly time
