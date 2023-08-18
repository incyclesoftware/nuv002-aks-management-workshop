# Challenge 8: Workload Troubleshooting

[< Previous Challenge](./07-rbac.md) - **[Home](../README.md)** - [Next Challenge >](./09-image-deprecation.md)

## Introduction
Now that we have a workload running, let's set up some good monitoring, break the application, and figure out how to un-break it!

## Description
- Enable Azure Monitor for Containers (note: May take a few minutes for metrics to start showing up, just wait!)
- Run `template-web-ingress-deploy.yml` in  `Resources/Challenge 8`. Don't peek at the YAML quite yet!
- Your application is broken!
- Use the tools in your diagnostic toolbox to figure out the problem and **fix it!**
    - Some potentially useful commands:
        - `kubectl describe deploy` / `describe pod`
        - `kubectl logs`
        - `kubectl get node`
    - Don't forget that you can look at Container Insights, too!

## Success Criteria
- Azure Monitor for Containers is enabled
- You've corrected the deployment issue with `content-web`