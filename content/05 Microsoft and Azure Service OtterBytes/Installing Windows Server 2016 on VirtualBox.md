---
tags:
  - windows
  - virtualization
---
## Overview
This page will show you how to download and install Windows Server 2016. This is a starting point where you can branch out and begin projects such as [[Deploying an Active Directory Domain Controller]]. 
## Download the Windows ISO
Navigate to https://www.microsoft.com/en-us/evalcenter/download-windows-server-2016

Select the 'English (United States)' 64-bit ISO download:

![[Pasted image 20240814140107.png]]

## Configure virtual machine settings and install Windows
In VirtualBox, select 'New':

![[Pasted image 20240814140223.png]]

Give the virtual machine a name and load the ISO image, remember to check the 'Skip Unattended Installation' box:

![[Pasted image 20240814140340.png]]

Depending on the hardware of the computer you are running the hypervisor on, allocate the appropriate memory and processors:

![[Pasted image 20240814140548.png]]

Allocate the appropriate size of storage you would want the virtual machine to have:

![[Pasted image 20240814140620.png]]

Confirm all your settings and click 'Finish':

![[Pasted image 20240814140702.png]]

Select the 'Start' arrow to run the virtual machine:

![[Pasted image 20240814140735.png]]
## Installing Windows 2016
After booting up the machine, click 'Install now':

![[Pasted image 20240814132410.png]]

Select the 'Standard Evaluation (Desktop Experience)':

![[Pasted image 20240814133746.png]]

Accept the license terms:

![[Pasted image 20240814132613.png]]

Select the Custom installation:

![[Pasted image 20240814132646.png]]

Select the drive that you want to install the OS on:

![[Pasted image 20240814132733.png]]

Allow Windows to install:

![[Pasted image 20240814132807.png]]

After installation, it will prompt you to set an Administrator password, click 'Finish':

![[Pasted image 20240814134751.png]]

You will be greeted with the Windows lock screen:

![[Pasted image 20240814135033.png]]

If using a VM, go to the top left and select 'Input' > 'Keyboard' > 'Insert Ctrl+Alt+Del':

![[Pasted image 20240814135311.png]]

Enter the credentials for the Administrator account:

![[Pasted image 20240814135403.png]]

Allow the profile to be created and you will be greeted with the Desktop of your Windows Server:

![[Pasted image 20240814135705.png]]
## Summary
Windows is the cornerstone of every organization and learning how to successfully deploy a server that can allow you to setup Active Directory and various other services such as IIS will enable more possibilities to your organization.

If you want to learn how to install Active Directory click here: [[Deploying an Active Directory Domain Controller]] 



