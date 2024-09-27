
While the OSI protocol stack is the most commonly referenced, the most commonly used model is the TCP/IP model.

![[OSI vs TCP IP.png]]
#### Differences between OSI and TCP/IP
The first and most obvious difference between the stacks is the number of layers. The TCP/IP stack uses four layers as opposed to the seven layers used in OSI. Even though three of the four layers in the TCP/IP model **have names that match names in the OSI model**, no other similarity should be assumed. 

In fact, even though some of the names are the same, the functions being performed at those layers are **not identical** to that of the OSI model. 

>[!tip] Similarity and differences
>
>Regardless of the number of layers in a stack, the entire functionality leading to a properly formed communication must be met. Even though the TCP/IP stack has only four layers as compared to the seven-layer OSI model, the TCP/IP stack must still perform all the **same** functions. **Fewer layers just means each layer has to do a little more work**.

#### Pros and Cons
A benefit of the OSI model is the fact that it is more granular, as it splits apart some functionality that is combined in the TCP/IP model. For example, in the TCP/IP model, the Network layer comprises both the Physical and Data Link layers of the OSI model. 

The OSI model is more granular as it was designed with the mindset of supporting protocols other than just TCP/IP. By supporting more layers, the designers of OSI made it easier to break down specific network functionality and build more specific interfaces and linkages between the layers.

>[!abstract] Why were different protocol stacks created?
>
>Protocols stacks were created based on **different philosophies and motives**, although they all accomplish the same goal. 
>
>For example, the OSI model was developed by the International Organization for Standardization (ISO) to standardize how different systems communicate. 
>
>##### Different Design Philosophies
>**OSI Model**: This model takes a **top-down approach** and was designed with a clear separation of functions into seven layers, each responsible for a specific aspect of communication (e.g., physical transmission, routing, data presentation). The OSI model was built to be a **comprehensive, all-encompassing standard** that could handle various network types, not just the internet.
>
>**TCP/IP Model**: This model emerged from practical needs rather than theoretical design. The **bottom-up approach** of TCP/IP focused more on the functionality that worked well for real-world networking (like error correction, routing, and handling congestion) rather than adhering to strict separations of concerns like in OSI. It became the de facto model for internet communication due to its robustness and scalability.

To summarize, no matter which model is used, it must perform all the functions required to take a piece of application data, place it into a packet, put that packet through the network connection, and deliver it to its destination.


