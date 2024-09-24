#### Why IEEE 802.1X?

An 802.1X network is different from home networks in one major way; it has an authentication server called a RADIUS Server. It checks a user's credentials to see if they are an active member of the organization and, depending on the network policies, grants users varying levels of access to the network. 

This allows unique credentials or certificates to be used per user, eliminating the reliance on a single network password that can be easily stolen (SecureW2, 2024).

#### EAPoL
![[802.1X Diagram.png]]

EAP is an authentication framework with supports multiple authentication methods. EAP defines three terminologies:

1. **Supplicant:** A device that requests access to the LAN and switch services. The workstation running the IEEE802.1X-compliant client software is called the _Supplicant._

2. **Authenticator:** A device (a switch or a wireless access point) that controls the **physical access** to the network based on the authentication status of the Supplicant. The Authenticator requests the identity from the Supplicant, verifies that information with the Authentication Server and relays the response to the Supplicant. The Authenticator includes the RADIUS Client. The EAP messages are encapsulated and decapsulated by the Authenticator while interacting with the Authentication Server.

3. **Authentication Server:** A device that performs the actual authentication of the Supplicant. The Authentication Server validates the identity of the Supplicant and notifies the Authenticator whether the Supplicant is allowed to use the LAN and switch services.


#### References
- SecureW2. (2024, September 5). _What is 802.1X? How Does it Work?_ https://www.securew2.com/solutions/802-1x
- _Knowledge Base - Understanding 802.1X_. (n.d.). https://sites.google.com/site/amitsciscozone/switching/802-1x