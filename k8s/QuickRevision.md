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
