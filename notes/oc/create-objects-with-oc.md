---
title: Deployment var management tips
tags:
  - Openshift 4
  - oc
emoji: "\U0001F5C2️"
link: 'https://docs.openshift.com/container-platform'
created: 2020-09-22T18:45:35.000Z
modified: 2020-09-22T18:45:35.000Z
---

# Create objects using bash `here documents`

This is just an example of a `LoadBalancer` service, but it could be anything yaml based:

```
cat <<EOF | oc apply -f -
apiVersion: v1
kind: Service
metadata:
  name: hello-openshift-lb
spec:
  externalTrafficPolicy: Cluster
  ports:
  - name: http
    port: 80
    protocol: TCP
    targetPort: 8080
  selector:
    app: hello-openshift
  sessionAffinity: None
  type: LoadBalancer
EOF
```
