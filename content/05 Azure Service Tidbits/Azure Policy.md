Policies allow administrators to forbid the creation of resources or remain compliant with certain regulations.

If you want to assign multiple policies check out [[Azure Initiative]]
Navigate to Azure Policy and under Definitions:

![[Pasted image 20240715093310.png]]

For this example, we will be using the 'Allowed locations':

![[Pasted image 20240715093354.png]]

Select 'Assign policy':

![[Pasted image 20240715093520.png]]

Select the scope and optionally add exclusions to the policy if you need to:

![[Pasted image 20240715094145.png]]

In the Parameters tab, select the location where you will allow resources to be created:

![[Pasted image 20240715095631.png]]

Select create and now the policy has been assigned. 

If we try to create a resource outside of West US, we are denied:

![[Pasted image 20240715100106.png]]



