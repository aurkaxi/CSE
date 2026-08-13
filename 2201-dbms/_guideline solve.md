que
1. Define an Entity-Relationship model. Explain the main components of the E-R model and their purposes in database design.
---
# entity relationship model
The Entity-Relationship Model (ER Model) is a conceptual model for designing a database. This model represents the logical structure of a database, including entities, their attributes, and relationships between them.
## entity
An entity in an Entity-Relationship (ER) model is a real-world object, concept, or event about which data is stored

An entity serves as the foundational building block of an ER model, representing real-world "nouns" (e.g., Student, Order) to translate complex data environments into clear, logical structures before physical database implementation. 

## attribute
In an Entity-Relationship (ER) model, attributes are the characteristics, properties, or data elements that describe an entity

Their primary purpose is to hold specific information about the data being modeled, which translates into the columns that store actual values in the final database tables
## relationship
Relationships in an Entity-Relationship (ER) model define how different entities (data objects) interact with each other.

Their primary purpose is to represent logical connections, enforce rules (like data integrity), and provide a blueprint for translating a real-world system into a functional, structured database.
<div class="page-break" style="page-break-before: always;"></div>

que
2. Differentiate between entity sets and relationship sets. Provide examples to clarify your explanation. 
---

| feature       | entity set                                                          | relationship set                                                        |
| ------------- | ------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| definition    | A collection of similar, independent real-world objects or "nouns". | A collection of mathematical links or associations between entity sets. |
| Basic Unit    | Contains Entities (individual records)                              | Contains Relationships (tuples mapping the connected entities).         |
| ER Symbol     | Represented by a Rectangle.                                         | Represented by a Diamond.                                               |
| RDBMS Mapping | Maps to a base table; rows represent independent object instances.  | Maps to a table containing Foreign Keys linking the participant tables. |
| Example       | "John Doe", "math 101"                                              | "John Doe takes Math 101"                                               |
<div class="page-break" style="page-break-before: always;"></div>

que
3. Explain the concept of cardinality in relationships. What are the different types of cardinalities, and how do they affect database design? 
---

Cardinality in database and data modeling defines the numerical relationship between rows in two tables. It dictates how many instances of one entity can or must be associated with instances of another entity, ensuring data integrity and correct table structures.

1. One-to-One (1:1)
   One record in Table A is associated with exactly one record in Table B.
   Example: An Employees table and an EmployeeDetails table where each employee has exactly one associated personnel file.
   Impact on Design: these are rare and often used to segment sensitive data for security or to bypass column limits. The Primary Key of one table becomes both the Primary and Foreign Key in the other.
2. One-to-Many (1:N):
   One record in Table A is associated with multiple records in Table B, but records in Table B relate to only one record in Table A.
   Example: A Customers table and an Orders table. A single customer can place many orders, but an order belongs to only one customer.
   Impact on Design: This is the foundational building block of relational databases. It is implemented by placing the Primary Key of the "One" side (the parent table) as a Foreign Key in the "Many" side (the child table).
3. Many-to-Many (M:N):
   Multiple records in Table A are associated with multiple records in Table B.
   Example: A Students table and a Courses table. A student can enroll in multiple courses, and a course contains multiple students.
   Impact on Design: Relational databases cannot natively establish a direct M:N relationship because it causes data duplication. It is resolved by creating a junction/associative table (e.g., Enrollments) that breaks the many-to-many relationship into two one-to-many (1:N) relationships.
<div class="page-break" style="page-break-before: always;"></div>

que
4. Describe the role of attributes in an E-R model. Explain the differences between simple, composite, derived, and multivalued attributes.
---
In an Entity-Relationship (E-R) model, attributes act as the defining properties or characteristics of an entity. They provide the specific details—acting like columns in a database table—that give the model meaning, structure, and actionable context.
Key Functions of Attributes:
1. Identify Unique Entities: Attributes designated as Primary Keys uniquely distinguish one specific entity instance from another.
2. Provide Detail & Context: They describe the actual information you want to store, such as a customer's Name, Address, or Date of Birth.
3. Enforce Data Integrity: Attributes define the expected data types and constraints, ensuring information remains consistent across the system.

| Attribute Type  | Definition                                                 | Database Table Implementation                                      | Real-World Example                                                  | ER symbol                     |
| --------------- | ---------------------------------------------------------- | ------------------------------------------------------------------ | ------------------------------------------------------------------- | ----------------------------- |
| Simple (Atomic) | Cannot be divided into smaller sub-parts.                  | Maps directly to a single column.                                  | `Roll_No`, `Salary`                                                 | oval                          |
| Composite       | Can be divided into smaller, independent sub-attributes.   | Flattened into multiple separate columns for each sub-part.        | `Name` (First, Last)<br><br>  <br><br>`Address` (Street, City, Zip) | Oval branching into sub-ovals |
| Multivalued     | Can hold more than one value for a single entity instance. | Requires a new table with a Foreign Key to avoid violating 1NF.    | `Phone_Number`, `Skills`                                            | double oval                   |
| Derived         | Value is calculated dynamically from other attributes.     | Not stored physically; calculated via queries/views to save space. | `Age` (derived from `DOB`)                                          | dashed oval                   |
<div class="page-break" style="page-break-before: always;"></div>

que
5. What is a weak entity set? Explain with an example, and discuss the importance of a discriminator in a weak entity set. 
---

A weak entity set is an entity set that does not possess a primary key of its own. Its existence is entirely dependent on a dominant entity set, known as the identifying (or strong) entity set.
* ER Symbol: Represented by a Double Rectangle.
* Relationship: It connects to the strong entity via an identifying relationship (represented by a Double Diamond).
* Participation: Its participation in the identifying relationship is always total (represented by a Double Line).

