---
title: Remove kubeadmin user
tags:
  - Openshift 4
  - Configuration
  - Admin Tasks
emoji: "\U0001F5C2️"
link: 'https://docs.openshift.com/container-platform'
created: 2020-09-22T15:57:09.000Z
modified: 2020-09-22T15:57:09.000Z
---

# Remove kubeadmin user

Note: If you do this, ensure that you have another method of Authentication configured and be aware that if that auth backend goes down you will not be able to login to your cluster any longer.

```
oc delete secret kubeadmin -n kube-system
```
