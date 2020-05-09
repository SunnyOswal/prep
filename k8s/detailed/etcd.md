# ETCD : Distributed reliable key-value store that is simple,secure & fast.

+ key-value store
    + Stores info in the form of documents or pages.
    + unstructured.
    + JSON/YAML
+ installation
    + Download binary
    + extract
    + run etcd service
+ Operate
    + PORT 2379
    + etcdctl client/CLI used.
    + ectdl get/set common cmds.
    
+ ETCD in K8S:

    + Stores info about cluster's Nodes,Pods,configs,secrets,accounts,roles,bindings,etc
    + all kubectl CLI output is from etcd cluster db.
    + when deployed from scratch , advertise-client-urls is on what etcd listens to https://${INTERNAL_IP:2379}
    + kubeadm tool creates etcd-master pods for etcd in kube-system namespace
    + in HA , as multiple master nodes exist therefore we will have etcd on each master node. We need to make sure all etcd stores are aware of each other by updating the "initial-cluster controller" configuration
