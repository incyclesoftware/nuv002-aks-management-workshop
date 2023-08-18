# Challenge 09: Coach's Guide

[< Previous Challenge](./08-node-patching.md) - **[Home](README.md)** 

## Notes & Guidance

- Create ACR: `az acr create --name dbmacrtest --resource-group dm-aks-lab-rg --sku Premium`
- ACR login: 
    - `az acr login -n dbmacrtest --expose-token`
    - `podman login dbmacrtest.azurecr.io -u 00000000-0000-0000-0000-000000000000 -p <token>`
- Build:
podman build . -t dbmacrtest.azurecr.io/content-web:v1
podman build . -t dbmacrtest.azurecr.io/content-web:v2-pre

az acr config soft-delete update -r dbmacrtest --days 7 --status enabled
Purge: az acr run --registry dbmacrtest --cmd 'acr purge --filter "content-web:.*-pre" --untagged --ago 0m' /d
ev/null