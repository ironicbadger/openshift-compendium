---
title: Configure Insecure Registries
tags:
  - Openshift 4
  - Registry
emoji: 🎓
---

To add insecureRegistries you will need to edit the images.config.openshift.io cluster resource. Use the example below as reference.

```bash
oc edit images.config.openshift.io cluster

spec:
  registrySources:
    insecureRegistries:
    - nexus.example.com:5000
    - 192.168.1.100:5000
```
