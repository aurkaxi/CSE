1. Bucket Size (Capacity)
	- **What it is:** The maximum number of requests, data packets, or units of "water" the bucket (buffer or queue) can hold at any given time.
	- **Role:**
	    - Acts as a temporary holding area for incoming spikes or bursts of traffic.
	    - If incoming requests arrive faster than they can be processed, they accumulate in the bucket up to this limit.
    - If the number of requests exceeds the bucket size, the bucket overflows, and any extra incoming requests are immediately rejected or dropped.
2. Leak Rate
	- **What it is:** The constant, fixed rate at which requests or data packets leave the bucket and get processed per unit of time (e.g., 5 requests per second).
	- **Role:**
	    - Enforces a steady, predictable output speed regardless of how chaotic or erratic the input traffic is.
	    - Acts as a reflection of the system's actual processing capacity.
	    - Converts irregular, bursty traffic into a smooth, uniform stream.