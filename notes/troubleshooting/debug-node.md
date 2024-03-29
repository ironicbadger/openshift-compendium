---
title: Debug node
tags:
  - Openshift 4
  - Troubleshooting
emoji: "\U0001F9F0"
created: 2020-06-15T21:35:25.000Z
modified: 2020-09-22T13:49:21.000Z
---

For RHCOS systems, it is not recommended to use SSH to directly access the nodes.  Instead, `oc debug node` should be run.  Here are some examples:

```bash
# check how long the node has been running since last reboot
oc debug node/<node-name> -- chroot /host; uptime

# check if NetworkManager service is running
oc debug node/<node-name> -- chroot /host; systemctl status NetworkManager

# delete unused images in RHCOS node's podman
oc debug node/<node-name> -- chroot /host; podman rmi --all
```