Example
Consider a `Dependent` entity set (tracking employees' family members for insurance) linked to an `Employee` strong entity set.
If an employee leaves the company, their dependents are removed from the database because a dependent cannot exist in the system without a corresponding employee.

Importance of a Discriminator
A discriminator (also called a partial key) is the set of attributes that uniquely distinguishes among all the entities within a weak entity set under the same strong entity instance. It is represented by a dashed underline.
* Forming the Primary Key: Since a weak entity has no primary key, its unique identity is constructed by combining the Primary Key of the Strong Entity + the Discriminator of the weak entity.
* Data Disambiguation: In the example, two different employees might both have a dependent named "John". The discriminator (`Dependent_Name`) allows the system to distinguish between Employee A's "John" and Employee B's "John" by pairing them with their respective parent primary keys (`Emp_ID`).
<div class="page-break" style="page-break-before: always;"></div>

que
6. Describe the purpose of an E-R diagram. How does it help in the database design process?
---

The primary purpose of an Entity Relationship Diagram is to provide a clear, non-technical overview of how data is organized within a system. It acts as a structural blueprint that translates real-world business objects (like "Customers," "Orders," and "Products") into a conceptual data model.

1. Spotting Design Flaws Early: 
   They reveal structural issues—such as data duplication, missing relationships, or circular logic—before any actual code is written.
2. Simplifying Translation to SQL: 
   They directly translate into physical database tables (entities) and the primary/foreign keys needed to connect them.
3. Bridging Communication Gaps: 
   They provide a shared, visual language that aligns developers, product managers, and non-technical stakeholders on exactly what data the system will store.
4. Documenting for the Future: 
   They act as permanent, easy-to-read documentation, making future database updates, maintenance, or troubleshooting significantly easier.
<div class="page-break" style="page-break-before: always;"></div>

que
7. Explain the difference between primary key and foreign key in the context of E-R modeling. Why is a primary key essential for each entity set? 
---

| Feature          | Primary Key (PK)                          | Foreign Key (FK)                         |
| ---------------- | ----------------------------------------- | ---------------------------------------- |
| Main Objective   | Uniquely identifies an entity instance.   | Links tables to establish relationships. |
| Uniqueness       | Strictly unique values only.              | Duplicate values are fully permitted.    |
| Null Values      | Never allowed (NOT NULL).                 | Allowed unless defined otherwise.        |
| Limit per Entity | Only one allowed per entity.              | Multiple foreign keys are allowed.       |
| Data Placement   | Resides in the parent/independent entity. | Resides in the child/dependent entity.   |
A primary key is essential for each entity set because it guarantees uniqueness, enforces data integrity, and establishes relationships between tables. Without it, retrieving and modifying specific records becomes prone to errors and duplication.
1. Unambiguous Identification: It acts as a permanent fingerprint for every entity. Even if two records share similar data (like two employees with the same name), their primary keys remain distinct.
2. Relational Mapping: It serves as a foundational reference point. Primary keys are called by related entity sets as foreign keys to connect, query, and structure relational databases.
3. Entity Integrity Enforcement: It forces the database to ensure no two records have the same identifier and that every record has a valid (non-null) value.
4. Optimized Data Access: Database systems automatically use primary keys to build indices, speeding up search and retrieval operations.
<div class="page-break" style="page-break-before: always;"></div>

que
8. Discuss the process of mapping an E-R model to a relational database schema. Outline the steps involved and provide examples.
---

1. Map Regular (Strong) Entities
   Create a separate table for each strong entity. The entity's attributes become table columns, and the chosen E-R key becomes the Primary Key (\(PK\)).
   Example: Entity Student with attributes \(StudentID\) and \(Name\) becomes table Student(StudentID, Name) where \(StudentID\) is the \(PK\).
2. Map Weak Entities
   Create a table for the weak entity. Its Primary Key is a composite key consisting of its partial key and the Primary Key of its identifying strong (owner) entity. The owner's key acts as a Foreign Key (\(FK\)).
   Example: Weak entity Dependent (attributes \(DepName\), \(Age\)) dependent on Employee (\(EmpID\)). Becomes table Dependent(EmpID, DepName, Age).
3. Map 1:1 (One-to-One) Relationships
   Take the Primary Key of one table and include it as a Foreign Key in the other, or merge the two entities into a single table.
   Example: Employee manages Department. Table Department can have \(EmpID\) added as an \(FK\) pointing to the Employee table.
4. Map 1:N (One-to-Many) Relationships
   Identify the 'Many' side of the relationship. Take the Primary Key from the 'One' side and add it as a Foreign Key in the 'Many' side.
   Example: Department (1) has many Employees (N). Add \(DeptID\) (from Department) as a Foreign Key in the Employee table.
5. Map M:N (Many-to-Many) Relationships
   Create a new intersection (associative) table. This table's Primary Key is a composite of the Primary Keys of both participating entities. Any attributes of the relationship itself are also placed here.
   Example: Student enrolls in Course. Create a table Enrollment(StudentID, CourseID, Grade) where (\(StudentID\), \(CourseID\)) is the composite \(PK\).
6. Map Multi-valued Attributes
   Create a new table for the multi-valued attribute. Include the Primary Key of the original entity as a Foreign Key to link them, alongside the attribute itself.
   Example: An Employee with multiple \(PhoneNumbers\). Create EmployeePhone(EmpID, PhoneNumber).
<div class="page-break" style="page-break-before: always;"></div>

que
9. What is generalization and specialization in E-R models? Explain with examples how these concepts are used in database design.
---

1. Generalization (bottom up approach)
	- Definition: Combines multiple lower-level entities into a single higher-level entity based on common attributes.
	- Goal: Minimizes redundancy by grouping shared traits into a single superclass.
	- Example: You have separate entity sets for Student and Faculty. Both share attributes like Name, Address, and Phone_Number. You extract these shared attributes to create a higher-level entity called Person.
2. Specialization (top down approach)
	- Definition: Splits a single higher-level entity into multiple lower-level sub-entities based on distinct features.
	- Goal: Focuses on distinct qualities that apply only to specific subgroups.
	- Example: You start with a broad Employee entity containing Employee_ID and Salary. Because different jobs require unique data, you break it down into subgroups like Developer and Tester. Developer gets a specific attribute like Programming_Language, while Tester gets Testing_Tool.

use in db design
1. Attribute Inheritance: Sub-entities automatically inherit all standard attributes from the superclass table. You only need to define unique columns for the specialized tables
2. redundancy Elimination: Shared columns are defined exactly once in the parent table instead of being duplicated across multiple tables.
3. Constraint Enforcement: Designers apply rules like Disjoint (an entity can only belong to one sub-category) or Overlapping (an entity can belong to multiple) to preserve data integrity.
4. Query Optimization: It allows clean logical partitioning, meaning you can query the broad group (Person) or easily zoom into details (Student).
5. Table Mapping: When converting the ER diagram to a physical relational database, designers decide whether to generate a single unified table with optional null fields or split them into mapped parent-child tables utilizing foreign keys.
<div class="page-break" style="page-break-before: always;"></div>

que
10. Define the concept of a ternary relationship. How does it differ from a binary relationship, and when is it necessary to use a ternary relationship? 
---

A ternary relationship is a relationship of degree three in which three independent entities participate simultaneously in a single association. It is used when a connection among three distinct concepts cannot be accurately or fully represented by multiple individual binary (two-entity) relationships

| Feature         | Binary                                                                       | Ternary                                                                      |
| --------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| Degree          | 2                                                                            | 3                                                                            |
| Complexity      | Simple; easy to implement and map.                                           | Complex; harder to resolve structural constraints.                           |
| Dependency      | Connects one entity instance directly to another.                            | All three instances must exist concurrently for the association to hold.     |
| Cardinality     | Expressed natively as 1:1, 1:N, or M:N.                                      | Evaluated in pairs against the remaining single entity (e.g., 1:1:M, M:N:P). |
| Database Tables | Often mapped directly by nesting foreign keys or using standard join tables. | Always requires a dedicated relationship table holding three foreign keys.   |
To determine whether you should use one ternary relationship or multiple binary relationships, ask yourself these questions:
1. Does the association involve three entities? (e.g., Doctor, Patient, Medication).
2. Does splitting the relationship into binary links cause a loss of data? 
   If you connect Doctor to Patient and Doctor to Medication, you lose track of which doctor prescribed which medication to which patient.
3. Does the relationship contain descriptive attributes of its own? 
   If you need to store attributes like "Date assigned" or "Quantity supplied" that only make sense when all three entities are connected together, you need a ternary relationship.
<div class="page-break" style="page-break-before: always;"></div>

que.
11. Explain aggregation in the E-R model. When is it used, and how does it benefit complex relationships? 
---

Aggregation in an E-R model is an abstraction through which a relationship and its participating entities are treated as a single, higher-level entity. It is primarily used to represent relationships between relationships, allowing a connection to be made between a unified set and another entity.

Aggregation is used when standard E-R relationships cannot accurately model complex, real-world scenarios, particularly when you need an entity to relate to an entire interaction rather than just a single object.
Example: In a university database, a Student enrolls in a Course (creating an enrollment relationship). If this specific Student and Course combination is then supervised or assessed by a Professor, you cannot easily link the Professor directly to the Student-Course relationship without aggregation.
The Solution: The Student-Course relationship is aggregated into a single entity called Enrollment. This new higher-level entity is then linked to the Professor entity.

1. Models Higher-Order Interactions: 
   It allows relationships to take part in other relationships, accurately capturing the requirements of advanced, real-world data interactions.
2. Simplifies E-R Diagrams: 
   By grouping complex relationships into a higher-level abstract unit, it prevents diagrams from becoming chaotic and unreadable.
3. Improves Clarity and Consistency: 
   It reduces data redundancy by ensuring that complex multi-entity constraints are represented logically.
4. Enables Complex Queries: 
   Grouping interactions into aggregates makes it easier to track, scale, and query intricate multi-entity conditions.
<div class="page-break" style="page-break-before: always;"></div>

que
12. Describe the concept of total and partial participation in relationships. Provide examples of both types in an E-R diagram.
---

Total Participation (Mandatory)
Total participation means every entity in the entity set must participate in at least one relationship. If an entity cannot exist in the database without being tied to another specific entity, it has total participation. In an ER diagram, it is represented by a double line.
Example: Consider the entities Employee and Department linked by the relationship Works_For. If company rules dictate that every employee must be assigned to a department, then Employee exhibits total participation in the Works_For relationship. An Employee entity cannot be created or exist without an associated Department.2. 

Partial Participation (Optional)
Partial participation means that only some (not necessarily all) entities in the set may participate in the relationship. An entity can exist independently without being connected to the other entity in the relationship. In an ER diagram, it is represented by a single line.
Example: Using the same Employee and Department entities, a department may or may not have employees assigned to it at any given time (e.g., a newly created department). Therefore, the Department entity exhibits partial participation in the Works_For relationship—its existence does not depend on having workers.

![[Pasted image 20260612124617.png]]
<div class="page-break" style="page-break-before: always;"></div>

que
13. Define normalization in the context of database design. Explain the importance of normalization in relational databases. 
---

Database normalization is the systematic process of organizing data to reduce redundancy and eliminate undesirable characteristics like update anomaly, redundancy, inconsistencies. It involves dividing large, complex tables into smaller, logically related tables and linking them using primary and foreign keys. 

1. Minimizes Redundancy: 
   By splitting large tables into smaller logical ones, you avoid storing the exact same data in multiple places, saving storage and speeding up processing.
2. Improves Consistency: 
   Clear relationships between tables ensure that data remains accurate and reliable across the entire system
3. Improves Integrity: 
   Changes only need to be made in one place. This ensures consistent reporting and eliminates conflicting records.
4. Prevents Anomalies: 
   It removes insertion, updating, and deletion anomalies. For instance, it ensures you don't accidentally erase a customer's personal details just because they deleted a product order.
<div class="page-break" style="page-break-before: always;"></div>

que
14. Describe the First Normal Form (1NF). Give an example of a table that is not in 1NF and then convert it to 1NF. 
---

First Normal Form (1NF) is a foundational rule in database design that requires every cell in a table to contain only a single, indivisible value (atomicity). A table is in 1NF if there are no repeating groups, arrays, or comma-separated lists within a single field

The rules for 1NF include:
- Each column must contain only one value per cell.
- All values in a column must be of the same data type.
- Every column must have a unique name.
- No two rows are exactly identical (each row is uniquely identifiable by a primary key).

example: Unnormalized Table (Not in 1NF)
Below is an Employees table where an employee's skills are stored as a comma-separated list. This violates 1NF because the Skills column holds multiple values in a single cell.

| EmployeeID | Name  | Skills        |
| ---------- | ----- | ------------- |
| 101        | Alice | Java, Python  |
| 102        | Bob   | Communication |


Conversion to 1NF
To convert this table to 1NF, we must flatten the table so that every cell contains only one atomic (indivisible) value. We do this by separating the multiple skills into individual rows.

| EmployeeID | Name  | Skill         |
| ---------- | ----- | ------------- |
| 101        | Alice | Java          |
| 101        | Alice | Python        |
| 102        | Bob   | Communication |

The table is now in 1NF. Every column contains only atomic values, though this approach causes a bit of data duplication (e.g., repeating Alice's department).
<div class="page-break" style="page-break-before: always;"></div>

que
15. Explain the concept of functional dependency. Why is it important in understanding normalization? 
---

A functional dependency is a constraint in a database that describes how one attribute (or column) uniquely identifies another attribute. It is written as X → Y, meaning "X determines Y". For every unique value of X, there is precisely one corresponding value of Y.

- **Identifying Candidate Keys:** FDs define which attributes uniquely identify a record, allowing developers to identify primary and candidate keys.
- **Spotting Partial Dependencies (2NF):** Normalization relies on FDs to ensure that non-prime attributes depend on the _entire_ primary key rather than just a part of it, which achieves Second Normal Form (2NF). 
- **Eliminating Transitive Dependencies (3NF):** FDs expose hidden "chain reactions" where one non-key attribute determines another non-key attribute. Breaking these chains helps achieve Third Normal Form (3NF).]
- **Preventing Database Anomalies:** By evaluating FDs, designers can cleanly break large tables into smaller, related ones. This stops **insert**, **update**, and **delete anomalies** (such as inadvertently losing data about a department when the last student in that department is deleted). 
- **Achieves Advanced Normal Forms (BCNF):** The Boyce-Codd Normal Form strictly dictates that for every functional dependency X → Y, X _must_ be a super key. FDs allow architects to evaluate schemas mathematically to ensure this rule is never violated. 
<div class="page-break" style="page-break-before: always;"></div>

que
16. What is Boyce-Codd Normal Form (BCNF)? Describe the conditions for a relation to be in BCNF and provide an example. 
---

Boyce-Codd Normal Form (BCNF) is an advanced level of database normalization that eliminates data redundancy and anomalies more strictly than the Third Normal Form (3NF). Often referred to as "3.5NF," a table is in BCNF if and only if it is in 3NF and every determinant is a candidate key (or superkey).

For a table to satisfy the Boyce-Codd Normal Form, it should satisfy the following two conditions: 
1. It should be in the Third Normal Form and
2. for any dependency A → B, A should be a super key.

Imagine a database tracking Instructors and the Subjects they teach:

Instructor|Subject|Department
-|-|-
Dr. Smith|Math|Science
Dr. Smith|Physics|Science

- Candidate Key: {Instructor, Subject} (Together, they identify a unique row).
- Functional Dependency: Instructor → Department (Dr. Smith is always in the Science department).

The BCNF Violation: This table violates BCNF because Instructor determines Department, but Instructor is not a candidate key (it only works when paired with Subject). This causes redundancies: if Dr. Smith teaches 5 classes, we waste space storing "Science" 5 times.

The BCNF Solution: To fix this and achieve BCNF, we split (decompose) the table into two:
Table 1: Instructor Departments

Instructor|Department
-|-
Dr. Smith|Science

Table 2: Instructor Subjects

Instructor|Subject
-|-
Dr. Smith|Math
Dr. Smith|Physics
Now, both tables strictly follow the BCNF rule, removing redundancies and update anomalies.
<div class="page-break" style="page-break-before: always;"></div>

que
17. Explain the concept of transitive dependency. Why is it considered problematic in database design? 
---

A transitive dependency is an indirect functional dependency in a relational database where a non-key attribute determines another non-key attribute, rather than being determined directly by the primary key. It occurs when a chain of relationships exists: Attribute A determines Attribute B (\(A -> B\)), and Attribute B determines Attribute C (\(B -> C\)), meaning A indirectly determines C (\(A -> C\)).

Transitive dependencies violate the Third Normal Form (3NF) rules. They introduce severe database anomalies and data management issues:
1. Data Redundancy: 
   The relationship between non-key columns repeats across multiple rows unnecessarily, bloating storage.
2. Update Anomalies: 
   If a non-key value changes, you must update every single row containing that value. Missing even one row corrupts data consistency.
3. Insertion Anomalies: 
   You cannot record a relationship between the non-key attributes until you have a valid primary key to attach them to.
4. Deletion Anomalies: 
   Deleting a primary key record can accidentally erase the only copy of the independent relationship between your non-key attributes.
<div class="page-break" style="page-break-before: always;"></div>

que
18. Describe the requirements of the Second Normal Form (2NF) and explain how it differs from 1NF. 
---

A relation schema R is in second normal form (2NF) if it satisfies the following conditions :
1. must be in first normal form
2. every non-prime attribute A in R is fully functionally dependent on the primary key i.e table must not contain partial dependency. 

| feature             | 1nf                                                                      | 2nf                                                     |
| ------------------- | ------------------------------------------------------------------------ | ------------------------------------------------------- |
| primary goal        | Organizes data into a basic, flat table format.                          | Eliminates redundant data and partial-key dependencies. |
| Primary Requirement | Data values must be atomic (indivisible). No repeating groups or arrays. | Must already be in 1NF.                                 |
|Dependency Rule|Each row must be uniquely identified by a primary key.|No partial dependencies. All non-key attributes must rely on the whole primary key.|
|When it Matters|Applies to all tables.|Primarily matters when your table uses a composite key (a primary key made of two or more columns).|
<div class="page-break" style="page-break-before: always;"></div>

que
19. What is Third Normal Form (3NF)? Illustrate with an example how a relation that is in 2NF may not be in 3NF. 
---

Third Normal Form (3NF) is a database normalization rule stating that a table must be in Second Normal Form (2NF) and must not contain any transitive dependencies. This means no non-primary key column should depend on another non-primary key column, ensuring data consistency and reducing update anomalies.

A table is in 2NF if it is in 1NF and no non-key attribute is dependent on a proper subset of any candidate key. However, a "hidden" dependency can still occur where a non-key attribute determines another non-key attribute.
imagine an employee database that stores information in a single table: Employee_Project.
Table: Employee_Project

| Emp_ID (PK) | Emp_Name | Department_ID | Department_Name | Project_ID |
| ----------- | -------- | ------------- | --------------- | ---------- |
| 101         | Alice    | D01           | IT              | P1         |
| 102         | Bob      | D02           | HR              | P2         |
| 103         | Charlie  | D01           | IT              | P3         |
Assuming Emp_ID and Project_ID together form the primary composite key, meaning every non-key attribute depends on the whole primary key, satisfying 2NF).

