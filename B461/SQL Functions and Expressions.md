
#### Expressions in SELECT clause
`SELECT sqrt(2), 'John'||'Smith', 2=3`
- Returns relation with square root of 2, `John` and `Smith` concatenated together, and false for `2=3`

```sql
SELECT EXISTS (SELECT S.Sid
				FROM Student S, Enroll E
				WHERE S.Major='CS' AND S.Sid=E.Sid
				);
```

"Find new employee salaries after an increase by 5%"
```sql
SELECT E.Eid, E.Salary*1.05 AS NewSalary
	FROM Employee E
```

"Report whether or not an employee has the lowest salary"
```sql
SELECT E.Eid, E.Salary <= ALL(SELECT E1.Salary
								FROM Employee E1) AS HasLowestSalary
	FROM Employee E
```

#### CASE expression
```sql
SELECT E.Eid,
	CASE WHEN E.Salary > 100000 THEN 'high'
		WHEN E.Salary < 10000 THEN 'low'
		ELSE 'medium'
	END AS SalaryRange
	
	FROM Employee E
```

#### Parameterized sub-queries
"Report whether or not a student takes a course in the department in which he or she majors in"
```sql
SELECT S.Sid, S.Major IN (SELECT C.Dept
							FROM Course C, Enroll E
							WHERE E.Sid=S.Sid AND E.Cno=C.Cno)
	FROM Student S
```
- What makes this parameterized is the fact that `Student S` is referenced in the subquery

#### Expressions in WHERE clause
Consider a relation of points in 2-dimensional space with the schema:
	`Point(Pid, X, Y)`

"Find the pairs of points that are within distance 3"
```sql
SELECT P1.Pid AS P1, P2.Pid AS P2
	FROM Point P1, Point P2
	WHERE sqrt(power(P1.X-P2.X, 2) + power(P1.Y-P2.Y, 2)) <= 3
```
- `sqrt(value)` and `power(value, power)` are PostgreSQL function


"Raise the salary of an employee by 5% provided that the raise is less than $1000"
```sql
-- Query of those who will have a raise of less than $1000
(SELECT E.Eid, E.Salary*1.05 AS NewSalary
	FROM Employee E
	WHERE E.Salary*0.05 < 1000)
UNION
-- Query of those who will have a raise of greather than equal to $1000	
(SELECT E.Eid, E.Salary AS NewSalary
	FROM Employee E
	WHERE E.Salary*0.05>=1000)
```

#### User-defined functions
"Define the increment-by-1 function"
```sql
CREATE FUNCTION increment (n INTEGER)
	RETURNS INTEGER AS
	$$
		SELECT n+1;
	$$ LANGUAGE SQL;

SELECT increment(5) AS Value;
```

"Distance function between two points"
```sql
CREATE FUNCTION distnace(x1 FLOAT, y1 FLOAT, x2 FLOAT, y2 FLOAT)
	RETURNS FLOAT AS
	$$
		SELECT sqrt(power(x1-x2, 2) + power(y1-y2, 2));
	$$ LANGUAGE SQL
```

#### Functions with output parameters
`OUT` parameters are useful to return multiple things, it returns as a tuple (or row like from a table)
```sql
CREATE FUNCTION sum_and_product(x int, y int, OUT sum int, OUT product int) AS
$$
	SELECT x+y, x*y;
$$ LANGUAGE SQL;

SELECT t.sum, t.product
FROM sum_and_product(3,4) t;
```

#### Types
```sql
CREATE TYPE edge AS (source INT, target INT);

CREATE FUNCTION printEdge(x INT, y INT) RETURNS edge AS
$$
    SELECT x, y;
$$ LANGUAGE SQL;

SELECT * FROM printEdge(1, 2);
SELECT source FROM printEdge(1,2);
```

#### Functions returning sets (relations)
```sql
CREATE FUNCTION sum_and_product()
RETURNS SETOF RECORD AS
$$
    SELECT P.x+:P.y, P.x*P.y FROM Pair P;
$$ LANGUAGE SQL;

-- OR RETURN AS TABLE:

CREATE FUNCTION sum_and_product()
RETURNS TABLE (sum INTEGER, product INTEGER) AS
$$
    SELECT P.x+:P.y, P.x*P.y FROM Pair P;
$$ LANGUAGE SQL;


```
- In the first query, without the `SETOF` keyword, if you just has `RETURNS RECORD`, the entire set of records will still be computed but it will only return one record instead of a set
