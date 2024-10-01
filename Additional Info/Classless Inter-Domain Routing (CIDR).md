Classless Inter-Domain Routing (CIDR) is a collection of IP standards designed to optimize the process of allocating IP addresses by forming unique identifiers.

### Classful addresses

>[!abstract] Recall
>An IPv4 address consists of 32 bits (4 octets).

| Class A | A Class A IPv4 address has 8 network prefix bits. For example, consider 44.0.0.1, where 44 is the network address and 0.0.1 is the host address.<br><br>As a result, Class A supported 16,777,214 (1 x 2^8 x 2^8 x 2^8 -2) hosts (Only first octet is fixed).<br> |
| ------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Class B | A Class B IPv4 address has 16 network bits. Eg. 128.16.0.2, where 128.16 is the network address and 0.2 is the host address.<br><br>As a result, Class B supported 65,534 (1 x 1 x 2^8 x 2^8 -2) hosts (First 2 octets are fixed).<br>                            |
| Class C | A Class C IPv4 address has 24 network bits. Eg. 192.168.1.100, where 192.168.1 is the network address and 100 is the host address.<br><br>As a result, Class C supported 254 (1 x 1 x 1 x 2^8 -2) hosts (First 3 octets are fixed).                               |

>[!bug] The problem with classful IP addressing
>
>##### Inflexible IP addressing 1
>In a classful IP addressing system, each class only supported a **fixed** number of devices (since they support a fixed number of IP addresses).
>
>Class A: **16,777,214** hosts
>Class B: **65,534** hosts
>Class C: **254** hosts
>
>This approach is highly inefficient and resulted in a waste of IP address spaces. This is because if an organisation requires 300 IP addresses (300 devices), they could not use Class C IP addresses as it only permitted 254 hosts. 
>
>They would instead be forced to apply for Class B IP addresses which provided 65,534 host addresses. This would mean that 65,234 IP addresses would be left unused.
>
>##### Inflexible IP addressing 2
>E.g. Since the subnet mask of Class C was fixed as 255.255.255.0, network administrators were unable to combine 2 Class C networks together in the classful architecture. 
>192.168.1.0 and 192.168.0.0 would belong in 2 different networks.

### How does CIDR work?
Classless Inter-Domain Routing (CIDR) allows network routers to route data packets to the respective device based on the indicated subnet. Instead of classifying the IP address based on classes, routers retrieve the network and host address as specified by the CIDR suffix.

