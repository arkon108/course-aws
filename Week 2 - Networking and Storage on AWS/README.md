# Week 2 - Networking and Storage on AWS


## Amazon Virtual Private Cloud (VPC)

The idea of the VPC is to provide a box where my application lives and nothing else comes inside, and nothing goes of the box without my explicit permission. The space in the VPC is divided into subnets. Usually subnets are used to allow services to talk quickly one to another. In AWS, subnets are used to determine access to gateways, ingress/egress & to isolate a specific traffic I want to allow or block. 

To build a VPC I need to specify two things:

  1. The region
  2. IP range for the private range of IPs which are going to run inside this VPC

For example, IP range can be 10.10.0.0/16. First subnet could then be 10.10.1.0/24 (24 means first 24 bits are frozen in CIDR notation).

To allow website being accessed, we need to add a gateway - IGW (Internet Gateway). It also needs a route table, associated with the subnet. 0.0.0.0/0 represents the traffic from the internet. Even though this can be done manually, in production environment is suggested that be done programatically. Once all of this is set up, EC2 instance can be set up.

After the EC2 instance is set up on the VPC, we'd want to add the database to it. It shouldn't go to the same public subnet, since we don't want direct access to the DB. That requires another subnet (private), which doesn't have access to the IGW - 10.10.2.0/24.

High availability means moving away from a single AZ. Which means creating 2 new subnets in a different AZ. Once they're created, it's necessary to associate them with the routing table we have. After that we create another EC2 instance and a RDS in the second AZ. Since we have 2 EC instances in 2 subnets, we need an Elastic Load Balancer (ELB). 

To communicate with internal objects, not available over the internet, we'd use Virtual Private Gateway (VGW), which can be associate with private subnets. 

### CIDR

Classless Inter-Domain Routing is notation used for addresses in the VPC. [Article](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing)

### Subnets

[Documentation](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Subnets.html)

### Default VPC

AWS will provide a default VPC with a /16 CIDR block (65,536) addresses plus /20 subnet for each AZ in the region which provides 4,096 addresses per subnet, with a few reserved for AWS use. You can modify or delete the default VPC. [More info](https://docs.aws.amazon.com/vpc/latest/userguide/default-vpc.html)


## Storage

  * S3 is OBJECT level storage
  * RDS is BLOCK level storage

### Amazon Elastic Block Store (Amazon EBS)

Most common block storage. It provides persistent block storage volumes for use with EC2 instances. Each EBS volume is automatically replicated inside of AZ. Main two categories are SDD (DBs and boot volumes, performance depends on IOPS) and HDD volumes (MapReduce, log processing, performance depends on MB/s).

  * [Documentation](https://aws.amazon.com/ebs)
  * [Pricing](https://aws.amazon.com/ebs/pricing/)

## Amazon Simple Storage Service (Amazon S3)

Used for image, file storage, backups, media hosting, etc. 

Objects are stored in "buckets". They are repositories living in a region. Their names must be globally unique across all AWS accounts and must be DNS compliant (b/c objects are accessible over HTTP(s)). Objects can be up to 5TB in size.  

  * [Documentation](https://aws.amazon.com/s3)
  * [Price Calculator](https://calculator.s3.amazonaws.com/index.html)

## Amazon Elastic File System (Amazon EFS)

For a single store of a shared file system for multiple EC2 instances. Designed to be regionally distributed (not in a single subnet). It can connect to instances in different VPCs. Amazon EFS is designed to provide massively parallel shared access to thousands of Amazon EC2 instances.

[Documentation](https://aws.amazon.com/efs/)

