
Transmission Control Protocol (TCP) is a session-oriented communication protocol, operating at the Transport Layer (Layer 4) of the OSI model.

>[!tip] TCP: An overview
>
>- Works by establishing a session prior to data exchange
>- Session leads to connection-oriented communication
>- Provides a 'guarantee of delivery' by providing 'receipts of successful delivery'
>	- Additional overload required to track packet delivery
>- Other protocols (like HTTP, HTTPS, SSH, etc.) leverage TCP's benefits


**Recall**: The Network layer (Layer 3) of the OSI model is concerned with the work of determining the best path (route) for a communication to take. IP is best-effort; It helps to determine the best path but is unable to guarantee that a communication will ultimately be delivered. 

Determining whether a communication was successfully received by a remote host is something TCP can assist with.

TCP works by establishing a 'virtual' connection' (session) between hosts that desire to communicate. Session establishment refers to a series of steps taken prior to the communication of data that help the communicating hosts agree on aspects of how communication will be handled. TCP initiates a 3-way handshake to establish a connection between hosts. 

Flow control, verification of data received, and retransmission of any missed communication are all examples of benefits obtained through the establishment of a session.

>[!faq] Flow control
>
>Flow control ensures that the transmitting device does not send more data to the receiving device than it can handle. If a device receives more data than it can process or store in memory at any given time, the data is lost and needs to be retransmitted.
>
>TCP regulates the rate of data transmission between the sender and receiver to prevent congestion or overwhelming the receiver.
>
>See: [[Flow Control (TCP)]]

TCP's benefits is the reason why it is considered as the most utilized of the transport layer protocols. 

#### References
- Sheldon, R. (2023, May 31). _flow control_. WhatIs. https://www.techtarget.com/whatis/definition/flow-control