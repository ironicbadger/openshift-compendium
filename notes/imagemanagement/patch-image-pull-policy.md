---
title: Patch image pull policy
tags:
  - Openshift 4
  - Images
emoji: "\U0001F39E️"
link: >-
  https://docs.openshift.com/container-platform/4.5/openshift_images/managing_images/image-pull-policy.html
created: 2020-09-22T16:03:44.000Z
modified: 2020-09-22T16:03:44.000Z
---

# Patch image pull policy

```
oc patch dc mydeployment -p '{"spec":{"template":{"spec":{"containers":[{"imagePullPolicy":"IfNotPresent","name":"mydeployment"}]}}}}'
```
