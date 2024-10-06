Sniffers come in different forms based on required functionality, work-flow ability, or application best-practice. The list below is not an exhaustive list of all sniffers. The list does, however, include some of the more well-known ones.

>[!example]+ Example of sniffers
>
>### `tcpdump`: Initial triage
>
>tcpdump runs primarily on Unix/Linux style operating systems and even ships with a few Linux distributions. For Microsoft Windows, a Windows port was made available, but it hasn't seen any extensive updating in recent years.
>
>tcpdump isn't as fully featured as other, more capable sniffers, but that can a benefit. The more functionality offered by a sniffer, the more the strain there is on computing resources, taking away from the resources needed just to sniff all the network traffic as it passes by. 
>
>The more traffic we expect to record, the more computing resources must be made available to the system running the sniffer. If the sniffer does more than recording the packets of communication (ie. it performs analysis at the same time) it will only put further strain on the computing resources, leading to traffic possibly being 'dropped' (not recorded).
>
>In some situations, it might be preferred to have a full record of communication and later analyze it, as opposed to having the sniffer perform analysis while capturing packets (leading to the absence of a full record of packets). As such, we may not be overly concerned that tcpdump isn't as capable from an analysis perspective as other sniffers.
>
>tcpdump can be used to capture as much traffic as possible, and provide that traffic for analysis by a more capable sniffer at a later point in time. 
>
>### `Wireshark`: Detailed packet and protocol analysis
>
>Wireshark is best described as not as a sniffer but as a network protocol analyzer. It can understand a variety of different protocols and media types. 
>
>While Wireshark can sniff network communication, that is not its primary purpose. Its primary purpose is to better assist an analyst by providing more effective analysis of what is being communicated.
>
>### `Snort`: Intrusion Detection System
>
>Snort is an instantiation of an IDS; It performs detailed inspection of network traffic to assist in the earlier detection of malicious activity.
>
>### `Kismet`: Wireless network sniffer
>
>Kismet is a sniffer designed for traditional wireless (WLAN) networks. It processes the radio signals produced by WLANs to provide information on what security controls are in place on the WLAN (such as WPA2/WPA3). 
>
>The data gathered by Kismet can also be combined with geographic mapping tools in order to map the location of a WLAN (including how far the signal transmits from that location)
>
>>[!tip] Wardriving
>>
>>Kismet can be used for wardriving.
>>
>>In the realm of Wi-Fi penetration testing, war-driving remains a pivotal technique. It involves traversing areas to detect and evaluate wireless networks. This approach is vital for pinpointing vulnerabilities, understanding network security configurations, and assessing potential exposure to cyber threats.
>
>### `BetterCAP`: Sniffing on switches, via the use of MiTM attacks
>
>BetterCAP is not really considered a sniffer per se; It is a tool that combines sniffing with the ability of being able to sniff traffic - even in the presence of a network switch. 
>
>This tool obtains its sniffing capabilities by utilizing attacks, including MiTM. Once a MiTM is in place, BetterCAP will sniff the traffic is can observe.
>
>>[!tip] Not just a sniffer
>>
>>While BetterCAP can capture and analyze network traffic like traditional sniffers (e.g., Wireshark), it goes further by allowing active network attacks. It's primarily focused on active interception rather than passive listening.


