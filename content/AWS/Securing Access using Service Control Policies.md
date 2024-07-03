---
title: Securing Access using service control policies
draft: false
tags:
  - aws
---
 
The rest of your content lives here. You can use **Markdown** here :)We can prevent accounts from accessing services through the use of SCP. 

If you apply a SCP to an Organizational Unit (OU), everything down the tree will be affected.

Navigate to the 'Policies' section of AWS Organizations:

![[Pasted image 20240702084215.png]]

Select 'Create policy':
![[Pasted image 20240702084321.png]]

Give it a policy name and description of what it will do:

![[Pasted image 20240702084757.png]]

For this example I will be allowing all services while denying EC2 and Budgets:
![[Pasted image 20240702084844.png]]

Navigate back to the main page in AWS Organisations and select which Organizational Unit (OU) you want to apply the policy to. We will be using the PROD OU:

![[Pasted image 20240702085029.png]]

Select the polices tab and select 'Attach':

![[Pasted image 20240702085209.png]]

Select the SCP you created earlier and click on 'Attach policy':

![[Pasted image 20240702085306.png]]

Now that the SCP has been attached, you can navigate into the targeted account and notice that EC2 has been denied:

![[Pasted image 20240702085705.png]]

Going into Budgets also show that it has been denied:

![[Pasted image 20240702085839.png]]

You can now create and apply SCPs to OUs, effectively allowing or denying access on an organizational scale. 
