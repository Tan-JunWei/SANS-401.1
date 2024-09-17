>[!abstract]- CDP Information Disclosure
>**What are Discovery Protocols?**
>Cisco Delivery Protocol (CDP) is an example of a discovery protocol. Discovery protocols are used by many different types of devices on networks, they are **not exclusive to switches**. Discovery protocols are used to aid devices in **discovering other devices** that also exists on a network 
>
>Switches need to **understand which other switches exist**. A method of sharing some information of a switch's setup and configuration is via the use of a discovery protocol such as CDP. Information provided by a network discovery protocol might be crucial to switch operation and perhaps equally crucial to the success of an attacker. 
>
>Discovery protocols provide a tremendous amount of information, thus sniffing of such protocols can yield a substantial amount of valuable information, such as:
>	- name of switch vendor
>	- version of OS software installed
>	- usernames of administrative accounts used to login to the switch
>
>Something as simple as current version of installed OS software can allow an attacker to know exactly which attack will be successful against a specific switch from a specific vendor. We need the information conveyed by a discovery protocol, but we don't want an attacker to have easy access to the same information.
>
>One way is to try and restrict an attacker's access to limit the dissemination of the discovery information (limit where on the network the communication is broadcast), especially because his discovery information is important to a switch but isn't important to a desktop.
>
>>[!failure] Disclosure of discovery information
>>By default in most organizations, discovery protocol traffic is more than likely being broadcast across the entirety of the network although it shouldn't be. By restricting the broadcast to management interfaces of the switches we can limit the disclosure of this vital Information in a way that makes an attackers job more difficult.

>[!abstract]- MAC Flooding
>In a MAC flooding attack the attacker floods the MAC address table of a switch with fake non-existent MAC addresses. After a computer is connected to a switch (via a network cable), the switch records the MAC address of the computer's interface that is being connected. MAC addresses therefore indicate the source and/or destination of local network communication
>
>>[!question] How are MAC addresses important?
>>Switches uses MAC addresses to determine which connected computer the traffic is destined for. A switch will only send and receive information to and from the physical switch ports where the source and destination devices are connected
>
>This means that an attacker, post compromise of a computing device, will only see network traffic to and from the compromised device itself. An attacker would desire to see more, if not all, of a networks communication.
>
>>[!bug] How does MAC flooding attack work?
>>One way for an attacker to potentially gain access to more communication traffic even in the presence of a switch might be by the use of a **downgrade attack** against the switch.
>>A downgrade attack in general results in convincing a victim device to use a lower level or security capability that it might be configured to use.
>> - In a MAC flooding attack, an attacker convinces a switch that new devices continue to connect in an almost non-stop continual fashion (via the use of fake non-existent MAC addresses)
>> - The switch will reach a point where it no longer has enough memory to record each new MAC address that connects. The switch will start to enter a error condition, and as part of said error conditioning, the switch (in order to continue operating as opposed to shutting down) might downgrade itself to the concept of a network hub
>> - Hubs, the precursor devices to switches, have a fundamental security issue - a lack of awareness of which MAC addresses is connected to which physical port of the hub itself, leading to a broadcasting of all traffic to each and every connected computer (each computer discards traffic not actually meant for it).
>> - This allows for the sniffing of ALL network communication to be performed in an almost trivial fashion.

>[!abstract]- DHCP Manipulation
>[[DHCP|DHCP (Dynamic Host Configuration protocol)]] is commonly used by computing devices to obtain their network configuration, which will include items such as their IP address, the subnet mask for the network segment, the IP address of the default gateway (default router), and maybe even the IP address of a server that will provide the OS for the computing device.
>
>So, the manipulation of this valuable configuration information could be of high value to an attacker. 
>
>>[!bug] How does a DHCP manipulation attack work?
>>- When the attacker is in a sufficient position on a victim network, they can monitor for DHCP requests that are being sent from a computing device. If >the attacker operates fast enough, he can supply an answer of the DHCP request to the device **before the legitimate DHCP server does**.
>>- In doing so, the attacker has gained control of the network configuration information that will be used by the computing device. 
>>- The attacker provides network configuration information to deceive the victim computer, perhaps indicating that the attacker's IP address is the IP address of the default router of the network. In doing so, the victim now sends all non-local network traffic to the IP address of the 'default router', which happens to be the IP address of the attacker's machine on the network (the machine that the attacker has compromised). 
>>- The attacker, on behalf of the victim, will forward the traffic to the actual default router, resulting in a completed communication (and a successful >MiTM position). There are better ways for an attacker to achieve a MiTM, but this attack demonstrates the risk of DHCP manipulation.

>[!abstract]- STP Manipulation
>STP (Spanning Tree Protocol) manipulation attacks are related, in part, to the CDP attack described above.
>As part of the CDP conversation, it was highlighted that switches need to understand how they are connected to one another themselves. This is important because switch loops may occur if the switches are not connected properly, causing **traffic to loop in a circle**.
>
>One of the responsibilities of STP is to ensure that switch loops do not occur (prevention of switch loops).
>
>STP, like CDP, is plaintext (readable and observable). An attacker, with sufficient access to the network, might be able to impersonate STP communication and manipulate it to their advantage. If successful, the result will be switch reconfiguration.
>- Such manipulation could be performed in an effort to cause a switch loop, resulting in a DoS, or to intentionally reconfigure switches to facilitate a MiTM capability.
>- STP can be configured to help prevent unintentional manipulation, and just like CDP, STP should be available only to management interfaces (not the network overall).

>[!abstract]- VLAN Hopping
>[[Virtual Local Area Network (VLAN)|VLAN]] (Virtual Local Area Network) is a concept of network segmentation.
>
>>[!danger] Danger
>>Switches connect devices together, to form a network, in the spirit of all devices being equally accessible for device-to-device communication. This, however, assumes that our devices are of all of the same trust level, which they are not.
>>A model of intrinsic trust will allow an adversary to more easily pivot across the devices of a network.
>
>Network segmentation is a method of enforcing the concept that devices should not be allowed to communicate with one another simply by the nature of being connected. Network segmentation, such as in the form of a VLAN, makes the life of an adversary initially more difficult and is why an adversary may attempt a VLAN hopping attack.
>
>>[!success] Normal circumstances
>>In a properly segmented network, devices within one VLAN should not be able to communicate with devices in another VLAN unless explicitly allowed by network policy, typically through a router or firewall.
>
>In the formation of a VLAN hopping attack, an attacker will manipulate the characteristics of network packets in a such a way that a switch will allow an attacker to 'hop' from one VLAN to another in a way that would otherwise be prohibited.


See also:
[[Switch vs Router]]
[[Attacks against Routers]]