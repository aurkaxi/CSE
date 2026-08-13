# 4.a. what is normalization? what are the conditions required for a relation to be 2nf, 3nf and bcnf explain.

Normalization in DBMS is a systematic process of organizing data into tables to minimize redundancy (duplicate data) and eliminate data anomalies such as insertion, updation, and deletion issues while ensuring data dependencies are logical.

## 2nf
### condition
1. A relation that is in First Normal Form
2. every non-primary-key attribute is fully functionally dependent on the primary key
### example
For a composite key (StudentID, CourseID), if the "StudentName" depends only on "StudentID" and not on the entire key, it violates 2NF. To normalize, move StudentName into a separate table where it depends only on "StudentID".

## 3nf
### condition
1. A relation that is in second Normal Form
2. there is no transitive dependency for non-prime attributes. (non-prime attributes should not depend on other non-prime attributes)
### example
Consider a table with (StudentID, CourseID, Instructor). If Instructor depends on "CourseID", and "CourseID" depends on "StudentID", then Instructor indirectly depends on "StudentID", which violates 3NF. To resolve this, place Instructor in a separate table linked by "CourseID".

## bcnf (Boyce-Codd Normal Form, strongest form of 3nf)
### condition
1. The relation should be in the 3rd Normal Form.
2. X should be a super-key for every functional dependency (FD) X−>Y in a given relation.
### example
If a table has a dependency (StudentID, CourseID) → Instructor, but neither "StudentID" nor "CourseID" is a superkey, then it violates BCNF. To bring it into BCNF, decompose the table so that each determinant is a candidate key.

# 4.b. explain the relational integrity constraints with categories
Relational integrity constraints are a set of rules used to maintain the quality, accuracy, and consistency of data within a relational database. They ensure that modifications (insertions, updates, or deletions) do not result in a loss of data integrity.

These constraints are generally categorized into four main types:
## 1. Domain Integrity
Domain integrity ensures that every entry in a specific column follows the defined data type, format, and range. It ensures that the data being entered is "meaningful" for that column.
**Example:** an `Age` column might be restricted to values between 1 and 120.
## 2. Entity Integrity
Entity integrity ensures that each row in a table is uniquely identifiable and that the primary key column cannot contain **NULL** values. If a primary key were null, the database would have no way to uniquely identify that specific record, violating the fundamental rule of a relational table.
**Example:** In a `Students` table, the `Student_ID` cannot be empty for any student.
## 3. Referential Integrity
It states that a **Foreign Key** must either match a valid primary key in the referenced table or be NULL. If Table B has a foreign key pointing to Table A, you cannot delete a record in Table A that is still being referenced by Table B.
## 4. Key Constraints
Key constraints ensure that the values used to identify tuples (rows) are unique and follow specific rules.
* **Candidate Key:** A set of attributes that can uniquely identify a tuple. There can be multiple candidate keys in a table.
* **Primary Key:** The specific candidate key chosen by the database designer to be the unique identifier.
* **Unique Constraint:** Similar to a primary key, it ensures all values in a column are distinct, but unlike a primary key, a column with a Unique constraint *can* contain a NULL value (depending on the DBMS).

# 4.c. interpret following statements
##  $\pi_{sname}\Big(\pi_{sid}((\sigma_{color='red'}(Parts)) \bowtie (\sigma_{cost<100}(Catalog))) \bowtie Suppliers\Big)$
1. `σ color='red' (Parts)`  
    → Select only **red parts**
2. `σ cost<100 (Catalog)`  
    → Select catalog entries where part price is **less than 100**
3. Join them  
    → Find red parts being sold for under 100
4. `π sid`  
    → Keep only supplier IDs of those suppliers
5. Join with `Suppliers`
6. `π sname`  
    → Get supplier names
### Meaning:
Names of suppliers who supply red parts costing less than 100.
## $\pi_{sname}\Big(\pi_{sid}((\sigma_{color='red'}(Parts)) \bowtie (\sigma_{cost<100}(Catalog) \bowtie Suppliers))\Big)$
1. `σ cost<100(Catalog)`  
    → Catalog entries with cost < 100
2. Join with `Suppliers`  
    → Attach supplier details
3. Join with red parts  
    → Keep only red parts
4. `π sid`
5. `π sname`
### Meaning:
Also gives names of suppliers who supply red parts costing less than 100.
##
Both **(i)** and **(ii)** produce the **same result**. Difference is only **order of joins / query execution plan**, not final output.

# 5.a. why domain constraints are important?
there are two types of domain constraints.
1. not null
2. check

importance of not null constraint
1. Ensures data completeness by requiring values for important fields.
2. Prevents errors and inconsistencies that can arise from missing or incomplete data.
3. Helps maintain data integrity and reliability across the database.

importance of check constraint
1. Allows for customised data validation based on specific requirements.
2. Ensures data integrity by preventing the entry of invalid values.
3. Helps maintain logical consistency in the database by adhering to real-world rules (e.g., age, prices).

