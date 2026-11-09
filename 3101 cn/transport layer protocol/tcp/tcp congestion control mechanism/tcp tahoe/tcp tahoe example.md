suppose cwnd = 200 and packet loss occurs, then 
sshtresh = cwnd / 2 = 100; cwnd will be reset to initcwnd value that is 10
again slow start will begin.
now say cwnd increases to 20, 40, 80, 100 in 5th RTT
once cwnd reaches sshthresh, aimd starts
aimd increases cwnd by 1 per rtt, so if packet drop occurs at cwnd = 125
then cwnd = 10 and ssthresh=62 and slow start restarts
