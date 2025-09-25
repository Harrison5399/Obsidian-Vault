**View** - a virtual relation defined by a query

```sql
CREATE VIEW cs_course AS  
	SELECT c.cno, c.cname  
	FROM course c  
	WHERE c.dept = 'CS';
```
**cs_course**

| cno | cname |
| --- | ----- |
| c1  | Dbs   |
| c4  | AI    |

Once defined, views can be used as relations in queries
```sql
SELECT c.cname
FROM cs_course c;
```

Views may also be used to define other views
```sql
CREATE VIEW student_enrolled_in_cs_course AS  
	SELECT s.sid, s.sname, s.major, s.byear  
	FROM student s  
	WHERE s.sid IN 
		(SELECT e.sid  
		FROM enroll e  
		WHERE e.cno IN 
			(SELECT c.cno  
			FROM cs_course c));  
```

Views are used to modularize a complex query or table into simpler units

**Logical Data Independence** - Base tables can be expanded with new attributes and constraints, but a view dependent on the base table is independent and unchanged by these alteration

It may be better to restructure your main table as a view dependent on sub tables
- Replace the `student(sid, sname, major, byear)` with `student_info(sid, sname, byear)` and `student_major(sid, major)` creating a `student` view with: 
```sql
	CREATE VIEW student AS  
		SELECT s.sid AS sid, s.sname AS sname, s.byear AS byear, sm.major AS major 
		FROM student_info s, student_major sm  
		WHERE s.sid = sm.sid;
```

Trying to `DROP TABLE [table_name]` or `DROP VIEW [view_name]` but the table/view has dependents, the operation will not succeed. Add the `CASCADE` keyword to the end of the statement to delete it, also deleting its dependents.

Inserting into a view will insert `NULL` into any fields in the base tables that are not used in the view
```sql
INSERT INTO cs_course VALUES('c6', 'Networks');
-- Is equal to
INSERT INTO course VALUES('c6', 'Networks', NULL);
```

Deletions are relatively safe and deleting from a view will delete the entry from the base table

View queries are executed when they are called, meaning the views are not being updated real time as you insert into the base table, and also must be re-calculated every time they are called. 


**Materialized View** - views that are updated real time and precomputed
```sql
CREATE MATERIALIZED VIEW cs_course AS
	SELECT c.cno, c.cname
	FROM course c
	WHERE c.dept = 'CS';
```
`REFRESH MATERIALIZED VIEW cs_course;` - recomputes `cs_course` view

**Temporary Views**
```sql
WITH view_1 AS (SQL query 1),  
	view_2 AS (SQL query 2),  
	--...  
	view_n AS (SQL query n)  
	
	--SQL query that can use view_1, ..., view_n;
```

#### Recursive Views


#### Parameterized Views