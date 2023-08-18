# Challenge 4: Coach's Guide

[< Previous Challenge](./01-k8sintro.md) - **[Home](README.md)** - [Next Challenge >](./03-rbac.md)

## Notes & Guidance
- Coaches should be familiar with common kubectl commands in order to help the students troublshoot:
	- `kubectl get nodes`
	- `kubectl get pods`
	- `kubectl describe pod <pod-name>`
	- `kubectl get services`
	- `kubectl get deployments`
	- `kubectl delete deployment <deployment-name>`
	- `kubectl delete pod <pod-name>`
  	- `kubectl delete service <service-name>`
	- `kubectl apply -f <yaml-file>`
- When the service is deployed it will take some time for an External IP to be assigned.
	- Issue the following kubectl command and look in the **EXTERNAL-IP** column
		- `kubectl get services`
	- You will see `<pending>` if the IP hasn’t yet been assigned.
- To verify that the API app is correctly deployed the students need to:
	- Figure out the name of the pod the API app was deployed to, eg: 	
    	- `content-api-23aceed`
	- Then use a kubectl command like this to get a bash shell:
		- `kubectl exec -it content-api-23aceed -- /bin/bash`
	- To verify the API app is working you need to curl the /speakers endpoint:
		- `curl http://localhost:3001/speakers`
    - They should see a huge JSON document printed to the screen.

