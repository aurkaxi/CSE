# participation constraints
- participation constraints is applied on the entity participating in the relationship set
	- total participation
	- partial participation
## total participation
- each entity in the entity set is involved it at least one relationship in a relationship set i.e. the number of relationship in every entity is involved is greater than 0
- consider two endities employeee and department therefore an employee entity exist if it has at least one works_for relationship with department entity
- thus the participation of employee in works_for is total relationship
- total participation is represented by double line in er diagram
![[Pasted image 20260611040303.png]]
## partial participation
- each entity in entity set may or may not occcur in at least one relationship in a relationship set
- for example: consider two entities employee and department and they are related to each other via manages relationship 
- an employee must manage a department, he or she could be the head of the department. but not every employee in the company manages the department
- so participation of employee in the manages relationship type is partial i.e. only a particular set of employees will manage the department but not all
(single line)
# strong entity
- the strong entity always have a primary key
- its existence is not dependent on any other entity i.e. it is independent of other entity
- a set of strong entity is knows as strong entity set
- strong entity is represented by a single rectangle
# weak entity
- the weak entity does not sufficient attributes to form a primary key i.e. weak entity don't have a primary key
- a weak entity is dependent on a strong entity to ensure its existence
- a set ow weak entity is known as weak entity set
- weak entity is represented by double rectangle
## weak entity set
- the existence of a weak entity set depends on the existence of a strong entity set (called identifying entity set)
- the relationship associating the weak entity set with the strong entity set is called identifying relationship (depicted using double diamond)
- the participation of weak entity set from identifying relations set is always total
- the identifying relationship is one-to-many relationship from the identifying entity set to the weak entity set
- the discriminator or partial key of a weak entity set is the set of attributes that distinguishes among all the entities of a weak entity set (underlined with a dashed line)
- the primary key of a weak entity set is formed by the primary key of the strong entity set on which the reak entity sets existence dependent, plus the weak entity sets discriminator

>[!example]
>![[Pasted image 20260611044104.png]]
>the professor is strong entity whereas dependent is a weak entity
>id is the primary key (represented with a line) and name in dependent entity is called partial key (represented with dotted line)

# strong entity vs weak entity
| key                         | strong                                             | weak                                                                    |
| --------------------------- | -------------------------------------------------- | ----------------------------------------------------------------------- |
| primary key                 | strong entity always have one primary key          | weak entity have a foreign key referencing primary key of strong entity |
| dependency                  | independent of other entities                      | dependent on strong entity                                              |
| representation              | single rectangle                                   | double rectangle                                                        |
| relationship representation | single diamond                                     | double diamond                                                          |
| participation               | may or may not participate in entity relationships | always participates in entity relationship                              |
# class hierarchy
