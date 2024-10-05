![[TCP connection diagram.png]]

>[!tip] TCP Handshake
>
>A TCP connection is established by a 3-way handshake in which Initial Sequence Numbers (ISNs) are exchanged.

The handshake that facilitates a TCP session is a 3-way handshake. Segments of the handshake are often named after the TCP header flags that are set. 

The segment containing only a SYN is called "SYN", and the segment containing only a "ACK" is called "ACK". A segment with both SYN and ACK is called "SYN/ACK".

>[!example]- 3-way Handshake Example
>
>##### SYN
>For example, we have a client host initiating a connection to a server host. The client initiates the 3-way handshake by sending a SYN, indicating a desire to request a TCP connection to the server. 
>
>##### SYN/ACK
>If the server is operational and willing to receive the communication, it will accept the incoming connection request and respond to the SYN with a response of SYN/ACK. The ACK is an acknowledgement of the client's initial connection request and a connection request of its own (SYN), altogether in a single segment. 
>
>##### ACK
>Finally, after the client receives the SYN/ACK, it sends the third and final segment (ACK) to the server, acknowledging the server's request to have a connection to the client. Once the server receives the ACK, the 3-way handshake is complete, and the session has been established, and the host systems can now exchange data.

### A deeper understanding of what happens behind the scenes in the 3-way handshake

#### SYN
SYN is the term used to indicate that the computing systems are synchronizing their sequence numbers.

>[!faq] What are sequence numbers?
>
>A sequence number is an integer that will assist in the tracking of data being communicated in either direction. Sequence numbers are randomly chosen by each host and then subsequently exchanged on the SYN segments.

### ACK
ACK is used to acknowledge the next sequence number a host expects to receive from the other host. By carefully considering the ACKs, compared to the amount of data transmitted, a transmitting system can understand what data has, or has not, been received by the other host.

>[!example]+
>
>Using the above 3-way handshake example, the client host sends a SYN to the server host. Prior to the transmission of the SYN, the client host chooses its initial sequence number (ISN). 
>
>Arbitrarily, a value of 500 is assigned for the client's ISN. This ISN value of 500 will be sent with the SYN from the client to the server. 
>
>Upon receipt of the SYN by the server, the server observes that the ISN of the client host is 500. The server acknowledges (ACK) the client's ISN. The ACK contains an integer, representing what the current sequence number of the other host should be **+1**. In this case, the server's ACK will contain the value of 501 (501 +1). 
>
>When the client receives the ACK, the value of the ACK will be compared to its current sequence number. If the ACK represents the current sequence number +1, the client can confirm that the server is in possession of the correct (current) sequence number. This means that the sequence number has been acknowledged. 
>
>The same process happens in reverse, as the server will send its ISN to the client (with the SYN from the server to the client), and the client will respond accordingly with an ACK of the server's ISN +1.

By the end of the 3-way handshake, both computers will be in possession of each other's sequence numbers. Going forward, the sequence number increments by 1, for each byte of data that is transmitted by a party. 

Continuing with the above example, if the client sends 10 bytes of data to the server, the client's sequence number will increment from 500 to 510 (500 + 10). From the server's perspective, upon receipt of the 10 bytes of data sent by the client, the server will use the client's ISN (500), increment by the number of bytes received, and calculate a sequence number of 510. 

>[!note] Next sequence numbers
>
>In TCP, the sender does not explicitly transmit the next sequence number (in this case, 510) to the receiver. Instead, the receiver is responsible for calculating the next expected sequence number based on the data it has received.

The server acknowledges the receipt of the 10 bytes by sending an ACK to the client, containing the value of the next expected sequence number 511 (510+1). When the client compares the server's ACK of 511 with its own current sequence number (510), it will determine that 511 does indeed represent its next sequence number. As such, the client will arrive at the appropriate conclusion that the server would only know the next sequence number if it had received the original 10 bytes transmission (successful data transmission).

>[!abstract] 'Receipts of delivery' in TCP
>
>It is with the exchange of SYNs and ACKs that allow for hosts to have a 'receipt of delivery'.

After the 3-way handshake, for the entirety of the remaining communication, host systems will continue acknowledging each other's next sequence number. This allows for hosts to quickly determine whether data has been successfully received. 

In order to minimize the volume of traffic that could result from sending ACKS on their own, ACKs are 'piggy-backed' as frequently as possible onto packets containing data being sent, as opposed to sending a packet with just an ACK. 