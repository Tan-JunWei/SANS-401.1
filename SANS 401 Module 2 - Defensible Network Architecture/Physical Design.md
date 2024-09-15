- Builds upon the logical design by providing detailed aspects of the network components
	- Note that "physical design" can have multiple meanings
		- Initial purpose: physical design involves a continuation of our evolving understanding of network architecture, building upon [[Conceptual Design]] and [[Logical Design]], while still being on paper
		- [[Logical Design]] does not cover the finely detailed aspects of network components. In physical design, those details are broken out
		  
- Details might include OS versions, patch levels, hardening configurations, risk categorization, etc.
	- Patch level: denotes either a patch level or a patch set. More specifically, when patches must be applied in order, the patch level is the identifier of the most recently applied patch.
	- [[Systems Hardening]]
	- Categorization of risk related to the criticality of the components ([[Conceptual Design]])
	  
- Physical design also considers physical risks such as network cable location, risk of communication interception, etc.
	- Actual "physical" design of the network and any potential physical weaknesses that are present or may manifest physically at some point
  
- Physical security can betray logical security controls
	- "Our logical security can be bypassed by physical weakness"
	- Much of the controls we focus on in cybersecurity are logically based. Examples include authentication via passwords or smart cards, biometrics, file systems permissions, etc.
	  
	  See also:
	  [[Security controls framework - AAA]] 
	  [[Biometric security]]
	- While logical controls are important, they might be made mute by a physical security compromise
		- If someone can walk up to the server and steal it physically, it does not matter that a server is secured by strong logical controls