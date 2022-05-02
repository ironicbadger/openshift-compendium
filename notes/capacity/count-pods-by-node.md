---
title: Count pods by node
tags:
  - Openshift 4
  - Capacity
emoji: "\U0001F522"
created: 2020-06-16T19:48:27.000Z
modified: 2020-09-22T13:49:21.000Z
---

Count running pods:

```bash
oc get pods -o wide --all-namespaces | grep Running | awk '{print $4, $8}' | grep -v "STATUS NODE" | sort | uniq -c | sort -rn
```

Count all pods by node:
```bash
oc get pods -o wide --all-namespaces | awk '{print $4, $8}' | grep -v "STATUS NODE" | sort | uniq -c | sort -rn
```
