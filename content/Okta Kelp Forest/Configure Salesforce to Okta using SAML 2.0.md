---
tags:
  - okta
  - iam
---
This is a follow along from Bryan Ly's Okta Course on Udemy.

# Objectives
Create a Salesforce Developer Account
Connect Salesforce to Okta using SAML 2.0
Test SSO from Okta to Salesforce

# Create a Salesforce Developer Account
https://developer.salesforce.com/signup

Enter your credentials to gain access to Salesforce:

![[Pasted image 20241218112341.png]]

After submitting the form, go to the email used and look for the account verification:

![[Pasted image 20241218112812.png]]

Reset your password and login to Salesforce:

![[Pasted image 20241218113057.png]]

# Add Salesforce in Okta
In Okta, go to Applications > Browse App Catalog > Search for Salesforce:

![[Pasted image 20241218113355.png]]

![[Pasted image 20241218113514.png]]

Select Salesforce and click on Add Integration:

![[Pasted image 20241218113604.png]]

In the Sign On options, Select 'SAML 2.0' and for Application username format select 'Custom':

Enter the Okta Expression Language ```
```
substringBefore(user.email, '@')+"YOURDOMAINHERE"
```


![[Pasted image 20241218114910.png]]

Select Done.

# Configure Salesforce Settings

In the top left search box, search for Single Sign-On settings:

![[Pasted image 20241218121556.png]]

For first time setup, enable SAML by clicking the Edit and tick the 'SAML Enabled', click save:

![[Pasted image 20241218122144.png]]

![[Pasted image 20241218122216.png]]

Create a new settings by selecting the 'New' button:


Inside the Okta portal in the Salesforce application, there is a SAML setup guide, there will be data we need to enter into Salesforce.

 ![[Pasted image 20241218123231.png]]
![[Pasted image 20241218123558.png]]

Cross reference and fill out the data in Salesforce:

![[Pasted image 20241218124149.png]]

After saving, take note of the Endpoints section, we will use this to input into the application section in Okta:

![[Pasted image 20241218124936.png]]

In Okta, paste the data into Advanced Sign-On Settings:

![[Pasted image 20241218125155.png]]

Assign users to the Salesforce application in Okta. 
![[Pasted image 20241218130257.png]]
We are now ready to test our integration.

# Test Connection
In the user portal, select the Salesforce.com app:

![[Pasted image 20241218131053.png]]

It should direct you straight into the Salesforce portal:

![[Pasted image 20241218131139.png]]
# Things to Note
When assigning users to Salesforce in Okta, I had an issue where the user did not have the '@' sign added to their username so Salesforce ran into an error. We can fix this during the user assignment process. 

