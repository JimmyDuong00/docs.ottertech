> [!info] 
> Azure Firewall allows us to block layer 4 of the OSI model. 
> If you're looking for layer 7 filtering, check out [[Web Application Firewall (WAF)]]


>[!warning] 
>Deploying this service will incur costs, refer to the footnotes for pricing information from Azure [^1]

Navigate to [[WIP Azure Firewall Manager]] and in the Azure firewalls blade, select 'Create':

![[Pasted image 20240717134746.png]]

Select the Subscription and Resource Group where you want to deploy the firewall. For this demonstration, we will create a new Resource Group:

![[Pasted image 20240717142134.png]]

Create a new firewall policy:

![[Pasted image 20240717142509.png]]







[^1]: Azure Firewall Pricing https://azure.microsoft.com/en-us/pricing/details/azure-firewall/#pricing