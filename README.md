# AWS EC2 Nginx Infrastructure Project

## 📌 Project Overview

This project demonstrates how to deploy a Linux-based web server on AWS using Amazon EC2.  
The objective was to configure secure remote access, install Nginx, and expose a public web server using properly configured security group rules.

---

## 🏗 Architecture

Internet  
↓  
Security Group (Port 80 open to public, Port 22 restricted to my IP)  
↓  
EC2 Instance (Ubuntu 22.04 LTS)  
↓  
Nginx Web Server  

---

## 🔐 Security Configuration

- SSH (Port 22) restricted to my public IP
- HTTP (Port 80) open to 0.0.0.0/0
- Key-based authentication using RSA (.pem file)
- IAM admin user used instead of root account
- Default VPC configuration

---

## 🚀 Deployment Steps

### 1️⃣ Launch EC2 Instance

- AMI: Ubuntu Server 22.04 LTS
- Instance type: t2.micro (Free Tier eligible)
- Auto-assign Public IP: Enabled
- Key pair: RSA (.pem)

---

### 2️⃣ Configure Security Group

- SSH → My IP only
- HTTP → 0.0.0.0/0

---

### 3️⃣ Connect via SSH

```bash
chmod 400 nginx-server.pem
ssh -i nginx-server.pem ubuntu@<PUBLIC_IP>

4️⃣ Install Nginx
sudo apt update
sudo apt install nginx -y
sudo systemctl status nginx
📊 Verification

Accessed the web server using:

http://<PUBLIC_IP>

Confirmed that the default Nginx welcome page was successfully displayed in the browser.
