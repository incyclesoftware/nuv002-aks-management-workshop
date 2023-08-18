# Challenge 06: Coach's Guide

[< Previous Challenge](./05-node-patching.md) - **[Home](README.md)** - [Next Challenge >](./07-rbac.md)

## Notes & Guidance

- Make sure that students have a clear picture of what services are and the different types (ClusterIP, LoadBalancer, etc) and how they map to different types of networking.
- The Ingress Controller has many capabilities, students are going to experiment only with its routing capability in this challenge
- Make sure that each student's AKS cluster has the App Gateway Ingress Controller installed. They should eventually find this page that is a step by step walkthrough on installing the App Gateway Ingress Controller on an AKS cluster:
	- <https://learn.microsoft.com/en-us/azure/application-gateway/tutorial-ingress-controller-add-on-existing>
- Refer to the AKS documentation for the verification of logs
- CLI AGW:
az network public-ip create -n dm-aks-agw-pip -g dm-aks-lab-rg --allocation-method Static --sku Standard
az network vnet create -n dm-aks-agw-vnet -g dm-aks-lab-rg --address-prefix 10.0.0.0/16 --subnet-name agw-snet --subnet-prefix 10.0.0.0/24 
az network application-gateway create -n dm-aks-agw -l eastus -g dm-aks-lab-rg --sku Standard_v2 --public-ip-address aks-agw-pip --vnet-name dm-aks-agw-vnet --subnet agw-snet --priority 100

nodeResourceGroup=$(az aks show -n wth-aks02-poc -g dm-aks-lab-rg -o tsv --query "nodeResourceGroup")
aksVnetName=$(az network vnet list -g $nodeResourceGroup -o tsv --query "[0].name")
appGWVnetId=$(az network vnet show -n dm-aks-agw-vnet -g dm-aks-lab-rg -o tsv --query "id")
appgwId=$(az network application-gateway show -n dm-aks-agw -g dm-aks-lab-rg -o tsv --query "id") 

aksVnetId=$(az network vnet show -n $aksVnetName -g $nodeResourceGroup -o tsv --query "id")
az network vnet peering create -n AppGWtoAKSVnetPeering -g dm-aks-lab-rg --vnet-name dm-aks-agw-vnet --remote-vnet $aksVnetId --allow-vnet-access
az network vnet peering create -n AKStoAppGWVnetPeering -g $nodeResourceGroup --vnet-name $aksVnetName --remote-vnet $appGWVnetId --allow-vnet-access
az aks enable-addons -n wth-aks02-poc -g dm-aks-lab-rg -a ingress-appgw --appgw-id $appgwId

RBAC needs to be assigned to AGW as well, check ingress controller error logs for exact commands


az network vnet peering create -n AKStoAppGWVnetPeering -g MC_dm-aks-lab-rg_wth-aks02-poc_eastus --vnet-name aks-vnet-25331608 --remote-vnet /subscriptions/34e71616-6e64-4b62-a61b-bb2714cda8c6/resourceGroups/dm-aks-lab-rg/providers/Microsoft.Network/applicationGateways/dm-aks-agw --allow-vnet-access