Physical design builds upon the logical design by providing detailed aspects of the network components.

>[!abstract] 
>Note that "physical design" can have multiple meanings.
>
>>[!faq] 1st definition
>>Physical design involves a continuation of our evolving understanding of network architecture, building upon [[Conceptual Design]] and [[Logical Design]], while still being on paper.
>
>**What does physical design include?**
>- [[Logical Design]] does not cover the finely detailed aspects of network components. In physical design, those details are broken out.
>- Details might include OS versions, installed patches, applied hardening configurations, **risk categorization**, etc.
>	- Related: [[Systems Hardening]]
>	- Categorization of risk related to the criticality of the components ([[Conceptual Design]])
>
>>[!faq] 2nd definition
>>Physical design also considers physical risks such as network cable location, risk of communication interception, etc (**actual "physical" design of the network** and any potential physical weaknesses that are present or may manifest physically at some point).
>
>**Why is the actual physical design of the network important?**
>
>Logical security can be bypassed by physical weakness, as much of the controls we focus on in cybersecurity are **logically based**. 
>Examples include authentication ([[Security controls framework - AAA|AAA]]) via passwords or smart cards, [[Biometric security|biometrics]], file systems permissions, etc.
>
>>[!fail] Understanding "physical" security
>>While logical controls are important, they might be made mute by a physical security compromise
>>If someone can walk up to the server and steal it physically, it **does not matter** that a server is secured by strong logical controls.