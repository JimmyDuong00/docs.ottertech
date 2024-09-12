---
title: Creating AD Users
tags:
  - iam
  - azure
---
## Types of Identities
In Azure, there are three types of user identities:

##### Cloud Identity
Users created in [[Entra ID]], completely located in the cloud
Usually ending with a @onmicrosoft.com
##### Synchronized Identity
Identities synced from on-premises [[Active Directory Users and Computers]] through [[Deploying Entra ID Connect for On prem Active Directory sync]]

##### Guest Identity
External users from other Identity providers ie. Facebook, Google, or other [[Entra ID]] Tenants


Users are the foundational building block of Azure and serve as the entryway to cloud services into our organization.

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
An admin can speed up user management by utilizing bulk operations. 

![[Pasted image 20240710090900.png]]

If you select an operation, it will allow you to download a .csv file:

![[Pasted image 20240710090832.png]]

In the .csv file, you can fill out entries for multiple users and bulk create, invite, and delete users

> [!info] Per the Azure documentation:
>If you are adding only one entry using the CSV template, you must preserve row 3 and add your new entry to row 4. 
>
>Ensure that you add the `.csv` file extension and remove any leading spaces before `userPrincipalName`, `passwordProfile`, and `accountEnabled`.

![[Pasted image 20240710080332.png]]

Once the file has been filled out, upload the file and click on 'Submit':

![[Pasted image 20240710080700.png]]

We can now see the new users added to Entra ID:

![[Pasted image 20240710090744.png]]

You can now create, invite, and perform bulk operations on users in Entra ID. 

## Default user role permissions and Guest user access
Note that when a user is created in [[Entra ID]], they will have default role permissions. You can edit them under the User settings section as well as guest user access:

![[Pasted image 20240824130309.png]]