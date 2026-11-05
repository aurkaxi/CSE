1. number of subnets: $2^text(given bits for mask - no. of bits in default mask)$
2. subnet address: AND result of subnet mask and the given ip address
3. broadcast address: by putting the host bits as 1 and retaining the network bits as in the ip address
4. number of hosts per subnet: $2^(32 - text(given bits for mask)) - 2$
5. first host id: subnet address + 1 
6. last host id: subnet address + number of hosts