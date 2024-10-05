
There are 2 ways TCP can close a session. The use of Reset (RST), Acknowledgement (ACK) and Finished (FIN) labels represent the different flags that will be set in the packets during the closure.

The 2 main methods for closure are known as graceful closure and abrupt closure. FIN packets are used in the process of a graceful closure; RST packets are used in the process of an abrupt closure.

### Graceful closure

![[TCP Graceful Closure Diagram.png]]

>[!example] 
>
>The client is ready to indicate to the server that it no longer needs to continue communicating. With TCP, either of the communicating parties can initiate the closure of a session (client is chosen in this example arbitrarily).
>
>As part of the 3-way handshake, each host initiated the ability to communicate via the use of SYN packets, and as such, each side must also initiate a termination of its own communication using FIN packets.
>
>Here, the process of a graceful closure begins with a FIN packet from the client to the server, indicating to the server that the client wishes to close its portion of the session. 
>
>Upon receiving the FIN request, the server will acknowledge by sending an ACK packet. Next, the server will send its own FIN packet to the client indicating its wish to close the portion of the session.
>
>Finally, the client sends an ACK packet to the server, acknowledging the receipt of the server's FIN request.

For more information about states like FIN_WAIT_1, refer to https://www.geeksforgeeks.org/tcp-connection-termination/

### Why and when is abrupt closure required?

While a graceful closure will occur in most circumstances, there needs to be an option for a host to terminate a session when communications have broken down.

>[!faq] Why abrupt closure?
>
>An abrupt connection release is carried out when an RST segment is sent. An RST segment can be sent for the below reasons: 
>
>1. When a non-SYN segment was received for a non-existing TCP connection.
>2. In an open connection, some TCP implementations send an RST segment when a segment with an invalid header is received. This will prevent attacks by closing the corresponding connection.
>3. When some implementations need to close an existing TCP connection, they send an RST segment. They will close an existing TCP connection for the following reasons:
>    - Lack of resources to support the connection
>    - The remote host is now unreachable and has stopped responding.

### Abrupt closure

With an abrupt closure, either host can immediately terminate a session by sending a single RST. The moment a host sends a RST packet, the host considers the session terminated.

What is different here, is that in this instance there is not expected response to this change in the state of the session. The other host will not issue a response (not even an ACK). Even if the other host did respond to the RST, the response will be ignored.

>[!tip] Explanation
>
>If there has been a breakdown of the communication, the 'other' host has become unavailable. As such, there would be no way for that other system to respond to the RST (if it even received the RST). 
>
>If it was necessary to wait for an ACK response, a broken session would continue to exist in the memory of a host, leading an an eventual DoS. 

See also: [[Establishing a TCP connection]]
#### References
- GeeksforGeeks. (2022, May 12). _TCP Connection Termination_. GeeksforGeeks. https://www.geeksforgeeks.org/tcp-connection-termination/