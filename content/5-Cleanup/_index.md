+++
title = "Resource Cleanup"
date = 2021
weight = 5
chapter = false
pre = "<b>5. </b>"
+++

We will perform the following steps to delete the resources we created in this workshop.

#### Delete EC2 instance

1. Access the [EC2 service management interface](https://console.aws.amazon.com/ec2/v2/home)
  + Click **Instances**.
  + Click to select the **Public Linux Instance**. 
  + Click **Instance state**.
  + Click **Terminate instance**, then click **Terminate** to confirm.
  
![Clean](/images/5.Cleanup/01-Clean.png)

2. Click **Users**.
  + Click to select the user you created.
  + Click **Delete**, then enter the user name and click **Delete** to delete the user.

#### Delete S3 bucket

1. Access the [S3 service management interface](https://s3.console.aws.amazon.com/s3/home)
  + Click to select the S3 bucket we created for the workshop. (Example: license-optimization-storage)
  + Click **Empty**.
  + Enter **permanently delete**, then click **Empty** to delete objects in the bucket.
  + Click **Exit**.

2. After deleting all objects in the bucket, click **Delete**

![Clean](/images/5.Cleanup/02-Clean.png)

3. Enter the S3 bucket name, then click **Delete bucket** to delete the S3 bucket.

![Clean](/images/5.Cleanup/03-Clean.png)

#### Delete DynamoDB

1. Access the [DynamoDB service management interface](https://us-east-1.console.aws.amazon.com/dynamodbv2/home)
  + Click **Tables**.
  + Click to select the Table we created
  + Click **Delete**.
![Clean](/images/5.Cleanup/04-Clean.png)

  + Enter **Confirm** and click the **Delete** button to confirm deletion.

![Clean](/images/5.Cleanup/05-Clean.png)