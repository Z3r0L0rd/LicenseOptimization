---
title : "Các lỗi phát sinh"
date: "2025-07-29" 
weight : 2
chapter : false
pre : " <b> 3.2. </b> "
---
{{% notice warning %}}
**Lưu ý:** Những lỗi dưới đây được tôi phát hiện và tổng hợp trong lúc đang làm hugo này. Nếu các bạn phát hiện lỗi của mình không nằm trong đây vui lòng liên hệ chủ post hoặc tốt hơn là tự sửa lỗi và báo cáo lên cho chủ post =/
{{% /notice %}}
Ở đây chúng ta sẽ thực hiện chỉnh sửa các lỗi xuất hiện trong lúc đang khởi động app:

1. **Lỗi không thể kết nối đến máy chủ EC2**:
   - Kiểm tra kĩ region: Bài app này được tạo và chỉ chạy trên region **us-east-1**. Bạn có thể kiểm tra trên cửa sổ của dịch vụ.
   ![RegionPicking](/images/3-EC2Linking/3.2/01-Region.png)
   - Kiểm tra lại file keypair.pem đã được đặt đúng vị trí và có quyền truy cập của User.
   - Đảm bảo rằng máy chủ EC2 đang hoạt động và nhập **đúng** public IPv4 address. Lưu ý rằng public IPv4 sẽ **thay đổi** mỗi lần khởi động lại máy chủ.
   - Kiểm tra các Inbound rules của Security Group mà máy chủ đang sử dụng. Có thể truy cập vào thông qua **Click chọn máy chủ -> chọn mục Security -> Click vào Security Group (mặc định được tạo ra khi tạo máy chủ).
   ![SecurityGroup](/images/3-EC2Linking/3.2/02-SecurityGroup.png) 
   ![InboundRules](/images/3-EC2Linking/3.2/03-SecurityGroup.png)
   
   **Bắt buộc** phải thiết lập 3 inbound IPv4 để app có thể liên kết như trên hình: 
      1. Một IPv4 loại **SSH**,  chạy Port **22** có thể sử dụng My IP hoặc 0.0.0.0/0 để liên kết lên máy chủ EC2 dễ dàng hơn.
      2. Một IPv4 loại **HTTPS** , chạy Port **443** dùng IP 0.0.0.0/0.
      3. Một IPv4 loại **custom TCP**, chạy Port **8501**, dùng IP 0.0.0.0/0 để có thể chạy liên kết web app dễ dàng.
   {{% notice info %}}
   Lưu ý: Chỉ nên thiết lập security group như trên trong các bài lab hoặc các project mang tính demo vì IP 0.0.0.0/0 sẽ cho tất cả mọi người tiếp cận và nguy cơ cao hệ thống bị xâm nhập.
   Nếu bạn muốn bảo mật hơn hãy sử dụng IP của mình hoặc IP của những người có quyền truy cập vào máy chủ.
   {{% /notice %}}

2. **Máy chủ không thể Clone project github/ yêu cầu nhập tài khoản**:
   - Hãy thử cài đặt lại Git mới nhất bằng lệnh `sudo yum install git -y` và thử lại.
   - Nếu bạn phải đăng nhập tài khoản để có thể clone về thì chắc đã không clone project của tôi về. Hãy chắc chắn bạn đã đọc kĩ hướng dẫn và clone về từ [https://github.com/Z3r0L0rd/license_optimize](https://github.com/Z3r0L0rd/license_optimize) và đừng đăng nhập Git bằng máy chủ vì tôi đã thử rất nhiều lần nhưng vẫn không thể đăng nhập được.

3. **Không chạy được app trên máy chủ**:
   - Không chạy được app trên máy chủ có thể bao gồm nhiều nguyên nhân nhưng tôi xin phép chia ra làm 3 nguyên nhân chính:
      + Lý do vê thiết lập: Hãy kiểm tra các thiết lập về Inbound rules tôi đã đề cập ở mục 1, kiểm tra cấu hình AWS CLI bằng cách nhập đầy đủ thông tin access key lẫn secret key của User và kiểm tra xem có đang kích hoạt key không, Đảm bảo ghi region **us-east-1** ở mục region.
      + Sai liên kết: Liên kết là `http://[IPv4Adress]:8501` với IPv4Address là địa chỉ public của IPv4 máy chủ và 8501 chính là Port mà app sẽ chạy, và đã tuyên chỉ định trong thiết lập Security Group.
      + Lỗi về code: Nếu bạn đã làm đúng các bước trên mà vẫn không chạy được app thì có thể do lỗi code. Hãy kiểm tra lại các bước cài đặt dependencies thường sẽ tự động cài sẵn thông qua file `setup.sh` và chạy lại lệnh `streamlit run streamlit_app.py --server.port=8501 --server.address=0.0.0.0 --server.headless=true`.



