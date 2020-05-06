# Immutable Infrastructure  
https://rollout.io/blog/immutable-infrastructure/  
https://medium.com/rigged-ops/a-tale-of-two-terraforms-a-model-for-managing-immutable-and-mutable-infrastructure-fa0f5422c27b
# Choosing between Terraform vs. Ansible vs. Puppet vs. Chef 
Some of the tools are going to be a better fit for certain types of tasks  
![IaCComparison](https://github.com/SunnyOswal/prep/blob/master/images/IaC.PNG)
+ **Configuration Management vs Provisioning**  
     + Chef, Puppet, Ansible, and SaltStack are all **configuration management tools**, which means they are designed to install and manage software on existing servers.
     + CloudFormation and Terraform are **provisioning tools**, which means they are designed to provision the infra themselves leaving the job of configuring those servers to other tools.
+ **Mutable Infrastructure vs Immutable Infrastructure**
     + Configuration management tools typically default to a mutable infrastructure paradigm.
     + This often leads to a phenomenon known as configuration drift, where each server becomes slightly different than all the others, leading to subtle configuration bugs that are difficult to diagnose and nearly impossible to reproduce.
     + Terraform deploy that image across a set of totally new servers, and then undeploy the old servers. This approach reduces the likelihood of configuration drift bugs.
+ **Procedural vs Declarative**
+ **Master Versus Masterless**
+ **Agent Versus Agentless**
+ **Large Community vs Small Community**
+ **Mature Versus Cutting Edge**
