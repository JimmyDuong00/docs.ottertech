---
tags:
  - azure
  - sentinel
---
## Project Overview  
As more organizations move toward the cloud, we can utilize Azure Sentinel to help us detect and present this data to enable organizations to effectively respond and remediate incidents in time.

This lab takes inspiration from Charles Q's Azure [Cloud Detection Lab]( https://cyberwoxacademy.com/azure-cloud-detection-lab-project/) from Cyberwox Academy and Josh Madakor's Sentinel Map Project. All credits to Charles and Josh I appreciate their hard work advancing the profession. 

>Note: There are some differences in steps since I plan to add extra functionality to the project later on (Allow * on ASG, Honeypot VM).

In this lab, we will:  
  
1. Setup Lab Infrastructure: Set up a Honeypot Virtual Machine, Log Analytics Workspace, and Microsoft Sentinel.  
2. Create Log Analytics Workspace and Deploy Sentinel**: Connect the VM to Sentinel for analysis.  
3. Exposing Firewalls Turn off Honeypot VM firewalls and allow all on Network Security Groups.  
4. KQL Queries: Query logs using Kusto Query Language.  
5. **Generating a Scheduled Task**:  Create a Scheduled task to build data.
6. **Write Custom Analytic Rules**: Detect specific Microsoft Security Events.   
  
### Part 1: Setup Lab Infrastructure  
  
#### Step 1: Create a Free Azure Account  
  
