---
tags:
  - azure
  - iam
---
After assigning users a [[Privileged Identity Management (PIM)]] role, we can perform access reviews to ensure that users that need permissions will be allowed access to elevated systems. If not, they will be removed.

In [[Entra ID]], navigate to the Identity Governance section:

![[Pasted image 20240711103346.png]]

Select 'Access reviews' and click on 'New access review':

![[Pasted image 20240711103256.png]]

Select 'Teams + Groups" and choose the group you want to review. Here we will choose the management group:

![[Pasted image 20240711104524.png]]

In the Reviews tab, select the reviewers and the recurence:

![[Pasted image 20240711104758.png]]

In the Settings tab, we can also set actions based on no responce and various other options. I selected to send a notification to myself:

![[Pasted image 20240711105010.png]]

After creating the review we can now see it under 'Access reviews':

![[Pasted image 20240711105130.png]]

Azure will send out an email to the reviewer:

![[Pasted image 20240711105358.png]]

Upon starting the review, the reviewer can now decide if they will approve or deny access:

![[Pasted image 20240711105514.png]]

If they decide to make a decision, they will need to justify their actions:

![[Pasted image 20240711105603.png]]

































