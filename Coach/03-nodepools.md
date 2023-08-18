# Challenge 3: Coach's Guide

[< Previous Challenge](./02-k8sdeployment.md) - **[Home](README.md)** - [Next Challenge >](./04-scaling.md)

## Notes & Guidance
az aks nodepool add --resource-group dm-aks-lab-rg --cluster-name wth-aks02-poc --name systempool --node-count 3 --mode System --node-taints CriticalAddonsOnly=true:NoSchedule
az aks nodepool delete --resource-group dm-aks-lab-rg --cluster-name wth-aks02-poc --name nodepool1
az aks nodepool add --resource-group dm-aks-lab-rg --cluster-name wth-aks02-poc --name userpool --node-count 3 --mode User

`kubectl get pod -A -o wide` shows what node a pod is on
`kubectl describe nodes` will show taints