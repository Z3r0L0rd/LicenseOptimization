---
title : "Hướng dẫn kết nối EC2"
date: "2025-07-29" 
weight : 1
chapter : false
pre : " <b> 3.1. </b> "
---


> **Mục tiêu:** Có thể lên terminal của máy chủ EC2, clone project về máy và khởi động được app. 

1. Truy cập vào [giao diện quản trị của dịch vụ EC2](https://console.aws.amazon.com/ec2/v2/home).
  + Click chọn một máy chủ EC2 dùng để chạy app.
  {{% notice warning %}}
  **Lưu ý:** Hãy chắc rằng bạn đã có một máy chủ public trong trạng thái đang hoạt động, có file keypair.pem của máy chủ đó. Nếu không hãy tham khảo lại ở [các bước chuẩn bị](../../2-Prerequiste/)
  {{% /notice %}}
  + Hãy ghi nhớ **Public IPv4 address** của server. Mỗi khi tắt/dừng hoạt động server public IPv4 của máy chủ sẽ bị tắt và thay đổi, nên hãy nhớ kiểm tra thường xuyên.
  ![IPv4Remember](/images/3-EC2Linking/3.1/01-IPv4Remember.png)

2. Tìm kiếm file chứa key pair và chạy máy chủ trên máy tính:
  + mở terminal ở vị trí chứa file key pair.
  + Sau khi mở Terminal, hãy nhập lệnh sau `ssh -i "[tên file keypair].pem" ec2-user@[Public IPv4]`.
  ![EC2 Linking](/images/3-EC2Linking/3.1/02-EC2linking.png)
  + Bấm yes nếu bạn lần đầu tiên khởi động EC2 trên terminal để máy tính ghi nhận IP của máy chủ.
  ![EC2 Linking Success](/images/3-EC2Linking/3.1/03-EC2linking.png)
Nếu màn hình bạn xuất hiện theo ảnh trên đây vậy xin chúc mừng. Bạn đã khởi động thành công máy chủ EC2 trên máy local. Từ giờ tôi sẽ gọi cửa sổ terminal đã liên kết với EC2 là **máy chủ**.

3. Cấu hình AWS trong máy chủ:
  + Nhập lệnh `sudo yum install aws-cli -y` để cài đặt AWS CLI.
  + Nhập lệnh `aws configure` để cấu hình AWS CLI:
    - Nhập **Access key ID** và **Secret access key** đã lưu trong file .csv ở bước tạo IAM user.
    - Nhập **Default region name:** us-east-1 là khu vực mà bạn đã tạo máy chủ EC2.
    - Nhập **Default output format:** json.

{{% notice info %}}
Người dùng cần phải cấu hình AWS CLI để có thể khởi động các dịch vụ có trong app nếu không app sẽ từ chối hoạt động.
{{% /notice %}}
  ![AWS Configure](/images/3-EC2Linking/3.1/04-Configure.png)

4. Clone project và chạy app từ git hub:
  + Gõ lệnh `sudo yum install git -y` để cài đặt Git bash vào máy chủ.
  + Sau khi cài đặt xong, clone repo [**ở đây**](https://github.com/Z3r0L0rd/license_optimize) bằng lệnh `git clone https://github.com/Z3r0L0rd/license_optimize.git`

{{% notice tip %}}
Đây là nơi chứa source code của app và được cài đặt quyền **công khai** nên không cần yêu cầu tài khoản git để clone về.
{{% /notice %}}

  + Nhập lệnh `ls -li` trong máy chủ để kiểm tra sự xuất hiện của file license_optimize.
  ![License Check](/images/3-EC2Linking/3.1/05-LicenseCheck.png)
  + Di chuyển vào file bằng lệnh `cd license_optimize`, rồi sau đó dùng lại lệnh `ls -li` để xem bên trong tệp.
  ![License Check Detail](/images/3-EC2Linking/3.1/06-LicenseCheck.png)
  + Nhập lệnh `chmod +x setup.sh` và nhập lệnh `./setup.sh` để cài đặt các dependencies và khởi tạo bảng dữ liệu.
  ![Setup](/images/3-EC2Linking/3.1/07-Setup.png)
  + Sau đó nhập lệnh `streamlit run streamlit_app.py --server.port=8501 --server.address=0.0.0.0 --server.headless=true` để khởi động app trên máy chủ.
  ![Run App](/images/3-EC2Linking/3.1/08-Run.png)
  ![App Running](/images/3-EC2Linking/3.1/09-App.png)
  + Kiểm tra app thông qua đường dẫn `http://[IPv4-address]:8501` nếu bạn thấy như trên hình thì bạn đã chạy app thành công. Bạn có thể dừng app lại bằng tổ hợp phím **Ctrl + c** trên màn hình terminal.

  >**Nhắc nhở:** Các lỗi phát lỗi phát sinh trong quá trình làm vui lòng kiểm tra [**Các lỗi phát sinh**](../3.2-bugfixing/)

