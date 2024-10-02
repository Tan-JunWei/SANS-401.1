>[!abstract] TLDR: Why NAT?
>
>The idea of NAT is to allow multiple devices to access the Internet through a single public address. To achieve this, a private IP address must be translated into a public IP address.
>
>One public IP address is needed to access the Internet, but we can use a private IP address in our private network. 
>
>![[NAT DIagram.png]]

##### How does NAT work?
Generally, the border router is configured for NAT i.e. the router which has one interface in the local (inside) network and one interface in the global (outside) network. When a packet traverse outside the local (inside) network, then NAT converts that local (private) IP address to a global (public) IP address. When a packet enters the local network, the global (public) IP address is converted to a local (private) IP address. 

>[!todo] Why was NAT developed?
>
>Due to the exponential growth of the Internet and the increased demand for IP addresses, the number of available IP addresses were insufficient.
>
>So, instead of every computing having a public IP address to communicate with other computers on the internet, NAT allows a single device (like a router) to act as an agent between the Internet and the local network.
>
>Thus, all computers in a private network are allowed to share a **common, unique IP address** which can be used to represent the entire group of computers effectively. 
>
>This way, 100 hosts will not require 100 unique public IP addresses. Instead, a single public IP address could be shared by all 100 hosts, conserving 99 public IP addresses.
#### References
- GeeksforGeeks. (2024f, August 26). _Network Address Translation (NAT)_. GeeksforGeeks. https://www.geeksforgeeks.org/network-address-translation-nat/