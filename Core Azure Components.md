#azure_fundamentals
# What is Azure?
Azure is Microsoft cloud computing platform that serves an expanding pack of services which allows your organization meet business requirements.
# Azure infrastructures
The core architectural components of Azure may be broken down into two main groupings: **the physical infrastructure, and the management infrastructure**.
## Physical infrastructures
The physical infrastructure for Azure starts with datacenters. Conceptually, the datacenters are the same as large corporate datacenters. They’re facilities with resources arranged in racks, with dedicated power, cooling, and networking infrastructure.

As a global cloud provider, Azure has datacenters around the world. However, these individual datacenters aren’t directly accessible. Datacenters are grouped into Azure Regions or Azure Availability Zones that are designed to help you achieve resiliency and reliability for your business-critical workloads.
## Regions
A region is a geographical area on the planet that contains at least one, but potentially multiple datacenters that are nearby and networked together with a low-latency network. Azure intelligently assigns and controls the resources within each region to ensure workloads are appropriately balanced.

> When you deploy a resource in Azure, you'll often need to choose the region where you want your resource deployed.
## Availability Zones
Availability zones are physically separate datacenters within an Azure region. Each availability zone is made up of one or more datacenters equipped with independent power, cooling, and networking. An availability zone is set up to be an isolation boundary. If one zone goes down, the other continues working. Availability zones are connected through high-speed, private fiber-optic networks.
![Availability Zones](https://learn.microsoft.com/en-us/training/wwl-azure/describe-core-architectural-components-of-azure/media/availability-zones-c22f95a3.png)
Availability zones are primarily for VMs, managed disks, load balancers, and SQL databases. Azure services that support availability zones fall into three categories:
- **Zonal services**: You pin the resource to a specific zone (for example, VMs, managed disks, IP addresses).
- **Zone-redundant services**: The platform replicates automatically across zones (for example, zone-redundant storage, SQL Database).
- **Non-regional services**: Services are always available from Azure geographies and are resilient to zone-wide outages as well as region-wide outages.
## Regions Pair
Most Azure regions are paired with another region within the same geography (such as US, Europe, or Asia) at least 300 miles away. This approach allows for the replication of resources across a geography that helps reduce the likelihood of interruptions because of events such as natural disasters, civil unrest, power outages, or physical network outages that affect an entire region. For example, if a region in a pair was affected by a natural disaster, services would automatically fail over to the other region in its region pair.
![Regions Pair](https://learn.microsoft.com/en-us/training/wwl-azure/describe-core-architectural-components-of-azure/media/region-pairs-7c495a33.png)

> **Sovereign Regions**: In addition to regular regions, Azure also has sovereign regions. Sovereign regions are instances of Azure that are isolated from the main instance of Azure. You may need to use a sovereign region for compliance or legal purposes.

# Azure management infrastructure

> The management infrastructure includes *Azure resources and resource groups, subscriptions, and accounts.*

## Resources and resource groups
### Azure Resources
 Anything you create, provision, deploy, etc. is a resource. Virtual Machines (VMs), virtual networks, databases, cognitive services, etc. are all considered resources within Azure.
### Azure resource groups

 Resource groups are simply groupings of resources. When you create a resource, you’re required to place it into a resource group. While a resource group can contain many resources, a single resource can only be in one resource group at a time. Some resources may be moved between resource groups, but when you move a resource to a new group, it will no longer be associated with the former group. Additionally, resource groups can't be nested, meaning you can’t put resource group B inside of resource group A.
## Azure subscriptions
Using Azure requires an Azure subscription. A subscription provides you with authenticated and authorized access to Azure products and services. It also allows you to provision resources. An Azure subscription links to an Azure account, which is an identity in Azure Active Directory (Azure AD) or in a directory that Azure AD trusts.

### Multiple subscriptions
An account can have multiple subscriptions, in a multi-subscription account, you can use Azure subscriptions to define boundaries around Azure products, services, and resources. There are two types of subscription boundaries that you can use:

- **Billing boundary**: This subscription type determines how an Azure account is billed for using Azure. You can create multiple subscriptions for different types of billing requirements. Azure generates separate billing reports and invoices for each subscription so that you can organize and manage costs.
- **Access control boundary**: Azure applies access-management policies at the subscription level, and you can create separate subscriptions to reflect different organizational structures. An example is that within a business, you have different departments to which you apply distinct Azure subscription policies. This billing model allows you to manage and control access to the resources that users provision with specific subscriptions.
## Azure management groups
Resources are gathered into resource groups, and resource groups are gathered into subscriptions.
![Management group hierarchy](https://learn.microsoft.com/en-us/training/wwl-azure/describe-core-architectural-components-of-azure/media/management-groups-subscriptions-dfd5a108.png)
