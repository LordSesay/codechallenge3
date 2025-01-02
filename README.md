# Cloud Engineer Coding Challenge

## Overview

This project demonstrates the use of **Terraform** for provisioning infrastructure on **AWS** and **Ansible** for configuration management. The infrastructure includes an **EC2 instance**, an **S3 bucket**, and necessary **IAM roles and security groups**. The EC2 instance is configured using Ansible to install and configure a **web server** (Nginx or Apache) and deploy a simple **"Hello, World!"** web page.

## Requirements

Before you begin, ensure that the following are installed:

- **Terraform**: [Install Terraform](https://learn.hashicorp.com/tutorials/terraform/install-cli)
- **Ansible**: [Install Ansible](https://docs.ansible.com/ansible/latest/installation_guide/index.html)
- **AWS Account**: You need an AWS account with appropriate permissions to create and manage EC2 instances, S3 buckets, and IAM roles.
- **Git**: To version control your code and push it to GitHub.
- **AWS CLI**: [Install AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html) (for interacting with AWS via command line)

## Setup Instructions

### 1. Clone the Repository

Clone this repository to your local machine:

```bash
git clone https://github.com/yourusername/cloud-engineer-coding-challenge.git
cd cloud-engineer-coding-challenge
