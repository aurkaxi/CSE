traditional ip addressing used classes with fixed address ranges (e.g. class a: 1.0.0.0 to 126.0.0.0). cidr uses a format that combines an ip address and a prefix length to denote the network and subnet portion (e.g. 192.168.1.0/24).

>[!example] check whether 100.1.2.32 to 100.1.2.47 is a valid ip address block or not?
>1. all the ip addresses are contiguous.
>2. total number of idd addresses in the block = 16= $2^4$
>3. 1st ip address: 100.1.2.00100000 since, host id will contains last 4 bits and all the least significant 4 bits are zero. hence, first ip address is evenly divisible by the size of the block
>all three rules are followed by this block. hence, it is a valid ip address block