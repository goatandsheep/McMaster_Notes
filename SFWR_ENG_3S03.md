SFWR ENG 3S03 Summary
=====================

* Teacher: Dr. Khedri
* *Winter 2015*
* McMaster University
* *Primary Author*: Kemal Ahmed

-----------------------------------

![Requirements Hierarchy](images/Requirements_Hierarchy.PNG)

Challenges of Software Testing
-----------------------------------

* Budget pressure
 * Project planner underestimates costs of a stage
 * Estimated budget was never approved
 * Safety is required before features 
* Time pressure
 * Lower time pressure with more developers
 * Can happen if there are too many delaying factors
* Managing testing
 * Those who do testing need to be qualified
 * How to test?
     * What?
     * When?
     * How much resources?
 * Ambiguous Requirements, documentation, etc.
 * More environments
 * More languages
 * More layers

Measurement
-----------

**Metric**: a quantitative attribute 

**Measurement**: a mapping from the empirical world to the formal, relational world

**Benchmark**: a standard unit of measurement 

**Measure**: to determine the measurements of something

**Symbol**: a short representation of a unit of measurement

**Manipulate**: combining measurements

###What to measure?

Measure everything useful to achieving your goals.

Sometimes, it can be difficult to describe an attribute using a metric, e.g. colour in nanometres.

Sometimes you want to measure something that is a combination of attributes.

###Types of measurements

**Deductive**: directly measured 

**Inductive**: determined by putting different deduced information together

Models for testing
-----------------------------------

Often, it's not enough to simply say whether something is good or bad, so we define a model that scores it using a combination of metrics that give a quantitative score. That includes:

* Quality of Requirements
* Management issues
* Quality of work
* Productivity
* Cost
 * **Effort**: 
 * **Size**: lines of codes & function points
 * **Productivity**: 
* etc.

* Product: stuff support team measures, e.g. corrective maintenance, usability
* Process: observable at run-time, e.g. complexity, errors
* Resource: hr stuff, manpower, e.g. productivity

Models demonstrate:

1. Things whose effects are neglected
2. Things that affect that model that you didn't consider.
3. Things that you did consider

**Gib's Fuzzy Testing**: 

<ins>Khedri's words of wisdom</ins>: when the company at your internship is doing stuff in a non-systematic way, do what you can to change it.

**COnstructive COst MOdel (COCOMO)**:

```sequence
A->B: h^{nf}
A->B: h
```

$A=(A,F,R)$

$h^{m_R}$ is a subset of P

`(S,F,R)`

A structure is **algebraic** iff $R=0$
`(S,F)`

A structure is **relational** iff $F=0$
`(S,R)`

####e.g. Graphs

$$G = (V,E)
=( \{a,b,c,d\},\{a,d\},\{b,c\},\{a,b\},\{d,c\},)$$

A = V
F = 0
$R = \{E\}$

$h \left ( f\left ( a_1,...,a_{n_y} \right ) \right ) = g \left (h^{n_f} \left ( a_1,..., a_{n_y} \right ) \right )$

