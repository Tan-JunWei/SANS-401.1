
![[UDP Header Diagram.png]]

There are only a total of 4 fields in the UDP header: Source port, Destination port, Length and Checksum, as shown in the above image. 

>[!info]
>
>Each field is **exactly 2 bytes (16 bits)** long, resulting in a mere 8 bytes of UDP overhead per packet.

>[!faq]+ What is a UDP checksum and what is it used for?
>
>### How the UDP Checksum Works
>
> ##### Checksum Calculation
>    
>    - The sender calculates a checksum value based on the contents of the UDP packet (which includes the header and the data) as well as parts of the IP header.
>    - This checksum is a form of redundancy check, typically a 16-bit value that is derived by performing a mathematical operation (like adding up the binary values of parts of the packet) on the data.
>    - The checksum is then inserted into the UDP header and the packet is sent to the receiver.
>      
>##### Verification at the Receiver
>    
>    - When the packet arrives at the receiver, the receiver performs the same checksum calculation on the received packet.
>    - The receiver compares this newly calculated checksum with the checksum sent by the sender.
>    - If the two checksums match, the packet is considered intact and uncorrupted. If they do not match, the packet is considered corrupted.
>
>### Optional Nature of UDP Checksum
>
>- In IPv4, the UDP checksum is **optional**, meaning that it is possible to disable it (in such cases, the checksum field is set to 0). This is often done in scenarios where error-checking is not needed or to reduce processing overhead.
>    
>- In IPv6, however, the UDP checksum is **mandatory**, meaning it must always be used. This was done to improve error detection in IPv6 networks.

### Source Port and Destination Port, 16 bits (each)

There is 1 additional aspect of port numbers, yet to be discussed, that applies equally for TCP and UDP. 

>[!faq]- What port number to use??
>
>As to which port numbers a system will use (in a general sense), the conversation will be different if we are discussing a server's use of port numbers versus a client's use of port numbers. 
>
>#### Server
>In general, servers have traditionally used port numbers in the range of 1 to 1023, sometimes referred to as **privileged ports** for services they offer.
>
>Because we need servers to consistently be available, a server service will always listen on its assigned port(s), even if the service or server is restarted. We can think of them as statically assigned.
>
>As new services were created over time, available port numbers in said range (1 to 1023) began to dwindle, and as such it is not uncommon to observe some server services using port numbers outside of this range.
>
>#### Client 
>As far as client hosts are concerned, clients are (technically) required to use port numbers in the range of 1023 - 65535. These port numbers have been traditionally referred to as **ephemeral port numbers**. The term "ephemeral" means "for a limited time".
>
>While server services will continue to use the port(s) assigned to them, the same cannot be said of client applications. This is because clients will choose the port numbers to be used for their communications in a non-predictive way, meaning that the port numbers will change on each use of the application. 

>[!abstract] Conclusion
>
>UDP is a good choice for a transport protocol on a fast reliable network where there is a need for high throughput, quick response times, or both.
>
>It is by avoiding expensive error checking that applications can take advantage of UDP's quick and responsive nature. 
>
>>[!bug]+ "Expensive error checking"
>>
>>"Expensive error checking" refers to the computational and network costs associated with ensuring that data sent over a network is delivered correctly and in order. 
>>
>>In the context of transport protocols like TCP (Transmission Control Protocol), error checking includes multiple mechanisms designed to guarantee the reliability of the communication. 
>>
>>These mechanisms introduce overhead, or "expense," in terms of both processing time and network efficiency.
>
>Still, it must be noted that it is not a perfect protocol, and its greatest strength is also one of its greatest weaknesses.