Why is this not in 3NF?
This table violates 3NF because of a transitive dependency: Emp_ID determines Department_ID, and Department_ID determines Department_Name.
Since Department_Name is dependent on Department_ID (which is not a primary key), it is only indirectly dependent on Emp_ID. This results in redundancy; for instance, "IT" and "D01" are repeated in every Alice and Charlie record.
<div class="page-break" style="page-break-before: always;"></div>

que
20. Discuss the advantages and disadvantages of decomposing relations in the process of normalization. 
---

advantage:
- Elimination of Data Redundancy: Large tables are split so each data item is stored in only one place. This prevents unnecessary repetition and saves significant storage space.
- Prevention of Data Anomalies: Decomposition fixes flawed designs by eliminating Insertion, Update, and Deletion Anomalies. For instance, updating data in a single location prevents data inconsistency.
- Improved Data Integrity: Attributes are logically grouped by entity, keeping the database accurate and reliable. This enforces relational integrity and maintains clear data dependencies.
- Easier Maintenance: Smaller, well-structured tables are easier to manage, scale, and update. Modifying schemas becomes less error-prone because changes are isolated to specific tables.
- Greater Flexibility and Performance: Logical separation makes the database more adaptable. Smaller, focused tables reduce memory overhead and optimize query performance by eliminating redundancy.

