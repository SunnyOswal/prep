# Network Model
![Network Model](https://github.com/SunnyOswal/prep/blob/master/images/k8s-network-model.PNG)

+ an IP address is automatically assigned to **each node** from an internal private network range.
+ **Each pod** that you deploy gets assigned an IP from a pool of IP addresses.
+ By default, the pods and nodes can't communicate with each other by **using different IP address ranges**.


# Network Overlays
These are used to address container, pod, service and external client connectivity in k8s clusters.

# Network Policies
feature of k8s that allow ingress & egress to be restricted or enabled by pod and container instance.
