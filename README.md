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
├── Level-3-VPC/
│   ├── template.yaml
│   └── README.md
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
```

---

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

# Deployment

Deploy any template using the AWS CLI:

```bash
aws cloudformation deploy \
  --template-file template.yaml \
  --stack-name my-stack \
  --capabilities CAPABILITY_NAMED_IAM
```

For nested stacks:

```bash
aws cloudformation deploy \
  --template-file root.yaml \
  --stack-name nested-stack \
  --capabilities CAPABILITY_NAMED_IAM
```

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

MPhil Computer Science

Regulatory Administrative Officer

National Communications Authority (NCA)

---

# License

This project is intended for educational and learning purposes.
