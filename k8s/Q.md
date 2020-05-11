# [Pull container image from private regsistry](https://kubernetes.io/docs/tasks/configure-pod-container/pull-image-private-registry/#create-a-secret-by-providing-credentials-on-the-command-line)
A Kubernetes cluster uses the **Secret** of **docker-registry** type to authenticate with a container registry to pull a private image

# Difference between Annotations & Labels
+ Either labels or annotations to attach metadata to Kubernetes objects.
+ Labels can be used to select objects and to find collections of objects that satisfy certain conditions. In contrast, **annotations** are **not used** to identify and select objects.
+ The metadata in an annotation **can include characters not permitted by labels**.

# Liveness Probe vs Readiness Probe
+ Readiness : let Kubernetes know when your app is ready to serve traffic.
+ Liveness : let Kubernetes know if your app is alive or dead. If you app is alive, then Kubernetes leaves it alone. If your app is dead, Kubernetes removes the Pod and starts a new one to replace it.
