#azure_architecture #azure_fundamentals #VMs #containers #azure_functions #azure_app_service #azure_container_instances #azure_virtual_networking
# Azure virtual machine
Virtual machines are [[Basic Concepts of Cloud Computing#IaaS|IaaS]] in the from of virtualized servers that you can customize all the software and OS running on these VMs. 
VMs are an ideal choice when you need:
- Total control over the operating system (OS).
- The ability to run custom software.
- To use custom hosting configurations.
## Scale of VMs in Azure
### VM scale sets
scale sets let you manage group of identical VMs by centrally control them and update or configure in a large pack of VMs within minutes. The number of VM instances can automatically increase or decrease in response to demand, or you can set it to scale based on a defined schedule. Virtual machine scale sets also automatically deploy a load balancer to make sure that your resources are being used efficiently. 
### VM availability sets
Availability sets are designed to ensure that VMs stagger updates and have varied power and network connectivity, preventing you from losing all your VMs with a single network or power failure.

Availability sets do this by grouping VMs in two ways: update domain and fault domain:
- **Updated domain:** The update domain groups VMs that can be rebooted at the same time. This allows you to apply updates while knowing that only one update domain grouping will be offline at a time. All of the machines in one update domain will be updated. An update group going through the update process is given a 30-minute time to recover before maintenance on the next update domain starts.
- **Fault domain:** The fault domain groups your VMs by common power source and network switch. By default, an availability set will split your VMs across up to three fault domains. This helps protect against a physical power or networking failure by having VMs in different fault domain.
# Azure container
Azure Container Instances offer the fastest and simplest way to run a container in Azure; without having to manage any virtual machines or adopt any additional services. Azure Container Instances are a platform as a service (PaaS) offering. Azure Container Instances allow you to upload your containers and then the service will run the containers for you.
# Azure Function
If you build an app using VMs or containers, those resources have to be “running” in order for your app to function. With Azure Functions, an event wakes the function, alleviating the need to keep resources provisioned when there are no events.
## Benefits of using Azure Function
> Using Azure Functions is ideal when you're only concerned about the code running your service and not about the underlying platform or infrastructure.

- Azure Functions runs your code when it's triggered and automatically deallocates resources when the function is finished. -> Pay as you use
- No infrastructure management like: OS, networking,...
- Perform work response to events: through APIs, timer, messaging, etc...
- Automatically scale based on demand
# Azure application hosting with Azure App Service
Azure App Service is HTTP-based service which allows you to host web apps, jobs, backend services in programming language without worrying about underlying infrastructure. It is also supports auto deployment from GitHub, Azure DevOps...
Azure App Service supports multiple languages, including .NET, .NET Core, Java, Ruby, Node.js, PHP, or Python. It also supports both Windows and Linux environments.
# Azure Virtual Networking
AZ Virtual Networks and subnets enable Azure resources communicate with each other, with users on internet and organization's on-premises computer.
Key capabilities of AZ Virtual Networking:
- Isolation and segmentation
- Internet communications
- Communicate between Azure resources
- Communicate with on-premises resources
- Route network traffic
- Filter network traffic
- Connect virtual networks
## Internet communications
Incoming internet connections can be achieved by assigning public IP addresses to AZ resources or using public load balancer.
## Azure resource communications
You can create a network to link resources inside your on-prem environment and within Azure subscription through these three mechanisms: 
1. Point-to-site: the client computer initiates an encrypted VPN connection to connect to the Azure virtual network.
2. Site-to-site: link your on-premises VPN device or gateway to the Azure VPN gateway in a virtual network.
3. Azure ExpressRoute: provides a dedicated private connectivity to Azure that doesn't travel over the internet. This is useful for environments where you need greater bandwidth and even higher levels of security.
## Route network traffic
By default, Azure routes traffic between subnets on any connected virtual networks, on-premises networks, and the internet. You also can control routing and override those settings, as follows:

- Route tables allow you to define rules about how traffic should be directed. You can create custom route tables that control how packets are routed between subnets.
- Border Gateway Protocol (BGP) works with Azure VPN gateways, Azure Route Server, or Azure ExpressRoute to propagate on-premises BGP routes to Azure virtual networks.
## Filter network traffic
Azure virtual networks enable you to filter traffic between subnets by using the following approaches:

- Network security groups are Azure resources that can contain multiple inbound and outbound security rules. You can define these rules to allow or block traffic, based on factors such as source and destination IP address, port, and protocol.
- Network virtual appliances are specialized VMs that can be compared to a hardened network appliance. A network virtual appliance carries out a particular network function, such as running a firewall or performing wide area network (WAN) optimization.
## Connecting virtual networks
You can link virtual networks together by using virtual network peering. Peering allows two virtual networks to connect directly to each other. Network traffic between peered networks is private, and travels on the Microsoft backbone network, never entering the public internet.
# Azure Virtual Private Networks
A virtual private network (VPN) uses an encrypted tunnel within another network. VPNs are typically deployed to connect two or more trusted private networks to one another over an untrusted network (typically the public internet). Traffic is encrypted while traveling over the untrusted network to prevent eavesdropping or other attacks. VPNs can enable networks to safely and securely share sensitive information.
## VPN gateways
VPN gateway is a type of virtual network gateway its instances is deployed in a dedicated subnet of virtual network and allows following connectivity:
- On-prem connect through site-to-site
- Individual devices connect through point-to-site
- Virtual network connections through network-to-network
You can deploy only one VPN gateway in each virtual network. However, you can use one gateway to connect to multiple locations, which includes other virtual networks or on-premises datacenters. When you deploy a VPN gateway, specification for the VPN type must be defined:
- Policy-based: VPN gateways specify statically the IP address of packets that should be encrypted through each tunnel. This type of device evaluates every data packet against those sets of IP addresses to choose the tunnel where that packet is going to be sent through.
- In Routed-Based: IPSec tunnels are modeled as a network interface or virtual tunnel interface. IP routing (either static routes or dynamic routing protocols) decides which one of these tunnel interfaces to use when sending each packet.
## High-availability VPN
There are a few ways to maximize the resiliency of your VPN gateway:
### Active/standby
By default, VPN gateways are deployed as two instances in an active/standby configuration, even if you only see one VPN gateway resource in Azure. When planned maintenance or unplanned disruption affects the active instance, the standby instance automatically assumes responsibility for connections without any user intervention.
### Active/active
In this configuration, you assign a unique public IP address to each instance. You then create separate tunnels from the on-premises device to each IP address. You can extend the high availability by deploying an additional VPN device on-premises.
### ExpressRoute failover
ExpressRoute circuits have resiliency built in. However, they aren't immune to physical problems that affect the cables delivering connectivity or outages that affect the complete ExpressRoute location. In high-availability scenarios, where there's risk associated with an outage of an ExpressRoute circuit, you can also provision a VPN gateway that uses the internet as an alternative method of connectivity. In this way, you can ensure there's always a connection to the virtual networks.
### Zone-redundant gateways
In regions that support availability zones, VPN gateways and ExpressRoute gateways can be deployed in a zone-redundant configuration. This configuration brings resiliency, scalability, and higher availability to virtual network gateways. Deploying gateways in Azure availability zones physically and logically separates gateways within a region while protecting your on-premises network connectivity to Azure from zone-level failures.
# Azure ExpressRoute
This allows you to **extends your current on-prem networks into cloud Microsoft provider** through using private connection called *ExpressRoute Circuit*. Through this, your on-prem networks can established connection to MS Azure and MS 365.
> With ExpressRoute, your data doesn't travel over the public internet, so it's not exposed to the potential risks associated with internet communications. ExpressRoute is a private connection from your on-premises infrastructure to your Azure infrastructure. Even if you have an ExpressRoute connection, DNS queries, certificate revocation list checking, and Azure Content Delivery Network requests are still sent over the public internet.
## Benefits of using ExpressRoute
- Connectivity to Microsoft cloud services across all regions in the geopolitical region.
- Global connectivity to Microsoft services across all regions with the ExpressRoute Global Reach.
- Dynamic routing between your network and Microsoft via Border Gateway Protocol (BGP).
- Built-in redundancy in every peering location for higher reliability.
## Global connectivity
Through *ExpressRoute Global Reach* you can exchange data across on-prem sites. For example, say you had an office in Asia and a datacenter in Europe, both with ExpressRoute circuits connecting them to the Microsoft network. You could use ExpressRoute Global Reach to connect those two facilities, allowing them to communicate without transferring data over the public internet.
## ExpressRoute connectivity models
- CloudExchange colocation
- Point-to-point Ethernet connection
- Any-to-any connection
- Directly from ExpressRoute sites
# Azure DNS
Azure DNS is a hosting service for DNS domains that provides name resolution by using Microsoft Azure infrastructure. By hosting your domains in Azure, you can manage your DNS records using the same credentials, APIs, tools, and billing as your other Azure services.
## Benefits of using Azure DNS
### Reliability
DNS domains in Azure DNS are hosted on Azure's global network of DNS name servers, providing resiliency and high availability.
### Security
Azure DNS is based on Azure Resource Manager, which provides features such as:

- Azure role-based access control (Azure RBAC) to control who has access to specific actions for your organization.
- Activity logs to monitor how a user in your organization modified a resource or to find an error when troubleshooting.
- Resource locking to lock a subscription, resource group, or resource. Locking prevents other users in your organization from accidentally deleting or modifying critical resources.
### Ease of use
Azure DNS can manage DNS records for your Azure services and provide DNS for your external resources as well. Azure DNS is integrated in the Azure portal and uses the same credentials, support contract, and billing as your other Azure services.
### Customizable virtual networks with private domains
Azure DNS also supports private DNS domains. This feature allows you to use your own custom domain names in your private virtual networks, rather than being stuck with the Azure-provided names.
### Alias records
Azure DNS also supports alias record sets. You can use an alias record set to refer to an Azure resource, such as an Azure public IP address, an Azure Traffic Manager profile, or an Azure Content Delivery Network (CDN) endpoint. If the IP address of the underlying resource changes, the alias record set seamlessly updates itself during DNS resolution. The alias record set points to the service instance, and the service instance is associated with an IP address.