---
title: Connecting CloudWatch to EC2 Instances
tags:
  - aws
---

Create an instance and connect to it:


run ```sudo dnf install amazon-cloudwatch-agent```:

![[Pasted image 20240703113643 1.png]]

Type ```y``` and hit 'Enter':

![[Pasted image 20240703113759 1.png]]

## Create an IAM role
Navigate to IAM and under Access Management, select Roles and click on the 'Create role' button:

![[Pasted image 20240703114111 1.png]]

Select AWS Service and EC2:

![[Pasted image 20240703114211 1.png]]

Search up 'CloudWatchAgentServerPolicy' and 'AmazonSSMFullAccess':

![[Pasted image 20240703114349 1.png]]
![[Pasted image 20240703114418 1.png]]

Give the role a name and select the 'Create role' button:

![[Pasted image 20240703114613 1.png]]

Navigate back into the EC2 portal and right click the instance, go to Security and choose 'Modify IAM role':

![[Pasted image 20240703114730 1.png]]

Select the role created earlier in the drop down box and select 'Update IAM role':

![[Pasted image 20240703114910 1.png]]

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

![[Pasted image 20240703120510 1.png]]

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

![[Pasted image 20240703121833 1.png]]

Select the access_log and choose a stream:

![[Pasted image 20240703122101 1.png]]

You can see all the log events:

![[Pasted image 20240703122208 1.png]]

### Checking Metrics
In the CloudWatch page, navigate to 'All metrics' and select 'CWAgent'
![[Pasted image 20240703122330 1.png]]

Due to installing the CloudWatch agent on the instance, you can now see all the operating system level metrics:

![[Pasted image 20240703122610 1.png]]

A4L instance CPU metrics:
![[Pasted image 20240703123301 1.png]]

This project covered installing the CloudWatch Agent on an EC2 instance.

[^1]: Adrian Cantrill's Lab Commands: https://learn-cantrill-labs.s3.amazonaws.com/awscoursedemos/0013-aws-associate-ec2-cwagent/lesson_commands_AL2023.txt