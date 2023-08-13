#azure_management #azure_fundamentals #cost_management 
# Factors that can effect cost in Azure
Azure shifts development costs from the capital expense (CapEx) of building out and maintaining infrastructure and facilities to an operational expense (OpEx) of renting infrastructure as you need it, whether it’s compute, storage, networking, and so on. Here are some factors that can take effect on Azure OpEX:
## Resource Type
A number of factors influence the cost of Azure resources. The type of resources, the settings for the resource, and the Azure region will all have an impact on how much a resource costs. When you provision an Azure resource, Azure creates metered instances for that resource. The meters track the resources' usage and generate a usage record that is used to calculate your bill.
## Consumption
Pay-as-you-go has been a consistent theme throughout, and that’s the cloud payment model where you pay for the resources that you use during a billing cycle. If you use more compute this cycle, you pay more. If you use less in the current cycle, you pay less. It’s a straight forward pricing mechanism that allows for maximum flexibility.
However, Azure also offers the ability to commit to using a set amount of cloud resources in advance and receiving discounts on those “reserved” resources. Many services, including databases, compute, and storage all provide the option to commit to a level of use and receive a discount, in some cases up to 72 percent.
## Maintenance
The flexibility of the cloud makes it possible to rapidly adjust resources based on demand. Using resource groups can help keep all of your resources organized. In order to control costs, it’s important to maintain your cloud environment. For example, every time you provision a VM, additional resources such as storage and networking are also provisioned. If you deprovision the VM, those additional resources may not deprovision at the same time, either intentionally or unintentionally. By keeping an eye on your resources and making sure you’re not keeping around resources that are no longer needed, you can help control cloud costs.
## Geography
When you provision most resources in Azure, you need to define a region where the resource deploys. Azure infrastructure is distributed globally, which enables you to deploy your services centrally or closest to your customers, or something in between. With this global deployment comes global pricing differences. The cost of power, labor, taxes, and fees vary depending on the location. Due to these variations, Azure resources can differ in costs to deploy depending on the region.
## Network Traffic
Bandwidth refers to data moving in and out of Azure datacenters. Some inbound data transfers (data going into Azure datacenters) are free. For outbound data transfers (data leaving Azure datacenters), data transfer pricing is based on [[Core Azure Components#Availability Zones|zones]].
## Subscription types
Some Azure subscription types also include usage allowances, which affect costs.
## Azure Marketplace
Azure Marketplace lets you purchase Azure-based solutions and services from third-party vendors. This could be a server with software preinstalled and configured, or managed network firewall appliances, or connectors to third-party backup services. When you purchase products through Azure Marketplace, you may pay for not only the Azure services that you’re using, but also the services or expertise of the third-party vendor. Billing structures are set by the vendor.
# Compare the Pricing and Total Cost of Ownership Calculator (TCO)
## Pricing Calculator
The pricing calculator is designed to give you an estimated cost for provisioning resources in Azure. You can get an estimate for individual resources, build out a solution, or use an example scenario to see an estimate of the Azure spend. The pricing calculator’s focus is on the cost of provisioned resources in Azure.
## TCO Calculator
The TCO calculator is designed to help you compare the costs for running an on-premises infrastructure compared to an Azure Cloud infrastructure. With the TCO calculator, you enter your current infrastructure configuration, including servers, databases, storage, and outbound network traffic. The TCO calculator then compares the anticipated costs for your current environment with an Azure environment supporting the same infrastructure requirements.

With the TCO calculator, you enter your configuration, add in assumptions like power and IT labor costs, and are presented with an estimation of the cost difference to run the same environment in your current datacenter or in Azure.
# Azure Cost management tool
## What is Cost Management?
Cost Management provides the ability to quickly check Azure resource costs, create alerts based on resource spend, and create budgets that can be used to automate management of resources.
Cost analysis is a subset of Cost Management that provides a quick visual for your Azure costs. Using cost analysis, you can quickly view the total cost in a variety of different ways, including by billing cycle, region, resource, and so on.
![Cost Management](https://learn.microsoft.com/en-us/training/wwl-azure/describe-cost-management-azure/media/cost-analysis-b52dedab.png)
You use cost analysis to explore and analyze your organizational costs. You can view aggregated costs by organization to understand where costs are accrued and to identify spending trends. And you can see accumulated costs over time to estimate monthly, quarterly, or even yearly cost trends against a budget.
## Cost Alert
Cost alerts provide a single location to quickly check on all of the different alert types that may show up in the Cost Management service. The three types of alerts that may show up are:
### Budget Alert
Budget alerts notify you when spending, based on usage or cost, reaches or exceeds the amount defined in the alert condition of the budget. Cost Management budgets are created using the Azure portal or the Azure Consumption API.
### Credit Alert
Credit alerts notify you when your Azure credit monetary commitments are consumed. Monetary commitments are for organizations with Enterprise Agreements (EAs). Credit alerts are generated automatically at 90% and at 100% of your Azure credit balance. Whenever an alert is generated, it's reflected in cost alerts, and in the email sent to the account owners.
### Department spending Quota alert
Department spending quota alerts notify you when department spending reaches a fixed threshold of the quota. Spending quotas are configured in the EA portal. Whenever a threshold is met, it generates an email to department owners, and appears in cost alerts. For example, 50 percent or 75 percent of the quota.
# Purpose of tags in Cost Management
Resource tags are another way to organize resources. Tags provide extra information, or metadata, about your resources. This metadata is useful for:

- **Resource management** Tags enable you to locate and act on resources that are associated with specific workloads, environments, business units, and owners.
- **Cost management and optimization** Tags enable you to group resources so that you can report on costs, allocate internal cost centers, track budgets, and forecast estimated cost.
- **Operations management** Tags enable you to group resources according to how critical their availability is to your business. This grouping helps you formulate service-level agreements (SLAs). An SLA is an uptime or performance guarantee between you and your users.
- **Security** Tags enable you to classify data by its security level, such as public or confidential.
- **Governance and regulatory compliance** Tags enable you to identify resources that align with governance or regulatory compliance requirements, such as ISO 27001. Tags can also be part of your standards enforcement efforts. For example, you might require that all resources be tagged with an owner or department name.
- **Workload optimization and automation** Tags can help you visualize all of the resources that participate in complex deployments. For example, you might tag a resource with its associated workload or application name and use software such as Azure DevOps to perform automated tasks on those resources.
## Manage resource tags
You can use Azure Policy to enforce tagging rules and conventions. For example, you can require that certain tags be added to new resources as they're provisioned. You can also define rules that reapply tags that have been removed. Resources don't inherit tags from subscriptions and resource groups, meaning that you can apply tags at one level and not have those tags automatically show up at a different level, allowing you to create custom tagging schemas that change depending on the level (resource, resource group, subscription, and so on).