disadvantage:
1. Performance Overhead & Complex Queries
	- Slow Reads: Frequent JOINs tax memory and degrade read performance.
	- Complex Development: Reconstructing fragmented data requires complex, nested SQL queries.
	- Indexing Limits: Indexing efficiency drops when queries constantly merge multiple tables.
2. Complex Data Entry & Maintenance
	- Multi-Step Inserts: Adding a single record requires coordinated writes across multiple tables.
	- Foreign Key Fatigue: Heavy reliance on foreign keys overcomplicates the schema and updates.
3. Risk of Information & Dependency Loss
	- Lossy Decomposition: Bad splits cause lossy decomposition, preventing perfect data reconstruction via JOINs.
	- Dependency Loss: Enforcing functional dependencies becomes impossible without costly JOINs.
	- System Cost: Highly normalized relations demand more hardware and specialized management.
<div class="page-break" style="page-break-before: always;"></div>

que
21. Define multivalued dependency and explain its role in Fourth Normal Form (4NF). Provide an example. 
---

A multivalued dependency (MVD) occurs when two independent, multi-valued attributes in a table both depend on a third attribute.

For a database to be in Fourth Normal Form (4NF), it must meet two conditions:
1. It must satisfy Boyce-Codd Normal Form (BCNF).
2. It must have no non-trivial multivalued dependencies.
4NF’s role is to eliminate the severe data redundancies and update anomalies caused by MVDs. When a table has independent multivalued facts about the same entity, it forces you to create multiple rows for every combination, even though the facts are unrelated. To achieve 4NF, these problematic tables are split into two or more smaller, independent tables.

