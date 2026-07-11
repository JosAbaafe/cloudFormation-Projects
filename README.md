<<<<<<< HEAD
# AWS CloudFormation Learning Labs

## Overview

This repository contains a collection of hands-on AWS CloudFormation labs completed as part of an Infrastructure as Code (IaC) learning journey. Each lab builds upon the previous one, gradually introducing more advanced CloudFormation concepts, from creating basic networking resources to implementing nested stacks and Lambda-backed custom resources.

The purpose of these labs is to develop a practical understanding of CloudFormation templates, reusable infrastructure, automation, and custom resource development.

---

## Learning Objectives

Throughout these labs, the following CloudFormation concepts are demonstrated:

* Infrastructure as Code (IaC)
* YAML template syntax
* Parameters, Outputs, and Intrinsic Functions
* Resource Dependencies
* Virtual Private Cloud (VPC) deployment
* EC2 instance provisioning
* Security Groups
* User Data scripts
* Nested Stacks
* Cross-stack communication
* IAM Roles and Policies
* AWS Lambda
* CloudFormation Custom Resources
* Dynamic AMI discovery

---

## Repository Structure

```text
CloudFormation-Labs/
│
├── Level-5-WebServer/
│   ├── template.yaml
│   └── README.md
│
├── Level-6-Nested-Stacks/
│   ├── network.yaml
│   ├── compute.yaml
│   ├── root.yaml
│   └── README.md
│
├── Level-7-Custom-Resource/
│   ├── template.yaml
│   └── README.md
│
└── README.md
=======
# Level 5 – Deploying an EC2 Web Server with CloudFormation

## Overview

In this project, I used AWS CloudFormation to deploy a fully functional EC2 web server. Instead of manually launching an instance and configuring it through the AWS Management Console, the entire infrastructure—including the EC2 instance, Security Group, and web server installation—was defined declaratively in a CloudFormation template.

The template automatically provisions an Amazon Linux 2023 EC2 instance, installs Apache HTTP Server using UserData, configures the service to start at boot, and publishes the website's public URL as a CloudFormation output.
---
## Deployment Result

The CloudFormation template successfully provisioned all required resources. The stack reached the **CREATE_COMPLETE** state, confirming that the EC2 instance, Security Group, and associated resources were deployed successfully.

### CloudFormation Stack

![CloudFormation Stack](screenshoots/stack-creat-complete.png)

### Stack Outputs

The Outputs section displays the automatically generated public IP address and website URL.

![CloudFormation Outputs](screenshoots/cloudformation-outputs.png)

---

## Objectives

* Provision an EC2 instance using CloudFormation.
* Create a Security Group allowing HTTP and SSH access.
* Install and configure Apache automatically with UserData.
* Dynamically retrieve the latest Amazon Linux AMI using AWS Systems Manager Parameter Store.
* Output the instance's Public IP and Website URL.

---

## Technologies Used

* AWS CloudFormation
* Amazon EC2
* Amazon Linux 2023
* Security Groups
* UserData
* AWS Systems Manager Parameter Store

---

## Architecture

```text
                    AWS CloudFormation
                           │
                           ▼
                Creates Security Group
                           │
                           ▼
                 Launches EC2 Instance
                           │
                           ▼
              Executes UserData Script
                           │
                           ▼
            Installs Apache HTTP Server
                           │
                           ▼
             Hosts Static HTML Web Page
                           │
                           ▼
             Accessible via Public IP
