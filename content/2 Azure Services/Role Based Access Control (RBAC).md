
Navigate to Resource groups and select a resource group you want to enable RBAC for:

![[Pasted image 20240711133315.png]]

Navigate to the Access control (IAM) blade:

![[Pasted image 20240711133430.png]]

In the Role assignments tab, we can see all the roles that have been assigned for this resource group:

![[Pasted image 20240711133654.png]]

In the Add dropdown, select 'Add role assignment':

![[Pasted image 20240711133844.png]]

Select the desired role you want to assign:

![[Pasted image 20240711134006.png]]

Select members and assign them:

![[Pasted image 20240711134109.png]]

The user is now assigned the reader role to the resource group:

![[Pasted image 20240711134220.png]]

Remember that roles are inherited so anything created under this resource group will allow the user to access with their reader role.







