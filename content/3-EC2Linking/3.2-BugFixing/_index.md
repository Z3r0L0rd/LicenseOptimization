---
title : "Troubleshooting"
date: "2025-07-29" 
weight : 2
chapter : false
pre : " <b> 3.2. </b> "
---
{{% notice warning %}}
**Note:** The errors below were discovered and compiled while working on this Hugo site. If you find errors not listed here, please contact the post author or better yet, fix the error yourself and report it to the post author =/
{{% /notice %}}
Here we will fix errors that appear while launching the app:

1. **Unable to connect to EC2 server error**:
   - Check the region carefully: This app was created and only runs on the **us-east-1** region. You can check this in the service window.
   ![RegionPicking](/images/3-EC2Linking/3.2/01-Region.png)
   - Check that the keypair.pem file is placed in the correct location and has user access permissions.
   - Ensure that the EC2 server is running and enter the **correct** public IPv4 address. Note that the public IPv4 will **change** each time the server is restarted.
   - Check the Inbound rules of the Security Group that the server is using. You can access this through **Click select server -> select Security section -> Click on Security Group (created by default when creating the server).
   ![SecurityGroup](/images/3-EC2Linking/3.2/02-SecurityGroup.png) 
   ![InboundRules](/images/3-EC2Linking/3.2/03-SecurityGroup.png)
   
   **Required** to set up 3 inbound IPv4 rules for the app to connect as shown above: 
      1. One IPv4 type **SSH**, running Port **22** can use My IP or 0.0.0.0/0 to connect to EC2 server more easily.
      2. One IPv4 type **HTTPS**, running Port **443** using IP 0.0.0.0/0.
      3. One IPv4 type **custom TCP**, running Port **8501**, using IP 0.0.0.0/0 to be able to run web app connection easily.
   {{% notice info %}}
   Note: You should only set up security groups like above in labs or demo projects because IP 0.0.0.0/0 will allow everyone to access and there is a high risk of system intrusion.
   If you want more security, use your own IP or the IP of those who have access to the server.
   {{% /notice %}}

2. **Server cannot clone GitHub project / requires account login**:
   - Try reinstalling the latest Git with the command `sudo yum install git -y` and try again.
   - If you have to log in to an account to clone, you probably didn't clone my project. Make sure you read the instructions carefully and clone from [https://github.com/Z3r0L0rd/license_optimize](https://github.com/Z3r0L0rd/license_optimize) and don't log into Git on the server because I've tried many times but still can't log in.

3. **Cannot run app on server**:
   - Not being able to run the app on the server can include many causes, but I would like to divide it into 3 main causes:
      + Setup reasons: Check the Inbound rules settings I mentioned in section 1, check AWS CLI configuration by entering complete access key and secret key information of the User and check if the key is activated, Make sure to write region **us-east-1** in the region section.
      + Wrong connection: The connection is `http://[IPv4Address]:8501` where IPv4Address is the public address of the server IPv4 and 8501 is the Port that the app will run on, and has been specified in the Security Group settings.
      + Code errors: If you have done the above steps correctly but still cannot run the app, it may be due to code errors. Check the dependency installation steps again, which will usually be automatically installed through the `setup.sh` file and run the command `streamlit run streamlit_app.py --server.port=8501 --server.address=0.0.0.0 --server.headless=true` again.

