---
title: View certificates
tags:
  - Troubleshooting
  - Certificates
emoji: 🎓
---

The following are useful commands to view certificates to assist in troubleshooting.

##  View a certificate chain for a local certificate file (i.e. *.cer, *.pem)

```bash
openssl x509 -in mycert.cer -noout -text
```

## View a certificate chain on a remote server

If the remote server is using SNI (that is, sharing multiple SSL hosts on a single IP address) you will need to send the correct hostname in order to get the right certificate.

```bash
openssl s_client -showcerts -servername www.example.com -connect www.example.com:443
```

If the remote server is not using SNI, then you can skip -servername parameter:

```bash
openssl s_client -showcerts -connect www.example.com:443
```

## View expiration date for all certificates
```bash
echo -e "NAMESPACE\tNAME\tEXPIRY" && oc get secrets --all-namespaces -o go-template='{{range .items}}{{if eq .type "kubernetes.io/tls"}}{{.metadata.namespace}}{{" "}}{{.metadata.name}}{{" "}}{{index .data "tls.crt"}}{{"\n"}}{{end}}{{end}}' | while read namespace name cert; do echo -en "$namespace\t$name\t"; echo $cert | base64 -d | openssl x509 -noout -enddate; done
```
