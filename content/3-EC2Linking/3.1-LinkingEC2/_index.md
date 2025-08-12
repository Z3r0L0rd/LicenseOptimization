---
title : "EC2 Connection Guide"
date: "2025-07-29" 
weight : 1
chapter : false
pre : " <b> 3.1. </b> "
---


> **Objective:** Access EC2 server terminal, clone project to the server and launch the app. 

1. Access the [EC2 service management console](https://console.aws.amazon.com/ec2/v2/home).
  + Click to select an EC2 instance to run the app.
  {{% notice warning %}}
  **Note:** Make sure you have a public instance in running state with the keypair.pem file for that instance. If not, please refer to [preparation steps](../../2-prerequiste/)
  {{% /notice %}}
  + Remember the **Public IPv4 address** of the server. Each time you stop/start the server, the public IPv4 will be turned off and changed, so remember to check regularly.
  ![IPv4Remember](/images/3-EC2Linking/3.1/01-IPv4Remember.png)

2. Find the key pair file and connect to the server from your computer:
  + Open terminal at the location containing the key pair file.
  + After opening Terminal, enter the following command `ssh -i "[keypair filename].pem" ec2-user@[Public IPv4]`.
  ![EC2 Linking](/images/3-EC2Linking/3.1/02-EC2linking.png)
  + Press yes if this is your first time connecting to EC2 via terminal so the computer can recognize the server IP.
  ![EC2 Linking Success](/images/3-EC2Linking/3.1/03-EC2linking.png)
If your screen appears as shown above, congratulations. You have successfully connected to the EC2 server from your local machine. From now on, I will refer to the terminal window connected to EC2 as the **server**.

3. Configure AWS on the server:
  + Enter the command `sudo yum install aws-cli -y` to install AWS CLI.
  + Enter the command `aws configure` to configure AWS CLI:
    - Enter **Access key ID** and **Secret access key** saved in the .csv file from the IAM user creation step.
    - Enter **Default region name:** us-east-1 which is the region where you created the EC2 instance.
    - Enter **Default output format:** json.

{{% notice info %}}
Users must configure AWS CLI to be able to launch the services in the app, otherwise the app will refuse to operate.
{{% /notice %}}
  ![AWS Configure](/images/3-EC2Linking/3.1/04-Configure.png)

4. Clone project and run app from GitHub:
  + Type the command `sudo yum install git -y` to install Git bash on the server.
  + After installation is complete, clone the repo [**here**](https://github.com/Z3r0L0rd/license_optimize) using the command `git clone https://github.com/Z3r0L0rd/license_optimize.git`

{{% notice tip %}}
This is where the app source code is stored and is set to **public** permissions, so no git account is required to clone.
{{% /notice %}}

  + Enter the command `ls -li` on the server to check for the appearance of the license_optimize file.
  ![License Check](/images/3-EC2Linking/3.1/05-LicenseCheck.png)
  + Navigate into the file using the command `cd license_optimize`, then use the command `ls -li` again to see inside the directory.
  ![License Check Detail](/images/3-EC2Linking/3.1/06-LicenseCheck.png)
  + Enter the command `chmod +x setup.sh` and enter the command `./setup.sh` to install dependencies and initialize the database.
  ![Setup](/images/3-EC2Linking/3.1/07-Setup.png)
  + Then enter the command `streamlit run streamlit_app.py --server.port=8501 --server.address=0.0.0.0 --server.headless=true` to launch the app on the server.
  ![Run App](/images/3-EC2Linking/3.1/08-Run.png)
  ![App Running](/images/3-EC2Linking/3.1/09-App.png)
  + Check the app through the URL `http://[IPv4-address]:8501` if you see as shown above, you have successfully run the app. You can stop the app using the key combination **Ctrl + c** on the terminal screen.

  >**Reminder:** For errors that occur during the process, please check [**Troubleshooting**](../3.2-bugfixing/)

