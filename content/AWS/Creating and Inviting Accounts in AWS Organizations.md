---
title: Creating and Inviting Accounts in AWS Organizations
draft: false
tags:
  - aws
---

Create or invite other AWS accounts into the organization structure.

### Invite Account
To invite an existing account to the org, you need the target account ID or email address to create and invite.
#### Send Invite
In the AWS Organizations portal:
Select 'Add and AWS Account':
![[Pasted image 20240701100211.png]]
Select 'Send Invitation':
![[Pasted image 20240701102639.png]]
In the target account, remember to accept the invitation inside the AWS Organizations portal and you are now connected to the organization. To enable role switching, follow below to enable IAM access to the account.
#### Adding IAM role to target account
Now that we have sent an invitation, we need to add the proper IAM roles in order to allow access from the management account:

![[Pasted image 20240702080800.png]]

Select 'Create Role':
![[Pasted image 20240702080843.png]]
Select:
AWS Account>Another AWS Account and enter the management account ID:
![[Pasted image 20240702080933.png]]
To add permissions, search 'administratoraccess':
![[Pasted image 20240702081017.png]] 
You can give it any role name but 'OrganizationAccountAccessRole'  is the standard role name that AWS has when allowing organization access: ![[Pasted image 20240702081048.png]]
 Click on 'Create role' when you have finished. You can now go to the Role Switching section below.
### Create New Account
In the AWS portal, navigate to AWS Organizations and select the 'Add an AWS Account':
![[Pasted image 20240701100211.png]]
Enter a unique username and email address:
![[2024-07-01 09_51_41-Add an AWS account _ AWS Organizations _ Global — Mozilla Firefox.png]]
Once the account has been created, copy the ID (Green Box) and move to the role switching section below:
![[Pasted image 20240701100310.png]]
Note: You can only access this type of account through role switching.
### Role Switching
For invited accounts: In order to implement this, in the destination account, add an IAM role to allow administrator access for another AWS account.

On the top right side, select the 'Switch Role' button:

![[Pasted image 20240701102311.png]]

Enter the:
- Account ID (Copied earlier in the 'Create Account' section above
- IAM role name you used when creating the account (Default should be 'OrganizationAccountAccessRole')
- Display name - identifier for the account
- Display Color - for easier identification
Select switch role when done:

![[Pasted image 20240701100506.png]]

The console will direct you to the new account which can be identified by the top right corner:
![[Pasted image 20240701102343.png]]

You once you switch the role, you will now see that you are in the target account on the top right corner of the console. To go back select the 'switch back' button:

![[Pasted image 20240702082152.png]]

You can now invite, create, and switch AWS accounts. 


