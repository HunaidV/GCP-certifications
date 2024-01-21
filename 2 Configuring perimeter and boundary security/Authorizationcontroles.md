Considerations include:
● Managing privileged roles and separation of duties with Identity and Access
Management (IAM) roles and permissions
● Granting permissions to different types of identities
● Managing IAM and access control list (ACL) permissions
● Managing Cloud Storage IAM and ACL permissions
● Designing identity roles at the organization, folder, project, and resource level
● Configuring Access Context Manager
● Applying Policy Intelligence for better permission management
● Managing permissions through groups


● https://cloud.google.com/resource-manager/docs/access-control-proj
● https://cloud.google.com/resource-manager/docs/access-control-org
● https://cloud.google.com/resource-manager/docs/access-control-folders
● https://cloud.google.com/iam/docs/understanding-roles
● https://cloud.google.com/iam/docs/understanding-roles#app-engine-roles



How to move project from one organzation to other ? 
https://cloud.google.com/resource-manager/docs/project-migration


11's Top Threats
Insufficient identity, credential, access and key management (#4)
Insecure interfaces and APIs (#7)
Misconfiguration and inadequate change control (#2)
Lack of cloud security architecture and strategy (#3)
Insecure software development
Unsecure third-party resources
System vulnerabilities
Accidental cloud data disclosure/disclosure
Misconfiguration and exploitation of serverless and container workloads
Organized crime/hackers/APT
Cloud storage data exfiltration


https://cloud.google.com/sdk/gcloud/reference/compute/security-policies/rules/
update


All about Load balancer security 



<img src="https://cloud.google.com/static/load-balancing/images/lb-product-tree.svg" alt="Getting started" />

https://cloud.google.com/load-balancing/docs/ssl-certificates/encryption-to-the-backends\


https://github.com/terraform-google-modules/terraform-docs-samples/blob/af34c43c5c16ad5f48f3926c455920f7064bd85a/lb/health_check_tcp/main.tf



Firewall rule gcloud cli 


gcloud compute --project=production-api-enabill firewall-rules create fw-allow-ssh --direction=INGRESS --priority=1000 --network=lb-network --action=ALLOW --rules=tcp:22 --source-ranges=0.0.0.0/0 --target-tags=allow-ssh