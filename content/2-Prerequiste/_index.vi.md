---
title : "Các bước chuẩn bị"
date: "2025-07-29" 
weight : 2 
chapter : false
pre : " <b> 2. </b> "
---
### Tài khoản AWS 
Để thực hiện workshop này, bạn cần có tài khoản AWS để có thể truy cập vào AWS Management Console. Nếu bạn chưa có tài khoản, hãy đăng ký tại [AWS](https://aws.amazon.com/). Bạn có thể sẽ cần thêm thẻ thanh toán quốc tế (Mastercard/Visa), nhưng bạn có thể truy cập và bắt đầu sử dụng các dịch vụ của AWS.

Bạn hãy bắt đầu đăng kí ngay hôm nay [tại đây](https://aws.amazon.com/free/) từ tháng sau tháng 7 để có cơ hội nhận đến 200$ credit để sử dụng cho các dịch vụ AWS.

### Xây dựng một EC2 instance
{{% notice info %}}
Bạn cần tạo chỉnh sang miền us-east-1 khi tạo EC2 để workshop có thể hoạt động
{{% /notice %}}
Để tìm hiểu cách tạo các EC2 instance các bạn có thể tham khảo bài lab [Giới thiệu về Amazon EC2](https://000004.awsstudygroup.com/vi/)

### IAM User

Nhằm phục vụ việc truy cập vào EC2 ta cần phải có một có một User(Access key của User). Có thể tạo User thông qua cách sau:
1. Vào trang [Management Console](https://aws.amazon.com/console/) của AWS.
2. Đăng nhập với vai trò là **root user**. Xác thực đăng nhập nếu có(nên thiết lập các phương pháp đăng nhập).
![Login](/images/2.prerequisite/01-Login.png)
3. Nhập vào `IAM` trên thanh tìm kiếm và chọn lựa chọn theo hình.
![IAM](/images/2.prerequisite/02-IAM.png)
4. Ở thanh bên trái, bấm vào **Users**.
5. Chọn **Create user**.
![Create](/images/2.prerequisite/03-Create.png)
6. Nhập tên User muốn tạo rồi bấm **Next**.
{{% notice info %}}
Lưu ý: IAM user nếu không chọn **Provide user access to the AWS Management Console**-> **I want to create an IAM user** thì User được tạo ra sẽ không có mật khẩu lẫn quyền truy cập Management Console. Ở đây ta chỉ cần Access Key của User nên không cần tài khoản phải đăng nhập được, nếu các bạn muốn tài khoản có thể đăng nhập thì nên chọn như trên để có thể thêm mật khẩu.
{{% /notice %}}
![Create User](/images/2.prerequisite/04-UserCreate.png)
7. Ở mục **Permissions options**, chọn **Attach Policies directly**.
![Policies](/images/2.prerequisite/05-Policies.png)
8. Lần lượt chọn các policies trong **Permissions policies** sau:
  - `AdministratorAccess` để có các quyền giống root account.
  - `AmazonEC2FullAccess` cấp phép quyền tạo và quản lý EC2.
  - `AmazonDynamoDBFullAccess` cấp phép quyền tạo và quản lý các bảng Dynamo.
  - `AmazonS3FullAccess` cấp quyền tạo S3 bucket và đăng tải tài liệu.
  - `IAMFullAccess` tạo IAM role,policies cho roles.
  - `CloudWatchLogsFullAccess` tạo log groups.
  > Chức năng sử dụng **CloudWatch** trong workshop vẫn đang trong quá trình phát triển nên có thể không hoạt động tốt.
9. Bấm **Next**, kiểm tra lại các permissions đã thêm rồi Nhấn vào **Create user**.
10. Ta vào nhấp vào user đã thêm (có thể cần phải refresh lại page).
11. Nhấp vào **Security credentials**.
![Security](/images/2.prerequisite/06-CreateKey.png)
12. Tìm mục **Access Keys** và nhấn vào nút **Create access key**.
13. Tại bước 1, nhấn vào lựa chọn **CLI**, xác nhận lựa chọn rồi bấm **Next**.
14. Tại bước 2, nhập `Workshop demo` vào description hoặc không cần nhập, bấm **Create access key**.
![Create Key](/images/2.prerequisite/06-CreateKey.png)
15. Ở bước 3, hãy ghi nhớ **Access key** và **Secret access key** hoặc đơn giản hơn là chọn nút **Download .csv file** để tải về máy, sau đó bấm done.
16. Kiểm tra lại Access key.
![Check key](/images/2.prerequisite/07-CheckKey.png)
{{% notice tip %}}
Bạn có thể tạo và sử dụng tối đa 2 access key cho mỗi user, hãy nhớ **tắt/deactivated** key khi không sử dụng đề phòng ai đó "vô tình" sử dụng cho mục đích riêng và khiến các bạn bị tính phí.
{{% /notice %}}
### Các dịch vụ các đã dùng khác

Workshop này mặc dù các dịch vụ AWS đã được thiết lập tự động nhưng mà các bạn cũng có thể tìm hiểu qua các dịch vụ đã được sử dụng:
  - [Giới thiệu về Amazon DynamoDB](https://aws.amazon.com/dynamodb/)
  - [Giới thiệu về Amazon S3](https://aws.amazon.com/s3/)
  - [Giới thiệu về CloudWatch](https://aws.amazon.com/cloudwatch/)
  
 App này có sử dụng một số [công nghệ khác](https://github.com/Z3r0L0rd/license_optimize/blob/master/requirements.txt) các bạn có thể muốn biết.  


  
