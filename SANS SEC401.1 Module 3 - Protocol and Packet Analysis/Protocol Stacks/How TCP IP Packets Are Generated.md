
![[TCP IP headers diagram.png]]

>[!abstract] Walkthrough of a network communication as it moves down to TCP/IP stack (Example: Web browser requesting for a webpage)
>
>To begin, the Application Layer takes information from an application that wants to use the network. Let's consider a web browser sending a request for a webpage. The web browser gives the request to the stack's Application Layer, which creates an empty packet (**so no header yet**) and places the request inside. This packet is then sent to the Transport Layer.
>
>The Transport Layer takes the packet and adds a header to it. The header has all information that the Transport Layer on the other side of the communication needs to determine what to do with the packet. After the transport header is put on the packet, it is given to the Internet Layer.
>
>The Internet Layer adds its header to the front of the packet. This header contains data such as the source and destination IP address, which will assist in the movement of the packet from network to network. After this header is attached, the packet is sent to the Network Layer.
>
>When the destination computer receives the data packet, the **reverse operation** occurs. The Network Layer strips off the Network Layer header, performs necessary work, and then passes the remainder of the data packet up to the Internet Layer. The process continues up through the rest of the stack, each layer removing **only the corresponding header information** and performing any necessary work, until the original webpage request reaches the web server application at the Application Layer.





