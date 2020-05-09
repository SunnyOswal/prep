# Secure Hosts
+ Pswd based authN disabled
+ SSH key based authN enabled
+ Root access disabled

# Secure k8s
+ kube-apiserver should be controlled as it is the first line of defense.
+ All Communication w ith kube-apiserver should be made with TLS.
+ All cluster communication should be secured as well
    + Recommended: Use server/Client certificates for servers/clients.
        + Server Components: kube-apiserver,etcd server,kubekete server.
        + Client components: kubectl , kube-scheduler , kube-controller-manager ,kube-proxy , kube-api-server(for etcd server & kubelete it is a client)

   + Authentication
      + Users: Admins , Devs , App End Users
      + Service Accounts : Bots
      + All "user" access is managed by kube-apiserver and it authenticates request before processing the request.
      + Authenticate via :
        + Static pswd/tpken file (Not recommended)
        + Certificate (Controller manageris responsible for all certificates)
            + TLS: 
                + Client/Server says who he is and communication is encrypted.
                + Certificate issue process: Send a CSR equest > CA will Validate Information > Sign & Send Certificate
                + Public CA have private CA hosted options as well for internal applications.
                + Certificate (Public key) naming : *.crt , *.pem
                + Private key naming: *.key , *-key.pem
        + kubeconfig : configurations having certificate, CA,key details
          + Structure
              + Clusters
              + Contexts
              + Users

   + Authorization (RBAC)
      + Role object having rules.
        + Rules:
            + apiGroups
            + resources
            + verbs
        + RoleBinding object to link roles with user
      + ClusterRoles (Roles for cluster scoped resources)
        + Resources are either namespace scoped or cluster scoped.
        + ClusterRoleBindings
        
