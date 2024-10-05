>[!abstract] What is a sniffer?
>
>A sniffer provides the capability to observe, record and analyze traffic as it transits a network. 
>
>Sniffers can observe network communication on wired and wireless networks alike.
>
>#### How can sniffing be used by different parties?
>
>Sniffing is used legitimately by administrators and security professionals for network troubleshooting, performance monitoring, and analysis, etc.
>
>Sniffing if used illegitimately (maliciously) by the adversary:
>
>- Much of our communication is unencrypted (particularly on internal networks)
>- Sniffing might yield credentials, sensitive data, and audio from VoIP calls, etc.

Normally, a host system's Network Interface Card (NIC) will only accept communication that is destined for its MAC address or communication that is broadcast for the entirety of a network segment.

If a NIC is placed into promiscuous mode, however, it will accept all traffic that it receives, regardless of whether the traffic is addressed to its MAC address or not. 

The use of a sniffer, in combination with a NIC in promiscuous mode, allows for network communication observed by a NIC to be analyzed and even recorded.

