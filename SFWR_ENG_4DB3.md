#SFWR ENG 4DB3

* *Professor*: Dr. Chiang
* *Winter 2015*
* McMaster University
* *Primary Author*: Kemal Ahmed

---------

##Introduction

**Database Management System (DBMS)**: 

Typically, we represent each set of related data in a *tuple*. Each tuple could describe information about a student or a movie. We call each of these sets **relations**.

**Attribute**: characteristics that are defined in the database, e.g. student number, student name, etc. 

**Unique identifier**: something that no other relation has that allows you to identify it as being distinct from other entries 

##Keys

**Key**: a set of 1/+ attributes of a relation that:

* No 2 distinct tuples have the same values in the key fields
* The above is not true for any subset of the key
* e.g. {First name, Last Name}

Types of keys:

* **Superkey**:
* **Candidate key**:
* **Primary Key**: primary keys are unique and <ins>underlined</ins>
* **Foreign Key**: 

`NULL`

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

