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
Amazon Route 53 health checks monitor the primary workload. If the primary endpoint becomes unavailable, DNS failover directs traffic toward the secondary region. 

## Planned High Availability Expansion 
The project will be expanded to include an Amazon RDS database using a Multi-AZ deployment. 

The database architecture will demonstrate: 
- Primary DB instance
- Standby DB instance
- Separate Availability Zones
- Automatic database failover
- High availability within the primary AWS Region

## Future Enhancements 
- Amazon RDS Multi-AZ
- Database subnet group
- Database security group
- Application to date connectivity
- Monitoring and failover validation
  
- 
