# Week 4 - Monitoring and Scaling

Modern applications are often modular, folowing service-oriented or microservices architecture. It's important to have insight into current state of infrastructure and applications. 

## Monitoring and Amazon CloudWatch

It allows creating alarms based on load, which can launch auto-scaling. It's a monitoring service, which can be used to collect and track metrics, collect and monitor log files, set alarms and automatically react to changes in AWS resources. 

CloudWatch events are near real-time stream of system events describing changes in AWS resources. With simple rules, they can match events and route them to target functions or streams. 

CloudWatch logs allow monitoring, storing and access to log files from Amazon EC2 instances, AWS CloudTrail, Amazon Route 53, and other sources. Monitoring of metrics is done by installing the CloudWatch Agent on the server. It can also be installed on on-premises Linux or Windows servers.

  * [CloudWatch](https://aws.amazon.com/cloudwatch/)
  * [CloudWatch Events](https://docs.aws.amazon.com/AmazonCloudWatch/latest/events/WhatIsCloudWatchEvents.html)
  * [CloudWatch Logs](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/WhatIsCloudWatchLogs.html)


## Load Balancing

Elastic Load Balancing, ELB, is a regional service, launched inside the VPC. It can perform network load balancing or application load balancing, on the parts of the application. It can also be used internally, like between a fleet of web servers and the application tier. 

It can handle traffic within one or more AZs. It offers three types of load balancers:

  1. Application Load Balancer; operates on request level (Layer 7), routing traffic to targets, like EC2 instances, microservices and containers within VPC, based on the content of the request. Ideal for advanced load balancing of HTTP(s) traffic.

  2. Network Load Balancer; operates at connection level (Layer 4), routing connection to targets like EC2 instances, microservices and containers within VPC, based on IP protocol data. Ideal for load balancing TCP traffic.

  3. Classic Load Balancer operates both on connection and request level, and provides load balancing between multiple EC2 instances.

[Documentation](https://aws.amazon.com/elasticloadbalancing/) 


## Auto Scaling 

Allows for automatic scaling of the EC2 instance capacity and availability. The scaling is based on the conditions defined (e.g. CPU utilization over 60%). It can increase the number of EC2 instances during spikes, and decrease over lull times.
