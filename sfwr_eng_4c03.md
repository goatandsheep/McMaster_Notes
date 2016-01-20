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

#### TCP

![TCP](http://www.skullbox.net/tcp.jpg)

* Transmission Control Protocol (TCP)
* better for security

## Security

* **Transport Layer Security (TLS)**: an encryption layer on top of the above protocols
  * Deprecated version: **Secure Socket Layer (SSL)**