$$Dx(y) &= text(estimate of least cost from x to y)

c(x,v) &= text(node x knows cost to each neighbor v)

Dx &= [Dx(y): y in N] = text(node x maintains distance vector)$$
node x also maintains its neighbors' distance vectors

for each neighbor v, x maintains $Dv = [Dv(y): y in N]$

>[!note]
>1. from time to time, each node sends its own distance vector estimate to neighbors
>2. when a node x receives new DV estimate form any neighbor v, it saves v's distance vector and it updates its own DV using B-F equation:
>$Dx(y) = min{C(x,v) + Dv(y), Dx(y)}$ for each node $y in N$

