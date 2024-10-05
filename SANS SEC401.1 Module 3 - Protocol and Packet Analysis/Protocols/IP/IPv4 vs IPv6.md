
IPv4 has some limitations, specifically in the number of unique addresses supported. While IPv4 accommodates **4.2 billion (2^32) unique 32-bit addresses**, the allocation of IP addresses on the internet was completed in the most efficient manner, leading to a **shortage of available IP addresses**.

There have been methods used to mitigate this shortage ([[Network Address Translation (NAT)]] and [[Classless Inter-Domain Routing (CIDR)]]. However, 4.2 billion addresses would still not be enough even with the most considerate use of available space. 

##### IPv4 vs IPv6 - What's the difference?

IPv6 has 128 bits of address space, which means it can accommodate 340 undecillion (2^128) addresses. This larger address also allows for greater flexibility in allocating addresses. Utilizing IPv6, Internet Service Providers (ISPs) will be able to geographically assign IPv6 prefixes to different parts of the world, facilitating a simplification of routing traffic over the Internet. 

IPv6 allows for organizations, large and small, to obtain a IPv6 prefix with sufficient available addresses to accommodate all present and future addressing needs.

| IPv4                                | IPv6                                                       |
| ----------------------------------- | ---------------------------------------------------------- |
| 32-bit address                      | 128-bit address                                            |
| No authentication                   | Provides authentication of endpoints                       |
| Encryption provided by applications | Support for encryption in protocol                         |
| Best effort transport               | Quality of Service (QoS) features provided in the protocol |

To assist with the security shortcomings of IPv4, a set of security protocols ([[IPSec]]) was created. The core design of IPv6 focuses on leveraging aspects of IPSec to provide some of the security required in a more modern and ever-connected world.

Authentication of endpoints and encryption of data **in transit** are 2 examples of improved security features. 

IPv6 also gives us QoS features that permit real-time sensitive applications, such as Voice over IP (VoIP) and interactive media, to take priority over less critical packet streams. 

[[More information about QoS in IPv6]]