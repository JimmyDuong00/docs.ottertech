To assign multiple polices at once we can use Initiative.

In [[Azure Policy]], navigate to the Definitions and select initiative definition:

![[Pasted image 20240715112425.png]]

Select the location, name, and create a new category for the initiative:

![[Pasted image 20240715112249.png]]


For this example we will add four policies:
```
Require a tag and its value on resources
Allowed virtual machine size SKUs
Allowed resource types
Inherit a tag from the resource group
```

![[Pasted image 20240715114857.png]]

In the Groups section, create two groups:

![[Pasted image 20240715115246.png]]

Go back into the Policies sections and at the three dots select edit groups and assign the policies to the correct group:

![[Pasted image 20240715115421.png]]

In the Policy parameters, assign the values required for the initiative. ie. virtualMachines, staticSites, and storageAccounts:

![[Pasted image 20240715123209.png]]

Once done, Review and Create the initiative.

Navigate back to the Definitions blade in [[Azure Policy]]. It will take a while to load:

![[Pasted image 20240715123622.png]]

Click on the Initiative and select the Assign initiative button:

![[Pasted image 20240715125238.png]]

Select the scope of the initiative and Create:

![[Pasted image 20240715125909.png]]

As we can see here, there is one policy that is showing non compliant:

![[Pasted image 20240716090518.png]]

The resources in the resource group is missing a tag so we can add it to the resources to remain compliant:

![[Pasted image 20240716090702.png]]

After a while, we can see the Initiative now shows everything as compliant:

![[Pasted image 20240716131956.png]]

We can also see the initiative in action when attempting to create a Log Analytics Workspace:

![[Pasted image 20240716091238.png]]