# Lab 5 - Design Rehosting migration

### Instructions

Write one page High-Level Design (HLD) document for migrating a 3-tier eCommerce application to a cloud-native architecture.

The application consists of:

A Frontend Web Server running on WebAppVM
A Backend API Server running on APIVM
A SQL Database running on DBVM
The application requires load balancing for the frontend and auto-scaling capabilities for both the API and database tiers. Data consistency is critical, and downtime must not exceed 2 hours.

Insert more technical details of application infrastructure, current configurations, and services

Your HLD should include the following:

A detailed solution diagram showing the cloud-native target architecture (e.g., load balancers, managed databases, autoscaling groups)
A description of how the target architecture addresses scalability, availability, and disaster recovery
A step-by-step breakdown of the migration process, including necessary considerations such as data migration, testing, and rollback strategies
Make sure to leverage resources from AWS or GCP 

### Solution Diagram

![Solution Diagram](/images/TargetSolutionDiagram.jpg)

### Explanation of the Target Architecture

We can plan the migration structure of the frontend, backend and database servers in the virtual machines to the AWS cloud system as seen in the target design diagram. 
We use the Route 53 service, which is one of the AWS services, to direct requests from clients to Active Region.
At the same time, with Route 53, we can direct requests to the disaster region in case of any disaster scenario.
It is designed to use Amazon S3 service on the AWS cloud for on-premise front-end servers.
AWS Elastic Load Balancer was used to control the load distribution of incoming requests.
A three-tier architecture was planned, and the front-end, back-end, and database layers were offered in three different tiers.
Each of these layers has been created as an auto-scaling group, creating an architecture that can be scaled up and down according to the current demand.

### Migration Process


#### 1. Pre-Migration Planning


#### 2. Setup Cloud Environment


#### 3. Data Migration


#### 4. Application Layer Migration


#### 5. Testing






