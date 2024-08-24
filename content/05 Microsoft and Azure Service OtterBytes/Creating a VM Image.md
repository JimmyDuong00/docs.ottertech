When we want to decommission a VM in Azure, we can create an image for faster deployment.

Select a Virtual Machine and click on 'Capture', in the drop down, we will choose the 'Image' option:

![[Pasted image 20240812112944.png]]

Select the Resource group where you want to save the image and create a new gallery. You can also delete the current deployed VM after creating the image:

![[Pasted image 20240812113207.png]]

Give a name to the Target VM image and select the storage SKU and replica count. We will use LRS since the image is not critical to the organization and will save us storage costs:

![[Pasted image 20240812113708.png]]

Once done, select 'Review + create', navigate to the 


