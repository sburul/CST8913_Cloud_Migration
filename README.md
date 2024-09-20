# IaaS/PaaS Architecture

## Instructions
Scenario: The following application consists of a Web Server written in Flask. A UI front end written in React. A database layer consisting of Postgres.

1. Describe how this application can be deployed in the cloud using IaaS infrastructure
2. Describe how this application can be deployed in the cloud using PaaS infrastructure.
3. For each case, draw a diagram that represents the target architecture and describe each of the chosen cloud components.

### On-Premise Infrastructure

Let's assume that the React and Flask applications specified in the scenario are kept on two servers, frontend and backend. PortgreSQL, which is used as a database, will be kept on a separate server. The request sent to the server with the web browser first reaches the DNS server and then comes to the Web Server, the user encounters the interface prepared with React and thanks to this interface, data operations are performed on the server side with Flask in the background. In this architecture, separate resources are needed for all server, firewall, database, and network operations.

![Application Diagram](/images/OnPremise_Diagram.jpg)

### IaaS infrastructure

If we consider that the application is deployed with the IaaS approach to cloud technology using the Azure infrastructure, we will need some components on the cloud side. Application Gateway will be used to meet and direct requests coming to our application. A Virtual Network structure needs to be established for Frontend, Backend and Database. In addition, these servers are planned to provide service on VMs. Furthermore, using LoadBalancer to share the load on the servers according to the load created by the incoming requests will be appropriate for the architecture.Considering the IaaS approach, it can be seen that concepts such as network, application, database and load distribution, and server are configured by the user in cloud technology.

![Application Diagram](/images/IaaS_Diagram.jpg)

### PaaS infrastructure

When we consider our scenario according to the PaaS approach in cloud technology, it has been observed that no server, network and load balancer, etc related components are used by using Application and Database services on the Azure side.With this approach, it is seen that Azure, the cloud service provider, is responsible for the server, network and etc workloads that occur in the background after the application is developed and deployed.

![Application Diagram](/images/PaaS_Diagram.jpg)