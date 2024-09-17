>[!abstract]- Denial of Service (DoS) and Distributed Denial of Service (DDoS) 
>**Denial of Service (DoS)**
>Because routers are critical devices for any network, their availability being impacted can result in substantial impact for any organisation.
>The impact can be dependent on the length of time of the outage but the impact is often much larger than most anticipate.
>		
>**Distributed Denial of Service (DDoS)**
>A traditional DoS attack might have been launched from one machine, or from one location (from a single IP address).
>
>Because the attack is being launched from a single location, it might allow for defense through the implementation of an Access Control List (ACL) block at an upstream network provider (like a telecommunications provider).
>
>In order to counter this defense, the adversary will launch the attack from many different locations simultaneously.
>Blocking a DDoS attack, using ACLs, is much more difficult, if not impossible, especially if the organisation is attempting to implement the block in their own networking infrastructure.
>
>Content Distribution Network (CDN) providers can sometimes provide potential relief from a DDoS attack by leveraging their own massive network infrastructure to handle both the attack and legitimate traffic at the same time. However, the ability of a CDN to provide relief is based upon how much money the organisation is willing to spend on such a service, and the size of the attack itself.

>[!abstract]- Packet Sniffing 
>- Refers to the capture (and analysis) of the traffic of a network 
>- Confidentiality and integrity can be heavily impacted by sniffing of network traffic

>[!abstract]- Packet Misrouting and Routing Table Poisoning
>Packet Misrouting and Routing Table Poisoning attacks both fit into the category of integrity-based attacks. In either attack, victim routers are convinced to re-configure how and where they will route their traffic.
>		
>**Packet Misrouting**
>- With packet misrouting, a router's configuration is manipulated such that the traffic is no longer routed properly and might be routed to non-existent network locations or traffic might be sent back to a previous router (routing loop)
>		
>**Routing Table Poisoning**
>- Results in the modification of a victim's router routing table
>- Routers use their routing tables to determine the next best routing hop (which best router to next send traffic to), as network traffic moves from router to router
>- Routers often update their tables by conversing with their routing peers, allowing for routers to dynamically update and re-route traffic as necessary
>
>>[!bug] What happens in a routing table poisoning attack?
>>In a routing table poisoning attack, the adversary convinces a router to update its routing table, resulting in traffic redirection.
>>
>> This redirection might redirect traffic to routers of an adversary's choosing (perhaps routers controlled by adversary), facilitating an adversary getting access to victim's routed traffic (e.g. of a MiTM attack).
>>
>> A redirection of traffic is not always immediately evident to the victim organisation because network communication is not impeded.
>>
>> This is the reason that MiTM attacks can be devastating for an organisation; communication continues to be sent and received successfully, but the victim is unaware the communication is transiting through an untrusted third party.


See also: 
[[Switch vs Router]]
[[Attacks against Switches]]