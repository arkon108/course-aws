# Week 1 - Introduction, Infrastructure & Compute

## AWS account

  * [Getting Started](https://aws.amazon.com/getting-started/)
  * [Console](https://console.aws.amazon.com/console/home)
  * [Launch a Cloud Server](https://lightsail.aws.amazon.com/ls/webapp)

## AWS Overview

### What is AWS Cloud?

It's an on-demand, pay-as-you go, IT services, delivered over the Internet.


### Six Advantages and Benefits of Cloud Computing

  * Trade capital expenses for variable expense
  * Benefit from massive economies of scale
  * Stop guessing capacity
  * Increase speed and agility
  * Stop spending money on running and maintaining data centers
  * Go global in minutes

Additional information about [what is cloud computing](https://aws.amazon.com/what-is-cloud-computing/). 


### Deployment models

For some customers, it makes more sense to keep some of application on-premises (in their own infrastructure), while deploying others in the cloud. Over time, they might migrate more of their infrastructure with eventually reaching all-in-the-cloud deployment.

[More details](https://aws.amazon.com/types-of-cloud-computing/).


### Products

With over 150 products and services offered by AWS, they cover areas like compute, storage, IoT, security, databases, analytics, networking, mobile, developer tools, management tools and enterprise applications.

The [comprehensive list of products](https://aws.amazon.com/products/).


### AWS Partner Network

Read [more](https://aws.amazon.com/partners/).


### AWS Marketplace 

Is a digital catalog with thousands of software listings from independent software vendors. It offers testing, buying and deploying software on AWS. 

More info on [AWS Marketplace](https://aws.amazon.com/marketplace).


## AWS Infrastructure

How does AWS deploy it's services regionally? The region is a geographically self-contained area which contains all the necessary resources. It's inside a single country boundary, within a single set of laws. 

Every region is designed to be self-contained, with all the assets needed to run my application. To answer which region is appropriate for my app, there are four considerations:

  1. Latency - where are the customers located? 
  2. Cost - not every region is priced the same. Because of different tax laws in different countries. 
  3. Compliance - legal restrictions. Eg. HIPAA or GDPR requirements. 
  4. Service availability - when a brand new feature gets released, it might take a few months to get all the regions around the world.

### What is a region actually made of? 

AWS region is a collection of availability zones. You can think of it like a standalone data center (even though might be multiple data centers). 

Inside a region, there's at least two availability zones, separated by a distance, connected with a high-speed fiber network. It's for redundancy and reliability purposes. 

AWS [global infrastructure](https://aws.amazon.com/about-aws/global-infrastructure/)


## Compute

Sample aplication is a corporate directory application, which will serve to demonstrate how different AWS services can work together to build an application. 

### Sample app structure

--traffic--> Elastic Load Balancer (ELB)----> Elastic Compute Cloud (EC2) instances
                                                    |    |    |   
                                                    |    |    V
                                                    |    V  DynamoDB
                                                    V   Relational Database Service (RDS)
                                                 Simple Storage Service (S3)


### Introduction to Compute Services on AWS

Usually, after estimating the compute capacity needed for our app, we'd buy the hardware to support that capacity and deploy our app on them. After deployment, it's necessary to maintain the servers, both physically and sofware-wise. 

With cloud services, it's possible to use compute-as-service model. That way it's possible to provision and consume raw compute or server capacity with pay-as-you go pricing. Which eliminates the need to maintain the machines. 

The advantage of compute-as-a-service is the fact that it's easier to increase or decrease the capacity, eliminitating the risk in underprovisioning or overprovisioning the resources. 

AWS offers

  * container services, allowing to use Docker through Elastic Container Service (ECS)
  * Kubernetes (EKS)
  * pure serverless solutions - AWS Lambda

Details about the full range of [AWS compute services](https://aws.amazon.com/products/compute/).


### Amazon Elastic Compute Cloud (EC2)

Allows for provisioning of virtual servers on-demand. Each server is called an EC2 instance. 

When setting up an instance, I choose an Amazon Machine Image (AMI), e.g. Linux, Windows. It contains information how the instance needs to be configured, with OS and other software. 

[Features and Cost of EC2](https://aws.amazon.com/ec2/).

### EC2 Instance Types

A wide selection of instance types is optimized for different use cases, with varying combinations of CPU, memory, storage and networking capacity. Current details about available instances is [here](https://aws.amazon.com/ec2/instance-types/).


## Amazon Lightsail

Simpler than EC2, with a lot of built-in options. For example, running a Wordpress site, e-commerce site (Magneto), Drupal, Joomla, Plesk, etc. Or a developer environment, nginx, node server. 

  * [Launch video](https://www.youtube.com/watch?v=29_LqYnomdg)
  * [Lightsail](https://aws.amazon.com/lightsail/)