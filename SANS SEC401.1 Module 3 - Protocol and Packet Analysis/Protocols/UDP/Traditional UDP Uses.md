
>[!abstract] Traditional UDP uses
>
>- Applications where small amounts of occasional packet loss may be acceptable, or where retransmission doesn't make sense
>	- DNS (Domain Name System) requests and responses
>- Applications where the overhead of TCP could impact performance
>	- VoIP and other multimedia exchange
>- Example UDP ports:
>	- DNS: 53
>	- BOOTP/DHCP: 67 and 68
>	- TFTP: 69
>	- NTP: 123
>	- SNMP: 161 and 162
>	- NFS 2049

There are situations in which a small amount of packet loss is acceptable (small amount of packet loss does not result in catastrophic failure of the entirety of the overall communication). 

>[!example] Example: VoIP
>
>An example of such a situation is with real-time communication, such as a VoIP telephone call. If a few packets of the audio from the call are lost, the human brain might automatically error correct and be able to make up for any perceived gap. 
>
>Furthermore, any small gap in the communication is just that small, and a given UDP packet in the VoIP call might represent an insignificant fragment of what is being said that the loss of said packet might not represent anything of substantial value (what compared to the entirety of the communication). Perhaps the packet only represents a part of a word.
>
>Even if the loss of a specific series of packets were to result in a misunderstanding by one of the parties, that party would more than likely ask the other part to repeat what was said (error correction at the human layer).
>
>>[!tip]- Comparison with TCP
>>
>>While true that TCP might result in all packets eventually being received, if the parties have already moved beyond the part of the conversation for which a packet is to about to be retransmitted, not only is the retransmission unnecessary, but it could cause confusion.
>>
>>The overhead required to make TCP useful might, in this case, result in a slowing down of the communication, causing parts of the audio to be elongated and therefore, making the conversation more difficult to understand. 
>>
>>The use of TCP's error correction capabilities, in direct comparison to the performance benefits of UDP, might not only be not worthwhile, but the normally beneficial aspects of TCP might be more harmful than helpful.


UDP is also useful for applications that expect to only send a small amount of data (perhaps just a handful of bytes) overall. 

In such a case, not only would a retransmission be highly unlikely (due to the small size of the overall communication), but if an application did require to send a communication again, it can simply do so.


>[!example] Example: DNS
>
>One such application is DNS (Domain Name System). With DNS, queries (and the responses to queries) can usually fit inside single packets. 
>
>If a client sends a DNS request to a DNS server, and the server does not respond timely (perhaps due to a transmission error), the client can just quickly send the request again. 
>
>The time it takes to recover from the occasional dropped packet is more than made up for by the time saved by not checking for errors that rarely happen anyway. 


>[!info] Examples of UDP-based protocols
>
>- Network Time Protocol (NTP): Time synchronization
>- BOOTP/DHCP protocols: Auto configuration of network interfaces and the ability to automatically start an OS from the network during system startup.
>- Network File System (NFS): File sharing support for UNIX-based networks
>- Simple Network Management Protocol (SNMP): Monitoring and troubleshooting for server-based devices
>- Trivial File Transfer Protocol (TFTP): Inter-device file transfer without the requirement for authentication
>  
>  As computers and networks continue to evolve their performance capabilities, some applications have made the move from UDP to TCP, as the detriments of TCP overhead can be overcome by improved performance of computers and networks themselves.
>  
>  Some of the above UDP-based protocols and applications now support both TCP and UDP.

