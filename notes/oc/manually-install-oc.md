---
title: 'Download and extract oc, kubectl and openshift-install one liner'
tags:
  - Openshift 4
  - oc
emoji: "\U0001F527"
link: 'https://docs.openshift.com/container-platform'
created: 2020-09-22T18:45:35.000Z
modified: 2020-09-22T18:45:35.000Z
---

# Download and extract oc, kubectl and openshift-install one liner

```
curl -sL https://mirror.openshift.com/pub/openshift-v4/clients/ocp/latest/openshift-client-linux-${OCPVERSION}.tar.gz | sudo tar -C /usr/local/bin -xzf - oc kubectl
curl -sL https://mirror.openshift.com/pub/openshift-v4/clients/ocp/latest/openshift-install-linux-${OCPVERSION}.tar.gz | sudo tar -C /usr/local/bin -xzf - openshift-install
```
