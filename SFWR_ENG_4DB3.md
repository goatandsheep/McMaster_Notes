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
> * **[Relations](#relations)**: diamonds
> * **Is a**: triangle

```flow
set=>operation: Entity Set
att=>start: Attribute
rel=>condition: Relation

att->rel(no)->set
```

* Open arrow: exactly 1
* Closed arrow: 0 or 1
* None: 0-n

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

**Cascade**: when something has a foreign key of something else, a change in one will result in a change in the other

##SQL
: *Structured Query Language*

**Query**:

**Sub-query**: 

> **Note**: Place single constant values in 'quotes'. Put double-quotes to indicate an actual quotation, like 'Murphy<ins>''</ins>s law'.
> 
> Also, don't use the `terminate` command.

**Weak Entity Set**: if the primary key is a foreign key, many many-one relationships

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

###Aggregation
: *Computing numerical results*

* `SUM`
* `AVG`
* `COUNT`
* `MIN`
* `MAX`
* `COUNT(*)`: number of tuples
* `GROUP BY <attribute>, <attribute_n>`: specifies that the aggregation is repeated for every available attribute instead of being done on everything 

> **Note**: `NULL` does nothing, unless everything is `NULL`, in which case returns `NULL`

###Join Operation
: *lala*

####Outer join
: *Allows for inclusion of dangling references by padding them with `NULL`*

	R OUTER JOIN S

> Degree:
> 
> * `FULL`: [default] allows for all columns and all rows
> * `LEFT`: common rows / columns from `rel1`, all from `rel2`
> * `RIGHT`: common rows / columns from `rel2`, all from `rel1`

`Natural`: check for when there are shared values

`ON <condition>`:

####Cross Product
	{{query1.entity1},{query2.entity1}; {query1.entity1},{query2.entityn}}

##Views
: *A type of conceptual schema*

	CREATE [MATERIALIZED] VIEW <name> AS <query>

**Virtual**: not stored, pretty much just a query

**Materialized**: stored in database

##B+ Trees
: *A type of database indexing structure that uses a binary tree*

Each node is >50% full

**Leftward arrows**: children are smaller

**Rightward arrows**: children are larger

-----------

**Indexes**: speed up important queries, but requires additional maintenance

##Relational Algebra
: *lol*

$\sigma$

**Projection**: select certain attributes
$R_1 := \Pi_L(R_2)$ 

**Theta-join**: don't combine repeated attributes
	Query1 $\bowtie_\text{condition}$ Query2 

**Natural join**: combine repeated attributes
	Query1 $\bowtie$ Query2

**Union Compatible**: attributes are exactly the same (number, names, types)

**Bag**: (or *multiset*) set where values can be repeated

**Relational Calculus**: 