---
title: Edit qcow2 image with virt-edit
tags:
  - Openshift 4
  - Installation
emoji: "\U0001F9F9"
link: 'https://docs.openshift.com/'
created: 2020-06-14T04:10:05.000Z
modified: 2020-09-22T13:49:21.000Z
---

This is useful if you need to edit a `.qcow2` file. For example, editing startup configuration of a RHCOS image.

```bash
gunzip image.qcow2.gz
virt-edit -a disk.qcow2 -m /dev/sda1 /loader.1/entries/ostree-1-rhcos.conf
gzip disk.qcow2
```
