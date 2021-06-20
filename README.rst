==============================
Improved Traceroute Measurement Protocol
==============================

The purpose of this protocol is to provide an advanced traceroute model that provides
solutions to the challenges posed when using the current traceroute model by giving additional information regarding the buffer sizes which may be a cause of delay in the network and reducing the amount of active traffic added to the network by sending a single packet instead of relying on multiple ICMP messages from IP packets.

Features
--------

The following features were used for this project. I have attached the links to the specific devices

* The user inputs the source address , destination address and the maximum number of hops.
ITMP then sends a packet from the source address to the destination address.
* The switches will increment the count value that indicates the total number of switches
traversed and append their switch ID and queue length to the packet sent from the source
address. ITMP will then compute the delay occurring at the switch after each hop.
* The terminal then displays information regarding the switches that the packet traversed as well
as their corresponding queue length and delays.

Running the ITMP protocol
-------------
Read the installation process from the Documentation link above.

.. image:: https://github.com/CassandraDacha/ITMP/blob/main/topology.png
    :width: 400px
    :align: center
    :height: 400px
    :alt: Circuit Diagram

To compile the ITMP.p4 and start an instance with two switches (S0 a0d S1) and two hosts (h1 with IP address 10.0.1.1 and h2 with IP address 10.0.2.2) run

   $ make 

Once the program is compiled and the mininet command prompt is visible,we need to ssh into the two hosts using the following command

   $ Xterm h1 h2

In `h1`'s xterm, send one packet per second to `h2` using send.py
   say for 30 seconds:

   $ ./send.py 10.0.2.2 "Cassie is cool" 30
 
In `h2`'s xterm, start the server that captures packets:

   $ ./receive.py
   

Credits
-------
A majority of the code detailed above was obtained from https://github.com/p4lang/tutorials/tree/master/exercises
