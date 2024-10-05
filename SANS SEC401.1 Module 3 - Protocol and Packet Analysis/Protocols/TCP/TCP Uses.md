>[!abstract] TCP Uses
>
>- Flow control to better support changing network and host communication capabilities in real-time
>  
>- Confidence in TCP's ability to perform data receipt validation allows for greater confidence in larger data transmissions (per packet) than other transport layer protocols
>  
>- Example TCP ports: 
>	- FTP Data: 20
>	- FTP: 21
>	- SSH: 22
>	- Telnet: 23
>	- SMTP: 25
>	- DNS: 53
>	- HTTP: 80
>	- HTTPS: 443
>	  
>Application developers can take advantage of transport layer functionality without having to build the capabilities themselves.

### Flow control

>[!example] Flow control: An example
>
>A server is offering a service to which only a handful of clients are currently connected. The server has enough capability to handle substantially more clients, and as such, can handle the small number of currently connected clients with ease.
>
>In such a situation, the server may communicate with the connected clients that they are free to send larger amounts of data at any given time, since the server is not as busy as it could be and can easily keep up with the larger amounts of expected communicated flow).
>
>A little later, more clients connect to the server, resulting in the server being under a heavier load. The server communicates to each connected client that a client is now allowed to send a much smaller amount of data at any given time, as the server is busy and will a more difficult time keeping up with communication flow if the clients are not told to send less data. 
>
>In other words, the server leverages the flow control capabilities of the session to 'speed up' and 'slow down' communication exchange as required.

### Comfort level of sending larger amounts of data (overall) as compared to other transport layer protocols (like UDP)

Because a host can verify the receipt of another host's communication, we can feel much more comfortable in leveraging that session reliability to send more data per packet than we might otherwise. 

The more data exchanged per packet, the less the overhead of the communication becomes (sending 1 packet of 1000 bytes is more efficient than sending 1000 packets of 1 byte)

### Ease at which application developers can take advantage of the functionality of TCP

Instead of requiring a developer to figure out how to perform advanced error checking, re-transmission of communication, flow control etc., a developer can simply offload these desired functions to the transport layer. 

Because these details are automatically handled as part of the TCP mechanisms, developers can instead spend more time working on the core functionality of their application, without worrying about how the underlying communication between hosts will be managed (do not required manual intervention.




