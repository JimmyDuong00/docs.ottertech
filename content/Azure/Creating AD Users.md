#iam #azure 

Users are the foundational building block of Azure.

## Create a New User

To begin, navigate to Microsoft Entra ID and select 'Users':

![[Pasted image 20240709132217.png]]

In the 'New user' tab, select 'Create a new user':

![[Pasted image 20240709132424.png]]

Enter the user principal name and password:

![[Pasted image 20240709140142.png]]

In the properties, assignments page, fill out the required information and required roles for the user:

![[Pasted image 20240709140230.png]]

The user has now been created:

![[Pasted image 20240709140452.png]]

## Inviting External Users
In the Users blade in EntraID, select 'New user' and choose 'Invite external user':
![[Pasted image 20240709140820.png]]

Fill out the fields with the external user's email and message. You can change out the redirect URL at this stage as well:

![[Pasted image 20240709141753.png]]

The user will now receive an email invite in their inbox:

![[Pasted image 20240709142121.png]]

The default invite link sends users to https://myapplications.microsoft.com/ :

![[Pasted image 20240709142232.png]]
## Bulk Operations: Create - Invite - Delete