# 5.b. convert the below relation of student enrollments table in boycee-codd normal form
| student_id | course_name | professor      |
| ---------- | ----------- | -------------- |
| 101        | java        | prof. java     |
| 102        | c++         | prof. cpp      |
| 101        | python      | prof. python   |
| 103        | java        | prof. java_2   |
| 104        | python      | prof. python_2 |

## step 1. find candidate key
a student can take many courses
a courses can have many students
so unique row identified by (student_id, course_name); that is our candidate key.
## step 2. find functional dependencies
from relation:
1. (student_id, course_name) -> professor: each student-course pair has one professor
2. professor->course_name: each professor teaches one course
## step 3. check bcnf condition
rule: for every functional dependency X->Y, x must be a super key.

check:
1. (student_id, course_name) -> professor. left side is key. follows the rule.
2. professor -> course_name. professor is not super key. 
so relation is not in bcnf
## step 4. decompose relation
splitting professor->course_name relation into
1. r1 (professor, course)
2. r2 (student_id, professor)
## step 5. final bcnf relations
professor_course = R1(professor, course_name)

| professor      | course_name |
| -------------- | ----------- |
| prof. java     | java        |
| prof. cpp      | c++         |
| prof. python   | python      |
| prof. java_2   | java        |
| prof. python_2 | python      |
enrollment = r2(student_id, professor)

| student_id | professor      |
| ---------- | -------------- |
| 101        | prof. java     |
| 102        | prof. cpp      |
| 101        | prof. python   |
| 103        | prof. java_2   |
| 104        | prof. python_2 |
# 5.c. describe database design process
1. requirement analysis: collect user needs and system requirements. 
	1. what data to store, 
	2. what reports needed, 
	3. who will use the system etc. 
2. conceptual design: create high-level design using er diagram. 
	1. identify entities, 
	2. attributes, 
	3. relationships etc.
3. logical design: convert er model into relational tables
	1. create relations (tables)
	2. define primary keys
	3. define foreign keys
	4. normalize tables
4. physical design: decide how data will be stored physically
	1. file organization
	2. indexing 
	3. storage method
	4. performance tuning
5. implementation: create database using dbms commands
6. testing and evaluation: check
	1. data correctness
	2. security
	3. speed
	4. backup/recovery
7. maintenance: update database when requirements change
	1. add new tables
	2. modify fields
	3. improve performance
# 6.a. define database join. explain different types of join operations with appropriate examples
A **Join** is a binary operation in SQL used to combine rows from two or more tables based on a related column between them.
consider two tables. 

table: students

| student_id | name  | dept_id |
| ---------- | ----- | ------- |
| 1          | Rahim | 10      |
| 2          | Karim | 20      |
| 3          | Nila  | 30      |
table: departments

| dept_id | dept_name |
| ------- | --------- |
| 10      | CSE       |
| 20      | EEE       |
| 40      | BBA       |
## 1. Inner Join
Returns only matching rows from both tables.
```sql
SELECT name, dept_name
FROM Student
INNER JOIN Department
ON Student.dept_id = Department.dept_id;
```

|**name**|**dept_name**|
|---|---|
|Alice|CSE|
|Bob|EEE|
## 2. Left Join (Left Outer Join)
Returns all rows from left table and matched rows from right table.
```sql
SELECT name, dept_name  
FROM Student  
LEFT JOIN Department  
ON Student.dept_id = Department.dept_id;
```

| name  | dept_name |
| ----- | --------- |
| Rahim | CSE       |
| Karim | EEE       |
| Nila  | NULL      |
## 3. Right Join (Right Outer Join)
Returns all rows from right table and matched rows from left table.
```sql
SELECT name, dept_name  
FROM Student  
RIGHT JOIN Department  
ON Student.dept_id = Department.dept_id;
```

| name  | dept_name |
| ----- | --------- |
| Rahim | CSE       |
| Karim | EEE       |
| NULL  | BBA       |
## 4. Full Join (Full Outer Join)
Returns all matched and unmatched rows from both tables.
```sql
SELECT name, dept_name  
FROM Student  
FULL JOIN Department  
ON Student.dept_id = Department.dept_id;
```

|name|dept_name|
|---|---|
|Rahim|CSE|
|Karim|EEE|
|Nila|NULL|
|NULL|BBA|
## 5. Cross Join
Returns Cartesian product of both tables.
```sql
SELECT name, dept_name  
FROM Student  
CROSS JOIN Department;
```
If 3 students and 3 departments → 9 rows.
## 6. Self Join
A table joined with itself.
Example: Employee table with manager relationship.
```sql
SELECT A.name, B.name AS manager  
FROM Employee A  
JOIN Employee B  
ON A.manager_id = B.emp_id;
```

# 6.b. what is null attribute? draw an e-r diagram for a university database that contains students, courses, professors, and departments. clearly indicate entities, attributes, relationships, primary keys, and cardinality constraints.
A **Null attribute** represents a value that is currently unknown, missing, or not applicable for a specific tuple (row). It is **not** equivalent to a zero or a blank string; it signifies the absence of a value.
diagram eta na, onno vabe hobe. apatoto pari na

