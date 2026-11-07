A simple leaky bucket algorithm can be implemented using FIFO queue. A FIFO queue holds the packets. If the traffic consists of fixed-size packets (e.g., cells in ATM networks), the process removes a fixed number of packets from the queue at each tick of the clock. If the traffic consists of variable-length packets, the fixed output rate must be based on the number of bytes or bits. 

The following is an algorithm for variable-length packets: 
1. Initialize a counter to n at the tick of the clock. 
2. Repeat until n is smaller than the packet size of the packet at the head of the queue. 
	1. Pop a packet out of the head of the queue, say P. 
	2. Send the packet P, into the network 
	3. Decrement the counter by the size of packet P. 
3. Reset the counter and go to step 1. 

example:
let n = 1000
packet = {200,700, 500, 450, 400, 200}

since n > size of the packet at the head of the queue, i.e. n>200
therefore, n = 1000-200=800
packet size of 200 is sent into the network

{200, 700, 500, 450, 400}
now, again n > size of the packet at the head of the queue, i.e. n > 400
therefore, n = 800-400 = 400

{200, 700, 500, 450}
since, n < size of the packet at the head of the queue, i.e. n < 450
therefore, the procedure is stopped

initialize n = 1000 on another tick of the clock.
this procedure is repeated until all the packets are sent into the network.