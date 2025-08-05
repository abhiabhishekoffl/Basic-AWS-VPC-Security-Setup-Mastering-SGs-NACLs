#📘 Project Title: Basic-AWS-VPC-Security-Setup-Mastering-SGs-NACLs
Secure AWS networking setup with VPC, public/private subnets, EC2 with Apache, Security Groups, and NACLs. Ideal for beginners exploring AWS infrastructure and security best practices. Includes a clean architecture diagram.

Description:
This project demonstrates how to build a secure and scalable Virtual Private Cloud (VPC) environment on AWS using best practices for network segmentation and layered security.

Key components include:
- VPC with public/private subnets
- Internet Gateway and Route Tables
- EC2 instance with Apache Web Server
- Elastic IP for public access
- Security Groups (SG) for instance-level protection
- Network ACLs (NACLs) for subnet-level traffic control

📊 A custom architecture diagram is included for visual reference.
This setup is ideal for beginners looking to understand the core networking and security features of AWS.

# 📍 Architecture Summary
Component	Details
VPC CIDR	10.0.0.0/16
Public Subnet	10.0.1.0/24
Private Subnet	10.0.2.0/24
EC2	Public subnet + Elastic IP
Apache Server	Installed on EC2 (port 80 open)
IGW	Connected to Public subnet
Route Table	Routes 0.0.0.0/0 to IGW
SG	Allows ports 22 (SSH), 80 (HTTP)
NACL	Granular traffic control rules
