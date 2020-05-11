# [Pull container image from private regsistry](https://kubernetes.io/docs/tasks/configure-pod-container/pull-image-private-registry/#create-a-secret-by-providing-credentials-on-the-command-line)
A Kubernetes cluster uses the **Secret** of **docker-registry** type to authenticate with a container registry to pull a private image

# Difference between Annotations & Labels
+ Either labels or annotations to attach metadata to Kubernetes objects.
+ Labels can be used to select objects and to find collections of objects that satisfy certain conditions. In contrast, **annotations** are **not used** to identify and select objects.
+ The metadata in an annotation **can include characters not permitted by labels**.
