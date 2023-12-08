---
layout: post
title: Cost Efficient VPN in Azure
categories: [Blog, Azure]
tags: [VPN, Azure, Costs]
toc: true
---

# Cost Efficient VPN in Azure 
If you need to support a small or mediaum-sized organisation in Azure, cost is essential.

Microsoft Azure offers a range of Virtual private network (VPN) solutions to securely connect on-premise or remote devices to Azure resources.
In this blog, we'll discuss cost-efficient VPN solutions that fits best with your organisation.

## Types of VPN Solutions
1) *Azure Point-to-Site (P2S) VPN*: This is the simplest and most cost-effective solution for connecting remote devices to Azure resources.    
   P2S VPN uses SSL/TLS to secure the connection, and it can be easily managed using Azure VPN client. 
   The pricing model is based on the number of active clients, making it a cost-effective solution for small-scale deployments.

1) *Azure Site-to-Site (S2S) VPN*: This solution is used for connecting multiple on-premise sites to Azure resources. 
   It uses IPsec to secure the connection and provides a scalable solution for large-scale deployments. The pricing model is based on the number of VPN tunnels and the amount of data transmitted over the VPN.

2) *Azure ExpressRoute*: This is a dedicated, private connection to Azure resources and provides a more secure and reliable alternative to   VPNs. 
   ExpressRoute uses a direct connection to Azure and provides a high-bandwidth, low-latency solution for large-scale deployments. 
   The pricing model is based on the amount of data transmitted over the connection.

## Our choice
It's important to note that there are other factors that can impact the pricing of these VPN solutions, such as the size and type of VPN gateway, the type of ExpressRoute circuit, and the use of any additional features. To get an accurate estimate of the cost for your specific deployment, use the Azure pricing calculator.

For a development environment set up securely, we recommend setting up a P2S VPN solution in Basic SKU. 
This is going to cost the organisation arround €10 / month which is a cheap alternative to still put the resources private in the Azure environment and enabling some security in your development setup.

### High Level Design
![image](https://user-images.githubusercontent.com/78689165/215430980-9bc2c000-3b4a-44e4-8e57-0a3386fa2895.png)

## Conclusion
In conclusion, Azure VPN solutions offer a range of cost-effective solutions to securely connect devices to Azure resources. P2S VPN is the simplest and most cost-effective solution for small-scale deployments, while S2S VPN and ExpressRoute are scalable solutions for large-scale deployments. Choose the solution that fits your specific requirements and budget.

#### *Tip:*
[Azure Caluclator](https://azure.microsoft.com/en-gb/pricing/calculator/?OCID=AIDcmmbnk3rt9z_SEM_9bf430da2ed71bea2f38530dabe722a1%3AG%3As&ef_id=9bf430da2ed71bea2f38530dabe722a1%3AG%3As&msclkid=9bf430da2ed71bea2f38530dabe722a1)
