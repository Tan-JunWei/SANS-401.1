
>[!abstract] ICMP: An Overview
>
>The Internet Control Message Protocol is a protocol designed to report error conditions, assist with the performance of network troubleshooting, and to provide other network-related information, such as whether a host is available to receive a communication. 
>
>It is **not** meant to be used for the transmission of data per se.
>
>#### 2 purposes
>- Reports errors or troubleshooting
>	- Destination host unreachable
>	- TTL exceeded in transit (packets expire)
>
>#### 2 versions
>- ICMP for IPv4-based networks 
>- ICMP for IPv6-based networks (ICMPv6)



Since the objectives of ICMP are focused on assisting with network related concepts, it is discussed as operating at the Network Layer of the OSI model (same layer as IP). In fact, ICMP relies upon the IP protocol for transmission.


ICMP's placement as a Layer 3 protocol should not be confused with the idea of being limited to assisting only the IP protocol. Other upper layer protocols like UDP also rely on ICMP to provide information on network conditions and other related status and error messages that pertain to their specific transmission.


>[!todo] Helpful applications built with ICMP
>While ICMP was meant to act only in a supportive role and not be user-facing. there are applications designed specifically around parts of the ICMP capability. 2 such applications are **traceroute** and **ping**.
>- traceroute: determines the route a packet will take, from its source to its destination 
>	- ICMP packets are sent across the network, and every router involved in transferring the data receives these packets. 
>	- The ICMP packets provide information about whether the routers used in the transmission are able to effectively transfer the data (mapping out the network)
>
>	  For more information about traceroute: Visit [this](https://www.fortinet.com/resources/cyberglossary/traceroutes#:~:text=A%20traceroute%20provides%20a%20map,along%20the%20way%2C%20particularly%20routers.) site
>	  
>- ping: (command) determine if a host is present and available
>  
>  #### Important ICMP message types
>- Echo Request/Echo Reply (used in Ping to test connectivity)
>- Time Exceeded (used in Traceroute). This is generated when a packet's TTL expires in transit
>  
>  >[!tip] How ICMP leverages TTL
>  >
>  >"Time Exceeded" is useful in Traceroute because it helps identify the path packets take to a destination. 
>  >
>  >When Traceroute sends packets, it manipulates the TTL (Time to Live) value, starting at 1. Each router along the path decreases the TTL, and when it reaches 0, the router responds with a "Time Exceeded" message. By gradually increasing the TTL, Traceroute gets responses from each hop, revealing the sequence of routers leading to the destination.

#### References
- _What is Traceroute: What Does it Do & How Does It Work?_ (n.d.). Fortinet. https://www.fortinet.com/resources/cyberglossary/traceroutes#:~:text=A%20traceroute%20provides%20a%20map,along%20the%20way%2C%20particularly%20routers.