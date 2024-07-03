---
title: Revoking Temporaroy Access Credentials
draft: false
tags:
  - aws
---
Securing credentials is crucial in preventing unauthorized access to the cloud. In the event that a credential is leaked, follow the steps below.

In order to revoke Temporary Access Credentials, we need to remove active sessions using the credentials. Running the revoke policy will remove any services that are assuming the role therefore, make sure to identify what services or users are using it before beginning the process.

Navigate to IAM and under Access Management, select Roles:

![[Pasted image 20240702103852.png]]

Select the role that was compromised and select 'Revoke sessions':
![[Pasted image 20240702103958.png]]

Click on 'Revoke active sessions':

![[Pasted image 20240702103745.png]]

A green banner will notify you that all active sessions have been revoked:

![[Pasted image 20240702104131.png]]

If you go back to the permissions tab, you will notice a new policy revoking older sessions:

![[Pasted image 20240702105458.png]]

Note: If EC2 instances are using the role, restart the instances and it will regenerate a new set of credentials for the service. 