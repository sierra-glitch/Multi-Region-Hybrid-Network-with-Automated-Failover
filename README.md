# Multi-Region Hybrid Network with Automated Failover
##Project Overview 

This independent AWS project demonstrates the design and implementation of a multi-region, active/passive network architecture with automated failover. The project was inspired by my previous experience working with Global Command and Control System-Maritime (GCCS-M) and multi-system environments in the U.S Navy. I am using this project to translate concepts from mission-critical network operations into a modern cloud environment using AWS networking, compute, security, DNS, and monitoring services. 

The architecture consists of two AWS Regions representing a primary and disaster recovery environment:
|Primary Region | US East (N. Virginia) | us-east-1 |
|Secondary Region | US West (Oregon) | us-west-2 |

The primary environment handles normal workload traffic while the secondary environment remains available as a warm standby. Route 53 health checks are used to detect primary workload failure and support automated DNS Failover to the secondary environment.

## Project Objectives 
- Design a multi-region AWS network from the ground up 
- Implement isolated VPC environments in two AWS regions
- Apply subnetting and routing fundamentals
- Deploy Linux-based EC2 workloads
- Configure security groups using the principle of least privilege
- Implement DNS-based traffic management with Amazon Route 53
- Configure health monitoring for the primary workload
- Demonstrate automated failover to a secondary region 
- Apply disaster recovery and high-availability concepts in AWS
- Document the architecture and implementation process for a technical portfolio

## Architecture 
The project uses a multi-region, active/passive architecture designed to provide workload availability and automated disaster recovery. Two independent VPC environments are deployed across separate AWS Regions, with one environment serving as the primary workload location and the second operating as a warm standby. Each VPC uses a /16 CIDR block, with /24 subnet allocations for public and private workloads. The address spaces are non-overlapping to provide clear network segmentation and simplified routing. 

|Environment | AWS Region | VPC CIDR | Role | 
|---|---|---|---|
|Carrier 1 | us-east-1 | 10.0.0.0/16 | Primary | 
|Carrier 2 | us-west-2 | 10.1.0.0/16 | Warm Standby | 

Carrier 1 operates in US East (N.Virginia) as the primary environment. Carrier 2 operates in US West (Oregon) as the secondary disaster recovery environment. 

Under normal operating conditions, application traffic is directed to the primary environment. Amazon Route 53 health checks monitor the primary workload, and the DNS failover is configured to redirect traffic to the secondary environment when the primary endpoint becomes unavailable. 

Each regional VPC is segmented into public and private subnets to separate internet-facing workloads from internal resources. The environments use non-overlapping CIDR ranges to provide clear network boundaries and support future expansion. The architecture is designed to demonstrate core cloud networking and disaster recovery concepts, including VPC isolation, subnetting, routing, security controls, DNS-based failover, health monitoring, and high availability. 

## Network Architecture 
Within the network, there are two independent AWS VPC environments across separate AWS Regions. The primary environment operates in US East (N.Virginia) while the secondary environment operates in US West (Oregon) as warm standby for disaster recovery and automated failover. 

# Subnet Design 
Each VPC contains one public subnet and one private subnet. The public subnets are designed to support internet workloads, while the private subnets provide an isolated network segment for resources that do not require direct internet exposure. 

|Environment |  Subnet | CIDR | Type |
|---|---|---|---|
|Carrier 1 | Carrier1-Public-Subnet | 10.0.1.0/24 | Public
|Carrier 1 | Carrier1-Private-Subnet | 10.0.2.0/24 | Private
|Carrier 2 | Carrier2-Public-Subnet | 10.1.1.0/24 | Public
|Carrier 2 | Carrier2-Private-Subnet | 10.1.2.0/24 | Private 

##Network Segmentation 
The public and private subnet design provides separation between internet facing and internal workloads. 

## Public subnet responsibilites 
- Hosts internet facing EC2 workloads
- Uses a route table with a default route to an Internet Gateway 
- Supports the publicly accessible application endpoint 

## Private subnet responsibilites 
- Provides an isolated network segment for internal resources
- Does not provide direct inbound internet access
- Can be used for future application, database, or management workloads

## AWS Services Used 
This project uses the following AWS services to build the framework of the multi-region network architecture. 
|AWS Service | Purpose |
|---|---|
|Amazon VPC | Provides isolated virtual networks for the primary and secondary carriers |
|Amazon EC2 | Hosts the Linux-based workloads used to represent application endpoints in each region |
|Amazon Route 53 | Provides DNS management, health checks, and automated failover between the primary and secondary carriers |
|Internet Gateway | Provides internet connectivity for resources deployed in the public subnets |
|Route Tables | Control traffic routing within each VPC and provide the appropriate path to the Internet Gateway |
|Security Groups | Provide stateful, instance-level network access controls based on the principle of least privilege |
|Amazon CloudWatch | Provides monitoring and visibility into AWS resources and workload health |



