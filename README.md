# AWS-Project-1
Deploying a Multi-Tier Website using AWS EC2

📘 Project: High Availability PHP Website on AWS Using EC2 Auto Scaling & RDS

📌 Project Overview

This project demonstrates how to deploy a highly available PHP-based website on AWS using Amazon EC2 Auto Scaling and Amazon RDS (MySQL).
The architecture ensures scalability, fault tolerance, and secure communication between application and database layers.

🏗️ Architecture Components

    Amazon EC2 – Hosts the PHP website
    
    Auto Scaling Group (ASG) – Maintains a minimum of 2 EC2 instances for high availability
    
    Amazon RDS (MySQL) – Managed relational database
    
    Security Groups – Controls traffic between EC2 and RDS
    
    Elastic Load Balancer (Optional but Recommended) – Distributes traffic across EC2 instances

⚙️ Prerequisites

    AWS Account
    
    IAM User with EC2, RDS, Auto Scaling, and Security Group permissions
    
    Basic knowledge of Linux, PHP, and MySQL
    
    GitHub Account

🚀 Implementation Steps
    1. Launch EC2 Instance
    
    Created an Amazon Linux EC2 instance
    
    Installed:
    
    Apache Web Server
    
    PHP
    
    MySQL client
    
    Uploaded PHP website files to /var/www/html
    
    2. Create AMI & Enable Auto Scaling
    
    Created a custom AMI from the configured EC2 instance
    
    Created a Launch Template using the AMI
    
    Configured Auto Scaling Group:
    
    Minimum instances: 2
    
    Desired capacity: 2
    
    Maximum instances: As per requirement
    
    3. Create RDS Instance
    
    Engine: MySQL
    
    Database Name: intel
    
    Master Username: admin
    
    Password: intel123
    
    4. Create Database & Table
    
    Connected to RDS from EC2 and ran:
    
    CREATE DATABASE intel;
    USE intel;
    
    CREATE TABLE data (
        id INT AUTO_INCREMENT PRIMARY KEY,
        name VARCHAR(100),
        value VARCHAR(100)
    );
    
    5. Update Website Database Hostname
    
    Edited the PHP config file to use the RDS endpoint instead of localhost:
    
    $host = "your-rds-endpoint.amazonaws.com";
    $username = "admin";
    $password = "intel123";
    $database = "intel";
    
    6. Configure Security Groups
    
    EC2 Security Group:
    
    Allow HTTP (80) from anywhere
    
    Allow SSH (22) from your IP
    
    RDS Security Group:
    
    Allow MySQL (3306) only from EC2 Security Group
    
    7. Enable Public Access to Website
    
    Verified website accessibility using EC2 Public IP / Load Balancer DNS

🔐 Security Considerations

    RDS is not publicly accessible
    
    Database access restricted to EC2 instances only
    
    SSH access limited to trusted IPs

📸 Screenshots

    Screenshots of:
    
    EC2 Instance Setup
    
    Auto Scaling Group Configuration
    
    RDS Database Creation
    
    Website Running Successfully

✅ Outcome

    Successfully deployed a scalable and highly available PHP website
    
    Auto Scaling ensures minimum 2 EC2 instances at all times
    
    Secure and reliable database connectivity using Amazon RDS

🧠 Learning Highlights

    EC2 & Auto Scaling Configuration
    
    RDS MySQL Setup
    
    Security Group Rules & Network Security
    
    Real-world AWS Architecture Design
