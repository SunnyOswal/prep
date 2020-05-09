# OS Upgrades
+ Drain nodes which will schedule pods on other nodes and the node will be marked for NoSchedule.
+ Update the node and then uncordon the node.

# K8s version
+ v1.11.3
+ Format : Major.Minor.Patch
+ Releases Type: Alpha > Beta > Stable
+ etcd & coredns will have separate versions than k8s core control plane components.
+ control core components can also have different versions but should not be more than kube-api-server
+ Allowed versions:
  + X version (Kubeapiserver) > X-1 (master node components like controller-manager,kube-scheduler) > X-2 (node components like kubelet,kube-proxy)

# Cluster Upgrade Process
+ Recommended approach: 1 minor version at a time.
+ In managed k8s in cloud providers : few clicks can upgrade cluster k8s version.
+ Via kubeadm tool:
    + Master nodes maintenance doesn't mean worker nodes is down. Just that k8s master features won't work.
    + Worker Nodes upgrade strategy
        + all nodes at a time.
        + one node at a time.
        + add newer version nodes > drain old nodes to move pods to newer ones > once all done , remove old nodes
        
# Backup & Restore
  + Backup Candidates:
    + Resource Configuration: declarative files in source control is a best practice
    + Resource Configuration: from the kube-apiserver incase somebody created the imperative way.
    + ETCD cluster
