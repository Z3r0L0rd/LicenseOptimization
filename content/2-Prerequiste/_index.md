---
title : "Preparation Steps"
date: "2025-07-29" 
weight : 2 
chapter : false
pre : " <b> 2. </b> "
---
### AWS Account 
To perform this workshop, you need an AWS account to access the AWS Management Console. If you don't have an account yet, register at [AWS](https://aws.amazon.com/). You may need to add an international payment card (Mastercard/Visa), but you can access and start using AWS services.

Start registering today [here](https://aws.amazon.com/free/) from next month after July to have a chance to receive up to $200 credit to use for AWS services.

### Build an EC2 instance
{{% notice info %}}
You need to switch to the us-east-1 region when creating EC2 for the workshop to work
{{% /notice %}}
To learn how to create EC2 instances, you can refer to the lab [Introduction to Amazon EC2](https://000004.awsstudygroup.com/vi/)

### IAM User

To serve access to EC2, we need to have a User (User's Access key). You can create a User through the following method:
1. Go to the AWS [Management Console](https://aws.amazon.com/console/) page.
2. Log in as **root user**. Authenticate login if available (should set up login methods).
![Login](/images/2.prerequisite/01-Login.png)
3. Enter `IAM` in the search bar and select the option as shown.
![IAM](/images/2.prerequisite/02-IAM.png)
4. In the left sidebar, click **Users**.
5. Select **Create user**.
![Create](/images/2.prerequisite/03-Create.png)
6. Enter the User name you want to create then click **Next**.
{{% notice info %}}
Note: If IAM user does not select **Provide user access to the AWS Management Console**-> **I want to create an IAM user**, the created User will not have a password or access to the Management Console. Here we only need the User's Access Key so the account doesn't need to be able to log in. If you want the account to be able to log in, you should select as above to add a password.
{{% /notice %}}
![Create User](/images/2.prerequisite/04-UserCreate.png)
7. In the **Permissions options** section, select **Attach Policies directly**.
![Policies](/images/2.prerequisite/05-Policies.png)
8. Select the following policies in **Permissions policies**:
  - `AdministratorAccess` to have the same permissions as root account.
  - `AmazonEC2FullAccess` grants permission to create and manage EC2.
  - `AmazonDynamoDBFullAccess` grants permission to create and manage Dynamo tables.
  - `AmazonS3FullAccess` grants permission to create S3 buckets and upload documents.
  - `IAMFullAccess` creates IAM roles, policies for roles.
  - `CloudWatchLogsFullAccess` creates log groups.
  > The **CloudWatch** functionality in the workshop is still under development so it may not work well.
9. Click **Next**, review the added permissions then click **Create user**.
10. Click on the added user (may need to refresh the page).
11. Click **Security credentials**.
![Security](/images/2.prerequisite/06-CreateKey.png)
12. Find the **Access Keys** section and click the **Create access key** button.
13. At step 1, click the **CLI** option, confirm the selection then click **Next**.
14. At step 2, enter `Workshop demo` in description or leave blank, click **Create access key**.
![Create Key](/images/2.prerequisite/06-CreateKey.png)
15. At step 3, remember the **Access key** and **Secret access key** or simply select the **Download .csv file** button to download to your computer, then click done.
16. Check the Access key again.
![Check key](/images/2.prerequisite/07-CheckKey.png)
{{% notice tip %}}
You can create and use up to 2 access keys per user, remember to **turn off/deactivate** keys when not in use to prevent someone from "accidentally" using them for personal purposes and causing you to be charged.
{{% /notice %}}
### Other services used

Although AWS services in this workshop are set up automatically, you can also learn about the services used:
  - [Introduction to Amazon DynamoDB](https://aws.amazon.com/dynamodb/)
  - [Introduction to Amazon S3](https://aws.amazon.com/s3/)
  - [Introduction to CloudWatch](https://aws.amazon.com/cloudwatch/)
  
This app uses some [other technologies](https://github.com/Z3r0L0rd/license_optimize/blob/master/requirements.txt) you might want to know about.
