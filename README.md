# AWS Cloud Support Lab - Linux Administration and Monitoring

## Project Overview

This project simulates the real-world responsabilities of a Cloud Support Engineer. It demonstrates how to provision, configure, secure and monitor an enterprise Linux server hosted on AWS using Free Tier eligible resources.

--

## Skills & Technologies Demonstrated:

- Cloud Infrastructure: Amazon EC2, Elastic Block Storage (EBS), Amazon CloudWatch, AWS IAM, Security Groups.

- Security Administration: Linux User & Group Management, Privilege Escalation (sudoers), Package Management (dnf), Storage Volumes Partitioning and Mounting (blkid, mkfs, /etc/fstab) 

- DevOps Frameworks: Version Control (Git/GitHub), Security Best Practices (Private Key insulation, firewall narrowing), Telemetry Configuration (JSON configuration files)

--

## Architecture & Data Flow

GitHub Codespaces (Ubuntu)
             │
             │ Secure SSH (Port 22)
             ▼
┌─────────────────────────────────────────────────────────┐
│ AWS Cloud (Free Tier)                                   │
│                                                         │
│   ┌─────────────────────────────────────────────────┐   │
│   │ Amazon EC2 (Amazon Linux 2023)                  │   │
│   │                                                 │   │
│   │  ├── IAM Role: cloud-support-lab-monitor-role   │   │
│   │  │                                              │   │
│   │  ├── Security Group Firewall (Port 22 Allow)    │   │
│   │  │                                              │   │
│   │  ├── Attached 2 GiB EBS Disk (/mnt/data)        │   │
│   │  │                                              │   │
│   │  └── CloudWatch Telemetry Agent (RAM/Disk metrics)─┼┐
│   └─────────────────────────────────────────────────┘  ││
└──────────────────────────────────────────────────────  ┼┘
                                                         │
                                                         ▼
                                             Amazon CloudWatch Metrics

## Proof of Work & Validation

### 1. SSH Authentication
Successfully configured private key file permissions (chmod 400) and bypassed a common network gateway block to log securely into the Amazon Linux machine using SSH.

### 2. Live System Diagnostics & Persistent Storage Expansion
Provisioned a secondary raw 2 GiB block storage volume (EBS) via AWS, attached it, formatted it with an XFS filesystem layout, and registerd it permanently inside "etc/fstab" using its unique hardware UUID.

### 3. Granular OS Performance Monitoring
Configured a locak JSON schema payload rule for the "amazon-cloudwatch-agent" tool daemon. Attached an IAM server policy role to authorize the collection of granular OS memory usage statistics into CloudWatch metrics charts.


