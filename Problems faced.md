### 1. Understanding the Traffic Flow Between Services

At the beginning of the project, I struggled to clearly understand how user requests move between Route 53, CloudFront, the Load Balancer, and the EC2 instances. This made it difficult to design the architecture correctly.

**How I solved it:**
I broke down the request flow step by step and mapped each service’s role separately. I also referred to AWS documentation and sample architectures to validate the flow. Creating the architecture diagram helped me visualize and confirm the correct traffic path.

---

### 2. Designing Secure Communication Between Tiers

Defining proper Security Group rules for each tier was challenging, especially ensuring that only required traffic was allowed between the web, application, and database layers.

**How I solved it:**
I followed the principle of least privilege and designed Security Groups so that each tier only accepts traffic from the immediate upper tier. I avoided opening any public access to the database layer and tested the rules logically before finalizing them.

---

### 3. Implementing High Availability Across Availability Zones

Initially, I was unsure how Auto Scaling Groups and Multi-AZ deployments work together to provide high availability.

**How I solved it:**
I studied how Auto Scaling Groups distribute EC2 instances across multiple Availability Zones and how Amazon RDS Multi-AZ provides automatic failover. I then updated the architecture to explicitly show two Availability Zones for both the application and database tiers.

---

### 4. Balancing Cost with Reliability

While designing the architecture, I found it difficult to decide which services and configurations would provide reliability without increasing cost unnecessarily.

**How I solved it:**
I focused on using managed AWS services like RDS and Auto Scaling to reduce operational overhead. I also included cost-saving strategies such as right-sizing EC2 instances, CloudFront caching, and S3 Intelligent-Tiering.

---

