---
tags:
  - moc
aliases:
---
Welcome to my projects page, feel free to take a look at the various aspects of Cloud, Cybersecurity, and general IT I have worked on to strengthen my hands on skills and gain more insight with various tools and technologies.

Click on each project for more in depth explanations of the architecture and methodologies. 
### [[Project OtterVanguard]]
OtterVanguard is a multi cloud organization that focuses on wildland fires and oceanic oil spills.
This project covers various aspects of building and securing organization:
#### [[OtterVanguard Serverless Multi-Tier Web Architecture]]
OtterVanguard uses AWS serverless services to provide a website to inform the public of current oil spills. Spread simulations for current events and a portal to sign in and search for custom data. The website also includes developer dashboards to monitor website statistics.

Website link here: vanguard.ottertech.cloud (to be added by end of September)

Technologies used: React, Amplify, [[S3 (Secure Storage Service)]], Lambda, CloudFront, and Relational Database Service (RDS), AWS Cognito, Prometheus and Grafana
#### [[OtterVanguard Rapid Deployment Computation Centers]]
[[OtterVanguard Terraform Misconfiguration Hunting with Aqua Security Trivy]]
When an oil spill occurs, OtterVanguard will deploy a control center using Terraform to provision infrastructure. Researchers can run simulations and predict the spread of oil spills.

Uses HashiCorp Configuration Language (HCL) to create an instantly deployable AWS infrastructure closest to the affected region for simulating wildland fires and oil spills. Tested system resilience by performing failover tests to ensure quick recovery from disruptions.

Stored secrets in encrypted S3 buckets and state locking using RDS. Scanned code using Aqua Security Trivy and Synk to remediate vulnerabilities, exposed secrets, and misconfigurations before pushing to production repository.
#### [[OtterVanguard Threat Detection and Hunting]]
This section covers managing enterprise connected devices and remediate any affected servers and endpoint devices in the event of a security breach. 

Technologies used: Sentinel, Defender for Cloud, Defender for Endpoint, Intune

Enhanced the threat hunting model, proactively identifying vulnerabilities by analyzing threat actor Tactics, Techniques, and Procedures (TTPs) and implementing preventative measures.

#### [[OtterVanguard Regulatory Compliance]]
This organization collects sensitive data so the company must remain compliant with International, Federal, and State compliance. 

Frameworks: NIST, GBLA, HIPPA, PCI/DSS, SOX, FERC, NERC
Technologies used: Purview, Defender for Cloud, [[Azure Policy]], [[Azure Initiative]]. 
Utilized Defender for Cloud to enforce required regulatory compliance according to Federal and State standards. Frameworks: NIST, GBLA, HIPPA, PCI/DSS, SOX, ISO.

#### [[OtterVanguard Identity and Access Management (IAM)]]
Since OtterVanguard uses [[Entra ID]] to provision user accounts, this portion of the project focuses on development of cross cloud SSO to access AWS resources for OtterVanguard employees.

• Managed cross account user access using Entra ID and AWS IAM, providing SSO, secure, and role-based access control across both cloud environments.

• Configured Azure PIM for just-in-time (JIT), configuring entitlement management, reducing risks by controlling and monitoring elevated permissions.

Services used: [[Entra ID]], AWS IAM, RBAC, [[Privileged Identity Management (PIM)]], JIT
## In Progress and Planned Projects
[[Code Vulnerability Scanning using OWASP ZAP & SonarQube]]

[[Connecting Azure to On-Prem Using VPN]]

[[Container orchestration using Docker and Kubernetes]]

[[Building a RAID enabled server tosync multiple local endpoints using Syncthing]]

[[Deploying an Active Directory Domain Controller]]

[[Deploying Entra ID Connect for On prem Active Directory sync]]

[[Installing Windows Server 2016 on VirtualBox]]

## Misc. Finished Projects
[[Azure Sentinel Threat Detection]]

[[Transforming images using S3 Events and Lambda]]


## AzureGoat Series (WIP)
## [[Project AzureGoat Uncovering Azure Vulnerabilities and Securing Cloud Environments]]
## Attacking:
[[Insecure Direct Object Reference]]
[[Server Side Request Forgery]]
[[Security Misconfiguration]]
[[Using Azure Runbooks for Privilege Escalation]]

## Defending
[[Defending SQL Injection Attacks with Azure Web Application Firewall]]
[[Defending Storage Accounts]]
[[Defending Against Privilege Escalation using Azure Polices and Alerts]]
[[Adding security controls into Terraform]]