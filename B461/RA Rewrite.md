
Push down select $\sigma$

#### Notation
- $E$ denotes an RA expression and $A_E$ denotes its schema (set of attributes)
- $F$ denotes an RA expression and $A_F$ denotes its schema (set of attributes)
- $C$ is a condition and $A_C$ denotes the set of attributes that occur in $C$
- $L$ denotes an attribute list and $A_L$ denotes the set of attributes in $L$
- $A$ means schema/attributes

#### Definitions

**RA**
- $E \cup F$
	- with $A_E = A_F$ (schema of E = schema of F)
- $E \cap F$
	- with $A_E = A_F$
- $E-F$
	- with $A_E = A_F$
- $\sigma_C(E)$
	- with $A_C \subseteq A_E$
- $\pi_L(E)$
	- with $A_L \subseteq A_E$
- $E \times F$
	- with $A_E \cap A_F = \emptyset$
- $E \bowtie_C F$
	- with $A_E \cap A_F = \emptyset$ and $A_C \subseteq (A_E \cup A_F)$
- $E \bowtie F$
- $E \semijoin F$
- $E \antijoin F$

**Conditions**
- $A \s \theta \s a$ 
	- with $A$ an attribute, $a$ a constant and $\theta$ one of $=, \not =, <, \leq, >, \geq$ 
- $A \s \theta \s B$
	- with $A$ and $B$ attributes
- $C_1 \land C_2$
	- with $C_1$ and $C_2$ conditions
- $C_1 \lor C_2$
- $\neg C$
- $(C)$

To prove $E = F$ you must show that $E \subseteq F$ **and** $F \subseteq E$
- $A \cap (B \cup C) = (A \cup B) \cap (A \cup C)$
	- $A \cap (B \cup C) \subseteq (A \cup B) \cap (A \cup C)$
	- $(A \cup B) \cap (A \cup C) \subseteq A \cap (B \cup C)$

**Union $\cup$, Intersect $\cap$, Difference $-$**
- $E - (E-F) = E\cup F$
	- Double complementation of F relative to E
- $E - (E - F) = F$
	- When $E \supseteq F$
- $E-(F \cap G) = (E-F)\cup(E-G)$
	- De Morgan
- $E-(F \cup G) = (E-F) \cap (E-G)$
	- De Morgan
- $E \cap (F \cup G) = (E \cap F) \cup (E \cap G)$
	- Distribution
- $E \cup (F \cap G) = (E \cup F) \cap (E \cup G)$
	- Distribution
- $E \cap E = E$
	- Idempotence
- $E \cap E = E$
	- Idempotence
- $\overline{A \cup B} \equiv \overline{A} \cap \overline{B}$
	- De Morgan
- $\overline{A \cap B} \equiv \overline{A} \cup \overline{B}$
	- De Morgan
- $E \cap F = F \cup E$
	- Commutativity
- $E \cup F = F \cup E$
	- Commutativity
- $E \cap (F \cap G) = (E \cap F) \cap G$
	- Associativity
- $E \cap (F \cap G) = (E \cap F) \cap G$
	- Associativity
- $E \cap (E \cup F) = E$
	- Absorption
- $E \cup (E \cap F) = E$
	- Absorption
- $E \cap (F - E) = \emptyset$
	- Relativized contradiction
- $E \cup (F - E) = E \cup F$
	- Relativized tautology
- $E \cup \emptyset = E$
	- Identity
- $E \cap \emptyset = \emptyset$
	- Domination
- $E \cap F = E \join F$

**Selection $\sigma$**
- $\sigma_{C_{1}\land C_{2}(E)}= \sigma_{C_1}(\sigma_{C_2}(E))$
	- Cascading
- $\sigma_{C_1}(\sigma_{C_{2}(E))}= \sigma_{C_2}(\sigma_{C_1}(E))$
	- Commutativity
- $\sigma_{C_{1}\land C_{2}(E)}= \sigma_{C_{1}}(E) \cap \sigma{C_2}(E)$
	- Boolean decomposition
- $\sigma_{C_{1} \lor C_{2}}(E)= \sigma_{C_{1}}(E)\cap \sigma_{C_2}(E)$
	- Boolean decomposition
- $\sigma_{\neg C} (E) = E - \sigma_C(E)$
	- Boolean decomposition
- $\sigma_{C} (E\cup F) = \sigma_C (E) \cup \sigma_{C}(F)$
- $\sigma_{C}(E \cap F) = \sigma_{C}(E) \cap \sigma_{C}(F) = \sigma_{C}(E) \cap F = E \cup \sigma_{C}(F)$
- $\sigma_{C}(E - F) = \sigma_{C}(E) - \sigma_{C}(F) = \sigma_{C}(E) - F$
- $\sigma_{C}(E \times F) = E \join_{C}F$
	- Definition of $\join_C$
