How to Use a Network Policy on Google Kubernetes Engine

Network connections can be restricted at two tiers of your Kubernetes Engine infrastructure. The first, and coarser grained, mechanism is the application of Firewall Rules at the Network, Subnetwork, and Host levels. These rules are applied outside of the Kubernetes Engine at the VPC level.

While Firewall Rules are a powerful security measure, and Kubernetes enables you to define even finer grained rules via Network Policies. Network Policies are used to limit intra-cluster communication. Network policies do not apply to pods attached to the host's network namespace.