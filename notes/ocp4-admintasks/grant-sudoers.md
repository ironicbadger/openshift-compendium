---
title: 'Grant Users ability to run --as system:admin'
tags:
  - Openshift 4
  - Admin Tasks
emoji: "\U0001F512"
link: >-
  https://docs.openshift.com/container-platform/4.6/authentication/impersonating-system-admin.html
created: 2020-11-19T16:53:02.000Z
modified: 2020-11-19T16:53:02.000Z
---

There are situations where you want a user to have the ability to run commands but you do not wish to grant them `cluster-admin` privileges. To do this you can add the `sudoer` cluster role to a user.

```bash
oc adm policy add-cluster-role-to-user sudoer <username> --as system:admin
```

Once done the user can now run commands that previous required system:admin level access by appending `--as system:admin` to the end of the command.

```bash
$ oc get nodes
Error from server (Forbidden): nodes is forbidden: User "username" cannot list resource "nodes" in API group "" at the cluster scope

$ oc get nodes --as system:admin
NAME                      STATUS   ROLES    AGE   VERSION
openshift-nq869-master1   Ready    master   35m   v1.19.0+9f84db3
openshift-nq869-master2   Ready    master   35m   v1.19.0+9f84db3
openshift-nq869-master3   Ready    master   35m   v1.19.0+9f84db3
openshift-nq869-worker1   Ready    worker   23m   v1.19.0+9f84db3
openshift-nq869-worker2   Ready    worker   23m   v1.19.0+9f84db3
```
