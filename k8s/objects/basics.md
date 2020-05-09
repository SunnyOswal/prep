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
+ Replica Sets:

+ Deloyments:

+ Namespaces:
+ Services:

+