![[WhatsApp Image 2026-04-29 at 10.13.27 PM.jpeg]]
# 6.c. explain aggregate functions in sql. give examples of aggregate functions.
**Aggregate functions** in SQL perform a calculation on a set of values and return a **single scalar value**. They are typically used in conjunction with the `GROUP BY` clause to summarize data.

Common Aggregate Functions
1. **`COUNT()`**
    Returns the total number of rows or non-null values in a column.
    - _Example:_ `SELECT COUNT(student_id) FROM Students;` (Total number of students).
2. **`SUM()`**
    Calculates the total sum of a numeric column.
    - _Example:_ `SELECT SUM(credits) FROM Courses;` (Total credits offered).
3. **`AVG()`**
    Calculates the numerical average of a column.
    - _Example:_ `SELECT AVG(marks) FROM Results;` (Mean score of a class).
4. **`MIN()`**
    Returns the smallest value in a column.
    - _Example:_ `SELECT MIN(age) FROM Students;` (Age of the youngest student).
5. **`MAX()`**
    Returns the largest value in a column.
    - _Example:_ `SELECT MAX(salary) FROM Professors;` (Highest faculty salary).
# 7.a. consider two relations: cs_students (student_id, name) and math_students (student_id, name) and create the relational algebraic expressions for the following statements:
## a. Students enrolled in BOTH Computer Science and Mathematics
To find students common to both sets, we use the **Intersection** ($\cap$) operation. This returns tuples that appear in both relations.
**Relational Algebraic Expression:**
$$\Pi_{student\_id, name}(cs\_students) \cap \Pi_{student\_id, name}(math\_students)$$
**Detailed Explanation:**
- **Projection ($\Pi$):** While the tables already have the same schema, using the projection operator ensures we are specifically comparing the $student\_id$ and $name$ columns.
- **Intersection ($\cap$):** This operator acts like a logical `AND`. A student must exist in the `cs_students` relation **and** the `math_students` relation to be included in the final result.
## b. Students in Computer Science but NOT in Mathematics
To find students belonging to the first set but excluded from the second, we use the **Set Difference** ($-$) operation (also known as Minus).
**Relational Algebraic Expression:**
$$\Pi_{student\_id, name}(cs\_students) - \Pi_{student\_id, name}(math\_students)$$
**Detailed Explanation:**
- **Set Difference ($- house$):** This operation takes all tuples from the first relation (`cs_students`) and removes any tuples that also appear in the second relation (`math_students`).
- **Prerequisite:** For this to work, both relations must be **union-compatible**, meaning they must have the same number of attributes and corresponding attributes must have the same domain.
- **Result:** The output will contain students who are strictly enrolled in Computer Science only.
# 7.b. "all super keys are candidate keys but all candidate keys are not super keys" - justify your answer.
> **"All candidate keys are super keys, but not all super keys are candidate keys."**

The Definitions
- **Super Key:** A set of one or more attributes that, taken collectively, allows us to identify a tuple uniquely in a relation. It can have redundant attributes.
- **Candidate Key:** A **minimal** super key. It is a super key that has no proper subset which is also a super key. It contains no unnecessary attributes.

Justification
By definition, a candidate key must first satisfy the requirement of uniquely identifying a row. Since any set of attributes that provides uniqueness is a super key, every candidate key automatically falls into the category of super keys.

A super key can contain **extra, redundant attributes** that are not necessary for uniqueness. If you can remove an attribute from a super key and it still identifies rows uniquely, it is a super key but **not** a candidate key.

Example
Consider a `Student` table with attributes: `(ID, Name, Email)`.
- **Candidate Keys:** `{ID}`, `{Email}` (Minimal and unique).
- **Super Keys:** * `{ID}` (Also a candidate key)
    - `{Email}` (Also a candidate key)
    - `{ID, Name}` (Super key, but **not** a candidate key because `{ID}` alone is enough).
    - `{ID, Name, Email}` (Super key, but **not** a candidate key because it is not minimal).

Summary
- **Candidate Key** = Uniqueness + Minimality.
- **Super Key** = Uniqueness (Minimality is optional).
Therefore, the set of Candidate Keys is a **subset** of the set of Super Keys.

# 7.c. define trigger in dbms. how delete, drop, and truncate differ from each other in terms of functionality, impact on data, and rollback capability.
A **Trigger** is a stored procedure that automatically executes (or "fires") in response to a specific event on a particular table or view, such as `INSERT`, `UPDATE`, or `DELETE`. It is used to maintain integrity, automate audit trails, or enforce complex business rules.

| Feature            | DELETE                                   | TRUNCATE                                    | DROP                            |
| ------------------ | ---------------------------------------- | ------------------------------------------- | ------------------------------- |
| **Functionality**  | Removes selected rows using WHERE clause | Removes all rows from table                 | Removes entire table structure  |
| **Impact on Data** | Data removed row-by-row                  | All data removed quickly                    | Table + data completely removed |
| **Rollback**       | Can be rolled back (transaction-safe)    | Usually not rollback-safe (depends on DBMS) | Cannot be rolled back           |
