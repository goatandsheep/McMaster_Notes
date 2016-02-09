SFWR ENG 4F03
=============

Kemal Ahmed

SFWR ENG 4F03

Winter 2016

Ned^2

Note: to be moved to word doc

-------------------

##Memory

**Bus**: switches

**Crossbar**: crossing switches and stuff

* faster than buses
* switches are more expensive

**Direct Interconnects**: 

* **...**: 
* **Toroidal mesh**: 

**Bisection width**: ?

**Indirect Interconnects**:

##Communication

1. Header
2. Message

---

Node latency:

**Bandwidth** [r]: (words/sec)

* **startup time** [t_s]:
* **pre-hop time** [t_h]:
	* time header traverses through a link
	* node latency
* **pre-word time** [t_w]: time for a word to traverse a line
	* 1/r

**Store and forward routing**: start moving the data only after you've received and stored all the data within a message

* **Links** [l]:
* **Words** [m]: size of message
* t_com = t_s + t_h * l + m * t_w * l
= t_s + l (t_h + m * t_w)
~= t_s + l * m * t_w

**Packet Routing**: old way of routing

**Cut-through routing**: messages broken down into *flits*

* **flow-control digits (flits)**: smaller pieces of messages, usually one word
* 4b to 32B
* All take same route ==> no sequencing information
* Less overhead for error detection

**Message size** [M]:

flits = m/k

Header will arrive in l * t_h

Header reaches destination: t_s + l * t_h

Time for a flit to traverse a link: t_w * m/k

1. st flit arrives t_w * m/k after header
2. nd flit arrives t_w * m/k after first

Total t_com = t_s + l * t_h + t_w * m

l doesn't occur in t_w * m

l * t_h << t_w * m, since l is not very large

t_com = t_s + t_w * m

##Ambdahl's Law

r parallel

1-r serial

T_p = (1 - r)T_s + (rT_s)/P

S(p) = T_s / T_p = T_s/((1-r)T_s + (rT_s)/P)

S(P) = 1/(1 - r + r/p) = P/(r + (1-r)p)

S'(p) > 0, S(p) increasing

lim_(p -> inf) S(P) = 1/(1-r)

S(P) <= 1/(1-r)

Problem fixed

###e.g.)

Matrix * vector

A (n * n), x (1 * n), y = A * x

Assume A & X are distributed by rows

* Each process "collects" X
* Each process multiplies in parallel

T_s = n^2

T_p = T_{comm} + n^2/p

T_{comm} = t_s logp + t_w m (p-1)
= t_s log(p) + t_w n/p (p-1)
~= t_s log(p) + t_w n

T_p = t_s log(p) + t_w n + n^2 /p

* Multiplication is done in parallel
* Calculation for each vector is given to a different processor, represented by n/p

S = T_s / T_p
= n^2 /(t_s log(p) t t_w n + n^2/p)
= 1 / (t_s log(p)/n^2 + t_w/n + 1/p)
= P/(1 + t_s plog(p)/n^2 + p/n t_w)

**Efficiency** [E]:

**Nodes** [p]:

E = 1/(1 + t_s plog(p)/n^2 + p/n t_w

if n fixed and p is increasing, E decreases.

n = 10^5
p = 4
(10^5/4 * 10^5) 10^5

p = 10^3

(10^5 / 10^3 * 10^5) * 10^5

Let M be the max number of words (floating-point) that can be stored per mode.

Assume p nodes. We can store M * p words. Matrix of size n takes n^2 memory n^2 = M * p

n = sqrt(M * p)

E = 1/(1+t_s p log(p) + p/n t_w)
= 1/(1 + t_s (p log(p))/(p * M) + t_w * p/sqrt(M * p))
~= 1/(p log(p))
= 1/(1 + t_s/M log(p) + sqrt(p) * t_w/sqrt(M))
~= 1/sqrt(p)

##Gustafson's Law

Assumption:

* **Serial time** [a]:
* **Parallel time** [b]:

work: p * b

T_s = a + p * b

* a is negligible
* b

T_p = a + b

[$\alpha$]:

S = T_s / T_p
= (a + p * b)/(a + b)
= a/(a + b)

alpha = a/(a+b)
= p-alpha(p-1)

S(p) --> p
as p incareases
a <<b
alpha = a/a+b ~= D


Consider addign n numbers on n processors

a0	a1	a2	a3	a4	a5	a6	a7

V	<	V	<	V	<	V	<

a0+a1	a2+a3	a4+a5	a6+a7

V		<		V		<

a0+..a3			a4+..a7

V				<

a0+..a7

O(n), n=2^K

[t_c]: time to add

(t_s + t_w) logn communication

t_c * log(n) to do additions

T_p = (t_c + t_s + t_w) log(n) = O(log(n))

S = T_s / T_p = O(n)/O(lgn) = O(n/logn)

E = S/n = O(1/logn)

Assume p << n processors: each process gets n/p numbers

T_p = O(n/p + log(p))

S = O(n/(n/p + log(p))) = 1/(1/p + log(p)/n) = p/(1 + p log(p)/n)

E = 1/(1 + p log(p)/n)

##Communication

Think: how to determine number of cycles to communicate

(startup time + message * word) * log(p) + propagation

1. Send small message
2. Check time
3. Send slightly larger message
4. Check time
5. Find equation
6. Take y-intercept
7. Treat as optimization problem

7)

* MIN c1, where t_1 = t_2 + c1
* MIN c2, where t_2 = t_3 + c2
