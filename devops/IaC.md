# Immutable Infrastructure  
https://rollout.io/blog/immutable-infrastructure/  
https://medium.com/rigged-ops/a-tale-of-two-terraforms-a-model-for-managing-immutable-and-mutable-infrastructure-fa0f5422c27b
# Choosing between Terraform vs. Ansible vs. Puppet vs. Chef 
Some of the tools are going to be a better fit for certain types of tasks.  
**Common Combinations:**  
+ **Provisioning plus configuration management**
     + Terraform and Ansible. You use Terraform to deploy all the underlying infrastructurethen use Ansible to deploy your apps on it.
     + Terraform adds special tags to your servers and Ansible uses those tags to find the server and configure them.
+ **Provisioning plus server templating**
     + Terraform and Packer. You use Packer to package your apps as virtual machine images. You then use Terraform to deploy servers with these virtual machine images.
     +  this is an immutable infrastructure approach, which will make maintenance easier.
+ **Provisioning plus server templating plus orchestration**  
     + 

![IaCComparison](https://github.com/SunnyOswal/prep/blob/master/images/IaC.PNG)
+ **Configuration Management vs Provisioning**  
     + Chef, Puppet, Ansible, and SaltStack are all **configuration management tools(CMT)**, which means they are designed to install and manage software on existing servers.
     + CloudFormation and Terraform are **provisioning tools(PT)**, which means they are designed to provision the infra themselves leaving the job of configuring those servers to other tools.
+ **Mutable Infrastructure vs Immutable Infrastructure**
     + Configuration management tools typically default to a mutable infrastructure paradigm.
     + This often leads to a phenomenon known as configuration drift, where each server becomes slightly different than all the others, leading to subtle configuration bugs that are difficult to diagnose and nearly impossible to reproduce.
     + Terraform deploy that image across a set of totally new servers, and then undeploy the old servers. This approach reduces the likelihood of configuration drift bugs.
+ **Procedural vs Declarative**
     + **Chef & Ansible** encourage a **procedural style** where you write code that specifies, step-by-step, how to to achieve some desired end state. **ORDER** IN WHICH TEMPLATES ARE APPLIED IS IMPORTANT !
     + Reusability of procedural code is inherently limited . As a result, procedural code bases tend to grow large and complicated over time.
     + **Terraform, CloudFormation, SaltStack, and Puppet** all encourage a more **declarative style** where you write code that specifies your desired end state, and the IAC tool itself is responsible for figuring out how to achieve that state.
     + Terraform codebases tend to stay small and reusable .
     + Rolling, zero-downtime deployment, are hard to express in purely declarative terms.
+ **Master Versus Masterless**
     + **Chef, Puppet, and SaltStack** client to issue new commands to the master server, and the master server either pushes the updates out to all the other servers, or those servers pull the latest updates down from the master server on a regular basis.
     + This adds extra infra , maintenance & security overhead.
     + **Ansible** works by connecting directly to each server over SSH, so again, you don’t have to run any extra infrastructure or manage extra authentication mechanisms.
+ **Agent Versus Agentless**
     + **Chef, Puppet, and SaltStack** all require you to install agent software.
     + All of these extra moving parts **introduce a large number of new failure modes** into your infrastructure. Each time you get a bug report , you’ll have to figure out if it’s a bug in your application code, or your IAC code, or the configuration management client, or the master server(s), or the way the client talks to the master server(s), or the way other servers talk to the master server(s), or…
     + **Ansible, CloudFormation, Heat, and Terraform** do not require you to install any extra agents.
     + **Ansible**, your servers need to run the SSH Daemon, which is common to run on most servers anyway.
+ **Large Community vs Small Community**
     + **Terraform and Ansible** are experiencing explosive growth.
+ **Mature Versus Cutting Edge**
     + Terraform’s biggest weakness, cutting-edge tool is that it is not as mature as some of the other IAC options.
