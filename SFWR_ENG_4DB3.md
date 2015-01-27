#SFWR ENG 4DB3

* *Professor*: [Dr. Chiang](http://www.cas.mcmaster.ca/~fchiang/courses/db3/W15/schedule.html)
* *Winter 2015*
* McMaster University
* *Primary Author*: Kemal Ahmed

---------

[TOC]

##Introduction

A **database** is an organized way of representing your data and information about your files (found in a **datastore**).

Typically, we represent each set of related data in a *tuple*. Each tuple could describe information about a student, movie, etc. The objects described by these tuples are called **entities**.

Collections of entities are called **entity sets**.

####Relations
: Any associations between several entities

**Relationship Set**: the set of relations associated with a tuple

####DBMS
> **DataBase Management System:**
> 
> * system that allows you to store, access, and organize a database
> * complicated to set up, so mainly used for large data sets
> 
> **Data independence:**
> 
> The way the data is stored does not affect the data stored in a system. Immunity from changes in the organization of the data is called **logical independence**. Immunity from changes in the storage structure is called **physical independence**.

####Concurrent Execution
> * multiple people accessing your database simultaneously
> * multiple processes using the same database simultaneously
> * an advantage of using a [DBMS](#DBMS)
 
####Attribute
: A characteristic defined in the database
> e.g. student number, student name, etc.

####Schema
: The description of the types of data you'll be saving
> * i.e. the columns in the data tables
> * i.e. all the [attributes](#Attribute)

####Relational Database
: A database of tables with a fixed [schema](#schema)

##Integrity Constraints
: **IC**s limit the data that can be entered

####Intra-relational constraint
: A numerical range for attributes

####Inter-relational constraint
: A constraint that relies on the values of other data within the same table

> e.g. if you're trying to sort students by name in a table
	> ```
	> student.name(index=1)>student.name(index=2)
	> ```

####Domain constraint
: What is the range of acceptable data?

####Tuple constraint
: If <kbd>attribute A</kbd> == <kbd>condition</kbd>, <kbd>attribute B</kbd> will have <ins>this</ins> range
> e.g. for all `students`, where <kbd>major</kbd> == <kbd>engineering</kbd>, <kbd>GPA</kbd> > 4

##Keys
: A set of 1/+ attributes of a relation with:
> * No 2 distinct tuples have the same values in the fields in the key fields
> * No subsets of the key are keys
> * e.g. `{First name, Last Name}`

####Unique identifier
: Something that no other relation has that allows you to identify it as being distinct from other entries

###Types of keys

####Superkey
: Any combination of column(s) for which that combination of values will be unique across all rows in a table.

####Candidate key
: A [superkey](#superkey) which you cannot remove any fields.

####Primary Key
: The key that's used to identify a tuple 
> * one **primary key** per table
> * <ins>underlined column names</ins>
> * does not accept <kbd>NULL</kbd> values

####Foreign Key
: The key that contains the primary key of a relation in another table that is used to identify the relation

###Foreign Key Constraints
: When inputs violate constraints, reject the input.
 
####Referential Integrity
: When all foreign key constraints are enforced
> * i.e. no <ins>dangling references</ins>
> * i.e. no references to non-existent relations

##Database Design

When designing your database, you need to consider:

* What entities and relationships are to be in the database
* Poop

####Entity-Relationship Diagram
: ER Diagrams are a way of representing a system
> * **Entity Sets**: rectangles
> * **[Attributes](#attribute)**: ovals

```flow
set=>operation: Entity Set
att=>start: Attribute

att->set
```

#####Binary Relationship


**Many-One Relationship**: 

**Many-Many Relationship**: 


##Data Definition Language

**Data Definition Language (DDL)**: 

**Data manipulation language (DML)**:

**Assertions**: 

###Violations

Violations of constraints from `R` to `S`:

1. Insert / update to `R` introduces values not found in `S`.
2. Deletion / update in `S` causes dangling in `R`.

Response to violations:

1. 

**Cascade**: 

##SQL
: Structured Query Language

**Query**:

**Sub-query**: 

> **Note**: Place single constant values in 'quotes'. Put double-quotes to indicate an actual quotation, like 'Murphy<ins>''</ins>s law'.

###Operators
: Can return:
> * the tuples that satisfy the conditions
> * `TRUE`/`FALSE` 

* Usual operators, like `<`, `>`, `<=`,`>=`, `==`
* `<>`: not equals, usually portrayed by `!=`
* `x = ANY(<subquery>)`: returns `TRUE` iff there exists an element in the subquery that equals `x`
  * Can also be written as `x IN <subquery>`
* `EXISTS(<subquery>)`: returns `TRUE` iff the subquery is not empty
* `ALL`:
* `FROM <database>`: which database?
* `JOIN`: 
* `SELECT <attribute(s)>`: what attributes do you want to return?, could be `*`, i.e. all attributes
* `WHERE <condition>`: a non-mandatory condition on the results of your query
* `(<subquery>) UNION (<subquery>)`: require same schema
* `(<subquery>) INTERSECT (<subquery>)`: require same schema
* `(<subquery>) EXCEPT (<subquery>)`: aren't in both
* `(<subquery>) DISTINCT (<subquery>)`: don't include the stuff in the second subquery
* `(<subquery>) ORDER BY <attribute>`: 

###Saving query as object 

Useful if you want to be able to differentiate between multiple similar queries:

`SELECT t.name` instead of `SELECT name`

`FROM Beers t` instead of `FROM Beers`

`WHERE t.brewer = "Hobbits"` instead of `WHERE brewer = "Hobbits"`

---------------------------------

Conditions: {`TRUE`, `FALSE`, `UNKNOWN`}

###Modifying Databases

Types of modification:

* *[Insert](#insert)*: put new data into tables
* *[Delete](#delete)*: remove data from table
* *[Update](#update)*: change existing data

####Insert

	INSERT INTO <relation> VALUES(<list of values>);

> Insert individual values.
> 
> e.g.
> `INSERT INTO Likes VALUES('Bud','Miller');`

	INSERT INTO <relation> VALUES(<subquery>);
> Insert a subquery into the relation.
> 
> e.g.
> `INSERT INTO ...;`

####Delete
	DELETE FROM <relation> WHERE <condition>

####Update

	UPDATE <relation> SET <attributes to change> = <value> WHERE <condition on tuples>;
