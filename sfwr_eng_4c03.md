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

#### TCP

![TCP](http://www.skullbox.net/tcp.jpg)

* Transmission Control Protocol (TCP)
* better for security
* Features:
  * Multiplexor / Demultiplexor
  * Relaible data transfer
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

##### Error detection

* adding extra bits to each packet
  
* **Parity Checking**: adding a bit to the end. A very simple mechanism to see if it has been changed
  
  * **Odd parity**: number of 1s will be odd
    
  * **Even parity**: number of 1s will be even
    
    ​