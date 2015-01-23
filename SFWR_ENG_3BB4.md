SFWR ENG 3BB4 Summary
=====================
-----------------------------------

* Dr. Maibaum
* *Winter 2015*
* McMaster University
* *Primary Author*: Kemal Ahmed

-----------------------------------

This course is about concurrency in systems.

**Concurrent Software**: 

**Distributed Software**:

We represent models of concurrency using finite state machines.

Processes and Threads
---------------------

**Sequential process**:

**Processes**: units of sequential execution

<ins>Models of Processes:</ins>

* **Finite State Processes (FSP)**: model processes as sequence of actions in an <ins>algebraic form</ins>
* **Labelled Transition Systems (LTS)**: analyzes, displays, animates behaviour in a <ins>graphical form</ins>

**Labelled Transition Systems Animator (LTSA)**: a cool program

<ins>FSPs follow algebraic rules, such as:</ins>

* Associativity: order of which operations to perform is sometimes irrelevant
* Communitivity: *x + y = y + x*

<ins>State Machine Details:</ins>

* Colour coding is sometimes used
 * Blue generally defines arbitrary states
 * Red generally defines the first state
* An arrow without a head is still the standard for the beginning state, like from [2FA3](https://docs.google.com/document/d/12b0YsgYtB3cnhiu39eKqpl6b2guSE04wUk4Gg8G9nt4/edit)
* Arrow is triggered by a condition and 

**Trace**: a possible sequence of actions; there can be multiple traces for a given FSM

**Maximal trace**: 

**Action** [x]:

**Process** [P]: processes are ALWAYS CAPITALIZED

`(x -> P)`: a representation of a *process*, engaged by an action, x, and does the process, P

###e.g.

`SWITCH = OFF`,  
`OFF = (on -> ON)`,  
`ON = (off -> OFF)`.

`SWITCH = OFF`,  
`OFF = (on -> (off -> OFF))`.

`SWITCH = (on -> off -> SWITCH)`.

----------------------

One rule of precedence that allows you to remove brackets is that you execute from Right to Left

`(x -> P | y -> Q)`: engages in either the first or second action, depending on the input that selects it

**Concurrency**: 

**Parallelism**: 

*Are there shared actions?*

**Labels**: (`label:Process` | e.g. `a:P`)

**Prefix Labels**: useful for modelling shared resources (`{set of prefix labels}::Process` | e.g. `{a1,..,ax}::P`)

*When you're implementing a parallel database, you need to make sure that you don't do half the re-saving/editing processes before you allow someone else to open the file.*

