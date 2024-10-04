![[TCP Header Diagram.png]]

We shall discuss certain fields in the TCP header that bear additional study. Just like how specific important fields in the header were discussed for the previously covered protocols (IPv4, IPv6, ICMP), it is prudent to gain a deeper understanding of the fields in the TCP header as well. 

This is especially so because TCP is the most utilized Layer 4 (Transport Layer) protocol. 

### Source Port and Destination Port, 16 bits (each)
A port number indicates on a host system where an application is sending and receiving its network communications. There are 65,536 (2^16) possible port numbers, 0 to 65,535. While this is the range of possible port numbers, certain port numbers (like port 0) are reserved and would not be used under normal circumstances.

### Sequence number, 32 bits
The sequence number represents either the ISN (as sent on the SYN in the 3-way handshake), or the accumulated sequence number (a totality of data sent as related to the current packet) indicating the first data octet for the packet being sent. 

### Acknowledgement number, 32 bits
The acknowledgement number indicates the value of the next expected sequence number from a party of the communication. 

>[!tip]- Acknowledgement number: Importance
>
>The acknowledgment number in a TCP segment indicates the next byte that the sender of the acknowledgment expects to receive. This number is crucial for maintaining the order of data packets and ensuring that all packets are received correctly.
>
>- **Reliable Delivery**: TCP is a connection-oriented protocol that provides reliable data transfer. When a sender transmits data, the receiver must acknowledge receipt. The acknowledgment number tells the sender what data has been successfully received.
>
>- **Flow Control**: By indicating which bytes have been received, TCP can manage the flow of data between sender and receiver, preventing overwhelming the receiver with too much data at once.
>
>- **Error Recovery**: If the sender does not receive an acknowledgment within a certain time (due to packet loss or other issues), it will retransmit the data.

### Data offset, 4 bits
Data offset refers to the length of the header. The value in the field indicates the number of 32-bit words (4 bytes) that are contained in the TCP header. The minimum decimal value for this field is 5 to indicate 20 bytes of information (4 * 5 bytes = 20 bytes), as the minimum length of a TCP header is 20 bytes. A decimal value of more than 5 in this field would indicate the use of TCP options.

### TCP flags, 9 bits
TCP flags represent a characteristic of the session's status or of the importance of a specific packet. 

While there were originally only 6 flags, additional flags have been created over time to provide additional functionality. The original 6 flags are:
- Urgent (URG)
- Acknowledgement (ACK)
- Push (PSH)
- Reset (RST)
- Synchronize (SYN)
- Finished (FIN)

The 3 additional flags that have since been added are:
- ECN-nonce (NS)
- Congestion Windows Reduced (CWR)
- ECN-echo (ECE)

These additional flags relate to Explicit Congestion Notification (ECN) which is a way for routers to convey that routers are experiencing congestion (perhaps due to higher volumes of traffic). ECN works by leveraging the functionality of TCP's flow control mechanisms such that clients can assist routers through a reduction in the volume of host communication. 

### Windows Size, 16 bits
The value described by the window size indicates the number of data octets that the sender of this segment is willing to accept (flow control).

### Options, minimum of 32 bits, multiples of 32 bits
If TCP options are used, this field is occupied by a minimum of 4 bytes and consumes multiples of 4 bytes. Unneeded space is padded with zeroes.

Common TCP options include Maximum Segment Size (MSS), Windows scale, Selective ACK (SACK), Timestamp, and No Operation (NOOP).