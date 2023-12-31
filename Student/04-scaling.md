# Challenge 4: Scaling and High Availability

[< Previous Challenge](./03-nodepools.md) - **[Home](../README.md)** - [Next Challenge >](./05-node-patching.md)

## Introduction

Now that you have your application running there are a few things to consider. How do you make it responsive? How do you make it resilient? How do you control costs while mananging load? In this challenge, we'll find that out.

## Description

In this challenge we will cover scale and resiliency from multiple aspects. We'll make sure enough replicas of our container are running to handle load. We'll make sure that there are enough resources in our cluster to handle all the containers we want to run and we'll figure out how Kubernetes repairs itself.

**Note** All node operations in this exercise should be performed against your user node pool, not your system node pool.

- Scale the nodes in the AKS cluster from 3 to 1.  Make sure you watch the pods after you perform the scale operation.  You can use an Azure CLI command like the following to do this:

**`az aks nodepool scale --resource-group wth-rg01-poc --cluster-name wth-aks01-poc --name userpool --node-count 1`**


- Scale the **Web** app to 2 instances
	- This should be done by modifying the YAML file for the Web app and re-deploying it or by using the `kubectl scale` command
- Scale the **API** app to 4 instances using the same technique as above.  
- Watch events using kubectl with its special watch option (the docs are your friend!).
	- You will find an error occurs because the cluster does not have enough resources to support that many instances.
	- There are three ways to fix this: increase the size of your cluster, decrease the resources needed by the deployments or deploy the cluster autoscaler to your cluster.  
- To fully deploy the application, you will need 4 instances of the API app running and 2 instances of the Web app. 
	- Hint: If you fixed the issue above correctly (look at pod resource request!), you should be able to do this with the resources of your original cluster.

- Enable autoscaling from 1 to 3 nodes.
**`az aks nodepool update --resource-group wth-rg01-poc --cluster-name wth-aks01-poc --name userpool --enable-cluster-autoscaler --min-count 1 --max-count 3`**

- When your cluster is fully deployed, browse to the “/stats.html” page of the web application.
	- Keep refreshing to see the API app’s host name keep changing between the deployed instances.
- Scale the API app back down to 1, and immediately keep refreshing the `/stats.html` page.
	- You will notice that without any downtime it now directs traffic only to the single instance left.

## Success Criteria

1. You can scale your cluster down to 1 node.
1. Run 2 replicas of content-web.
1. Run 4 replicas of content-api.
1. Fix the resource issues.
1. Enable autoscaling on your user nodepool