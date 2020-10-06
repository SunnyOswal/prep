## ARCH ##
+ **Kubernetes cluster**:highest level of abstraction to start with.
  + Kubernetes clusters are composed of nodes. The term cluster refers to all the machines collectively and can be thought of as an entire running system.
+ **Nodes**: The machines in the cluster are referred to as nodes.
  + A node may be a virtual machine or a physical machine.
  +  Nodes are characterized as worker nodes and master nodes. 
  + Each worker node includes software to run containers managed by the Kubernetes control plane. 
  + Control plane itself runs on master notes. 
+ **The control plane**: set of APIs and software that Kubernetes users interact with. 
  + These APIs and software are collectively referred to as master components. 
  + The control plane schedules containers onto nodes. 
  + Think of it from a kernel perspective. The kernel schedules processors onto the CPU according to multiple factors. Certain processes need more or less compute or have different Quality of Service rules. 
  + Ultimately the scheduler does its best to ensure that every container runs. 
  + Scheduling in this case refers to the decision process of placing containers onto nodes in accordance with their declared compute requirements. 
+ **Pods** : basic building block in kubernetes
  + containers are grouped into Pods.
  + Pods may include one or more containers.
  + All containers in a Pod run on the same node.
  + The Pod is the smallest building block in Kubernetes.
  + All pods share a container network that allows any pod to communicate with any other pod, regardless of the nodes the pods are running on.
  + Each pod gets a single IP address in the container network.
  + Because pods include containers, the declaration of a pod includes all of the properties that you would expect for running containers.
  + These include the container image, any ports you want to publish to allow access into the container, choosing a restart policy to determine if a pod should automatically restart when its container fails, and limits on the cpu and memory resources.
  + Unfortunately Kubernetes can not update ports on a running pod. So we need to delete the pod and recreate it.
  + 
  +
  + 
  +
  + 
  +
  + 
  +
+ **Services** define networking rules for exposing Pods to other Pods or exposing Pods to the public Internet.
+ **Deployments** to manage deploying configuration changes to running Pods and also horizontal scaling.
+ **Manifest files** All of the desired properties are written to a manifest file.
  + Manifest files are used to describe all kinds of resources in Kubernetes, not only pods. Based on the kind of resource the manifest describes, you will configure different properties. The configuration specific to each kind of resource is referred to as its specification or spec. 
  + The manifests are sent to the Kubernetes API server where the necessary actions are taken to realize what is described in the manifest.
  + You will use kubectl to send the manifest to the API server. 
  + All manifests have the same top-level keys: api version, kind, and metadata followed by the spec.
  + Kubernetes supports multiple api versions. V1 is the core api version containing many of the most common resources such as pods and nodes.
  + Kind indicates what the resource is. 
  + Metadata includes information relevant to the resource and can help identify resources. The minimum amount of metadata is a name . Names must be unique within a Kubernetes namespace.
  + Spec is the specification for the declared kind and must match what is expected by the defined api version, for example the spec can change between the beta and the generally available API version of a resource. 
  + The pod spec defines the containers in the pod. The minimum required field is a single container which must declare its image and name.
+ **Labels** are key-value pairs that identify resource attributes, for example the application tier whether it is front-end or backend, or a region such as us-east or us-west.
   + In addition to providing meaningful identifying information, labels are used to make selections in Kubernetes.
   + For example, you could tell kubectl to get  only resources in the us-west region.
+ **Quality of Service Classes** how kubernetes can schedule pods based on their resource requests. 
  + If the pods didn’t set any resource request. That makes it easier to schedule them because the scheduler doesn’t need to find nodes with the requested amounts of resources.
  + It will just schedule them onto any node that isn’t under pressure or starved for resources. 
  + However, these pods will be the first to be evicted if a node becomes under pressure and needs to free up resources.
  + Request sets the minimum required resources to schedule the pod onto a node 
  + Limit is the maximum amount of resources you want the node to ever give the pod. 
  + You can set resource requests and limits for each container. There is also support for requesting amounts local disk by using the ephemeral-storage.
  + The pod will be guaranteed the resources you requested or it won’t be scheduled until those resources are available. 