Suppose we want to track employees, the programming languages they know, and the branch offices they work at.

| Employee | Programming Language | Branch Office |
| -------- | -------------------- | ------------- |
| John     | Java                 | New York      |
| John     | Java                 | London        |
| John     | Python               | New York      |
| John     | Python               | London        |
The Problem:  
John knows 2 languages and works at 2 branches. Because there is no relationship between his programming languages and the branch offices, this single table generates 4 rows of repetitive data. The dependencies are:
- Employee -> -> Programming Language
- Employee -> -> Branch Office

The Solution (Achieving 4NF):  
To eliminate the multivalued dependency, we split the original table into two separate tables:
1. Employee Languages Table

|Employee|Programming Language|
|---|---|
|John|Java|
|John|Python|
2. Employee Branches Table

|Employee|Branch Office|
|---|---|
|John|New York|
|John|London|
By isolating the independent multivalued attributes into their own distinct tables, you eliminate unnecessary data redundancy.
<div class="page-break" style="page-break-before: always;"></div>

que
22. How can redundancy be removed from a relation in BCNF? Discuss the impact of redundancy on database performance. 
---

To remove redundancy, you must decompose the table so that for every functional dependency X → Y, the determinant X is a super key. Decompose the relation into smaller, valid tables using the BCNF decomposition algorithm.
The Step-by-Step BCNF Decomposition Process
1. Identify Candidate Keys: Find all possible candidate keys in your original relation.
2. Find Violations: Look for any non-trivial functional dependency X → Y where X is not a super key.
3. Decompose the Table: Separate the violating relation into two new tables:
    - Table 1: Contains the attributes of the closure X⁺ (all attributes directly or indirectly determined by X).
    - Table 2: Contains the determinant X plus all the original attributes that are not in the closure X⁺.
4. Verify and Repeat: Check if the new relations satisfy BCNF. If any table still contains a BCNF violation, apply this decomposition process recursively until every single table is in BCNF.


Negative Impacts (Unintentional Redundancy)
- Update Anomalies: Changing data requires updates across multiple rows/tables, increasing overhead and resource locking.
- Increased Storage: Excess disk usage balloons database size, causing longer query load times and higher costs.
- Complex Data Management: The DBMS must scan more data during searches, leading to poor execution plans and slower responses.
Positive Impacts (Deliberate Redundancy)
- Faster Read Operations: Denormalization pre-stores joined data, eliminating time-consuming JOIN operations.
- Load Distribution & Scalability: Data replication spreads read workloads across multiple servers to handle high concurrent traffic.
- Reduced Network Latency: Geographic redundancy places data copies closer to users, drastically cutting retrieval wait times.
<div class="page-break" style="page-break-before: always;"></div>

que
23. Describe a real-world scenario where denormalization might be preferred over full normalization. Explain the trade-offs involved. 
---

Scenario: An E-commerce dashboard stores pre-computed order details (customer name, address, products) in a single `Order_Summary` table to avoid expensive table joins.

Benefits
- Faster Reads: Eliminates complex table JOINs at query time, drastically reducing page load latency.
- Simpler Query Logic: Applications can fetch complete order histories via simple SELECT queries, leading to cleaner code.

Drawbacks & Risks
- Data Redundancy: Storing identical data across multiple tables (e.g., `Customer` and `Order_Summary`) consumes excess storage.
- Write Inefficiency: Modifying data (e.g., an address) requires updating multiple rows, making writes (Insert/Update/Delete) slower and more complex.
- Anomalies & Staleness: If a background update fails or lags, the database risks becoming inconsistent or stale.
<div class="page-break" style="page-break-before: always;"></div>

que
24. Explain the Fifth Normal Form (5NF). What type of dependencies does it address, and when is it typically applied in database design? 
---

