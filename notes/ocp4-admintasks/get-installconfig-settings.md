---
title: Get settings used in install-config
tags:
  - Openshift 4
  - Admin Tasks
  - Configuration
emoji: ⚙️
created: 2020-09-22T15:57:09.000Z
modified: 2020-09-22T15:57:09.000Z
---

# Get Settings used in install config

```
oc get cm -n kube-system cluster-config-v1 -o yaml
```
