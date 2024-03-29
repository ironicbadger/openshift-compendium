---
title: Check etcd Performance
tags:
  - Openshift 4
  - Admin Tasks
  - etcd
emoji: "\U0001F9F9"
link: 'https://access.redhat.com/solutions/4985441'
created: 2020-06-30T16:15:30.000Z
modified: 2020-12-20T17:09:49.000Z
---

This command is useful if you need to check the performance of etcd.


## OCP 4.5+

Starting with OpenShift 4.5 there is a new recommended way to test the performance of etcd. The output reports whether the disk is fast enough to host etcd by comparing the 99th percentile of the fsync metric captured from the run to see if it is less than 10ms.

> Run the follow command from a master node.

```bash
podman run --volume /var/lib/etcd:/var/lib/etcd:Z quay.io/openshift-scale/etcd-perf
```

## OCP 4.4+

> Run commands from a master node.

```bash
id=$(sudo crictl ps --name etcdctl | awk 'FNR==2{ print $1}') && sudo crictl exec -it $id /bin/bash

etcdctl check perf --load="m"
etcdctl check perf --load="l"
etcdctl check perf --load="xl"
```

## OCP 4.1-4.3

> Run commands from a master node.

```bash
id=$(sudo crictl ps --name etcd-member | awk 'FNR==2{ print $1}') && sudo crictl exec -it $id /bin/bash

export ETCDCTL_API=3 ETCDCTL_CACERT=/etc/ssl/etcd/ca.crt ETCDCTL_CERT=$(find /etc/ssl/ -name *peer*crt) ETCDCTL_KEY=$(find /etc/ssl/ -name *peer*key)

etcdctl check perf --load="m"
etcdctl check perf --load="l"
etcdctl check perf --load="xl"
```

Example output:

~~~
$ etcdctl check perf --load="m"
 60 / 60 Booooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooo! 100.00%1m0s
PASS: Throughput is 974 writes/s
PASS: Slowest request took 0.468174s
PASS: Stddev is 0.028241s
PASS

$ etcdctl check perf --load="l"
 60 / 60 Booooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooo! 100.00%1m0s
FAIL: Throughput too low: 6491 writes/s
PASS: Slowest request took 0.204441s
PASS: Stddev is 0.023631s
FAIL

$ etcdctl check perf --load="xl"
 60 / 60 Booooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooo! 100.00%1m0s
FAIL: Throughput too low: 8451 writes/s
Slowest request took too long: 0.786915s
PASS: Stddev is 0.063215s
FAIL
~~~
