1. all ip addresses must be contiguous.
2. block size must be the power of 2. 
3. first ip address of the block must be evenly divisible by the size of the block. in simple words, the least significant part should always start with zeros in the host id. since all the least significant bits of host id is zero, then we can use it as block id part

>[!example] check whether 100.1.2.32 to 100.1.2.47 is a valid IP address block or not? 
>1. All the IP addresses are contiguous. 
>2. Total number of IP addresses in the Block = 16 = $2^4$. 
>3. 1st IP address: 100.1.2.0010**0000** Since, Host Id will contains last 4 bits and all the least significant 4 bits are zero. Hence, first IP address is evenly divisible by the size of the block. 
>All three rules are followed by this Block. Hence, it is a valid IP address block.

