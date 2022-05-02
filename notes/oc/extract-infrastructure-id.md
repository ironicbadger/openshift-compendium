---
title: Extract Infrastructure ID (infraID)
tags:
  - Openshift 4
  - oc
emoji: "\U0001F527"
link: 'https://docs.openshift.com/container-platform'
created: 2020-09-25T20:00:26.000Z
modified: 2021-10-12T11:15:48.000Z
---

### Extract Infrastructure ID (infraID) using the oc command

```
oc get -o jsonpath='{.status.infrastructureName}{"\n"}' infrastructure cluster
```

### Extract Infrastructure ID (infraID) from $install_dir

```
jq -r '."*installconfig.ClusterID".InfraID' .openshift_install_state.json
jq -r .infraID metadata.json
```
