---
title: Use oc to get cluster role information
tags:
  - Openshift 4
  - oc
emoji: "\U0001F5C2️"
link: 'https://docs.openshift.com/container-platform'
created: 2020-09-25T18:54:23.000Z
modified: 2020-09-25T18:54:23.000Z
---

# Use `oc` to get local clusterroles

```
oc describe rolebinding.rbac -n default
```

# Describe role bindings

```
oc describe clusterrolebindings.rbac
```
