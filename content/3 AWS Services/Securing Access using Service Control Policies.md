---
title: Securing Access using Service Control Policies
draft: false
tags:
  - aws
---
 
The rest of your content lives here. You can use **Markdown** here :)We can prevent accounts from accessing services through the use of SCP. 

If you apply a SCP to an Organizational Unit (OU), everything down the tree will be affected.

Navigate to the 'Policies' section of AWS Organizations:

![[content/3 AWS Services/Images/Pasted image 20240702084215.png]]

Select 'Create policy':
![[content/3 AWS Services/Images/Pasted image 20240702084321.png]]

Give it a policy name and description of what it will do:

![[content/3 AWS Services/Images/Pasted image 20240702084757.png]]

For this example I will be allowing all services while denying EC2 and Budgets:
![[content/3 AWS Services/Images/Pasted image 20240702084844.png]]

Navigate back to the main page in AWS Organisations and select which Organizational Unit (OU) you want to apply the policy to. We will be using the PROD OU:

![[content/3 AWS Services/Images/Pasted image 20240702085029.png]]

Select the polices tab and select 'Attach':

![[content/3 AWS Services/Images/Pasted image 20240702085209.png]]

Select the SCP you created earlier and click on 'Attach policy':

![[content/3 AWS Services/Images/Pasted image 20240702085306.png]]

Now that the SCP has been attached, you can navigate into the targeted account and notice that EC2 has been denied:

![[content/3 AWS Services/Images/Pasted image 20240702085705.png]]

Going into Budgets also show that it has been denied:

![[content/3 AWS Services/Images/Pasted image 20240702085839.png]]

You can now create and apply SCPs to OUs, effectively allowing or denying access on an organizational scale. 
