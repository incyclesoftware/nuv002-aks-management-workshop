# Challenge 3: System and User node pools

[< Previous Challenge](./02-k8sdeployment.md) - **[Home](../README.md)** - [Next Challenge >](./04-scaling.md)

## Introduction

Now that you have your application running there are a few things to consider. How do you make it responsive? How do you make it resilient? How do you control costs while mananging load? In this challenge, we'll find that out.

## Description

In this challenge we will add a User and System nodepool to our cluster and delete the existing nodepool

- Create a system nodepool named `systempool` with 3 nodes. Ensure this node pool has the taint `CriticalAddonsOnly=true:NoSchedule` so that only system pods will schedule there.
    - `az aks nodepool add`
- Delete the nodepool `nodepool1`
    - `az aks nodepool delete`

- Create a user nodepool named `userpool` with 3 nodes. This node should have no taints.

### Help
https://learn.microsoft.com/en-us/cli/azure/aks/nodepool?view=azure-cli-latest#az-aks-nodepool-add

## Success Criteria

1. You have two nodepools: `userpool` and `systempool`
2. `userpool` is a user pool and only user workloads are running on it.
    - Note that some system pods run as `DaemonSet`s, meaning a copy of the pod runs on *all* nodes regardless of taints. For example, `kube-proxy` must run on all nodes.
3. `systempool` is a system pool and only system workloads are running on it. System pool nodes should have the appropriate taint on it.