Fifth Normal Form (5NF), or Project-Join Normal Form (PJNF), ensures a table is decomposed into the smallest possible pieces without data loss. A table is in 5NF if every non-trivial join dependency is implied by its candidate keys, preventing the generation of spurious (fake) tuples during reconstruction.

5NF specifically addresses **Join Dependencies (JD)**. A Join Dependency exists when a table can be split into smaller sub-relations and perfectly reconstructed by joining them back together, without losing or creating records.
It eliminates redundant data combinations by decomposing the table into smaller sub-relations until all remaining join dependencies are explicitly enforced by the **candidate keys**, preventing the generation of spurious (fake) tuples during reconstruction.

Because 5NF handles complex relationships involving three or more interrelated composite keys, it is applied in:
- **Complex Multi-valued / Ternary Relationships:** Where multiple attributes simultaneously depend on multiple entities (e.g., _Agent_ $\times$ _Company_ $\times$ _Product_).
- **Rigorous Business Rule Enforcement:** To guarantee specific, multi-entity combinations are correctly isolated.
- **High-Integrity Datasets:** Advanced logical modeling where absolute data precision outweighs performance costs.
In practice, 5NF is rarely used beyond theoretical design. Real-world applications typically stop at 3NF or BCNF because over-normalizing into 5NF creates excessive tables, severely degrading query performance due to constant JOINs.
<div class="page-break" style="page-break-before: always;"></div>

que.
25. What is a view in DBMS? Explain the advantages and disadvantages of using views in database design.
---

In a Database Management System (DBMS), a view is a virtual table that does not store data physically on a disk; instead, it stores a predefined SQL SELECT query that dynamically pulls data from one or more underlying base tables whenever the view is called. To the end-user or application, a view looks and behaves exactly like a normal database table with rows and columns.

Advantages of Using Views
- **Enhanced Data Security**: You can restrict access to sensitive information by exposing only specific rows or columns to certain users without giving them access to the base tables.
- **Query Simplification**: Views can encapsulate complex SQL logic, multi-table `JOIN` statements, and aggregations into a single object, allowing users to query them with simple `SELECT * FROM view_name` syntax.
- **Logical Data Independence**: If you change the structural layout of the underlying physical tables, you only need to modify the view definition, meaning external applications querying the view will not break.
- **Storage Efficiency**: Standard views do not duplicate data or require extra physical storage spaces since they only hold the query definition.
- **Data Consistency**: Views provide a standardized, unified format for presenting data across different business units or reporting tools.

Disadvantages of Using Views
- **Performance Overhead**: Standard views run their underlying query every time they are called; if the view contains highly complex joins or calculations over millions of rows, it can drastically slow down response times. 
- **Update Limitations**: Many views are read-only. Views that combine multiple tables, use `GROUP BY` clauses, or contain distinct aggregations generally cannot be targeted for direct data modification (`INSERT`, `UPDATE`, `DELETE`).
- **Dependency Issues**: Views are completely dependent on their underlying source tables; if a base table is dropped, renamed, or a structural column is modified, the associated view will break and fail.
- **Hidden Optimization Complexities**: Because the true query logic is abstracted behind the view, database administrators and developers may find it harder to debug, trace, and optimize inefficient execution plans.
<div class="page-break" style="page-break-before: always;"></div>

que.
26. Write an SQL query to create a view named Employee_View that displays the employee_id, name, and department of employees from the Employee table where the salary is greater than 50,000.
---

```sql
CREATE VIEW Employee_View AS
SELECT employee_id, name, department
FROM Employee
WHERE salary > 50000;
```

- **`CREATE VIEW Employee_View AS`**: This command creates a virtual table named `Employee_View` based on the result set of the subsequent `SELECT` statement.
- **`SELECT employee_id, name, department`**: Specifies the exact columns to be displayed in the view.
- **`FROM Employee`**: Identifies the base table from which to pull the data.
- **`WHERE salary > 50000`**: Applies the conditional filter to ensure only employees earning more than 50,000 are included in the view.
<div class="page-break" style="page-break-before: always;"></div>

que.
27. Can a view be updated? Discuss the conditions under which a view is updatable. Provide an example to illustrate your answer.
---

Yes, a view can be updated. When you update a view, you are actually modifying data in the underlying base table(s). You can also use statements like CREATE OR REPLACE VIEW to modify a view's structure.

- **Single Table Constraint:** The view must reference exactly one base table in the `FROM` clause. Views joining multiple tables or using unnested collections are usually not inherently updatable.
- **No Grouping/Aggregates:** The view definition must not use aggregate functions (e.g., `SUM`, `AVG`, `MAX`, `MIN`), `GROUP BY`, `HAVING`, or `DISTINCT`.
- **No Derived Columns:** The `SELECT` clause cannot contain calculations, mathematical expressions, or literal string values.
- **No Subqueries:** The view definition must not include subqueries.
- **Primary/Unique Keys:** The view must include the primary key (or enough `NOT NULL` unique identifier columns) of the underlying table.

Imagine a base table named `Employees`:

|EmployeeID|Name|Department|Salary|
|---|---|---|---|
|101|Alice|IT|$50000|
|102|Bob|HR|$45000|

You can create an updatable view to safely manage HR employee records:

```sql
CREATE VIEW HR_Employees AS
SELECT EmployeeID, Name, Salary
FROM Employees
WHERE Department = 'HR';
```

Because the view maps cleanly to a single base table without aggregations, you can update it directly:

```sql
UPDATE HR_Employees
SET Salary = 48000
WHERE EmployeeID = 102;
```

This specific `UPDATE` statement is successfully translated by the database and passes through to change Bob’s salary to $48000 in the original `Employees` table.
<div class="page-break" style="page-break-before: always;"></div>

que
28. Compare and contrast a view with a table in DBMS. How does their functionality differ in terms of data storage, access, and updates? 
---

1. Data Storage
	- **Table:** Consumes physical disk space. It is the primary repository where data is durably stored, indexed, and organized.
	- **View:** Occupies almost no physical storage because it only stores the SQL query definition itself (not the resulting data).
2. Data Access
	- **Table:** Users query tables directly using data manipulation language (DML) to get the raw information. It is the source of truth.
	- **View:** Users interact with a view exactly as if it were a table. However, when accessed, the database executes the underlying query on the base tables in real-time.
	- **Functionality & Use Case:** Views are primarily used for **security** (hiding sensitive columns like salaries) and **abstraction** (simplifying complex joins or aggregations into a single easy-to-read name).
