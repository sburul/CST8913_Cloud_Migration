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
AWS Lambda: Hosts the API in containers or serverless functions for auto-scaling.
AWS Elastic Load Balancer was used to control the load distribution of incoming requests.
A three-tier architecture was planned, and the front-end, back-end, and database layers were offered in three different tiers.
Each of these layers has been created as an auto-scaling group, creating an architecture that can be scaled up and down according to the current demand.
A different passive region was created for the disaster scenario and database replication working with an asynchronous structure was made ready. With database replication, RDS in the active region continuously updates the database in the Disaster region. Route 53 directs incoming traffic to the disaster region in any disaster, ensuring system availability.


### Migration Process

#### 1. Pre-Migration Planning

The existing infrastructure is examined, requirements are determined, configurations are planned, performance measurements are completed and the existing application and infrastructure are evaluated comprehensively.Additionally, it’s essential to identify potential risks and challenges associated with the migration, such as downtime and data integrity issues.

#### 2. Setup Cloud Environment

When planning a cloud infrastructure, establishing a robust cloud infrastructure specifically designed for e-commerce applications is a priority. The necessary IAM roles and policies must be defined to manage access permissions for services that will be used in the cloud infrastructure. Resources such as Amazon S3 for static assets, Amazon RDS for the database, and Elastic Load Balancers for traffic distribution must be provisioned and configured according to best practices. A different region is created for the disaster scenario and the replica of the system is kept in this region. In case of any disaster, the system is routed to the disaster region using AWS Route 53.

#### 3. Data Migration

Data migration is critical in projects with high service availability, such as e-commerce applications.During database transfer, SQL database transfer can be performed without interruption by using AWS Database Migration Service. In addition, database consistency is tested after the migration is completed.

#### 4. Application Layer Migration

In application layer migration, the frontend is migrated to the Amazon S3 service. The AWS Lamda service to be used for the backend is configured according to the application architecture and the application is migrated to this service. In addition, the auto-scaling feature is activated and the service is scaled according to the incoming demand. Comprehensive testing will be performed to validate functionality, performance, and integration with the new architecture, ensuring a smooth user experience post-migration.

#### 5. Testing

The Testing phase is essential to ensure that the migrated eCommerce application functions correctly and meets performance expectations in the cloud-native environment. 
Integration tests, unit tests and user acceptance tests, which are among the test methodologies and enable end-to-end testing of the system, are performed.
Additionally, load tests are performed to check the performance of the system under user traffic.
All errors and problems identified during comprehensive tests will be documented and used during system aenhancement and improvement.

#### 6. Rollback Strategy

If any issues occur during migration, a rollback strategy will be implemented to quickly revert to the previous database state, preserving the performance and reliability of the application.





