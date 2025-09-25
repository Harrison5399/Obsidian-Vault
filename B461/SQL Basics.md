#### DDL vs DDL
- **DDL** - Data Definition Language, Used to define and manage database structures, e.g., creating, altering, or dropping tables. Examples: `CREATE`, `ALTER`, `DROP`
- **DML** - Data Manipulation Language, Used to manipulate data within tables, e.g., inserting, updating, or deleting records. Examples: `INSERT`, `UPDATE`, `DELETE`, `SELECT`

#### Creating Databases & Tables

```SQL
CREATE DATABASE University;

\connect University

CREATE TABLE Student (  
	Sid TEXT NOT NULL,  
	Sname VARCHAR(30),  
	Major VARCHAR(15),  
	Byear INTEGER,  
	PRIMARY KEY (Sid)  
);

CREATE TABLE Course (  
	Cno TEXT NOT NULL,  
	Cname VARCHAR(20),  
	Dept VARCHAR(15),  
	PRIMARY KEY (Cno)  
);

CREATE TABLE Enroll (  
	Sid TEXT,  
	Cno TEXT,  
	Grade VARCHAR(2),  
	PRIMARY KEY (Sid, Cno),  
	FOREIGN KEY (Sid) REFERENCES Student(Sid),  
	FOREIGN KEY (Cno) REFERENCES Course(Cno)  
);

INSERT INTO Student VALUES('s1', 'John', 'CS', 1990);

INSERT INTO Student VALUES  
	('s1', 'John', 'CS', 1990),  
	('s2', 'Ellen', 'Math', 1995),  
	('s3', 'Eric', 'CS', 1990),  
	('s4', 'Ann', 'Biology', 2001);

\q
```
**Foreign Key** – In `Enroll`, `Sid` and `Cno` are foreign keys referencing `Student` and `Course`.
- **Cascading Deletions** – Deleting an entry from `Student` will also remove corresponding rows in `Enroll` if you add `ON DELETE CASCADE` to the foreign key.
- `ON DELETE RESTRICT` – Prevents deletion if referenced.
- `ON DELETE NO ACTION` (default) – Similar to restrict.

##### Useful Commands
- `\l` – Lists all databases
- `\d` – Lists all visible tables
- `\d [table_name]` – Shows schema of a table
- `DROP DATABASE [database_name]` – Removes a database
- `DROP TABLE [table_name]` – Removes a table

---
#### Basic Queries
`SELECT * FROM [table_name]` – Shows all entries in a table.

```sql
SELECT S.Sid, S.Sname  
FROM Student S  
WHERE S.Major = 'CS';
```
**Meaning:** Show the IDs and names of all students majoring in Computer Science.

``` SQL
SELECT S.Sid, S.Sname, E.Cno  
FROM Student S, Enroll E  
WHERE S.Sid = E.Sid AND E.Grade = 'B';
```
**Meaning:** Show the IDs, names, and course numbers of all students who earned a grade of B.

```SQL
SELECT DISTINCT s.major  
	FROM student s;
```
**Meaning:** List all unique majors in the Student table.

```SQL
SELECT s.sid AS identifier, s.sname AS name  
FROM student s;
```
**Meaning:** Show student IDs and names, renaming the columns as `identifier` and `name`.

```SQL
SELECT s.sid, s.sname  
	FROM student s  
	ORDER BY sname;
```
**Meaning:** Show students sorted alphabetically by name.

```SQL
SELECT s.sid, s.sname  
	FROM student s  
	ORDER BY RANDOM();
```
**Meaning:** Show students in a random order.

#### Subqueries
```SQL
SELECT s.sname, c.cno  
	FROM student s, 
	(
		SELECT e.sid, e.cno  
		FROM enroll e  
		WHERE e.grade = 'B'
	)  
	WHERE s.sid = c.sid;
```
**Meaning:** Show student names and course numbers for students who earned a grade of B.

