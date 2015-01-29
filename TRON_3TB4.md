TRON 3TB4 Summary
=================

* Instructor: Dr. Lawford 
* *Winter 2015*
* McMaster University
* *Primary Author*: Kemal Ahmed
> Written with [StackEdit](https://stackedit.io/).

##CanBUS

> Controller Area Network

* 2-wire protocol: `CAN_H` and `CAN_L` that allows microcontrollers and devices to communicate without a host computer
* uses <ins>constructive arbitration</ins>
	*  Since 2 wires travel the same length, they experience the same external noise, so you can just remove the noise 
* When both lines have same voltage, signal is *recessive*
* If `CAN_H` - `CAN_L` > 0.9V, signal is *dominant*
* No ground reference, i.e. no ground noise
* Maximum transmission rate: 1 Megabit / s
* Each device has its own priority
  * If the controller is busy when a signal has been sent to it, it will be delayed until it has the highest priority

##Bit Stuffing
> Inserting extra non-data bits into data signals. The extra bits are removed upon being received.
 
This is important for increasing bit rates when they're too slow 

####RZ
> **Return to Zero mode**:
> Pulses will always return to 0 even if there are consecutive pulses. 

The signal is bit-stuffed with 0's

![consecutive pulses](images/rzcode.png)

####NRZ
> **Non-Return to Zero mode**:
> Pulses will never return to 0

The signal is bit-stuffed to keep its value, until the next pulse

![consecutive pulses](images/nrzcode.png)

###Manchester Coding
> A.K.A. **Phase encoding**

**Biphase Manchester**:

**Dominant node**: zeroes

**Recessive node**: ones

**Ethernet** uses <ins>destructive conflict resolution</ins>.

**Prototols**: how to interpret/represent a set of inputs

**Slew Rate**: rate of change of voltage / s; how jagged are your square waves?

**Baud Rate**: number of signals; 1/period

RTR remote messages

**Arbitration**:

**Differential BUS**: when 2 wires travel along the same path, they experience the same external interference. To determine the message, you need to find the difference between the 2 wires, so you actually end up subtracting out the interference

![CAN Data frame](images/can_data_frame.png)

Each CANBUS Node has:

* **Host processor**: generates messages to be sent; deciphers received messages
* **CAN Controller**: takes messages from host and transmits them to the bus
* **Transceiver**:

**Start Of Message (SOM) Bit**:

**Polling**: 

* **Normal mode**: 
* **Loopback mode**: sends TX from controller to RX; don't need acknowledgements
* **Silent mode**: sends RX to TX; more checking if messages are spam
* **Silent-loopback mode**: 

----

Message filtering:

* Software

**ElectroMagnetic Interference (EMI)**:

![Transmission Gate Multiplexor](images/tgate_mux.png)

##Verilog

####Initial Block
: Executed only once, providing initial values for system

####Always Block
: A block wired non-sequentially
> * Infinitely repeated concurrently
> * Can only have one always block

####Blocking assignment
: A block of code where statements *block* the execution of the following statement(s)
> First statement must complete before the second statement
> Identify in this format:
	> ```
	> begin
	> <statements>;
	> end
	> ```