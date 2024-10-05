![[IPv4 Header Diagram.png]]
\
Above is an example of an IPv4 header, containing fields of data that can help describe aspects of data communication.

Across the top of the diagram, the numbers represent the numbers of bits in each row of the header. 

>[!abstract] Note
>Note that the leftmost number starts from 0.

As 8 bits is equal to 1 byte, it can be common to see the top of the header labelled in bytes instead of bits (**0 to 3 bytes** instead of **0 to 31 bits**).

### IPv4 Header: Key Fields
#### Version, 4 bits
This field identifies the version of IP used to create the header. A value of 4 (decimal) indicates IPv4 and correspondingly,  a value of 6 (decimal) represents IPv6.

#### Protocol, 8 bits
This field identifies the encapsulated protocol. It contains an integer value, which denotes the exact type of IP message encapsulated in the packet. 
- TCP packet: 6 (decimal value)
- UDP packet: 17 (decimal value)
- ICMP packet: 1 (decimal value)
Some analysts refer to this field as a field that indicates which header comes next on the packet.

#### Time to Live (TTL), 8 bits
This field tells us the number of router 'hops' a packet can transit prior to the packet's expiration. If a destination router can be reached in less hops than allowed by the TTL, it will not expire prior to delivery. 

>[!warning] Why do packets need to expire?
>
>Without expiration, a packet might 'live' forever, especially in the case of an availability issue (such as a router loop). In such a situation, packet after packet will continue to get transmitted circling from router to router endlessly. 
>
>This can eventually lead to subsequent overwhelming of routers (a DoS).

>[!abstract] TTL: An example
>
>If a packet were to be created with a value of TTL at 32 in the header, the packet can transit through a maximum of 32 routers on its way to its destination network. Each time it passes through a router, the router will subtract a value of 1 from the TTL. This decrementing of the TTL continues for each subsequent router.
>
>If a router subtracts 1 from the TTL and it arrives at a value of 0, the packet will be classified as expired. As a result, the router will drop this packet.
>
>A router in such a situation may (if configured to do so) send an ICMP communication to the original sender to let the sender know that its packet was not successfully delivered due to the expiration of the TTL. 

TTL helps packets in a routing loop to expire quickly and stop competing for network resources.

##### Fragmentation, 16 bits (3 for flag and 13 for Fragment Offset)
>[!faq] What if a router encounters a packet that is too large for it to transmit in one go?
>
>In such a situation, rather than signaling an error to the sender, most routers simply fragment the packet and send those fragments on their way.
>

Fragmentation can occur when packets traverse different types of network data links as some network technologies provide for different packet size maximum. 

The fragment offset field indicates to the receiver where a particular fragment should be placed in relation to the other fragments of the original packet, such that the fragments can subsequently be reconstructed into the larger whole. 

#### Source Address and Destination Address, 32 bits (each) 
Of course, the computers involved in the communication, and all the routers and network devices between them, need to know who is talking to whom. 
- Source address: IP address of sender
- Destination address: IP address of intended recipient

#### Options (less common/necessary today)
>[!faq] What is the minimum length of an IPv4 header?
>
>As shown above diagram, a single "row" consists of fields that add up to 32 bits (4 bytes). There are 6 such "rows". with the last being `Options`, which is optional.
>
>Hence, the minimum length of an IPv4 header is the combined length of the different fields, which is calculated as:
>
>5 (rows) x 4 (bytes) = 20 bytes
>
>Hence, the minimum length of an IPv4 header is **20 bytes**.

If options (optional) happen to be set, the length of the IPv4 will extend beyond the size of 20 bytes. 

The possible options can be of variable length, but the options field must always end on a 4-byte boundary. This means that regardless of the specific length of the option itself, it must be padded to ensure that the total length is a multiple of 4 bytes. 
As such, each option will result in an increase in the IPv4 header length of 4 bytes minimum (per option).

While there are valid uses for IPv4 options (especially for network troubleshooting), they are rarely used by legitimate network traffic today. The presence of IPv4 options in an IPv4 header might indicate a malicious aspect to the communication.

More information about the Options Field in the IPv4 header: https://www.tutorialspoint.com/options-field-in-ipv4-header