```SQL
SELECT DISTINCT s.sid, s.sname  
	FROM student s, enroll e1, enroll e2  
	WHERE s.sid = e1.sid AND s.sid = e2.sid AND e1.cno <> e2.cno;
```
**Meaning:** Show IDs and names of students who are enrolled in more than one different course.
- `<>` means “not equal”.
- `DISTINCT` is required because a student could appear multiple times otherwise.

##### Set Operations

| Operation    | SQL Notation |
| ------------ | ------------ |
| Union        | UNION        |
| Intersection | INTERSECT    |
| Difference   | EXCEPT       |
```SQL
	(SELECT s.sid, s.sname  
	FROM student s  
	WHERE s.major = 'CS')  
UNION  
	(SELECT s.sid, s.sname  
	FROM student s  
	WHERE s.major = 'Math');
```
**Meaning:** Show IDs and names of students majoring in either CS or Math. Equivalent to using `OR`.

```SQL
SELECT s.sid, s.sname  
	FROM student s  
	WHERE s.major = 'CS' OR s.major = 'Math';
```
**Meaning:** Same as above, using `OR` instead of UNION.

```SQL
	(SELECT e.sid  
	FROM enroll e  
	WHERE e.cno = 'c1')  
INTERSECT  
	(SELECT e.sid  
	FROM enroll e  
	WHERE e.cno = 'c2');
```
**Meaning:** Show IDs of students enrolled in both course c1 and course c2.

```SQL
	(SELECT s.sid  
	FROM student s)  
EXCEPT  
	(SELECT e.sid  
	FROM enroll e);
```
**Meaning:** Show IDs of students who are not enrolled in any course.

- By default, these return sets (no duplicates) (set semantics).
- Use `UNION ALL`, `INTERSECT ALL`, `EXCEPT ALL` to return bags (with duplicates) (bag semantics).
   
##### IN Predicate
```SQL
SELECT DISTINCT e.sid  
	FROM enroll e  
	WHERE e.cno IN 
		(  
			SELECT c.cno  
			FROM course c  
			WHERE c.dept = 'CS'
		)  
);
```
**Meaning:** Show IDs of students enrolled in at least one course offered by the CS department.

```SQL
SELECT DISTINCT e.sid  
	FROM enroll e  
	WHERE e.cno NOT IN 
	(  
		SELECT c.cno  
		FROM course c  
		WHERE c.dept = 'CS'
	)
);
```
**Meaning:** Show IDs of students not enrolled in any CS department course.

```SQL
SELECT s.sid, s.sname  
	FROM student s  
	WHERE (s.sid, s.major) IN 
	(  
		SELECT e.sid, c.dept  
		FROM enroll e, course c  
		WHERE e.cno = c.cno
	)
);
```
**Meaning:** Show IDs and names of students whose major matches the department of at least one course they are enrolled in.

#### SOME Predicate
```SQL
SELECT DISTINCT e.sid  
	FROM enroll e  
	WHERE e.cno = SOME 
	(  
		SELECT c.cno  
		FROM course c  
		WHERE c.dept = 'CS'
	)  
);
```
**Meaning:** Show IDs of students enrolled in at least one course from the CS department. (`SOME` is equivalent to `IN`).

#### ALL Predicate
```SQL
SELECT p.pid  
	FROM person p  
	WHERE p.age <= ALL 
	(  
		SELECT p1.age  
		FROM person p1  
	)
);
```
**Meaning:** Show the person ID(s) of the youngest person(s), since their age is less than or equal to everyone else’s.

#### EXISTS Predicate
```SQL
EXISTS (  
	SELECT s.sid  
	FROM student s  
	WHERE s.major = 'CS'  
);
```
**Meaning:** Returns `TRUE` if there is at least one student majoring in CS.

```SQL
NOT EXISTS (  
	SELECT s.sid  
	FROM student s  
	WHERE s.major = 'CS'  
);
```
**Meaning:** Returns `TRUE` if there are no students majoring in CS.

```SQL
SELECT s.sid  
	FROM student s  
	WHERE EXISTS 
	(  
		SELECT e.cno  
		FROM enroll e  
		WHERE s.sid = e.sid
	)  
);
```
**Meaning:** Show IDs of students who are enrolled in at least one course.