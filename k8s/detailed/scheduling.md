+ Labels & Selectors
  + Labels: properties attached to each object
  + Selectors: filters objects on the basis of labels
  
+ Taints & Tolerations (adds restrictions only)
  + Taints: are set on nodes . Below are taint-effects:
      + NoSchedule
      + PreferNoSchedule
      + NoExecute: if configured, will remove any pre existing pods from the node
  + Tolerations: are set on pods.
      + whether pods can tolerate a taint or not.
      
+ Node Affinity (pods on specific nodes)
  + Taints & Tolerations can't make sure if pod will be scheduled on  a particular node. They are only used to restrictions.
  + Node affinity is used to schedule pod on a particular node.
  + "Node selectors" can't do advanced operators and can only match selectors with labels.
  + Key , operator, value is used for matching.
  + "Operators" example: In , NotIn , Exists ,etc
  + Logic for not pods matching labels is handled by Type of node affinity:
    + requiredDuringSchedulingIgnoredDuringExecution
    + preferredDuringSchedulingIgnoredDuringExecution

+ ResourceLimits:
  + Default limits are set for containers.
  + CPU Limits is hard limit but memory is soft limit and pods can be scheduled.
  + Resource Requests: CPU , MEMORY , DISK
  
 + DaemonSets:
    +  Like replica set but makes sure each replica is on each node.
    + If new node added/removed, replica will be added/removed by daemon sets.
    + Use Case: kube-proxy
  
