---
title : "License Management"
date: "2025-07-29" 
weight : 2
chapter : false
pre : " <b> 4.2. </b> "
---
**License Management** includes CRUD (Create-Read-Update-Delete) functions for licenses, updating licenses in real-time to AWS DynamoDB service.

![View License](/images/4.Function/421-License.png)
You can add new licenses and the system will automatically update data to the Cloud. The website supports 3 types of registration: SUBSCRIPTION, PERPETUAL (one-time purchase) and CONCURRENT (simultaneous use).
{{% notice tip %}}
You can leave the expiration date blank and the app will understand that the license is valid indefinitely.
{{% /notice %}}
![Add License](/images/4.Function/422-License.png)
You can only update the number of licenses currently in use.
![Update License](/images/4.Function/423-License.png)
![Delete License](/images/4.Function/424-License.png)