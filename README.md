# Multi-Region-Hybrid-Network-with-Automated-Failover
Project Overview 

This independent AWS project demonstrates the design and implementation of a multi-region, active/passive network architecture with automated failover. The project was inspired by my previous experience working with Global Command and Control System-Maritime (GCCS-M) and multi-system environments in the U.S Navy. I am using this project to translate concepts from mission-critical network operations into a modern cloud environment using AWS networking, compute, security, DNS, and monitoring services. 

The architecture consists of two AWS Regions representing a primary and disaster recovery environment:
Primary Region: US East (N. Virginia) - us-east-1
Secondary Region: US West (Oregon) - us-west-2 

The primary environment handles normal workload traffic while the secondary environment remains available as a warm standby. Route 53 health checks are used to detect primary workload failure and support automated DNS Failover to the secondary environment.

Project Objectives
The objectives of this project are to: 

Design a multi-region AWS network from the ground up 
Implement isolated VPC environments in two AWS regions
Apply subnetting and routing fundamentals
Deploy Linux-based EC2 workloads
Configure security groups using the principle of least privilege
Implement DNS-based traffic management with Amazon Route 53
Configure health monitoring for the primary workload
Demonstrate automated failover to a secondary region 
Apply disaster recovery and high-availability concepts in AWS
Document the architecture and implementation process for a technical portfolio

