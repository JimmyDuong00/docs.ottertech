This project is a fully scaled enterprise focused on wildland fire tracking, oil spill prediction, analysis, and incident response.
## Overview
This project covers various aspects of building an organization:
### [[OtterVanguard Serverless Multi-Tier Web Architecture]]
OtterVanguard uses AWS serverless services to provide a website to inform the public of current oil spills. Spread simulations for current events and a portal to sign in and search for custom data. The website also includes developer dashboards to monitor website statistics.

Website link here: otterhaven.ottertech.cloud (to be added by end of September)

Technologies used: React, Amplify, [[S3 (Secure Storage Service)]], Lambda, CloudFront, and Relational Database Service (RDS), AWS Cognito, Prometheus and Grafana
• Deployed a serverless web facing application to allow for public information, updates, and fire reports (AWS Amplify, Lambda, CloudFront, RDS).

• Set up uptime monitoring with Grafana dashboards and Prometheus for real-time performance tracking for AWS resources (S3, Lambda, Website uptime).
#### [[WIP OtterVanguard Rapid Deployment Computation Centers]]
When an oil spill occurs, OtterVanguard will deploy a control center using Terraform to provision infrastructure. Researchers can run simulations and predict the spread of oil spills.

[[OtterVanguard Terraform Misconfiguration Hunting with Aqua Security Trivy]]

• Utilized HashiCorp Configuration Language (HCL) to create an instantly deployable AWS infrastructure closest to the affected region for simulating wildland fires and oil spills. Tested system resilience by performing failover tests to ensure quick recovery from disruptions.

• Stored secrets in encrypted S3 buckets and state locking using RDS. Scanned code using Aqua Security Trivy and Synk to remediate vulnerabilities, exposed secrets, and misconfigurations before pushing to production repository.

**Threat Detection and Hunting**                
• Configured Microsoft Sentinel with custom KQL queries for reactive threat detection and automated remediation using playbooks.

### [[OtterVanguard Asset Management and Incident Response]]
This portion will document the process of managing enterprise connected devices and remediate any affected servers and endpoint devices in the event of a security breach. 

Technologies used: Defender for Cloud, Defender for Endpoint, Intune

• Enhanced the threat hunting model, proactively identifying vulnerabilities by analyzing threat actor Tactics, Techniques, and Procedures (TTPs) and implementing preventative measures.
Incident Response using SP800-61 Rev. 2
#### [[OtterVanguard Regulatory Compliance]]
This organization collects sensitive data so the company must remain compliant with International, Federal, and State compliance. 

Frameworks: NIST, GBLA, HIPPA, PCI/DSS, SOX, FERC, NERC
Technologies used: Purview, Defender for Cloud, [[Azure Policy]], [[Azure Initiative]]. 
• Utilized Defender for Cloud to enforce required regulatory compliance according to Federal and State standards. HIPPA, NIST, ISO.

#### [[OtterVanguard Identity and Access Management (IAM)]]
Since OtterVanguard uses [[Entra ID]] to provision user accounts, this portion of the project focuses on development of cross cloud SSO to access AWS resources for OtterVanguard employees.

• Managed cross account user access using Entra ID and AWS IAM, providing SSO, secure, and role-based access control across both cloud environments.

• Configured Azure PIM for just-in-time (JIT), configuring entitlement management, reducing risks by controlling and monitoring elevated permissions.

Services used: [[Entra ID]], AWS IAM, RBAC, [[⌛ Configuring Privileged Identity Management (PIM) access for critical infrastructure]], JIT

