Peering zones

DNS peering lets you send requests for records that come from one zone's namespace to another VPC network. For example, a SaaS provider can give a SaaS customer access to DNS records it manages.


The DNS zone. If you enable DNSSEC for a zone, Cloud DNS automatically manages the creation and rotation of DNSSEC keys (DNSKEY records) and the signing of zone data with resource record digital signature (RRSIG) records.

After enabling DNSSEC for your zone, you must activate DNSSEC at your registrar. To activate DNSSEC, you create a DS record for your domain in the parent zone so that resolvers know that your domain is DNSSEC-enabled and can validate its data. Each registrar has a different procedure to create this DS record; many registrars use a website form.


IMP*

If you use network tags, remember that an instance administrator can change those tags. This can circumvent security policy. Therefore, if you do use network tags in a production environment, use an automation framework to help you overcome the lack of IAM governance over the network tags. For example, use Forseti, which gives you insight into changes to your configuration and can help remediate issues.



VPC Peering 

auto mode - auto mode peering is not allowed

Auto mode - custom mode is allowed, but 10.128.0.0/9 address space should not be there in any subnet of custom mode network

Network security
VPC Network Peering does not exchange any VPC firewall rules or hierarchical firewall policies. VPC firewall rules in one VPC network can't specify targets or sources using network tags or service accounts from the other VPC network. However, the same target network tag can be used in both networks.

Every VPC network contains implied firewall rules. Because of the implied deny ingress firewall rules, Security Administrators for a local VPC network must create appropriate allow ingress firewall rules or hierarchical firewall policies. These rules or policies permit packets from the required source IP address ranges in the peered VPC network.

Because of the implied allow egress firewall rules, you don't need to create allow egress firewall rules or hierarchical firewall policies to permit packets to the destinations in the peered VPC network. However, if Security Administrators for the local VPC network have created explicit egress deny rules, you must create egress allow rules or policies.