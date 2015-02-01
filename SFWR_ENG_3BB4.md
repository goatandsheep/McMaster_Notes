SFWR ENG 3BB4 Summary
=====================

* Dr. Maibaum
* *Winter 2015*
* McMaster University
* *Primary Author*: Kemal Ahmed

-----------------------------------

This course is about concurrency in systems.

**Concurrent Software**: 

**Distributed Software**:

We represent models of concurrency using finite state machines.

Threads
-------
: *<ins>active</ins> entities because they initiate actions*

> Opposite of [monitors](#monitors)

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

	SWITCH = OFF  
	OFF = (on -> ON),  
	ON = (off -> OFF).
	
	SWITCH = OFF,
	OFF = (on -> (off -> OFF)).
	
	SWITCH = (on -> off -> SWITCH).

One rule of precedence that allows you to remove brackets is that you execute from Right to Left

`(x -> P | y -> Q)`: engages in either the first or second action, depending on the input that selects it

**Concurrency**: 

**Parallelism**: 

*Are there shared actions?*

**Labels**: (`label:Process` | e.g. `a:P`)

**Prefix Labels**: useful for modelling shared resources (`{set of prefix labels}::Process` | e.g. `{a1,..,ax}::P`)

*When you're implementing a parallel database, you need to make sure that you don't do half the re-saving/editing processes before you allow someone else to open the file.*

**Equivalent**: same trace

##Shared Objects
: *How do you allocate access to a resource among multiple processes?*

####Semaphor
: *Something that constricts when you can/cannot run a process*
> You can implement a *handshake* using multiple semaphors that allows you to toggle execution when sharing a resource

**Race Conditions**: the process that gets to the resource the fastest goes first

If you have multiple processes that need to be executed from a given processor that are waiting to be executed on a shared resource, you can push the processes onto a stack and wait, until the resource is free. Using this in conjunction with the semaphores will be nice.

##LTSA
: *Labelled Transition System Analyser*

`ERROR`: predefined process to identify...error

`acquire`

`release`

**livelock**: when processes are waiting for a process to stop using a resource that they are locked into using

####Synchronized
`synchronized`:

`synchronized <object>`: only one person can access a method at a time

##Monitors
: *<ins>passive</ins> entities which respond to actions*  

> * Opposite of a [thread](#threads)
> * The early conception of an object
> * Can be implemented in object-oriented languages, where its use makes it a *monitor*

**Guarded Actions**: modelling by defining the range of the system monitors


* `wait()`: sleeps thread, until notification from another thread
* `notify()`: only runs one thread
* `notifyAll()`: wakes up all waiting threads and the ones that don't get access get put to sleep
	* overkill, so use `notify()` if you know you only have one thread
	* operating system deals with the order in which threads are executed 
