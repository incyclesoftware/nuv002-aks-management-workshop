# Challenge 7: Coach's Guide

[< Previous Challenge](./06-networking.md) - **[Home](README.md)** - [Next Challenge >](./08-workload-troubleshooting.md)

## Notes & Guidance
Get cluster resource ID: az aks show -g dm-aks-lab-rg -n wth-aks02-poc -o json --query id
Get current user ID: az ad signed-in-user show --query id

`az aks update -g dm-aks-lab-rg -n wth-aks02-poc --enable-azure-rbac --enable-aad --disable-local-accounts``

Run `az aks get-credentials -g dm-aks-lab-rg -n wth-aks02-poc`
Try to list pod - failure
Assign self 'Azure Kubernetes Service RBAC Reader'
`az role assignment create --role "Azure Kubernetes Service RBAC Reader" --assignee f11249e1-bcac-49f8-ba36-1f4f75b72064 --scope /subscriptions/34e71616-6e64-4b62-a61b-bb2714cda8c6/resourcegroups/dm-aks-lab-rg/providers/Microsoft.ContainerService/managedClusters/wth-aks02-poc`
Try to get pod - success
Try to delete pod - failure

Assign self 'Azure Kubernetes Service RBAC Cluster Admin'
`az role assignment create --role "Azure Kubernetes Service RBAC Cluster Admin" --assignee f11249e1-bcac-49f8-ba36-1f4f75b72064 --scope /subscriptions/34e71616-6e64-4b62-a61b-bb2714cda8c6/resourcegroups/dm-aks-lab-rg/providers/Microsoft.ContainerService/managedClusters/wth-aks02-poc`

Try to delete pod - success. May take a few minutes for permission to propagate.