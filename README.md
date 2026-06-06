# FashionFlow — Cloud Business Platform

A cloud-hosted business platform for a wholesale fashion company, built as part of a BTEC Unit 6: Networking in the Cloud assignment.

## Overview

This project simulates the ERP, CRM, and WMS systems of a wholesale fashion company migrated to AWS cloud infrastructure.

## Pages

| Page | Description |
|------|-------------|
| `index.html` | Main landing page |
| `pages/erp.html` | Enterprise Resource Planning dashboard |
| `pages/crm.html` | Customer Relationship Management dashboard |
| `pages/wms.html` | Warehouse Management System dashboard |

## Technology Stack

- HTML5 / CSS3 / Vanilla JavaScript
- Hosted on AWS EC2 (Ubuntu 22.04)
- Served via Nginx web server
- Network: AWS VPC, Public/Private Subnets, ALB, NAT Gateway

## AWS Infrastructure

```
Internet
    │
    ▼
Internet Gateway
    │
    ▼
Application Load Balancer (Public Subnet)
    │
    ▼
EC2 Instance — Nginx (Public Subnet 10.0.1.0/24)
    │
    ▼
Private Subnet (10.0.2.0/24) — DB / Backend
    │
NAT Gateway → Internet (outbound only)
```

## CI/CD

Automated deployment via GitHub Actions — on every push to `main`, the site is automatically deployed to the EC2 instance via SSH.

## Deployment

```bash
# On EC2 instance
sudo apt update
sudo apt install nginx -y
sudo cp -r . /var/www/html/
sudo systemctl restart nginx
```
