We need to understand Conceptual Design, [[Logical Design]] and [[Physical Design]] to effectively understand network architecture. These 3 models are arranged in **decreasing levels of abstraction**, from left to right.

Conceptual design refers to the **high-level** network overview (abstraction).

>[!tip] Conceptual Design
>Conceptual design:
>- Includes core components of a network architecture
>	- internal and external systems, data flow, and overall system behavior
>
>- Will consider OS platforms, server services, critical core operational functions, etc.
>
>- Helps to understand the overall purpose of a network (**WHY** we have it and **WHAT** it helps us to achieve)
>	- Related: **_[[Know Thy Systems]] (Network)_**
>	- Not about how the systems are configured, but rather what systems we need to achieve our objectives (understanding the **interdependency** between those systems, and how end-users interact with those systems)
>	  
>	- Once we understand these purposes, we can begin to determine criticality (to understand what needs to be protected from a **security** perspective):
>		- criticality of **assets**
>		- criticality of **processes**
>		- criticality of **individuals**
>		  
>	- Some organizations take additional data into consideration for this design phase such as regulatory, legal, security, and safety concerns
>   - These additional considerations aren't necessary at this phase of understanding they are, however, mentioned for completeness
>      
>- is sometimes referred to as "closed-box" diagramming by industry publications
>	- Notion of describing a system by its functionality and use without requiring any knowledge of how the system achieves that functionality (the concept of **_abstraction_**)