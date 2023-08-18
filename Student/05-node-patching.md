# Challenge 5: Node Patching

[< Previous Challenge](./04-scaling.md) - **[Home](../README.md)** - [Next Challenge >](./06-networking.md)

## Introduction
Now we need to make sure Kubernetes updates are applied to our cluster on a regular basis. Rather than worrying about doing it ourselves, we can turn on an upgrade policy to handle it for us!

## Description
- Turn on an upgrade policy using the `rapid` channel
- Trigger an update Kubernetes to the cluster-level Kubernetes version (`az aks upgrade --kubernetes-version`)
- Watch the nodes upgrade!


az aks update --resource-group dm-aks-lab-rg --name wth-aks02-poc --auto-upgrade-channel rapid

## Success Criteria
- An upgrade policy is applied to the cluster
- We observe the nodes upgrading (`kubectl get nodes`)