#SFWR ENG 4DB3

* *Professor*: [Dr. Chiang](http://www.cas.mcmaster.ca/~fchiang/courses/db3/W15/schedule.html)
* *Winter 2015*
* McMaster University
* *Primary Author*: Kemal Ahmed

---------

##Introduction

**Database Management System (DBMS)**: system that allows you to store, access, and organize data; complicated to set up, so only used for large data sets

**Concurrent Execution**: one advantage of using a DBMS is that you can have multiple people accessing your database  and multiple processes running simultaneously 

Typically, we represent each set of related data in a *tuple*. Each tuple could describe information about a student, movie, etc. We call each of these sets **relations**.

**Schema**: the description of the types of data you'll be saving, so the columns in the data tables. 

**Attribute**: a characteristic defined in the database, e.g. student number, student name, etc.

**Relational Database**: a database of tables

##Integrity Constraints

**Integrity Constraint**: limits the data that can be entered

* **Intra-relational constraint**: a numerical range for attributes
* **Inter-relational constraint**: a constraint that relies on the values of other data within the same table; e.g. if you're trying to sort students by name in a table, student.name(index=1) > student.name(index=2)
* **Domain constraint**: what is the range of acceptable data?
* **Tuple constraint**: if *attribute A* is *condition*, *attribute B* will have *this* range; e.g. students with major == engineering must have GPA > 4

##Keys

**Key**: a set of 1/+ attributes of a relation that:

* No 2 distinct tuples have the same values in the key fields
* No subsets of the key are keys
* e.g. {First name, Last Name}

Types of keys:

* **Superkey**: when 1/+ subsets of your key is also a key
* **Candidate key**: no subsets of the key are keys; default key type
* **Primary Key**: <ins>underlined column name</ins>; does not allow for `NULL` values 
* **Foreign Key**: 

**Unique identifier**: something that no other relation has that allows you to identify it as being distinct from other entries

**Referential Integrity**: if all foreign key constraints are enforced, i.e. no *dangling references*

###Foreign Key Constraints

##Database Design

**Conceptual Design**: what entities and and relationships are to be in the database

**Entity**: 

**Entity Set**: a collection of similar entities; think classes, objects 

**Attribute**: a property of an entity set

**Relationship Set**: useful for relating information between 3+ entities, but also works for less...

Many-One relationship

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

**Structured Query Language (SQL)**: 

* `SELECT` <ins>attribute(s)</ins>: what attributes do you want to return?, could be `*`, i.e. all attributes
* `FROM` <ins>database</ins>: which database?
* `WHERE` <ins>condition</ins>: a non-mandatory condition on the results of your query

Place single constant values in 'quotes'. Put double-quotes to indicate an actual quotation, like 'Murphy<ins>''</ins>s law'.

###Saving query as object 

Useful if you want to be able to differentiate between multiple similar queries:

`SELECT t.name` instead of `SELECT name`

`FROM Beers t` instead of `FROM Beers`

`WHERE t.brewer = "Hobbits"` instead of `WHERE brewer = "Hobbits"`

---------------------------------

Conditions: {`TRUE`, `FALSE`, `UNKNOWN`}

