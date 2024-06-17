! [Alt text](/static-website-deployement-on-aws.png)
## Static Website Deployment on AWS

This repository contains the resources and instructions to deploy a static HTML web application on AWS using various AWS services. The deployment leverages a range of AWS services to ensure reliability, scalability, and security.

## Project Overview

This project involves deploying a static website on AWS with the following key components:

- **Virtual Private Cloud (VPC):** Configured with both public and private subnets across two different availability zones.
- **Internet Gateway:** Facilitates connectivity between VPC instances and the wider Internet.
- **Security Groups:** Act as a network firewall mechanism.
- **Availability Zones:** Enhance system reliability and fault tolerance by leveraging multiple zones.
- **Public Subnets:** Used for infrastructure components like the NAT Gateway and Application Load Balancer.
- **EC2 Instance Connect Endpoint:** Enables secure connections to assets within both public and private subnets.
- **Private Subnets:** Host web servers (EC2 instances) for enhanced security.
- **NAT Gateway:** Allows instances in private subnets to access the Internet.
- **EC2 Instances:** Host the static website.
- **Application Load Balancer:** Distributes web traffic evenly to an Auto Scaling Group of EC2 instances across multiple availability zones.
- **Auto Scaling Group:** Automatically manages EC2 instances to ensure availability, scalability, fault tolerance, and elasticity.
- **Certificate Manager:** Secures application communications.
- **Simple Notification Service (SNS):** Alerts about activities within the Auto Scaling Group.
- **Route 53:** Manages domain names and DNS records.

## Architecture Diagram

## Prerequisites

Before you begin, ensure you have the following:

- An AWS account with the necessary permissions to create and manage AWS resources.
- AWS CLI configured on your local machine.
- Git installed on your local machine.

## Deployment Script

Follow these steps to deploy the static website:

1. **Clone the Repository:**
    
    ```bash
    #!/bin/bash
    
    #STATIC WEBSITE INSTALLATION SCRIPT ON THE EC2
    
    # Switch to the root user to gain full administrative privileges
    sudo su
    
    # Update all installed packages to their latest versions
    yum update -y
    
    # Install Apache HTTP Server
    yum install -y httpd
    
    # Change the current working directory to the Apache web root
    cd /var/www/html
    
    # Install Git
    yum install git -y
    
    # Clone the project GitHub repository to the current directory
    git clone https://github.com/fred4impact/static-website-deployement-on-aws.git
    
    # Copy all files, including hidden ones, from the cloned repository to the Apache web root
    cp -R host-a-static-website-on-aws/. /var/www/html/
    
    # Remove the cloned repository directory to clean up unnecessary files
    rm -rf host-a-static-website-on-aws
    
    # Enable the Apache HTTP Server to start automatically at system boot
    systemctl enable httpd 
    
    # Start the Apache HTTP Server to serve web content
    systemctl start httpd
    ```