3. Data Updates
	- **Table:** Data can be freely added, modified, or deleted using `INSERT`, `UPDATE`, and `DELETE` statements.
	- **View:** Updates through a view are restricted.
	    - **Simple Views:** If the view is based on a single table without any aggregate functions or grouping, you can typically perform `INSERT`, `UPDATE`, and `DELETE` operations that will alter the underlying base table.
	    - **Complex Views:** Views that use `JOIN`s, `GROUP BY`, or `DISTINCT` generally do not support direct updates, as the database engine cannot map the changes back to multiple source tables.
<div class="page-break" style="page-break-before: always;"></div>

que
29. How do views improve data security and simplify complex queries in DBMS? Provide examples to support your arguments. 
---

DBMS views improve data security by hiding sensitive columns and restricting row access. They simplify complex queries by encapsulating complicated logic, joins, and aggregations into reusable, virtual tables.
1. Improving Data Security

- **How they work:** You can grant users access to a restricted view without giving them read permissions on the actual underlying table.
- **Example:** In an `Employees` table containing `Name`, `Department`, and `Salary`, you can create a view called `PublicEmployeeInfo` that excludes the `Salary` column:
```sql
CREATE VIEW PublicEmployeeInfo AS
SELECT Name, Department
FROM Employees;
```

Users querying this view can see names and departments but are completely blocked from viewing salaries.

2. Simplifying Complex Queries

- **How they work:** They store intricate operations once. Instead of repeatedly writing lengthy scripts, users can query the view as if it were a simple, single table.
- **Example:** If you frequently need to combine data from `Employees` and `Departments`, writing `JOIN` queries gets tedious. You can encapsulate this:
```sql
CREATE VIEW EmployeeDetails AS
SELECT e.Name, d.DeptName
FROM Employees e
JOIN Departments d ON e.DeptID = d.ID;
```

To retrieve this joined data, users simply run a straightforward: 
```sql
SELECT * FROM EmployeeDetails;
```
<div class="page-break" style="page-break-before: always;"></div>

que
30. Define a stored procedure. Explain its advantages and disadvantages in database management systems with suitable examples. 
---

A stored procedure is a precompiled collection of SQL statements and procedural logic (like variables, conditions, and loops) stored directly inside a database. It acts like a reusable function, allowing applications to execute complex database operations with a single call.

advantage
- **Performance:** They are precompiled and cached, executing faster than raw, repetitive inline queries.
- **Network Traffic:** Sending just a procedure call instead of long SQL strings minimizes network round-trips.
- **Security:** Prevents SQL injection attacks and restricts direct access to underlying tables.
- **Reusability & Maintenance:** A single centralized procedure can be utilized by multiple applications; updates only need to be made once.

disadvantage
- **Portability:** Proprietary database languages (e.g., T-SQL for SQL Server, PL/SQL for Oracle) make procedures hard to migrate across different database systems.
- **Debugging & Testing:** Troubleshooting stored procedures can be difficult compared to standard application code.
- **Resource Intensive:** Executing complex logic inside the DBMS can cause performance bottlenecks and increase server load.

Real-World Example: Processing an Order

Suppose an e-commerce store needs to process an order. Without a stored procedure, the application might have to send multiple queries over the network:

1. `INSERT INTO Orders`
2. `UPDATE Inventory SET Stock = Stock - 1 WHERE ItemID = 10`
3. `UPDATE Customers SET Points = Points + 10 WHERE CustomerID = 23`

Instead, all of this sequential logic is wrapped into a single, precompiled stored procedure like `ProcessOrder`:

```sql
CREATE PROCEDURE ProcessOrder
    @CustomerID INT,
    @ItemID INT,
    @Quantity INT
AS
BEGIN
    -- Start Transaction
    BEGIN TRANSACTION;

    -- 1. Insert the order
    INSERT INTO Orders (CustomerID, OrderDate) VALUES (@CustomerID, GETDATE());

    -- 2. Update Inventory
    UPDATE Inventory SET Stock = Stock - @Quantity WHERE ItemID = @ItemID;

    -- 3. Update Customer Points
    UPDATE Customers SET Points = Points + 10 WHERE CustomerID = @CustomerID;

    -- Commit if successful
    COMMIT TRANSACTION;
END;
```

To execute this entire sequence, the application simply calls the procedure in one line:  
`EXEC ProcessOrder 23, 10, 2;`
<div class="page-break" style="page-break-before: always;"></div>

que
31. Differentiate between stored procedures and functions in DBMS. Discuss at least three key differences with examples. 
---

1. Return Value Requirement
- **Stored Procedure**: Does not require a return statement. It can pass multiple values back to the calling environment using `OUT` or `INOUT` parameters, or simply output a full data result set.
- **Function**: Must contain a `RETURN` statement. It can only yield a single data value (scalar) or a structured table object.

**Stored Procedure Example (No explicit return value):**
```sql
CREATE PROCEDURE GetEmployeeDept(IN emp_id INT, OUT dept_name VARCHAR(50))
BEGIN
    SELECT department INTO dept_name FROM employees WHERE id = emp_id;
END;
```

**Function Example (Mandatory return value):**
```sql
CREATE FUNCTION CalculateTax(salary DECIMAL(10,2)) 
RETURNS DECIMAL(10,2) DETERMINISTIC
BEGIN
    RETURN salary * 0.15;
END;
```

2. Ability to Modify Data (DML Operations)

- **Stored Procedure**: Can freely read and modify database records using Data Manipulation Language commands like `INSERT`, `UPDATE`, and `DELETE`.
- **Function**: Strictly used for read-only computational operations. It cannot modify table structures or data values because it must avoid side effects during regular queries. 
**Stored Procedure Example (Modifying data):**
```sql
CREATE PROCEDURE UpdateSalary(IN emp_id INT, IN bonus DECIMAL(10,2))
BEGIN
    UPDATE employees SET salary = salary + bonus WHERE id = emp_id;
END;
```
(A function attempting an `UPDATE` query like this would throw a compilation error).

3. Execution and Usage Environment
- **Stored Procedure**: Run independently using specific activation keywords like `CALL` or `EXECUTE`. You cannot use them inside a standard inline filter or projection.
- **Function**: Treated like built-in database expressions. You can integrate them right inside `SELECT`, `WHERE`, `HAVING`, or `JOIN` blocks.

