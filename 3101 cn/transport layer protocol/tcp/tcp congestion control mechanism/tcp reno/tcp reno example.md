cwnd=120, ssthresh=∞ 

1. packet loss detected using 3-duplicate ACK (aka Fast Retransmit). 
   cwnd will be reduced to 50%, cwnd=60 
   ssthresh will be new cwnd, ssthresh=60 
   Now Reno has entered Fast Recovery Phase, it skips the slow start and AIMD takes over. Whereas in Tahoe Slow Start restarts when packet loss is detected. This is the difference between these two. 
2) Now say cwnd is reached to 70 in 10 more RTT from cwnd=60, after AIMD started. 
   packet drop occurs at cwnd=70, cwnd becomes 35 and ssthresh=35. 
3) now cwnd increases to 50, and packet loss detected using RTO. 
   then cwnd=initial cwnd= 10, ssthresh=cwnd/2=25 
   Whenever packet loss detected, Reno never uses Slow Start again, it skip it. 
