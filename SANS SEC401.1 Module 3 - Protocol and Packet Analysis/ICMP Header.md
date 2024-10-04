
![[ICMP Header Diagram.png]]

The ICMP header contains 3 fields, one of which is simply a checksum. 

### Type, 8 bits
The type field contains an integer that identifies which 'type' of ICMP packet is being sent. 

A type is like a category of conditions that are often related. For example, Type 3 is a category with several conditions related to 'destination unreachable'.

### Code, 8 bits
The code field contains an integer that provides additional clarification to the overall 'type' (the condition relayed to the type as described above). The code provides a better understanding of 'what' and 'why'. 

For example, Type 3, Code 1 indicates that a destination is unreachable because the **destination host** is unreachable. Correspondingly, Type 3, Code 3 indicates that a destination is unreachable because the **destination port** is unreachable.

>[!bug]- How information provided by ICMP header fields (Type and Code) may be used by malicious attackers
>
>While the combination of Type and Code can be invaluable for administrators, it can also be very beneficial to attackers as ICMP allows for inference. Considering again Type 3 Code 3, we know that the host is available (if not it would have been Type 3 Code 1) and further that the port we are attempting to communicate with at the remote host is not actively providing a service (**port is unreachable**).
>
>An adversary can use that inference to modify an attack and will eventually find on the remote host an active port with a vulnerable service, leading to an exploit of the system.

The content of the packet's payload might also be important to the receiver of an ICMP communication. This is because when generating an ICMP error message, a system might include the entire IP header plus the first 8 bytes of the IP payload (which happens to be the beginning of a TCP or UDP header, if present) of the packet that caused the error condition. 

This data allows the receiver of the ICMP error message to know which packet caused the error, the destination IP address of the original communication and potentially the source and destination ports.

Knowing this information is vital to sending the error up the stack to the application which sent the original communication, such that the application can be made aware an error has occurred and take necessary corrective action (respond accordingly).

>[!abstract]- Precautionary measures
>
>In some cases, attackers might also generate fake ICMP error messages to disrupt communication or mislead the receiving system, causing it to drop legitimate connections or take inappropriate actions. 
>
>>[!bug] What can possibly happen?
>>When an application receives a fake ICMP error message, it might take unnecessary or harmful actions based on the belief that a legitimate error occurred. 
>>
>>#### Possible scenarios
>>
>>**Premature Termination** of Connections: If an application receives an ICMP "Destination Unreachable" message, it might close the connection prematurely, interrupting legitimate communication. This can cause services to stop, transactions to fail, or users to experience downtime.
>>
>>**Delayed or Stalled Traffic**: An ICMP "Time Exceeded" message could trick the system into thinking that a packet has timed out and should be retransmitted. This can result in unnecessary delays or increased network congestion, slowing down the application.
>>
>>**Dropped Packets**: ICMP error messages could lead the system to drop packets that were actually valid. This could disrupt ongoing data transfers or affect protocols that depend on uninterrupted communication, like TCP, causing retransmissions or connection resets.
>>
>>**Security Implications**: Fake ICMP messages can also be used as part of more sophisticated attacks, like interrupting encrypted traffic (e.g., TLS) to create vulnerabilities or degrade service quality, making the network more vulnerable to further exploitation.
>
>This is basically another case of something useful being exploited by malicious threat actors with different motives. Therefore, it's important to secure ICMP traffic and ensure that systems properly validate ICMP error messages to minimize the risk of exploitation.


### ICMP: Common Types and Codes

Because ICMP types and corresponding codes can be beneficial to both administrator and attacker alike, it is prudent to familiarize ourselves with some of the common and interesting types and codes. 

>[!todo]+ TLDR: Common Types and Codes
>
>- Type 0: Echo reply
>  
>- Type 3: Destination unreachable
>	- Code 0: Network unreachable
>	- Code 1: Host unreachable
>	- Code 3: Port unreachable
>	- Network prohibited
>	  
>- Type 5: Redirect
>  
>- Type 8: Echo request
>  
>- Type 11: Time exceeded
>	- Code 0: TTL expired in transit
>	- Code 1: TTL expired during reassembly

#### Type 0 and Type 8
The first relationship of interest is that neither type has any corresponding code values. While there may not be any corresponding code values, there is **no skipping of any field in the header** (even if the field does not serve any purpose). As such, a value of 0 will be populated into the Code field nonetheless.

The second and more important relationship is that these types are both part of an overall communication that can help to determine if a destination host is 'alive' (operational and responding). 

>[!tip]- How to determine whether a destination host is 'alive'
>
>1. A Type 8, Code 0 (echo request) is sent to a destination host in order to determine its operational status.  
>   
> 2. If it is available (and willing to respond), it does so by responding with a Type 0, Code 0 (echo reply).
>    
>The originator is now aware that the destination host is alive.
>
>In fact, Type 8 and Type 0 are common used by the 'ping' tool to determine host availability and to measure any latency in the back-and-forth communication.
>
>See also: [[Introduction to ICMP]]

#### Type 3
Much of Type 3 is centered around a remote destination being unreachable. There are however, many reasons why a destination might be unreachable, and the code value is meant to provide additional context as to the specific reason why. 

>[!example]- Examples
>
>If a router is unable to pass a packet to the next router on the route to the destination host, it is probable that a network unreachable (Type 3, Code 0) will be returned to the sending host.
>
>If the route is functional but the destination host simply doesn't exist, then a host unreachable (Type 3, Code 1) will be returned.
>
>If some type of administrative access control list prevents access to the destination network, even if the network path exists, a destination network administratively prohibited (Type 3, Code 9) will be returned.
>
>Each one of these example codes for Type 3 **can be leveraged by adversaries to better refine an attack**. 

### Type 11
Type 11 is associated with conditions related to the exceeding of the time limit (TTL = 0).

See also: [[IPv4 Header#Time to Live (TTL), 8 bits|IPv4 Header: TTL field]]