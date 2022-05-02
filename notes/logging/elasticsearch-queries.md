---
title: ElasticSearch queries
tags:
  - Openshift 4
  - Logging
emoji: "\U0001F4DC"
link: 'https://access.redhat.com/articles/5015121'
created: 2020-10-09T16:00:26.000Z
modified: 2020-10-09T16:00:26.000Z
---

Display ElasticSearch indices:

```bash
es_pod=$(oc get pod -n openshift-logging --selector=component=elasticsearch --no-headers -o jsonpath='{range .items[?(@.status.phase=="Running")]}{.metadata.name}{"\n"}{end}' | head -n1)
oc exec -c elasticsearch $es_pod -n openshift-logging -- curl -s --key /etc/elasticsearch/secret/admin-key --cert /etc/elasticsearch/secret/admin-cert --cacert /etc/elasticsearch/secret/admin-ca https://localhost:9200/_cat/indices
```

