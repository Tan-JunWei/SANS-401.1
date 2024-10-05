![[IPv6 Header diagram.png]]

The IPv6 header indeed looks different from the corresponding IPv4 header, but it only takes a slight amount of work to translate the names and fields from IPv4 into IPv6 if we keep in mind the purpose of IP.

>[!todo] Length of IPv6 header
>
>The length of the IPv6 header is fixed at 40 bytes, as opposed to the variable length of an IPv4 header.
>
>The calculation is as follows:
>
>The first 2 'rows' of the IPv6 header are 32 bits each, and the source and destination address fields are 128 bits each.
>
>Adding them up together gives us 32 + 32 + 128 + 128 = 320 bits, which is equivalent to 40 bytes.
>

### Version, 4 bits
Just as with IPv4, this field indicates the version of IP that is in use. For IPv6, the value present in this field would be 6 (decimal).

### Traffic Class (8 bits) and Flow Label (20 bits)
Traffic Class and Flow Label are 2 fields whose use cases can be related, and are hence discussed together.

#### Traffic Class
The Traffic Class field is used to help provide QoS (Quality of Service) for network communication As covered previously, IP is a best effort protocol that does its best to deliver a communication leveraging the best route available at the time of transmission and in transit. IP (as a concept) does not guarantee any delivery will be successful nor does it consider that a given packet may not be 'equal' to any of the other packets also being sent and received.

>[!abstract] Example: Why QoS?
>
>Packets related to an ongoing voice communication, such as VoIP (Voice over IP) might be of a more time-sensitive nature for delivery than packets of an email communication that happen to be transiting the same routers. 
>
>If a router could give a time-sensitivity preference to one communication over the other (delay in voice communication can break down the entire communication), then perhaps it should. 

Hence, the Traffic Class is designed with this concept of importance, and can also consider aspects of ECN (Explicit Congestion Notification), a concept that works with TCP, to help provide overall quality of service to network-base communication.

For more information about QoS: [[More information about QoS in IPv6]]

#### Flow Label
One use case of Flow Label is the furtherance of QoS aspects by classifying packets together, as a 'flow' of communication. There is also the potential for a future use of labelling a communication flow in approach to assist with the detection of spoofed packets.

### Payload Length, 16 bits
Similar to the Total Length field of an IPv4 header, the Payload Length field specifies the length of the packet (in bytes).

### Next Header, 8 bits
The Next Header field contains an integer value, denoting the exact type of IP message encapsulated in the packet (similar to the Protocol field of the IPv4 header). The values that are assigned to IPv4 embedded protocols (such as TCP, UDP, and ICMP) are forward-compatible with the IPv6 Next Header field.

### Hop Limit. 8 bits
This Hop Limit field shares the same concept of the Time to Live (TTL) field found in the IPv4 header and works in the same manner.

### Source Address and Destination Address, 128 bits (each)
These fields represent the source and destination addresses respectively of the computers involved in a communication.

Since IPv6 has 128 bits of address space, the source and destination addresses are 128 bits each (in comparison to 32 bits each for IPv4 addresses).

>[!info] Observation
>
>As seen in the IPv4 header and the newer IPv6 header, both headers do contain similar (or exactly the same) fields in terms of functionality and purpose, but some fields have been renamed in the IPv6 header (TTL -> Hop Limit). 
>
>There are also fields that were previously included in the IPv4 header, but are not kept in that of IPv6, such as the Options and Fragmentation (Flags + Fragment Offset) fields.
>
>In fact, there were also rearrangement of fields in the IPv6 header as compared to the IPv4 header.
>
>>[!tip] Why were the adjustments made?
>>
>>The IPv6 header has fewer fields which makes it more efficient and faster to process. Another big advantage is that the header length is fixed size 40 bytes, comparing to the variable length size of the IPv4 header.