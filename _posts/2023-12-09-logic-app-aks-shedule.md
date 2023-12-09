---
layout: post
author: Jeroen
title: Schedule AKS clusters to run during Business Hours
categories: [Blog, Azure]
tags: [AKS, Azure, Costs]
toc: true
---

## Introduction
In the dynamic landscape of cloud computing, optimizing costs is a crucial aspect of managing resources effeciently.  
Microsoft Azure Kubernetes Services (AKS) is a powerful platform for deploying, managing, and scaling containerized applications.   
While AKS provides flexibility and scalability, it's equally important for organizations to adopt cost-saving measures.   
One effective strategy is shutting down and starting AKS clusters during business hours.  

In this blog post, I will explore the benefits of shutting down AKS clusters in Azure to save costs on an authomatic approach.  
I will use a low code Logic App approach to shutdown and startup the AKS clusters flagged by a specific tag.

> This article can save you costs when running a couple of AKS clusters.
{: .prompt-tip }

## Starting with the start of a cluster
1. Creating a Logic App like I did in my Azure environment **(comsumption based)**   
   ![img-description](/assets/img/blogs/logic-app-1.png) 

2. Adding the tag to the AKS Cluster   
   
   ![img-description](/assets/img/blogs/aks-tagging.png)

3. Starting with the creationg of the flow in the Logic App.

### Starting with Flow to start the AKS cluster
Adding some reccurence action to the logic app to make sure it will start before business hours.  

1. Start with a schedule action and list all the resources from a subscription   

![step 1 for Logic App Flow](assets/img/blogs/la-step-1.png)

2. Extract the correct tags from the payload
  ``` json
  {
    "items": {
        "properties": {
            "id": {
                "type": "string"
            },
            "identity": {
                "properties": {
                    "principalId": {
                        "type": "string"
                    },
                    "tenantId": {
                        "type": "string"
                    },
                    "type": {
                        "type": "string"
                    }
                },
                "type": "object"
            },
            "location": {
                "type": "string"
            },
            "name": {
                "type": "string"
            },
            "tags": {
                "properties": {
                    "Hours": {
                        "type": "string"
                    }
                },
                "type": "object"
            },
            "type": {
                "type": "string"
            }
        },
        "required": [
            "id",
            "name",
            "type",
            "location",
            "identity",
            "tags"
        ],
        "type": "object"
    },
    "type": "array"
}
  ```

![step 1 for Logic App Flow](/assets/img/blogs/la-step-2.png)


3. Now, we got all the resources that are tagged with Business, so they need to run only during business hours.  
   Let's start these AKS clusters with a Foreach.  

![Last step from the flow](/assets/img/blogs/la-step-3.png)

Here you can find the code for the split function!
```
split(outputs('Get_resource_Id'),'/')[4]
```


## Shutdown a AKS cluster after Business Hours
For the shutdown it's the same flow only the last part is different.   

![Shutdown a cluster](/assets/img/blogs/la-step-4.png)


## Conlusion
In the shift to the cloud cost optimization remains a top priority for organizations leveraging services like Azure Kubernetes Service.   
Shutting down AKS clusters during idle periods is a practical and effective strategy to reducing costs, aligning expenses with actual usage, and maintaining a secure and efficient cloud environment. 

Happy Cloud! :) 

P.S If you want receive the ARM template form the flows, just send me an e-mail ;)
