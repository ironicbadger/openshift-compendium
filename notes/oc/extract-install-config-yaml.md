---
title: Extract install-config.yaml
tags:
  - Openshift 4
  - oc
emoji: "\U0001F527"
link: 'https://docs.openshift.com/container-platform'
created: 2020-09-23T19:19:51.000Z
modified: 2020-09-23T19:27:25.000Z
---

### Extract the install-config.yaml in the event it is needed after installation is complete

```
oc get cm cluster-config-v1 -n kube-system -o yaml
```
