This project will use S3 events that will trigger a lambda. Every time an image is uploaded, it will trigger the Lambda and pixelizes the image. 

This lab was taken from Adrian Cantrill's course: https://github.com/acantril/learn-cantrill-io-labs/tree/master/00-aws-simple-demos/aws-lambda-s3-events
#### Create the S3 Buckets
In the S3 portal, click on 'Create bucket' we will need to create 2 buckets:

![[content/3 AWS Services/Images/Pasted image 20240702113438.png]]

Give it a unique name, I named one 'imagepixelationsource' and 'imagepixelationprocessed':

![[content/3 AWS Services/Images/Pasted image 20240702115102.png]]
![[content/3 AWS Services/Images/Pasted image 20240702115818.png]]

##### Create the Lambda role

Navigate to IAM and select 'Roles', click on 'Create role':

![[content/3 AWS Services/Images/Pasted image 20240702120014.png]]

Select 'AWS service' and choose Lambda:

![[content/3 AWS Services/Images/Pasted image 20240702120116.png]]

Give it a name and select 'Create role', we will not be adding any policies yet:

![[content/3 AWS Services/Images/Pasted image 20240702120226.png]]

Select the role and select 'Add permissions' and 'Create inline policy':
![[content/3 AWS Services/Images/Pasted image 20240702120902.png]]

Select JSON and paste the JSON copied from https://raw.githubusercontent.com/acantril/learn-cantrill-io-labs/master/00-aws-simple-demos/aws-lambda-s3-events/01_LABSETUP/policy/s3pixelator.json to here. Edit in the bucket names and account ID:

![[content/3 AWS Services/Images/Pasted image 20240702121437.png]]

Give the policy a name and click 'Create policy':

![[content/3 AWS Services/Images/Pasted image 20240702121628.png]]

#### Create the Lambda Function

Navigate to the Lambda page and click on 'Create a function':

![[content/3 AWS Services/Images/Pasted image 20240702122338.png]]

Author from scratch and fill out the required information:
	Function name
	Python 3.9
	x86_64
	Use an existing role (Select the role created in the step above)

![[content/3 AWS Services/Images/Pasted image 20240702122509.png]]

Select the 'Upload from' and choose the .zip file. Upload the .zip file from https://github.com/acantril/learn-cantrill-io-labs/blob/master/00-aws-simple-demos/aws-lambda-s3-events/01_LABSETUP/my-deployment-package.zip :

![[content/3 AWS Services/Images/Pasted image 20240702122729.png]]

Click on the 'Configuration' tab and under 'Environment Variables', select 'Edit':

![[content/3 AWS Services/Images/Pasted image 20240702122953.png]]

Add the processed bucket key and value and hit 'Save':

![[content/3 AWS Services/Images/Pasted image 20240702123115.png]]

Under 'General configuration', change the timeout to 1 minute:

![[content/3 AWS Services/Images/Pasted image 20240702123329.png]]

Under the 'Triggers' section, add a trigger:

![[content/3 AWS Services/Images/Pasted image 20240702123416.png]]

Make sure to select the source bucket or it may cause an exponential look and increase your costs!:

![[content/3 AWS Services/Images/Pasted image 20240702123606.png]]

#### Assembling everything together

Upload an image into the source bucket and see how the processed bucket will output 5 images with varying degrees of pixelation:

![[content/3 AWS Services/Images/Pasted image 20240702125012.png]]![[content/3 AWS Services/Images/Pasted image 20240702125030.png]]

![[content/3 AWS Services/Images/Pasted image 20240702125139.png]]

![[content/3 AWS Services/Images/Pasted image 20240702125252.png]]