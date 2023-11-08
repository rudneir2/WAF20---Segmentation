# WAF20 - Segmentation

**NOTE:** 
This content below is supposed to be part of the WAF 20 document, to be embedded in the chapter "WAF > Recommendations > SE:04 Segmentation".

https://review.learn.microsoft.com/en-us/azure/well-architected/security/segmentation?branch=release-waf-2-0-1

## Introduction / Use case

Well-architected framework recommendations for **Segmentation** provide best practices to a different level of isolation, which could be in the level of your Tenant, subscription, or even your workload.
The diagram below will help you understand how a segmentation strategy may help your company to build a more secure environment, based on a common IT environment.

Let's start with a simple diagram from the subscription level.

![image](https://github.com/rudneir2/WAF20---Segmentation/assets/97529152/3ad84105-cc17-4dbe-855a-555956cd3775)

Let's consider the following in the image above:

1. Azure Subscription, as Office 365 services, Microsoft 365 Defender, and Purview Compliance, all rely on Azure Active Directory (now called Entra ID) for authentication. This may be considered the highest level of isolation you may build in your environment, as this would allow you to segment your environment based on identities (users and groups). So, you may build your Azure environment based on different Tenants (Entra ID), such as the Production environment and the Development environment.
2. as part of your Entra ID, as mentioned above, we have Azure subscriptions. Those subscriptions may be grouped (segmented) by "Management Groups", which will allow you to set different RBAC (Role Based Access Controls) and permissions to different groups of subscriptions.
3. finally, Azure subscription may also allow you to segment environments or workloads, in different ways, by isolating production and development environments, as a simple example, or isolating different types of workloads in different subscriptions.
4. inside a single subscription, you may still consider "Resource Groups", a logical container that holds your Azure resources, such as VMs, Storages, databases, apps, etc. Resource Groups offer a good level of isolation.

So, you may think of a hierarchical level of segmentation like that: Tenant > Management Groups > Subscription > Resource Group, in which you may apply different permissions and levels of isolation.


IMAGE

Let's consider the following in the image above:

1. X
2. X
3. X



**NOTE:**
If you'd like to understand more about any solution described in the diagram, including acronyms, please refer to this table of contents, from the **Baseline chapter**.
(table to be built)

**This content above is intended to be embedded with current WAF 20 draft content, in the time of this writing (Nov, 2023), still in development**










