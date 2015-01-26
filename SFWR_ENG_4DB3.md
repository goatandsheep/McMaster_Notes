#SFWR ENG 4DB3

* *Professor*: [Dr. Chiang](http://www.cas.mcmaster.ca/~fchiang/courses/db3/W15/schedule.html)
* *Winter 2015*
* McMaster University
* *Primary Author*: Kemal Ahmed

---------

[TOC]

##Introduction

A **database** is an organized way of representing your data and information about your files (found in a **datastore**).

Typically, we represent each set of related data in a *tuple*. Each tuple could describe information about a student, movie, etc. We call each of these sets **relations**.

####DBMS
> **DataBase Management System:**
> 
> * system that allows you to store, access, and organize a database
> * complicated to set up, so mainly used for large data sets

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
: A constraint that relies on the values of other data within the same tabl

> e.g. if you're trying to sort students by name in a table,
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
: When 1/+ subsets of your key is also a key

####Candidate key
: No subsets of the key are keys
> Default key type

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

* What entities and and relationships are to be in the database

**Entity**: 

**Entity Set**: a collection of similar entities; think classes, objects 

**Attribute**: a property of an entity set

**Relationship Set**: useful for relating information between 3+ entities, but also works for less...

**Many-One relationship**

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

