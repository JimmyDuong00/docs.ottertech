---
draft: true
tags:
  - azure
  - iam
---
We will implement Azure's lab on setting up a VPN from Azure to On Premises. https://learn.microsoft.com/en-us/training/modules/security-virtual-networks/6-virtual-wide-area-network

To begin, open up the CloudShell and run ``` Get-AzSubscription``` to see the list of subscriptions:

![[Pasted image 20240722094115.png]]

We will create a new resource group ``` New-AzResourceGroup -Location "West US" -Name "VPNRG"```:

![[Pasted image 20240722094455.png]]

Create a virtual WAN using this cmdlet, ```$virtualWan = New-AzVirtualWan -ResourceGroupName VPNRG -Name TestVWAN1 -Location "West US"```:

![[Pasted image 20240722094739.png]]


Creat a hub and configure settings
```$virtualHub = New-AzVirtualHub -VirtualWan $virtualWan -ResourceGroupName "VPNRG" -Name "Hub1" -AddressPrefix "10.1.0.0/16" -Location "westus"```:




