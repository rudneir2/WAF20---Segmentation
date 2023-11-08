# WAF20 - Segmentation

**NOTE:** 
This content below is supposed to be part of the WAF 20 document, to be embedded in the chapter "WAF > Recommendations > SE:04 Segmentation".

https://review.learn.microsoft.com/en-us/azure/well-architected/security/segmentation?branch=release-waf-2-0-1

## Introduction / Use case

Well-architected framework recommendations for **Segmentation** provide best practices to a different level of isolation, which could be in the level of your Tenant, subscription, or even your workload.
The diagram below will help you understand how a segmentation strategy may help your company to build a more secure environment, based on a common IT environment.

### Tenant and Subscription segmentation level

Let's start with a simple diagram from the subscription level.

![image](https://github.com/rudneir2/WAF20---Segmentation/assets/97529152/3ad84105-cc17-4dbe-855a-555956cd3775)

Let's consider the following in the image above:

1. Azure Subscription, as Office 365 services, Microsoft 365 Defender, and Purview Compliance, all rely on Azure Active Directory (now called Entra ID) for authentication. This may be considered the highest level of isolation you may build in your environment, as this would allow you to segment your environment based on identities (users and groups). So, you may build your Azure environment based on different Tenants (Entra ID), such as the Production environment and the Development environment.

2. as part of your Entra ID, as mentioned above, we have Azure subscriptions. Those subscriptions may be grouped (segmented) by "Management Groups", which will allow you to set different RBAC (Role Based Access Controls) and permissions to different groups of subscriptions.

3. finally, Azure subscription may also allow you to segment environments or workloads, in different ways, by isolating production and development environments, as a simple example, or isolating different types of workloads in different subscriptions.

4. inside a single subscription, you may still consider "Resource Groups", a logical container that holds your Azure resources, such as VMs, Storages, databases, apps, etc. Resource Groups offer a good level of isolation.

So, you may think of a hierarchical level of segmentation like that: Tenant > Management Groups > Subscription > Resource Group, in which you may apply different permissions and levels of isolation.

### Network, Identity, and workload segmentation level

The next diagram shows in detail another level of segmentation that may be applied to your environment. Let's consider the following in the image below:

![image](https://github.com/rudneir2/WAF20---Segmentation/assets/97529152/43b20cc1-71b1-4a04-baab-d1e5af64bd61)

1. different "personas" with different roles may access your IT environment at different levels or resources. In this simple example, we show a user accessing Azure resources through a Security VNET, which could be through an Azure Firewall or an Application Gateway service that contains a Web Application Firewall, then reaching other resources connected to that Security VNET such as a VM or Web App. Any of those users may become a potential threat to your environment.

2. isolation may be created at the network level in different ways, in which you may build a hub-spoke network topology to isolate your workloads in VNETs and subnets, referred to as "spoke" VNETs, protected by the Security VNET, also referred as "hub" VNET. Any type of access would start from those Security VNETs, so your workload would never be exposed to the internet or to direct access.

3. another level of network segmentation may be reached by using the "Application Security Group", which is part of the Network Security Groups (NSG), and allows you to tag different VMs in different subnets to isolate them as groups of resources. Those groups may refer to a specific workload or solution, delivering what usually is called micro-segmentation.

4. related to identity, Entra ID allows you to work with RBAC (Role Based Access Control), which offer isolation at the identity level. RBAC has different roles that may be applied to different users or groups, then based on the role and group of users defined, you then apply it to the level of resource that you need. It may be applied to the subscription level, resource group level, or directly to the resource, hierarchically.


**NOTE:**
If you'd like to understand more about any solution described in the diagram, including acronyms, please refer to this table of contents, from the **Baseline chapter**.
(table to be built)

**This content above is intended to be embedded with current WAF 20 draft content, in the time of this writing (Nov, 2023), still in development**