Create a free Azure account using [this link](https://azure.microsoft.com/en-us/free/). This process will automatically set up the account and associated Azure Subscription.  
#### Step 2: Deploy a Virtual Machine  
  
Deploy a Windows Virtual Machine to collect data, acting as a Honeypot.  
  
1. Navigate to Azure Virtual machines and click "Create".  

![[Pasted image 20240807131100.png]]
  
2. Create a resource group and give the VM a name. Remember to choose a small VM size that will have ample processing and memory power:

![[Pasted image 20240807131532.png]]
3. Fill out the username and password of the virtual machine, this will be our login credentials when RDP to the machine. Click "Review + create" and then "Create":

![[Pasted image 20240807131740.png]]
4. We can now RDP into our virtual machine by typing in our IP address.
   
![[Pasted image 20240807132735.png]]

5. Choose the use a different account option and enter the credentials you created in Step 3:
   
![[Pasted image 20240807133033.png]]
### Part 2: Create Log Analytics Workspace and Deploy Sentinel  
  
1. Search for "Microsoft Sentinel" in the Azure Portal search bar:

![[Pasted image 20240807133219.png]]

2. Follow the prompts to create a Log Analytics Workspace using the same resource group as the VM.  Click “Review and Create” to finalize the workspace:
 
![[Pasted image 20240807133402.png]]  

3. Search for Sentinel and select 'Create':
   
![[Pasted image 20240807133754.png]]
 
4. Select the workspace and 'Add': 

![[Pasted image 20240807133826.png]]

### Part 3: Getting Data into Sentinel  
Now that we have the VM running and Sentinel setup, we can import data from the VM to Sentinel.
To bring data into Sentinel:  
  
1. Navigate to the Data Connectors tab in Sentinel and select 'Go to content hub':
   
![[Pasted image 20240807134525.png]]

2. Search for "Windows Security" and select 'Install/Update':
   
![[Pasted image 20240807134713.png]]
3. After installation, go back to the data connectors tab and click on 'Open connector page':
![[Pasted image 20240807134929.png]]

3. Add a data collection rule, connect it to the resource group, and add the VM as a resource:
   
![[Pasted image 20240807135010.png]]

4. Fill in the Subscription and Resource Group we created earlier:
   
![[Pasted image 20240807135119.png]]
![[Pasted image 20240807135241.png]]

5. Choose 'All security Events':

![[Pasted image 20240807135319.png]]

6. If we go back to the data connectors page, we will see that it is now connected:

![[Pasted image 20240807135623.png]]
### Part 4: Exposing NSG and Host Firewall to Generate Security Events 
  
We will expose the Honeypot VM to the public internet generate security events:  
  
1. Create a rule to allow all access to the NSG.

![[Pasted image 20240807143902.png]]

2. Remote back into the VM. 
3. Search for 'Windows Firewall' navigate to 'Windows Firewall Properties':
   
![[Pasted image 20240807141212.png]]

4.  Turn off all the firewalls for the VM by clicking the drop down and selecting 'Off', repeat this for the public and private profiles. Select apply when done:

![[Pasted image 20240807141319.png]]

All protection has been removed and we will now receive traffic from external sources.

### Part 5: Creating a Scheduled Task to Generate Security Events
In order to setup alerts in Sentinel for events in an endpoint device.

Enable logging for the Event

1. Remote into the honeypot and search for 'Local Security Policy', Select 'Advanced Audit Policy Configuration', 'Object Access', right click on 'Audit Other Object Access Events' and select 'Properties':

![[Pasted image 20240808120432.png]]
  
2. Select all the checkboxes on the properties page:

![[Pasted image 20240808120708.png]]
3. Select 'Apply' and 'Ok'.

Creating a Scheduled Task:

1. Search 'Task Scheduler' in the Honeypot VM.
2. Select 'Action' and 'Create Task':

![[Pasted image 20240808121204.png]]

3. Give the Task a name and under the 'Configure for' section, select your OS:

![[Pasted image 20240808121435.png]]

4. On the 'Triggers' tab, select the 'New...' button to create a new trigger. On the right, edit the date to be a couple minutes ahead:

![[Pasted image 20240808121747.png]]
   
5. In the 'Actions' tab, create a new action to open Internet Explorer and select 'OK' to save when done:

![[Pasted image 20240808122013.png]]

6. If we go to the Event Viewer, we can look for the EventID '4698' and can see that it has been logged on the system:
   
![[Pasted image 20240808122412.png]]

We have now created a scheduled task.
   
### Part 6: Test Kusto Query Language (KQL) Queries for EventID

### Part 7: Writing an Analytics Rule for Incident Alerts
Writing an Analytics Rule will allow us to setup automatic incident alerts in Sentinel. This will streamline incident response and reduce investigation and remediation times.

1. Navigate to Sentinel portal and in 'Analytics', create a 'Scheduled query rule':

![[Pasted image 20240808123102.png]]

2. Give the Analytics Rule a name and description:

![[Pasted image 20240808123339.png]]

3. We can run a simple query to test if we have data connectivity for this EventID. Note the EventData, we will use this in the next step:

```
Security Event
| where EventID == 4698
```

![[Pasted image 20240808124208.png]]

4. Using the KQL query from Charles Cyberwox, we are able to have a more simplified view:

![[Pasted image 20240808124444.png]]

5. In the section below, we can enrich alerts by adding more context to the alert:

![[Pasted image 20240808124914.png]]

6. For scheduling the queries, we can run it ever 5 minutes:

![[Pasted image 20240808125355.png]]

7. Now that the rule has been created, go back into the Honeypot machine and create a few more Scheduled Tasks.

8. After waiting for a bit, we can see that Sentinel has alerted us on an incident:

![[Pasted image 20240808130715.png]]

9. Upon clicking on the 'View full details' button, we can see the Account, Host, and the potential malware that was created on the VM:

![[Pasted image 20240808131204.png]]


  
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
### Part 8: Utilizing Powershell and GeoIP API to Transform Data
In order to setup alerts in Sentinel for events in an endpoint device.

Enable logging for the Event

1. Remote into the honeypot and search for 'Local Security Policy', Select 'Advanced Audit Policy Configuration', 'Object Access', right click on 'Audit Other Object Access Events' and select 'Properties':

![[Pasted image 20240808120432.png]]
  
2. Select all the checkboxes on the properties page:

![[Pasted image 20240808120708.png]]
3. Select 'Apply' and 'Ok'.

Creating a Scheduled Task:

1. Search 'Task Scheduler' in the Honeypot VM.
2. Select 'Action' and 'Create Task':

![[Pasted image 20240808121204.png]]

3. Give the Task a name and under the 'Configure for' section, select your OS:

![[Pasted image 20240808121435.png]]

4. On the 'Triggers' tab, select the 'New...' button to create a new trigger. On the right, edit the date to be a couple minutes ahead:

![[Pasted image 20240808121747.png]]
   
5. In the 'Actions' tab, create a new action to open Internet Explorer and select 'OK' to save when done:

![[Pasted image 20240808122013.png]]

6. If we go to the Event Viewer, we can look for the EventID '4698' and can see that it has been logged on the system:
   
![[Pasted image 20240808122412.png]]

We have now created a scheduled task.

