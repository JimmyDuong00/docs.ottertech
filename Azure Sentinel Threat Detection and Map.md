## Lab Overview  
As more organizations move toward the cloud, we can utilize Azure Sentinel to help us detect and present this data to enable organizations to effectively respond and remediate incidents in time.
  
In this lab, we will:  
  
1. **Configure and Deploy Azure Resources**: Set up Honeypot Virtual Machine, Log Analytics Workspace, and Microsoft Sentinel.  
3. **Data Connectors**: Connect the VM to Sentinel for analysis.  
5. **Remove Protection** Turn off honeypot firewalls and allow all on Network Security Groups.  
6. **Utilize KQL**: Query logs using Kusto Query Language.  
7. **Write Custom Analytic Rules**: Detect specific Microsoft Security Events.   
## Microsoft Sentinel Lab Network Design & Topology  
  
### Part 1: Setup Lab Infrastructure  
  
#### Step 1: Create a Free Azure Account  
  
Create a free Azure account using [this link](https://azure.microsoft.com/en-us/free/). This process will automatically set up the account and associated Azure Subscription.  
#### Step 2: Deploy a Virtual Machine  
  
Deploy a Windows Virtual Machine to collect data, acting as a honeypot.  
  
1. Navigate to Azure Virtual machines and click "Create".  

![[Pasted image 20240807131100.png]]
  
2. Create a resource group and give the VM a name. Remember to choose a small VM size that will have ample processing and memory power:

![[Pasted image 20240807131532.png]]
3. Fill out the username and password of the virtual machine, this will be our login credentials when RDP to the machine. Click "Review + create" and then "Create":

![[Pasted image 20240807131740.png]]
5. We can now RDP into our virtual machine by typing in our IP address.  
![[Pasted image 20240807132735.png]]

6. Choose the use a different account option and enter the credentials you created in step 3:
![[Pasted image 20240807133033.png]]
### Part 2: Create Log Analytics Workspace and Deploy Sentinel  
  
Create a Log Analytics Workspace to store and operate log data from Azure resources.  
  
1. Search for "Microsoft Sentinel" in the Azure Portal search bar:

![[Pasted image 20240807133219.png]]
2. Follow the prompts to create a Log Analytics Workspace using the same resource group as the VM.  Click “Review and Create” to finalize the workspace.:
![[Pasted image 20240807133402.png]]  
2. Search for Sentinel and select 'Create':
![[Pasted image 20240807133754.png]]
 4. Select the workspace and 'Add': 
![[Pasted image 20240807133826.png]]

### Part 3: Getting Data into Sentinel  
Now that we have the VM running and Sentinel setup, we can import data from the VM to Sentinel.
To bring data into Sentinel:  
  
1. Navigate to the Data Connectors tab in Sentinel and select 'Go to content hub':
![[Pasted image 20240807134525.png]]
1. Search for "Windows Security" and select 'Install/Update':
![[Pasted image 20240807134713.png]]
3. After installation, go back to the data connectors tab and click on 'Open connector page':
![[Pasted image 20240807134929.png]]
1. Add a data collection rule, connect it to the resource group, and add the VM as a resource:
![[Pasted image 20240807135010.png]]
1. Fill in the Subscription and Resource Group we created earlier:
![[Pasted image 20240807135119.png]]
![[Pasted image 20240807135241.png]]
Choose 'All security Events':

![[Pasted image 20240807135319.png]]

If we go back to the data connectors page, we will see that it is now connected:

![[Pasted image 20240807135623.png]]
### Part 4: Exposing Host Firewall to Generate Security Events 
  
To generate security events:  
  
1. Create a rule to allow all access to the NSG.
![[Pasted image 20240807143902.png]]
1. Remote back into the VM. 
2. Search for 'Windows Firewall' navigate to 'Windows Firewall Properties':
![[Pasted image 20240807141212.png]]
3.  Turn off all the firewalls for the VM by clicking the drop down and selecting 'Off', repeat this for the public and private profiles. Select apply when done:
![[Pasted image 20240807141319.png]]
### Part 5: Kusto Query Language (KQL)  
  
In Sentinel, we can now query for failed RDP attempts:  
  
1. Go to the "Logs" section.  
2. Use KQL to query for failed RDP attempts (EventID = 4625):  
   ```kql  
   SecurityEvent  
   | where EventID == 4625  
   | project TimeGenerated, Computer, AccountName  
   ```  
3. This query filters failed logon events and projects the time, computer, and account name.  
  
### Part 6: Setup Workbooks
  
We will create a workbook to display the locations of where the RDP attempts originated from.
  
1. 