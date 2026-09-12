cat > README.md <<'EOF'
# Amazon EC2 Static Website

## Overview

This project demonstrates hosting a static website on an Amazon EC2 instance running Ubuntu Server and Apache HTTP Server.

The deployment covers:

- Amazon EC2 instance provisioning
- Ubuntu Server 22.04 LTS
- EC2 security group configuration
- SSH access configuration
- Apache web server installation and management
- Static website deployment to `/var/www/html`
- File ownership and permissions
- Public IP website verification

## Assignment Objective

Host a static website using Amazon EC2 with an Ubuntu server and Apache web server.

The final website displays:

> **Hello AWS!**  
> **Website hosted on Amazon EC2.**

## Architecture

```text
User Browser
     |
     | HTTP :80
     v
+-----------------------------+
| Amazon EC2                  |
| Ubuntu Server 22.04 LTS     |
|                             |
| Apache Web Server            |
| /var/www/html                |
|                             |
| index.html                   |
+-----------------------------+