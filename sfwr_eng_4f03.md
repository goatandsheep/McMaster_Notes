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
* **Words** [m]:
* t_com = t_s + t_h * l + m * t_w * l = t_s + l (t_h + m * t_w) ~= t_s + l * m * t_w

**Packet Routing**: old way of routing

**Cut-through routing**: messages broken down into *flits*

* **flow-control digits (flits)**: smaller pieces of messages, usually one word
* 4b to 32B
* All take same route ==> no sequencing information
* Less overhead for error detection

Message size [M]

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