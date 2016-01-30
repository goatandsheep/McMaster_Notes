# Summary SFWR ENG 4C03

Kemal Ahmed

Winter 2016

[TOC]

## Internet Architecture

**Datagram**: 

bit (b)

byte (B)

* **Application Layer**: 
  * e.g.
* **Transport Layer**: 
  * e.g.
* **Network layer**: routing of *datagrams* from source to destination
  * e.g.
* **Data Layer**: data transfer between neighbouring network elements
  * a.k.a. **Link layer**
  * e.g.

**Bits per second (bps)**:

**Packet Switches**: forward packets

## Packet Delay

Sources:

* queue in router buffers
* arrival rate > output rate
* read queue

**Link bandwidth** [R]: (bps)

**Packet Length** [L]: (bits)

**Physical link length** [p]:

**Propagation speed** [s]: medium (~3 * 10^8^ m/sec for optic fibre)

1. Processing delay [d~proc~]: negligible
2. Queuing delay [d~queue~]: 
3. Transmission delay [d~trans~]: time to send bits into link = L/R
4. Propagation delay [d~prop~]: p/s

**Nodal delay** [d~nodal~]:  d~proc~ +  d~queue~ +  d~trans~ +  d~prop~

## Application Layer

### Protocol

* Types of messages
* Message syntax
* Message semantics
* Rules: when, how processes send, receive

### Architectures

1. Client-server
2. Peer-to-peer (P2P)
3. Hybrid

### Transport Protocols

#### UDP

![UDP](http://www.skullbox.net/udp.jpg)

* User Datagram Protocol (UDP)
* way better for speed
* used for messaging services, streaming
* Multiplexor / Demultiplexor
* 16-word checksum

#### TCP

![TCP](http://www.skullbox.net/tcp.jpg)

* Transmission Control Protocol (TCP)
* better for security
* Features:
  * Multiplexor / Demultiplexor
  * Reliable data transfer
  * Flow Control
  * Congestion Control

## Security

* **Transport Layer Security (TLS)**: an encryption layer on top of the above protocols
  * Deprecated version: **Secure Socket Layer (SSL)**

## DNS

**Domain Name Server (DNS)**:

* Name servers cache the mappings
* Messages are not sent directly, but rather through multiple DNS first. This is good because
  * You can cache the page instead of bothering the server each request
  * You use an optimal map
* blackadder, baldric.cis.mcmaster.ca
* [dig](https://toolbox.googleapps.com/apps/dig/)
* Thought: could one spoof a server, then send unlimited messages from the IP address they're spoofing

## Socket Programming

`AF_INET`: IP protocol

`SOCK_DGRAM`: SOCKet DataGRAM

`listen()`: wait for incoming connections

**raw socket**:

SSL: encrypting the network socket

## Transport Layer

Internet protocols including UDP and TCP

### Functions

#### Multiplexing/Demultiplexing

1. 32 bits for source port # + destination port #, i.e. 16 bits each, i.e. 2^16 ports
2. Other header fields
3. Application data

#### Reliability

Things like a microwaves can distort your messages. This detects for packets that are erroneous / missing and recovers them

**Utilization**: maximum data rate / bandwidth

##### Error detection

* adding extra bits to each packet
* **Parity Checking**: adding a bit to the end. A very simple mechanism to see if it has been changed
  * **Odd parity**: number of 1s will be odd (after adding parity bit)
  * **Even parity**: number of 1s will be even (after adding parity bit)

**Redundancy**: bits/message bits

	Could tertiary, i.e. base 3 work for analog signal streams (not storage)? Problem is that some signals can be affected by external radiation. Maybe even different colours.

**Bursting Error**:

**2-D Parity checking**:

	1 0 1 0 1 | 1
	1 1 1 1 0 | 0
	0 1 1 0 1 | 1
	--------------
	0 0 1 0 1 | 0

* Helps identify which bit is correct.
* Corner bit is 1 if they are different
* Even parity works best because the corner value needs to be checked and can result in mistakes
* redundant bits = i + j + 1
* redundancy = ((i * j) + i + j + 1)/(i * j)

**carrier**: when you add two numbers and there is a number that carries over to the next base 

**Two's complement sum**: add each of the words together (i.e 4 hex characters)

**One's complement sum**:

1. get two's complement sum
2. remove *carrier*
3. add value of carrier to the first bit.
4. If there is still a carrier, go to step 1

##### Loss Detection

Causes:

* buffer overflow

Methods:

* Label the packets with the packet number. If there's a packet # missing, the receiving server will keep looking for it.
	* Could one spoof the server IP, then send only 1, 3, and 4? The server will send a message to itself and it will start looking for the message.
* **Fin package**: concludes the transmission
* Respond to sender:
	* **Negative ACK (NACK)**:
	* **positive ACK (ACK)**: