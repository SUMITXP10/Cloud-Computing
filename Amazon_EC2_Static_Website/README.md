# Amazon EC2 Static Website

## Overview

This project demonstrates how to host a static website on an Ubuntu Amazon EC2 instance using the Apache web server.

The website was deployed to an Ubuntu EC2 instance and made publicly accessible through the instance's public IPv4 address.

The activity covers:

- Launching and configuring an Ubuntu EC2 instance
- Configuring SSH and HTTP access
- Connecting to and managing the EC2 environment
- Installing and configuring Apache
- Deploying a static HTML website
- Configuring website file permissions
- Verifying Apache and website accessibility
- Accessing the hosted website using the EC2 public IP address
- Cleaning up AWS resources after completion

The workflow follows the requirements provided in the **Student Activity Amazon EC2** document. :contentReference[oaicite:0]{index=0}

---

## Assignment Objective

To deploy a static website on an Ubuntu Amazon EC2 instance using Apache and make the website accessible through the EC2 instance's public IP address.

The assignment specifically requires the website to be served from:

```text
/var/www/html

Amazon_EC2_Static_Website/
│
├── screenshots/
│   ├── Final_Website_Verification.png
│   └── ...
│
├── index.html
├── index2.html
├── My_Day.png
├── Amazon-EC2-Static-Website-Key.pem
├── Commands.txt
├── README.md
├── Student Activity Amazon EC2.pdf
├── Terminal_Output_1.txt
├── Terminal_Output_2.txt
└── Screenshot.pdf

Operating System : Ubuntu Server 22.04 LTS
Instance Type    : t2.micro
Region           : ap-south-1

| Protocol | Port | Purpose |
| -------- | ---: | ------- |
| TCP      |   22 | SSH     |
| TCP      |   80 | HTTP    |

#Apache Web Server Installation

##Apache2 was installed on the Ubuntu EC2 instance.

## Commands used :

sudo apt update
sudo apt upgrade -y
sudo apt install apache2 -y

Apache was then started and enabled to start automatically:

sudo systemctl start apache2
sudo systemctl enable apache2

The service status was verified using:

sudo systemctl status apache2

The State was:

Active: active (running)

Apache Website Directory

/var/www/html

Static Website

A project-owned index.html was created locally and deployed to the EC2 instance.

The final website contains:

A126023 AWS Project

AMAZON EC2 • STATIC WEBSITE

My First Website
Hosted on AWS

A simple static website deployed on an Ubuntu Amazon EC2
instance using the Apache web server.

View Project

Amazon EC2
Ubuntu Server
Apache Running

The project also includes index2.html, which contains the final styled version with the custom background image:

My_Day.png

The website's View Project button links to:

https://github.com/SUMITXP10/Cloud-Computing

Website Permissions

The deployed website files were assigned the appropriate ownership:

sudo chown -R www-data:www-data /var/www/html

Permissions were configured using:

sudo chmod -R 755 /var/www/html

Apache Restart

After deploying the final website files, Apache was restarted:

sudo systemctl restart apache2

Website Verification

The website was verified from the EC2 public IP address.

Final website URL:

http://3.110.176.24/

The website was also verified programmatically from PowerShell using:

Invoke-WebRequest "http://$PUBLIC_IP" -UseBasicParsing

Result:

StatusCode : 200

Final Website Architecture

                    User Browser
                         │
                         │ HTTP : 80
                         ▼
             ┌─────────────────────────┐
             │      Amazon EC2         │
             │    Ubuntu Server       │
             │                         │
             │      Apache2            │
             │                         │
             │    /var/www/html/       │
             │                         │
             │      index.html         │
             │      My_Day.png         │
             └─────────────────────────┘
                         │
                         ▼
                 Static Web Page


This matches the architecture described in the activity: browser → HTTP port 80 → Ubuntu EC2 → Apache → /var/www/html.

AWS Management Approach

AWS Systems Manager (SSM) was used during the deployment workflow to execute commands on the EC2 instance.

This allowed the Apache installation, website deployment, file permission configuration, service restart, and verification to be performed without repeatedly establishing an interactive SSH session.

Evidence

The project contains terminal transcripts and screenshots documenting the implementation.

Important evidence includes:

EC2 instance configuration
Security Group configuration
Apache installation
Apache service status
Website deployment
File permissions
Website verification
Final browser output
AWS resource cleanup

Terminal command history is preserved in:

Terminal_Output_1.txt
Terminal_Output_2.txt

Additional commands are documented in:

Commands.txt

AWS Resource Cleanup

After the assignment was completed and the final evidence was captured, the AWS resources created specifically for this exercise were cleaned up.

Cleaned resources included:

EC2 Instance
Security Group
AWS-side EC2 Key Pair
IAM Instance Profile
IAM Role

The local project files and GitHub repository were retained.

Existing default AWS networking resources such as the default VPC, default subnet, default route table, and Internet Gateway were not deleted because they were pre-existing shared networking infrastructure.

Learning Outcomes

This exercise demonstrated the following:

Launching and configuring an Ubuntu EC2 instance
Connecting to an EC2 server
Configuring AWS Security Groups
Installing and managing Apache
Deploying a static website
Managing files under /var/www/html
Configuring Linux file ownership and permissions
Verifying Apache service availability
Testing HTTP website accessibility
Using AWS CLI and Systems Manager
Managing AWS resources responsibly after completion

These outcomes align with the learning outcomes listed in the provided activity document.

Final Result

The static website was successfully deployed on Amazon EC2 using Ubuntu Server and Apache.

Final website:

http://3.110.176.24/