It is a control algorithm that dictates when traffic can be transmitted based on the presence of tokens in the bucket.

1. **Bucket Creation and Initialization**
    1. A logical container (the bucket) is set up with a maximum capacity \(B\).
    2. The bucket starts completely full (containing \(B\) tokens) or empty, depending on the system design. 
2. **Continuous Token Refill**
    1. Tokens are added to the bucket at a steady, fixed rate (\(r\)).
    2. If the bucket reaches its maximum capacity \(B\), any newly generated tokens overflow and are discarded (the bucket never holds more than \(B\) tokens).
    3. _Idle Benefit:_ If the system or user sends no data for a period, unused tokens accumulate in the bucket up to the limit \(B\).
3. **Request or Packet Arrival**
    1. When a request or network packet arrives, the system intercepts it before transmission.
    2. The system checks the current number of available tokens in the bucket.
4. **Token Consumption & Decision**
    1. **If enough tokens are available** (tokens \(\ge \) required token cost):
        1. The required number of tokens is deducted from the bucket.
        2. The request or packet is **allowed to proceed/transmit immediately**.
    2. **If insufficient tokens are available** (tokens < required token cost):
        1. The request cannot be sent right away.
        2. Depending on the system policy, the packet is either **delayed (queued)** until more tokens refill, or **dropped/rejected** (common in API rate limiting or network policing). 