---
tags:
  - iam
  - okta
---
In Okta, there are two ways you can add users in the admin dashboard. 

## Adding a Single User
Navigate to Directory > People
Select 'Add person' button:

![[Pasted image 20241109131907.png]]

Add the user's first and last name, email and select if you want to activate the account:

![[Pasted image 20241109132240.png]]

The user will receive an email asking them to sign in and set a password if we have left the 'I will set password' unchecked.

## Bulk Import
We can add users by importing them with a CSV.
Naviagate to Directory > People
Under 'More actions', select 'Import users from CSV':

![[Pasted image 20241109132706.png]]

Select 'Browse' and choose the CSV file you would like to import
Click on 'Upload CSV' and select 'Next':

![[Pasted image 20241109132909.png]]
Note: The login, firstName, lastName and email fields must be filled out for the import to be parsed successfully

Select the first option:

![[Pasted image 20241109132929.png]]

Okta will provide you a summary of what changed after the import:

![[Pasted image 20241109134514.png]]

After refreshing the page, we can now see the users that have been added:

![[Pasted image 20241109140950.png]]