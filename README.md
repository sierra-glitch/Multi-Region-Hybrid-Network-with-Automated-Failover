# Multi-Region-Hybrid-Network-with-Automated-Failover
Project Overview 

This independent AWS project demonstrates the design and implementation of a multi-region, active/passive network architecture with automated failover. The project was inspired by my previous experience working with Global Command and Control System-Maritime (GCCS-M) and multi-system environments in the U.S Navy. I am using this project to translate concepts from mission-critical network operations into a modern cloud environment using AWS networking, compute, security, DNS, and monitoring services. 

The architecture consists of two AWS Regions representing a primary and disaster recovery environment:
Primary Region: US East (N. Virginia) - us-east-1
Secondary Region: US West (Oregon) - us-west-2 

The primary environment handles normal workload traffic while the secondary environment remains available as a warm standby. Route 53 health checks are used to detect primary workload failure and support automated DNS Failover to the secondary environment.

