---
title: Retrieve ignition
tags:
  - Openshift 4
  - Admin Tasks
  - Secrets
emoji: "\U0001F680"
created: 2020-07-15T16:02:27.000Z
modified: 2020-09-22T15:57:09.000Z
---

Retrieve the ignition files used for the purposes of adding new nodes to the cluster.

```oc
# retrieve master ignition
oc extract -n openshift-machine-api secret/master-user-data --keys=userData --to=-

# retrieve worker ignition
oc extract -n openshift-machine-api secret/worker-user-data --keys=userData --to=-
```
