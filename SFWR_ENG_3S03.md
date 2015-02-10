SFWR ENG 3S03 Summary
=====================

* Teacher: Dr. Khedri
* *Winter 2015*
* McMaster University
* *Primary Author*: Kemal Ahmed

-----------------------------------

![Requirements Hierarchy](images/Requirements_Hierarchy.PNG)

##Challenges of Software Testing

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

##Measurement

**Metric**: a quantitative attribute 

**Measurement**:

**Benchmark**: a standard unit of measurement 

**Measure**: to determine the measurements of something

**Symbol**: a short representation of a unit of measurement

###What to measure?

Measure everything useful to achieving your goals.

Sometimes, it can be difficult to describe an attribute using a metric, e.g. colour in nanometres.

Sometimes you want to measure something that is a combination of attributes.

###Types of measurements

**Deductive**: directly measured 

**Inductive**: determined by putting different deduced information together

##Models for testing

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

Models demonstrate:

1. Things whose effects are neglected
2. Things that affect that model that you didn't consider.
3. Things that you did consider

**Gib's Fuzzy Testing**: 

<ins>Khedri's words of wisdom</ins>: when the company at your internship is doing stuff in a non-systematic way, do what you can to change it.

**COnstructive COst MOdel (COCOMO)**:

------------------

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

####Bijection
: *A function + injective + subjective*
> Every definition is reached once

####Surjective
: *lala*
> * Not [injective](#injective)
> * Could be a <ins>measurement mapping</ins>

####Injective
: *noonoo*
> Not [surjective](#surjective)

###Evaluating software

####Likert Scale
: A reliability scale of software where someone selects agreement from a set of {`strongly agree`, `agree`, `neither`, `disagree`, `strongly disagree`}

####Forced Ranking
: Rank the options from 1 (best) to *n* (worst).

####Verbal Frequency
: Select failure frequency from the set of {`Always`, `Often`, `Sometimes`, `Seldom`, `Never`}.

####Ordinal Software
: brb

####Comparative Scale
: Pick integer from 1---*n* from `Superior` to `Inferior`

####Numerical Scale
: Pick integer from 1---*n* from `Unimportant` to `Important`

####Statement Type
: blah

###More...

####Homomorphism
: A **homomorphism** or **representation** is a mapping from $A$ to $B$ that reserves the operations of $A$ to the corresponding in $B$. It also weakly reserves the relations in $A$ to their corresponding in $B$.
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

>**Direct Measurement**:
> ga
> 
> Examples:
> * 

####Reliability Model

$$F(t) = 1 - e^{-\left (N - i + 1 \right )at}$$

###Measurement Scales

Scale = (, mapping)

**Algebraic Difference Structure**: 

**Admissible transformation**: allows you to move from scale-to-scale

####Nominal
: *oogachacka*

####Ordinal
: *transitivity*

####Interval
: *comparing stuff on the same interval*

> * Obsolete system, but we should know it :unamused:

####Ratio
: *hee hee*

**Quotient Structure**: MyHill-