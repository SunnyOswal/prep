+ Only decides which pod goes on which node but doesn't actually deploys it (kubelet soes that).
+ Makes sure nodes have sufficient capacity for requirements from pods.


Phase:
+ Filter Nodes (nodes which do not have enough capacity)
+ Rank Nodes by scoring 0-10 on priority like checking resources left after placing it)



