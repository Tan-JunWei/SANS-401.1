
### IPv6 Features (Benefits and additional considerations)

- Extended address space
	- Permits for better route aggregation (such as based on geographic considerations)
	- Improved delegation/ management of addresses to organizations and ISPs
	- Provide hierarchical distribution of address space that makes troubleshooting and internet routing simpler
	
>[!abstract] Route aggregation
>
>Route aggregation in IPv6 combines multiple IP addresses into a single, summarized route. Instead of routing each address individually, several addresses are grouped under a broader prefix, reducing the number of routes that need to be handled. This improves efficiency and scalability in network routing.
	
- Auto configuration support
	- With 128 bits of address space available for an IPv6 address, it becomes possible to use the MAC address assigned to a network interface as part of the IPv6 address itself
	- In this way, administrators can simply introduce a new node to an IPv6 network without manually specifying an IP address (as the IP address is configured automatically based on the network interface MAC address and advertisement information received from the default gateway on the network)
	  
- Support for IPv6 over IPv4 (Tunneling)
	- Allows for IPv6 communication between 2 IPv6 endpoints without the routing systems in the middle requiring any knowledge of IPv6 (IPv6 packets to be encapsulated within IPv4 packets)
	- A virtual 'tunnel' allows for communication between the 2 IPv6 endpoints transiting through IPv4 systems along the path.
	  
- Support for IPv4 over IPv6 (Translation)
	- Allows for IPv4 addressed to be 'translated' from their current form into IPv6 compatible addresses
	- It ensures interoperability during the transition from IPv4 to IPv6 networks.
	  
- Authentication of endpoints and cryptographic protection of communication (utilizing concepts of [[IPSec]])
	  
- Flexible embedded protocol support
	- IPv6 header length is fixed at 40 bytes, as discussed in earlier sections.
	- The IPv4 header was able to expand to include additional 'options' in the Options field (which means the length can vary)
	- This is not to say IPv6 doesn't accommodate options, it accommodates the use options by utilizing Next Header field instead. This means that while this field works similarly to the Protocol field found in IPv4, it can further indicate that there are not one, but multiple protocol headers that follow, one after another.
	- These 'next headers' can be used to facilitate the instantiation of IP options.