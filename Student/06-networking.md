# Challenge 6: Networking

[< Previous Challenge](./05-node-patching.md) - **[Home](../README.md)** - [Next Challenge >](./07-rbac.md)

## Introduction

We started out with some very simple, default networking that Kubernetes gives us for free. But this is rarely what we'll need to go into production. Now we'll get a little more in depth on networking in Kubernetes

## Description

In this challenge you will be installing an Ingress Controller and learning how the "Ingress" resource in Kubernetes works. 

- Install the App Gateway ingress controller using the Azure Portal (you can also use the CLI, but it's *much* more complicated!).
	- Creating the app gateway will take a few minutes. Be patient!
- Deploy the content-web service and create an Ingress resource for it. 
	- The reference template can be found in the Challenge 6 Resources folder: `template-web-ingress-deploy.yaml`

- Access the application by the app gateway's IP address (`kubectl get ingress`)

## Success Criteria

1. The App Gateway Ingress Controller is installed in your cluster
2. You've recreated a new Ingress for content-web that allows access through an app gateway IP address
3. You've examined the app gateway's backend configuration to see how the rules changed based on your cluster's configuration