**How to call a Function inline:**
```sql
SELECT name, CalculateTax(salary) AS tax_amount FROM employees;
```
**How to call a Stored Procedure:**
```sql
CALL UpdateSalary(101, 500.00);
```
<div class="page-break" style="page-break-before: always;"></div>

que
32. A company wants to calculate the annual bonus for employees based on their performance rating and current salary. Write a stored procedure to perform this calculation and update the employee records in the database. Include input parameters for salary and rating. 
---

```sql
CREATE OR REPLACE PROCEDURE calculate_employee_bonus(
    p_employee_id INT,
    p_rating VARCHAR(10)
)
LANGUAGE plpgsql
AS $$
DECLARE
    v_salary DECIMAL(10,2);
    v_bonus_percentage DECIMAL(4,2);
    v_bonus_amount DECIMAL(10,2);
BEGIN
    -- 1. Fetch the current salary of the employee
    SELECT salary INTO v_salary
    FROM employees
    WHERE employee_id = p_employee_id;

    -- Exit if the employee does not exist
    IF NOT FOUND THEN
        RAISE NOTICE 'Employee ID % not found.', p_employee_id;
        RETURN;
    END IF;

    -- 2. Determine the bonus percentage based on performance rating
    CASE UPPER(p_rating)
        WHEN 'EXCELLENT' THEN v_bonus_percentage := 0.15; -- 15%
        WHEN 'GOOD'      THEN v_bonus_percentage := 0.10; -- 10%
        WHEN 'AVERAGE'   THEN v_bonus_percentage := 0.05; -- 5%
        ELSE v_bonus_percentage := 0.00;                  -- 0%
    END CASE;

    -- 3. Calculate the bonus amount
    v_bonus_amount := v_salary * v_bonus_percentage;

    -- 4. Update the employee record
    UPDATE employees
    SET bonus = v_bonus_amount,
        performance_rating = UPPER(p_rating)
    WHERE employee_id = p_employee_id;

    RAISE NOTICE 'Updated Employee ID %. Bonus: $%', p_employee_id, v_bonus_amount;
END;
$$;
```
<div class="page-break" style="page-break-before: always;"></div>

que
33. Explain what a trigger is in a DBMS, its components, and how it differs from a stored procedure. Provide an example of a real-life scenario where a trigger would be useful. 
---

A database trigger is a specialized, event-driven program that automatically executes (fires) in response to a specific event occurring on a table or view within a Database Management System (DBMS). Unlike standard code blocks, triggers do not require manual execution or application calls; they act as automated internal guardians to enforce security, validation, and data integrity.

Every database trigger consists of three fundamental components, often referred to as the **E-C-A model**:
1. **Event (E)**: The specific database modification that wakes up the trigger, such as `INSERT`, `UPDATE`, or `DELETE`.
2. **Condition (C)**: An optional boolean expression that determines whether the trigger body should execute after the event occurs.
3. **Action (A)**: The actual block of SQL statementsthat runs automatically if the condition is met.
Additionally, triggers require a specified **Timing** (such as `BEFORE` or `AFTER` the event) and a **Scope** (defining whether it runs `FOR EACH ROW` affected or once per entire SQL statement).

| Feature                 | Trigger                                           | Stored Procedure                                        |
| ----------------------- | ------------------------------------------------- | ------------------------------------------------------- |
| **Invocation**          | Fired **automatically** by database events.       | Called **explicitly** by a user or application.         |
| **Parameters**          | Cannot accept input or output parameters.         | Can freely accept input, output, and in-out parameters. |
| **Transaction Control** | Cannot execute `COMMIT` or `ROLLBACK` internally. | Allows full transaction control statements.             |
| **Return Values**       | Cannot return any values.                         | Can return values or result sets.                       |
| **Scheduling**          | Cannot be scheduled independently.                | Can be scheduled to run as a recurring automated job.   |

A classic, practical use case for a trigger is creating an **immutable audit trail** for sensitive financial data.

Imagine an e-commerce or banking system with an `Accounts` table containing customer balances. If a malicious user or an unexpected application bug alters a balance directly in the database, it can lead to massive security issues.

An `AFTER UPDATE` trigger solves this by watching the `Accounts` table. The moment a balance changes, the trigger automatically captures: 
- The old account balance
- The new account balance
- The exact timestamp of the change
- The database user ID who made the modification

It then immediately writes this information into a separate `Audit_Logs` table. Because this occurs natively at the database level, no application update can bypass it, providing a foolproof history for financial regulators.
<div class="page-break" style="page-break-before: always;"></div>

que
34. Write a trigger in SQL that automatically updates the stock quantity in a "Products" table whenever a new record is inserted into an "Orders" table.
---

```sql
DELIMITER $$

CREATE TRIGGER trg_UpdateStockAfterOrder
AFTER INSERT ON Orders
FOR EACH ROW
BEGIN
    UPDATE Products
    SET stock_quantity = stock_quantity - NEW.quantity
    WHERE product_id = NEW.product_id;
END$$

DELIMITER ;
```
<div class="page-break" style="page-break-before: always;"></div>

que
35. Consider the following trigger: 
   ```sql
   CREATE TRIGGER check_salary 
   BEFORE INSERT ON Employees 
   FOR EACH ROW 
   BEGIN 
	   IF NEW.salary < 0 THEN 
		   SIGNAL SQLSTATE '45000' SET MESSAGE_TEXT = 'Salary cannot be negative'; 
		END IF; 
	END;
   ```
   Analyze and describe what will happen when an attempt is made to insert a negative salary into the "Employees" table

---

1. Trigger Activation
	- The `BEFORE INSERT` clause intercepts the operation.
	- It fires automatically before data writes to the table.
	- The trigger evaluates the data line by line.
2. Condition Evaluation
	- The `IF NEW.salary < 0` statement checks the incoming value.
	- `NEW` represents the row currently being inserted.
	- The condition evaluates to true because the salary is negative.
3. Exception Raising
	- The database executes the `SIGNAL SQLSTATE '45000'` command.
	- State `'45000'` defines a generic user-defined exception.
	- The system aborts the `INSERT` transaction immediately. 
4. Error Message Delivery
	- The database engine rolls back any uncommitted changes.
	- It returns the explicit string: `'Salary cannot be negative'`.
	- No new row is added to the `Employees` table.
<div class="page-break" style="page-break-before: always;"></div>

.