####Surjective
: *Nothing goes unmapped*
> * Not [injective](#injective)
> * Could be a <ins>measurement mapping</ins>

![moo](https://upload.wikimedia.org/wikipedia/commons/thumb/6/6c/Surjection.svg/200px-Surjection.svg.png)

####Injective
: *No overlap*
> Not [surjective](#surjective)

![moo](https://upload.wikimedia.org/wikipedia/commons/thumb/0/02/Injection.svg/200px-Injection.svg.png)

####Bijection
: *A function + injective + surjective*
> Every definition is reached once

![moo](https://upload.wikimedia.org/wikipedia/commons/thumb/a/a5/Bijection.svg/200px-Bijection.svg.png)

###Evaluating software

####Likert Scale
: A reliability scale of software where someone selects agreement from a set of {`strongly agree`, `agree`, `neither`, `disagree`, `strongly disagree`}

####Forced Ranking
: Rank the options from 1 (best) to *n* (worst).

####Verbal Frequency
: Select failure frequency from the set of {`Always`, `Often`, `Sometimes`, `Seldom`, `Never`}.

####Comparative Scale
: Pick integer from 1---*n* from `Superior` to `Inferior`

####Numerical Scale
: Pick integer from 1---*n* from `Unimportant` to `Important`

####Statement Type
: blah

###More...

####Homomorphism
: A **homomorphism** or **representation** is a mapping from $A$ to $B$ that preserves the operations of $A$ to the corresponding in $B$. It also weakly preserves the relations in $A$ to their corresponding in $B$.
> i.e. a structure from $A$ to $B$ that satisfies rule 2 (function) and 3 (relation).
> $$h: A  \rightarrow  B$$

: An application of this concept is described in a book called [*Calculus is Algebra* by William Hatcher](https://www.jstor.org/stable/pdfplus/2321645.pdf?acceptTC=true).

The connection between the real $(S, F, R)$ and mathematical worlds $\mathbb{R}_R, F_R, R_R$, using empirical analysis, $\mu_1$.


####McCabe Threshold

$\eta$ measures:

* fault-prone
* maintainability
* Range: 0-10

####Direct Measurement
> ga

####Reliability Model

$$F(t) = 1 - e^{-\left (N - i + 1 \right )at}$$

###Measurement Scales

Scale = (, mapping)

**Algebraic Difference Structure**: 

**Admissible transformation**: allows you to move from scale-to-scale when the attributes and scale are the same

* Integral scale: $g(x) = \alpha\mu(x) + p$
* Ratio scale: $g(x) = \alpha\mu(x)$
* Ordinal scale: strictly monotonic scale
	* 
* Nominal: one-to-one mapping

**Halstead**: 

##Concatenating Scales

####Nominal
* <ins>no order</ins>
* pick from set of categorized responses
* e.g. gender, colour, religion, etc.

####Ordinal
* <ins>ordered</ins>
* non-linear scale
* Arbitrary distance between values
* e.g. satisfaction from 1-4
	* Difference between 1-2 ≠ diff 3-4

####Interval
* ordered
* <ins>linear scale</ins>
* arbitrary zero value

####Ratio
* ordered
* linear scale
* <ins>zero identifies absence</ins>

####Absolute
* ordered
* linear scale
* zero identifies absence
* <ins>cannot be negative</ins>

Empirical Scale
---------------

> derived through experimentation and observation, not theory

Analyzing the difference between reality and mathematical scales

1. Define your empirical relation. It could be any symbol you want. `>>`, `+`, `o`, etc.

$sc = $ 

##Other Stuff again

**Quotient Structure**: MyHill-

MCC**:

**BSEQ**:

**BALT**:

**RSEQ**: $\text(RSEQ)(R_1, R_2) = $

$\mu (x) = \frac{1}{\mu'(x)}$

System Risks
------------

Events that may cause the system to perform in a way that it is not supposed to.

**Correctness**: accuracy

**Integrity**: ensuring your files have not been tampered with, saved, or changed, in an unwanted way

Writing a Testing Plan
-----------------------------------

* Make sure you don't use illegal software
* If it's free, there's probably a license associated with it, so read that license.
* Implied warranty
* Be specific of inputs

**Meaningful transformation**:  

###Parts

1. **Specifications**: correct input and output, i.e. pre- & post-conditions
2. **Methods & Constraints**: 
3. **Methodology**: 
4. **Test tools**
5. **Extent**: how much of the code and why
6. **Data Recording**: 
7. **Constraints**: 
8. **Evaluation**: 

###Project Management

* Unit description
* Milestones (a.k.a. dates)
* Budget
* Test approach
* Functions not tested
* Test constraints

###Principles

1. Include an expected output for each test
2. *Developers should avoid testing their own programs (still debug, tho)*:
	1. dev's perspective is different from users' perspective
	2. Mistakes will be repeated from building to testing
3. *Organizations should avoid testing their own programs*: people have stresses like time that makes people within an organization accept certain mistakes
4. Thoroughly inspect the results of each test.
5. Test cases must be written for input conditions that are invalid and unexpected, as well as for those that are valid and expected.
6. Try to make test cases that you can re-use for other programs
7. Test to prove the program has errors rather than prove it is clean.

* Testing should help locate errors, not just detect their presence.
* Tests should be organized in a way that helps isolate errors

Testing
: Finding the errors in a program, **NOT** proving its correctness

Fault Seeding
: Predicting where your program will fail

Ideal test set
----------------

> A set that shows an error wherever there is an error

For all output ranges, the test is correct if the program outputs something from all ranges of outputs

###Criterion

For a correct program, <ins>any test set is ideal</ins>.

**Edge cases**
: tries around conditions as to break the system

**Compound Conditions**
: Multiple conditions in one conditional or nested loops, e.g. what if `test==2` is always tested, but never `test>4`, it will pass all *path coverage*, but not all *condition coverage* tests. This is different than `if`/`elseif`.

```
if ((test==2 || test>4) {
    invoke_something
}
else {
    do_something_benign;
}
```

**Fine**: a test criteria is *finer* than another if it has stricter criteria

**Complete Coverage**: a test that covers at least one test case from each of the domains of potential inputs

**Statement Coverage**: runs every single line

**Branch Coverage**: (a.k.a. *edge coverage*) runs `TRUE` for each conditional

**Path Coverage**: an extension of *branch coverage*, where you try every single combination of `TRUE`s and `FALSE`s, e.g. (`TRUE`,`FALSE`,`FALSE`), (`TRUE`,`TRUE`,`FALSE`),(`FALSE`,`TRUE`,`FALSE`), etc.

**Condition Coverage**
: tries, true/false for each *compound condition* (one is true, the second is true, neither are true; short-circuiting takes care of both being true)

Things to look for:

* Loops that execute zero times or a minimum number of loops
* Loops that have a maximum number of items
* Loops that execute an average number of times
* Complex criteria
* Nested loops

**Fault Seeding**: a.k.a. *bebugging*, a method of estimating the number of faults in a system. It involves taking the set of errors that you get from one part of a system and retrying it on a different part of the program. 

* [N]: number of initial errors
* [M]: number of new errors
* [M']: number of initial errors that come up again

$$\rm{ratio} = (M - M')\times \frac{N}{M'}$$

Note: random test cases are usually not useful

**Response Time**: total time that a job takes (think external, including connection issues, etc.)

**Turnaround Time**: internal within a system

Testing
-------

###Extent

**Partial Testing**: not testing in every possible domain of inputs

**Total Testing**: testing in every possible domain of inputs

###Types

To make this section easier to read, I'm going to use symbols to summarize what each test is dealing with:

* Code [C]
* Documentation [D]
* User interactions [U]

**Dynamic Analysis**: run the program (requires that you simulate the environment)

**Static Analysis**: syntax checking

####Structural Testing

> Is the system stable?

**Stress Testing** [C]: testing the boundaries of the program, i.e. can systems function under large volumes of inputs. This can also be done by exposing systems to inputs for long periods of time 

**Execution Testing** [C]: performance testing in terms of speed

**Recovery Testing** [C,D,U]: ability to continue after integrity of system is compromised. Revert to a point where the integrity of the system is known and reprocess.

**Operations Testing** [D,U]: completion of documentation, training, etc.

**Compliance Testing** [C,D]: complies to standards, procedures, and guidelines

**Security Testing** [C]: ensuring confidentiality and integrity of private information

####Functional Testing

> Does the program follow the requirements

**Regression Testing** [C,D]: after a change of one component of a system, checking that <ins>other components</ins> still run the same, usually with your previously saved unit tests; this includes updates to documentation

**Parallel Testing** [C]: after a change of one component of a system, checking that <ins>the same component</ins> still runs the same

**Error-Handling Testing** [C]: ensuring most reasonable errors correct themselves

**Manual-Support Testing** [D,U]:  a type of operations testing, ensuring people can still use your program after changes, including documentation changes

**Intersystem Testing** [C,D]: testing changes to the system after applications used by the system are updated

**Control Testing** [U]: making sure the system administrative controls can handle/counter risks 

JUnit
-----

What:
An open source Java testing framework to automate testing

I'm using NetBeans

For each class you want to test:

1. Open the class / bring it into view
2. `Tools` > `Create/Update Tests`: Select the latest JUnit edition and use default settings. This will generate a test file.
3. Scroll down to the function in that test file with `@Test` above it.
4. The other four functions:
	1. `@BeforeClass`: at the beginning of the test cycle, i.e. all the tests
	2. `@Before`: at the beginning of each test
		1. Maybe you'll want to initialize stuff
	3. `@After`: at the end of each test
		1. Maybe you'll want to reset values between tests
	4. `@AfterClass`: at the end of the test cycle
5. You'll notice that each test function will have a `fail` command by default. That is just to make sure you edit the function. Remove it.
6. Put the paramaters of your test and expected output into the variables and press `Run` > `Run File`.
7. If you want to make another test, copy and paste the test function, change the name of the function, and put different values in the variables, i.e. none of the method names matter.

You may want to organize your test file. The convention for comments is using a pound symbol `#`. You also have to manually add something that ignores the comments.

	if (line.startsWith("#")){ //Ignore comments
		continue;
	}

Security
--------

> Some suggestions on where people usually break systems

* Prevent buffer overflows in C/C++ using `strncpy` and `strncat`
* Metacharacters like `;`
	* Allows for command injection
* Automatically created variables in PHP
* Languages that require virtual machines are safer, like Java/C#
* Lack of error handling allows hackers to make their own exceptions
* Symbolic linking: hackers can change the link to their own file