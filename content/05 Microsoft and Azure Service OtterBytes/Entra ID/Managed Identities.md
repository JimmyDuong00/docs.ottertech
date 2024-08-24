We can use Managed Identities when managing apps created in Azure.
Instead of using [[Entra ID Application Identities]] and having to store and secure the client secret of the app, Microsoft will take care of it.

Identity for a solution that is running in Azure, a virtual machine, app service, function apps.

## Types of Managed Identity
### System assigned
Managed identity for a single resource
Will be erased when resource is destroyed

### User assigned 
A user can create and share an identity with multiple resources
Will not be erased along with resource


## Enabling a System Assigned Managed Identity
Under a virtual machine or any other resource, navigate to Identity
Toggle the status to 'On' and Save:

![[Pasted image 20240824145343.png]]

Now that we have enabled a managed identity, we can now assign a role to the identity.

Navigate to the resource group the virtual machine is at and add a role assignment:

![[Pasted image 20240824150048.png]]

Select the 'Reader' role:

![[Pasted image 20240824150233.png]]

Select Managed identity and add the virtual machine, review and assign:

![[Pasted image 20240824150416.png]]

We have added roles to the identity.

#### Logging in as the Managed Identity
In a virtual machine, open PowerShell as Admin:

```
az login --identity
```

![[Pasted image 20240824154006.png]]

We have now logged in as the Microsoft system assigned managed identity.
### Creating a User Assigned Managed Identity

Navigate to the Managed Identities and select 'Create':

![[Pasted image 20240824155049.png]]

Select the resource group and give the instance (managed identity) a name:

![[Pasted image 20240824155205.png]]

We can go to multiple virtual machines and assign the User assigned identity:

![[Pasted image 20240824155601.png]]

>[!note]
>You will need to assign the proper RBAC roles to the User assigned Identity in the Subscription level. 

We have now assigned a user assigned managed identity to a resource. 