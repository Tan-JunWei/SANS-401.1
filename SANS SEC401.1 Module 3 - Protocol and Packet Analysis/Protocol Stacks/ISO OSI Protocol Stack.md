
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
The session layer **handles the establishment and maintenance of communication channels (sessions)** between systems. It negotiates a connection, sets that connection up, ensures it remains **open and functional while data is being transferred**, and closes it when communication ends.

- **Synchronization:** This layer allows a process to add checkpoints that are considered synchronization points in the data. These synchronization points help to identify the error so that the data is re-synchronized properly, and ends of the messages are not cut prematurely and data loss is avoided.


##### Layer 4 (Transport)
The transport layer interacts with the **data of a communication and prepares it to be transmitted across the network**. The **primary focus** of the transport layer is to ensure that data packets arrive in the **right order, without losses or errors**, or can be seamlessly recovered if required. 

It is this layer that may ensure **resilient connectivity from end to end** (it provides the **acknowledgment of the successful data transmission** and re-transmits the data if an error is found). 

- **Segmentation and Reassembly**: This layer accepts the message from the (session) layer, and breaks the message into smaller units. Each of the segments produced has a header associated with it. The transport layer at the destination station reassembles the message.


##### Layer 3 (Network)
The network layer **handles the network address scheme and connectivity between multiple network segments**. It describes how systems of different network segments find and communicate with each other. 

- **Routing:** The network layer protocols determine which route is suitable from source to destination. This function of the network layer is known as routing.


##### Layer 2 (Data Link)
The data link layer **connects the physical part of the network** (cables and electrical signals) with the **abstract part** (packets and data streams).


##### Layer 1 (Physical)
The physical layer **handles transmission (information in the form of bits) across the physical media**. This includes examples such as electrical pulses on copper wires, modulation of radio waves, modulation of light pulses in fiber optics, connection specifications between interface hardware and network cabling, and voltage regulation. 


>[!tip] Mnemonic to remember the layers of the OSI model
>
>**"Please Do Not Throw Sausage Pizza Away"**
>
>P : **P**hysical
>D : **D**ata Link
>N : **N**etwork
>T : **T**ransport
>S : **S**ession
>P: **P**resentation
>A : **A**pplication

#### References
- Threat, I. (2023, December 21). _What is OSI Model | 7 Layers Explained | Imperva_. Learning Center. https://www.imperva.com/learn/application-security/osi-model/
- GeeksforGeeks. (2024g, August 30). _What is OSI Model? Layers of OSI Model_. GeeksforGeeks. https://www.geeksforgeeks.org/open-systems-interconnection-model-osi/
- _What is the OSI Model? - 7 OSI Layers Explained - AWS_. (n.d.). Amazon Web Services, Inc. https://aws.amazon.com/what-is/osi-model/