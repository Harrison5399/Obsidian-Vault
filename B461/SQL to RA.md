
**SQL to SQL Translation**
- Eliminate set predicates
	- `IN` `ALL` `SOME` `ANY` `EXISTS` are set predicates, not `EXCEPT`
- Eliminate `WHERE` conditions
	- Replace the `WHERE` conditions with selection or joins, or decompose them into more basic components with union, intersection or set difference. 

**SQL to RA Translation**
- Straightforward after the above steps

---

#### WHERE condition Decomposition

**$\pi$ distributes over $\cup$**
- $\pi_L (E_1 \cup E_2) = \pi_L(E_1)\cup\pi_L(E_2)$
 - $\pi_L (\sigma_{C_1 \lor C_2} (E)) = \pi_L(\sigma_{C_1}(E) \cup \sigma_{C_2}(E)) = \pi_L (\sigma_{C_2}(E)) \cup \pi_L(\sigma_{C_2}(E))$

**$\pi$ does NOT distribute over $\cap$**
- $\pi_L(E_1 \cup E_2) \subseteq \pi_L(E_1)\cap\pi_L(E_2)$
- $\pi_L(\sigma_{C_1\land C_2}(E) = \pi_L(\sigma_{C_1}(E) \cap \sigma_{C_2}(E)) \subseteq \pi_L(\sigma_{C_1}(E)) \cap \pi_L(\sigma_{C_2}(E))$
- Example - 
	- Given - $\pi_a (\sigma_{b=1\land c=1}(R))$
	- Correct - $\pi_a (\sigma_{b=1}(R) \cap \sigma_{c=1}(R))$
	- Incorrect - $\pi_a(\sigma_{b=1}(R))\cap\pi_a(\sigma_{c=1}(R))$

**$\pi$ does NOT distribute over $-$**
- $\pi_L(E_1-E_2) \supseteq \pi_L(E_1)-\pi_L(E_2)$
- $\pi_L(\sigma_{\neg C}(E) = \pi_L(E - \sigma_C(E)) \supseteq \pi_L(E) - \pi_L(\sigma_C(E))$
	- Example - 
		- Given - $\pi_a(\sigma_{\neg(b=1)}(R))$
		- Correct - $\pi_a(R - \sigma_{b=1}(R))$
		- Incorrect - $\pi_a(R) - \pi_a(\sigma_{b=1}(R))$

**OR in WHERE clause**
```sql
SELECT L(t_1, ..., t_n)
FROM R_1 t_1, ..., R_n t_n
WHERE C_1(t_1, ..., t_n) OR C_2(t_1, ..., t_n)

-- BECOMES

SELECT L(t_1, ..., t_n)
FROM R_1 t_1, ..., R_n t_n
WHERE C_1(t_1, ..., t_n)
UNION
SELECT L(t_1, ..., t_n)
FROM R_1 t_1, ..., R_n t_n
WHERE C_2(t_1, ..., t_n)
```

**AND in WHERE clause**
```sql
SELECT L(t_1, ..., t_n)
FROM R_1 t_1, ..., R_n t_n
WHERE C_1(t_1, ..., t_n) AND C_2(t_1, ..., t_n)

-- BECOMES

SELECT L^q(t_1, ..., t_n)
FROM (
	SELECT t_1.*, ..., t_n.*
	FROM R_1 t_1, ..., R_n t_n
	WHERE C_1(t_1, ..., t_n)
	INTERSECT
	SELECT t_1.*, ..., t_n.*
	FROM R_1 t_1, ..., R_n t_n
	WHERE C_2(t_1, ..., t_n)
) q
```
- `L^q(t_1, ..., t_n)` represents the components of t_1, ..., t_n in L that are renamed as q from the subquery

**NOT in WHERE clause**
```sql
SELECT L(t_1, ..., t_n)
FROM R_1 t_1, ..., R_n t_n
WHERE NOT C(t_1, ..., t_n)

-- BECOMES

SELECT L^q(t_1, ..., t_n)
FROM (
	SELECT t_1.*, ..., t_n.*
	FROM R_1 t_1, ..., R_n t_n
	EXCEPT
	SELECT t_1.*, ..., t_n.*
	FROM R_1 t_1, ..., R_n t_n
	WHERE C(t_1, ..., t_n)
) q
```

**AND NOT in WHERE clause**
```sql
SELECT L(t_1, ..., t_n)
FROM R_1 t_1, ..., R_n t_n
WHERE C_1(t_1, ..., t_n) AND NOT C_2(t_1, ..., t_n)

-- BECOMES

SELECT L^q(t_1, ..., t_n)
FROM (
	SELECT t_1.*, ..., t_n.*
	FROM R_1 t_1, ..., R_n t_n
	WHERE C_1(t_1, ..., t_n)
	EXCEPT
	SELECT t_1.*, ..., t_n.*
	FROM R_1 t_1, ..., R_n t_n
	WHERE C_2(t_1, ..., t_n)
) q

-- OR

SELECT L^q(t_1, ..., t_n)
FROM (
	SELECT t_1.*, ..., t_n.*
	FROM R_1 t_1, ..., R_n t_n
	WHERE C_1(t_1, ..., t_n)
	EXCEPT
	SELECT t_1.*, ..., t_n.*
	FROM R_1 t_1, ..., R_n t_n
	WHERE C_1(t_1, ..., t_n) AND C_2(t_1, ..., t_n)
) q
```

#### Eliminating Set Predicates

**EXISTS in WHERE clause**
```sql
SELECT L(t_1, ..., t_n)
FROM R_1 t_1, ..., R_n t_n
WHERE EXISTS (
	SELECT 1
	FROM S_1 u_1, ..., S_m u_m
	WHERE C(u_1, ..., u_m, t_1, ..., t_n)
)

-- BECOMES

SELECT DISTINCT L(t_1, ..., t_n)
FROM R_1 t_1, ..., R_n t_n, S_1 u_1, ..., S_m u_m
WHERE C(u_1, ..., u_m, t_1, ..., t_n)
```
- `DISTINCT` is important here

**NOT EXISTS in WHERE clause**
```sql
SELECT L(t_1, ..., t_n)
FROM R_1 t_1, ..., R_n t_n
WHERE NOT EXISTS (
	SELECT 1
	FROM S_1 u_1, ..., S_m u_m
	WHERE C(u_1, ..., u_m, t_1, ..., t_n)
)

-- BECOMES

SELECT DISTINCT L^q(t_1, ..., t_n)
FROM (
	SELECT t_1.*, ..., t_n.*
	FROM R_1 t_1, ..., R_n t_n
	EXCEPT
	SELECT t_1.*, ..., t_n.*
	FROM R_1 t_1, ..., R_n t_n, S_1 u_1, ..., S_m u_m
	WHERE C(u_1, ..., u_m, t_1, ..., t_n)
) q
```

**AND NOT EXISTS in WHERE clause**
```sql
SELECT s.sid
FROM Student s
WHERE s.sname = 'Ann' AND
	NOT EXISTS (
	SELECT 1
	FROM Enroll e
	WHERE e.sid = s.sid AND e.grade = 'A'	
)

-- BECOMES

SELECT q.sid
FROM (
	SELECT s.sid, s.sname
	FROM Student s
	WHERE s.sname = 'Ann'
	EXCEPT
	SELECT s.sid, s.sname
	FROM Student s, Enroll e
	WHERE e.sid = s.sid AND e.grade = 'A'
) q

-- OR

SELECT q.sid
FROM (
	SELECT s.sid, s.sname
	FROM Student s
	WHERE s.sname = 'Ann'
	EXCEPT
	SELECT s.sid, s.sname
	FROM Student s, Enroll e
	WHERE s.sname = 'Ann' AND e.sid = s.sid AND e.grade = 'A'
) q
```

**IN in WHERE clause**
```SQL
SELECT L(t_1, ..., t_n)
FROM R_1 t_1, ..., R_n t_n
WHERE (t_j_1.A_j_1, ..., t_k_k.A_j_k) IN (
	SELECT u_l_1.B_m_1, ..., u_l_k.B_m_k
	FROM S_1 u_1, ..., S_m u_m
	WHERE C(u_1, ..., u_m, t_1, ..., t_n)
)

-- BECOMES

SELECT DISTINCT L(t_1, ..., t_n)
FROM R_1 t_1, ..., R_n t_n, S_1 u_1, ..., S_m u_m
WHERE C(u_1, ..., u_m, t_1, ..., t_n) AND
	(t_i_1.A_j_1 = u_l_1.B_m_1 AND ... AND t_i_k.A_j_k = u_l_k.B_m_k)
```

**NOT IN in WHERE clause**
```sql
SELECT L(t_1, ..., t_n)
FROM R_1 t_1, ..., R_n t_n
WHERE (t_i_1.A_j_1, ..., t_i_k.A_j_k) NOT IN (
	SELECT u_l_1.B_m_1, ..., u_l_k.B_m_k
	FROM S_1 u_1, ..., S_m u_m
	WHERE C(u_1, ..., u_m, t_1, ..., t_n)
)

-- BECOMES

SELECT L^q(t_1, ..., t_n)
FROM (
	SELECT t_1.*, ..., t_n.*
	FROM R_1 t_1, ..., R_n t_n
	EXCEPT
	SELECT t_1.*, ..., t_n.*
	FROM R_1 t_1, ..., R_n t_n, S_1 u_1, ..., S_m u_m
	WHERE C(u_1, ..., u_m, t_1, ..., t_n) AND
		(t_i_1.A_j_1 = u_l_1.B_m_1 AND ... AND t_i_k.A_j_k = u_l_k.B_m_k)
) q
```

**$\theta$ SOME in WHERE clause**
```sql
SELECT L(t_1, ..., t_n)
FROM R_1 t_1, ..., R_n t_n
WHERE t_i_1.A_j_1 \theta SOME (
	SELECT u_l_1.B_m_1
	FROM S_1 u_1, ..., S_m u_m
	WHERE C(u_1, ..., u_m, t_1, ..., t_n)	
)

-- BECOMES

SELECT DISTINCT L(t_1, ..., t_n)
FROM R_1 t_1, ..., R_n t_n, S_1 u_1, ..., S_m u_m
WHERE C(u_1, ..., u_m, t_1, ..., t_n) AND
	(t_i_1.A_j_1 \theta u_l_1.B_m_1)
```

**$\theta$ ALL in WHERE clause**
```sql
SELECT L(t_1, ..., t_n)
FROM R_1 t_1, ..., R_n t_n
WHERE t_i_1.A_j_1 \theta ALL (
	SELECT u_l_1.B_m_1
	FROM S_1 u_1, ..., S_m u_m
	WHERE C(u_1, ..., u_m, t_1, ..., t_n)
)

-- BECOMES

SELECT L^q(t_1, ..., t_n)
FROM (
	SELECT t_1.*, ..., t_n.*
	FROM R_1 t_1, ..., R_n t_n
	EXCEPT
	SELECT t_1.*, ..., t_n.*
	FROM R_1 t_1, ..., R_n t_n, S_1 u_1, ..., S_m u_m
	WHERE C(u_1, ..., u_m, t_1, ..., t_n) AND
		NOT (t_i_1.A_j_1 \theta u_l_1.B_m_1)
) q
```

#### WHERE decomposed to FROM using selection and join operations


