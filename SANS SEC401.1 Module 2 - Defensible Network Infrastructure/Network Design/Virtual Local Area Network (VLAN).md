
>[!abstract] What's a VLAN?
>
>A VLAN is an example of logical segmentation control. This logical control allows for the network to be logically separated into virtual network segments, 
>
>A physical separation is always more robust than a logical one because logical separations are performed by software (and software is only as robust as the code written). Fundamentally, however, VLANS are a very valid form of segmentation and should be leveraged. 

A **VLAN (Virtual Local Area Network)** helps organize a large network into smaller, isolated networks, even though all devices are physically connected to the same switch.

The easiest way to conceptualize a VLAN is to imagine that certain groupings of physical ports on the switch are defined as belonging to specific networks. VLANs receive a self-identifying 'tag'; these tags are subsequently attached to traffic communicated through the switch. This tagging of traffic allows the switch to understand which network segment a communication belongs to. 

>[!info]- VLAN analogy
>
>### Imagine this:
>
>- Think of a **switch** like a huge office building with lots of rooms (physical ports).
>- In a regular office, different departments (HR, Marketing, IT) work in different rooms, but in our switch, everyone is in one big room.
>
>A **VLAN** is like grouping rooms for each department, but instead of rooms, we're grouping the ports on the switch. For example:
>
>- HR might use ports 1–4.
>- Marketing might use ports 5–8.
>
>Even though everyone is physically in the same building (connected to the same switch), VLANs **logically separate** them into different "virtual networks." So HR people only talk to HR people, Marketing to Marketing, and so on.
>
>### How do VLANs know which group traffic belongs to?
>
>- Each VLAN gets a **tag** (like a label).
>- When someone in HR (port 1) sends data, the switch adds the **HR tag** to the traffic.
>- This tag tells the switch, "Hey, this belongs to the HR VLAN."
>- The switch ensures that only the other HR ports (ports 2–4) receive that traffic, even if Marketing is in the same building (switch).

>[!note] Use of VLAN
>
>While VLANs can be used to implement a security segmentation, they are often created by IT and network administrators for ease of management instead. For example, a VLAN may be created to represent the servers. 
>
>Each VLAN is technically its own network and as such, will have its own range of IP addresses, thus separating devices this way does allow for easier management (a certain range of IP address represents a certain group of devices). 

See also: [[Approaches to Network Design#Why network segmentation?|Understanding the "why" behind network segmentation]]