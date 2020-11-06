# Network Model
![Network Model](https://github.com/SunnyOswal/prep/blob/master/images/k8s-network-model.PNG)

+ an IP address is automatically assigned to **each node** from an internal private network range.
+ **Each pod** that you deploy gets assigned an IP from a pool of IP addresses.
+ By default, the pods and nodes can't communicate with each other by **using different IP address ranges**.


# Network Overlays
These are used to address container, pod, service and external client connectivity in k8s clusters.

# Network Policies
feature of k8s that allow ingress & egress to be restricted or enabled by pod and container instance.

# Exposing the application
  - For quick troubleshooting: ```kubectl port-forward```
  - For few apps, **Service** of ```type: LoadBalancer``` to expose your Pods.
  - For multiple apps, **Ingress** routes the traffic based on paths, domains, headers, etc., which consolidates multiple endpoints in a single resource that runs inside Kubernetes. It has 2 parts:
    - **Ingress manifest**  is the same as Deployment or Service in Kubernetes. This is defined by the kind part in the YAML manifest.
    - **Ingress controller** acts as a reverse proxy that routes the traffic to your Pods i.e controls the load balancers, so they know how to serve the requests and forward the data to the Pods.
