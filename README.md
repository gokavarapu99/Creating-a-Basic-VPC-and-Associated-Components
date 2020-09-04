# Creating-a-Basic-VPC-and-Associated-Components
Create a VPC 
Create a Public and Private Subnet in Different Availability Zones 
Create a VPC from scratch (without using the VPC Wizard).
Set the VPC CIDR to 172.16.0.0/16.
Create Two Network Access Control Lists (NACLs), and Associate Each with the Proper Subnet Create an Internet Gateway, and Connect It to the VPC 
Create a public and private subnet in different Availability Zones using the following IP CIDR addresses:
Public1 subnet in us-east-1a: 172.16.1.0/24
Private1 subnet in us-east-1b: 172.16.2.0/24
Create Two Route Tables, and Associate Them with the Correct Subnet
Create a public NACL with inbound rules allowing HTTP and SSH traffic, as well as an outbound rule allowing traffic on port range 1024-65535.
Associate the public NACL with the public subnet.
Create a private NACL with an inbound rule allowing SSH traffic with a source of 172.16.1.0/24, as well as an outbound rule allowing traffic on port range 1024-65535.
Associate the private NACL with the private subnet.
Create an Internet Gateway, and Connect It to the VPC
Create Two Route Tables, and Associate Them with the Correct Subnet
Create two route tables:
One for the public subnet with an internet gateway route
One for the private subnet without an internet gateway route
For the public route table, create a default route to the internet using the 0.0.0.0/0 CIDR notation.
# Steps for the Hands On Lab.

Creating a Basic VPC and Associated Components
Introduction
In this hands-on lab, we will create a VPC with an internet gateway, as well as create subnets across multiple Availability Zones.

Solution
Log in to the live AWS environment using the credentials provided. Make sure you're in the N. Virginia (us-east-1) region throughout the lab.

Note: The steps below follow a slightly different order than the steps in the lab videos, but it should not affect the successful outcome of the lab.

Create a VPC
Navigate to the VPC dashboard.
Click Your VPCs in the left-hand menu.
Click Create VPC, and set the following values:
Name tag: VPC1
IPv4 CIDR block: 172.16.0.0/16
Leave the IPv6 CIDR block and Tenancy fields as their default values.
Click Create.
Create a Public and Private Subnet in Different Availability Zones
Create Public Subnet
Click Subnets in the left-hand menu.
Click Create subnet, and set the following values:
Name tag: Public1
VPC: VPC1
Availability Zone: us-east-1a
IPv4 CIDR block: 172.16.1.0/24
Click Create.
Create Private Subnet
Click Create subnet, and set the following values:
Name tag: Private1
VPC: VPC1
Availability Zone: us-east-1b
IPv4 CIDR block: 172.16.2.0/24
Click Create.
Create Two Network Access Control Lists (NACLs), and Associate Each With the Proper Subnet
Create and Configure Public NACL
Click Network ACLs in the left-hand menu.
Click Create network ACL, and set the following values:
Name tag: Public_NACL
VPC: VPC1
Click Create.
With Public_NACL selected, click the Inbound Rules tab below.
Click Edit inbound rules.
Click Add Rule, and set the following values:
Rule #: 100
Type: HTTP (80)
Port Range: 80
Source: 0.0.0.0/0
Allow / Deny: ALLOW
Click Add Rule, and set the following values:
Rule #: 110
Type: SSH (22)
Port Range: 22
Source: 0.0.0.0/0
Allow / Deny: ALLOW
Click Save.
Click the Outbound Rules tab.
Click Edit outbound rules.
Click Add Rule, and set the following values:
Rule #: 100
Type: Custom TCP Rule
Port Range: 1024-65535
Destination: 0.0.0.0/0
Allow / Deny: ALLOW
Click Save.
Click the Subnet associations tab.
Click Edit subnet associations.
Select the Public1 subnet, and click Edit.
Create and Configure Private NACL
Click Create network ACL, and set the following values:
Name tag: Private_NACL
VPC: VPC1
Click Create.
With Private_NACL selected, click the Inbound Rules tab below.
Click Edit inbound rules.
Click Add Rule, and set the following values:
Rule #: 100
Type: SSH (22)
Port Range: 22
Source: 172.16.1.0/24
Allow / Deny: ALLOW
Click Save.
Click the Outbound Rules tab.
Click Edit outbound rules.
Click Add Rule, and set the following values:
Rule #: 100
Type: Custom TCP Rule
Port Range: 1024-65535
Destination: 0.0.0.0/0
Allow / Deny: ALLOW
Click Save.
Click the Subnet associations tab.
Click Edit subnet associations.
Select the Private1 subnet, and click Edit.
Create an Internet Gateway, and Connect It to the VPC
Click Internet Gateways in the left-hand menu.
Click Create internet gateway.
Give it a Name tag of "IGW".
Click Create.
Once it's created, click Actions > Attach to VPC.
In the dropdown, select our VPC1.
Click Attach.
Create Two Route Tables, and Associate Them with the Correct Subnet
Create and Configure Public Route Table
Click Route Tables in the left-hand menu.
Click Create route table, and set the following values:
Name tag: PublicRT
VPC: VPC1
Click Create.
With PublicRT selected, click the Routes tab on the page.
Click Edit routes.
Click Add route, and set the following values:
Destination: 0.0.0.0/0
Target: Internet Gateway > IGW
Click Save routes.
Click the Subnet Associations tab.
Click Edit subnet associations.
Select our Public1 subnet.
Click Save.
Create and Configure Private Route Table
Click Route Tables in the left-hand menu.
Click Create route table, and set the following values:
Name tag: PrivateRT
VPC: VPC1
Click Create.
With PrivateRT selected, click the Subnet Associations tab.
Click Edit subnet associations.
Select our Private1 subnet.
Click Save.
