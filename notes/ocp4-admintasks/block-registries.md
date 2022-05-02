---
title: Block Registries
tags:
  - Openshift 4
  - Registry
emoji: "\U0001F393"
created: 2020-11-19T16:53:02.000Z
modified: 2020-11-19T16:53:02.000Z
---

Blocked Registries cannot be used for image pull or push actions. To block a registry you will need to edit the images.config.openshift.io cluster resource. Use the example below as reference.

```bash
oc edit images.config.openshift.io cluster

spec:
  registrySources:
    blockedRegistries:
    - docker.io
```
Once applied the `/etc/containers/registries.conf` on all nodes will be updated.

```
$ cat /etc/containers/registries.conf
[registries]
  [registries.search]
    registries = ["registry.access.redhat.com", "docker.io"]
  [registries.insecure]
    registries = []
  [registries.block]
    registries = ["docker.io"]
```
