- A sampling of possible switch attacks
	- CDP Information Disclosure
		- Cisco Delivery Protocol (CDP) is an example of a discovery protocol
		- Discovery protocols are used by many different types of devices on networks, they are not exclusive to switches
		- Discovery protocols are used to aid devices in discovering other devices that also exists on a network 
		- Switches need to understand which other switches exist
		- A method of sharing some information of a switch's setup and configuration is via the use of a discovery protocol such as CDP
		- Information provided by a network discovery protocol might be crucial to switch operation and perhaps equally crucial to the success of an attacker
		- Discovery protocols provide a tremendous amount of information, thus sniffing of such protocols can yield a substantial amount of valuable information, such as:
			- name of switch vendor
			- version of OS software installed
			- usernames of administrative accounts used to login to the switch
		- Something as simple as current version of installed OS software can allow an attacker to know exactly which attack will be successful against a specific switch from a specific vendor
		- We need the information conveyed by a discovery protocol, but we don't want an attacker to have easy access to the same information
			- One way is to try and restrict an attacker's access to limit the dissemination of the discovery information (limit where on the network the communication is broadcast)
			- This discovery information is important to a switch but isn't important to a desktop
			- By default in most organizations, discovery protocol traffic is more than likely being broadcast across the entirety of the network although it shouldn't be
			- By restricting the broadcast to management interfaces of the switches we can limit the disclosure of this vital Information in a way that makes an attackers job more difficult
			  
	- MAC Flooding
		- In a MAC flooding attack the attacker floods the MAC address table of a switch with fake non-existent MAC addresses
		- After a computer is connected to a switch (via a network cable), the switch records the MAC address of the computer's interface that is being connected. MAC addresses therefore indicate the source and/or destination of local network communication
		- Switches uses MAC addresses to determine which connected computer the traffic is destined for. A switch will only send and receive information to and from the physical switch ports where the source and destination devices are connected
		- This means that an attacker, post compromise of a computing device, will only see network traffic to and from the compromised device itself. An attacker would desire to see more, if not all, of a networks communication
		- One way for an attacker to potentially gain access to more communication traffic even in the presence of a switch might be by the use of a downgrade attack against the switch
		- A downgrade attack in general results in convincing a victim device to use a lower level or security capability that it might be configured to use
		- In a MAC flooding attack, an attacker convinces a switch that new devices continue to connect in an almost non-stop continual fashion(via the use of fake non-existent MAC addresses)
		- The switch will reach a point where it no longer has enough memory to record each new MAC address that connects. The switch will start to enter a error condition, and as part of said error conditioning, the switch (in order to continue operating as opposed to shutting down) might downgrade itself to the concept of a network hub
		- Hubs, the precursor devices to switches, have a fundamental security issue - a lack of awareness of which MAC addresses is connected to which physical port of the hub itself, leading to a broadcasting of all traffic to each and every connected computer (each computer discards traffic not actually meant for it)
		- This allows for the sniffing of ALL network communication to be performed in an almost trivial fashion
		  
	- DHCP Manipulation
		- [[DHCP]] is commonly used by computing devices to obtain their network configuration, which will include items such as their IP address, the subnet mask for the network segment, the IP address of the default gateway (default router), and maybe even the IP address of a server that will provide the OS for the computing device.
		- So, the manipulation of this valuable configuration information could be of high value to an attacker. 
		- When the attacker is in a sufficient position on a victim network, they can monitor for DHCP requests that are being sent from a computing device. If the attacker operates fast enough, he can supply an answer of the DHCP request to the device **before the legitimate DHCP server does**.
		- In doing so, the attacker has gained control of the network configuration information that will be used by the computing device. 
		- The attacker provides network configuration information to deceive the victim computer, perhaps indicating that the attacker's IP address is the IP address of the default router of the network. In doing so, the victim now sends all non-local network traffic to the IP address of the 'default router', which happens to be the IP address of the attacker's machine on the network (the machine that the attacker has compromised). 
		- The attacker, on behalf of the victim, will forward the traffic to the actual default router, resulting in a completed communication (and a successful MiTM position). There are better ways for an attacker to achieve a MiTM, but this attack demonstrates the risk of DHCP manipulation.
		  
	- STP Manipulation
	- VLAN Hopping

See also:
[[Switch vs Router]]
[[Attacks against Routers]]