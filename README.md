# AWS Highly Available Cloud Infrastructure Project

## Project Overview

This project demonstrates the design and deployment of a highly available AWS cloud infrastructure for a web application.

The infrastructure was built with a focus on networking, availability, security, monitoring, scaling, and backup — key areas for an Associate Cloud Engineer role.

## Architecture

Internet  
↓  
Application Load Balancer  
↓  
Target Group  
↓  
Auto Scaling Group  
↓  
EC2 Instances in Private Subnets across multiple Availability Zones

Private EC2 instances use a NAT Gateway for outbound internet connectivity.

## AWS Services Used

- Amazon VPC
- Public and Private Subnets
- Internet Gateway
- NAT Gateway
- Route Tables
- Security Groups
- Amazon EC2
- Launch Template
- Application Load Balancer
- Target Groups
- Auto Scaling Group
- IAM Roles
- AWS Systems Manager permissions
- Amazon CloudWatch
- Amazon SNS
- Amazon EBS
- EBS Snapshots

## Implementation

### Networking
- Created a custom VPC.
- Created 2 public and 2 private subnets across two Availability Zones.
- Configured separate public and private route tables.
- Connected public subnets to an Internet Gateway.
- Configured NAT Gateway access for private subnets.

### Security
- Created a public-facing security group for the Application Load Balancer.
- Allowed EC2 HTTP traffic only from the ALB security group.
- Used IAM roles instead of storing permanent credentials.

### Compute and High Availability
- Created a reusable EC2 Launch Template.
- Configured an Auto Scaling Group with:
  - Minimum capacity: 2
  - Desired capacity: 2
  - Maximum capacity: 4
- Distributed EC2 instances across multiple Availability Zones.

### Load Balancing
- Created an Application Load Balancer.
- Created a Target Group with HTTP health checks.
- Connected the Auto Scaling Group to the Target Group.
- Verified both EC2 targets as Healthy.
- Successfully accessed the application using the ALB DNS endpoint.

### Auto Scaling
- Configured a target tracking scaling policy based on average CPU utilization.

### Monitoring
- Configured Amazon CloudWatch CPU monitoring.
- Created a CloudWatch CPU alarm.
- Integrated the alarm with an Amazon SNS topic for notifications.

### Storage and Backup
- Created an EBS snapshot from an EC2 volume.
- Restored a new EBS volume from the snapshot.

## High Availability Design

The application runs across multiple Availability Zones.

If an EC2 instance becomes unavailable, the Auto Scaling Group can launch a replacement instance using the Launch Template while the Application Load Balancer routes traffic to healthy targets.

## Project Result

Successfully built a working AWS infrastructure that demonstrates:

- High Availability
- Load Balancing
- Auto Scaling
- Private EC2 architecture
- Network segmentation
- IAM-based security
- Cloud monitoring
- SNS integration
- EBS backup and recovery

## Author

Rohit Kumar  
Associate Cloud Engineer
