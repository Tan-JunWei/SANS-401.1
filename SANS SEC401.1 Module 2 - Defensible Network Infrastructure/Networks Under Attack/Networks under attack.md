Security tends to focus on traditional IT assets: servers, desktops, and applications
  
Other areas are sometimes completely ignored (neglected), including key network devices such as routers and switches.

Compromise of routers and switches can facilitate communication interception and manipulation, allowing adversary to sniff network communication and subsequently:

- inspect the communication in search for sensitive data like authentication credentials
	See also: [[Security controls framework - AAA]]

- modify network communication (integrity violation)

- perhaps even bypass security controls in general
	- Network devices, such as switches, don't have to allow all communication; switches can be used to limit communication (e.g. [[Virtual Local Area Network (VLAN)]])
	- A compromise of the switch may allow the adversary to modify the configuration, resulting in granting themselves to additional parts of the network

>[!tip] Considerations
>It is not uncommon for such devices to be unpatched and without hardening for long periods of time.
>
>The more critical an asset is, the more difficult it becomes to secure. Critical assets simply cannot be unavailable (even though a lack of security, ironically, can also lead to an impact on availability)