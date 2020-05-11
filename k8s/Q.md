# [Pull container image from private registry](https://kubernetes.io/docs/tasks/configure-pod-container/pull-image-private-registry/#create-a-secret-by-providing-credentials-on-the-command-line)
A Kubernetes cluster uses the **Secret** of **docker-registry** type to authenticate with a container registry to pull a private image

# Difference between Annotations & Labels
+ Either labels or annotations to attach metadata to Kubernetes objects.
+ Labels can be used to select objects and to find collections of objects that satisfy certain conditions. In contrast, **annotations** are **not used** to identify and select objects.
+ The metadata in an annotation **can include characters not permitted by labels**.

# Liveness Probe vs Readiness Probe
+ **Readiness**: let Kubernetes know when your app is ready to serve traffic.
+ **Liveness**: let Kubernetes know if your app is alive or dead. If you app is alive, then Kubernetes leaves it alone. If your app is dead, Kubernetes removes the Pod and starts a new one to replace it.

# Best practices to run k8s in production
+ **Number of Replicas**: Always run at least two replicas (three or more are recommended) of your application to survive cluster updates and autoscaling without downtime.
+ **Readiness Probes**: Web applications should always configure a readinessProbe to make sure that the container only gets traffic after a successful startup
+ **Resource Requests**: Always configure resource requests for both CPU and memory. The Kubernetes scheduler and cluster autoscaler need this information in order to make the right decisions.
+ **Resource Limits**: You should configure a resource limit for memory if possible. The memory resource limit will get your container OOMKilled when reaching the limit. 

# Container Network Interface (CNI)
+ CNCF project that consists of a specification and libraries for writing plugins to configure network connectivity of containers and removing allocated resources when the container is deleted.
+ Kubernetes uses CNI as an interface between network providers and Kubernetes pod networking.
