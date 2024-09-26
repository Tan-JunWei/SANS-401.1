
![[OSI Model Diagram.png]]

The OSI model is perhaps the most prolifically referenced of any protocol stack model. 

>[!abstract] Layers of the OSI Model
>
>It divides network communications into **7 layers**. Each layer has no real understanding of any function by a layer above or by a layer below. Each layer is **independently concerned with its own specific function only**.

The 7 layers of the OSI model are as follows:
##### Layer 7 (Application)
The application layer interacts with an application to determine which **network services are required**. When a program requires access to the network, the application layer manages requests from the program to the other layers below.

##### Layer 6 (Presentation)
The presentation layer makes sure that the **data sent from one side of the connection is received in a format that is useful to the other side**. If a sender compresses data prior to transmission, for example, the presentation layer on the receiving end would have to decompress it before it could be used.

##### Layer 5 (Session)
The session layer **handles the establishment and maintenance of connections** between systems. It negotiates a connection, sets that connection up, and makes sure that information exchanges across the connection (session) is **in sync on both sides**.

##### Layer 4 (Transport)
The transport layer interacts with the **data of a communication and prepares it to be transmitted across the network**. It is this layer that may ensure **resilient connectivity from end to end**. The transport layer can also handle the sequencing of packets in a transmission. 

##### Layer 3 (Network)
The network layer **handles the network address scheme and connectivity between multiple network segments**. It describes how systems of different network segments find and communicate with each other. 

##### Layer 2 (Data Link)
The data link layer **connects the physical part of the network** (cables and electrical signals) with the **abstract part** (packets and data streams).

##### Layer 1 (Physical)
The physical layer **handles transmission across the physical media**. This includes examples such as electrical pulses on copper wires, modulation of radio waves, modulation of light pulses in fiber optics, connection specifications between interface hardware and network cabling, and voltage regulation.