# Lab 04 - Design Rehosting Migration V2

### Instructions

Write a 1-page high-level design (HLD) document for a lift-and-shift migration of the following application.

The application consists of two virtual machines: WebServerVM and SQLVM. For high availability in the cloud, the web server will be containerized using Docker and hosted on Azure Kubernetes Service (AKS), and the SQL database will be migrated to a Managed SQL Database service. The application can handle no more than 6 hours of downtime.

### Solution Diagram

![Solution Diagram](/images/TargetSolutionDiagram.jpg)

### Explanation of the Target Architecture

Azure Kubernetes Service (AKS) is a service that makes it easy to manage Kubernetes on the Microsoft Azure platform. Kubernetes is an open source system for automatically deploying, scaling, and managing containerized applications.

According to the information given in the scenario, the NodeJS application and SQL Server database in VMs will be transferred to the Azure platform by containerizing them to Azure Kubernetes Service using Cluster and the lift and shift methodology.

As shown in the diagram above, the application is containerized with the help of Docker. The distribution process is carried out by dividing the containers into small units with the help of POD. Here, in case of any malfunction that may occur in any POD, Kubernetes creates a new POD to prevent the system from going down.

To ensure the operation and management of the Kubernetes system with the help of the Kubernetes Cluster.

NODs are units running inside the Kubernetes Cluster and provide the CPU and resource requirements for the applications that are maintained. The ability to virtualize these resources on the machine can also be represented on different machines. Having NODs on different machines reduces the risk of system downtime because if one machine is down, the other one remains up.

The SQL database is planned to be rehosted from the VM and migrated to the Managed SQL database in the Azure cloud.

The SQL database running on the VM machine operates with an on-premise approach and uses the resources of the VM it is installed on. With the help of Azure SQL Managed Instance, resource sharing between databases is done easily.

### Containerization of the web application

There are some steps to be followed in the containerization process of the application specified in the scenario. These are listed as follows;

1-Determining the Dependencies of the Application
2-Creating the Docker file  ( Copying App files and uploading dependencies )
3-Creating the Docker Image ( This is a runnable version of the Docker file)
4-Running a Container from the Docker Image 
5-Organization of the Containers (Azure Kubernetes Service)

### Migration of the database to a managed SQL service

In order to migrate a SQL database currently running on a VM machine to an Azure Managed SQL database, some steps need to be followed.
Before migration, requirements need to be determined, such as database workload, size, performance, and availability.
After the requirements are determined, the existing database must be backed up and its suitability for the database to be migrated must be checked, and the network infrastructure to be used in the migration must be prepared.

When the migration phase is reached, the existing database can be moved to Azure Managed SQL Server using Azure Database Migration Service. However, it is also possible to use different methods. For example, the existing database can be exported to a BACPAC file and then imported to Azure Managed SQL Server. Or, the existing database can be replicated to the target database with minimum downtime using the Transactional Replication method.

### Configuration of the Kubernetes cluster for high availability

Deploying an AKS Cluster across multiple Availability Zones helps protect against outages within a region by spreading nodes across different physical locations. At the same time, by using Load Balancer, the workload can be distributed among the application PODs, thus increasing system performance. 
