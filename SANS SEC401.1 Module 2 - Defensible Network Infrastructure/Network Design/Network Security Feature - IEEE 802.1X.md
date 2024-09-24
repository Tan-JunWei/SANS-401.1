
>[!abstract] TLDR: 802.1 X:IEEE Standard for port-based network access control
>- Standard that provides for authentication (computer and/or user) prior to gaining network access
>- The X represents the eXtensible nature of the methods used for authentication (standard can be extended to support different types of authentication methods)
>- Can be used on wired and wireless networks

Upon the connection of a device to a network, a device is granted the least amount of access deemed necessary (perhaps no access at all). Authentication must occur before the device is granted additional access.
#### How is the authentication process like?
1. Software on the device, referred to as a supplicant, will make a request for authentication and subsequent access to the network. 

2. The request is passed through an authenticator (e.g. network switch), to a back-end authentication server. If the authentication is deemed legitimate, the authenticator notifies the device requesting access, and the switch port is opened to a level of access deemed appropriate (configured by the switch administrator). 

The passing of the authentication request and the subsequent response to the request is conducted between the supplicant software and the authenticator, via the use of [[IEEE 802.1X#EAPoL|EAPoL]] (Extensible Authentication Protocol over LAN) messages.

{_More information about [[IEEE 802.1X]]_ authentication process}

Due to 802.1X being extensible, support for various factors of authentication can be made possible. The authentication method could be as simple as a password or as cryptographically secure as authentication leveraging certificates. They can also be combined together (multi-factor access)

See also: [[Security controls framework - AAA]]

