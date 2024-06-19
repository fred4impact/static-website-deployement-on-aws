![Alt text](/static-website-deployement-on-aws.png)
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
 ```
#!/bin/bash

# Update package lists and install required packages
sudo apt update
sudo apt install apache2 git -y

# Clone repository and copy files to Apache document root
git clone https://github.com/fred4impact/static-website-deployement-on-aws.git
sudo cp -R static-website-deployement-on-aws/. /var/www/html/

# Clean up cloned repository
sudo rm -rf static-website-deployement-on-aws

# Enable and start Apache
sudo systemctl enable apache2
sudo systemctl start apache2

# Display Apache status
sudo systemctl status apache2

# Start the Apache HTTP Server to serve web content
 systemctl start httpd
 ```
