# mec incourse 1
1. dbms vs conventional file processing system
2. explain key contraints with proper example and describe the responsibility of dba
3. strong vs week entity
4. concept of cardinality in relationships. types and how do they affect database design
5. role of attributes in e-r model. difference among simple, composite, derived, and multivalued attributes.
# mec incourse 2
1. define normalization. conditions for 2nf, 3nf, and bcnf
2. make bcnf

| student | subject  | teacher |
| ------- | -------- | ------- |
| abc     | database | mno     |
| abc     | c        | pqr     |
| xyz     | database | mno     |
| xyz     | c        | stu     |
candidate key: (student, subject)
3. define null attribute. draw e-r diagram for a university database that contains students, courses, professors, and departments. clearly indicate entities, attributes, relationships, primary key and cardinalities constraints
4. explain aggregate functions in sql. with example 
5. "all super keys are candidate keys but all candidate keys are not super keys"- justify
# niter incourse 1
1. discuss about data models and data abstraction levels
2. assume that two students are trying to register for a course in which there is only one open seat. what component of a database system prevents both students from being that last seat?
3. describe at least three tables that might be used to store information in a social networking system such as facebook
4. "a domain is atomic if elements of the domain are considered to be indivisible units", establish it.
5. consider the employee database:
   employee(person name, street, city)
   works(person name, company name, salary)
   company(company name, city)
   given an expression in the relational algebra to express each of the following queries.
	1. find the id and name of each emploee who does not work for "bigbank"
	2. find the id and name of each employee who earns at least as much as every employee in the database
6. what is the result of first performing the cartesian product of student and advisor, and then performing a selection operation on the result with the predicate Sid=ID? (using the symbolic notation of relational algebra, this query can be written as $sigma_(sid)=ID(student xx advisor)$)
