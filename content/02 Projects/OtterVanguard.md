# Rapid Response, Lasting Recovery.

Welcome to Project OtterVanguard's writeup!

Website link here: otterhaven.ottertech.cloud (to be added by end of September)
## Overview
This project is split into multiple parts:
### [[OtterVanguard Serverless Multi-Tier Web Architecture]]
OtterVanguard uses AWS serverless services to provide a website to inform the public of current oil spills. Spread simulations for current events and a portal to sign in and search for custom data. The website also includes developer dashboards to monitor website statistics.

Technologies used: React, Amplify, [[S3 (Secure Storage Service)]], Lambda, CloudFront, and Relational Database Service (RDS), AWS Cognito, Prometheus and Grafana
### [[OtterVanguard Rapid Response Centers]]
When an oil spill occurs, OtterVanguard will deploy a control center using Terraform to provision infrastructure. Researchers can run simulations and predict the spread of oil spills.

[[OtterVanguard Terraform Misconfiguration Hunting with Aqua Security Trivy]]

Technologies used: Terraform, Trivy
### [[OtterVanguard Identity and Access Management (IAM)]]
Since OtterVanguard uses [[Entra ID]] to provision user accounts, this portion of the project focuses on development of cross cloud SSO to access AWS resources for OtterVanguard employees.

Services used: [[Entra ID]], AWS IAM, RBAC, [[Privileged Identity Management (PIM)]], JIT
### [[OtterVanguard Asset Management and Incident Response]]
This portion will document the process of managing enterprise connected devices and remediate any affected servers and endpoint devices in the event of a security breach. 

Technologies used: Defender for Cloud, Defender for Endpoint, Intune
### [[OtterVanguard International Compliance]]
This organization collects sensitive data so the company must remain compliant with National, Federal, and State compliance. 

Frameworks: NIST, GBLA, HIPPA, PCI/DSS, SOX, FERC, NERC
Technologies used: Purview, Defender for Cloud, [[Azure Policy]], [[Azure Initiative]]. 


