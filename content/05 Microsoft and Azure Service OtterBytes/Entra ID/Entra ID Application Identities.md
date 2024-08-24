Register an on-prem application to access resources in Azure and [[Entra ID]].


## Authentication Method

When registering an app, the App Identity will require:

App (Client) ID - Similar to a username

- Client Secret - The app's password
or 
- Certificate (more secure)

## App Registrations
If we are building an app to work with [[Entra ID]] then choose App Registrations

In [[Entra ID]], navigate to App registrations and select 'New registration':

![[Pasted image 20240824132351.png]]

Give the app a name and choose the supported account types. We will be using default as we only need it for a single tenant.
We can also add the redirect URI to direct the user to the app:

![[Pasted image 20240824132534.png]]

After selecting 'Register', we can now see the app has been registered:

![[Pasted image 20240824132851.png]]

We can create client secrets and upload secrets to verify our app:

![[Pasted image 20240824133054.png]]

## Logging in using an App Identity
We can test this out by creating a VM, and assigning proper RBAC roles in the resource group.

Navigate to the resource group where the VM has been created and add a role assignment:

![[Pasted image 20240824150048.png]]

Select the 'Reader' role:

![[Pasted image 20240824150233.png]]

Select 'User, group or service principal', choose the app and select 'Review + assign':

![[Pasted image 20240824154616.png]]

#### Create a VM and use the Azure CLI to login as the application:

```ps
az login --service-principal -p XXX Enter #1 XXX -u XXX Enter #2 XXX --tenant XXX Enter #3 XXX
```

>[!warning]
>You may need to download the [Azure CLI](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli-windows?view=azure-cli-latest&tabs=azure-cli) if PowerShell does not recognize the 'az' command.

![[Pasted image 20240824153423.png]]
![[Pasted image 20240824153602.png]]
![[Pasted image 20240824152641.png]]

We have now used the app identity to log in to Azure.
## Enterprise applications
We can use Enterprise applications to manage who can use apps.

Navigate to [[Entra ID]] and select 'Enterprise applications':

![[Pasted image 20240824133950.png]]

We can see our registered app 'OtterApp' that was created earlier added:

![[Pasted image 20240824134130.png]]

Clicking on the app, we can now edit if we would like to require assignments and make the app visible to users:

![[Pasted image 20240824134513.png]]

If 'Assignment required' is positive, users will need to be added before they can access the app:

![[Pasted image 20240824134650.png]]

If we added a user, they can now see the app we registered at https://myapps.microsoft.com/:

![[Pasted image 20240824135409.png]]