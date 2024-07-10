Multifactor Authentication allows a more secure access to accounts, confirming the user is who they say they are. 

## Configuring Multifactor Authentication in Azure

Navigate to [[Entra ID]] and select 'Users', select 'Per-user MFA':

![[Pasted image 20240710142707.png]]
 Select a user you want to turn on MFA:
 
![[Pasted image 20240710142812.png]]

Click on 'Enable' and 'enable multi-factor auth':

![[Pasted image 20240710142857.png]]

The user now has MFA enabled:

![[Pasted image 20240710143013.png]]

## Bulk Update
Bulk turning on MFA for users is simple, in the MFA page, select 'bulk update':

![[Pasted image 20240710143133.png]]

Upload the .csv file with the user information and click the next arrow:

![[Pasted image 20240710143210.png]]

Once the file has been verified, you will have bulk added MFA to users.

## Verification Options and Trusted IPs

You can edit verification options by navigating to the 'service settings' section:

![[Pasted image 20240710143605.png]]
## Lockout
Navigate to Multifactor Authentication in the portal and select 'Account lockout':

![[Pasted image 20240710142253.png]]


