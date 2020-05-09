# CLUSTER ARCHITECTURE

+ Master : Manage, Plan , Schedule , Monitor Nodes

    + etcd Cluster : HA key value store DB stores cluster info.
    + kube-scheduler: Identifies right node to schedules pods/containers according to requirements.
    + node-controller: onboarding new nodes, handling detroyed nodes.
    + replication-controller: ensures desired no. of containers are always running in replication group.
    + controller-manager: Manages controllers.
    + kube-apiserver: orchaestrating / exposese API to control/manage cluster. 

+ Worker Nodes : Host Application as Containers
    + container runtime: on all nodes including master
docker,rkt,containerd.
    + kubelet: agent runs on each node in cluster and listens to api server, api server fetches status from kubelet.
    + kube-proxy: hosted on each node for communication between worker nodes and necessary rules in place to make communication possible.

