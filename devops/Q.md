# Common Workflow in Configuration management tools
+ You have a set of machines that you want to control what software is installed on them.
+ You also have a configuration management server that holds all of your different machine configurations.
+ When you want to make a change, you update the configuration on the server. Then the client machines connect to the server, get the update, and make the appropriate changes

# Mutable Infrastructure VS Immutable Infrastructure
+ **Mutable Infrastructure**: 
    + updating an existing set of machines instead of replacing them with new ones.
    + Configuration management tools like Chef,Puppet & Ansible are used to manage mutable infra.
    + Orchestrating the lifecycle of the underlying infrastructure is usually out of scope for configuration management tools. 
+ **Immutable Infrastructure**:
    + recreating your infrastructure from scratch every time you want to make a change.
    + It usually involves making a machine or container image then reusing that image.
    + useful when you want to prevent software and configuration drift.
