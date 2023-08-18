# Challenge 2: Your First Deployment

[< Previous Challenge](./01-k8sintro.md) - **[Home](../README.md)** - [Next Challenge >](./03-nodepools.md)

## Introduction

Now the rubber meets the road.... we will be deploying the application to our newly minted cluster and making sure it works as intended. You'll learn about pods, deployments and services, oh my!

## Description

In this challenge we need to get our application up and running in Kubernetes. We will learn about Kubernetes configuration YAML files used to create the various Kubernetes resources that will be needed to run our app. We will give our containers resource limits and open the app up to the outside world so we can test it.

- **NOTE:** Microsoft has staged the FabMedical apps on Docker Hub at these locations:
	- **API app:** whatthehackmsft/content-api
	- **Web app:** whatthehackmsft/content-web
- Create a new namespace named `fabmedical`
- Deploy the **API app** into the `fabmedical` namespace from the command line using kubectl and YAML files:
	- **NOTE:** We have provided YAML files for this exercise in the [Resources](Resources/Challenge%201/) directory.
- Deploy the Web app  into the `fabmedical` namespace from the command line using kubectl and YAML files
	- **NOTE:** We have provided YAML files for this exercise in the [Resources](Resources/Challenge%201/) directory.
	- **NOTE:** Applying your YAML files with kubectl can be done over and over as you update the YAML file. Only the delta will be changed.
	- **NOTE:** The Kubernetes documentation site is your friend. The full YAML specs can be found there: <https://kubernetes.io/docs>
- Find out the External IP that was assigned to your service. You can use kubectl for this.
- Test the application by browsing to the Web app's external IP and port and seeing the front page come up.
	- Ensure that you see a list of both speakers and sessions on their respective pages.
	- If you don't see the lists, then the web app is not able to communicate with the API app.

## Success Criteria

1. You have the **content-api** container image deployed and can get data from the `/speakers` endpoint.
1. You have the **content-web** container deployed and can access its page from the open internet.
1. The `/speakers` and `/sessions` pages display speakers and sessions respectively, not just blank pages.