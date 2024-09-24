
>[!abstract] Segmentation
>
>Segmentation is the idea that the network as a whole, is not a single, trusted entity. Within the network architecture, there are areas of differing **capability, criticality and security risk**. 
>
>- Segmentation means **separation** (of components), resulting in reduced capacity for communication and connection
>- Assets should not be free to communicate unabated
>- Concept of [[Principle of Least Privilege]]

#### How is network segmentation achieved?

Network segmentation can be achieved in different ways, with the most commonly-used example being the establishment of a [[Virtual Local Area Network (VLAN)]]. Segmentation can also be performed by leveraging IPsec, using internal firewalls and [[Approaches to Network Design#Software-Defined Networking (SDN)|SDN]], etc. These examples are examples of logical controls, but physical controls (such as air-gaps) can be used to enforce network segmentation as well. 

#### Software-Defined Networking (SDN)

SDN is a concept that is related to the notion of virtualization. With SDN, we are no longer dependent upon what **underlying network hardware in place**. We can programmatically apply networking concepts in general, including network segmentation. 

- Considers networking from a virtualized concept
- Can visualize the network as a whole and segment accordingly
- Can be achieved programmatically

>[!abstract] SDN
>
>In general, SDN has the potential to take segmentation to the next level, far above the traditional methods of segmentation like using a VLAN. 
>
>**1st reason**
>SDN allows for us to see our environment as a whole - regardless of network boundaries and physical location. Traditional segmentation considers individual segments as applied to a whole of the network, whereas SDN sees and segmentation of the whole, as applied to individual segments. SDN can observe the entirety of the environment and maintain the segmentation of a **dynamically changing network**.
>   
>**2nd reason**
>SDN is beneficial in maintaining segmentation, even in the face of a hybrid cloud environment. With hybrid cloud, an organization has a private cloud and a public cloud component. SDN sees everything (both public and private) and segmentation can be maintained regardless of an asset's **current location**.
 
#### Why network segmentation?

The largest benefit to segmentation is that with segmentation in place, life for the attacker simply becomes more difficult. 

>[!bug] Attacker's motive 
>
>Once an attack gains an initial foothold, they will desire to increase their level of access by pivoting to other machines (attacking other internal machines and moving from one to another), until they have sufficient access to achieve a long-term goal. 
>
>The lack of segmentation makes it easy for an attacker to pivot. If any computing device can communicate with any other computing device on the network, then so can the attacker once they have compromised the computing device. 

See also: [[Networks under attack]], [[Virtual Local Area Network (VLAN)]]