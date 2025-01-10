# Write-up Template

## Analyze, choose, and justify the appropriate resource option for deploying the app.

*For **both** a VM or App Service solution for the CMS app:*
- *Analyze costs, scalability, availability, and workflow*
- *Choose the appropriate solution (VM or App Service) for deploying the app*
- *Justify your choice*

## Introduction
This document presents a comparative analysis of deploying the Udacity CMS project app using either a Virtual Machine (VM) or an App Service solution. It evaluates key factors such as costs, scalability, availability, and deployment workflow for both options. Based on this analysis, a recommendation is made for the most suitable deployment method, with a detailed justification to support the chosen approach.

## Azure Compute Services
Below there is an overview of two important Azure Compute services that Azure provides. We will first sum up the benefits and limitations of boths of the Compute Services, so that we can better justify what the better option is to deploy this application on.

### Azure Virtual Machine
Azure Virtual Machines (IaaS) have the following benetifts:
- VM's can be setup with high availability, scalability and redundancy. Scaling can be done with Scale Sets and Load Balancers.
- VMs can be setup the same way the on-premise hardware was set up. This makes for easy migrations.
- VMs are cheaper to purchase and maintain then physical hardware.
- VMs allow for granular control over the configurations.
- Support for both Linux and Windows VMs.

Azure Virtual Machines can have the below limitations:
- They are more expensive then other Azure Compute Options.
- Setting up and maintaining the VMs are more time consuming.
- Software must be kept up to date for security reasons.

### Azure App Service
Azure App Service (PaaS) have the following benetifts:
- Support of mulitple languages, such as .NET, .NET Core, Java, Ruby, Node.js, PHP or Pyhton
- High availablity, auto-scaling and support of both LInux and Windows envinroments.
- Continuous deployment model using GitHub, Azur DevOps, or any Git repo.
- Possiblity of Vertial and Horizontal scaling.
- The choice of different hardware tiers, which varies in costs.

Azure App Service can have the below limitations:
- Limited access to the host server, so you are unable to control the underlying OS or install software on the server.
- Always paying for the service plan, even if your services or application isn’t running.
- There are hardware limitations, such as a maximum of 14GB of memory and 4 vCPU cores per instance
- Not all programming languages are supported.

## CMS Solution Intent
Below I will go over the infrastructure design choses I've made for the Udacity CMS project. I will do this based on cost analysis, scalability, availability, and workflow. After going over these topics I will choose the best Azure service I see fit. In the [next section](#assess-app-changes-that-would-change-your-decision) I will also go over the design changes I would have made when the Udacity CMS project would have been changes to a real live successful product.

### Cost analysis
As Virtual Machines are always on, even in idle, the price of Azure Virtual Machines are higher for our Udacity CMS project. Especially because the CMS project is not expected to need access to the underling OS, as its a simple project, we are  able to choose for Azure App Service. The CMS itself is also very light weight, somehting that can be easily run within Azure App Serivce.

The Udacity CMS project will not go to production and thus can make use of pre-production workloads. This makes it possible to use the Dev/Test tier, with less hardware allocation, to reduce the cost even more within Azure App Service.

### Scalability
For a small Python-based Udacity CMS application intended solely for showcase purposes, Azure App Service offers better scalability than deploying on an Azure Virtual Machine (VM). While an Azure VM provides more control over the environment, scaling requires manual setup, such as configuring load balancers and managing infrastructure. In contrast, Azure App Service offers built-in auto-scaling, allowing the application to handle varying loads without manual intervention. It supports seamless vertical and horizontal scaling, making it easier to adjust resources based on demand. Since this project is not meant for production and requires minimal maintenance, Azure App Service is the more efficient and scalable solution for demonstration purposes.

### Availablity
When considering availability for this project, Azure App Service is a superior choice compared to an Azure Virtual Machine (VM). Azure App Service provides high availability by default, with features like load balancing, automatic failover, and platform-managed updates, ensuring minimal downtime. In contrast, Azure VMs require manual configuration for high availability, including setting up redundant instances, configuring availability sets, and managing updates. For a showcase application, maintaining consistent uptime with minimal administrative effort is crucial, making Azure App Service the better option for ensuring reliable availability.

### Conclusion
After evaluating cost, scalability, and availability, Azure App Service is clearly the better choice for deploying the Udacity CMS project. The lower costs associated with App Service, especially when using Dev/Test tiers, make it more suitable for a lightweight, non-production showcase application. Additionally, App Service’s built-in auto-scaling and high availability features reduce the need for manual configuration, making it a more efficient solution. Given that the project does not require extensive infrastructure control or access to the underlying operating system, Azure App Service provides a cost-effective, scalable, and highly available platform that meets all the needs of this demonstration project.

## Assess app changes that would change your decision.
If the Udacity CMS project moves to production with increasing traffic, Azure App Service would still be suitable for small to medium-sized applications that prioritize ease of management and built-in scalability. However, for large-scale, high-traffic production environments requiring custom scaling, advanced availability, security, and flexibility, Azure Virtual Machines (or Azure Kubernetes Service) would be a more robust solution. Its hard to say how the infrasctructure will change as it depends on the complexity of the application, traffic growth expectations, and required control over the infrastructure.

## Resources
[Microsoft Learn](https://learn.microsoft.com)

[Udacity - Cloud Developer using Microsoft Azure](https://learn.udacity.com/nanodegrees/nd081/)