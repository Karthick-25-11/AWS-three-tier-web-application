# AWS Three-Tier Architecture Deployment (Restart Project)

## 📌 Project Overview

In this project, I designed and deployed a **highly available Three-Tier Architecture on AWS** using core AWS services. The architecture clearly separates the **presentation (web)**, **application**, and **database** layers inside a secure Virtual Private Cloud (VPC).

I completed this project as part of a hands-on AWS infrastructure assignment, where the main focus was on **networking, security, high availability, and controlled access using a Bastion Host**.

---

## 🏗️ Architecture Overview

I followed AWS best practices while designing the architecture:

* **Public Subnet** hosting the Bastion Host and Web Server
* **Private Subnets** hosting the Application Server and Database
* **NAT Gateway** to allow outbound internet access for private resources
* **Internet Gateway** to enable public access where required
* **Multi–Availability Zone deployment** to improve fault tolerance and availability

---

## 🧱 AWS Services Used

* Amazon VPC
* Amazon EC2 (Amazon Linux 2)
* Internet Gateway
* NAT Gateway
* Elastic IP
* Route Tables
* Security Groups
* Amazon RDS (MariaDB)

---

## 🌐 Network Design

I created a custom VPC with the following setup:

* **4 Subnets**

  * 1 Public Subnet
  * 3 Private Subnets
* Subnets distributed across **two Availability Zones** to ensure high availability

### Routing Configuration

* Public Subnet traffic routed through the **Internet Gateway**
* Private Subnet traffic routed through the **NAT Gateway**

---

## 🔐 Security Architecture

To enforce least-privilege access, I created and linked multiple **Security Groups**:

* **Bastion Host Security Group**

  * Allows SSH access from trusted sources only
* **Web Server Security Group**

  * Allows HTTP (Port 80) access from the internet
* **Application Server Security Group**

  * Allows traffic only from the Web Server security group
* **Database Security Group**

  * Allows database access only from the Application Server security group

This design ensures that **no direct public access** is possible to the application or database layers.

---

## 💻 EC2 Instances Configuration

### Bastion Host

* Amazon Linux 2
* Instance Type: t3.micro
* Deployed in the public subnet
* Used as the single secure entry point to access private instances

### Web Server

* Amazon Linux 2
* Deployed in the public subnet and accessible via HTTP


### Application Server

* Amazon Linux 2
* MariaDB client installed
* Deployed in a private subnet
* Accessible only through the Bastion Host

---

## 🗄️ Database Layer

* Amazon RDS using MariaDB
* Free Tier eligible configuration
* Deployed in a private subnet group
* Public access disabled
* Database access restricted to the Application Server only

---

## 🔑 Secure Access Flow

I validated secure access using the following flow:

1. Connected to the **Bastion Host** via SSH
2. From the Bastion Host, accessed the **Application Server** using its private IP
3. From the Application Server:

   * Pinged the Web Server using its private IP
   * Connected to the RDS database
   * Verified database connectivity and availability

This confirmed correct **routing**, **security group rules**, and **tier isolation**.

---

## ✅ Project Validation

* ✔ Successfully accessed Bastion Host via SSH
* ✔ Confirmed private instances are not reachable from the internet
* ✔ Verified Web Server accessibility through public IP
* ✔ Confirmed Application Server communication with Database
* ✔ Ensured NAT Gateway enabled outbound access for private instances

---

## 🚧 Challenges Faced

* Designing and linking multiple security groups correctly
* Understanding the difference between Internet Gateway and NAT Gateway
* Troubleshooting SSH access through the Bastion Host
* Correctly associating route tables with subnets

---

## 📈 Key Learnings

* Hands-on experience implementing a real-world AWS Three-Tier Architecture
* Strong understanding of VPC networking and subnet design
* Practical knowledge of Bastion Host–based secure access
* Improved troubleshooting and AWS resource management skills

---

## 🏁 Conclusion

Through this project, I gained practical experience building a **production-style AWS infrastructure** with a strong focus on **security, scalability, and availability**.

---


