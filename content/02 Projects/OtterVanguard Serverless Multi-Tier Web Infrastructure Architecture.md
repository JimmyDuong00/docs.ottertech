This post will cover the public web architecture for [[OtterVanguard]].

Creating DynamoDB:
1. Navigate to DynamoDB in the AWS Portal and select 'Create table':

![[Pasted image 20240904105803.png]]

2. Give the table a name and enter the partition key:

![[Pasted image 20240904105845.png]]

3. We have created the DynamoDB table for the website:

![[Pasted image 20240904105936.png]]
4. Navigate to the table and under 'Additional info' save the ARN for later steps:

![[Pasted image 20240904112755.png]]

## Creating Lambda Function
1. Navigate to Lambda in the AWS console and select 'Create function':

![[Pasted image 20240904110141.png]]

2. Give the function a name and select Python 3.12 for the runtime:

![[Pasted image 20240904110332.png]]

3. In the code tab, add the function code listed in the GitHub repository and select 'Deploy':

![[Pasted image 20240904110919.png]]

## Adding permissions:

In order to allow the Lambda to access the DynamoDB, we will need to add read and write permissions to the Lambda.

1. Inside the Lambda function, select on the configuration tab and permissions. Clock on the role name to be directed to another browser tab:

![[Pasted image 20240904111409.png]]

2. Select 'Add permissions' and 'Create inline policy':

![[Pasted image 20240904111814.png]]

3. In the 'Choose a service' box, type 'DynamoDB' and select it:

![[Pasted image 20240904112000.png]]

4. Select the 'Scan' and 'PutItem' for the access level:

![[Pasted image 20240904112313.png]]

5. Under Resources, paste the ARN of the DynamoDB we created in Step 1. The resource region and table name should autofill. 

![[Pasted image 20240904112956.png]]![[Pasted image 20240904113104.png]]

6. Once you have added the ARNs, select 'Next' and 'Create policy':

![[Pasted image 20240904113420.png]]
7. We can now see the DynamoDB permissions in the Lambda function:

![[Pasted image 20240904113558.png]]


## Testing the Lambda function
Now we have added the proper permissions, we can test to see if the function can add values to the DynamoDB.

1. Navigate to the code of the Lambda function and select 'Test'
