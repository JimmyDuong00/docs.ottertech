

## Creating a Blueprint:

![[Pasted image 20240717084458.png]]

There are samples of various blueprints we can deploy but for this example we will be creating a blank blueprint:

![[Pasted image 20240717090152.png]]

Give the blueprint a name and define which subscription where it should be located at:

![[Pasted image 20240717090601.png]]

Select 'Add artifact' and specify the Artifact type and you can fill in the details now or leave it when you assign the blueprint:

![[Pasted image 20240717100654.png]]

We can also add [[Azure Policy]] and [[Azure Initiative]] artifacts to the blueprint:

![[Pasted image 20240717103213.png]]

Once done, select Save Draft.
## Publish the Blueprint

Navigate to the Blueprint definitions and you will find the newly created blueprint. You might need to find the location of the blueprint (This example was saved in Azure subscription 1):

![[Pasted image 20240717103916.png]]

On the three dots, select Publish blueprint:

![[Pasted image 20240717104106.png]]

Give it a version number and click on publish:

![[Pasted image 20240717104205.png]]

## Assign the Blueprint

In the blueprint definitions blade, select Assign blueprint:

![[Pasted image 20240717104431.png]]

Fill in the Location and values that you specified when creating a blueprint, once done select Assign:

![[Pasted image 20240717104606.png]]

Once the blueprint is finished assigning, we can see it in the Assigned blueprints:

![[Pasted image 20240717104722.png]]

The resource group have been created and [[Azure Initiative]] deployed:

![[Pasted image 20240717104830.png]]

![[Pasted image 20240717104858.png]]
![[Pasted image 20240717105313.png]]





