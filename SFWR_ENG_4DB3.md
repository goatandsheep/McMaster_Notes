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

**Data independence:**
: The way the data is stored does not affect the data stored in a system. Immunity from changes in the organization of the data is called **logical independence**. Immunity from changes in the storage structure is called **physical independence**.

**Partial Dependence**
: 

**Transitive Dependence**
: 

####Concurrent Execution

* multiple people accessing your database simultaneously
* multiple processes using the same database simultaneously
* an advantage of using a [DBMS](#DBMS)
 
####Attribute

> A characteristic defined in the database
> 
> e.g. student number, student name, etc.

####Schema

> The description of the types of data you'll be saving

* i.e. the columns in the data tables
* i.e. all the [attributes](#Attribute)

####Relational Database

> A database of tables with a fixed [schema](#schema)

**Advantages**:

* no redundancy
* deletion / updating 


##Integrity Constraints

> (IC): limit the data that can be entered

####Intra-relational constraint

> A numerical range for attributes

####Inter-relational constraint

> A constraint that relies on the values of other data within the same table
>
> e.g. if you're trying to sort students by name in a table
	> ```
	> student.name(index=1)>student.name(index=2)
	> ```

####Domain constraint
: What is the range of acceptable data?

####Tuple constraint

> If <kbd>attribute A</kbd> == <kbd>condition</kbd>, <kbd>attribute B</kbd> will have <ins>this</ins> range
> 
> e.g. for all `students`, where <kbd>major</kbd> == <kbd>engineering</kbd>, <kbd>GPA</kbd> > 4

Keys
----

**Key**:

* A set of 1/+ attributes of a relation with:
* No 2 distinct tuples have the same values in the fields in the key fields
* No subsets of the key are keys
* e.g. `{First name, Last Name}`

####Unique identifier
: Something that no other relation has that allows you to identify it as being distinct from other entries

###Types of keys

####Superkey

> Any combination of column(s) for which that combination of values will be unique across all rows in a table.


**Candidate key**
: A superkey which you cannot remove any fields.

**Composite Key**
: requires multiple keys to uniquely identify it

####Primary Key

> The key that's used to identify a tuple 

* one **primary key** per table
* <ins>underlined column names</ins>
* does not accept <kbd>NULL</kbd> values
* a.k.a. prime attribute, i.e. other attributes are non-prime

####Foreign Key
: The key that contains the primary key of a relation in another table that is used to identify the relation

###Foreign Key Constraints
: When inputs violate constraints, reject the input.
 
####Referential Integrity

> When all foreign key constraints are enforced

* no <ins>dangling references</ins>
* no references to non-existent relations

##Database Design

When designing your database, you need to consider:

* What entities and relationships are to be in the database
* Poop

####Entity-Relationship Diagram

ER Diagrams are a way of representing a system

* **Entity Sets**: rectangles
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


Data Definition Language
------------------------

**Data Definition Language (DDL)**: 

**Data manipulation language (DML)**:

**Assertions**: 

###Violations

Violations of constraints from `R` to `S`:

1. Insert / update to `R` introduces values not found in `S`.
2. Deletion / update in `S` causes dangling in `R`.

Response to violations:

**Cascade**: when something has a foreign key of something else, a change in one will result in a change in the other

SQL
---

> *Structured Query Language*

###Query

> *A command to fetch a specific set of data*

* Each is separated by `;`
* Comments are done using `#`
* 3 Parts:
	* `SELECT <relation>.<attribute(s)>`: what attributes do you want to return? could be `*`; relation is an optional tag
	*  attributes
	* `FROM <database>`: which database tables are we pulling stuff from?
	* `WHERE <condition>`: a non-mandatory condition on the results of your query
	* When you only want certain attributes from a row, delimit using commas, i.e. `SELECT <attribute1>, <attribute2>` 

**Sub-query**: 

> **Note**: Place single constant values in 'quotes'. Put double-quotes to indicate an actual quotation, 
>  'Murphy<ins>''</ins>s law'.
> 
> Also, don't use the `terminate` command.

**Weak Entity Set**: if the primary key is a foreign key, many many-one relationships

###Operators

> Can return:
> * the tuples that satisfy the conditions
> * `TRUE`/`FALSE` 

* Usual operators, like `<`, `>`, `<=`,`>=`, `==`
* `<>`: not equals, usually portrayed by `!=`
* `x = ANY(<subquery>)`: returns `TRUE` iff there exists an element in the subquery that equals `x`
  * Can also be written as `x IN <subquery>`
* `EXISTS(<subquery>)`: returns `TRUE` iff the subquery is not empty
* `ALL`:
* `JOIN`: 
* `(<subquery>) UNION (<subquery>)`: require same schema
* `(<subquery>) INTERSECT (<subquery>)`: require same schema
* `(<subquery>) EXCEPT (<subquery>)`: duplicates are eliminated
* `(<subquery>) DISTINCT (<subquery>)`: don't include the stuff in the second subquery
* `(<subquery>) ORDER BY <attribute>`: 

###String Patterns

* Format: `<attribute> LIKE '<pattern>'`
* Any string: `%`
* Any character: `_`

###Saving query as object 

Useful if you want to be able to differentiate between multiple similar queries:

`SELECT t.name` instead of `SELECT name`

`FROM Beers t` instead of `FROM Beers`

`WHERE t.brewer = "Hobbits"` instead of `WHERE brewer = "Hobbits"`

---------------------------------

Conditions: {`TRUE`, `FALSE`, `UNKNOWN`}

`YEAR(<YYYY-MM-DD>)`

###Modifying Databases

Types of modification:

* *[Insert](#insert)*: put new data into tables
* *[Delete](#delete)*: remove data from table
* *[Update](#update)*: change existing data
* `ALTER`: change the column names

####Insert

	INSERT INTO <relation>(<attributes updated (optional)>) VALUES(<list of values>);

> Insert individual values.
> 
> e.g.
> `INSERT INTO Likes(beer, drinker) VALUES('Bud','Sally');`

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

> *Computing numerical results*

Format: `Aggregation(<query>)` 

* `SUM`
* `AVG`
* `COUNT`
* `MIN`
* `MAX`
* `COUNT(*)`: number of tuples
* `GROUP BY <attribute
*  <attribute_n>`: specifies that the aggregation is repeated for every available attribute instead of being done on everything 

`HAVING`
> Like `WHERE` for attributes only if they are either
 
* A grouping attribute, or
* Aggregated

> **Hints**
> 
> * `NULL` does nothing, unless everything is `NULL`, in which case returns `NULL`
> * If any aggregation is used, then each element of the `SELECT` list must be either:
>   * Aggregated, or
>   * An attribute on the GROUP BY list.

Joins
-----

> *When you want to query columns from multiple tables, you need to join the tables first*

There are multiple types of joins:

![Joins](http://www.codeproject.com/KB/database/Visual_SQL_Joins/Visual_SQL_JOINS_orig.jpg)

####Outer join

> *Allows for inclusion of dangling references by padding them with `NULL`*

	R OUTER JOIN S

> Degree:
> 
> * `FULL`: [default] allows for all columns and all rows
> * `LEFT`: common rows / columns from `rel1`, all from `rel2`
> * `RIGHT`: common rows / columns from `rel2`, all from `rel1`

`Natural`: outputs only when there are shared values

`ON <condition>`: 

####Cross Product

	{{query1.entity1},{query2.entity1}; {query1.entity1},{query2.entityn}}

Views
-----

> *A type of conceptual schema*

	CREATE [MATERIALIZED] VIEW <name> AS <query>

**Virtual**: not stored, pretty much just a query

**Materialized**: stored in database

Indexing Structure
------------------

> *Each index type is useful for tuning the database to the fastest speed for the data you want*

###B+ Trees

> *A type of database indexing structure that uses a binary tree*

Each node is >50% full

**Leftward arrows**: children are smaller

**Rightward arrows**: children are larger

###Index Hash

**Indexes**: speed up important queries, but requires additional maintenance

**Hash index**: think about what a hash is and realize that it works better with specific equalities

**Tree Index**: ranges are fine

Relational Algebra
------------------

relation name := $\pi_\rm{conditions}\sigma_\rm{attributes}(Table_1 \times Table_2 \times etc.)$

relation name := $\pi_\rm{WHERE}\sigma_\rm{SELECT}(FROM)$

*L*: list of attributes of *R*

**Selection**: `WHERE` select tuples with conditions on attributes
$\sigma_c(R)$

**Projection**: `SELECT` certain attributes
$R_1 := \Pi_L(R_2)$ 

**Rename**: when you are joining multiple tables and you have attributes that share the same name, you need to rename them something like `a.attribute` and `b.attribute`
$\rho_{R_1(A_1,...,A_n)}(R_2)$

**Product**: Cartesian product (cross-product) $R_1 \times R_2$

**Theta-join**: don't combine repeated attributes
	Query1 $\bowtie_\text{condition}$ Query2 

**Natural join**: combine repeated attributes
	Query1 $\bowtie$ Query2

**Union Compatible**: attributes are exactly the same (number, names, types)

**Bag**: (or *multiset*) subset where values can be repeated

**Relational Calculus**: 

**Duplicate Elimination**: `DISTINCT` $\sigma$

**Sorting**: sort by the first attribute in L
$R_1 = \tau_L(R_2)$

**Grouping and Aggregation**: `AGG(A)` or `GROUP BY` $\gamma_L(R)$

| A |B | C|
|---|--|--|
| 1 | 2| 3|
| 4 | 5| 6|
| 1 | 2| 5|

becomes

| A |B | C|
|---|--|--|
| 1 | 2| 3|
| 1 | 2| 5|
| 4 | 5| 6|

Precedence of relational operators:

1. $\sigma, \Pi, \rho$
2. $\times, \bowtie$
3. $\cap$
4. $\cup, -$

Functional Dependencies
-----------------------

**(FD)**: `X -> Y`

Splitting the FD: only for right side; left-side is the independent part

> `ABC -> DEF =/= AB -> DEF & C -> DEF`

A set of FDs can help identify the superkey in a relation `X -> R`

DBMS cannot identify FDs nor optimize them

To find out if something is a [key](#keys), see if you can put all the elements on the right side of the relation.  

###Minimal Basis

> A set of FDs without redundancy

* No repeats
* Removing an FD will no longer retain the same meaning
* Increases performance
* A.K.A. **minimal cover**

####Finding Minimal Basis

1. Remove FDs where entities refer to themselves
2. Try looking at each FD and tracing through to see if there is an that results in the same answer, **e.g.** in {`A->B`, `B->C`, `A->C`}, you can remove `A->C`.

**Closure**
: the set of values that are connected using the FDs without repeating, identified by $\rm{set}^+$

The order of elements in the set does not matter

**Anomaly**: unmatched or missing information, caused by limitations or flaws within a given database. Anomalies can often cause redundancy

###Armstrong's Axioms

* Reﬂexivity: If Y ⊆ X, then X → Y .
* Augmentation: If X → Y, then XZ → YZ for any Z.
* Transitivity: If X → Y and Y → Z, then X → Z.
* Union: If X → Y and X → Z, then X → YZ.
* Decomposition: If X → YZ, then X → Y and X → Z.

Decomposing XY → Z can be done by looking at $X^+$ and $Y^+$. If $X^+$ contains Y you can remove Y and vice versa.  

###Normalization

**Atomic Values**: attributes in their most divided form that retain their meaning; simply put, a single-valued attribute (somewhat oversimplified, tho)

**Normal Form** (NF): no redundant data

####Types:

* First NF (1NF): each attribute only contains atomic values, i.e. single-valued
* Second NF (2NF): 1NF characteristics + non-key attributes depend on the primary key
	* Violated if any proper subset of each key contains a non-prime attribute in its closure
* Third NF (3NF): 2NF + non-key attributes don't have dependencies on non-prime keys
	* Decomposition:
		* Lossless Join: satisfied
		* No anomalies: <ins>not satisfied</ins>
		* Dependency Preservation: satisfied
* Boyce Codd NF (BCNF): 3NF + no non-trivial (i.e. redundant) functional dependencies of attributes on anything other than a superset of a candidate key
	* a.k.a. 3.5NF
	* exception: 3NF tables with 2/+ overlapping composite, candidate keys aren't BCNF
	* Decomposition:
		* Lossless Join: satisfied
		* No anomalies: satisfied
		* Dependency Preservation: <ins>not satisfied</ins>

####Information Loss

* Too much data
* Too little data

**FD Loss**: splitting a relation on a dependency that is no longer there

**Join loss**: lossless join

Loss test: A (binary) decomposition of `R = (R, F)` into `R1 = (R1, F1)` and `R2 = (R2, F2)`

1. 

**Dependency preservation**: when the original FD’s are satisﬁed after a join

Concurrency
-----------

> CP: multiple users accessing a database simultaneously

* **Interleaved processing**: asynchronous, 2/+ per CPU, each process runs segmented
* **Parallel processing**: one process / CPU

###Transaction

* `Commit`: finalize the change (changes can be made to database even if commit has not been made)
* `Abort`: 

####Airline example

When multiple people are trying to book the same seats. The second person who books the seat should be notified that the spot has been taken.

###Transaction Properties

* **Atomicity**: transaction acts as a whole or not at all
* **Consistent**: information
* **Isolation**: should operate as only transaction
* **Durability**: each committed change should persist even if system fails before all changes are reflected on disk

**Schedule**
: the order of events in the context of transactions

![Example precedence graph](https://upload.wikimedia.org/math/2/0/1/20181cd3dbfd74266bcd887ef98f595b.png)

**Strict Schedule**
:  a value written or changed by T1 is not read or overwritten by other T2 until T1 aborts or commits

Conflicts
---------

**Write-write conflict**: 

###Serializable 

> Proven using a *precedence graph* (example seen below)

![precedence graph](https://web.archive.org/web/20140718153403/http://db.grussell.org/img/pres2.gif)

**Recoverable**: if you can revert any of the commits and have the same data set you had before the schedule

**Avoid cascading abort (ACA)**: making sure changes in T1 that are aborted don't affect changes in T2. The following has a problem:

![aca](https://upload.wikimedia.org/math/4/4/c/44ceb372adb54067c8e56893840b29a6.png)

ACA compliance avoid this by disallowing transactions from reading 
uncommitted changes from another transactions in the same schedule.

**Serial Schedule**
: a schedule in which transactions are executed consecutively

**Conflict**: schedules are conflicting if:

* Both belong to separate transactions
* Both access the same data item(s)
* At least one of them is "write" operation

**Conflict Equivalent**: a schedule is considered *conflict equivalent* to another if:

* when the two schedules of S1 and S2 involve <ins>the same</ins> set of transactions
* ordering of actions within each transaction is <ins>the same</ins>

**Conflict Serializable**
: a schedule that is *conflict equivalent* to a *serial schedule*

###Locks

> Think *semaphor*. A transaction must acquire a lock before reading / writing. A lock can only be obtained by one transaction at a time. However, transactions can lock onto multiple objects at the same time.

Types:

* **[S]hared lock**: [R]ead lock
* **e[X]clusive lock**: [W]rite lock
* Generic [L]ock: S + X

It does this by either:

* **Aborting**: cancels changes, wasting work
* **Blocking**: restricts read access

####Two-phase locking

> **(2PL)** is a system where a release (i.e. [U]nlock) of any of the locks prohibits all future acquiring of locks

2 phases:

* **growing phase**:
* **shrinking phase**:

![2PL](https://web.archive.org/web/20150316172555im_/http://www.tutorialspoint.com/dbms/images/2PL.png)

**Strict 2PL**: release all locks at the same time, at commit

![Strict 2PL](https://web.archive.org/web/20150316172555im_/http://www.tutorialspoint.com/dbms/images/strict_2PL.png)

###Phantom Problem

**Phantoms**: tuples that are invisible for only part of the transaction execution

> Solutions:
>
> * Lock the entire table
> * Lock the affected column(s)
> * Note: the above are resource heavy

###Isolation Levels

Settings that define the level of concurrency

* **Read Uncommitted**: no read locks
* **Read committed**: short duration read locks
* **Repeatable read**: 
* **[Serializable](#serializable)**: worst at concurrency and performance-wise

**Thrashing**: when the number of transactions increases beyond a certain threshold, the amount of data going through the system decreases

Performance hints
-----------------

**Deadlock**: cycle of transactions waiting for locks to be released by each other

> e.g. if both T1 and T2 need A & B to run, but T1 snagged X(A) and T2 snagged X(B) 

* *Lock the smallest-sized object*: reduces the likelihood that 2 transactions will need the same lock
* *Reduce the time transactions can hold locks*
* *Reduce **hotspots***, i.e. places where there is a lot of activity
* If a transaction has been prolonged for too long, abort, in hopes of eliminating deadlock

**Granularity**: size of data items to lock, i.e. coarse granularity -> larger, fewer locks

**Waits-for graph**: a graph that helps detect deadlock by outlining where the methods need to wait for a resource from a limited number of transactions

**Victim**: 

**Wait-Die**: when a lock is being held by `T2`, `T1` <ins>aborts itself</ins>, unless `T1` has a higher priority, where <ins>`T1` will wait</ins>

**Wound-wait**: when a lock is being held by `T2`, `T1` <ins>waits</ins>, unless `T1` has a higher priority, where <ins>`T2` is aborted</ins>

Priority in this case is dependent on the time it began

Data Cleaning
-------------

> **Problem**: people enter data in wrong, bugs in system may save data incorrectly, join operation problems, corruption, etc.

Solutions:

* Programs only accept certain ranges of data
* Data cleaning crawlers fix data that may be incorrect / doesn't fit in the recommended ranges
	* Use FDs

Characteristics of good data:

* **Pattern**: a set of attributes that satisfy an FD
* **Frequency**: the number of tuples from a given *pattern*
* **Distribution**: graphing frequencies for each pattern

Different distributions have different performance levels

* Uniform: equal frequencies
* Random
* Zipfian: i dunno
* Normal: like in stats

![Normal distribution](https://upload.wikimedia.org/wikipedia/commons/a/a9/Empirical_Rule.PNG)

* Precision: percentage of suggestions that are correct
* Recall: percentage of correct suggestions retrieved