## WORKFLOWS ##
+ kubectl create . For pod manifests, the cluster will take the following actions: 
  + selecting a node with available resources for all of the pod’s containers, 
  + scheduling the pod to that node, 
  + the node then downloads the pod’s container images
  + And runs the containers.


## TOOLS ##
**Helm** (Kubernetes package manager)
+ You write packages called charts, then you can use the Helm CLI to install and upgrade charts as releases on your cluster.
+ Charts contain all the resources, like services and deployments required to run a particular application.
+ Helm charts make it easy to share complete applications built for kubernetes. Helm charts can be found on the helm hub.
+ Rather than build the data tier up from scratch and managing the resources ourselves we could take advantage of the redis charts available for helm. 
+ Charts can be installed with just a single helm cli command. 
+ You can create a chart for your entire micro service application, package up all the services, deployments, everyting, and publish it so other members of your organization or anyone can use it.  

**Kustomize** (https://github.com/kubernetes-sigs/kustomize)
+ allows you to customize YAML manifests in Kubernetes.
+ It can help you manage the complexity of your applications running in kubernetes.
+ An obvious example is managing different environments such as test and stage.
+ We saw how we could use configMaps and secrets to help with that but kustomize makes it easier.
+ Kustomize works by using a kustomization.yaml file that declares rules for customizing or transforming resource manifest files.
+ The original manifests are untouched and remain usable as they are which is a benefit compared to other tools that require templating in the manifests rendering them unusable on their own. 

Some examples of the kinds of rules you can create in kustomize are:

- Generating configmaps and secrets from files. In our data tier example we had to write the contents of the redis config file inside the configmap data. With kustomize you can generate it directly from the config file rather than trying to keep the config file and configmap in sync.

- You can also configure common fields across multiple resources. For example, you can set the namespace, labels, annotations, and name prefixes and suffixes using kustomize. That makes it easy to customize around your organizations conventions without polluting the original manifest files. The original manifests remain pristine and easy to share and reuse in other situations. In our example we had to keep our tier labels and prefixes manually synchronized across all the resources and had to specify the namespace at the command line every time to avoid hard-coding the namespace in the manifests. Kustomize can contain all of that complexity for us.

- You can also apply patches to any field in a manifest. Kustomize allows you to define a base group of resources and apply an overlay to customize to a base. This is an easy way to manage separate environments by applying a dev name prefix and label for a development environment for example. 

+ Kustomize has been directly integrated with kubectl since Kubernetes 1.14. The kubectl kustomize command prints the customized resource manifests with kustomization defined in a kustomization.yaml file applied. To accept the kustomization and realize them in the cluster you can include the --kustomize or -k option to kubectl create or apply.

**Prometheus** (https://prometheus.io/)
+ Prometheus is an open source monitoring and alerting system.
+ Prometheus is built up of many components but at its core is a server for pulling in time series metric data and storing it.
+ Kubernetes components supply all their own metrics in Prometheus format making it easy to integrate. 
+ There is also an adapter that allows kubernetes to get metrics from Prometheus so you can do things like autoscale pods based on custom metrics.
+ Prometheus has some built-in options for visualization but it is commonly paired with Grafana to create visualizations and dashboards. 
+ Prometheus also lets you define alert rules and send out notifications. It’s easy to install Prometheus in a cluster and one way to do it is by using a helm chart.

**kubeflow** (https://www.kubeflow.org/)
+ Kubeflow is aimed at making deployment of machine learning workflows on Kubernetes simple, scalable, and portable.
+ Kubeflow is a complete machine learning stack. You can use it for complete end-to-end machine learning including build models, training them and serving them all within Kubeflow.  

**knative** (https://knative.dev/)
+ Knative is a platform built on top of Kubernetes for building, deploying, and managing serverless workloads. 
+ Serverless has gained a lot of momentum because it allows developers and companies to focus more on their code and less on the servers that run it.
