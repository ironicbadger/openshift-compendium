---
title: API Resources
tags:
  - API
  - oc
emoji: ⌨️
link: 'https://www.openshift.com/blog/'
created: 2020-09-22T13:39:36.000Z
modified: 2020-09-22T13:39:36.000Z
---

A few commands to use when querying the Openshift API.

# API resources

    oc api-resources

## API resources per API group

    oc api-resources --api-group config.openshift.io -o name
    oc api-resources --api-group machineconfiguration.openshift.io -o name
