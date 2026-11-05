problem 1
given the cidr representation `20.10.30.35/27`. find the range of ip addresses in the cidr blocks
solution

27 bits are used for the identification of network
remaining 5 bits are used for the identification of hosts in the network
in binary= `00010100.00001010.00011110.00100011/27`
so 
first ip address =00010100.00001010.00011110.001**00000**/27 = 20.10.30.32
last ip address = 00010100.00001010.00011110.001**11111**/27 = 20.10.30.63
thus, range of ip addresss = [20.10.30.32, 20.10.30.63]

problem 2
given the cidr representation `100.1.2.35/20`. find the range of ip addresses in the cidr block.
solution

in binary
01100100.00000001.0000**0010.00100011**/20
so first ip = 01100100.00000001.0000**0000.00000000**/20 = 100.1.0.0
last ip = 01100100.00000001.0000**1111.11111111**/20 = 100.1.15.255

problem 3
consider a block of ip addresses ranging from 100.1.2.32 to 100.1.2.47
1. is it a cidr block
2. if yes, give the cid representation
solution

rule 1: ip addresses must be contiguous, which they are
rule 2: size of the block must be presentable as $2^n$. size of the block 16 = $2^4$ 
rule 3: first ip address must be divisible by size of the block.
100.1.2.32 = 100.1.2.0010**0000** is divisible by $2^4$ since the least significant 4 bits are zero

since all the rules are satisfied, therefore given block is a cidr block
size of block is $2^4$, host bit is 4, network id part = 32-4 = 28 
cidr: 100.1.2.32/28

we can choose any ip of the block, first ip is just a convention

problem 4
Consider a block of IP Addresses ranging from 150.10.20.64 to 150.10.20.127. 
1. Is it a CIDR block? 
2. If yes, give the CIDR representation. 
Solution
Rule-01: all the given IP Addresses are contiguous.
Rule-02: number of IP Addresses in given block = 127 – 64 + 1 = 64 = $2^6$
Rule-03: 150.10.20.64 = 150.10.20.01**000000** is divisible by $2^6$ since its 6 least significant bits are zero.
Since all the rules are satisfied, therefore given block is a CIDR block. 
Size of the block = $2^6$
Number of bits in the Network ID part = 32 – 6 = 26. Thus, CIDR Representation = 150.10.20.64 / 26 

problem-05: 
Perform CIDR aggregation on the following IP Addresses- 
128.56.24.0/24 
128.56.25.0/24 
128.56.26.0/24 
128.56.27.0/24 
Solution

All the 4 given entities represent CIDR block in itself. We have to now perform the aggregation of these 4 blocks. 

Rule-01: all the IP Addresses are contiguous.
Rule-02: Total number of IP Addresses = $2^8 + 2^8 + 2^8 + 2^8 = 2^2 x 2^8 = 2^10$.
Rule-03: 128.56.24.0 = 128.56.000110**00.00000000** is divisible by $2^10$ since its 10 least significant bits are zero. 
Since all the 3 rules are satisfied, so they can be aggregated

32 - 10 = 22
/22
