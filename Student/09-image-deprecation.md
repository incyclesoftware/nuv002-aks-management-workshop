# Challenge 9: Image Deprecation

[< Previous Challenge](./08-workload-troubleshooting.md) - **[Home](../README.md)** 

## Introduction
Let's look at how to manage deprecating images in a container registry.

## Description
- Create an ACR using the Premium SKU
- Enable soft delete (`az acr config soft-delete update`)
- Log in to the ACR
- Build and tag the sample containers (v1 and v2-pre)
- Push the sample containers to the ACR
- Purge only images containing the text `-pre`

## Success Criteria
- You have created an ACR
- You have pushed images into the ACR
- You have soft-deleted and purged images from the ACR
