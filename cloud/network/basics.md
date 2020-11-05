**NAT Gateway**
- You must specify the **public subnet** in which the NAT gateway should reside.
- You can use a network address translation (NAT) gateway to enable instances in a private subnet to connect to the internet or other AWS services, but prevent the internet from initiating a connection with those instances.
- You must also specify an **Elastic IP address** to associate with the NAT gateway when you create it.
- The Elastic IP address cannot be changed after you associate it with the NAT Gateway.
- After you've created a NAT gateway, you must **update the route table associated with one or more of your private subnets** to point internet-bound traffic to the NAT gateway. This enables instances in your private subnets to communicate with the internet.
