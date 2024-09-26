>[!info] What are topologies?
>
>Topologies are often used to describe the interrelationship amongst components in an environment. 
>
>In this case, topologies define the inter-relationship of **network-based components,** and can be defined as **physical or logical**. 
>
>>[!tip] Recall: [[SANS SEC401.1 Module 2 - Defensible Network Infrastructure/Contents#Understanding Network Architecture|Network Architecture]]
>>
>>The concept of understanding **network infrastructure** would be described via the use of a **network diagram**, which shows the **topology** of the network.


#### Physical Topology

Physical topologies describe the **physical interrelationship of the constituent components**, like how devices are wired together in a wired network, or how communication is sent over the physical connection (electrical signaling, light pulses, etc. ).

E.g [Star Topology - Advantages and disadvantages](https://www.geeksforgeeks.org/advantages-and-disadvantages-of-star-topology/) 
![[Star Topology.png]]

In a 2nd example, we could look at the various physical mediums that could be used to transmit signals, and **each description could be its own topology** ([[How Physical Mediums Determine Connectivity|Why is this so? ]]).

-  Traditional copper-based cabling: electrical signaling
-  Fiber optic cabling: pulses of light
-  Wireless communication: modulation of radio frequencies


#### Logical Topology

Logical topologies describe how communication is **logically formed prior to transmission**. They might describe how network communication occurs across the various physical mediums, regardless of medium; it describes how (or what) is communicated across the medium. 


>[!tip] Binary
>Binary is used to represent the 2 states of a bit, a **1** or a **0** (an **ON** or an **OFF**). 

##### How does binary relate of physical and logical topologies?

The binary 1s and 0s, and the format and structure of how they are combined to form a communication, would be an example of a **logical topology**.

How those 1s and 0s are re-represented as pulses of lights, electrical signals, etc. would be an example of a **physical topology**.

Understanding how communication occur and whether those communications are physical or logical is imperative to determining if there are risks to those communication.


See also: [[Physical Design]], [[Logical Design]] [[Conceptual Design]]
#### References
- GeeksforGeeks. (2024d, May 29). _Advantages and Disadvantages of Star Topology_. GeeksforGeeks. https://www.geeksforgeeks.org/advantages-and-disadvantages-of-star-topology/
