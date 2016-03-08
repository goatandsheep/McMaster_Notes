# Summary SFWR ENG 4C03

Kemal Ahmed

Winter 2016

[TOC]

## Internet Architecture

**Datagram**: basic transfer unit, essentially a packet

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

##Packet Capturing

**Promiscuous mode**: captures other people's traffic

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

###Persistent

todo

### Transport Protocols

#### UDP

![UDP](http://www.skullbox.net/udp.jpg)

* User Datagram Protocol (UDP)
* way better for speed
* used for messaging services, streaming
* Multiplexor / Demultiplexor
* 16-word checksum

####TCP

![TCP](http://www.skullbox.net/tcp.jpg)

* Transmission Control Protocol (TCP)
* better for security
* Features:
  * Multiplexor / Demultiplexor
  * Reliable data transfer
  * Flow Control: throttled by receiver, so sender reacts
  * Data flows in order
  * Congestion Control: Adjusts transmission rate based on congestion signal
* Both sides must "tear down connection" before either is allowed to stop receiving from the other side

## Security

* **Transport Layer Security (TLS)**: an encryption layer on top of the above protocols
  * Deprecated version: **Secure Socket Layer (SSL)**
  * can happen simultaneously with UDP

## DNS

**Domain Name Server (DNS)**:

* Name servers cache the mappings
* Messages are not sent directly, but rather through multiple DNS first. This is good because
  * You can cache the page instead of bothering the server each request
  * You use an optimal map
* blackadder, baldric.cis.mcmaster.ca
* [dig](https://toolbox.googleapps.com/apps/dig/)
* Thought: could one spoof a server, then send unlimited messages from the IP address they're spoofing

**Time To Live (TTL)**: number of hops until it dies
* Error messages can be dropped. They are sent by the router at which the TTL goes to 0

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

total delay   = Internet delay + access delay + LAN delay 

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
  * **Positive ACK (ACK)**: associated with a unique sequence number

##Congestion Control

**Flow Control**: telling the sender to stop if recipient is receiving too much and/or overwhelming the network

**Output Link Capacity** [R]:

**Max per-connection throughput**: R/2

**Flow conservation**: when you don't lose any packets. This occurs because everything has a finite buffer size

**Original Data** [$\lambda_{in}$]:

**Re-transmitted data** [$\lambda_{Tr}$]:

**Data sent** [$\lambda'_{in}$]: $\lambda_{in} + \lambda_{Tr}$

* If infinite buffer, linear increase until R/2
* In reality, it tapers off because re-transmission of data is necessary
* The difference between the two functions is the amount of re-transmitted data.
* If you have a matrix of multiple routers in a row, you need to be careful as to not cause *deadlock* if you fill up the buffers

**Chunking**: sending more, smaller packets so that if there's an error, you only have to resend that small portion

**Sequence Number**: which chunk? 

* What if the `ACK` gets lost? Wait for timeout and try again, until you can't or connection is closed.

t_transmission = L/R

t_ACK arrives = RTT + t_transmission

**Bandwidth Delay Product (BDP)**: BW * RTT = CW * L

**(CW)**: maximum packets in the pipe

	u_sender= (L/R)/(RTT + (L/R))
			= (CW * L / BW) / RTT

**Window**: a.k.a. buffer

**Sender Window (SW)**: doesn't move until the first packet in the window has been ACK'd

**Receiver Window (RW)**:

**Sliding Window Protocol**: if a packet that is not at the beginning of the queue is acknowledged, you can either move it out or simply mark it as acknowledged and wait before removing it, depending on the importance of the order of arrival 

**Selective Repeat (SR)**:

**Congestion WiNDow (CWND)**: congestion control  

**Receiver WiNDow (RWND)**:

**SW Size (SWS)**: `min(CWND, RWND)`

**RW Size (RWS)**:

**Effective Window**: = SWS - (`LastByteSent` - `LastByteACKed`)

rate = SWS/RTT (bytes/sec)

**Go-Back-N (GBN)**:

**Maximum Segment Size (MSS)**: (bytes)

**Slow-Start THRESHold value** [`ss_thresh`]: initial value is advertised window size

Congestion Control Phases:

* **Slow start (SS)**: `CWND < ss_thresh` starts increase exponentially fast, i.e. double packets sent every RTT
* **Congestion Avoidance (CA)**: `CWND >= ss_thresh` increment CWND 1MSS every RTT

**TCP Taho**: old standard

* After fast-retransmit:

  * cwnd = cwnd
  * ss_thresh = cwnd

* After timeout

  - ss_thresh = cwnd/2
  - cwnd = 1
  - Start slow start

  ​

**TCP Reno**: most common

* Regular:
  * 3 duplicate ACKs, retransmit presumed lost segment
  * congestion avoidance phase
* After fast-retransmit:
  * cwnd = cwnd/2
  * ss_thresh = cwnd
* After timeout: same as Taho

**Additive Increase & Multiplicative Decrease (AIMD)**:

* **Additive Increase**: cwnd+=1 MSS every RTT when no losses
* **Multiplicative Decrease**: cut cwnd in half after loss event

###Three-Way Handshake

**Three-Way Handshake**: how TCP connections establish a connection

**SYNc (SYN)**: determine the starting byte number

**SYN-ACK**: acknowledge sequence number + 1

1. **C** message: `connect()` (SeqC) the initial connect request from the client
2. **S** (SeqS) accompanied by ACK (SeqC+1) `listen()`
3. **C** ACK: SeqS + 1 to identify that the connection request is legitimate `accept()`

###Tear Down

1. **C** FIN, SeqA `close()`
2. **S** ACK, SeqA+1
3. **S** Data, SeqB
4. **C** ACK, SeqB+1
5. **S** FIN, SeqC
6. **C** ACK, SeqC+1

##Internet Protocol

> **Internet Protocol (IP)**: representation of an *interface* NOT a *device*, since you can route to multiple devices with one interface / address

**IPv4**: 32-bit number

**Internet Communication Message Protocol (ICMP)**: (`type`, `code`, first 8 bytes of IP datagram)

**(RIP)**:

**(OSPF)**: 

**(BGP)**:

**Forward Table**: determines what outgoing interface to route packets to

**Longest Prefix Matching**: method of determining how to save the least number of bits to identify IP. Save the longest common prefix once, then save the lower uncommon bits separately

**Switching rate**: 

**Switching Fabric**: 

Types:

* **Memory Fabric**: dynamic, fast, expensive
* **Bus Fabric**: cheap
* **Crossbar Fabric**: think 2DA4

**Fragmentation**: splitting up packets into smaller parts

**Subnet**: 

`Subnet_address` = `IP_Address` + `Subnet_mask`

Size of *subnet* [`10.0.0/24`]: 24 bits for representing an address 

**Broadcast Domain**:

**Gateway Router**:

**Dynamic Host Configuration Protocol (DHCP)**:

**Translation Table**: 

**Network Address Translation (NAT)**: allows for IP-ception, so one address represents them all

`(source_IP_address, port#)` -->

*Incoming datagrams*: replace `(NAT_IP, new_port#)` --> `(sourceIP, port#)` 

**Session Traversal Utilities for Nat's (STUN)**: 


