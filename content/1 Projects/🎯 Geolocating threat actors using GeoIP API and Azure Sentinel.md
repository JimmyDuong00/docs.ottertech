This post will cover:
1. Creating a virtual machine and disabling the firewall
2. Creating a Log Analytics Workspace and Data connectors
3. Create a Azure Function and Runbook
4. Downloading the Maxmind GeoIP database https://www.maxmind.com/en/home
5. Writing a Python function to convert threat actor IP addresses to real-world locations.
6. Importing the transformed data into Azure Sentinel
7. Create and display data on Azure Sentinel


### Part 4: Exposing Host Firewall to Generate Security Events 
  
We will expose the Honeypot VM to the public internet generate security events:  
  
1. Create a rule to allow all access to the NSG.

![[Pasted image 20240807143902.png]]

2. Remote back into the VM. 
3. Search for 'Windows Firewall' navigate to 'Windows Firewall Properties':
   
![[Pasted image 20240807141212.png]]

4.  Turn off all the firewalls for the VM by clicking the drop down and selecting 'Off', repeat this for the public and private profiles. Select apply when done:

![[Pasted image 20240807141319.png]]

All protection has been removed and we will now receive traffic from external sources.

In Sentinel, we can now query for failed RDP attempts:  
  
1. Go to the "Logs" section in Azure Sentinel:

![[Pasted image 20240808093158.png]]

2. Use KQL to query for failed RDP attempts (EventID = 4625):  

   ```kql  
   SecurityEvent  
   | where EventID == 4625  
   ```  

![[Pasted image 20240808093116.png]]

3. This query filters failed logon events where the EventID is equal to '4625'.  

![[Pasted image 20240808093547.png]]

4. We can also specify a more specific query to filter out information we don't need:

```kql
SecurityEvent
|where EventID == 4625
|project TimeGenerated, Account,IpAddress, TargetAccount, TargetUserName 
```

![[Pasted image 20240808094244.png]]
