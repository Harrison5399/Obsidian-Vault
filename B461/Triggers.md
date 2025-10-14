
Trigger state changes -
- `INSERT`
- `DELETE`
- `UPDATE`

Trigger temporal modes when they are executed - 
- `BEFORE`
- `AFTER`
- `INSTEAD OF`

Trigger levels - 
- Row level (main level)
- Statement level

Applications - 
- Materialized views
- View updates
- Constraint verification
- Dynamic aggregation function values maintenance
	- For those aggregation functions that take long to compute use triggers instead
- Logging/auditing

## `BEFORE INSERT`
Consider an `INSERT` trigger on the relation `Student(sid, sname, major, byear)`
```sql
CREATE OR REPLACE FUNCTION insert_into_Student() 
	RETURNS TRIGGER AS 
	$$ 
	    BEGIN IF NEW.Major = 'CS' THEN 
	        INSERT INTO CS_Student VALUES (NEW.sid, NEW.sname, NEW.byear); 
	    END IF; 
	    RETURN NEW; 
	    END; 
	$$ LANGUAGE 'plpgsql’;
```
- `NEW` - variable holding the new database row for `INSERT`/`UPDATE` operations in row level triggers
- `OLD` - variable holding the old database row for `UPDATE`/`DELETE` operations in row level triggers

Consider this similar trigger function -
```sql
CREATE OR REPLACE FUNCTION insert_into_Student() 
	RETURNS TRIGGER AS 
		$$ 
		    BEGIN IF NEW.Major = 'CS' THEN 
		        INSERT INTO CS_Student VALUES (NEW.sid, NEW.sname, NEW.byear);
		    END IF; 
		    RETURN NULL; 
		    END; 
		$$ LANGUAGE 'plpgsql’;
```
- Because this is returns `NULL` instead of `NEW`, nothing is going to be added to the student table because the trigger mode is `INSERT` so it will insert whatever is returned by the trigger function
	- `CS_Student` is still updated 

**NOTE** - both of these examples are missing the `CREATE TRIGGER` function to actually make this trigger work

## `AFTER INSERT`
The insert will always succeed on the table before the trigger function executes (unlike `BEFORE INSERT`)
- A `RETURN NEW` statement will do nothing because the `NEW` base value has already been inserted
	- So these types of triggers typically return `NULL`

```sql
CREATE OR REPLACE FUNCTION insert_into_Student() 
	RETURNS TRIGGER AS 
		$$ 
		    BEGIN IF NEW.Major = 'CS' THEN 
		        INSERT INTO CS_Student VALUES (NEW.sid, NEW.sname NEW.byear); 
		    END IF; 
		    RETURN NULL; -- Equivalent with RETURN NEW END; 
		$$ LANGUAGE 'plpgsql'; 

CREATE TRIGGER insert_into_Student_Relation 
	AFTER INSERT ON Student 
		FOR EACH ROW EXECUTE PROCEDURE insert_into_Student();
```

## `BEFORE DELETE`

```sql
CREATE OR REPLACE FUNCTION delete_from_Student() 
	RETURNS TRIGGER AS 
		$$ 
		    BEGIN IF OLD.Major = ‘CS’ THEN 
		        DELETE FROM CS_studentWHERE sid = OLD.sid; 
		    END IF; 
		    RETURN OLD; 
		    END; 
		$$ LANGUAGE 'plpgsql'; 

CREATE TRIGGER delete_from_Student_Relation 
	BEFORE DELETE ON Student 
		FOR EACH ROW EXECUTE PROCEDURE delete_from_Student();
```
- The `FOR EACH ROW` clause is important because if you insert multiple values into the table at once, it will guarantee that the trigger function is executed on each tuple inserted

## View Update `INSERT`
Consider a view for `CS_Student` dependent on the base table `Student`
```sql
CREATE VIEW CS_Student AS
	SELECT sid, sname, byear
	FROM Student
	WHERE Major='CS';
	
CREATE FUNCTION insert_CS_student()
	RETURNS TRIGGER AS
		$$
		    BEGIN
		    INSERT INTO CS_Student VALUES(NEW.sid, NEW.sname, NEW.byear);
		    RETURN NULL;
		    END;
		$$ LANGUAGE 'plpgsql'
	
CREATE TRIGGER insert_into_CS_student
	INSTEAD OF INSERT ON Student
		FOR EACH ROW
		EXECUTE PROCEDURE insert_CS_student();
```
- If a CS student is entered into `Student` then `INSTEAD OF` inserting there, it will be inserted into  `CS_Student` view
- A similar thing can be done for the `DELETE`

## Constraint Verification
```sql
CREATE OR REPLACE FUNCTION check_Student_key_constraint()
	RETURNS trigger AS
		$$
		    BEGIN
		    IF NEW.sid IN (SELECT sid FROM Student) THEN
			    RAISE EXCEPTION 'sid already exists';
			END IF;
			RETURN NEW;
			END;
		$$ LANGUAGE 'plpgsql'
		
CREATE TRIGGER check_Student_key
	BEFORE INSERT ON Student
		FOR EACH ROW
			EXECUTE PRODCEDURE check_Student_key_constraint();
```
- Ensures that `sid` is unique before inserting

## Aggregation Function Maintenance
```sql
CREATE TABLE Count_Studnets(total INTEGER);
INSERT INTO Count_Student VALUES (0);

CREATE OR REPLACE FUNCTION Maintain_Number_Students()
	RETURNS trigger AS
		$$
		    BEGIN
		    UPDATE Count_Student SET total = total + 1
		    RETURN NULL;
		    END;
		$$ LANGUAGE 'plpgsql';
		
CREATE TRIGGER Total_Students
	AFTER INSERT ON Student
		FOR EACH ROW
		EXECUTE PROCEDURE Maintain_Number_Students();
```

## Maintaining a Log
```sql
CREATE TABLE Student_log(sid TEXT, stamp, TIMESTAMP);

CREATE OR REPLACE FUNCTION time_stamp_for_student()
	RETURNS TRIGGER AS
		$$
		    BEGIN
		    INSERT INTO Student_log VALUES (NEW.sid, now());
		    RETURN NULL;
		    END;
		$$ LANGUAGE 'plpgsql';

CREATE TRIGGER log_student
	AFTER INSERT ON Student
		FOR EACH ROW
		EXECUTE PROCEDURE time_stamp_from_student();
```

## Infinite Loops with Triggers
```sql
CREATE TABLE A (x INTEGER);

CREATE FUNCTION insert_in_A ()
	RETURNS TRIGGER AS
		$$
			BEGIN
			INSERT INTO A VALUSE (NEW.x);
			RETURN NEW;
			END;
		$$ LANGUAGE 'plpgsql';

CREATE TRIGGER insert_into_A_relation
	BEFORE INSERT ON A
		FOR EACH ROW
		EXECUTE PROCEDURE insert_in_A();
		
INSERT INTO A VALUES(1)
```
- This creates an infinite loop because the trigger inserts a value into the same table that the trigger is performing on
