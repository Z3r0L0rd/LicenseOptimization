+++
title = "Dọn dẹp tài nguyên  "
date = 2021
weight = 5
chapter = false
pre = "<b>5. </b>"
+++

Chúng ta sẽ tiến hành các bước sau để xóa các tài nguyên chúng ta đã tạo trong bài thực hành này.

#### Xóa EC2 instance

1. Truy cập [giao diện quản trị dịch vụ EC2](https://console.aws.amazon.com/ec2/v2/home)
  + Click **Instances**.
  + Click chọn instance **Public Linux Instance**. 
  + Click **Instance state**.
  + Click **Terminate instance**, sau đó click **Terminate** để xác nhận.
  
![Clean](/images/5.Cleanup/01-Clean.png)

2. Click **Users**.
  + Click chọn user mà bạn đã tạo.
  + Click **Delete**, sau đó điền tên user và click **Delete** để xóa user.

#### Xóa S3 bucket

1. Truy cập [giao diện quản trị dịch vụ S3](https://s3.console.aws.amazon.com/s3/home)
  + Click chọn S3 bucket chúng ta đã tạo cho bài thực hành. ( Ví dụ : license-optimization-storage )
  + Click **Empty**.
  + Điền **permanently delete**, sau đó click **Empty** để tiến hành xóa object trong bucket.
  + Click **Exit**.

2. Sau khi xóa hết object trong bucket, click **Delete**

![Clean](/images/5.Cleanup/02-Clean.png)

3. Điền tên S3 bucket, sau đó click **Delete bucket** để tiến hành xóa S3 bucket.

![Clean](/images/5.Cleanup/03-Clean.png)

#### Xóa DynamoDB

1. Truy cập vào [giao diện quản trị dịch vụ DynamoDB](https://us-east-1.console.aws.amazon.com/dynamodbv2/home)
  + Click **Tables**.
  + Click chọn Table chúng ta đã tạo
  + Click **Delete**.
![Clean](/images/5.Cleanup/04-Clean.png)

  + Nhập **Confirm** và nhấn nut **Delete** để xác nhận xóa.

![Clean](/images/5.Cleanup/05-Clean.png)
