

Sample files can be found in the [openshift directory](https://github.com/karmab/openshaft/tree/master/openshift)
Note all the commands are associated to a previously created project called *openshaft*

## IMAGES

images for every component need to be pushed to internal registry. the existing playbooks can upload to openshift, if the following variables are defined (*registry_ip* is optional) :

```
registry_url: docker-registry-default.apps.karmalabs.local
registry_project: openshaft
registry_ip: 192.168.105.244
registry_user: karim
registry_token: nLpl4D7KmhPe3Jr77QkAPnLRqlLD2g6cHfVjgMr3yis
registry_certificate: |
  -----BEGIN CERTIFICATE-----
  MIIDaTCCAlGgAwIBAgIBGTANBgkqhkiG9w0BAQsFADAmMSQwIgYDVQQDDBtvcGVu
  c2hpZnQtc2lnbmVyQDE0OTU3MjM1MTYwHhcNMTcwNTI1MTUwMTAzWhcNMTkwNTI1
  MTUwMTA0WjAYMRYwFAYDVQQDEw0xNzIuMzAuMzMuMTk5MIIBIjANBgkqhkiG9w0B
  AQEFAAOCAQ8AMIIBCgKCAQEAs6CpEaxkBx4tXHBH/TWq7ThJaJWD08Egp5keT9EQ
  fJ6di+0rZv4sqazXjg7sUhXLq37Q5wQ6MaGzTT3pffLUBis7WSjXqBdgcFYJJ7p/
  XcuXeThkRhMTT6zBUPv7evSonLYoTPDugsvZ0XqdJ2Ahg9bXvQwnUTxFLqZB520n
  aao50uKxqtWinnsVaGyeeqi7WUtUW3LMLrp5E3B/AKxn/WwLYn1fJlkiYl/Y9a+g
  Ola1tnhrzwLKx9/dlgKYPiXB3a6528c0MQtJitHMtkfuo1mLS2QiZyx7bEG1Dfp6
  0gTBqapfyiSlStNSp4h5bOKlZyENJVWHvuhgMuXWYzGSkQIDAQABo4GvMIGsMA4G
  A1UdDwEB/wQEAwIFoDATBgNVHSUEDDAKBggrBgEFBQcDATAMBgNVHRMBAf8EAjAA
  MHcGA1UdEQRwMG6CLGRvY2tlci1yZWdpc3RyeS1kZWZhdWx0LmFwcHMua2FybWFs
  YWJzLmxvY2Fsgilkb2NrZXItcmVnaXN0cnkuZGVmYXVsdC5zdmMuY2x1c3Rlci5s
  b2NhbIINMTcyLjMwLjMzLjE5OYcErB4hxzANBgkqhkiG9w0BAQsFAAOCAQEAHas7
  ZMLk9gP4b1NQR2xCjNylui/rUg6N9wf4RgiV857bbMyWzI63eHQs3Zi6/4FPa/Dg
  2FaOwfHNdYiRSlIm9dG0cq5Cu/TX2+Lq0G+ubQeSDUA0XWhUSba83GCOKQrBEJW0
  CeDKEDmbYYCRPDdM0DkhDhbJahR0PG9J9dV5aj96o0ZHRMunavSGdXlt7/KNXHUd
  m7OlGuCPo85P2Lz6ltgd/Pb+NXkCf08hi806kLWQ8JWgLarp7c6+dcZ8NWJ7J220
  uuoOpxg74EnLfdQMpnk2qM7/3EPVybiziFUH6qK3MO4506mpu4BeglDhoNj+iTzy
  rDKw2R3lA10RwoimIw==
  -----END CERTIFICATE-----
  -----BEGIN CERTIFICATE-----
  MIIC6jCCAdKgAwIBAgIBATANBgkqhkiG9w0BAQsFADAmMSQwIgYDVQQDDBtvcGVu
  c2hpZnQtc2lnbmVyQDE0OTU3MjM1MTYwHhcNMTcwNTI1MTQ0NTE1WhcNMjIwNTI0
  MTQ0NTE2WjAmMSQwIgYDVQQDDBtvcGVuc2hpZnQtc2lnbmVyQDE0OTU3MjM1MTYw
  ggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQC7IsAWvHl+LwerdMlxxGR2
  rSNkvsBtsOID/XqnPfuz1q+lhRwpeLaZsGCyVuaHiB1Gykg3w8mumE4CkU+XhDEv
  Nf5WGpGLsso9rkbtZQzSbqKBi9hsEGHMoQr9pTmBZI2jsr0woSnR6ShZid6vL4Rv
  Jk/5LCg4m+KLy+rHzZOdPwuVKyuqS+ta92sM2V32CAEjKV/joWPszAIgFdUbuuIH
  u4W0vvYXKuGm7vUPaKkZBks3FPzT3HJVJVsRCBFCDRnbgkpefOhbk27KDx/I9EzE
  gWbCh11/ktz+nUY0eZ7bu8qf4cDl+DOqILxIKdIJbMWf/BY+PwIApD4J4XiAf8t5
  AgMBAAGjIzAhMA4GA1UdDwEB/wQEAwICpDAPBgNVHRMBAf8EBTADAQH/MA0GCSqG
  SIb3DQEBCwUAA4IBAQArj7Kf2mWs8bhWSiEHATIdWXBHA3HPKCITVhUJdS8t2xi7
  8oF6nHixKd8hwvntbgSrCrAVrue9eQyi9v/+PQQrthaEuei0MTO8goDjl2uwZba8
  bg3/nvRjBk8K12o3M5ME6aRPpkem/ILNZO8lOi+cSpez4aKklRSVMPuT/r9oTgQt
  IzqBb4TFJtqT3msvshJkwlfwE8zb33zjZQoUTvFv7qgesBcmkL+RipdDMVyGogkx
  aDcz0B8NFy8wbS9Y9O0TOW8n2xrGXbM4DQ1NBoEH8sgAxHvwleur81N1OVyvibr9
  D5X4PX9V2KSJH1DYKZZmY0uTPkclZj1rS0QyIs81
  -----END CERTIFICATE-----
```

## PV and PVC

persistent volumes need to be created by the administrator for:

- mysql dir
- glance images to be shared

the sample provided use nfs in both cases


## PERMISSIONS
in the openshaft project, as standard user , we create specific service accounts

```
oc create serviceaccount sa-anyuid
oc create serviceaccount sa-privileged
```

and add them to the corresponding scc

```
oc adm policy add-scc-to-user anyuid system:serviceaccount:openshaft:sa-anyuid
oc adm policy add-scc-to-user privileged system:serviceaccount:openshaft:sa-privileged
```


## CREATING DEPLOYMENT CONFIGS AND SERVICES

objects were mostly created using oc-newapp, redirecting it to a file

```
oc new-app --name=heat $COMPONENT:latest -o yaml > openshaft-$COMPONENT.yaml
```

the resulting file was then edited so that it contains:

- the proper service account ( either pointing to scc anyuid or privileged)
- enabling privileged

## ROUTES

```
oc expose service horizon -l name=horizon
```