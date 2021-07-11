# hands-on-019

## Connecting to an EC2 Instance via Systems Manager



## Goal
This hands-on illustrates how to connect to an EC2 instance via [Systems Manager](https://aws.amazon.com/systems-manager/), a service that offers a central place to view and manage AWS resources.

## Overview

Benefits of connecting to an instance using Systems Manager:

* it creates a log of all the sessions and
* you don't have to distribute key pairs. 

### Step 1 - Create a Role

Create a role named *EC2RoleForSystemsManager* to be attached to the EC2 instance so it can use the Systems Manager service. Go to *IAM - Roles - Create Role*. Select *AWS Service* as the trusted entity (i.e., the entity that can assume the role). Then choose *EC2* as the use case. Click *Next: Permissions*. Next select *AmazonSSMFullAccess* policy and click *Next: Tags* and then *Next: Review*. Conclude by giving a name for your role (*EC2RoleForSystemsManager*) and a description. Make sure you save the role.

### Step 2 - Launch Instance

If you choose *Amazon Linux 2 AMI* it already comes with the SSM agent pre-installed. In step 3 (Configure Instance), make sure to select the IAM role you created previously. Therefore, your EC2 instance will have the ability to use the *EC2RoleForSystemsManager* role. Because we will be using Systems Manager to connect to our instance, we don't even have to enable ssh access this time.

## Test and Validation

Go to *Systems Manager - Managed Instances*, select your EC2 instance and, using the actions drop-down menu, start a session to connect to your instance via Systems Manager.
