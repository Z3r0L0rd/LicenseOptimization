---
title : "Quản lí Licenses"
date: "2025-07-29" 
weight : 2
chapter : false
pre : " <b> 4.2. </b> "
---
**Quản lí Licenses** bao gồm các chức năng CRUD (Create-Read-Update-Delete) các license, cập nhật các license theo thời gian thực lên dịch vụ DynamoBD của AWS

![View License](/images/4.Function/421-License.png)
Bạn có thể thêm mới license vào và hệ thống sẽ tự động cập nhật dữ liệu lên Cloud. Trang web hỗ trợ 3 loại đăng kí: SUBCRIPTION(đăng kí), PERPETUAL(mua 1 lần) và CONCURRENT(sử dụng đồng thời)
{{% notice tip %}}
Các bạn có thể không điền ngày hết hạn thì app sẽ hiểu là license có hiệu lực vô thời hạn
{{% /notice %}}
![Add License](/images/4.Function/422-License.png)
Các bạn chỉ có thể cập nhật số license đang sử dụng.
![Update License](/images/4.Function/423-License.png)
![Delete License](/images/4.Function/424-License.png)