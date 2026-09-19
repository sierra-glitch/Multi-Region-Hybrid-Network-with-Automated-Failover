# Architecture Plan 

## Project Purpose 

The purpose of this project is to design and implement a multi-region AWS architecture that demonstrates high availability, disaster recovery, network segmentation, monitoring, and automated fail over. 

## Regional Architecture 

### Primary Region 
- Region: US East (N. Virginia)
- AWS Region: us-east-1
- Environment: Carrier 1
- Role: Primary

### Secondary Region 
- Region: US West (Oregon)
- AWS Region: us-west-2
- Environment: Carrier 2
- Role: Warm Standby / Disaster Recovery

## Network Design 

### Carrier 1 
- VPC: 10.0.0.0/16
- Public Subnet: 10.0.1.0/24
- Private Subnet: 10.0.2.0/24

### Carrier 2
- VPC: 10.1.0.0/16
- Public Subnet: 10.1.1.0/24
- Private Subnet: 10.1.2.0/24

## Failover Strategy 
Amazon Route 53 health continuously monitor the availability and performance of servers and applications. If the primary web server of carrier 1 stops operating, it is redirected to the secondary back up (secondary carrier).  

## Planned High Availability Expansion 
The project will be expanded to include an Amazon RDS database for high availability

## Amazon RDS MySQL database
- VPC:carrier-db-subnet-group
- Availability Zones: us-east-1a and us-east-1b
- subnets: private subnets is used
- security group: MySQL/Aurora (Port 3306) 

The database architecture will demonstrate: 
- strong isolation topology
- database security using port 3306
- Single Availability Zones
- Automatic database failover
- High availability within the primary AWS Region

## Modern Serverless & Event-Driven Architecture 
Amazon Lambda is a serverless, event-driven compute service that allows for applications to be ran by code without provisioning, configuring, or managing physical or virtual servers. Amazon Lambda executes code only when triggered by a specific event and automatically handles the underlying infrastructure, scaling, and security patching. 

  
- 
