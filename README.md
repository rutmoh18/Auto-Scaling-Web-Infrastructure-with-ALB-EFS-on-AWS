🚀 Auto-Scaling-Web-Infrastructure-with-ALB-EFS-on-AWS

📌 Project Overview

This project demonstrates the design and implementation of a highly available, scalable, and secure web application infrastructure on AWS.

The architecture is built to handle real-world challenges such as:

Variable traffic loads

High availability across multiple Availability Zones

Secure communication between services

Persistent shared storage

The system ensures automatic scaling, load balancing, and fault tolerance using AWS managed services.



🎯 Objectives

Achieve High Availability using Multi-AZ deployment

Implement Scalability using Auto Scaling

Ensure Security using Security Groups

Maintain Data Persistence using EFS

Provide Fault Tolerance with Load Balancer



🏗️ Architecture
User → Application Load Balancer → Target Groups → Auto Scaling Group → EC2 Instances → EFS
⚙️ AWS Services Used

Amazon EC2 → Compute (Web Server)

Amazon EFS → Shared Storage

Elastic Load Balancing → Traffic Distribution

AWS Auto Scaling → Dynamic Scaling

VPC → Network Isolation



🧱 Implementation Steps
🔹 1. VPC Setup

Created custom VPC (192.168.0.0/24)

Configured public and private subnets across multiple AZs

Attached Internet Gateway

Created NAT Gateway for private subnet access

🔹 2. EC2 Web Server Setup

Launched EC2 instance in public subnet

Installed Apache web server

Configured and tested web server

🔹 3. EFS Setup and Mount

Created EFS file system

Configured mount targets

Mounted EFS on EC2 at /var/www/html

Enabled persistent mount using /etc/fstab

🔹 4. Web Application Deployment

Created index.html inside EFS

Hosted custom web application

🔹 5. AMI Creation

Created AMI from configured EC2 instance

Used as a golden image

🔹 6. Launch Template

Created launch template using AMI

Configured instance type and security group

🔹 7. Target Groups

Web-App → Port 80

Test-App → Port 8080

🔹 8. Application Load Balancer (ALB)

Created internet-facing ALB

Configured listeners:

Port 80 → Web-App

Port 8080 → Test-App

🔹 9. Auto Scaling Group (ASG)

Used launch template

Configured:

Desired: 2

Min: 0

Max: 5

Attached target groups

🔹 10. Security Configuration

ALB-SG → Public access

Web-Server-SG → Allow only ALB

EFS-SG → Allow only EC2



🧪 Testing and Validation

Verified EC2 web server functionality

Validated EFS mount and persistence

Tested Auto Scaling (instance creation/replacement)

Checked Target Group health status

Verified Load Balancer routing

Tested application on:

Port 80 (Main App)

Port 8080 (Test App)

Simulated failure and confirmed automatic recovery



📊 Performance and Optimization

Load distributed across multiple instances

Reduced response time under load

Auto Scaling ensured efficient resource usage

EFS provided consistent shared storage

Security optimized using layered access control



🔐 Security Architecture
User → ALB → EC2 → EFS

ALB accepts public traffic

EC2 accepts traffic only from ALB

EFS accessible only from EC2



🎯 Key Features

High Availability (Multi-AZ)

Auto Scaling (Dynamic resource management)

Load Balancing (Traffic distribution)

Shared Storage (EFS)

Secure Architecture (Security Groups)

Fault Tolerance



📈 Results

Application handled multiple requests efficiently

No downtime observed during testing

Instances scaled automatically

Data persisted across instance restarts



📚 Lessons Learned

Importance of load balancing

Benefits of shared storage (EFS)

Auto Scaling improves reliability

Security group design is critical



🧠 Conclusion

This project successfully demonstrates a production-ready AWS architecture capable of handling real-world application requirements with scalability, high availability, and security.



👨‍💻 Author

Ritik Mohadikar
