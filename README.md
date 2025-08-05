#  📘 Project Title: Basic-AWS-VPC-Security-Setup-Mastering-SGs-NACLs

Secure AWS networking setup with VPC, public/private subnets, EC2 with Apache, Security Groups, and NACLs. Ideal for beginners exploring AWS infrastructure and security best practices. Includes a clean architecture diagram.

#  Description:
This project demonstrates how to build a secure and scalable Virtual Private Cloud (VPC) environment on AWS using best practices for network segmentation and layered security.

#  Key components include:
- VPC with public/private subnets
- Internet Gateway and Route Tables
- EC2 instance with Apache Web Server
- Elastic IP for public access
- Security Groups (SG) for instance-level protection
- Network ACLs (NACLs) for subnet-level traffic control

# 📍 Architecture Summary
| Component      | Details                          |
| -------------- | -------------------------------- |
| VPC CIDR       | 10.0.0.0/16                      |
| Public Subnet  | 10.0.1.0/24                      |
| Private Subnet | 10.0.2.0/24                      |
| EC2            | Public subnet + Elastic IP       |
| Apache Server  | Installed on EC2 (port 80 open)  |
| IGW            | Connected to Public subnet       |
| Route Table    | Routes 0.0.0.0/0 to IGW          |
| SG             | Allows ports 22 (SSH), 80 (HTTP) |
| NACL           | Granular traffic control rules   |

# 🛠️ Steps to Deploy via AWS Console

# ✅ Step 1: Create a VPC

* Go to **VPC Dashboard** → "Create VPC"
* Choose: IPv4 CIDR = `10.0.0.0/16`
* Name it: `Basic-Security-VPC`


# ✅ Step 2: Create Subnets

* Public Subnet: `10.0.1.0/24` (Name: `Public-Subnet`)
* Private Subnet: `10.0.2.0/24` (Name: `Private-Subnet`)

---

# ✅ Step 3: Attach Internet Gateway (IGW)

* Create IGW → Attach to VPC
* Create a **Route Table** with `0.0.0.0/0 → IGW`
* Associate it with the **Public Subnet**

#### ✅ Step 4: **Launch EC2 Instance**

* Place in **Public Subnet**
* Select **Amazon Linux 2 AMI**
* Use **t2.micro (Free Tier)**
* Assign **Elastic IP** (EIP) and associate it
* Install Apache:

  ```bash
  sudo yum update -y
  sudo yum install httpd -y
  sudo systemctl start httpd
  sudo systemctl enable httpd
  ```

---

#### ✅ Step 5: **Create Security Group**

* Allow **inbound**:

  * Port 22 (SSH) – from your IP
  * Port 80 (HTTP) – from all
* Allow **outbound**: All traffic

---

#### ✅ Step 6: **Configure Network ACLs**

* For **Public Subnet NACL**:

  * Inbound: Allow 22, 80, 443, 1024–65535
  * Outbound: Allow same ports
* For **Private Subnet NACL**:

  * Only allow internal port like **3306** (MySQL)

---

### 🔐 **Security Layered Concept**

| Level          | Tool           | Purpose                             |
| -------------- | -------------- | ----------------------------------- |
| Subnet-level   | NACL           | Stateless, broader traffic control  |
| Instance-level | Security Group | Stateful, fine-grained access rules |

---

### 🌐 **Architecture Diagram**

Attach the image you received earlier here in your GitHub 
