# AWS VPC

## creating a VPC in AWS with 2 public and 2 private subnet.

### Step 1: Create a VPC
1. Open the AWS Management Console.
2. Navigate to VPC > Create VPC.
3. Choose VPC only and specify:
4. Name: project
5. IPv4 CIDR Block: 10.0.0.0/16
6. Leave other settings as default and click Create VPC.

<img width="535" alt="Screenshot 2025-03-22 at 2 42 01 PM" src="https://github.com/user-attachments/assets/47c0d1a5-d367-4725-9335-1d22332b4a6f" />

### Step 2: Create a Subnet

1. In the VPC Console, go to Subnets > Create Subnet.
2. Select the VPC (MyVPC).
3. Choose an Availability Zone.
4. Enter CIDR Block (e.g., 10.0.1.0/24).
5. Click Create Subnet.
<img width="295" alt="Screenshot 2025-03-23 at 11 14 10 PM" src="https://github.com/user-attachments/assets/10392973-bda8-4ec7-b207-302d45a37e95" />

   


### Step 3: Create and Attach an Internet Gateway

Go to Internet Gateways > Create Internet Gateway.
Name it MyIGW and click Create.
Select MyIGW, click Actions > Attach to VPC > Select MyVPC.
<img width="276" alt="Screenshot 2025-03-23 at 11 17 00 PM" src="https://github.com/user-attachments/assets/82e9f786-9e55-49fa-b8ed-554a62be4951" />



### Step 4: Create a Route Table and Associate It with the Subnet

Go to Route Tables > Create Route Table.
Name it MyRouteTable, select MyVPC, and click Create.
Click on the Routes tab > Edit Routes.
Add a new route:
Destination: 0.0.0.0/0
Target: Select MyIGW
Click Save Routes.
Go to Subnet Associations and associate MySubnet with MyRouteTable.

<img width="276" alt="Screenshot 2025-03-23 at 11 18 39 PM" src="https://github.com/user-attachments/assets/ab3b8b02-4d77-4b65-8f34-c6efe0b9894d" />



### Resource map of vpc & security group

<img width="1049" alt="Screenshot 2025-03-23 at 11 21 43 PM" src="https://github.com/user-attachments/assets/aec12c2c-51f3-4a0a-8ce7-653a50cead27" />


### Step 5: Launch an EC2 Instance in the VPC

Navigate to EC2 > Launch Instance.
Select Amazon Linux or Ubuntu AMI.
Choose an instance type (e.g., t2.micro).
In Networking, select:
VPC: MyVPC
Subnet: MySubnet
Auto-assign Public IP: Enable
Configure key pair and security group (allow SSH and HTTP).
Click Launch.

<img width="1135" alt="Screenshot 2025-03-23 at 11 23 01 PM" src="https://github.com/user-attachments/assets/a8ac0a50-0d90-42d9-a472-7a8bc1fd8bc8" />


### Step 6: Install Apache and Download SSL Certificate



## SSH into Your EC2 Instance:

~~~bash
ssh -i my-key.pem ec2-user@<your-instance-public-ip>
~~~

## Install Apache2
~~~bash sudo apt update && sudo apt install apache2 -y  # (For Ubuntu)
sudo systemctl start apache2
sudo systemctl enable apache2
~~~

## Download an SSL certificate
~~~bash sudo apt install certbot python3-certbot-apache -y
sudo certbot --apache
~~~

# Step 7: Create a Virtual Private Gateway (VGW) and Attach to VPC

In VPC Console, go to Virtual Private Gateways.
Click Create Virtual Private Gateway.
Name it (MyVGW) and Create.
Select MyVGW, click Actions > Attach to VPC > Select MyVPC.

# Step 8: Configure Routing for VGW

In Route Tables, go to MyRouteTable.
Add a route for on-premise/private networks (e.g., 192.168.1.0/24) pointing to MyVGW.
Click Save Routes.

Open the Public IP of Instance

<img width="1135" alt="Screenshot 2025-03-23 at 11 38 06 PM" src="https://github.com/user-attachments/assets/26ab9360-740b-4b0d-b3f7-0ffb1ccd9201" />


