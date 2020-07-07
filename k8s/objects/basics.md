# Top Level/Root Level mandatory YAML properties for each object in K8S:
+ apiVersion
+ kind
+ metadata
+ spec

-- Remember "AKMS" shorthand.

# Objects
+ POD: 
    + Containers are encapsulated under pods object and is the smallest object that can be created in k8s
    + Scaling is always done by deploying on different pod and not on the same pod.
    + Multi containers are possible but they are not of the same kind instead are sidecar patterns(helper containers).
+ Replication Controller:
    + Old Object. Not Recommended now.
    + Used to create replicas/containers.
+ Replica Sets:
    + Used to create replicas/containers.
    + A selector allows the replica set to identify all the pods running underneath it.
    + "Spec > Selector" is major diff b/w RC and it enables Replicaset to manage pods existings pods/even who were not created by replica set.
    + "Labels" act as a filter for replicset to understand which pods to monitor.
+ Deployments:
    + Creates a management object one level higher than a replica set. 
    + Supports different kind of updates. like rolling upgrade,etc
    + Supports rollback & pausing .
    + Uses replica set internally.
+ Namespaces:
    + provides isolation for resources.
    + resources within same namespace can address each other with just the name of resource.
    + you can access other namepaces resources by using a specific syntax in CLI as well as k8s files.
    + "default" namespace is created by default and not recommended to use this and explicitly create respective namespaces.
    + "kube-system" is the namespace for internal k8s components.
    + "kube-public" is for exposed resources to public.
+ ResourceQuota:
+ Services:
    + enables connectivity between group of pods and external services/DB's. 
    + External > service > Node > Pods
    + NodePort : Creates/maps port to access
        + TargetPort: Port on Pod where service forwards the traffic to. The ports here are from service point of view.
        + Port: Port on service itself. This is the only mandatory port out of 3 ports.
        + NodePort: Port on node. Range: 30000-32767
        + Labels/selectors are used to map ports with pods.
    + ClusterIP: Creates service to access
        + Connectivity between services is setup using cluster IP service object . 
        + This service name will be used for connectivity instead of any IP's which usually are dynamic in k8s.
        + This is default service Type.
        + It needs target port & port. 
        + Labels/selectors are used to map ports with pods.
    + LoadBalancer: 
        + 
+ ConfigMaps
    + Manages configurations centrally in the form of key-value pairs and inject them as env variables as part of pod creation.
    + Stores in plain text so not good for secrets.
    + 2 phases: Create configmaps and then consuming in pods with below option :
        + As Env Variables by using "envFrom > configMapRef"
        + As files in volumes by using "volumes > configMap"
+ Secrets
    + stored in encoded format.
    + 2 phases: Create secret and then consuming in pods .
        + hash logic is used to decode the encoded secret in secret object
        + consumed via environment variable : "envFrom >secretRef"
        + consumed via volume files : "volumes > secret"
