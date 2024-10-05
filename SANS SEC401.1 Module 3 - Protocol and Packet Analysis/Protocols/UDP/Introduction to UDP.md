>[!abstract] UDP: An Overview
>
>- Connectionless (non-session-based) communications
>- Does not provide any 'guarantee of delivery'
>- Requires less overhead than TCP, resulting in performance gains
>- Can work well, even when a small amount of packet loss is acceptable

As compared to TCP, UDP (User Datagram Protocol) is the simpler of the 2 transport layer protocols discussed.

UDP is a useful and important protocol, commonly used by many different applications

UDP's goal is to be an efficient protocol for use on reliable networks. A reliable network is a network in which there is a high level of confidence that a packet, when transmitted, will be received by the destination host. 

Because there is a higher confidence level in the reliability of the network, the functions of other transport layer protocols - flow control, retransmission, validation of delivery - can be sacrificed in order to achieve a greater overall network throughput (performance). It is through the establishment of a session that allows a protocol, such as TCP, to utilize the features of retransmission, validation of delivery, etc.

When it comes to UDP, the sender of a UDP packet simply places the packet on the network and sends it. The sender isn't required to check to see if the receiving host is available prior to the transmission, nor are they required to notify the receiving host that a communication is being sent. 

After the sender transmit the UDP packet, the transport layer of the sender essentially 'forgets' that the packet was even sent, and it never confirms that the packet was received. Without a provision for a receiver to be aware that a communication is forthcoming, there is also no guarantee that the packets that do arrive will arrive in the same order as they were sent. 

None of this is of consequence to UDP: If any of this is consequential, there are only 2 options:
- Utilize TCP
- Build the desired functionality into the application that is communicating
In short, UDP does very little error checking or exception handling of any kind.

>[!tip] TCP vs UDP: Rate of transmission
>
>Statistically speaking, error checking is hardly ever needed on a fast, relatively error-free network, as almost all packets arrive (and in proper order). 
>
>It is by doing away with the overhead of the validation performed by TCP that UDP can transmit data at a much higher rate (all things considered equally).

If validation is considered important (but isn't performed at a lower layer of the OSI model), the validation must be performed at a higher layer (most commonly the Application layer).

If the validation is to be performed by the application at the Application layer, it would have to assume the extra burden of planning for exceptional conditions. The error-handling code of the application would only be invoked if an actual error occurred, as opposed to potentially every time a protocol operation happened. 

This approach saves a lot in the nature of CPU time, which results in better overall system performance. Although this approach puts more of a burden on the application programmer, it also provides the programmer with a great deal of flexibility and power with which to work.

>[!info] Validation in UDP-based applications
>
>##### UDP's Nature
>    
>    - **No Built-in Reliability**: Since UDP doesn't guarantee that data will arrive at its destination (or that it will arrive in the correct order), any validation of data integrity must be done by the application at the **Application Layer**. UDP will send packets as fast as it can without waiting for acknowledgments or error corrections.
>    - **No Connection Overhead**: UDP is efficient because it avoids the overhead of connection setup, teardown, and reliability mechanisms like retransmissions or sequence tracking that TCP uses. But this efficiency comes at the cost of leaving data validation to the higher layers.
>
>##### Application's Responsibility
>    
>    - **Error Handling and Validation**: The application has to assume a larger role in detecting and handling issues such as:
>        - **Missing packets**: The application needs to be able to detect and potentially request retransmission of lost packets (if that's critical to the application).
>        - **Out-of-order packets**: If the order of the packets is important (such as in streaming or gaming applications), the application must reassemble packets in the correct order.
>        - **Corruption**: The application may need to implement checksums or hashes to validate the integrity of the data received. While UDP has a checksum option, it's not as robust as other mechanisms, so the application might want to include additional verification.
>
>##### Flexibility and Performance
>    
>    - **CPU Efficiency**: Because UDP avoids connection management and validation overhead, it’s extremely fast. The application, in turn, only deals with exceptions (such as invalid packets) rather than validating every packet at the network level. This can lead to significant performance gains, especially in scenarios where high throughput and low latency are important, like in video streaming, voice-over-IP (VoIP), or gaming.
>    - **Programmer's Burden**: The trade-off, as mentioned before, is that the application developer needs to implement logic for error handling, reordering, retransmission (if necessary), and data integrity checks. The more complex the protocol the application needs, the more work the developer has to do.
>
>##### Application-Level Protocols on UDP
>    
>    - Many application protocols built on top of UDP (e.g., DNS, VoIP, certain streaming protocols) implement their own mechanisms for dealing with UDP's unreliability:
>        - **DNS**: Implements simple retransmission logic. If a response isn’t received within a timeout period, it retries the request.
>        - **VoIP**: Uses real-time transport protocols (RTP) that can handle packet loss without needing to resend every lost packet (since real-time transmission is more important than reliability).
>        - **Custom Protocols**: Developers often design custom protocols on top of UDP that fit their specific needs for error correction, reliability, or packet sequencing.

See also: [[Introduction to TCP]]