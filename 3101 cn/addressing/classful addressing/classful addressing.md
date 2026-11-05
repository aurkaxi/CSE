the network address identifies a network on the internet. using this, we can find a range of addresses in the network and total possible number of hosts in the network.

mask is a 32-bit binary number that gives the network address in the address block when AND operation is bitwise applied on the mask and any IP address of the block.

the default masks in different classes are:
- class a - 255.0.0.0
- class b - 255.255.0.0
- class c - 255.255.255.0

>[!question] given ip address 132.6.17.85 and default class B mask, find the beginning address (network address).
>the default mask is 255.255.0.0 which means that only the first 2 bytes are preserved and the other 2 bytes are set to 0. therefore, the network address is 132.6.0.0
>