>>>>>>> branch-level-5-ec2-webserver
```

---

<<<<<<< HEAD
# Project Summaries

## Level 5 – Web Server Deployment

### Objective

Deploy an EC2 web server inside the VPC.

### Resources Created

* EC2 Instance
* Security Group
* User Data script
* Elastic Network Interface
* Public IP assignment

### Features

* Amazon Linux instance
* Apache web server installation
* Automatic web page deployment
* HTTP access through Security Groups

### Skills Learned

* EC2 provisioning
* User Data automation
* Security Group configuration
* Intrinsic functions
* Resource references

---

## Level 6 – Nested Stacks

### Objective

Split infrastructure into reusable CloudFormation templates.

### Templates

**network.yaml**

Creates:

* VPC
* Public Subnet
* Internet Gateway
* Route Table

**compute.yaml**

Creates:

* Security Group
* EC2 Instance
* Apache installation

**root.yaml**

Acts as the parent template that deploys both child stacks using:

* AWS::CloudFormation::Stack

### Benefits

* Reusable infrastructure
* Modular design
* Easier maintenance
* Better organization
* Improved scalability

### Skills Learned

* Nested stacks
* Stack outputs
* Stack parameters
* Cross-stack references

---

## Level 7 – Lambda-backed Custom Resource

### Objective

Create a Lambda-backed CloudFormation Custom Resource that dynamically discovers the latest Amazon Linux 2023 AMI instead of hardcoding an AMI ID.

### Resources Created

* IAM Role
* Lambda Function
* CloudFormation Custom Resource

### Lambda Responsibilities

* Handle Create events
* Handle Update events
* Handle Delete events
* Query Amazon EC2 DescribeImages API
* Filter Amazon Linux 2023 images
* Return the latest available AMI

### Skills Learned

* Custom Resources
* Lambda inline code
* IAM permissions
* EC2 API integration
* CloudFormation lifecycle events
* ResponseURL handling

---

# Technologies Used

* AWS CloudFormation
* AWS Lambda
* Amazon EC2
* Amazon VPC
* IAM
* Amazon Linux 2023
* Python 3.12
* YAML

---

# Prerequisites

Before deploying these templates, ensure you have:

* AWS Account
* AWS CLI configured
* IAM permissions to create CloudFormation stacks
* An existing S3 bucket (for nested stack templates if required)

---

# Key CloudFormation Concepts Demonstrated

* Infrastructure as Code
* Declarative infrastructure
* Resource orchestration
* Stack outputs
* Parameters
* Nested stacks
* Custom resources
* Lambda integration
* IAM least privilege
* Dynamic infrastructure provisioning

---

# Lessons Learned

These labs demonstrate the progression from creating basic AWS infrastructure to building modular, reusable, and dynamic CloudFormation solutions. By the end of the exercises, the repository showcases how CloudFormation can automate infrastructure deployment while following best practices such as modular template design, reusable components, and event-driven custom resources.

---

# Author

**Emmanuel Abaafe**

---

# License

This project is intended for educational and learning purposes.
=======
## What I Learned

This project introduced several important CloudFormation concepts:

* Using Parameter Store to automatically retrieve the latest AMI.
* Bootstrapping EC2 instances using UserData.
* Using intrinsic functions such as Ref, GetAtt, Base64, and Sub.
* Publishing useful deployment information through Outputs.
* Managing infrastructure updates with CloudFormation.

---

## Observation

After updating the InstanceType from **t3.micro** to **t3.small**, CloudFormation replaced the EC2 instance because changing the instance type required resource replacement. As a result, the Public IP address also changed.

This demonstrates how CloudFormation determines whether a property can be updated in place or whether the resource must be recreated.

---
## Web Server Verification

After waiting a few minutes for the UserData script to complete, Apache HTTP Server was installed automatically and the web page became accessible through the public IP address.

![Web Server](screenshoots/website-homepage.png)

---
## EC2 Instance

The deployed EC2 instance is visible in the EC2 console with the instance type specified in the CloudFormation template.

![EC2 Instance](screenshoots/ec2-instance.png)

---

## Challenge Completed

As an extension, an Elastic IP can be associated with the EC2 instance using:

* AWS::EC2::EIP
* AWS::EC2::EIPAssociation

With an Elastic IP attached, future instance replacements preserve the public IP address, making the web server endpoint stable.

---

## Key Takeaways

* Infrastructure can be fully automated using CloudFormation.
* UserData enables automated software installation.
* Security Groups act as virtual firewalls.
* Outputs simplify retrieving deployment information.
* Elastic IPs provide stable public addresses across instance replacements.
>>>>>>> branch-level-5-ec2-webserver
