
In order to implement conditional access policies, we need to disable the default ones put in place by Azure.

Navigate to [[Entra ID]], under Properties select 'Manage security defaults': 
![[Pasted image 20240711090321.png]]

In the 'Security defaults' choose the 'Disabled' option in the dropdown and click save:

![[Pasted image 20240711090654.png]]

In [[Entra ID]], select 'Create new policy':

![[Pasted image 20240711090810.png]]


Give the policy a name and select the scope of the policy, here we are blocking user access to the Azure portal:

![[Pasted image 20240711092226.png]]


In the 'Target resources' section, select 'Cloud apps', and select 'Microsoft Admin Portals'. This will block access to Microsoft 365 admin center, Exchange admin center, Azure portal, Microsoft Entra admin center:

![[Pasted image 20240711093155.png]]

In the Conditions, we can configure access based on signals such as location and device state. For this demonstration, we will totally block access so we will not configure anything here:

![[Pasted image 20240711093316.png]]

In the Grant section, select 'Block access' as we are completely blocking access for the user. Instead, we can allow access depending on various factors:

![[Pasted image 20240711093612.png]]

Turn on the 'Enable policy' and click Create:

![[Pasted image 20240711093804.png]]

The user is now blocked from accessing the Azure portal. 

## Checking Sign in Logs
To check the sign in logs, navigate to [[Entra ID]] > Conditional Access > Monitoring > Sign in logs. Here we can see the user that signed in, the application and various other datapoints such as date and access location.

![[Pasted image 20240711101342.png]]
