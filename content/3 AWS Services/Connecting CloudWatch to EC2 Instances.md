---
title: Connecting CloudWatch to EC2 Instances
tags:
  - aws
---

Create an instance and connect to it:


run ```sudo dnf install amazon-cloudwatch-agent```:

![[content/3 AWS Services/Images/Pasted image 20240703113643.png]]

Type ```y``` and hit 'Enter':

![[content/3 AWS Services/Images/Pasted image 20240703113759.png]]

## Create an IAM role
Navigate to IAM and under Access Management, select Roles and click on the 'Create role' button:

![[content/3 AWS Services/Images/Pasted image 20240703114111.png]]

Select AWS Service and EC2:

![[content/3 AWS Services/Images/Pasted image 20240703114211.png]]

Search up 'CloudWatchAgentServerPolicy' and 'AmazonSSMFullAccess':

![[content/3 AWS Services/Images/Pasted image 20240703114349.png]]
![[content/3 AWS Services/Images/Pasted image 20240703114418.png]]

Give the role a name and select the 'Create role' button:

![[content/3 AWS Services/Images/Pasted image 20240703114613.png]]

Navigate back into the EC2 portal and right click the instance, go to Security and choose 'Modify IAM role':

![[content/3 AWS Services/Images/Pasted image 20240703114730.png]]

Select the role created earlier in the drop down box and select 'Update IAM role':

![[content/3 AWS Services/Images/Pasted image 20240703114910.png]]

### Installing the Agent
Go back into the EC2 instance, run:
```sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-config-wizard```

This will begin the CloudWatch Agent Configuration Manager
From Adrian Cantrill's command page summarized[^1] : 
```
Accept all defaults, until default metrics .. pick advanced.

/var/log/secure
/var/log/httpd/access_log
/var/log/httpd/error_log

(Accept default instance ID)
Accept the default retention option

Answer no to any more logs
Save config into SSM
Use the default name.

# Config will be stored in /opt/aws/amazon-cloudwatch-agent/bin/config.json and stored in SSM
```

Once the configuration has been completed, navigate to the SSM in the portal: 

![[content/3 AWS Services/Images/Pasted image 20240703120510.png]]

This configuration can now be used in any EC2 deployment.

Create a folder named 'collectd' and a database file 'types.db', this is a bug workaround since CloudWatch expects this folder in the system and Amazon Linux does not have it installed:
```
sudo mkdir -p /usr/share/collectd/
sudo touch /usr/share/collectd/types.db
```

Run this command to start the agent and pull the configuration file from the parameter store in SSM, then it will load the data into CloudWatch Logs:

```
sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl -a fetch-config -m ec2 -c ssm:AmazonCloudWatch-linux -s
```

### Checking CloudWatch Logs
Go to CloudWatch and under log groups you can see the logs that were generated:

![[content/3 AWS Services/Images/Pasted image 20240703121833.png]]

Select the access_log and choose a stream:

![[content/3 AWS Services/Images/Pasted image 20240703122101.png]]

You can see all the log events:

![[content/3 AWS Services/Images/Pasted image 20240703122208.png]]

### Checking Metrics
In the CloudWatch page, navigate to 'All metrics' and select 'CWAgent'
![[content/3 AWS Services/Images/Pasted image 20240703122330.png]]

Due to installing the CloudWatch agent on the instance, you can now see all the operating system level metrics:

![[content/3 AWS Services/Images/Pasted image 20240703122610.png]]

A4L instance CPU metrics:
![[content/3 AWS Services/Images/Pasted image 20240703123301.png]]

This project covered installing the CloudWatch Agent on an EC2 instance.

[^1]: Adrian Cantrill's Lab Commands: https://learn-cantrill-labs.s3.amazonaws.com/awscoursedemos/0013-aws-associate-ec2-cwagent/lesson_commands_AL2023.txt