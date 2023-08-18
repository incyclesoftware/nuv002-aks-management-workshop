# Challenge 7: Azure AD RBAC

[< Previous Challenge](./06-networking.md) - **[Home](README.md)** - [Next Challenge >](./08-workload-troubleshooting.md)

## Introduction
In this exercise, we will enable Azure AD Authentication and RBAC for our cluster, then assign ourselves a series of roles to see how roles contribute to our ability to interact with the cluster.

## Description
- Start by updating your cluster to use Azure AD for authentication and RBAC, as well as disabling local user accounts. This can be accomplished with `az aks update`. There are three flags you'll need to provide: One disables local user accounts, one enables Azure AD integration, and one enables Azure AD RBAC.
- Once your cluster is updated, delete your `.kube` folder: `rmdir /s %HOMEPATH%\.kube`. **Warning: this will delete credentials for all logged in clusters**
- Log in again with `az aks get-credentials`
- Attempt to list all of the pods in your `fabmedical` namespace. You should be denied.
- Assign yourself the `Azure Kubernetes Service RBAC Reader` role. This is a read-only role.
- Attempt to list all of the pods in your `fabmedical` namespace again. You should see a list of pods. However, if you try to *delete* one of the pods, you should be denied.
- Assign yourself the `Azure Kubernetes Service RBAC Cluster Admin` role. This is an admin role.
- You should now be able to *delete* pods as well as list and create them!

### Useful commands:
- Get cluster resource ID: az aks show -g <Resource Group Name> -n <Cluster Name> -o json --query id
- Get current user ID: az ad signed-in-user show --query id
- Assign RBAC roles: `az role assignment create`

### Notes
It may take a few minutes for role changes to propagate to your cluster!

## Success Criteria
- Your cluster has AAD RBAC enabled
- Local accounts are disabled
- You can log into the cluster
- You can delete pods from the cluster