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
git clone https://github.com/lordsesay/codechallenge3.git
cd codechallenge3  

### 2. Set Up AWS Credentials
Before running the Terraform or Ansible commands, you need to set up your AWS credentials. You can do this by configuring the AWS CLI:

bash
Copy code
aws configure
Provide your AWS Access Key, Secret Key, default region, and output format.

### 3. Terraform Configuration
a) Provisioning Infrastructure
In this section, we'll use Terraform to provision:

An EC2 instance
An S3 bucket
IAM roles and security groups
To get started with Terraform, initialize your project:

bash
Copy code
terraform init
This command will install the necessary Terraform provider plugins.

b) Plan and Apply Terraform Configuration
To review the infrastructure that Terraform will create, run the following:

bash
Copy code
terraform plan
If everything looks good, apply the configuration to create the infrastructure:

bash
Copy code
terraform apply
Terraform will prompt you for confirmation before proceeding. Type yes to proceed with the creation.

c) Resources Created
EC2 Instance: A Linux-based EC2 instance that serves as the web server.
S3 Bucket: A simple S3 bucket to be used for future configurations (if needed).
IAM Roles and Security Groups: Configured for secure access to the EC2 instance.

### 4. Ansible Configuration
a) Install and Configure the Web Server
Once the infrastructure is provisioned, use Ansible to configure the EC2 instance. You will install a web server (such as Nginx) and deploy a simple "Hello, World!" web page.

Ensure that the hosts file is updated to point to the newly created EC2 instance.
In your Ansible inventory, include the public IP or DNS of the EC2 instance.
Run the Ansible playbook to configure the server:

bash
Copy code
ansible-playbook -i hosts setup_web_server.yml
This will install the web server and deploy the "Hello, World!" page.

b) Ansible Playbook Explanation
setup_web_server.yml: This playbook installs Nginx, copies a simple HTML file to the server, and ensures that the web server is running.
Example playbook content:

yaml
Copy code
---
- name: Configure EC2 instance with Nginx
  hosts: web
  become: yes

  tasks:
    - name: Install Nginx
      apt:
        name: nginx
        state: present

    - name: Deploy Hello World page
      copy:
        content: "Hello, World!"
        dest: /var/www/html/index.html

    - name: Start Nginx service
      service:
        name: nginx
        state: started
        enabled: yes

### 5. Access the Web Page
Once the playbook runs successfully, you can access the web page by navigating to the public IP of your EC2 instance in a web browser. The page should display "Hello, World!".

Example URL:

vbnet
Copy code
http://<public-ip-of-ec2-instance>
6. Cleanup
To destroy the resources created by Terraform, run the following command:

bash
Copy code
terraform destroy
This will remove the EC2 instance, S3 bucket, and other infrastructure components.

Conclusion
This project demonstrates how to use Terraform and Ansible together to provision and configure infrastructure on AWS. The EC2 instance was configured with a simple web server that serves a "Hello, World!" page.

Repository Link
GitHub Repository

