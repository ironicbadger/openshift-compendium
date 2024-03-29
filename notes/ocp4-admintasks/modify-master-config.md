---
title: Modify Master configuration
tags:
  - Openshift 4
  - Admin Tasks
  - Configuration
emoji: ⚙️
created: 2020-09-22T15:57:09.000Z
modified: 2020-09-22T15:57:09.000Z
---

## OCP Master configuration

The master configuration is now stored in a `configMap`. During the installation
process, a few `configMaps` are created, so in order to get the latest:

```
oc get cm -n openshift-kube-apiserver | grep config
```

Observe the latest id and then:

```
oc get cm -n openshift-kube-apiserver config-ID
```

To get the output in a human-readable form, use:

```
oc get cm -n openshift-kube-apiserver config-ID \
  -o jsonpath='{.data.config\.yaml}' | jq
```

For the OpenShift api configuration:

```
oc get cm -n openshift-apiserver config -o jsonpath='{.data.config\.yaml}' | jq
```
