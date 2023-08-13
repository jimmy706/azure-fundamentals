Before beginning your cloud journey, the first thing you should do is to understand why you want to migrate to the cloud. Ask yourself how you want to use the cloud and what role is it going to play in your IT strategy. Cutting costs, even though it is important for any IT leader, should not be your main motivation, but flexibility, scalability and agility are.
# Step 1: Assess your environment and cloud readiness
Firstly, you should start by discussing migration project with relevant stakeholders and calculating the Total Cost of Ownership (TCO) of current infrastructure and identifying the workloads.
Azure will help you boost productivity and better manage your costs but not every workload and application in your current infrastructure is a good candidate for the cloud. Indeed, some legacy applications may not be able to run on Azure as an IaaS model and in some cases, you may need to refactor, rearchitect or even rebuild some applications from scratch using cloud-native technologies. This can lead to significant development costs that need to be taken into consideration.

### Key areas to consider during assessment for Azure cloud computing:
- **Virtual Networks**: Investigate creating Virtual Network to keep the same security level, performance and satiability you have on your on-prem datacenter. Especially check how many subnets you will need and which Azure service you choice to manage networking: via Active Directory or Azure DNS Service.
- **Storage:** Review Azure storage services to get insight of how much storages you will need, number of operations and also the nature of data: standard vs premium, [[Describe Azure storage services#Blob storage tiers| hot vs cold]].
- **Scalability:** In order to meet your evolving performance, consider to take a look into Azure Autoscale which you can use to configure for dynamically scale based on your requirements.
# Step 2: Define for your migration strategy
You can follow these common migration strategies:
## Rehost
This strategy is also called “Lift and Shift” and is the most common approach when migrating to the cloud. It involves replicating on-premise environments as closely as possible in the cloud. Physical and Virtual Machines can be migrated to Azure in real time using Azure Site recovery. This same technology can be used for disaster recovery purposes.
## Revise
You application might not need to be completely re-designed to align with Azure. Usually, some elements might just need some linear upgrades such as Microsoft SQL to Azure SQL or Office 365 identity management to Azure Active Directory. You will need to identify the areas needing partial configuration changes in order to save time and money. Checking Azure Migration Guide for best fit your application guideline.
## Refactor
This strategy is also known as “Rearchitecting” and it means that you will restructure your applications as “cloud native” to enable them to align with Azure and become highly available and scalable. The Azure App Services helps you quickly build, deploy and scale web apps and APIs on a fully managed platform. Re-use existing code where applicable and take
advantage of PaaS services when possible.
## Rebuild
This approach entails that you build your application from scratch and that you have an exhaustive knowledge of the existing application processes and functionality as well as the cloud services. By rebuilding your application in the cloud you can take advantage of the native PaaS services such as App Services, Azure SQL, Load Balancers, Applications Gateways, etc. This gives you complete control and flexibility of your application and allowing it to scale instantly at all layers.
# Step 3: Establish cloud KPIs
When planning a migration, it is important to ensure that the cloud will be a valuable asset to your business. To do so, you need to establish performance metrics to measure how it is performing against your expectations. You may already have defined performance metrics for your current applications and services, but will they be as relevant once they’re in the cloud?
![[cloud_kpis_terms.png]]