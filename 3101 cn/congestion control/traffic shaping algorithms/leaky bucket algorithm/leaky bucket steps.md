1. **Data Arrival (Inflow):** Data packets or API requests arrive at the network interface or application server at an irregular, variable (bursty) rate.
2. **Buffer Check (Capacity Test):** The algorithm checks whether there is enough free space in the bucket queue to accommodate the incoming packet.
3. **Enqueuing or Discarding:**
    1. **If space is available:** The packet is added to the queue (the bucket).
    2. **If the bucket is full:** The packet exceeds capacity and is dropped or rejected immediately.
4. **Constant Leak (Outflow):** Regardless of how fast or slow data enters, the system drains and transmits data out of the bucket at a strict, pre-defined constant rate (R).
5. **Steady Stream:** The downstream network or server receives a smooth, evenly paced flow of data, preventing system overload and congestion.