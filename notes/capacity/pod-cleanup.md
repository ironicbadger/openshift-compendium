---
title: Cleanup pods
tags:
  - Openshift 4
  - Admin Tasks
  - Cleanup
  - Capacity
emoji: "\U0001F9F9"
link: 'https://docs.openshift.com/'
created: 2020-06-14T04:06:39.000Z
modified: 2020-11-19T16:53:02.000Z
---

## Delete all 'Completed' pods

During the installation process, a few temporary pods are created. Keeping those pods as 'Completed' doesn't harm nor waste resources but if you want to delete them to have only 'running' pods in your environment you can use either one of these following command:

```bash
oc delete pod --field-selector=status.phase==Succeeded --all-namespaces

oc get pods --all-namespaces |  awk '{if ($4 == "Completed") system ("oc delete pod " $2 " -n " $1 )}'
```

## Additional methods to remove Failed, Pending, Evicted, and all 'Non-Running' pods

Failed pods:

```bash
oc delete pod --field-selector=status.phase==Failed --all-namespaces
```

Pending pods:

```bash
oc delete pod --field-selector=status.phase==Pending --all-namespaces
```
Evicted pods:

```bash
oc delete pod --field-selector=status.phase==Evicted --all-namespaces
```
All 'Non-Running' pods:

```bash
oc get pods --all-namespaces |  awk '{if ($4 != "Running") system ("oc delete pod " $2 " -n " $1 )}'
```