- $\sigma_{C}(E\join F) = \sigma_{C}(E) \join F$
	- When $A_{C}\subseteq A_E$
- $= E \join \sigma_{C}(F)$
	- When $A_{C}\subseteq A_F$
- $= \sigma_{C}(E) \join \sigma_{C}(F)$
	- When $A_{C}\subseteq A_{E}\cup A_F$
- $\sigma_{C_{1}} (E \join_{C_{2}}F) = \sigma_{C_{1}}(E) \join_{C_{2}}F$
	- When $A_{C_{1}} \subseteq A_E$
- $=E \join_{C_{2}}\sigma_{C_{1}}(F)$
	- When $A_{C_{1}}\subseteq A_F$
- $=E \join_{C_{1}\land C_{2}}F$
	- Always
- $\sigma_{C}(E \semijoin F) = \sigma_{C}(E) \semijoin F$
- $\sigma_{C}(E\overline{\semijoin} F) = \sigma_{C}(E) \overline{\semijoin} F$

**Projection $\pi$**
- $\pi_{L}(E \cup F) = \pi_{L}(E) \cup \pi_{L}(F)$
- $\pi_{L}(E \cap F) \subseteq \pi_{L}(E) \cap \pi_{L}(F)$
	- **NOT** equivalent
- $\pi_{L}(E - F) \supseteq \pi_{L}(E) - \pi_{L}(F)$
	- **NOT** equivalent
- $\pi_{L}(\sigma_{C}(E)) = \sigma_{C}(\pi_{L}(E))$
	- when $A_{C}\subseteq A_L$
- $\pi_{L}(E) = E$
	- When the schema of $E$ corresponds precisely with $L$
- $\pi_{B, A} (E) \not = E$
	- If the schema of $E$ is $(A, B)$
	- Projection acts as a permutation in this context
- $\pi_{L_1}(\pi_{L_{2}}(E)) = \pi_{L_{1}} (E))$
- $\pi_{L}(E \cap F) \not = \pi_{L}(E) \cap \pi_{L}(F)$
	- $\pi$ does not distribute over $\join$
- $\pi_{L}(E \join_{C}F) = \pi_{L}(\pi_{A_{L_{E}}}(E) \join_{C}\pi_{A_{L_{F}}}(F))$
	- $A_{L_{E}}= A_{E}\cap (A_{L}\cup A_{C})$
		- Attributes of $E$ that are either in $L$ or used in $C$
	- $A_{L_{F}}=A_{F}\cap (A_{L}\cup A_{C})$
		- Attributes of $F$ that are either in $L$ or used in $C$
	- So you are keeping only the attributes used in the projection list $L$ and in the condition $C$, then finally projecting on the projection list $L$
	- **Remember** - $A$ represents the attributes not column values
	- **IMPORTANT RULE**
	- Attribute elimination or pushing projections down over joins
- $\pi_{L}(E \join_{E.B_{1}=F.B_{1}\land \dots \land E.B_{k}= F.B_{k}} F) = \pi_{L}(E\join F)$
	- Assuming $E$ and $F$ have overlapping attributes $B_{1}, \dots, B_{k}$
- $E \semijoin F = \pi_{A_{E}}(E \join F)$
- $E \semijoin F = E \join \pi_{A_{E}\cap A_{F}} (F)$
- $E \overline{\semijoin} F = E - (E \semijoin F)$

#### Optimization Example
- **Given**
	- $\pi_{sname}(\sigma_{S.sid=E.sid \land cno=2003}(S \times E))$
- **Optimization **
	- $\pi_{\text{sname}} \left( \sigma_{S.\text{sid} = E.\text{sid}} \left( \sigma_{\text{cno} = 2003} (S \times E) \right) \right)$
	- $\pi_{\text{sname}} \left( \sigma_{S.\text{sid} = E.\text{sid}} (S \times \sigma_{\text{cno} = 2003} (E)) \right)$
	- $\pi_{\text{sname}} \left( S \join_{S.\text{sid} = E.\text{sid}} \sigma_{\text{cno} = 2003} (E) \right)$
	- $\pi_{\text{sname}} \left( \pi_{\text{sname, S.sid}} (S) \join_{S.\text{sid} = E.\text{sid}} (\pi_{E.\text{sid}} (\sigma_{\text{cno} = 2003} (E)) \right)$
	- $\pi_{\text{sname}} \left( \pi_{\text{sname, sid}} (S) \join \pi_{\text{sid}} (\sigma_{\text{cno} = 2003} (E)) \right)$
	- $\pi_{\text{sname}} \left( \pi_{\text{sname, sid}} (S) \semijoin \pi_{\text{sid}} (\sigma_{\text{cno} = 2003} (E)) \right)$
