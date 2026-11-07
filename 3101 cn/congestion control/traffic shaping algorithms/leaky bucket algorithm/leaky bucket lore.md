imagine a bucket with a small hole in the bottom. no matter what rate water enters the bucket, the outflow is at constant rate. when the bucket is full with water additional water entering spills over the side and is lost.
![[leaky bucket lore.png]]
similarly, each network interface contains a leaky bucket and the following steps are involved in leaky bucket algorithm
1. **The Inflow (Water poured in):** Data packets or network requests arrive at irregular, bursty speeds. This is like pouring water into the bucket in erratic splashes.
2. **The Bucket (The Buffer):** The bucket acts as a queue that holds the excess requests temporarily. 
3. **The Leak (Constant Outflow):** No matter how fast or how much water is poured in, the water drains out through the bottom hole at a **fixed, steady rate**. In computer networks or API rate limiting, the system processes and transmits requests at this same uniform speed.
4. **Overflow (Spilling Over):** If water is poured in faster than it can leak out and the bucket reaches its maximum capacity, the extra water spills over the sides and is lost. Similarly, if too many requests arrive and fill the buffer, the excess packets are dropped or rejected. 
5. in practice the bucket is a finite queue that outputs at a finite rate

By smoothing out erratic traffic spikes into a predictable, constant stream, the algorithm protects servers and networks from getting overloaded—just like a leaking bucket controls the flow of water.