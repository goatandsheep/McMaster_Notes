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
* **Primary Key**: primary keys are <ins>underlined</ins>
* **Foreign Key**: 

`NULL`

**Referential Integrity**: if all foreign key constraints are enforced, i.e. no *dangling references*