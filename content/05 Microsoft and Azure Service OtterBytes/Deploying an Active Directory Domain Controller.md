---
tags:
  - windows
  - active_directory
  - iam
---
## Prerequisites
This project requires a server or virtual machine that has Windows Server 2016 or 2022 running on it. You can learn how to install it here [[Installing Windows Server 2016 on VirtualBox]].

Once the server is running, login and we can begin the project. 
We will be using ottertechadmin for user and password
## Install Features

Once the server has booted up, wait for the Server Manager to pop up or search for it and select 'Add roles and features':

![[Pasted image 20240814094322.png]]

Select 'Next':

![[Pasted image 20240814094404.png]]

We will be selecting the 'Role-based or feature-based installation':

![[Pasted image 20240814094454.png]]

Select 'dc-01':

![[Pasted image 20240814094545.png]]

Check the 'Active Directory Domain Services':

![[Pasted image 20240814094654.png]]

Continue to the Confirmation page and select 'Install':

![[Pasted image 20240814094849.png]]

Wait for all the features to be installed:

![[Pasted image 20240814094925.png]]

Once the installation bar has filled up, select the 'Promot this server to a domain controller':

![[Pasted image 20240814095704.png]]

Select 'Add a new forest' and give it a Root domain name:

![[Pasted image 20240814100032.png]]

Enter a password for the DSRM:

![[Pasted image 20240814100125.png]]

We will skip specifying the DNS delegation option:

![[Pasted image 20240814100545.png]]

For the NetBIOS domain name, we will leave it as default:

![[Pasted image 20240814100458.png]]

We will leave all the folders as default for where to store the database, log and SYSVOL folders:

![[Pasted image 20240814100719.png]]

Confirm the options chosen and select 'Next': 

![[Pasted image 20240814100800.png]]

After passing the prerequisites check, select 'Install'. The Domain Controller will reboot a couple times:

![[Pasted image 20240814101022.png]]

After rebooting, you will be greeted with a login screen with your domain listed:

![[Pasted image 20240814142405.png]]

We can confirm Active Directory has been installed if we go to 'Windows Administrative Tools' and see all the newly installed tools:

![[Pasted image 20240814142506.png]]

# Summary
We have now installed ADDS on the the server. 